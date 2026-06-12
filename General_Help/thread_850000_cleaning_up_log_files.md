---
title: "cleaning up log files"
date: 2008-07-05
forum: General Help
---

### Post by rmvg on 2008-07-05
I am having problems with my log files they have become huge.  I have several programs that dump tons of stuff to the logs have a couple of questions.

I have setup bandwidth monitoring using webmin and it makes the logs very large.  Why do things get logged in so many places? i see the bandwidth stuff in 
/var/log/bandwith
/var/log/syslog
/var/log/kernel

also in dmesg

I do nightly remote backups and this amount redundant constantly changing data is costing me alot of money.

Please how do i stop these programs from spewing logfiles everywhere.

ps i am running ubuntu 6.06.2 LTS server

---

### Post by dcstar on 2008-07-05
> **rmvg said:**
> I am having problems with my log files they have become huge.  I have several programs that dump tons of stuff to the logs have a couple of questions.

I have setup bandwidth monitoring using webmin and it makes the logs very large.  Why do things get logged in so many places? i see the bandwidth stuff in 
/var/log/bandwith
/var/log/syslog
/var/log/kernel

also in dmesg

I do nightly remote backups and this amount redundant constantly changing data is costing me alot of money.

Please how do i stop these programs from spewing logfiles everywhere.

ps i am running ubuntu 6.06.2 LTS server

```
man logrotate
```

---

### Post by rmvg on 2008-07-05
Could you please be a little more specific I do not see how rotating the logs can stop all the duplicate triplicate log enteries

---

### Post by trevelyn on 2008-11-12
did you find a result?  maybe you can simply write a perl script or even a bash script with the "sort -u" command and argument and stick in in as a cron job?

---

