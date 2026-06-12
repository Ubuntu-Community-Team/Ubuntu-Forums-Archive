---
title: "Slimserver Problems [Mainly My SQL]"
date: 2008-04-14
forum: General Help
---

### Post by money2themax on 2008-04-14
this is my problem

```

[FONT=monospace]money2themax@MX-UBUNTU-000:~$ sudo apt-get install squeezecenter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmysqlclient15-dev mysql-server-5.0 sox
Suggested packages:
  mysql-doc-5.0 tinyca
The following NEW packages will be installed:
  libmysqlclient15-dev mysql-server-5.0 sox squeezecenter
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.9MB of archives.
After unpacking 154MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  squeezecenter
Install these packages without verification [y/N]? y
Get:1 http://debian.slimdevices.com stable/main squeezecenter 7.0 [18.9MB]                               
Get:2 http://archive.ubuntu.com gutsy-updates/main mysql-server-5.0 5.0.45-1ubuntu3.3 [26.8MB]                                                              
Get:3 http://archive.ubuntu.com gutsy-updates/main libmysqlclient15-dev 5.0.45-1ubuntu3.3 [7042kB]                                                          
Get:4 http://archive.ubuntu.com gutsy/universe sox 13.0.0-1build1 [199kB]                                                                                   
Fetched 52.9MB in 4m40s (189kB/s)                                                                                                                           
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 271992 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package libmysqlclient15-dev.
Unpacking libmysqlclient15-dev (from .../libmysqlclient15-dev_5.0.45-1ubuntu3.3_i386.deb) ...
Selecting previously deselected package sox.
Unpacking sox (from .../sox_13.0.0-1build1_i386.deb) ...
Selecting previously deselected package squeezecenter.
Unpacking squeezecenter (from .../squeezecenter_7.0_all.deb) ...
Setting up mysql-server-5.0 (5.0.45-1ubuntu3.3) ...
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
 * Starting MySQL database server mysqld                                                                                                              [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up libmysqlclient15-dev (5.0.45-1ubuntu3.3) ...

Setting up sox (13.0.0-1build1) ...

Setting up squeezecenter (7.0) ...
Adding system user `squeezecenter' (UID 117) ...
Adding new user `squeezecenter' (UID 117) with group `nogroup' ...
Not creating home directory `/usr/share/squeezecenter'.
Starting SqueezeCenter Audio Server.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[/FONT]

```

---

### Post by money2themax on 2008-04-14
actually id don't think its having a problem but i would like to know how to get to my control panel.

---

### Post by money2themax on 2008-04-14
bump

---

