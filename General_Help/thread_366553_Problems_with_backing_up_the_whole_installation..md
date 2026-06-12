---
title: "Problems with backing up the whole installation."
date: 2007-02-21
forum: General Help
---

### Post by ykhun on 2007-02-21
I tried almost all the different types of backup solutions like tar, rdiff-backup etc.

My rig is 6.10 server on Asus P5B Deluxe with 4 SATA on 2 volumes.

I always exclude the following folder:
/proc
/mnt
/tmp
/media/usbhdd  <-- To prevent infinite loop as this is where the backup goes to.

By excluding just the above folders, i was hoping to have a complete installation backup. (pipedream?) Anyways, nothing works. Tar (both bzip2 and gzip) will cause some massive kernel errors to spewed out on the console. rdiff-backup too gets the same error.

After some checking, i excluded the /sys folder as well. Then tar and rdiff-backup works perfectly. So the questions:

1. Have any1 attempt a full system backup (tar, rdiff-backup) like the one i tried and did you managed to do it without excluding the /sys folder as well?

2. What is in the /sys folder?

3. Related to (2) but i guess i better ask: With the /sys folder excluded, what do i lose?

---

### Post by nanotube on 2007-02-21
i don't remember my original sources of help when writing my rdiff-backup exclude list, but i have excluded /sys as well, so haven't run into your errors.
afaik, /sys is a new way of keeping track of devices, etc., that was introduced with the 2.6 kernel. don't know if you lose anything by not backing that up, presumably it is all auto-generated based on your hardware?
that's all i know, maybe someone with more detailed info can fill in. :)

---

### Post by indytim on 2007-02-21
One (of many options available)... you may want to check out Partimage (it's in the repositories).  It allows you to back up the entire partition to a number of formats and compression schemes.  I believe there is a "Live" version also.  Again, this is just one of many backup options.

Hope this helps,

IndyTim

---

### Post by Olav on 2007-02-21
Partimage is a good option for a "disaster recovery" sort of backup. It will allow you to restore your system exactly like it was. You need to run it **outside** your current operating system to make sure the partition you are backing up is not in use. I would use the [SystemRescueCD]("http://www.sysresccd.org/") for that (I also use it to "ghost" Windows computers).

If you insist on a file level backup, be sure to exclude /dev as well.

---

### Post by ykhun on 2007-02-21
> **indytim said:**
> One (of many options available)... you may want to check out Partimage (it's in the repositories).  It allows you to back up the entire partition to a number of formats and compression schemes.  I believe there is a "Live" version also.  Again, this is just one of many backup options.

Hope this helps,

IndyTim

Yeah, i'd checked out partimage and heard good things about it. But my rig is hot and i can't bring it down frequently to do backups. File level backups are really all i can do.

---

### Post by ykhun on 2007-02-21
> **Olav said:**
> Partimage is a good option for a "disaster recovery" sort of backup. It will allow you to restore your system exactly like it was. You need to run it **outside** your current operating system to make sure the partition you are backing up is not in use. I would use the [SystemRescueCD]("http://www.sysresccd.org/") for that (I also use it to "ghost" Windows computers).

If you insist on a file level backup, be sure to exclude /dev as well.

Thanks for the headsup. What are the files in /dev ? They seem like a bunch of links to me, aren't they impt if i ever need to attempt to restore my rig on a new machine?

---

### Post by hugmenot on 2007-02-22
/sys gets populated on boot by itself you should exclude it. It contains things that are not really data files but points of access for various system realted functions. /dev also gets populated at boot but there might be static symlinks (like /dev/modem -> /dev/ttyxxx) in there; so you should include it.

Anyways this is my rdiff-backup line:

/usr/bin/rdiff-backup  --print-statistics \
--exclude '/home/*/.gnupg' \
--exclude '/home/*/.ssh' \
--exclude '/home/*/.Trash' \
--exclude '/home/*/.thumbnails' \
--exclude '/home/*/.beagle' \
--exclude '/home/*/.opera/cache4' \
--exclude '/home/*/.opera/wand.dat' \
--exclude '/var/spool' \
--exclude '/var/cache' \
--include '/bin' \
--include '/boot' \
--include '/dev' \
--include '/etc' \
--include '/home' \
--include '/lib' \
--include '/opt' \
--include '/root' \
--include '/sbin' \
--include '/usr' \
--include '/var' \
--exclude '/*' \
/ /media/backupdisk/BACKUP/

You can see I exclude everything at the bottom and only selectively allow subtrees.

---

### Post by ykhun on 2007-02-23
Thanks for sharing ur setup :)

---

