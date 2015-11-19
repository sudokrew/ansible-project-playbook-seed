###Ansible Project Deployment Seed

####Installation
1. Clone this repo in your project root with the following command:

  `git clone git@bitbucket.org:sudokrew/ansible-project-playbook-seed.git deploy && rm -Rf deploy/.git`

2. Make the proper configuration settings in:

  * deploy/uat

  * deploy/staging

  * deploy/production

  * deploy/deploy-vars.yml

3. Make any per instance deployment changes to deploy/deploy.yml

4. Update the project package.json with the following key/value pairs replacing the __project_name__ with the intended target in your inventory file

  ```
  "scripts": {
    .
    .
    "deploy:production": "ansible-playbook -i deploy/production deploy/deploy.yml --ask-sudo-pass --extra-vars='target=__project_name__'",
    "deploy:staging": "ansible-playbook -i deploy/staging deploy/deploy.yml --ask-sudo-pass --extra-vars='target=__project_name__'",
    "deploy:uat": "ansible-playbook -i deploy/uat deploy/deploy.yml --ask-sudo-pass --extra-vars='target=__project_name__'",
    .
    .
  }
  ```