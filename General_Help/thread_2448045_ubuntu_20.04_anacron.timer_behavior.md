---
title: "ubuntu 20.04 anacron.timer behavior"
date: 2020-07-31
forum: General Help
---

### Post by jfaberna on 2020-07-31
I have a fresh install of Ubuntu Desktop 20.04 and added my daily jobs scripts to /etc/cron.daily.  They email me when done so I know the time that they complete. I see that these are running at around 7:35am everyday.

When I check /lib/systemd/system/anacron.timer I see:
```
[Unit]
Description=Trigger anacron every hour

[Timer]
OnCalendar=*-*-* 07..23:30
RandomizedDelaySec=5m
Persistent=true

[Install]
WantedBy=timers.target
```
I want to change my jobs to run at about 5:30am.  I'll use an override edit for that so I don't change the system file.  Can someone explain the syntax of the OnCalendar line.  I don't get what 07..23:30 means?  The 2 '.' after 07 confuses me.

---

### Post by dinkidonk on 2020-07-31
07..23:30 means that the timer is scheduled to run from 07 to 23:30: [docs]("https://www.freedesktop.org/software/systemd/man/systemd.time.html#").

---

### Post by jfaberna on 2020-07-31
> **dinkidonk said:**
> 07..23:30 means that the timer is scheduled to run from 07 to 23:30: [docs]("https://www.freedesktop.org/software/systemd/man/systemd.time.html#").

Thanks, but why would they want to run a daily set of tasks at a range of times?  To me, they run at 7:30 and then don't run again until the next day. I'm trying to decide whether my override time should be, OnCalendar=*-*-* 05..23:30  or OnCalendar=*-*-* 05:30:00.

Jim A

---

### Post by dinkidonk on 2020-07-31
7..23 means every hour from 7 to 23 - both inclusive. This means that the timer is repeated hourly from 7:30 to 23:30. In a terminal you could examine the output of:

```
systemd-analyze calendar *-*-* 07..23:30
```

and see what pops out :)

---

### Post by jfaberna on 2020-07-31
> **dinkidonk said:**
> 7..23 means every hour from 7 to 23 - both inclusive. This means that the timer is repeated hourly from 7:30 to 23:30. In a terminal you could examine the output of:

```
systemd-analyze calendar *-*-* 07..23:30
```

and see what pops out :)
Great! Now I just need to know how that affects cron.daily which is run by  anacron.  Is it that once the cron.daily list of scripts gets run they will not be run again that day? I would figure that if you told cron.daily's list of tasks to run a 7:30am then that would be it.  There must be either someone else using that systemd timer or some other reason.

---

### Post by dinkidonk on 2020-07-31
Even if anacron is launched multiple times during a day, the jobs in  the list are only executed once. I cannot see any problem in changing  the schedule from 07..23:30 to 05..23:30 if that is what you need. Look at the [manpage for anacron]("https://manpages.debian.org/buster/anacron/anacron.8.en.html") which describes how anacron works in details.

---

### Post by jfaberna on 2020-07-31
> **dinkidonk said:**
> Even if anacron is launched multiple times during a day, the jobs in  the list are only executed once. I cannot see any problem in changing  the schedule from 07..23:30 to 05..23:30 if that is what you need.
That's what I just did. We'll see what time it runs tomorrow.

Thanks.

---

