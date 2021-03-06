# Elk-Pro-Cyb
Northwestern Cyber Security Elk project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  elk_playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting access to the network.
What aspect of security do load balancers protect? They help distribute the traffic across multiple servers in case of fail. What is the advantage of a jump box? Help manage internal servers

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- _TODO: What does Filebeat watch for? Is a lightweight shipper that monitors the log files and reports to logstash
- _TODO: What does Metricbeat record? Monitors servers by collecting metrics from the system and services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name               | Function | IP Address | Operating System |
|--------------------|----------|------------|------------------|
| JumpBoxProvisioner | Gateway  | 10.0.0.4   | Linux            |
| Web-1              | Server   | 10.0.0.5   | Linux            |
| Web-2              | Server   | 10.0.0.6   | Linux            |
| Web-3              | Server   | 10.0.0.7   | Linux            |
| ELK-Web1           | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
73.211.142.146

Machines within the network can only be accessed by ELK-Web1.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses |
|--------------------|---------------------|----------------------|
| JumpBoxProvisioner | Yes                 | 10.0.0.4             |
| Web-1              | No                  | 10.0.0.5             |
| Web-2              | No                  | 10.0.0.6             |
| Web-3              | No                  | 10.0.0.7             |
| ELK-Web1           | Yes                 | 10.1.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
By automating with Ansible it simplifies tasks that otherwise will be too complex or time consuming. 
The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Configure the target VM to use more memory (_vm.max_map_count 262144_)
- Install _docker.io_ that is used for running containers; _python3-pip_ used to install Python software; _docker_ required to control state of Docker containers
- Download the Docker container _sebp/elk:761_
- Configure the container to be accessed by the following ports _5601, 9200, 5044_

- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: /Elk-Pro-Cyb/Images/docker_ps.png
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.5
10.0.0.6
10.0.0.7
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeat
Metricbeat
These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects file logs and forwards them to either Elasticsearch or Logstash for further indexing.
Metricbeat monitors and collects metrics from the servers and ships them to an Elasticsearch or Logstash for further inspection. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the hosts file to my ansible.
- Update the host file to include my ELK VM IP (10.1.0.4)...
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? The file is the install-elk.yml_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? I run the command ansible-playbook install-elk.yml _
- _Which URL do you navigate to in order to check that the ELK server is running? curl localhost:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
