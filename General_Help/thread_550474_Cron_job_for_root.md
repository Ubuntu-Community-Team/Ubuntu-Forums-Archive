---
title: "Cron job for root"
date: 2007-09-13
forum: General Help
---

### Post by deets52 on 2007-09-13
My /var/log/auth.log file is logging a lot of the following entries at 17 minutes and 1 second after the hour (every hour).
Sep 13 19:17:01 rocket-serv CRON[4168]: (pam_unix) session opened for user root$
Sep 13 19:17:01 rocket-serv CRON[4168]: (pam_unix) session closed for user root

How can I find out what is causing this? I have looked in /etc/cron.hourly and found nothing. 

Thanks for your help.

---

### Post by scxtt on 2007-09-13
mine does it too, wouldn't worry about it ... try stopping the cron daemon and see if they stop ...

---

### Post by pmg on 2007-09-13
Look in /etc/crontab.  You'll probably find:
```
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly

```
which is what checks for and runs any scripts in /etc/cron.hourly once an hour.

---

