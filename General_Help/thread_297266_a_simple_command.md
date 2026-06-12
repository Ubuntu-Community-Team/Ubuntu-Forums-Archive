---
title: "a simple command"
date: 2006-11-10
forum: General Help
---

### Post by satimis on 2006-11-10
Hi folks,

ubuntu-6.06-LAMP-server-amd64

Instead of running;
$ sudo /etc/init.d/mysql status
$ sudo /etc/init.d/apache2 status
etc respectively.

to find out whether they are running.  Is there a simple command to list the status of all applications collectively.

$ ps aux
lists all prcocesses which is not an ideal command for my application.

TIA

B.R.
satimis

---

### Post by taurus on 2006-11-10
I guess "ps -A" is not what you look for!!!

---

### Post by satimis on 2006-11-10
Hi taurus,

Tks for your advice.

> I guess "ps -A" is not what you look for!!!
Sorry, no.

$ ps -A | grep postfix
$ ps -A | grep apache2
both without printout.  They are running on the server.

Tks

B.R.
satimis

---

### Post by taurus on 2006-11-10
Are you trying to determine which daemon is running on your server?

---

### Post by satimis on 2006-11-10
> **taurus said:**
> Are you trying to determine which daemon is running on your server?
Hi taurus,

I expect to find out their running status, running or died, rather than running a command to detect each of them respectively.  At boot the text scrolling displays all of them.  After working a while I expect to find out their current status.

Tks

B.R.
satimis

---

### Post by taurus on 2006-11-10
Well, "ps -A" shows you everything is running on your machine so if you don't see it on that list, then it is not running...

---

### Post by satimis on 2006-11-10
> **taurus said:**
> Well, "ps -A" shows you everything is running on your machine so if you don't see it on that list, then it is not running...
Hi taurus,

I got it.

$ sudo /etc/init.d/mysql status```

/usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.22, for pc-linux-gnu on x86_64
Copyright (C) 2000 MySQL AB & MySQL Finland AB & TCX DataKonsult AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version          5.0.22-Debian_0ubuntu6.06.2-log
Protocol version        10
Connection              Localhost via UNIX socket
UNIX socket             /var/run/mysqld/mysqld.sock
Uptime:                 2 hours 44 min 51 sec

Threads: 1  Questions: 122  Slow queries: 0  Opens: 0  Flush tables: 1  Open tables: 17  Queries per second avg: 0.012
```

$ ps -A | grep mysql```

 4022 ?        00:00:00 mysqld_safe
 4086 ?        00:00:00 mysqld

```

Tks.

What are;```

 4022 ?
 4086 ?  

```
PID ???

B.R.
satimis

---

### Post by taurus on 2006-11-10
Yip.  Those are the process IDs.  In other words, if you want to kill mysqld, you would do something like this in a terminal.

```
sudo kill -9 4086
```

---

### Post by satimis on 2006-11-11
> **taurus said:**
> Yip.  Those are the process IDs.  In other words, if you want to kill mysqld, you would do something like this in a terminal.

```
sudo kill -9 4086
```Noted with tks.

satimis

---

