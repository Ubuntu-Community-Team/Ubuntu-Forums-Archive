---
title: "Install Snort"
date: 2008-04-23
forum: General Help
---

### Post by resmivarma on 2008-04-23
:confused:

We wanna install Snort in Ubuntu.
Could anyone help us give a link to some tutorial for installing this.
In fact we have already tried this but have been getting the same error again and again!!!! :(:confused:.The error was:


:"root@lalitha-desktop:/opt/snort-2.6.1.4# apt-get install snort-2.6.1.4  snort-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package snort-2.6.1.4
root@lalitha-desktop:/opt/snort-2.6.1.4# apt-get install libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libpcap0.8-dev

........"
we did install libpcap but the Snort couldn't find our libpcap

 regards
Resmi Varma R

---

### Post by justleen on 2008-04-23
dont add the version numbers when installing through apt. the snort packages are: ```
snort - Flexible Network Intrusion Detection System
snort-common - Flexible Network Intrusion Detection System [common files]
snort-common-libraries - Flexible Network Intrusion Detection System ruleset
snort-doc - Documentation for the Snort IDS [documentation]
snort-mysql - Flexible Network Intrusion Detection System [MySQL]
snort-pgsql - Flexible Network Intrusion Detection System [PostgreSQL]
snort-rules-default - Flexible Network Intrusion Detection System ruleset

```
```
 apt-cache search snort
apt-cache search libcap

```

---

### Post by resmivarma on 2008-04-26
Thanks for the reply Justleen.

We did try like what you said.
But the errors persist.
Could you please tell us where to work from?? Presently we work from /opt, but it still says 

"
root@lalitha-desktop:/# apt-cache search libcap
libcapi20-3 - libraries for CAPI support
libcapi20-dev - libraries for CAPI support
libcap1 - support for getting/setting POSIX.1e capabilities

root@lalitha-desktop:/opt# apt-cache search  snort
root@lalitha-desktop:/opt# cd snort-2.6.1.4
root@lalitha-desktop:/opt/snort-2.6.1.4# apt-get install snort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package snort

"
                   
                    If anyone could tell us some manual to install it without much confusion it would be of much help.
Thanks in advance.

---

### Post by Monicker on 2008-04-26
It does not matter which directory you are in when running "apt-get install snort".  Snort is part of the Universe repository, so make sure you have that one enabled.  You can do that via the Synaptic gui or by uncommenting the appropriate lines in /etc/apt/sources.list

---

### Post by resmivarma on 2008-04-26
Thanks for the reply Monicker.

We enabled the repository,installed and started it.But we were denied the permission to view the alerts.

---

### Post by resmivarma on 2008-04-27
Suppose we install snort and mysql seperately, how do we configure to access this database from another system of the same subnet?

---

### Post by Monicker on 2008-04-27
> **resmivarma said:**
> Suppose we install snort and mysql seperately, how do we configure to access this database from another system of the same subnet?

Modify the "output database" line in snort.conf, and make sure the mysql account is allowed to connect from the snort host.

---

### Post by resmivarma on 2008-04-28
we installed apache2 in ubuntu, but the httpd.conf file is empty!!!:confused:
how do we configure now??

---

### Post by Monicker on 2008-04-28
> **resmivarma said:**
> we installed apache2 in ubuntu, but the httpd.conf file is empty!!!:confused:
how do we configure now??

[http://ubuntuforums.org/showthread.php?t=47980]("http://ubuntuforums.org/showthread.php?t=47980")

Search engines are a good thing.

---

### Post by resmivarma on 2008-04-28
We have installed the snort and MySQL.
How can we send the alerts generated to another machine using socket?
Thanks in advance

---

