---
title: "Remote logging"
date: 2008-03-17
forum: General Help
---

### Post by wgcampbell on 2008-03-17
Hi -

I'm maintaining a log file of temperatures and humidity.  I'd like to periodically send that log to a remote mysql db or ftp site.  I do know of the logrotate routine, but I want something uploaded probably every 6 hours.

Can someone suggest something (canned) - other than a custom script?

---

### Post by DoctorMO on 2008-03-17
for ftp you could create an ftp command and stick it in a cron job. for mysql you'll need to create a script which you should stick in a similar cron job.

---

