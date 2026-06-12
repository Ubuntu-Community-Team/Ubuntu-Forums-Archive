---
title: "Slimserver and XAMPP"
date: 2007-06-25
forum: General Help
---

### Post by ImpelGD on 2007-06-25
Hi. I'm running Ubuntu 7.04, and have had Slimserver running okay for a few days now.

I've just extracted XAMPP and upon trying to start it I get:
```
user@emperor:~$ sudo /opt/lampp/lampp start
Password:
Starting XAMPP for Linux 1.6.2...
/opt/lampp/share/lampp/phpstatus: line 4: /opt/lampp/bin/php: No such file or directory
XAMPP: Starting Apache with SSL ...
XAMPP: Error 127! Couldn't start Apache!
XAMPP: Starting diagnose...
XAMPP: Sorry, I've no idea what's going wrong.
XAMPP: Please contact our forum http://www.apachefriends.org/f/
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP: /opt/lampp/lampp: line 302: /opt/lampp/sbin/proftpd: No such file or directory
XAMPP: Error 127! Couln't start ProFTPD!
XAMPP for Linux started.
```
The lines that give the "No such file or directory" errors seem to be present.

I assume "XAMPP: Another MySQL daemon is already running." is because Slimserver too uses MySQL. I've tried to stop slimserver but cannot:
```
user@emperor:~$ sudo slimserver stop
2007-06-25 12:12:04.0042 ERROR: Cannot write to preferences file /home/user/slimserver.pref, any changes made will not be preserved for the next startup of the server

/home/user/Cache/my.cnf: Permission denied at /usr/share/perl5/Slim/Utils/MySQLHelper.pm line 178.
2007-06-25 12:12:04.2247 Use of uninitialized value in sprintf at /usr/share/perl5/Slim/Utils/MySQLHelper.pm line 467.
```

:( I is stuck. Thanks for reading and any help you can give.

Edit: I should clarify that I need to have both Slimserver and Apache, PHP and MySQL (via XAMPP) running at the same time.

---

### Post by LaRoza on 2007-06-25
You can not have more than one server using the same socket. I do not know about Slimserver, but Apache and MySQL will use ports 80 and 3306.

---

### Post by ImpelGD on 2007-06-25
Thanks. I've read that Slimservers version of MySQL listens on port 9002, and the web interface is on 9000.

I found [this forum thread at XAMPP]("http://www.apachefriends.org/f/viewtopic.php?t=24382"). There seems to be two ways around the issue: uninstalling all Apache/MySQL servers or installing ia32-libs. I chose the latter, and it seems to be working.

:)

---

