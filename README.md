# Ansible NGINX Installation Playbook

This repository contains an Ansible playbook to automate the installation of NGINX on a remote web server. The playbook is organized according to Ansible best practices with separate directories for tasks, variables, and inventory.

## Project Structure

```plaintext
ansible_nginx/
│
├── ansible.cfg          # Configuration file for Ansible
├── inventory/
│   └── hosts            # Inventory file defining the target servers
│
├── playbooks/
│   └── nginx.yml        # Main playbook for installing NGINX
│
├── roles/
│   └── nginx/
│       ├── tasks/
│       │   └── main.yml # Tasks for installing and configuring NGINX
│       ├── vars/
│       │   └── main.yml # Variables used in the playbook (if any)
│       └── handlers/
│           └── main.yml # Handlers for actions like restarting NGINX
│
└── README.md            # Documentation of the project
```

## Prerequisites

- Ansible installed on your local machine.
- Python 3 and pip3 installed on the remote server.
- Passwordless SSH access to the remote server using the configured user.
- Passwordless sudo access configured for the Ansible user on the remote server.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/ansible_nginx.git
cd ansible_nginx
```

### 2. Update the Inventory File

Edit the `inventory/hosts` file to include your target server details. For example:

```ini
[web]
ubuntu_vb ansible_host=192.168.1.105 ansible_user=yalma
```

### 3. Run the Playbook

To install NGINX on the remote server, run the following command:

```bash
ansible-playbook playbooks/nginx.yml
```

### 4. Verify the Installation

After running the playbook, verify that NGINX is installed and running on your remote server:

```bash
curl http://<remote_server_ip>
```

You should see the default NGINX welcome page.

## Troubleshooting

If you encounter issues, try running the playbook with increased verbosity to gather more information:

```bash
ansible-playbook playbooks/nginx.yml -vvv
```

Ensure the remote server has Python 3 installed, and the Ansible user has the required permissions.

