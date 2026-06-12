---
title: "problem installing mysql-server 5"
date: 2007-11-29
forum: General Help
---

### Post by kernel1 on 2007-11-29
apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.8MB of archives.
After unpacking 69.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 157561 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1.1_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1.1_all.deb) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
/var/lib/dpkg/info/mysql-server-5.0.postinst: line 143: /etc/mysql/conf.d/old_passwords.cnf: No such file or directory
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I can't install mysql-server

I have removed the previous version and I have deleted the mysql folder in var lib and etc

---

### Post by cdonnelly on 2007-12-05
My friend suggested trying:
apt-get remove --purge mysql-server

He thinks that remove the dummy pkg will clean up the rest of the trash --purge'ing mysql-server-5.0 is not getting.  *shrug*


At work atm, but I'll test it this evening and post the results; just thought you might be able to try sooner.

---

### Post by gsf747 on 2007-12-12
Just ran across this thread because I was getting the same error.  I wasn't able to install mysql-server again until I purged mysql-server, mysql-server-5.0, and mysql-common.

---

### Post by m0rtal on 2008-07-02
> **gsf747 said:**
> Just ran across this thread because I was getting the same error.  I wasn't able to install mysql-server again until I purged mysql-server, mysql-server-5.0, and mysql-common.

thanks, man, that finally solved my similar case!

---

