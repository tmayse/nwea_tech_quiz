## NWEA Tech Quiz

- Requires Ansible 1.9 or newer
- Expects CentOS hosts

This playbook deploys nginx on a CentOS server, serves the index file
at https://github.com/nwea-techops/tech_quiz via HTTP from port 8888, and 
ensures SELinux is enabled and enforced. The document root will be /nginx.
It is recommended that a dedicated partition be mounted at /nginx.

The playbook will run against Ansible hosts in the *tech_quiz* group. An 
example group is provided in hosts.example

Run the playbook, like this:

	ansible-playbook -i hosts site.yml

Alternately, you may create an ad-hoc hosts file just for the quiz and replace *hosts* in the above command with the full path to that file.

### Ideas for Improvement

Here are some ideas for ways that this playbook could be extended:

- Break up generic server setup from quiz-specific configs
- Lock down iptables to just SSH and inbound HTTP on port 8888
- Clean up extraneous and dangerous files
- Additional hardening such as described here: http://www.cyberciti.biz/tips/linux-unix-bsd-nginx-webserver-security.html
- Create symlink for index.html rather than copying it allowing simple updates via git