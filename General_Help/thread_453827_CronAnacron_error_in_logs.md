---
title: "Cron/Anacron error in logs"
date: 2007-05-24
forum: General Help
---

### Post by pdowling on 2007-05-24
Hey folks,

I was trying to add something to the daily cron run.  Simple script that copies some files around (I can provide details if needed).

Getting this error sequence in my syslog...

May 23 22:59:18 peter-main anacron[569]: Anacron 2.3 started on 2007-05-23
May 23 22:59:18 peter-main anacron[569]: Can't open timestamp file for job cron.daily: Permission denied
May 23 22:59:18 peter-main anacron[569]: Aborted
May 23 23:05:16 peter-main cron[706]: (CRON) DEATH (can't open or create /var/run/crond.pid: Permission denied)
May 23 23:05:22 peter-main cron[708]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 6137: Resource temporarily unavailable)
May 23 23:05:43 peter-main cron[735]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 6137: Resource temporarily unavailable)

Here is what I did.  Made my script.  Marked it executable (755).  Put the file in /etc/cron.daily

If I run it manually from a terminal in that folder it works.

Any thoughts?

Thanks,

Peter

---

### Post by gustavoberman on 2007-05-24
maybe your cron is not running correctly?
have you tried to reload cron?

if you take out that script from /etc/cron.daily, does cron give any error?

---

### Post by pdowling on 2007-05-25
How would I check if cron is running correctly?  It seems to be doing something with log files, but other than that I can't tell.

I could try removing the file, but since I didn't edit any files and just put the script there I'm not sure why I'd get errors taking it out.

I was basically following the instructions [COLOR="Blue"][here]("http://doc.ubuntu.com/ubuntu/install/i386/ch08s02.html#id2528250")[/COLOR] which said to just put the executable script into the /etc/cron.daily folder.

Thanks again,

Peter

---

