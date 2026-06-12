---
title: "How can I stop cron from logging to syslog?"
date: 2008-01-30
forum: General Help
---

### Post by Rednarb on 2008-01-30
Is there a way to stop cron from logging to syslog?

TIA,

Eric

---

### Post by ayoli on 2008-01-30
> **Rednarb said:**
> Is there a way to stop cron from logging to syslog?

TIA,

Eric
maybe you can try to edit this file (make a backup copy before incase you want to restore the original) :
```
sudo cp /etc/syslog.conf /etc/syslog.conf.backup
sudo gedit /etc/syslog.conf
```
and change this line : 
```
*.*;auth,authpriv.none          -/var/log/syslog
```
with:
```
*.*;auth,authpriv.none,cron.!info,cron.!notice          -/var/log/syslog
```
and then restart syslog:
```
sudo /etc/init.d/sysklogd restart
```
and see if it works.

---

### Post by Rednarb on 2008-01-30
Worked great, thanks! I was expecting to change a cron config, not a syslog config... always another way to skin the cat...

---

### Post by ayoli on 2008-01-30
> **Rednarb said:**
> Worked great, thanks! I was expecting to change a cron config, not a syslog config... always another way to skin the cat...

glad that it works :)
btw it is not really a good idea since you will not see anymore if you're own cron jobs are running.

---

### Post by Goobie81 on 2008-04-09
Well you should only be interested when you first set it up. Just avoid redirecting the output of the command and check your mailbox (if u previously muted the output). Once it's working, you can re-mute it

IMO Logging to syslog on every cron execution is excessive. If you want evidence of the job, send the output of the command to a log

---

