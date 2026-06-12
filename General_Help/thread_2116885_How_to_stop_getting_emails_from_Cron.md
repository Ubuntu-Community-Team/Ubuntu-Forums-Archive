---
title: "How to stop getting emails from Cron"
date: 2013-02-17
forum: General Help
---

### Post by neo1691 on 2013-02-17
Hi. 

I have setup a ssmtp server with my gmail username and password.

After that i have been getting constant emails from my laptop to my gmail.

Here the mails.

The first one is somewhat like this:

The Subject is 
```
Cron <root@Innovator> [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
```

The sender is 
root <anubhav1691@gmail.com>

The body of the text is 
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20100525/msql.so' - /usr/lib/php5/20100525/msql.so: cannot open shared object file: No such file or directory in Unknown on line 0
```

The Second mail is:
Subject:
```
Anacron job 'cron.daily' on Innovator
```

Sender is: Anacron <anubhav1691@gmail.com>

Body is:
```
/etc/cron.daily/logrotate:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
/etc/cron.daily/update-notifier-common:
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.270.orig.tar.gz
Installing from local file /tmp/tmphjHyVl.gz
Flash Plugin installed.
```

When I look in /etc/cron.d there are two files:
anacron  php5

The contents of php5 are as follows:
```
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete 
```

And when I go in /etc/cron.daily there are the following files
0anacron   bsdmainutils      man-db              standard
0anacron~  cracklib-runtime  mlocate             update-notifier-common
apache2    dpkg              passwd
apport     google-chrome     popularity-contest
apt        logrotate         samba

The contents of the file 0anacron are as follows
```
#!/bin/sh
#
# anacron's cron script
#
# This script updates anacron time stamps. It is called through run-parts
# either by anacron itself or by cron.
#
# The script is called "0anacron" to assure that it will be executed
# _before_ all other scripts.

test -x /usr/sbin/anacron || exit 0 >/dev/null 2>&1
anacron -u cron.daily >/dev/null 2>&1
```

I have also tried adding the string >/dev/null 2>&1 at the end of the php file (as described [HERE]("http://goo.gl/oDs3W"))but still i get the mails.

How do i stop from getting the mails.

---

### Post by SeijiSensei on 2013-02-17
Are you running something that uses PHP?  If not, I'd just delete anacron.php5 since it's not relevant to your installation.

If, however, you are running Apache with PHP5 installed, then your PHP installation is missing the msql.so module.  

```
/usr/lib/php5/20100525/msql.so: cannot open shared object file: No such file or directory
```

I suspect this script has been generating this same error for months; you just didn't see the results because you didn't have an SMTP server running.

Now I haven't seen anyone use [mSQL]("http://php.net/manual/en/book.msql.php") in a very long time. Are you actually using this database system?

Is this copy of PHP installed from the repositories, or was it compiled separately?

---

### Post by neo1691 on 2013-02-18
Yes i am using php5 and mysql on localhost! 
Its kinda important for me.
So i cannot delete that php scripts!

---

