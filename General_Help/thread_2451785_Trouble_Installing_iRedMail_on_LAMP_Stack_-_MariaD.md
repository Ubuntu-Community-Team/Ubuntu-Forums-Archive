---
title: "Trouble Installing iRedMail on LAMP Stack - MariaDB Issue"
date: 2020-10-10
forum: General Help
---

### Post by aaronesteban on 2020-10-10
So I already installed the LAMP server from the default "one-click installation" on Digital Ocean, then tried to install iRedMail right after.


Do I need to install iRedMail first, or do I need to set a Domain Name and set up DNS records first with my LAMP stack? I'm not sure if I already needed LAMP stack with DNS records for a domain first or if I need to install iRedMail first. I believe that this is why I am running into this issue, but still not sure.


Also, when asked to "choose the web server" during installation, I chose not to install any because I already have the LAMP server installed. What should I have chosen in this case?


==== REQUIRED BASIC INFO OF YOUR IREDMAIL SERVER ====
- iRedMail version 1.3.1
- Deployed with ssh command line installation.
- Linux Ubuntu 20.04 (latest version)
- MySQL:
- Web Server is Apache
- Manage mail accounts with open source free version (to start with but thinking about pro version)
- Error log message is shown below:

```
The following packages have unmet dependencies:
mariadb-server : Depends: mariadb-server-10.3 (>= 1:10.3.22-1ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
<< ERROR >> Installation failed, please check the terminal output.

```+++++++++++++++++++++


Thanks for any support!

---

