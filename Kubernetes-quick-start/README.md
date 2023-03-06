## Intro K8S - Quick Start

Link
- https://learn.acloud.guru/course/9a0082c5-5331-492d-a677-173c393a85f7/overview

Chapter 1

K8s works with any Container iniciative, for example Docker.

### Contexto Docker
Docker node, have  1 or many containers, with his own IPs. No se ven entre si, no se puedne comunicar con otros nodos.
No hay name resolution, nada mapea el servicio, no proxy

- Todos los contenedores de un nodo COMPARTEN el espacio de HOST IP y deben coordinarse con que puertos trabajar.
Ejemplo, si tengo 2 containers con MYSQL, hay que usar un loadbalancer para redirigir el trafico con el puerto, porque todos usan el mismo espacio

- Si un container tiene que ser reemplazado, requiere un nuevo espacio de IP address, y si se hace un hard-codeo de IP, esto se rompera
Ejemplo, 1 container es una db, y otro container es el front. Si la db se borra, tengo que recrear toda mi base de datos

- Los nodos de docker, no son ip routeables, y todos los nodos tienen la misma ip, 172.17.42.1


### Kubernetes solves:
1. one master node, and N workers nodes. K8s deploys a POD, it is the smallest unit of K8s, and can be either a single container or a group of containers.
All containers in a pod have the same IP address, and all pods in a cluster have unique IPs in the same IP space.
2. 1 Cluster, have 1 or N PODS
3. The pod is what holds the IP address, por eso todos los contenedores en un pod, tienen la misma IP.
4. Todos los pods dentro de un cluster, comparten el mismo espacio de IP.
5. Todos los containers se pueden comunicar entre si, SIN NAT

K8s:
Network-> encargado de los puertos, y las ip de k8s
Etcd -> key value store for the cluster, asi todos los objetos y su metadata estan referenciados
Kubelet-> run all of the nodes, the master one, the workers y se asegura que sus estados, sean los estados que le asignaste
