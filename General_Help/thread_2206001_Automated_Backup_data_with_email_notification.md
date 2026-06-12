---
title: "Automated Backup data with email notification?"
date: 2014-02-16
forum: General Help
---

### Post by mtweldon on 2014-02-16
Looking to see if anyone has any recommendations for a program backing up files / folders only the changed / new items and having it send an email notification.

Coming from a synology diskstation and I love having that feature.

---

### Post by TheFu on 2014-02-17
Any backup program run via crontab will send an email notification provided that an email MTA is configured correctly - like postfix.
There must be 50 backup programs that only do incremental backups - most are based on the most excellent librsync.

I like **rdiff-backup** for a number of reasons, but it is impossible to recommend any backup tool with the data provided. What is the amount of source data? Where is the target storage?  Which OSes are involved and which file systemss (MOST IMPORTANT!).  Does the transfer need to be encrypted? Does the remote storage need to hold encrypted backups?  Is that remote storage S3 or some other provider?  Lots-o-questions.

I backup OS and personal files differently than I backup video and audio files.  With the larger files, having a mirror is enough, but with the OS, apps and personal files, I want differences stored for 30, 60, 90 days so if file corruption occurs for any reason, then an older version of the file will still be available. This is critical for spreadsheets and presentations.  Backups with 30-60 days of reverse incremental files are 1.2x the original storage or less, IME.  So, if my desktop is 20G, then for 60 days of backups I need just 24G of storage. That seems like a BARGAIN to me.

OTOH, if you need a GUI and only want to backup files in your HOME, then back-in-time is a nice, efficient alternative. The target storage must support hardlinks, so it cannot be NTFS or FAT-whatever.  Anyway - see why it would be helpful to have more information?

---

### Post by mtweldon on 2014-02-17
Sorry about that, wasn't very descriptive, I'll blame being tired.

I don't care if it's GUI or not, still learning linux, it's been a while since I've had the chance to dive into it, but I can pick it up as I go along. 

I'll be backing up locally to some USB3 drives that will be plugged in, primarily documents,video/audio and a few other files. Sitting at around 5TB right now, but the incremental back ups every other day would typically max out around 3-4GB.

---

### Post by TheFu on 2014-02-17
What file systems are on the USB3 drives?

---

### Post by mtweldon on 2014-02-17
I think it's FAT32 right now, but once I move over from my other server and restore everything I don't mind making it whatever is easiest, wouldn't mind compatibility with windows in the event I need to grab one for on the go, but not required.

---

### Post by TheFu on 2014-02-17
Well, if Windows compatibility isn't needed, then using ext4 would be best. That frees up all the Linux backup methods to select from.
FAT32 has too many limitations on file size to be useful anymore and NTFS doesn't support the UNIX-style linking which many backup tools use. Plus all permissions and ACLs are likely to be lost - that's terrible for system level backups with programs, settings ... anything that is not just a single HOME directory or pure media files.

RAID is not a backup. Have to put that in every thread for lurkers - not you of course.
Mirrors are not a suitable backup for OS, Apps and non-media data.

Real backups have a different "set" for every time the backup task is run. Restoring from yesterday or last week will get different versions of files. Modern backup tools deal with this efficiently - both on networking and for the storage.
In the last few days, I helped another guy get a simple rdiff-backup script working. You can search to find it. We discussed saving installed packages, system settings, data.  He ended up with a simple script to do it that almost anyone could use as a starting point for their own backups.

---

### Post by oldfred on 2014-02-17
See this one:
 Sample rsync file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)

      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

      
 Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

---

