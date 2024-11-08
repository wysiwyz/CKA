## Killer_sh_simulator_CKA

### Question 1

Keyword: 

[Solution 01](Sol01.txt)

### Question 2

Keyword: 

[Solution 02](Sol02.txt)

### Question 3

Keyword: 

[Solution 03](Sol03.txt)


### Question 4

Use context: kubectl config use-context k8s-c1-H

 

Do the following in Namespace default. Create a single Pod named ready-if-service-ready of image nginx:1.16.1-alpine. Configure a LivenessProbe which simply executes command true. Also configure a ReadinessProbe which does check if the url http://service-am-i-ready:80 is reachable, you can use wget -T2 -O- http://service-am-i-ready:80 for this. Start the Pod and confirm it isn't ready because of the ReadinessProbe.

Create a second Pod named am-i-ready of image nginx:1.16.1-alpine with label id: cross-server-ready. The already existing Service service-am-i-ready should now have that second Pod as endpoint.

Now the first Pod should be in ready state, confirm that.


Keyword: `execute true`, `readinessProbe`, `wget -T2 -O-`

[Solution 04](Sol04.txt)

### Question 5

Keyword: 

[Solution 05](Sol05.txt)

### Question 6

Keyword: 

[Solution 06](Sol06.txt)

### Question 7

Use context: kubectl config use-context k8s-c1-H

 

The metrics-server has been installed in the cluster. Your college would like to know the kubectl commands to:

    show Nodes resource usage

    show Pods and their containers resource usage

Please write the commands into /opt/course/7/node.sh and /opt/course/7/pod.sh.

Keyword: `kubectl top`, `metrics api`, `--containers=true`

[Solution 07](Sol07.txt)

### Question 8

Keyword: 

[Solution 08](Sol08.txt)

### Question 9
Use context: kubectl config use-context k8s-c2-AC



Ssh into the controlplane node with ssh cluster2-controlplane1. Temporarily stop the kube-scheduler, this means in a way that you can start it again afterwards.

Create a single Pod named manual-schedule of image httpd:2.4-alpine, confirm it's created but not scheduled on any node.

Now you're the scheduler and have all its power, manually schedule that Pod on node cluster2-controlplane1. Make sure it's running.

Start the kube-scheduler again and confirm it's running correctly by creating a second Pod named manual-schedule2 of image httpd:2.4-alpine and check if it's running on cluster2-node1.

Keyword: `systemctl stop`, `systemctl start kube-scheduler`

[Solution 09](Sol09.txt)


### Question 10

Keyword: 

[Solution 10](Sol10.txt)

### Question 11

Keyword: 

[Solution 11](Sol11.txt)

### Question 12

Use context: kubectl config use-context k8s-c1-H

 

Implement the following in Namespace project-tiger:

    Create a Deployment named deploy-important with 3 replicas

    The Deployment and its Pods should have label id=very-important

    It should have two containers:

        First named container1 with image nginx:1.17.6-alpine

        Second named container2 with image google/pause

    There should only ever be one Pod of that Deployment running on one worker node, use topologyKey: kubernetes.io/hostname for this

 

    ℹ️ Because there are two worker nodes and the Deployment has three replicas the result should be that the third Pod won't be scheduled. In a way it simulates the behaviour of a DaemonSet, but using a Deployment and a fixed number of replicas. 

Keyword: `topologyKey: kubernetes.io/hostname`, `topologySpreadConstraint`

[Solution 12](Sol12.txt)

### Question 13

Keyword: 

[Solution 13](Sol13.txt)


### Question 14

Use context: kubectl config use-context k8s-c1-H

 

You're ask to find out following information about the cluster k8s-c1-H:

    How many controlplane nodes are available?

    How many worker nodes are available?

    What is the Service CIDR?

    Which Networking (or CNI Plugin) is configured and where is its config file?

    Which suffix will static pods have that run on cluster1-node1?

Write your answers into file /opt/course/14/cluster-info, structured like this:

```bash
# /opt/course/14/cluster-info
1: [ANSWER]
2: [ANSWER]
3: [ANSWER]
4: [ANSWER]
5: [ANSWER]
```

Keyword: `cluster-info`, `service CIDR`, `CNI plugin-config file path`

[Solution 14](Sol14.txt)

### Question 15

Use context: kubectl config use-context k8s-c2-AC

 

Write a command into /opt/course/15/cluster_events.sh which shows the latest events in the whole cluster, ordered by time (metadata.creationTimestamp). Use kubectl for it.

