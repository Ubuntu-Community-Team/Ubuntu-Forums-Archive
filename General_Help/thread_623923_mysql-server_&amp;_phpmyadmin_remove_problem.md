---
title: "mysql-server &amp; phpmyadmin remove problem"
date: 2007-11-26
forum: General Help
---

### Post by kernel1 on 2007-11-26
Hi i want to uninstall mysql-server and phpmyadmin cause I can't reset root password. I tried many methods to reset/recover but I can't.

When I type: sudo apt-get remove mysql-server:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.38-0ubuntu1.1) but it is not going to be installed
                    Depends: libdbi-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Also when I tried to stop mysql server, always failed to stop

I am confused....

Thank you

---

### Post by TidusBlade on 2007-11-26
I think it's saying that you didn't install it, and assuming you didnt try it, what does "sudo apt-get -f install" return?

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
 * Stopping MySQL database server mysqld                           [fail] 
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

