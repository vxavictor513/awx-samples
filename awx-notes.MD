# AWX Notes

## Installation
The [official guide](https://github.com/ansible/awx/blob/devel/INSTALL.md "INSTALL.md") provides 3 ways to install AWX.
1. OpenShift
2. Kubernetes
3. Docker / Docker Compose

### Docker (to local host)
1. Download prerequisites
    * [Docker](https://docs.docker.com/engine/installation/, "Docker")
    * [docker-py](https://github.com/docker/docker-py "Python module")
    * ansible

2. Git clone [AWX source code](https://github.com/ansible/awx.git "AWX GitHub")
3. Configure [inventory variables](https://github.com/ansible/awx/blob/devel/INSTALL.md#inventory-variables), such as setting hostname of own's PostgreSQL server.
4. Start up AWX
```
# Set the working directory to installer
$ cd installer

# Run the Ansible playbook
$ ansible-playbook -i inventory install.yml
```

5. Shutdown AWX
```
docker stop awx_task awx_web memcached rabbitmq postgres
```

## Using AWX
The ultimate reference is the [Ansible Tower User Guide](https://docs.ansible.com/ansible-tower/latest/html/userguide/index.html "Ansible Tower User Guide").

### Login
Default user is `admin`, password is `password`.

### Key Concepts in AWX
* **Credentials** are utilized for authentication when launching Jobs against machines, synchronizing with inventory sources, and importing project content from a version control system. E.g. SSH private key, git username and password, AWS access key and secret.
* A **Project** is a logical collection of Ansible playbooks.
* An **Inventory** is a collection of hosts against which jobs may be launched, the same as an Ansible inventory file. See also [Smart Inventories](https://docs.ansible.com/ansible-tower/latest/html/userguide/inventories.html#smart-inventories "Smart Inventories").
* A **Job Template** is a definition and set of parameters for running an Ansible job.

## AWX API
Refer to [Ansible Tower API Guide](https://docs.ansible.com/ansible-tower/latest/html/towerapi/index.html "Ansible Tower API Guide").

## AWX v.s. Ansible Tower
1. Datasheet - https://www.redhat.com/en/resources/awx-and-ansible-tower-datasheet
2. FAQ - https://www.ansible.com/products/awx-project/faq

## How to upgrade AWX
1. https://github.com/ansible/awx/blob/devel/DATA_MIGRATION.md