Now delete the kube-proxy Pod running on node cluster2-node1 and write the events this caused into /opt/course/15/pod_kill.log.

Finally kill the containerd container of the kube-proxy Pod on node cluster2-node1 and write the events into /opt/course/15/container_kill.log.

Do you notice differences in the events both actions caused?

Keyword: 

[Solution 15](Sol15.txt)

### Question 16

Use context: kubectl config use-context k8s-c1-H

 

Write the names of all namespaced Kubernetes resources (like Pod, Secret, ConfigMap...) into /opt/course/16/resources.txt.

Find the project-* Namespace with the highest number of Roles defined in it and write its name and amount of Roles into /opt/course/16/crowded-namespace.txt.

Keyword: `namespace`, 

[Solution 16](Sol16.txt)

### Question 17

Use context: kubectl config use-context k8s-c1-H

 

In Namespace project-tiger create a Pod named tigers-reunite of image httpd:2.4.41-alpine with labels pod=container and container=pod. Find out on which node the Pod is scheduled. Ssh into that node and find the containerd container belonging to that Pod.

Using command crictl:

    Write the ID of the container and the info.runtimeType into /opt/course/17/pod-container.txt

    Write the logs of the container into /opt/course/17/pod-container.log

Keyword: `crictl`, `info.runtimeType`

[Solution 17](Sol17.txt)

### Question 18

Use context: kubectl config use-context k8s-c3-CCC

 

There seems to be an issue with the kubelet not running on cluster3-node1. Fix it and confirm that cluster has node cluster3-node1 available in Ready state afterwards. You should be able to schedule a Pod on cluster3-node1 afterwards.

Write the reason of the issue into /opt/course/18/reason.txt.

Keyword: `kubelet on workdernode`

[Solution 18](Sol18.txt)

### Question 19

> Scoring condition: completion of question 18 and question 20 

Use context: kubectl config use-context k8s-c3-CCC

 

Do the following in a new Namespace secret. Create a Pod named secret-pod of image busybox:1.31.1 which should keep running for some time.

There is an existing Secret located at /opt/course/19/secret1.yaml, create it in the Namespace secret and mount it readonly into the Pod at /tmp/secret1.

Create a new Secret in Namespace secret called secret2 which should contain user=user1 and pass=1234. These entries should be available inside the Pod's container as environment variables APP_USER and APP_PASS.

Confirm everything is working.

Keyword: `env[*].valueFrom.secretKeyRef`, `volumes[*].secret.secretName`

[Solution 19](Sol19.txt)


### Question 20

Use context: kubectl config use-context k8s-c3-CCC

 

Your coworker said node cluster3-node2 is running an older Kubernetes version and is not even part of the cluster. Update Kubernetes on that node to the exact version that's running on cluster3-controlplane1. Then add this node to the cluster. Use kubeadm for this.

Keyword: `kubeadm join`, `kubeadm upgrade apply`

[Solution 20](Sol20.txt)

### Question 21

Use context: kubectl config use-context k8s-c3-CCC

 

Create a Static Pod named my-static-pod in Namespace default on cluster3-controlplane1. It should be of image nginx:1.16-alpine and have resource requests for 10m CPU and 20Mi memory.

Then create a NodePort Service named static-pod-service which exposes that static Pod on port 80 and check if it has Endpoints and if it's reachable through the cluster3-controlplane1 internal IP address. You can connect to the internal node IPs from your main terminal.

Keyword: `static-pod`, `container resource requests`, `endpoint`

[Solution 21](Sol21.txt)

### Question 22
Use context: kubectl config use-context k8s-c2-AC

 

Check how long the kube-apiserver server certificate is valid on cluster2-controlplane1. Do this with openssl or cfssl. Write the expiration date into /opt/course/22/expiration.

Also run the correct kubeadm command to list the expiration dates and confirm both methods show the same date.

Write the correct kubeadm command that would renew the apiserver server certificate into /opt/course/22/kubeadm-renew-certs.sh.


Keyword: `kubeadm certs check-expiration`, `openssl x509 -noout -text -in <.../server.crt>`

[Solution 22](Sol22.txt)


### Question 23
Use context: kubectl config use-context k8s-c2-AC

 

Node cluster2-node1 has been added to the cluster using kubeadm and TLS bootstrapping.

Find the "Issuer" and "Extended Key Usage" values of the cluster2-node1:

    kubelet client certificate, the one used for outgoing connections to the kube-apiserver.

    kubelet server certificate, the one used for incoming connections from the kube-apiserver.

