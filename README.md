# argo-demo
Testeando ArgoCD + GithubActions

### instalacion de argo

```bash
helm install argo-cd argo-cd/ \
  --namespace argocd \
  --create-namespace --wait \
  --set configs.credentialTemplates.github.url=https://github.com/tinchos \
  --set configs.credentialTemplates.github.username=$GH_USERNAME \
  --set configs.credentialTemplates.github.password=$GH_PAT
```
verificar password:
```kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo```

acceder al GUI:
```kubectl port-forward service/argo-cd-argocd-server -n argocd 8080:443```

para utilizar los comando de argocd en la consola, seguir estos pasos:
https://argo-cd.readthedocs.io/en/stable/cli_installation/#download-latest-version

se puede cambiar la password de admin que viene por defecto por una custom con el siguiente comando:
1- hacer el login via consola previo port-foward ```argocd login localhost:8080```
2- cambiar la password: ```argocd account update-password```

