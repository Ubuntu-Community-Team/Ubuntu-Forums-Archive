---
title: "Cannot Install/Start MySQL Server"
date: 2014-06-12
forum: General Help
---

### Post by jp.brandon on 2014-06-12
I have not posted on here really before, and right now I am pulling out my hair. So if this is not in the right sub forum I am sorry about it...

I have all my database/tables dumped and on a seperate HDD. This is also a Dev Machine and not my main Production Machine. I also backed up the MySQL_Config and MySQL_Data.

Okay, I decided to migrate from MySQL Server 5.5.37 to Percona Server 5.6. I ended up removing MySQL Server by the following:

> 
sudo apt-get --purge remove mysql-server mysql-server-5.5 mysql-server-core-5.5 mysql-client mysql-client-core-5.5 mysql-common
sudo apt-get autoremove
sudo apt-get autoclean

rm -rf /var/lib/mysql
rm -rf /etc/mysql


Now I have a major problem, I can't seem to get MySQL Server 5.6 to install or start. When I installed 5.6 it asked for a password for the MySQL "root" password. I tried a pass and without a pass. I get the error "Cannot set "root" password". I also get this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
brandon@brandon-DB:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient18 libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server-5.5 mysql-server-core-5.5
Suggested packages:
  libmldbm-perl libnet-daemon-perl libplrpc-perl libsql-statement-perl tinyca mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libmysqlclient18 libterm-readkey-perl mysql-client-5.5 mysql-client-core-5.5 mysql-common
  mysql-server mysql-server-5.5 mysql-server-core-5.5
0 upgraded, 10 newly installed, 0 to remove and 35 not upgraded.
Need to get 0 B/8,955 kB of archives.
After this operation, 96.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 167760 files and directories currently installed.)
Preparing to unpack .../mysql-common_5.5.37-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package libmysqlclient18:amd64.
Preparing to unpack .../libmysqlclient18_5.5.37-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libmysqlclient18:amd64 (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package libdbi-perl.
Preparing to unpack .../libdbi-perl_1.630-1_amd64.deb ...
Unpacking libdbi-perl (1.630-1) ...
Selecting previously unselected package libdbd-mysql-perl.
Preparing to unpack .../libdbd-mysql-perl_4.025-1_amd64.deb ...
Unpacking libdbd-mysql-perl (4.025-1) ...
Selecting previously unselected package libterm-readkey-perl.
Preparing to unpack .../libterm-readkey-perl_2.31-1_amd64.deb ...
Unpacking libterm-readkey-perl (2.31-1) ...
Selecting previously unselected package mysql-client-core-5.5.
Preparing to unpack .../mysql-client-core-5.5_5.5.37-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-core-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-client-5.5.
Preparing to unpack .../mysql-client-5.5_5.5.37-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-client-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-core-5.5.
Preparing to unpack .../mysql-server-core-5.5_5.5.37-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-core-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up mysql-common (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server-5.5.
(Reading database ... 168116 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.37-0ubuntu0.14.04.1_amd64.deb ...
Unpacking mysql-server-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../mysql-server_5.5.37-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-server (5.5.37-0ubuntu0.14.04.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libmysqlclient18:amd64 (5.5.37-0ubuntu0.14.04.1) ...
Setting up libdbi-perl (1.630-1) ...
Setting up libdbd-mysql-perl (4.025-1) ...
Setting up libterm-readkey-perl (2.31-1) ...
Setting up mysql-client-core-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Setting up mysql-client-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Setting up mysql-server-core-5.5 (5.5.37-0ubuntu0.14.04.1) ...
Setting up mysql-server-5.5 (5.5.37-0ubuntu0.14.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by jp.brandon on 2014-06-12
I was able to get MySQL Server 5.6 Installed on my machine!

---

### Post by QIII on 2014-06-12
Hello!

Good news!  Could you fill us in on how you did it in case someone else has this problem later?

---

