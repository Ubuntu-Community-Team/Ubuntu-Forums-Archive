---
title: "Looking for a software flow-diagram for differential backup??"
date: 2023-01-14
forum: General Help
---

### Post by DVD-R on 2023-01-14
Hello All!
I was wondering if anyone knows of a software flow-diagram - which would clearly show the business rules governing a differential backup program - for example Déjà Dup.

In my mind - there are two critical conditions the system must respond to:

1) The condition in which the SOURCE contains files which are not found in the BACKUP

2) The condition in which the SOURCE is missing files which are found in the BACKUP

In Condition (1) I would hope the software would automatically copy SOURCE files not found within the BACKUP

In Condition (2) I would hope the software would display to the user - those files found in the BACKUP which are missing from the SOURCE
This is because there are going to be times in which a user creates docs, txt, pdf etc files - and then later decides to remove them from the system.

If the differential backup process simply always copies missing SOURCE files to the BACKUP - eventually the BACKUP will become bloated with files the user intended to remove.

I flow diagram would tell the story.
Any help would be greatly appreciated.
Thanks!

---

### Post by TheFu on 2023-01-15
DejaDup is based on Duplicity, so the same flows apply.

If you are familiar with dump/restore, a long-time Unix backup method, then you'll understand how duplicity works from a high level.  They are using old-school backup methods which are proven, but also can cause issues if full backups aren't performed often enough to reset the diffs that new files are related to.  Corruption of the prior full backup set will break any newer differential backups, until the next full backup is created.  I think the duplicity team recommends monthly full backups.  I suspect most users don't see or learn this and have been doing differential backups since the first time they did a full backup 3 yrs ago.  Only when there's some failure will they learn of the problem.

IMHO, there are better backup tools than following the old 1970 backup schedule.  Below is THE STANDARD monthly backup schedule for dump/restore:
```

S M T W T F S
- – - – - – - 
            F
D D D D D D M
D D D D D D F
D D D D D D F
D D D D D D F
```
Where
    D = Daily differential backup – changed data only, unless you can perform full backups within your backup window without impacting users
    F = Full backups – this limits the number of daily backups to be restored if there is an issue that week to 6 or 7
    M = Monthly – mark the first full backup of each month as the monthly and store it

