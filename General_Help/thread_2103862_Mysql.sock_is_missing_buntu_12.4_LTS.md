---
title: "Mysql.sock is missing buntu 12.4 LTS"
date: 2013-01-11
forum: General Help
---

### Post by Raafat1991 on 2013-01-11
Hi everyone....mysql.sock is missing i know this problem is common but also (after i have searched about 2 weeks) i have known  there is no a general solution for that problem .

So is there any an idea any soluation ?

thank you.

---

### Post by Raafat1991 on 2013-01-12
Please guys help me...i have important data

---

### Post by steeldriver on 2013-01-12
what command are you trying to run, and what is the exact error message?

have you checked that the mysql service is actually running?

```
service mysql status
```

---

### Post by Raafat1991 on 2013-01-12
> **steeldriver said:**
> what command are you trying to run, and what is the exact error message?

have you checked that the mysql service is actually running?

```
service mysql status
```

My command : 

```
mysql -uroot -p

```

the output :

```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

Also :

```
service mysql status

```

the output :

```
mysql stop/waiting

```

Also :

```
sudo /etc/init.d/mysql start
```

the output :

```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
start: Job failed to start

```


thank you.......

---

### Post by Raafat1991 on 2013-01-13
Come guys....please

---

### Post by steeldriver on 2013-01-13
AFAIK the correct command to start the server is now

```
sudo service mysql start
```but if it can't start for some reason then sometimes the easiest way to fix that is to reconfigure you installation

```
sudo dpkg-reconfigure mysql-server-5.5
```where 5.5 is the version installed on your system, which you can find e.g. by doing

```
dpkg -l | grep mysql-server
```

---

### Post by Raafat1991 on 2013-01-13
> **steeldriver said:**
> AFAIK the correct command to start the server is now

```
sudo service mysql start
```but if it can't start for some reason then sometimes the easiest way to fix that is to reconfigure you installation

```
sudo dpkg-reconfigure mysql-server-5.5
```where 5.5 is the version installed on your system, which you can find e.g. by doing

```
dpkg -l | grep mysql-server
```

Hi...after executing this command :
```
sudo dpkg-reconfigure mysql-server-5.5
```

this what i got :

```
130113 19:52:58 [ERROR] Unknown collation: 'utf8'
130113 19:52:58 [ERROR] Aborting

130113 19:52:58 [Note] /usr/sbin/mysqld: Shutdown complete

start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
```

then i decided to delete some lines of my.cnf file and all thing correctly go



Many thanks for everyone help me or tried that....

---

