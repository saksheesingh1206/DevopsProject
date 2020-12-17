# DevopsProject
DevopsProject 
Install Docker

apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
apt-key fingerprint 0EBFCD88
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt-get install -y docker-ce docker-ce-cli containerd.io

Install K8
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb https://apt.kubernetes.io/ kubernetes-xenial main
EOF
apt-get update
apt-get install -y kubelet kubeadm kubectl
apt-mark hold kubelet kubeadm kubectl


################################################################
 Note: Create local hosts entry  

 

Step1:  kubeadm init --pod-network-cidr=10.244.0.0/16 --upload-certs

 

Step2:

 

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

 

  
Step3:  kubectl apply -f  kube-flannel.yml
https://github.com/coreos/flannel/blob/master/Documentation/kube-flannel.yml



Step 4:

 

Then you can join any number of worker nodes by running the following on each as root:

 

kubeadm join 10.242.6.53:6443 --token xt6hfi.1f9vj23ayj9w3rly \
    --discovery-token-ca-cert-hash sha256:1746c089e3f91aa4243ee5622da741f4769942cd86de8d9454b89f4a859b2b62

 
