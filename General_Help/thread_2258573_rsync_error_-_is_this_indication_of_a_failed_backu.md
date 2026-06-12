---
title: "rsync error - is this indication of a failed backup ?"
date: 2014-12-28
forum: General Help
---

### Post by blanik on 2014-12-28
I use the command "[COLOR=#ff0000]rsync -azP /home/roy  r####@192.168.1.11:/home/roy/Laptop_Backups[/COLOR]" to backup the home directory on my laptop to a server on my home LAN.  The laptop is Ubuntu 14.10 and the server is MythBuntu 14.04.

At the conclusion of each rsync backup, I see the following error "[COLOR=#ff0000]rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1][/COLOR]"

Is this error an indication of a failed backup ?  Can anyone provide more information regarding the error message, or alternatively provide me with some information regarding where to look in the logs for more information.

Regards,

Roy

---

### Post by TheFu on 2014-12-29
rsync is good for mirrors, not so good for backups.  For media, a mirror is probably the only practical method of backup due to storage requirements. For the other parts of an OS, having versioned backups is absolutely critical.

When I see an error like that, it is usually because file permissions/ACLs cannot be transferred.  Run it again to see which file had the issue.  Add some -vvvv options to see more information.

rdiff-backup is a librsync-based backup tool that is highly efficient and provides versioning.  The most recent backup looks like an rsync mirror and older backups are efficiently stored as compressed, diffs.  30-60 days of versions are usually less than 10% more storage.

---

