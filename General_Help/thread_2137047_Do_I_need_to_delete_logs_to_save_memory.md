---
title: "Do I need to delete logs to save memory?"
date: 2013-04-19
forum: General Help
---

### Post by Psil0cybin on 2013-04-19
Sorry kind of a newb question, but since all log files are accessible, I was wondering 
Do these log files ever fill up and take up vast amount of space? Do they need to be deleted after specific periods of times?
Or do I just leave everything be and let Ubuntu take its course?
Thanks in advance,

---

### Post by matt_symes on 2013-04-19
Hi

Ubuntu runs log rotate. This will compress the log files after a period of time or when they reach a certain size. It will then delete them later.

Unless your logs are filling up really fast, leave them be. If they are filling up fast you can look to see why.

Kind regards

---

### Post by HermanAB on 2013-04-19
Read the man page.

/etc/logrotate.conf

---

### Post by tgalati4 on 2013-04-19
```
which logrotate
man logrotate
cat /etc/logrotate.conf
```

I've had a Dapper Drake (6.06) machine running continuously since 6.06 and I haven't had a problem with log files.  So *logrotate* is doing its job.

---

