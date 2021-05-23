## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Network Diagram:

https://drive.google.com/file/d/1CNpJVin53k6dWn3yT1I-avJiSzCOMgTO/view?usp=sharing
![image](https://user-images.githubusercontent.com/69355213/119244217-3d8cc680-bb3c-11eb-8699-082ca5b2de38.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional, in addition to restricting high-traffic to the network.

What aspect of security do load balancers protect?

It helps prevent overloading servers as well as optimizes productivity and maximizes uptime.
It also adds resiliency by rerouting live traffic from one server to another causing it to eliminate single points of failure from attacks such as DDoS attack.
What is the advantage of a jump box?

-Jump-box are highly secured computers that are never used for non-admin tasks. -Throughout the years, jump-box has improved into an even more comprehensive/lock-down secure admin workstation to decrease the chances of hackers/malware infection.

What does Filebeat watch for?

It monitors the log files/locations that you specify and forwards them to Elasticsearch/Logstash for indexing.
What does Metricbeat record?

It records metrics/statistics data and transports them to the output that you specifics thru Elasticsearch/Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
|Jump-Box | Gateway    52.255.189.190|   Linux
|Web-1     | VM      | 52.188.49.56  |   Linux     
|Web-2     | VM      | 52.188.49.56  |   Linux     |
|      |          |            |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

*The machines on the internal network are not exposed to the public Internet.

Only the jump-Box-Provisioner machine can accept connections from the Internet.

Access to this machine is only allowed from the following IP addresses:  71.140.151.81 (LocalHost IP address)

*Machines within the network can only be accessed by Jump-Box-Provisioner

Which machine did you allow to access your ELK VM?

Jump-Box-Provisioner 

What was its IP address?

10.0.0.4 (Private)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |     40.75.3.5       |
| Web-1    | No                  |     10.0.0.5         |
| web-2    | No                  |     10.0.0.6         |

### Elk Configuration

*Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

What is the main advantage of automating configuration with Ansible?

One main advantage would be YAML Playbooks. It is the best alternative for configuration management/automation.
It is also able to automate complex multi-tier IT application environemtns.
*The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

First I, SSH into the Jump-Box-Provisioner (ssh redadmin@)40.75.3.5
Start/Attached to the ansible docker (sudo docker start tender_morse)/(sudo docker attach tender_morse)
Went to /etc/ansible/roles directory and created the ELK playbook (Elk_Playbook.yml)
Ran the Elk_Playbook.yml in that same directory (ansible-playbook Elk_Playbook.yml)
Lastly, I SSH into the ELK-VM to verify the server is up and running.
*The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook

*In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

---Filebeat---

Copy the filebeat-configuration.yml file to /etc/ansible/roles/files.
Update the filebeat-configuration.yml file to include the ELK private IP in lines 1106 and 1806.
Run the playbook, and navigate to http://40.75.3.5:5601/app/kibana#/home/ (ELK-VM public IP) to check that the installation worked as expected.

http://40.75.3.5:5601/app/kibana#/dashboard/Filebeat-syslog-dashboard-ecs?_g=(refreshInterval:(pause:!f,value:900000),time:(from:now-7d,to:now))&_a=(description:'Syslog%20dashboard%20from%20the%20Filebeat%20System%20module',filters:!(),fullScreenMode:!f,options:(darkTheme:!f),panels:!((embeddableConfig:(),gridData:(h:16,i:'1',w:32,x:0,y:4),id:Syslog-events-by-hostname-ecs,panelIndex:'1',type:visualization,version:'7.6.1'),(embeddableConfig:(),gridData:(h:16,i:'2',w:16,x:32,y:4),id:Syslog-hostnames-and-processes-ecs,panelIndex:'2',type:visualization,version:'7.6.1'),(embeddableConfig:(columns:!(host.hostname,process.name,message),sort:!('@timestamp',desc)),gridData:(h:28,i:'3',w:48,x:0,y:20),id:Syslog-system-logs-ecs,panelIndex:'3',type:search,version:'7.6.1'),(embeddableConfig:(),gridData:(h:4,i:'4',w:48,x:0,y:0),id:'327417e0-8462-11e7-bab8-bd2f0fb42c54-ecs',panelIndex:'4',type:visualization,version:'7.6.1')),query:(language:kuery,query:''),timeRestore:!f,title:'%5BFilebeat%20System%5D%20Syslog%20dashboard%20ECS',viewMode:view)