Write the information into file /opt/course/23/certificate-info.txt.

Compare the "Issuer" and "Extended Key Usage" fields of both certificates and make sense of these.


Keyword: `kubeadm`, `kubelet.conf`

[Solution 23](Sol23.txt)


### Question 24

Use context: kubectl config use-context k8s-c1-H

 

There was a security incident where an intruder was able to access the whole cluster from a single hacked backend Pod.

To prevent this create a NetworkPolicy called np-backend in Namespace project-snake. It should allow the backend-* Pods only to:

    connect to db1-* Pods on port 1111

    connect to db2-* Pods on port 2222

Use the app label of Pods in your policy.

After implementation, connections from backend-* Pods to vault-* Pods on port 3333 should for example no longer work.

 

Keyword: `egress`, `pod selector`, `networkpolicy`

[Solution 24](Sol24.txt)


### Question 25

Use context: kubectl config use-context k8s-c3-CCC

 

Make a backup of etcd running on cluster3-controlplane1 and save it on the controlplane node at /tmp/etcd-backup.db.

Then create any kind of Pod in the cluster.

Finally restore the backup, confirm the cluster is still working and that the created Pod is no longer with us.

 

Keyword: `etcdctl snapshot restore`, `etcdctl snapshot save`

[Solution 25](Sol25.txt)


### Question EX 1

Use context: kubectl config use-context k8s-c1-H

 

Check all available Pods in the Namespace project-c13 and find the names of those that would probably be terminated first if the nodes run out of resources (cpu or memory) to schedule all Pods. Write the Pod names into /opt/course/e1/pods-not-stable.txt.

Keyword: `node-pressure eviction`

[Solution Ex 1](Sol_ex_1.txt)


### Question EX 2

Use context: kubectl config use-context k8s-c1-H


There is an existing ServiceAccount secret-reader in Namespace project-hamster. Create a Pod of image curlimages/curl:7.65.3 named tmp-api-contact which uses this ServiceAccount. Make sure the container keeps running.

Exec into the Pod and use curl to access the Kubernetes Api of that cluster manually, listing all available secrets. You can ignore insecure https connection. Write the command(s) for this into file /opt/course/e4/list-secrets.sh.

Keyword: `serviceaccount`, `curl-command`

[Solution Ex 2](Sol_ex_2.txt)


### Preview Question 1

Use context: kubectl config use-context k8s-c2-AC

The cluster admin asked you to find out the following information about etcd running on cluster2-controlplane1:

    Server private key location

    Server certificate expiration date

    Is client certificate authentication enabled

Write these information into /opt/course/p1/etcd-info.txt

Finally you're asked to save an etcd snapshot at /etc/etcd-snapshot.db on cluster2-controlplane1 and display its status.

Keyword: `etcd back up`, `client certificate authentication`

[Solution prev 1](Sol_prev_1.txt)


### Preview Question 2

Use context: kubectl config use-context k8s-c1-H

 
You're asked to confirm that kube-proxy is running correctly on all nodes. For this perform the following in Namespace project-hamster:

Create a new Pod named p2-pod with two containers, one of image nginx:1.21.3-alpine and one of image busybox:1.31. Make sure the busybox container keeps running for some time.

Create a new Service named p2-service which exposes that Pod internally in the cluster on port 3000->80.

Find the kube-proxy container on all nodes cluster1-controlplane1, cluster1-node1 and cluster1-node2 and make sure that it's using iptables. Use command crictl for this.

Write the iptables rules of all nodes belonging the created Service p2-service into file /opt/course/p2/iptables.txt.

Finally delete the Service and confirm that the iptables rules are gone from all nodes.

Keyword: `iptables`, `kube-proxy`, `crictl`

[Solution prev 2](Sol_prev_2.txt)


### Preview Question 3

Create a Pod named check-ip in Namespace default using image httpd:2.4.41-alpine. Expose it on port 80 as a ClusterIP Service named check-ip-service. Remember/output the IP of that Service.

Change the Service CIDR to 11.96.0.0/12 for the cluster.

Then create a second Service named check-ip-service2 pointing to the same Pod to check if your settings did take effect. Finally check if the IP of the first Service has changed.

Keyword: `kube-apiserver`, `service CIDR`

[Solution prev 3](Sol_prev_3.txt)

---

## Reference

- [查詢 -o custom-columns](https://kubernetes.io/docs/reference/kubectl/#custom-columns)

