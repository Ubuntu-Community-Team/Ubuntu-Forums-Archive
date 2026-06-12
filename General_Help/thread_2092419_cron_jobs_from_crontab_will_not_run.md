---
title: "cron jobs from crontab will not run"
date: 2012-12-07
forum: General Help
---

### Post by Ortix on 2012-12-07
So I have a really simple crontab set up. I'm running flexget every 30 minutes.

I use this simple line:
MAILTO="myemail@hotmail.com"
30 * * * * flexget


However it does not seem to run at all. Well.. I set it to 1 minute and waited 15 minutes and I didn't receive any mail :lolflag:

But then again, I checked the flexget logs, and it didn't run. Is there any other log I can check for errors or something?

---

### Post by agillator on 2012-12-07
The first thing to do is to use the full path for the program. Cron does not use your environment but its own very limited one. You can change that, but the better thing to do is to always use complete paths and never rely on the PATH variable.

---

### Post by Ortix on 2012-12-09
Well I did that but still no effect. The cron is still not running. No email is being received and flexget is not being run

---

### Post by SeijiSensei on 2012-12-09
Which crontab is this?  /var/spool/cron/user or /etc/crontab?  The syntax is different if you use /etc/crontab:

```

* 1 * * * username command

```

/etc/crontab requires a username.  The ones placed in /var/spool/cron using the "crontab -e" command do not.

Which user is this running as?  Permissions problems?

Scan the log for errors using

```
sudo grep cron /var/log/syslog
```

---

### Post by Ortix on 2012-12-11
Well I am using crontab -e so with no username. I'm running it as "ortix" and NOT as root.

I looked at the syslog but that only gave me jobs which have been run by root.

It seems that nothing from my username is being run..

---

### Post by Habitual on 2012-12-11
```
...
30 * * * * /path/to/flexget
```

---

