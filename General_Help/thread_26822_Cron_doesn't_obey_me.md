---
title: "Cron doesn't obey me"
date: 2005-04-14
forum: General Help
---

### Post by Firetech on 2005-04-14
Although I've changed the hours in my /etc/crontab, the cron jobs still run at the same times.
I have restarted my machine since i edited crontab, but still nothing happens.

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
00 *    * * *   root    run-parts --report /etc/cron.hourly
25 3    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 3    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 3    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#
15 3    * * 4   jocke   /opt/machine-update -m
```
The hour of the run-parts jobs were earlier 6, and  the cron.daily jobs (especially updatedb, which I can hear)have since the beginning of my ubuntu installation been running at about 7:30-7:40 am

I edited the updatedb job a little, so that it write the output from 'date' to a file before running and after running, and that confirmed that it only runs at ~7:40

What can I do to make the cron jobs run at 4:XX am instead, so I don't wake up by hearing the computer?

**Edit:** After a little research, I found out that anachron should be the fault (if you watch the "test -x" commands, it is very plausible.
Because my computer is on 24/7 and thus don't need anacron, I just did a "dpkg --purge anacron".

---

### Post by Firetech on 2005-04-14
After a little research, I found out that anachron should be the fault (if you watch the "test -x" commands, it is very plausible.
Because my computer is on 24/7 and thus don't need anacron, I just did a "dpkg --purge anacron".

---

