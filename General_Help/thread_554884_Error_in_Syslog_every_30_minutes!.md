---
title: "Error in Syslog every 30 minutes!"
date: 2007-09-19
forum: General Help
---

### Post by JCorrea920 on 2007-09-19
My system log shows an error every 30 minutes of a CRON command that is _[COLOR="Red"]NOT[/COLOR]_ listed under 

```
sudo crontab -e
```

my /var/log/syslog:

```
Sep 14 11:39:01 server1 /USR/SBIN/CRON[16248]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -omin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
```

I tried google and found nothing. Has anyone seen this before?

jcorrea920

Dell PowerEdge SC420
Ubuntu 6.06 LTS Server
kernel 2.6.15-23-386

---

### Post by apetresc on 2007-09-19
Why do you think this is an error? As far as I know, this is a perfectly normal PHP maintenance. The thread I found [here](http://www.linuxforums.org/forum/linux-security/71934-server-transmitting.html) seems to support my theory (see the last post).

For what it's worth, my syslog shows these same entries. I really think it's normal.

---

