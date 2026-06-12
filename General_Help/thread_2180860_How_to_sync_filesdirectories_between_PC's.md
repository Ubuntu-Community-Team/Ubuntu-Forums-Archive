---
title: "How to sync files/directories between PC's?"
date: 2013-10-14
forum: General Help
---

### Post by petegregar on 2013-10-14
I have directories that I want to mirror and keep backed up on different harddrives (PC's)

I used to use freefilesync in windows.

I tried it with Ubuntu but I cannot see network drives.

Any other software to try?

---

### Post by markbl on 2013-10-15
We use rsync to sync files on all Linux, Unix, and Mac systems. I use the free deltacopy program to rsync to/from windows pcs.

---

### Post by drmrgd on 2013-10-15
For a nice wrapper on rsync, try Rsnapshot:

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)

That will give you a really nice automated sync and backup utility that will allow for rolling backups and versions and scheduling at different time periods (hourly, daily, weekly, etc.).  I use this myself for the last couple years, and it's been great.

---

### Post by ibjsb4 on 2013-10-15
There is also [grsync]("https://help.ubuntu.com/community/rsync#Grsync") and [luckybackup]("https://apps.ubuntu.com/cat/applications/precise/luckybackup/"), Both are GUIs for rsync.

---

