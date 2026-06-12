---
title: "gutsy and cron"
date: 2007-12-05
forum: General Help
---

### Post by romeyde on 2007-12-05
Not new at this so really bugging me that I can't figure it out.   Running gutsy and trying to get a script to fire every 10 minutes via cron.   Runs just fine from the command line.   I've tried putting it in my personal crontab, tried putting it in roots crontab and even tried just running it from /etc/cron.hourly.

Right now, it's just in /etc/crontab and set to run every 10 minutes.  But again, monitoring syslog shows nothing.  It just never fires.  No sign as to why anywhere that I can find.

/etc/crontab entry:

10 *    * * *   root    /opt/prenominalNZB/prenominalNZB > /home/ear/prenominalNZB.log

Any suggestions?   Feel really stupid that I can't figure this out.

---

### Post by romeyde on 2007-12-05
Doh, sorry.   Don't know why but it just took a lot longer than I would have expected to finally start firing.   Works now...

Dec  5 20:10:01 shuttleXPC /USR/SBIN/CRON[12950]: (root) CMD (/opt/prenominalNZB/prenominalNZB > /home/ear/prenominalNZB.log)

---

