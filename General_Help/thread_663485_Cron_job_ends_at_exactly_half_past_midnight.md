---
title: "Cron job ends at exactly half past midnight"
date: 2008-01-10
forum: General Help
---

### Post by AlexDavidson on 2008-01-10
We have an onsite backup server running Ubuntu Server 7.04. Every night it mounts a series of NFS shares and rsyncs them to its RAID array. One share contains an SVN repository, and this is handled as a special case: svn fast backup is used.

Just prior to this, the repository is verified with svnadmin verify. All output from the job is dumped to a logfile, and when the entire job completes (backup included) it is mailed to the sysadmin distribution list explicitly (not by cron itself).

Recently the verification process has stopped completing. The output stops dead around revision 18200, with no errors, yet svnadmin is exiting with an error code causing the backup to be skipped. The log file's last modification time is always 00:30. The entire task starts via cron at midnight, so the process is running for precisely half an hour.

The log is still mailed, so I doubt that the cron job itself is what's getting killed. Most likely there's another job being started which is interfering, possibly by unmounting the share or causing a network timeout, making svnadmin fail without a message.

What jobs are run by a default USE installation at 00:30 every night?

---

### Post by cmnorton on 2008-01-12
As dumb simple as it sounds, you might have to write a small shell script to poll what's running with ps, and log that to a file. If that new program gets killed, you'll have more information, even if it is spooky. Or, you'll see what's running around the time your cron job stops.

---

