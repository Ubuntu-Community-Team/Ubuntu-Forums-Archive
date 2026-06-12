---
title: "Auto-expiring filesystem"
date: 2013-03-08
forum: General Help
---

### Post by hambone79 on 2013-03-08
Does anyone know if it is possible to setup Ubuntu to automatically delete files from the filesystem after they expire? Here is what I have in mind:

1. By default files stored on the system are not set to expire.
2. The user has the option of setting certain files to expire after X number of days, weeks, months, years. The system can also be configured to expire files that match a certain file naming pattern or to ignore certain directories.
3. The system can generate a list of files that will be deleted that day and require confirmation to delete them.

The reason I want to do this is that I am managing a file system where users have a tendency to store lots of unnecessary information until they are sure they don't need it any more. The problem is that most of them forget to delete the garbage when they determine it is no longer needed and we end up with huge backups and full file servers. If all else fails I can write a script or two that would do most of this, but I would really like an existing program that has been well tested.

---

### Post by kuifje09 on 2013-03-08
I would opt for just 2 script, even combined to 1.
First delete files in a specific directory of your choice, delete files not acessed by x days, or weeks...
Then delete empty dirs in that specific directory.
Just twice a loop through a row of dirs, and a find -exec rm {}  . ( maybe add a logging in between )
Run this i.e.  daily from cron and your done.
You could add against complains from users a logging with info about the deleted files.

---

### Post by schragge on 2013-03-08
There are tools that could be of some help here like [tmpreaper]("http://manpages.ubuntu.com/manpages/precise/en/man8/tmpreaper.8.html"), [incron]("http://manpages.ubuntu.com/manpages/precise/man5/incrontab.5.html"), [inoticoming]("http://manpages.ubuntu.com/manpages/precise/en/man1/inoticoming.1.html"). But be aware of any implications of using them. E.g. [the filesystem shouldn't be mounted noatime](http://lwn.net/Articles/499293) if you plan using tmpreaper on it, never use tmpreaper on root partition, etc.

---

