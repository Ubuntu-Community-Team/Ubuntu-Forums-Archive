---
title: "Failing to start MySQL server"
date: 2005-04-09
forum: General Help
---

### Post by Ces on 2005-04-09
Simply put, the command **mysqld_safe --user=mysql &** give
> Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[14543]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[14549]: ended

How can I get the server to stay up running? (*laughter* I managed to compile and run the latest version of PostgreSQL, but running an installed package of MySQL... :-|)

**mysql --version**: mysql  Ver 12.22 Distrib 4.0.23, for pc-linux-gnu (i386)

---

### Post by p!=f on 2005-04-09
So you use Ubuntu MySQL packages or did you compile MySQL on your own?

---

### Post by Ces on 2005-04-09
[QUOTE=p!=f]So you use Ubuntu MySQL packages or did you compile MySQL on your own?[/QUOTE]
 Ubuntu packages.

---

### Post by p!=f on 2005-04-09
In that case you should have start-up scripts installed. Check /etc/init.d/ for mysql presents. Start with
```

sudo /etc/init.d/mysql start

```
Does it help?

---

### Post by Ces on 2005-04-09
Thanks for the help, but it does not work due to some unknown reason.

```
$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
```

How do I locate the error log? I've tried with **locate**, **find**, **whereis**, and even **type mysql** to no avail.

---

### Post by p!=f on 2005-04-09
[QUOTE=Ces]Thanks for the help, but it does not work due to some unknown reason.

```
$ sudo /etc/init.d/mysql start
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
```

How do I locate the error log? I've tried with **locate**, **find**, **whereis**, and even **type mysql** to no avail.[/QUOTE]
Logs can be found in /var/log/ by default.
```

sudo tail /var/log/syslog

```
will show you last 10 lines of syslog
```

sudo tail -50 /var/log/syslog

```
will show you last 50 lines of syslog (you got the point ;))
```

sudo tail -f /var/log/syslog

```
will show you syslog as data are appended

or use gnome-system-log (can found in the GNOME menu, system)

---

### Post by Ces on 2005-04-09
```
sudo tail -40 var/log/syslog |grep '15:22'
Apr  9 15:22:43 localhost mysqld_safe[16261]: started
Apr  9 15:22:46 localhost mysqld[16264]: 050409 15:22:46 /usr/sbin/mysqld: Can't open file: 'host.MYI'. (errno: 142)
Apr  9 15:22:46 localhost mysqld[16264]: 050409 15:22:46 Fatal error: Can't open privilege tables: File '/usr/share/mysql/charsets/?.conf' not found (Errcode: 2)
Apr  9 15:22:46 localhost mysqld[16264]: 050409 15:22:46 Aborting
Apr  9 15:22:46 localhost mysqld[16264]:
Apr  9 15:22:46 localhost mysqld[16264]: 050409 15:22:46 /usr/sbin/mysqld: Shutdown Complete
Apr  9 15:22:46 localhost mysqld[16264]:
Apr  9 15:22:46 localhost mysqld_safe[16273]: ended
Apr  9 15:22:51 localhost /etc/init.d/mysql[16311]: 0 processes alive and '/usr/bin/mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf ping' resulted in
Apr  9 15:22:51 localhost /etc/init.d/mysql[16311]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Apr  9 15:22:51 localhost /etc/init.d/mysql[16311]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Apr  9 15:22:51 localhost /etc/init.d/mysql[16311]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Apr  9 15:22:51 localhost /etc/init.d/mysql[16311]:
```

(Hmmm... I guess I need to learn what all of this means some day.) After looking at the online MySQL manual I'm no wiser. Is there something I need to set up or change from Ubuntu's default tweakings?

---

### Post by p!=f on 2005-04-09
Looks like your MySQL is broken or you accidentaly deleted the important database.
Try to reinstall MySQL by
```

sudo apt-get --reinstall install mysql-server

```
if it doesn't work
```

sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server

```
Run 
```

dpkg -l | grep -v ^ii

```
and post the output here.

---

### Post by Ces on 2005-04-09
Thanks a lot!

The first step didn't work. Same error. Second step, a marvel! Thanks again. :)

---

### Post by Nolgthorn on 2005-09-23
AGHHHH! The second step worked for me too, plus I still have all my databases. Thank you. I have no idea why it stopped working in the first place.

---

### Post by infosys on 2008-05-19
I see this is in the archives, but this seems to be my exact issue, here is the output from "dpkg -l | grep -v ^ii":

infosys@perldesk:~$ dpkg -l | grep -v ^ii
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                 Description
+++-=====================================-=======================-============================================
infosys@perldesk:~$

Hope this helps, and hope somebody is monitorying this thread still.

---

