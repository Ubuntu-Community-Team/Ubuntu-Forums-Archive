---
title: "cron jobs end after one hour"
date: 2007-04-04
forum: General Help
---

### Post by ericnils on 2007-04-04
I am trying to schedule a backup job to run nightly via cron, but it keeps ending after exactly one hour.  If I run the job manually it runs for approximately eight hours and has no problems.

I first tried placing the following line in /etc/crontab:

45 18  *   *   *     root /backup/batch

After this job did not run to completion I removed the above line from /etc/crontab, changed the permissions on the backup job to allow my user to run the job, ran crontab -e and placed the following line in my own cron configuration:

45 18  *   *   *     /backup/batch

Again the script ended after exactly one hour.  I know this because the script constantly writes to a log file and the modified timestamp on that file is 19:45.

Is there a config setting in cron that is causing this to happen?  How do I change it?

---

