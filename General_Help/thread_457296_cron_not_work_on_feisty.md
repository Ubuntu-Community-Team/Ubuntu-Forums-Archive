---
title: "cron not work on feisty"
date: 2007-05-28
forum: General Help
---

### Post by biasquez on 2007-05-28
hi guys, i found a bug about cron on feisty. exactly i have my /etc/crontab right like commands, but i have this.

/etc/init.d/cron restart
 * Restarting periodic command scheduler crond
   ...done.


tail /var/log/syslog

 localhost /usr/sbin/cron[25451]: (CRON) INFO (pidfile fd = 3)
 localhost /usr/sbin/cron[25452]: (CRON) STARTUP (fork ok)
 localhost /usr/sbin/cron[25452]: (CRON) INFO (Skipping @reboot jobs -- not system startup)

so, cron doesn't work, that is commands in crontab aren't execute.

---

### Post by krismatth3 on 2007-05-28
Why do you say cron isn't working? I do not believe that can be deduced from the output you posted.

@reboot jobs are just that - they happen at reboot. Not at cron startup.

---

### Post by biasquez on 2007-05-30
cron not work, i sure, commands my crontab aren't execute. on edgy all works. i don't know what i can do to fix this problem.

---

### Post by EndPerform on 2007-05-30
Open a terminal, and type the following: 

```
crontab -l
```

Then post the output here so we can see what you have in your crontab.  I have cron jobs on my Feisty machine and it's working fine.

---

