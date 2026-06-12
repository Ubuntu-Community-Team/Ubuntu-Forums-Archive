---
title: "Good Backup software"
date: 2013-04-29
forum: General Help
---

### Post by Phil Binner on 2013-04-29
I've been doing backups just by making manual copies for years now, and I thought it was about time to get a bit more scientific.  First I tried Deja Dup, and then File Backup Manager, and I can't say I'm impressed with either.  Possibly because I'm not using gthem correctly.

All my important data is on the NAS, a 2 TB raid system, and I have a 1.5 TB disk on my media machine to recieve backups. Currently I have only about 350gb data, so there is no capacity issue.

I have various kinds of data, and I certainly don't want to treat them the same.  I suppose they could be viewed in 2 categories; big files I don't personally modify, like video, pictures and music, and documents which are much more volatile and a lot smaller.  For the big files an incremental backup may be best because I don't want to keep duplicating the same data, but would this mean that if something got accidentally deleted without my noticing it would also get deleted from the archive next time the incremental backup was performed.  For documents it's fesible I would want to go back to an earlier version, so multiple complete backups would seem more sensible.  Whatever kind of backup, I would like to schedule it for the middle of the night.

On Deja Dup I can set a backup schedule in terms of daily, weekly, etc, but not the time as far as i can see.  Also, on Deja Dup there seems to be only one single backup profile, so I can't treat different kinds of data differently.  File Backup Manager seems able to accept different backup profiles, but I couldn't find anywhere to set a schedule.

Can anyone suggest software I could look at which may meet my needs.  Alternatively, if the philosophy I'm trying to use to define my backups is wrong, I'm open to suggestions.

Thanks in advance.

---

### Post by ibjsb4 on 2013-04-29
Im half old school so I use rsync with a GUI.  Probably not as easy to set up as DejaDup, but I do not back up everything as I prefer to pick and choose.

[Luckybackup]("http://luckybackup.sourceforge.net/")

[Grsync]("http://www.opbyte.it/grsync/")

Both are in the software center.

---

### Post by ajgreeny on 2013-04-29
I also use grsync to backup to USB external disks which are themselves formatted as ext3.  I have several different backup sessions setup on grsync to backup different parts of my /home to different disks, and it all works very well.

For example I can backup my documents to one external disk and my multimedia to another very easily.  grsync and rsync both only make backups of files that have changed since last time, so after the first backup session the rest are very quick.

---

### Post by markbl on 2013-04-29
> **ibjsb4 said:**
> Im old school so I use rsync with a GUI.
Old schoolers don't use a GUI! ;)

I have used rsnapshot for many years and although I look around occasionally I still think it is the best backup solution. It is a perl script which uses rsync and runs from cron. I also install the free deltacopy on my wife's windows PC to pull directories from there into the backup.

---

### Post by ibjsb4 on 2013-04-29
I fixed that :rolleyes:

---

### Post by boogerama on 2013-04-29
I run backuppc. I don't know if you can run it off a NAS though, you'll need to do a little research on that.  I use it to backup all my Linux machine as well as my wife's Windows 7 laptop.  LuckyBackup is a nice option also.  You can schedule cron jobs to run at specified intervals.  Theres' quite a few options out there, it's just a matter of finding what you like best and what works for you.  

Let us know what route you took and what issues you ran into.

Thanks

---

