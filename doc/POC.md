# Demo instructions for accessing the ArgoCD interface.

# Installing a cluster using k3d and configuring argoCD

## Prerequisites

- k3d - https://k3d.io/
- kubectl - https://kubernetes.io/docs/tasks/tools/
- ArgoCD https://argo-cd.readthedocs.io/en/stable/

## Create cluster with k3d

```
k3d cluster create argo
```

## Install ArgocCD 

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Check cluster and resources

```
k cluster-info 
Kubernetes control plane is running at https://0.0.0.0:43231
CoreDNS is running at https://0.0.0.0:43231/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
Metrics-server is running at https://0.0.0.0:43231/api/v1/namespaces/kube-system/services/https:metrics-server:https/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

k get po -n argocd 
NAME                                                READY   STATUS    RESTARTS   AGE
argocd-redis-74d77964b-567wf                        1/1     Running   0          14m
argocd-applicationset-controller-78d68d858c-6fn48   1/1     Running   0          14m
argocd-notifications-controller-6c84989cb4-pb7ns    1/1     Running   0          14m
argocd-application-controller-0                     1/1     Running   0          14m
argocd-server-7c5d6b7df5-5sn2h                      1/1     Running   0          14m
argocd-dex-server-887bcbf79-27ts7                   1/1     Running   0          14m
argocd-repo-server-78bf57564c-xvggx                 1/1     Running   0          14m
```

## Access to ArgoCD UI

### Use `port-forward` to expose the service

```
kubectl port-forward svc/argocd-server -n argocd 8080:443&
```
### Open `url_for_argoc_cd` and make login to the system

### Make sure everything works as expected

## Demo
[![asciicast](https://asciinema.org/a/585159.svg)](https://asciinema.org/a/585159)

