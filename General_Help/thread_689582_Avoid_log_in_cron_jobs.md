---
title: "Avoid log in cron jobs"
date: 2008-02-06
forum: General Help
---

### Post by jmvidalvia on 2008-02-06
Hi!
As I have a couple of cron jobs running every 5 minutes, my /var/log/auth.log is full of logs.
Is there any way to avoid logging for cron jobs?
Thanks a lot!

---

### Post by gsiliceo on 2008-02-06
System/Admin/Services
A couple of those are loggers.
Im not sure if this helps

---

### Post by jmvidalvia on 2008-02-07
Thanks!
But I am afraid I don't understand your answer.
I don't want to remove or stop any services: crond is ok, just need to avoid that every new log of cron is sent to /var/log
Thank you very much.

---

### Post by kpkeerthi on 2008-02-07
Here is what you need in your crontab:
```

30 02  *    *   *    /my/long/and/boring/job.sh > /dev/null 2>&1

```
It redirects anything that is sent from /my/long/and/boring/job.sh to the **bit bucket** (null device) and gets discarded

**PS:** It is usually a good idea to redirect your cron logs to somewhere (like /home/logs/my-cron.log) so you can investigate later should something go wrong.

---

### Post by jmvidalvia on 2008-02-07
Thank you very much.
I understand about sending to /dev/null every messages, but I am afraid it won't avoid the log messages:
```
Feb  7 09:09:01 ubuntu CRON[19162]: (pam_unix) session opened for user root by (uid=0)
Feb  7 09:09:01 ubuntu CRON[19162]: (pam_unix) session closed for user root
Feb  7 09:10:01 ubuntu CRON[19170]: (pam_unix) session opened for user jmd by (uid=0)
Feb  7 09:10:01 ubuntu CRON[19171]: (pam_unix) session opened for user root by (uid=0)
Feb  7 09:10:01 ubuntu CRON[19171]: (pam_unix) session closed for user root
Feb  7 09:10:07 ubuntu CRON[19170]: (pam_unix) session closed for user jmd

```
Am I right?
Thanks again!

---

### Post by andrew.46 on 2008-02-09
Hi:

> **jmvidalvia said:**
> Hi!
As I have a couple of cron jobs running every 5 minutes, my /var/log/auth.log is full of logs.
Is there any way to avoid logging for cron jobs?
Thanks a lot!

Have you had a look at the settings in /etc/syslog.conf ?

              Andrew

---

### Post by jmvidalvia on 2008-02-09
Thank you very much!
> **andrew.46 said:**
> Hi:
Have you had a look at the settings in /etc/syslog.conf ?
              Andrew

This seems to be an interesting clue..
My /etc/syslog.conf looks like.
```
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

```

Regarding ```
#cron.*                         /var/log/cron.log
``` I never commented it, so there must be somwhere to configure the logs for cron.
Y checked at /etc and didn't see any cron.conf or similar, just these:
```
server:/var/log# ls /etc/cron*
/etc/crontab

/etc/cron.d:
php5

/etc/cron.daily:
apache2  apt  aptitude	bsdmainutils  exim4-base  logrotate  man-db  ntp  samba  standard  sysklogd

/etc/cron.hourly:

/etc/cron.monthly:
scrollkeeper  standard

/etc/cron.weekly:
man-db	sysklogd

```
Any idea?
Thanks again!

---------------------------------------------
Edited: Should I uncomment ```
#cron.*                         /var/log/cron.log
```?

---

### Post by andrew.46 on 2008-02-10
Hi,

 I suspect that anything written to auth.log is not actually recording the cron jobs themselves but recording security related events *related* to the running of the cron jobs.

 You would be best to leave most of the system logging alone but if the buildup of logs annoys you it is an easy matter to make them backup and rotate a little more frequently. This is controlled by /etc/logrotate.conf and I note the default settings (in Hardy):

> # see "man logrotate" for details

# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

So you can see here that log files by default are kept for a week before being backed up. These backups are kept for 4 weeks before being discarded. A new log file is created to replace the backed up file and the old file is *no*t compressed with gzip. logrotate also checks /etc/logrotate.d for settings.

All of these settings can be altered at your will and this might be better than actually *turning off* any of the system logs. As a side note I see that cron logging is turned off by default in my system as well.

              Andrew

---

### Post by jmvidalvia on 2008-02-10
Yes, good advice.
Many thanks!

---