dump/restore are still available for Linux today, if you like painful solutions.  [https://www.linuxshelltips.com/backup-linux-filesystem-using-dump-command/](https://www.linuxshelltips.com/backup-linux-filesystem-using-dump-command/)  dump/restore use the 5th field in the fstab file as part of their processing. From the fstab manpage:
```
       The fifth field (fs_freq).
              This field is used by dump(8)  to  determine  which  filesystems
              need  to  be  dumped.   Defaults  to  zero  (don't  dump) if not
              present.
```

After I learned that duplicity [https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)  , DejaDup [https://wiki.gnome.org/Apps/DejaDup/Details](https://wiki.gnome.org/Apps/DejaDup/Details) and Duplicati were all based on this method, I decided it was a little old school for my needs. 

Decided to use either rsync+hardlinks (rsnapshot [https://rsnapshot.org/](https://rsnapshot.org/) / back-in-time [https://backintime.readthedocs.io/en/latest/mainwindow.html#overview](https://backintime.readthedocs.io/en/latest/mainwindow.html#overview) ) or reverse-differential backups (rdiff-backup) where the most recent backup is a mirror of the sources.  I've used both types over the decades and even used dump/restore in the 1990s, but have been using rdiff-backup for about 13 yrs, happily.  The only trick for rdiff-backup [https://rdiff-backup.net/](https://rdiff-backup.net/) is that no intermediate backups can be removed. Just the oldest backups can be pruned safely.  Depending on risks for a system, I keep between 90 days and 366 days of backups.  Backup storage is about 1.3x the size of the original files for 60-90days.  I'm selective about what gets backed up and things that are easily replaced or unneeded don't get included.  It also means that to restore the most recent backup "set" just a cp or rsync is needed. No special tools, not even rdiff-backup.  The tool is handy if I need to restore a file from 38 days ago for some reason, which I've needed to do once.  Typically, I need to most recent version of a file or the most recent complete backup set.  There might be more efficient for storage backups.  I know of none that is more time/network efficient than rdiff-backup.  It is faster than rsync.

There are other backup methods, like Borg Backup [https://www.borgbackup.org/](https://www.borgbackup.org/) which works differently than all those.  When I looked at it, the tool was still too new for consideration.  The single most important thing on my systems is the data. Not the programs. Not the hardware.  THE DATA.  I'm not going to risk the data with unproven backups or some new fangled file system.

For how these things work, perhaps joining a virtual/live LUG meeting and asking someone with direct, deep, experience would be the easiest solution.  These things can be hard to understand by reading, but easy to understand by human-to-human discussions.  A number of LUGs have been meeting virtually since COVID and they don't mind when people from all around the world join.  My LUG has regulars that join from Asia, Europe, South America and all over the USA every week.  All we do is answer questions asked by the attendees.

---

### Post by HermanAB on 2023-01-15
Here is something that may help: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html?m=1](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html?m=1)

---

### Post by DVD-R on 2023-01-15
Wonderful!
Thank you very much for taking the time to explain all of that!
I'm looking into rsnapshot  :-]

---

### Post by DVD-R on 2023-01-15
Thank you very much!!!
This is new info - I'll have to digest it!
Much appreciate!

---

### Post by TheFu on 2023-01-15
> **DVD-R said:**
> Wonderful!
Thank you very much for taking the time to explain all of that!
I'm looking into rsnapshot  :-]

Hardlink-based backups have their own issues, like only the most recent owner, group, permissions, ACLs and xattrs are retained.  Also, the target storage has to support both hardlinks and each of those other metadata elements.  File systems matter.

That's one strength that duplicity covers well. rdiff-backup has covered most of them, but had issues with expanding sparse files until v2.x of rdiff-backup (included in Ubuntu 20.04 and later), which does handle them correctly.  I'm fairly certain that duplicity and related tools handed those things for a long time.

If you can work rsync, then you can work rdiff-backup.  The backup commands, --include/--exclude options are very similar.  I've posted simple rdiff-backup commands in these forums recently for typical desktop, local, versioned backups.

But only you will need to do the restore under pressure after something goes bad, so only you can decide.

As a quick, easy, test, I'd suggest you backup /etc/ using each tool (send them to different target-output directories) and compare what the target for each looks like, how long each takes for 10 versions, be certain to change a few files between most of the backup runs (not all!), what happens when a few files are changed, what that causes to happen, and how much total storage each uses.  /etc/ is relatively small, but files are owned by different users, which proper backups need to handle AND restore.
If you do that, in 15 minutes, you'll have a great understanding of 5 different backup tools and will be able to see what might be needed to restore those files correctly - 1 or all of them.

---

### Post by joshua123456 on 2023-01-15
> **TheFu said:**
> DejaDup is based on Duplicity, so the same flows apply.

For how these things work, perhaps joining a virtual/live LUG meeting and asking someone with direct, deep, experience would be the easiest solution.  These things can be hard to understand by reading, but easy to understand by human-to-human discussions.  A number of LUGs have been meeting virtually since COVID and they don't mind when people from all around the world join.  My LUG has regulars that join from Asia, Europe, South America and all over the USA every week.  All we do is answer questions asked by the attendees.

How can one join a virutal LUG meeting? Is there a website or something similar to keep an eye on?

---

### Post by Ralph L on 2023-01-21
I use LuckyBackup, which is a graphical front end to rsync, plus I think, a few other features. I found several problems, but I was able to work around them (mostly). If you are interested I can send a writeup I did for a web site on switching from Windows to Ubuntu back in 2010. Some things may have been fixed, since then. In my survey of back up systems at that time I felt LuckyBackup was the best. It still seems to work.

---

