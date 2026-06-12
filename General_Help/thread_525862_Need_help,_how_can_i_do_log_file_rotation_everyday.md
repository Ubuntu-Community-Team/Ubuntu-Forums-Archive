---
title: "Need help, how can i do log file rotation everyday or even every hour?"
date: 2007-08-14
forum: General Help
---

### Post by HaXiT on 2007-08-14
Hello,
I was wondering how i could make the log files rotate on a daily basis or even hourly basis? Any help would be appreciated. I am somewhat of a "n00b" when it comes to linux, i am still learning everyday. :)
Thank You!!
-------
HaXiT

---

### Post by HaXiT on 2007-08-14
Its been 50 minutes and no one has looked at it... :( Sorry for double posting...

---

### Post by pmg on 2007-08-14
See the **logrotate** command.  There is a **daily** option that can be used in config files.  The logrotate command is usually called by cron from a script in the /etc/cron.daily/ directory, so it only gets called once a day, but it could be called from /etc/cron.hourly/, or a more general crontab entry could be made to schedule when it's called.

---

