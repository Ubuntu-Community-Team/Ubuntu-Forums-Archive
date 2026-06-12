---
title: "[SOLVED] How can I  automatically run a command line every 8 hours?"
date: 2008-04-19
forum: General Help
---

### Post by Tsi99 on 2008-04-19
How can I  automatically run a command line every 8 hours?

Thanks,
Matt

---

### Post by Rinzwind on 2008-04-19
Check 'crontab'

[http://www.pantz.org/software/cron/croninfo.html](http://www.pantz.org/software/cron/croninfo.html)

> Cron is a daemon that executes scheduled commands. Cron is started automatically from /etc/init.d on entering multi-user runlevels. Cron searches its spool area (/var/spool/cron/crontabs) for crontab files (which are named after accounts in /etc/passwd); crontabs found are loaded into memory. Note that crontabs in this directory should not be accessed directly - the crontab command should be used to access and update them.

Cron also reads /etc/crontab, which is in a slightly different format (see crontab(5)). Additionally, cron reads the files in /etc/cron.d.

Cron then wakes up every minute, examining all stored crontabs, checking each command to see if it should be run in the current minute. When executing commands, any output is mailed to the owner of the crontab (or to the user named in the MAILTO environment variable in the crontab, if such exists). The children copies of cron running these processes have their name coerced to uppercase, as will be seen in the syslog and ps output.


Every 8 hours means @ 8:00 and @ 16:00 and @ 0:00 :)

---

### Post by ibutho on 2008-04-19
You can do that with cron. Take a look [here]("https://help.ubuntu.com/community/CronHowto") for more info.

---

### Post by Tsi99 on 2008-04-19
Thanks

---

