---
title: "Is there an Ubuntu version of Windows' &quot;Create System Image&quot; feature?"
date: 2024-04-07
forum: General Help
---

### Post by papriak on 2024-04-07
I'd like to create a complete backup of my Raspberry Pi 4's Ubuntu SD card installation while Ubuntu is running.

I've seen a few solutions online, but they seem to require using live media, unmounting the disk/partition to be backed up, or putting the SD card in another machine.

Windows has the ability to create a backup image while Windows is running, I'd like to do that with Ubuntu as well, if it's possible.

---

### Post by aljames2 on 2024-04-07
There is Timeshift, a gui tool which uses rsync under the hood.  I have never used Timeshift but I have used rsync, but not for backing up system files. TS is advertised for taking snapshots of system files, but I have no experience using it as a backup tool.

On ext4, I like to use LVM which has a snapshot feature. Then I like to use riff-backup to backup the portions of the snaphot that I would need if I were to restore, that would be /home & just a few other system directories. LVM snapshots can be taken on a running system. This type of plan though means that if something goes bad, I am prepared to do a fresh install and then go into my backups to get custom files, scripts, & /home data.

EDIT:  on second look, I see you are on a Pi4.  Timeshift may or may not be an option on that, others here may know more…

---

### Post by HermanAB on 2024-04-08
Hmm, you cannot copy a running system (unless you use a special file system with snapshot features).  

For an RPi, it is best and easiest to copy the SD card on another machine.

---

