---
title: "Ubuntu hangs due to php"
date: 2007-12-31
forum: General Help
---

### Post by adityam on 2007-12-31
Hi,

I am running ubuntu Gusty on a Lenovo thinkpad T61. Recently, I have found that ubunutu occasionally hangs. Looking at the logs (/var/log/syslog) I found that it is hanging on the command

```
 /USR/SBIN/CRON[10359]: (root) CMD (  [ -d /var/lib/php5  ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xa rgs -r -0 rm)

```

(This is always the command in the syslog file before a manual reboot). Any idea how to debug further.

I am guessing that this is being run because I have apache and mediawiki installed, but I am not sure.

Aditya

---

### Post by adityam on 2007-12-31
Looking at the logs in more detail I found that there was about 10 to 15 minutes gap between the above php line and the reboot. So, reboot is being caused by some other factor. 

For now, I have switched off compiz to see if that makes things more stable

---

### Post by scxtt on 2007-12-31
what in /etc/crontab or crontab -e (if you're root)? ... looks like a cron that's trying to do some php-related cleanup ... could also be in one of the cron directories ...

edit: found it ... it's a file called /etc/cron.d/php5

i have it, but don't have any issues ...

---

