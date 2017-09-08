based on tutorial @ <https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/>

NOTE: had to run `docker login` in order to build docker image

session

```sh
1029  mkdir nodejs-example
1030  cd nodejs-example
1031  touch server.js
1032  node server.js
1033  touch Dockerfile
1034  eval $(minikube docker-env)
1035  docker build -t hello-node:v1 .
1036  docker login
1037  docker build -t hello-node:v1 .
1038  kubectl run hello-node --image=hello-node:v1 --port=8080
1039  kubectl get deployments
1040  kubectl get pods
1041  kubectl get events
1042  kubectl config view
1043  kubectl expose deployment hello-node --type=LoadBalancer
1044  kubectl get services
1045  minikube service hello-node

# make a change to server.js
1047  docker build -t hello-node:v2 .
1048  kubectl set image deployment/hello-node hello-node=hello-node:v2
1049  minikube service hello-node
```