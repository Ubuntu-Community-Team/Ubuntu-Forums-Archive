---
title: "Chnge logrotate time"
date: 2007-10-03
forum: General Help
---

### Post by posterboy on 2007-10-03
Hmm, a week ago I posted about this. No answer. I got diverted into other (more important) things. Here's the issue. I want the cron jobs that rotate logs, updatedb, makewhatis, etc. to run at around 4AM. The default is to run at 7:30AM. I'm up and doing stuff by then. OK, that should be simple, just change the times in /etc/crontab, right? Uh-uh, all that still runs at 7:30. What controls this? Why do my changes not do anything?

---

### Post by ddrichardson on 2007-10-03
Post /etc/crontab

---

### Post by posterboy on 2007-10-03
Here we go:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
26 4    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
30 4    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 4    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

---

### Post by posterboy on 2007-10-06
Just for others, and because I hate a thread that's unresolved, /etc/crontab seems to be completely ignored in this regard. Look in /etc/cron.d, and there you will see the 7:30AM start time. Changing that, got it all running at 4AM, which was what I wanted. Thanks to those who helped.

---

