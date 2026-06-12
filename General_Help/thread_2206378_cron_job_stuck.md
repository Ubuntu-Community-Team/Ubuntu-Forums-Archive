---
title: "cron job stuck"
date: 2014-02-18
forum: General Help
---

### Post by loyhz2ayj-jeff on 2014-02-18
I had mrtg running under cron, and then I decided I wanted it to run as a daemon, so I removed it from Cron.  But I keep getting these crazy messages from cron saying that mrtg is already running.  "crontab -l" reports "no crontab for root".   Nothing in /etc/crontab except what Ubuntu leaves there.  And /var/spool/cron/crontabs is also empty.

Any idea what is going on?  I even rebooted and it keeps coming back!

---

### Post by coldcritter64 on 2014-02-18
Try listing the directories /etc/cron.* (the * wildcards any of the possible cron folders) for possible entries for mrtg.
```
ls /etc/cron.* | grep mrtg
```
If any contain an entry for mrtg that code should indicate it is there, you can then individually check the cron.hourly, cron.daily, cron.weekly and cron.monthly folders in /etc for an entry (there may be more than one entry to remove in some circumstances). Good luck.

---

### Post by loyhz2ayj-jeff on 2014-02-19
Yup, the install created /etc/cron.d/mrtg.. totally missed that.

---

