---
title: "I can't stop and uninstall mysql-server"
date: 2007-11-27
forum: General Help
---

### Post by kernel1 on 2007-11-27
Hmmm When I tried the command:

sudo apt-get remove mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-server-5.0
mysql-client-5.0 libplrpc-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
administrator@chaos:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
mysql-server
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/47.8kB of archives.
After unpacking 86.0kB of additional disk space will be used.
(Reading database ... 158878 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1.1_all.deb) ...
* Stopping MySQL database server mysqld [fail]
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1.1_all.deb (--unpack):
subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It can't stop the mysql-server!!!

---

### Post by MaindotC on 2007-11-27
I uninstalled using the same command and here is my output:```
root@feisty-ids-desktop:/home/feisty-ids# apt-get remove mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  snort-rules-default libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0
  mysql-common libplrpc-perl libmysqlclient15off snort-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mysql-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 86.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108798 files and directories currently installed.)
Removing mysql-server ...
root@feisty-ids-desktop:/home/feisty-ids# updatedb
```

However, assuming that now when I type mysql, it should say "command not found":```
root@feisty-ids-desktop:/home/feisty-ids# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

Very frustrating but hopefully it's a matter of googling.  I'll let you know when I find an answer.  I have to find one tonight b/c this IDS has to be up by tomorrow...$(*&!@

---

### Post by MaindotC on 2007-11-27
Update:

Stop the mysql-server by typing:```
root@feisty-ids-desktop:/etc/init.d/mysql stop
* Stopping MySQL database server mysqld
root@feisty-ids-desktop:apt-get autoremove mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mysql-server is not installed, so not removed
The following packages were automatically installed and are no longer required:
  snort-rules-default libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-server-5.0 mysql-client-5.0
  mysql-common libplrpc-perl libmysqlclient15off snort-common
The following packages will be REMOVED:
  libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl mysql-client-5.0
  mysql-common mysql-server-5.0 snort-common snort-rules-default
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 95.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108795 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                                             [ OK ]
Removing mysql-client-5.0 ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...
Removing libmysqlclient15off ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
Removing mysql-common ...
Removing snort-common ...
Removing snort-rules-default ...
root@feisty-ids-desktop:/home/feisty-ids# updatedb
root@feisty-ids-desktop:/home/feisty-ids# mysql
bash: /usr/bin/mysql: No such file or directory
```

Voila!

---

### Post by teryowen on 2007-11-27
im just making a suggestion not to familiar, but you can try booting up in recovery mode, and then from there just type the commands.

---

### Post by caglarozdag on 2008-06-16
I had the same problem and i fixed it buy running

```
ps -aux | grep mysql
```

and killing the processes (in my case 2 processes) that were related to the mysql daemon.

```
kill -9 12399
```
```
kill -9 1209
```

I don't recommend this solution as some of the related processes that you kill might also be required for other system processes.. I used it because it was an emergency and nothing bad happened so far.

---

