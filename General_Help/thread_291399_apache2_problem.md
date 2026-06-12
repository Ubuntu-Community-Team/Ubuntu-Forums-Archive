---
title: "apache2 problem"
date: 2006-11-02
forum: General Help
---

### Post by arxontas on 2006-11-02
hi guys 
i was trying to install apache2 in order to setup a LAMP SERVER (installation from alternate-cd)mostly as a test server in order to get familiar with linux..(consider me a total noob :)  
Don't lough but i am using a dial-up modem and i tried to install the apache2 from the alternate cdrom instead of the internet.i also installed php5 and mysql following the instructions with no problems.Now when i tried to test the status of the php installation the browser ask if i want to download the php file.
 When i tried to install libapache2-mod-php5 in order to fix it i get the following message:

> $ sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2-mpm-prefork (> 2.0.52) but it is not going to be installed
E: Broken packages



when i tried to install apache2-mpm-prefork i get the following message:

> $ sudo apt-get install apache2-mpm-prefork
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-mpm-prefork: Depends: apache2-common (= 2.0.55-4ubuntu2) but 2.0.55-4ubuntu2.1 is to be installed
E: Broken packages


This might help to understand the problem.

> $ sudo apt-show-versions |grep apache
libapache2-mod-auth-mysql/dapper uptodate 4.3.9-2ubuntu3
apache2-common/dapper uptodate 2.0.55-4ubuntu2.1
apache2-utils/dapper uptodate 2.0.55-4ubuntu2.1
apache2-mpm-worker/dapper uptodate 2.0.55-4ubuntu2.1


This is what i understand :
The apache2-mpm-prefork package depends in the apache2-common (= 2.0.55-4ubuntu2) instead of 2.0.55-4ubuntu**2.1**which i have installed.How can i solve this problem?
apt-get always downloads the apache-common 2.0.55-4ubuntu**2.1**

**PLEASE HELP !!!**

---

### Post by Ramses de Norre on 2006-11-02
Could you install apache2-common, and then do
```
sudo cp -p /var/lib/dpkg/status /var/lib/dpkg/status.old
sudo vi /var/lib/dpkg/status
```
Search the instance for apache2-common and change the version to the one apache2-mpm-prefork depends on. Then try to install it.

This is quiet hacky and it don't now whether it'll work but you can just recover the old status file and nothing will be damaged.

---

### Post by arxontas on 2006-11-02
YOU ARE THE MAN!!!

It worked man .now i have  finally installed a LAMP server.

thanks a lot

P.S how in the heck did you know that?:) 

case solved

---

