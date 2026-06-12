---
title: "logrotate - syslog-ng - rotate logs older than x days old"
date: 2008-04-18
forum: General Help
---

### Post by boozer_2 on 2008-04-18
I want to keep 3 days of logs, and have logrotate rotate and compress anything older than 3 days old.  syslog-ng automatically creates new files each day (i have them named with the date) so I just want to use logrotate to compress logs older than 3 days and maintain a years worth of logs.  

I want to rotate logs daily, but only ones that are x days old.  Can logrotate do this?

I figured i could write a cron script (like mv /syslog/`date +"%Y-%m-%d" -d '3 days ago'` /xxx) to move logs older than x days to a another directory and just have logrotate run on all files in that directory, but I wondered if logrotate could do it with some option or variable itself.

---

