---
title: "Autostart MySQL 5.6 in 14.04?"
date: 2014-10-03
forum: General Help
---

### Post by riahc3 on 2014-10-03
Hello

Im having problems autostarting MySQL 5.6 in Ubuntu 14.04

How can I do it?

---

### Post by slickymaster on 2014-10-03
Could you be facing something like [this bug report]("https://bugs.launchpad.net/bugs/1312936").

---

### Post by riahc3 on 2014-10-03
Nope. Reviewed it and tested it and nothing.

Maybe a better guide that I should follow for this?

---

### Post by riahc3 on 2014-10-06
Syslog doesn't say much....

Oct  6 10:20:29 vm /etc/mysql/debian-start[1376]: Upgrading MySQL tables if necessary.
Oct  6 10:20:30 vm /etc/mysql/debian-start[1379]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Oct  6 10:20:30 vm /etc/mysql/debian-start[1379]: Looking for 'mysql' as: /usr/bin/mysql
Oct  6 10:20:30 vm /etc/mysql/debian-start[1379]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Oct  6 10:20:30 vm /etc/mysql/debian-start[1379]: This installation of MySQL is already upgraded to 5.6.19, use --force if you still need to run mysql_upgrade
Oct  6 10:20:30 vm /etc/mysql/debian-start[1403]: Checking for insecure root accounts.
Oct  6 10:20:30 vm /etc/mysql/debian-start[1409]: Triggering myisam-recover for all MyISAM tables

I need this solved...

---

### Post by matt_symes on 2014-10-06
Hi

Can you start mysql from the command line ?

```
sudo service mysql start
```

Is there anything in /var/log/mysql.log ?

Is there anything in ```
/var/crash
``` or ```
~/.cache/upstart/*crash*
```

I'm wondering if mysql is crashing after this trigger.

> Triggering myisam-recover for all MyISAM tables

Kind regards

---

