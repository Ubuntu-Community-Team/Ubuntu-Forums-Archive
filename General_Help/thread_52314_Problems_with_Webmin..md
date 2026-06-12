---
title: "Problems with Webmin."
date: 2005-07-27
forum: General Help
---

### Post by Maxplayer14 on 2005-07-27
Ok, I have just installed ubuntu 2 days ago.  Never used Debian before, but I am hooked only after those 2 days.  Anyway, last night I was working on my ubuntu box from home (its at work) through webmin and ssh.  I did a reboot and webmin wouldn't come back up.  I tried everything I could think of.  I had webmin working through ports 20 and 10000.   But since that reboot it doesn't seem to be working at all.  Like its not even starting, although it says it is.

I try to restart the service.  I get this

```
root@jdog:/ # /etc/init.d/webmin start
Starting webmin: webmin.
root@jdog:/ # /etc/init.d/webmin restart
Restarting webmin: start-stop-daemon: warning: failed to kill 10324: No such process
webmin.
root@jdog:/ #
```

---

### Post by Maxplayer14 on 2005-07-27
webmin config

```
port=10000
host=jdog
addtype_cgi=internal/cgi
realm=Webmin Server
logfile=/var/log/webmin/miniserv.log
pidfile=/var/run/webmin.pid
logtime=168
ssl=1
env_WEBMIN_CONFIG=/etc/webmin
env_WEBMIN_VAR=/var/log/webmin
logout=/etc/webmin/logout-flag
listen=10000
userfile=/etc/webmin/miniserv.users
keyfile=/etc/webmin/miniserv.pem
libwrap=
alwaysresolve=1
blockhost_time=300
no_pam=0
logouttime=25
passdelay=1
session=1
blockhost_failures=3
syslog=1
log=1
logclear=
loghost=1
ppath=
atboot=1
denyfile=\.pl$
extraroot_0=/usr/local/share/webmin
preroot=debiantheme
root=/usr/share/webmin-1.220
mimetypes=/usr/share/webmin-1.220/mime.types
root=/usr/share/webmin-1.220
mimetypes=/usr/share/webmin-1.220/mime.types
passwd_file=/etc/shadow
passwd_uindex=0
passwd_pindex=1
passwd_cindex=2
passwd_mindex=4
passwd_mode=0
sockets=*:20
pam_conv=

```

---

