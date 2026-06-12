---
title: "Cron only working for some users"
date: 2007-08-15
forum: General Help
---

### Post by RedTiger84 on 2007-08-15
Hello,

I want to use cron to backup my postgres database every night. Due to security settings, only the user postgres can access the complete database, so this user has to run the backup script. The script works well when logging in with the postgres user and executed on the command line. But it seems not to be called at all with cron.

Cron is working for my regular user on the same box, but at user postgres, even the following line in his crontab produces nothing:
* * * * * echo "TEST" >> /var/lib/postgres/crontest.log

File is existant and accessible for this user.

Is there any reason for this? Same line works on other users. Postgres user has userid below 1000, where normal users start. Is there any setting disallowing these users accessing cron? There is no cron.allow or cron.deny file. I am using Ubuntu 7.04

Thanks and regards,
 Christoph

---

### Post by scxtt on 2007-08-15
put the FULL path to echo into your test cron ... chances are that user doesn't have a good $PATH ...

also, not sure a full set of *s is a great idea - that may not be helping either ...

(if it's 8:29am and you're impatient ;))
30 8 * * * /bin/echo "TEST" >> /var/lib/postgres/crontest.log

---

### Post by RedTiger84 on 2007-08-15
Changed to the full path, but still no result. 

The backup script I am trying to use already held the full path and did not work, sorry I should have mentioned this before.

---

### Post by pmg on 2007-08-16
Check the syslog file (/var/log/syslog, or /var/log/syslog.0 for the prior one) and see if there are any entries for **cron**around the time the job should be running.

---

### Post by RedTiger84 on 2007-08-16
In /var/log/syslog it says:

Aug 16 13:42:01 hitman /USR/SBIN/CRON[8390]: (postgres) CMD (/bin/echo "TEST" >> /var/lib/postgres/crontest.log)
Aug 16 13:42:01 hitman /USR/SBIN/CRON[8389]: (postgres) MAIL (mailed 77 bytes of output but got status 0x0001 )

I don't have a mail service installed on this machine, is there a simple way to see the output generated here?

---

### Post by pmg on 2007-08-17
We can see that it really is trying to run the cron job,  It only tries to send mail from the cron job if there is stdout/stderr output, which could be the error message if the command failed.  Try writing to a file in /tmp, just to me sure there isn't something you missed with the file permissions.

---

