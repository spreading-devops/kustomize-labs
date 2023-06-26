# Kustomize

## Step by Step how to use

### Create a Deployment (nginx version 1.16.0) and Kustomize YAML files

```bash
$ cat <<EOF >./nginx/kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
- deployment-nginx.yaml
images:
  - name: nginx
    newName: nginx
    newTag: 1.16.0
commonAnnotations:
  kubernetes.io/change-cause: "Initial deployment with 1.16.0"
EOF
```

### Kustomize it
```bash
$ kubectl kustomize ./nginx/
```

### Apply to the K8s cluster
```bash
$ kubectl apply -k nginx
```

### Modify the Deployment (update nginx to version 1.17.0) and update the Kustomize YAML files

```bash
$ cat <<EOF >./nginx/kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
- deployment-nginx.yaml
images:
  - name: nginx
    newName: nginx
    newTag: 1.17.0
commonAnnotations:
  kubernetes.io/change-cause: "image updated to 1.17.0"
EOF
```

### Kustomize it with the updated files
```bash
$ kubectl kustomize ./nginx/
```

### Apply the chanhes to the K8s cluster
```bash
$ kubectl apply -k nginx
```

### Check deployment history
```bash
$ kubectl rollout history deployment nginx-deployment
```

```bash
$ 
```

```bash
$ 
```


```bash
$ 
```


```bash
$ 
```


```bash
$ 
```






