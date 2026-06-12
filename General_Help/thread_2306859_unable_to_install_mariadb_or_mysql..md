---
title: "unable to install mariadb or mysql."
date: 2015-12-19
forum: General Help
---

### Post by arul1694 on 2015-12-19
I'm trying/have tried  to install mariadb as well as mysql but its giving error 
```
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

i have tried ```
sudo apt-get -f install 
``` but still the installation fails and i get some error.

i am providing the error images below.

Note: its a unmanaged vps with ubuntu 14 in which i have installed webmin.

---

### Post by ian-weisser on 2015-12-19
The error message says that you seem to have a *file conflict*.
You have two packages that are trying to install the same file. Not allowed.
You cannot install both packages on your system at the same time. Uninstall one of the packages.

This sometimes happens when you are following random instructions off the internet, or are trying a new approach without cleaning up the last try.

If you copy-and-paste the error text instead of using a screenshot, I will happily highlight the key passage that shows your the two packages and the exact problem.

I suggest uninstalling ALL mariadb packages, and disabling all non-Ubuntu repositories you have added, before you try again. Installing mariadb from the Ubuntu repositories is usually quite easy.

---

### Post by arul1694 on 2015-12-19
now sudo apt-get -f install also stopped working.

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 92 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up mysql-server-5.5 (5.5.46-0ubuntu0.14.04.2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)




heres my ```
dpkg -l | grep mysql
```

ii  libdbd-mysql-perl               4.025-1                        amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient18                5.5.47+maria-1~trusty          amd64        Virtual package to satisfy external depends
ii  mariadb-common                  5.5.47+maria-1~trusty          all          MariaDB database common files (e.g. /etc/mysql/conf.d/mariadb.cnf)
ii  mysql-client-5.5                5.5.46-0ubuntu0.14.04.2        amd64        MySQL database client binaries
ii  mysql-client-core-5.5           5.5.46-0ubuntu0.14.04.2        amd64        MySQL database core client binaries
ii  mysql-common                    5.5.47+maria-1~trusty          all          MariaDB database common files (e.g. /etc/mysql/my.cnf)
pF  mysql-server-5.5                5.5.46-0ubuntu0.14.04.2        amd64        MySQL database server binaries and system database setup
ii  mysql-server-core-5.5           5.5.46-0ubuntu0.14.04.2        amd64        MySQL database server binaries
rc  php5-mysql                      5.5.9+dfsg-1ubuntu4.14         amd64        MySQL module for php5
ii  php5-mysqlnd                    5.5.9+dfsg-1ubuntu4.14         amd64        MySQL module for php5 (Native Driver)
ii  python-mysqldb                  1.2.3-2ubuntu1                 amd64        Python interface to MySQL
ii  roundcube-mysql                 0.9.5-4                        all          metapackage providing MySQL dependencies for RoundCube

---

### Post by ian-weisser on 2015-12-19
Er, 'install -f' is a powerful command. Don't use it lightly. It will happily cause much damage if used improperly.
If you don't know what process is blocking config, take a break for a few minutes.
If it's still blocked after a break, reboot.

92 packages not upgraded seems like a much more important problem. Solve that before continuing with your install.

---

### Post by arul1694 on 2015-12-19
i upgrade them, now when i do apt-get update and apt-get upgrade, i get 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ian-weisser on 2015-12-19
That's much better.

Have you successfully installed MariaDB?
Or are you still working on that?

---

### Post by arul1694 on 2015-12-26
thnx for your help anf time @ ian.

the installation problem is finally fixed.

but i'm having one more problem mysql stops automatically after two days some time twice in a day and logs shows no error.

151225 14:55:37 InnoDB: Completed initialization of buffer pool
151225 14:55:37 InnoDB: highest supported file format is Barracuda.
151225 14:55:38  InnoDB: Waiting for the background threads to start
151225 14:55:39 InnoDB: 5.5.46 started; log sequence number 2078954
151225 14:55:39 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306
151225 14:55:39 [Note]   - '127.0.0.1' resolves to '127.0.0.1';
151225 14:55:39 [Note] Server socket created on IP: '127.0.0.1'.
151225 14:55:39 [Note] Event Scheduler: Loaded 0 events
151225 14:55:39 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.5.46-0ubuntu0.14.04.2'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)

---

