---
title: "Out of Disk Space due to syslog being several hundred GB"
date: 2018-11-25
forum: General Help
---

### Post by psyoma on 2018-11-25
I´m using Ubuntu 18:10 Cuttlefish.

I logged in this morning and was greeted with the message that I was out of disk space. Disk analyzer showed me that my log folder was 419 GB, with a syslog of 263 GB and syslog.1 of 151 GB.

As far as I can tell it´s the same error over and over again. 

```
Nov 25 00:00:23 cosmic update-notifier.desktop[4520]: [8273:8273:0100/000000.602009:ERROR:zygote_linux.cc(247)] Error reading message from browser: Socket operation on non-socket (88)
Nov 25 00:00:23 cosmic update-notifier.desktop[4520]: [8273:8273:0100/000000.602017:ERROR:zygote_linux.cc(247)] Error reading message from browser: Socket operation on non-socket (88)
Nov 25 00:00:23 cosmic update-notifier.desktop[4520]: [8273:8273:0100/000000.602026:ERROR:zygote_linux.cc(247)] Error reading message from browser: Socket operation on non-socket (88)
Nov 25 00:00:23 cosmic update-notifier.desktop[4520]: [8273:8273:0100/000000.602034:ERROR:zygote_linux.cc(247)] Error reading message from browser: Socket operation on non-socket (88)
Nov 25 00:00:23 cosmic update-notifier.desktop[4520]: [8273:8273:0100/000000.602042:ERROR:zygote_linux.cc(247)] Error reading message from browser: Socket operation on non-socket (88)
```

---

### Post by TheFu on 2018-11-25
Is logrotate working with appropriate settings?  logrotate can be set to limit the size of each file and rotate when that size is reached while retaining X number of logs 1, 5, 20, 300 ... whatever.  /etc/logrotate.d/  probably has multiple examples you can check out.

Which exact files are growing? Just syslog or do the others grow too?  
Do you have syslog setup to suppress repeat messages?

Googling seems to show this as a google chrome problem.  Shutdown chrome and use chromium to see of the problem isn't solved.

Of course, you'll probably want to delete the older, larger, files in /var/log/.

---

