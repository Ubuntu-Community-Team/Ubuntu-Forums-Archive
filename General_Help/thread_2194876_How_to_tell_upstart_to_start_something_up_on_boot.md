---
title: "How to tell upstart to start something up on boot"
date: 2013-12-21
forum: General Help
---

### Post by seanmoir99 on 2013-12-21
I was just wondering as systemd uses systemctl

---

### Post by buzzingrobot on 2013-12-21
The Upstart cookbook is here: [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/).

Look in /etc/init for examples.  For instance, here's the file that starts cron:```


# cron - regular background program processing daemon
#
# cron is a standard UNIX program that runs user-specified programs at
# periodic scheduled times

description    "regular background program processing daemon"

start on runlevel [2345]
stop on runlevel [!2345]

expect fork
respawn

exec cron

```

---

