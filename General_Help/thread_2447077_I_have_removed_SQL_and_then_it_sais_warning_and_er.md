---
title: "I have removed SQL and then it sais warning and error"
date: 2020-07-12
forum: General Help
---

### Post by oldiee on 2020-07-12
Hi there. 

I am trying to remove all of this sql and then start again on mariadb, but it still sais warning and errors:

```
sudo apt remove mysql-server mysql-client mariadb-server mariadb-client
sudo apt auroremove  mysql-server mysql-client mariadb-server mariadb-client
sudo apt purge mysql-server mysql-client mariadb-server mariadb-client
sudo apt update
sudo apt upgrade

```

see the four pictures (remove, auroremove, purge and upgrade): [https://ibb.co/r6zcTDf](https://ibb.co/r6zcTDf), [https://ibb.co/Xk7pPLk](https://ibb.co/Xk7pPLk), [https://ibb.co/KhLxPpw](https://ibb.co/KhLxPpw) and [https://ibb.co/khdgmJr](https://ibb.co/khdgmJr).




There are full of errors here:


/var/log/mysql/error.log
```

[System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.20-0ubuntu0.20.04.1)  (Ubuntu).
[System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.20-0ubuntu0.20.04.1) starting as process 15305
[System] [MY-011012] [Server] Starting upgrade of data directory.
[System] [MY-013576] [InnoDB] InnoDB initialization has started.
[ERROR] [MY-012936] [InnoDB] Database upgrade cannot be accomplished with innodb_force_recovery > 0
[ERROR] [MY-012930] [InnoDB] Plugin initialization aborted with error Generic error.
[ERROR] [MY-011013] [Server] Failed to initialize DD Storage Engine.
[ERROR] [MY-010020] [Server] Data Dictionary initialization failed.
[ERROR] [MY-010119] [Server] Aborting
[System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.20-0ubuntu0.20.04.1)  (Ubuntu).

```


I have `innodb_force_recovery = 1` on /etc/mysql/mysql.conf.d/mysqld.cnf, but that didn't help me.


Can you help me?
Ubuntu 20

---

### Post by EuclideanCoffee on 2020-07-12
Please re-upload the files as attachments to the post rather than using a third-party website. This is a security concern for users.

---

### Post by Impavidus on 2020-07-12
It's also inconvenient to post it like this. Best is to copy the output of the commands as text to a forum post, in code tags. There's no need for something as complex as a screenshot.

All four screenshots show the same error. Apt just repeats that error and refuses to do anything until you tell it how to solve it. You probably want to remove mysql-server-8.0. Maybe a simple```
sudo apt install -f
```does the trick.

---

### Post by oldiee on 2020-07-13
Is it either these of third-party? mysql-server, mysql-client, mariadb-server, mariadb-client, dpkg, nginx? Not sure.
[COLOR=#000000] 

sudo apt install -f[/COLOR]

Same:

```
...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

See the image here: [IMG]https://ibb.co/LQhjY7r[/IMG][IMG]https://ibb.co/LQhjY7r[/IMG]https://ibb.co/LQhjY7r

[COLOR=#000000]sudo apt remove -f mysql-server-8.0
[/COLOR]
```
...
dpkg: error while cleaning up:
installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


sudo apt reinstall mysql-server mysql-client mariadb-server mariadb-client phpmyadmin
```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mariadb-client : Depends: mariadb-client-10.3 (>= 1:10.3.22-1ubuntu1) but it is not going to be installed
 mariadb-server : Depends: mariadb-server-10.3 (>= 1:10.3.22-1ubuntu1) but it is not going to be installed

```

sudo apt autoremove mysql-server mysql-client mariadb-server mariadb-client phpmyadmin
```

Reading package lists...
Building dependency tree...
Reading state information...
Package 'mariadb-client' is not installed, so not removed
Package 'mariadb-server' is not installed, so not removed
Package 'mysql-client' is not installed, so not removed
Package 'mysql-server' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
mysqld will log errors to /var/log/mysql/error.log
2020-07-14T16:27:00.414756Z 0 [ERROR] [MY-010946] [Server] Failed to start mysqld daemon. Check mysqld error log.
Warning: Unable to start the server.
Skipping profile in /etc/apparmor.d/disable: usr.sbin.mysqld
Failed to preset unit: File mysql.service: Link has been severed
/usr/bin/deb-systemd-helper: error: systemctl preset failed on mysql.service: No such file or directory
Failed to start mysql.service: Unit mysql.service not found.
invoke-rc.d: initscript mysql, action "start" failed.
Unit mysql.service could not be found.
dpkg: error processing package mysql-server-8.0 (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 mysql-server-8.0

```


/etc/mysql/mysql.conf.d/mysqld.cnf
```

...
[mysqld]
innodb_force_recovery = 4
...

```



/var/log/mysql/error.log
```

[System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.20-0ubuntu0.20.04.1)  (Ubuntu).
[System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.20-0ubuntu0.20.04.1) starting as process 4142
[System] [MY-011012] [Server] Starting upgrade of data directory.
[System] [MY-013576] [InnoDB] InnoDB initialization has started.
[ERROR] [MY-012936] [InnoDB] Database upgrade cannot be accomplished with innodb_force_recovery > 0
[ERROR] [MY-012930] [InnoDB] Plugin initialization aborted with error Generic error.
[ERROR] [MY-011013] [Server] Failed to initialize DD Storage Engine.
[ERROR] [MY-010020] [Server] Data Dictionary initialization failed.
[ERROR] [MY-010119] [Server] Aborting

```


/var/log/mysql/error.log //innodb_force_recovery = 0
```

[System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.0.20-0ubuntu0.20.04.1)  (Ubuntu).
[System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.20-0ubuntu0.20.04.1) starting as process 4617
[System] [MY-011012] [Server] Starting upgrade of data directory.
[System] [MY-013576] [InnoDB] InnoDB initialization has started.
[ERROR] [MY-011971] [InnoDB] Tablespace 'innodb_undo_001' Page [page id: space=4294967279, page number=3] log sequence number 2824512 is in the future! Current system log sequence number 1659940.
[ERROR] [MY-011972] [InnoDB] Your database may be corrupt or you may have copied the InnoDB tablespace but not the InnoDB log files. Please refer to http://dev.mysql.com/doc/refman/8.0/en/forcing-innodb-recovery.html for information about forcing recovery.
[ERROR] [MY-011971] [InnoDB] Tablespace 'innodb_undo_001' Page [page id: space=4294967279, page number=4] log sequence number 1673689 is in the future! Current system log sequence number 1659940.

```

---

