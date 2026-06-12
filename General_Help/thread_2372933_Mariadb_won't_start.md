---
title: "Mariadb won't start"
date: 2017-09-30
forum: General Help
---

### Post by cliffmitchell on 2017-09-30
Our Mariadb installation has problems and I would appreciate any help available please.

The problems started when apt-get update started giving errors (below). It turned out there was a problem with duplicate repositories. In sources.list we had:

deb [arch=amd64,ppc64el,i386] [http://www.ftp.saix.net/DB/mariadb/repo/10.1/ubuntu](http://www.ftp.saix.net/DB/mariadb/repo/10.1/ubuntu) xenial main
and
deb [arch=amd64,i386,ppc64el] [http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu](http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu) xenial main

Deleting the second of these cleared the update problem but now mariadb will not start at all. I have tried:
apt-get purge mariadb-server
apt-get update
apt-get upgrade
apt-get autoremove
apt-get upgrade --fix-broken
apt-get -f install mariadb-server

but nothing seems to work.

I suspect there is a version clash between MariaDB 10.2.1 and 10.2.2 as I see 'A downgrade from MariaDB 10.2.2 or later is not supported.' in the myql errror.log (below).
I have taken a full backup of the /var/lib/mysql/ folder.

How can I get MariaDB working again without losing my existing databases and configuration?
Many thanks,
Cliff


_apt-get update errors:_
```

root@ubuntu:~# apt-get update
Hit:1 http://ppa.launchpad.net/pbek/qownnotes/ubuntu xenial InRelease
Hit:2 http://mirrors.coreix.net/mariadb/repo/10.2/ubuntu xenial InRelease                                                                   
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                                                  
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial InRelease                          
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]         
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                 
Fetched 306 kB in 0s (373 kB/s)                              
Reading package lists... Done
root@ubuntu:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libmariadbclient18 libmysqlclient18
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mariadb-server-10.1 (10.1.28+maria-1~xenial) ...
 * Stopping MariaDB database server mysqld                                                                                            [ OK ] 
 * Starting MariaDB database server mysqld                                                                                            [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing package mariadb-server-10.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mariadb-server-10.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~# service mysql restart
 * Stopping MariaDB database server mysqld                                                                                            [ OK ] 
 * Starting MariaDB database server mysqld                                                                                            [fail] 


```

_The mysql error.log shows:_

```

2017-09-30 14:06:23 139769919252736 [Note] Using unique option prefix 'myisam-recover' is error-prone and can break in the future. Please us$
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: innodb_empty_free_list_algorithm has been changed to legacy because of small buffer pool $

2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Using mutexes to ref count buffer pool pages
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: The InnoDB memory heap is disabled
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: GCC builtin __atomic_thread_fence() is used for memory barrier
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Compressed tables use zlib 1.2.8
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Using Linux native AIO
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Using SSE crc32 instructions
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Initializing buffer pool, size = 128.0M
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Completed initialization of buffer pool
2017-09-30 14:06:23 139769919252736 [Note] InnoDB: Highest supported file format is Barracuda.
InnoDB: No valid checkpoint found.
InnoDB: A downgrade from MariaDB 10.2.2 or later is not supported.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: http://dev.mysql.com/doc/refman/5.6/en/error-creating-innodb.html
2017-09-30 14:06:23 139769919252736 [ERROR] Plugin 'InnoDB' init function returned error.
2017-09-30 14:06:23 139769919252736 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2017-09-30 14:06:23 139769919252736 [Note] Plugin 'FEEDBACK' is disabled.

```

_Restarting mysql gives the following:_

```

root@ubuntu:~# service mysql restart
 * Stopping MariaDB database server mysqld                                                                                            [ OK ] 
 * Starting MariaDB database server mysqld                                                                                            [fail] 


```

---

### Post by cliffmitchell on 2017-09-30
For those who have a similar problem we have found the solution here: 
[URL="https://support.plesk.com/hc/en-us/articles/115000940709-Unable-to-start-MySQL-service-InnoDB-No-valid-checkpoint-found"]https://support.plesk.com/hc/en-us/articles/115000940709-Unable-to-start-MySQL-service-InnoDB-No-valid-checkpoint-found
[/URL]The cause of the problem is corrupted ib_logfile0 and ib_logfile1 files.
So for us the solution was: root@ubuntu:/var/lib/mysql# mv ib_logfile0 ib_logfile0_bak
root@ubuntu:/var/lib/mysql# mv ib_logfile1 ib_logfile1_bak

Hope that helps someone.

---

