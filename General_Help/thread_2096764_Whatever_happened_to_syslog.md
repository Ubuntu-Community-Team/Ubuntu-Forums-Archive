---
title: "Whatever happened to syslog?"
date: 2012-12-20
forum: General Help
---

### Post by pwabrahams on 2012-12-20
My **/var/log/syslog** file is empty, and **logger foo** puts nothing into it.  What might have gone wrong?

---

### Post by tgalati4 on 2012-12-20
You have a perfectly running system.  

Is syslogd running?  Perhaps it was stopped and needs to be restarted.


tgalati4@tpad-Gloria7 ~/Desktop $ ps -ef | grep syslogd
syslog    2295     1  0 Dec01 ?        00:00:03 /sbin/syslogd -u syslog
tgalati4 17640 15454  0 19:31 pts/0    00:00:00 grep --colour=auto syslogd

sudo /etc/init.d/sysklogd restart

---

### Post by pwabrahams on 2012-12-20
I guess some system changes have snuck up on me.  There are at least three logging daemons around, it seems: syslogd, rsyslog, and syslog-ng.  It used to be that in a default-configured Kubuntu, the log was kept in **/var/log/syslog** (with history in **syslog.1**, etc.)  In such a system, **logger foo** would write **foo** to **/var/log/syslog**.

After reading your post, I installed syslog-ng.  That forced the removal of rsyslog, which I knew nothing about.  

What has happened to the logging components of Kubuntu?

---

### Post by SeijiSensei on 2012-12-20
On my Kubuntu 12.04 rsyslogd is running and writing to /var/log/syslog among others.  I'll agree that the logging is sparse, but I'm used to servers where more events are logged.  You can always run dmesg, though I'd pipe it to a file.  It overflows my Konsole session with the default 1000 lines of saved text.

The configurations for rsyslog (which it sounds like you removed) reside in /etc/rsyslog.conf and /etc/rsyslog.d/.  Mine look like this:

```

cd /etc
ls -ltr rsyslog*

-rw-r--r-- 1 root root 1263 Mar 30  2012 rsyslog.conf

rsyslog.d:
total 12
-rw-r--r-- 1 root root  311 Mar 17  2012 20-ufw.conf
-rw-r--r-- 1 root root 1655 Mar 30  2012 50-default.conf
-rw-r--r-- 1 root root  242 Apr 24  2012 postfix.conf

```

I apparently have Postfix installed which I probably did manually.  On a standard client installation you may not have that file.

---

