---
title: "Rotating log files"
date: 2008-04-29
forum: General Help
---

### Post by seeker1458 on 2008-04-29
Im using 7.10 running syslog-ng.  I need to know how to make a shell script that will compress my current logs, at the end of every week. I have tried using logrotate, but somehow something got screwed up and I can't figure out what happened. Now I've got like a month's worth of logs built-up in my log files.  How Do I call gzip, and will syslog-ng re-create the auth.log, and syslog file? I've already set the flags to create files if they don't exist, but does that work for inherent syslog-ng files aswell?

---

