# Install Trunk Server

Welcome, if you are reading this, you must be trying to install Trunk Server. There will be 2 computers, the local dev computer and the target server you trying to install Trunk Server on. Before we get started there are a couple pre-requisites:
 
 ### Server
 Goto Digital Ocean and create a [Droplet](https://www.digitalocean.com/products/droplets/). Go for an Ubuntu one. Setup it up to login using your SSH key

 ### Domain
  - You need a domain the points to the server IP
  - The following sub-domains configured: www api admin account

### Ansible
  - Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#from-pip) on your local computer: 
  - update the `hosts` file with the IP address of your target server
  - update the `initalize.yml` with:
    - **DOMAIN** The domain you will be using
    - **letsencrypt_email** The email address for using to create Domain Certs
    - **DO_APP_TOKEN** The Digital Ocean App Token to use for verifying the domain during Cert Creation
  - run `ansible-playbook initalize.yml -i hosts`

 ### Config
  - ssh to the server
  - setup your `~/.aws/credentials`
  - configure `docker-prod.sh` and `docker-test.sh`
  - `./docker-prod.sh build`
  - `./docker-prod.sh up -d`
