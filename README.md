### Haproxy and k3s cluster with Ansible
### Copy your public key (~/.ssh/id_rsa.pub) to the appropriate server's ~/.ssh/authorized_keys or use:
#### ssh-copy-id wolf@192.168.4.196
#### ssh-copy-id wolf@192.168.4.195
---
### Edit:
#### sudo visudo
#### YourUSER ALL=(ALL) NOPASSWD:ALL
---
### "-K" must be used if the sudo password must be typed...
#### ansible-playbook -i inventory.ini playbook.yaml -K

### If You save .txt to /tmp/k3s_node_token.txt (MAC OSX):
#### ansible-playbook -i inventory.ini playbook.yml --ask-become-pass
---
### Haproxy install with ansible:
#### ansible-playbook -i inventory.ini playbook.yaml
---
#### Edit hosts:
#### sudo nano /etc/hosts

#### 192.168.4.194 haproxy
#### 192.168.4.196 master1
#### 192.168.4.195 master2
#### 192.168.4.197 worker1
---
### Use to master1:
#### sudo kubectl get nodes
---
#### Instal Haproxy manual:
#### sudo apt update && sudo apt install haproxy -y
#### /etc/haproxy/haproxy.cfg
#### sudo systemctl restart haproxy
---
#### k3s scripts location:
#### sudo ls -la /usr/local/bin/
---
#### Uninstall k3s:
#### sudo /usr/local/bin/k3s-uninstall.sh
#### sudo /usr/local/bin/k3s-agent-uninstall.sh