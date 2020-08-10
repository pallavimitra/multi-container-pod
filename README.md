# multi-container-pod
#2conatainer-pod-sharedvolume
create the pod:
kubectl apply -f 2conatainer-pod-sharedvolume.yml

View information about the Pod and the Containers:
kubectl get pod two-containers --output=yaml

Get a shell to nginx Container:
kubectl exec -it two-containers -c nginx-container -- /bin/bash
  
In your shell, verify that nginx is running:

root@two-containers:/# apt-get update
root@two-containers:/# apt-get install curl procps
root@two-containers:/# ps aux

Recall that the debian Container created the index.html file in the nginx root directory. Use curl to send a GET request to the nginx server:
root@two-containers:/# curl localhost
or 
kubectl exec -it two-containers -c nginx-container -- /bin/cat /usr/share/nginx/html/index.html
