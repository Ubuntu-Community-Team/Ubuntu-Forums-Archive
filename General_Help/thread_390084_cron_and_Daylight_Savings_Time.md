---
title: "cron and Daylight Savings Time"
date: 2007-03-21
forum: General Help
---

### Post by noris2go on 2007-03-21
Hi,

I noticed that my Ubuntu cron is behind one hour on daily/weekly/monthly jobs after the Daylight Savings Time is in effect, although the system is properly updated with the new rules (the 'date' command shows the proper time). The server is using UTC clock.

Is this an existing bug ? Does cron use a different mechanism to compute the time ?

Thank you.

---

### Post by dcstar on 2007-03-21
> **noris2go said:**
> Hi,

I noticed that my Ubuntu cron is behind one hour on daily/weekly/monthly jobs after the Daylight Savings Time is in effect, although the system is properly updated with the new rules (the 'date' command shows the proper time). The server is using UTC clock.

Is this an existing bug ? Does cron use a different mechanism to compute the time ?

Thank you.

I presume you set up a job to run at a certain date when DST wasn't in use?

If so, then Cron is probably using that time reference to run its jobs, it may change after a reboot but that is probably because the reference time offset that Cron will use will then change.

Restarting the Cron daemon may cause it to pick up the new DST time offset without a reboot.

---

### Post by noris2go on 2007-03-22
The daily/weekly/monthly jobs are part of the standard etc/crontab file configuration. I have restarted the cron ("/etc/init.d/cron restart") more than couple times and even restarted the machine but still with no luck. The daily job is configured to run at 6:30 and it does run at 7:30. I did not look at the internals of the cron to see how it finds the timezone offset so I thought I'll ask here.

Thank you.

---

### Post by noris2go on 2007-03-26
I figured it out. It was not cron running my jobs but anacron that is configured in /etc/cron.d to run at 7:30 (crontab had the job set at 6:30 but only if anacron was not present). So everything is OK, no problem here.

---

