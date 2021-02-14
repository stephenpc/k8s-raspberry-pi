# k8s-raspberry-pi
Automated Installation and Configuration of Kubernetes (K8s) on Raspberry Pi

## Prerequisites
* [Raspberry Pi](https://www.raspberrypi.org/products/raspberry-pi-4-model-b/) boards with a minimum of 2 GiB RAM, preconfigured with Ubuntu (20.04) and connected to your network
    * Here's a handy walkthrough, from Canonical: [How to install Ubuntu Server on your Raspberry Pi](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview)
* [Ansible](https://docs.ansible.com/ansible/latest/user_guide/index.html#getting-started) 2.5.x >= 2.9.x

## Directions

1. Clone this repository to your computer
1. Update `inventory/hosts` with any changes you'd like to make to node names and IPs for your Raspberry Pis
1. Run the installation playbook, overriding any variables specified in `vars`, if you need to
    ```
    ansible-playbook -i inventory kube_cluster_install.yml -v
    ```
1. Run the configuration playbook, which will initialize the control plane and join nodes to the cluster
    ```
    ansible-playbook -i inventory kube_cluster_config.yml -v
    ```
1. Verify that the cluster is healthy
    ```
    ansible-playbook -i inventory kube_cluster_verify.yml -v
    ```

## Special Thanks

The Ansible playbooks were based on these posts:

* [Installing Kubernetes on Raspberry Pi](https://uthark.github.io/post/2020-09-02-installing-kubernetes-raspberrypi/)
* [Build a Kubernetes cluster with the Raspberry Pi](https://opensource.com/article/20/6/kubernetes-raspberry-pi)