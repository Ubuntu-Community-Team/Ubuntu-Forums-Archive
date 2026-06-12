---
title: "Mythbuntu mysql hangs"
date: 2017-04-29
forum: General Help
---

### Post by jamoody on 2017-04-29
mysql hangs every few weeks, eating 100% CPU for hours on end.  /var/log/mysql.log is empty (zero bytes) so that doesn't seem to be the location of the log.  Can anyone point me to the log location?

After I reboot to recover, /var/log/mysql/mysql/error.log does show errors with timestamps right after the reboot so I don't know if the errors are caused by the reboot with mysql hung or if the mysql hang is due to the database errors.  

I see in syslog that cron.daily started running but it didn't seem to get as far as my database backup (first thing my backup routine does is touch a file to record the timestamp) so I don't believe the mysql hang is related to backing up the database.

I believe (please correct me if I'm wrong) that cron.daily runs in alphabetical order so mythdatabase-backup should run before optimize_mythdb so the optimization doesn't seem to be what is hanging mysql.

Other ideas?

I'm running Mythbuntu 14.04.5 with MythTV 0.28.1-21 (latest fixes as of 4/28).

---

### Post by jamoody on 2017-06-05
I discovered that / was getting changed sporadically to  read-only mode due to a drive failure and suspect that was causing the problem.  The drive has been replaced and all is good.

---

