# Kubernetes Ansible Role

```
cat << EOF > requirements.yml
- src: https://github.com/ozhankaraman/ansibleroles.git
  name: kubernetes
  scm: git
  version: main
EOF

cat << EOF > inventory.ini
x1 ansible_host=x1.zz.zebrastack.com ansible_connection=ssh ansible_ssh_user=root ansible_ssh_pass=xxxx
EOF

cat << EOF > kubernetes.yml
---
- name: Kubernetes Role
  hosts: all
  gather_facts: yes
  roles:
    - { role: kubernetes, tags: ['main'] }
EOF

ansible-galaxy install -r requirements.yml
ansible-galaxy  list
export ANSIBLE_HOST_KEY_CHECKING=False
ansible-playbook kubernetes.yml --inventory-file inventory.ini
```
