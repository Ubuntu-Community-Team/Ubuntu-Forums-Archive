---
title: "mysql"
date: 2008-02-17
forum: General Help
---

### Post by midnex on 2008-02-17
Im deleted user.frm now i cant install mysql... pls give me yours etc/mysql folder i need fast server is down ....


midnex@ZereX:~$ sudo apt-get install mysql-server-5.0
[sudo] password for midnex:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 libungif4g
Use 'apt-get autoremove' to remove them.
Suggested packages:
  tinyca mysql-doc-5.0
Recommended packages:
  mailx
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/26.8MB of archives.
After unpacking 84.5MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 104095 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
080217 10:39:28 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
080217 10:39:28 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/user.frm' (errno: 13)
ERROR: 1017  Can't find file: './mysql/user.frm' (errno: 13)
080217 10:39:28 [ERROR] Aborting

080217 10:39:28 [Note] /usr/sbin/mysqld: Shutdown complete

 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
midnex@ZereX:~$

---

### Post by midnex on 2008-02-17
any one knows? :/?

---

### Post by midnex on 2008-02-17
omg jeah its GOOD suport .................

---

### Post by torgrot on 2008-02-17
Try posting in the Server Platform group, someone there can probably give you the file you need.

torgrot

---

