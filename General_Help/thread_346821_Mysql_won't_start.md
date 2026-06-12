---
title: "Mysql won't start"
date: 2007-01-26
forum: General Help
---

### Post by c3o on 2007-01-26
Yesterday it ran just fine however after I rebooted today mysql won't start.

```
c3o@srv:~$ sudo mysqld
Password:
070126 17:08:55  InnoDB: Started; log sequence number 0 12522546
mysqld: File '/var/log/mysql/mysql-bin.000118' not found (Errcode: 2)
070126 17:08:55 [ERROR] Failed to open log (file '/var/log/mysql/mysql-bin.000118', errno 2)
070126 17:08:55 [ERROR] Could not open log file
070126 17:08:55 [ERROR] Can't init tc log
070126 17:08:55 [ERROR] Aborting

070126 17:08:55  InnoDB: Starting shutdown...
070126 17:08:58  InnoDB: Shutdown completed; log sequence number 0 12522546
070126 17:08:58 [Note] mysqld: Shutdown complete
```

Using MySQL 5.0 & Ubuntu 6.10

I did this...

```
c3o@srv:~$ sudo cp /var/log/mysql/mysql-bin.000108 /var/log/mysql/mysql-bin.000118
c3o@srv:~$ sudo chmod 777 /var/log/mysql/mysql-bin.000118
c3o@srv:~$ sudo mysqld
070126 17:27:33  InnoDB: Started; log sequence number 0 12522546
070126 17:27:33 [ERROR] Binlog has bad magic number;  It's not a binary log file that can be used by this version of MySQL
070126 17:27:33 [ERROR] Can't init tc log
070126 17:27:33 [ERROR] Aborting

070126 17:27:33  InnoDB: Starting shutdown...
070126 17:27:35  InnoDB: Shutdown completed; log sequence number 0 12522546
070126 17:27:35 [Note] mysqld: Shutdown complete
```

and if I replace the file with an empty one:

```
c3o@srv:~$ sudo mysqld
070126 17:30:03  InnoDB: Started; log sequence number 0 12522546
070126 17:30:03 [ERROR] I/O error reading the header from the binary log, errno=-1, io cache code=0
070126 17:30:03 [ERROR] I/O error reading the header from the binary log
070126 17:30:03 [ERROR] Can't init tc log
070126 17:30:03 [ERROR] Aborting

070126 17:30:03  InnoDB: Starting shutdown...
070126 17:30:05  InnoDB: Shutdown completed; log sequence number 0 12522546
070126 17:30:05 [Note] mysqld: Shutdown complete

```

---

### Post by lamego on 2007-01-26
```
sudo cp /var/log/mysql/mysql-bin.000108 /var/log/mysql/mysql-bin.000118
```
Your database seems to be corrupted (missing files), copying log files is not a fix...

---

### Post by Naveen P.L. on 2007-04-24
I had the same problem when trying to start mysql server. There was no problem when shutting down the system the previous day. However when I tried to restart the system in the morning it crashed during bootup and mysql failed to start after that. The following is the log from syslog
```

Apr 24 11:47:29 zyxware07 /etc/init.d/mysql[5219]: 
Apr 24 11:52:05 zyxware07 mysqld_safe[5340]: started
Apr 24 11:52:05 zyxware07 mysqld[5343]: 070424 11:52:05  InnoDB: Started; log sequence number 0 80094
Apr 24 11:52:05 zyxware07 mysqld[5343]: 070424 11:52:05 [ERROR] Binlog has bad magic number;  It's not a binary log file that can be used by this version of MySQL
Apr 24 11:52:05 zyxware07 mysqld[5343]: 070424 11:52:05 [ERROR] Can't init tc log
Apr 24 11:52:05 zyxware07 mysqld[5343]: 070424 11:52:05 [ERROR] Aborting
Apr 24 11:52:05 zyxware07 mysqld[5343]: 

```

It looked as if the last binary log file was corrupted during improper shutdown. 
I was able to get the server back by deleting the last binary log file from /var/log/mysql and then deleting the reference to this last file from /var/log/mysql/mysql-bin.index

---

