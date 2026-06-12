---
title: "Managing / deleting files in a tarball"
date: 2013-12-12
forum: General Help
---

### Post by jshendrich on 2013-12-12
I have a tarball that contains logfiles from my email server.  I have a cron job that adds each daily log file to the tarball.  Our retention policy is that we keep 6 months worth of log files.  I'm trying to find a way to automatically remove old log files from the tarball.  I currently use the --delete option with --wildcards which allows me to delete groups of files from the tarball.  I'd prefer to schedule this with cron but haven't found a way to do this.  It would be nice if tar had a -mtime option like find does.

Any suggestions?

---

