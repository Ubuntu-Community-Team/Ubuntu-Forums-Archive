---
title: "run-parts with logrotate issue"
date: 2024-03-04
forum: General Help
---

### Post by igz430 on 2024-03-04
Hello,
I previously configured logrotate for syslog with my specific requirements and it works fine when I run logrotate manually. 
I noticed, however that syslog is not being rotated automatically. This is what I have verified so far:
- The logrotate file is in /etc/cron.hourly - as per my requirements
- The syslog file has entries: CRON[26961]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly) that correspond to the expected times as per the crontab file (every hour at :17 minutes).
- When I manually run ```
/usr/sbin/logrotate /etc/logrotate.conf
``` (which is what's in the logrotate file) the syslog is rotated

- When I manually run ```
run-parts --report /etc/cron.hourly
``` I don't get errors but the syslog is **not** rotated.

- The manual runs were done with sudo

Any ideas are appreciated.

---

