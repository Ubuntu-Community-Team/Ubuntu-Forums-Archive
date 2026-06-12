---
title: "rooted ? omgbbq"
date: 2007-07-13
forum: General Help
---

### Post by cytg on 2007-07-13
So i went to bed around 0200 hours, leaving the pc on .. when i get up around 0900, to my surprise the pc was turned off. Figured it has crashed and just booted it again (but hey, this linux stuff aint supposed to crash like that unless theres a hardware fault right?).
Then just now 1900 hours i check the systemlog
under messages i see this
Jul 13 07:35:45 uber-c syslogd 1.4.1#20ubuntu4: restart.
And its a fact that i was asleep at this point.(but if its a restart then why was the pc powered down?)

syslog
Jul 13 07:35:45 uber-c syslogd 1.4.1#20ubuntu4: restart.
Jul 13 07:35:45 uber-c anacron[5826]: Job `cron.daily' terminated
Jul 13 07:35:45 uber-c anacron[5826]: Normal exit (1 job run)
Jul 13 07:52:25 uber-c -- MARK --


i dont quite know what to make of auth.log
Jul 13 00:17:01 uber-c CRON[31615]: (pam_unix) session opened for user root by (uid=0)
Jul 13 01:17:01 uber-c CRON[447]: (pam_unix) session opened for user root by (uid=0)
Jul 13 02:17:01 uber-c CRON[1451]: (pam_unix) session opened for user root by (uid=0)
Jul 13 03:17:01 uber-c CRON[2311]: (pam_unix) session opened for user root by (uid=0)
Jul 13 04:17:01 uber-c CRON[3117]: (pam_unix) session opened for user root by (uid=0)
Jul 13 05:17:01 uber-c CRON[3941]: (pam_unix) session opened for user root by (uid=0)
Jul 13 06:17:01 uber-c CRON[4761]: (pam_unix) session opened for user root by (uid=0)
Jul 13 06:25:01 uber-c CRON[4877]: (pam_unix) session opened for user root by (uid=0)
Jul 13 06:25:01 uber-c CRON[4877]: (pam_unix) session closed for user root
Jul 13 07:17:01 uber-c CRON[5605]: (pam_unix) session opened for user root by (uid=0)
Jul 13 07:30:01 uber-c CRON[5801]: (pam_unix) session opened for user root by (uid=0)
Jul 13 07:30:02 uber-c CRON[5801]: (pam_unix) session closed for user root
Jul 13 09:48:47 uber-c gdm[5156]: (pam_unix) session opened for user uber by (uid=0)

0948 must have been when i booted it up manually
but the rest seems to be some hourly cronjob requiring root priv ... whatever it is!! (update checks?)


Any ideas ? very very welcome ;)

---

### Post by pbaumgar on 2007-07-13
the entries in /var/log/messages are from the system crontab executing it's scheduled cron entries found in /etc/crontab.  You probably don't have any task set up, but it's executing because cron is running and executing cron.daily, cron.weekly, etc.  Anacron is probably set to restart daily at 07:30 or so.. look in /etc/cron.d/anacron.

---

