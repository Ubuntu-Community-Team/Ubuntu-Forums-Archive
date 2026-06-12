---
title: "klogd using high % of cpu"
date: 2005-09-01
forum: General Help
---

### Post by Dummies102 on 2005-09-01
I just noticed that all of a sudden my computer has been very slow. I loaded up the system monitor and it says that klogd is using 45-50% of my cpu (athlon xp 1800+). You'll all have to excuse me if I don't post any diagnostics, I wouldn't know what to put.

What has happened recently is this:
I no longer have an ethernet connection on my computer and thus no internet. I noticed the kern.log, message, and system log files were getting huge very fast. they were a combined total of 10GB before I deleted them and routed the logging to /dev/tty8
I haven't been able to read the logs because they've been so big (each reaching ~200MB within 10 minutes of idleness). I have noticed strange errors that seem to repeat though. I can't remember what they say but I will post if I see one again. It was something like "eth0: can't communicate to pci"

The only other thing that has happened is that I installed ivtv and a hauppauge winTV 250 card.

Thanks

---

### Post by Dummies102 on 2005-09-01
One more thing, syslogd is running with ~19% cpu usage and whatever dd is using 30-40ish

---

### Post by Dummies102 on 2005-09-02
bump

---

### Post by arnieboy on 2005-09-02
[QUOTE=Dummies102]bump[/QUOTE]
install BUM (boot up manager) . when u open up BUM, u will be able to see which services are configured to start up at boot time. u can uncheck klogd if thats clogging up your comp, and also disable other services which u probably dont need and are taking up too much cpu time and RAM.
BUM can be found at
[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

