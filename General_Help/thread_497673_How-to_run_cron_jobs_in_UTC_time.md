---
title: "How-to run cron jobs in UTC time?"
date: 2007-07-10
forum: General Help
---

### Post by evaldas on 2007-07-10
Hi,

is it possible to instruct cron to run its jobs based on UTC time (not local time)?
for example if doing nightly backups in the time interval from 02:00 to 02:59, someday in March it won't run at all, and one day in October it will run 2 times.

Is there a standard way to do this without recompiling cron as pointed [here]("http://widell.net/scripts/bd/dst/")?

/etc/default/rcS
> UTC=yes

---

