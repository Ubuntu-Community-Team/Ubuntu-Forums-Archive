---
title: "A few problems with MythTV jobs after upgrade"
date: 2014-03-26
forum: General Help
---

### Post by Phiwum on 2014-03-26
After upgrading to Ubuntu 13.10, I've noticed the following problems:

(1) The daily mythexport cronjob fails and reports 

     DBI connect('database=:host=;port=3306','',...) failed: Access denied for user 'root'@'localhost'

Seems to me that it ought to be connecting as mythtv, not as root, but I can't figure out how to fix it.

(2) The weekly mythtv-database cronjob fails and reports,

     ERROR: DBBackupDirectory not specified, stopped at /usr/share/mythtv/mythconverg_backup.pl line 856.
     run-parts: /etc/cron.weekly/mythtv-database exited with return code 255

(3) mythfilldatabase appears not to be downloading regularly.  I noticed today that I only had programs for local channels, and those were only for the next three days.  I manually ran mythfilldatabase, and the database filled as expected.  No idea what's going on there.  Nothing in the mythfilldatabase log jumps out at me as suspicious.

Thanks for any help

---

