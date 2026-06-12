---
title: "newly installed mysql won't start on 12.04 with 'initctl: Unknown job: mysql'"
date: 2015-07-11
forum: General Help
---

### Post by jywarren on 2015-07-11
I've installed 12.04 on a Chromebook (arm) and am getting my development environments running. I apt-get installed `mysql-server` and was prompted to enter a mysql root password, but after that, i sawL

```
Selecting previously unselected package mysql-server-core-5.5.                                                                                                                                
(Reading database ... 91885 files and directories currently installed.)
Unpacking mysql-server-core-5.5 (from .../mysql-server-core-5.5_5.5.43-0ubuntu0.12.04.1_armhf.deb) ...
Selecting previously unselected package mysql-server-5.5.
Unpacking mysql-server-5.5 (from .../mysql-server-5.5_5.5.43-0ubuntu0.12.04.1_armhf.deb) ...
Selecting previously unselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.5.43-0ubuntu0.12.04.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up mysql-server-core-5.5 (5.5.43-0ubuntu0.12.04.1) ...
Setting up mysql-server-5.5 (5.5.43-0ubuntu0.12.04.1) ...
runlevel:/var/run/utmp: No such file or directory
initctl: Unknown job: mysql
150711 14:01:00 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
150711 14:01:00 [Note] /usr/sbin/mysqld (mysqld 5.5.43-0ubuntu0.12.04.1) starting as process 10064 ...
runlevel:/var/run/utmp: No such file or directory
initctl: Unknown job: mysql
Setting up mysql-server (5.5.43-0ubuntu0.12.04.1) ...

```

I then tried to run:

```

(precise)warren@localhost:~/sites/mapknitter$ sudo service mysql start
start: Unknown job: mysql
(precise)warren@localhost:~/sites/mapknitter$ sudo /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start
initctl: Unknown job: mysql


Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
(precise)warren@localhost:~/sites/mapknitter$ mysql -u root -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

I don't seem to be able to get mysql to boot, and this is a basically fresh system; am I missing something? It is installed with Crouton, however, in a chroot, not actually a vanilla system. 

Perhaps I should ask on the crouton forums? Thanks!

---

### Post by jywarren on 2015-07-11
OMG -- as seems to happen, I figured this out shortly after posting. the "service" system routes to the ChromeOS, not to Ubuntu, so it just gets confused. Mysql can be manually started with `sudo mysqld &` --

[https://github.com/dnschneid/crouton/issues/217](https://github.com/dnschneid/crouton/issues/217)

---

