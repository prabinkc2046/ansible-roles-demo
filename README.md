# Deploying a containerized application with ansible

This project demonstrates how to automate the deployment of a containerized application using Ansible roles. The Ansible roles in this repository cover various aspects of the deployment process, ensuring that it is efficient, repeatable, and secure.

## Project Structure
```
app-deployment-with-ansible/
├── ansible.cfg
├── host_vars
│   ├── new_user.yml
│   └── shapetracker.yml
├── inventory
│   └── production
│       └── host
├── playbooks
│   ├── deploy-app.yml
│   ├── docker-compose-setup.yml
│   ├── docker-setup.yml
│   ├── firewall-setup.yml
│   ├── nginx-setup.yml
│   └── system-setup.yml
├── README.md
└── roles
    ├── deploy-app
    │   ├── defaults
    │   │   ├── main.yml
    │   │   └── new_user.yml
    │   └── tasks
    │       └── main.yml
    ├── docker-compose-setup
    │   ├── defaults
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── docker-setup
    │   ├── defaults
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── firewall-setup
    │   ├── defaults
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── nginx-setup
    │   ├── defaults
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── nginx.config.jj
    └── system-setup
        ├── defaults
        │   └── main.yml
        ├── handlers
        │   └── main.yml
        └── tasks
            └── main.yml
```

## Deployment Process

To deploy your containerized application, follow these steps:

### System Setup: Configure the target system for deployment.

```shell
ansible-playbook -i inventory/production/host playbooks/system-setup.yml
```

### Firewall Setup: Set up the firewall rules to secure the system.

```shell
ansible-playbook -i inventory/production/host playbooks/firewall-setup.yml
```

### Docker Setup: Install and configure Docker on the target system.

```shell
ansible-playbook -i inventory/production/host playbooks/docker-setup.yml
```
### Docker Compose Setup: Configure Docker Compose for container orchestration.

```shell
ansible-playbook -i inventory/production/host playbooks/docker-compose-setup.yml
```

### Deploy App: Deploy your containerized application.

```shell
ansible-playbook -i inventory/production/host playbooks/deploy-app.yml
```

### Nginx Setup: Configure Nginx as a reverse proxy for your application.

```shell
ansible-playbook -i inventory/production/host playbooks/nginx-setup.yml
```

After completing these steps, your application will be available at http://ip_address.

## Security
Security is a top priority in this project. All sensitive variables are encrypted using Ansible Vault to ensure the confidentiality of your deployment.

### Variables
host_vars/new_user.yml: Contains variables specific to the new user.
host_vars/shapetracker.yml: Contains variables specific to the host.

# Feedback and Contributions
If you have any feedback or would like to contribute to this project, please feel free to open an issue or a pull request on GitHub.

