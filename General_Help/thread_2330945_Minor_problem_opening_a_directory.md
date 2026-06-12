---
title: "Minor problem opening a directory"
date: 2016-07-16
forum: General Help
---

### Post by xeddog on 2016-07-16
I have a machine running Ubuntu 16.04.  In this machine there are two hard drives.  /dev/sda is the boot device that has all required file systems including /home.   Drive /dev/sdb is a drive that USED to be a boot drive and has just about all of the same files on it, including a version of /home from a previous linux install.  

I have a script I run when I boot the machine, and one of the things it does is backup a mysql database.  This database backup is directed to /home/(userid)/Backup directory that is on /dev/sdb.  It all works just fine **IF** I manually open that directory using nautilus prior to running the script.  If I do not open it first, the backup will fail giving me a "No such file or directory" error.

One thing I have done is to create a small txt file in that directory, and then "touch" it as the first thing in the script.  It doesn't work.

Anyone else have any ideas how to get this working?

Thanks,

Wayne

---

### Post by Keith_Helms on 2016-07-16
slash (/) should be the mount point for /dev/sda.  What's the mount point for /dev/sdb?

---

### Post by xeddog on 2016-07-16
The mount point for sdb is /media/(my userid)/(device uid).    In Nautilus it is shown as "492 GB Volume" in the tree view along the left column.

---

### Post by Keith_Helms on 2016-07-16
Okay, so it sounds like you don't have an entry for /dev/sdb1 in your /etc/fstab and Nautilus is mounting it when you use it to navigate there.  To get around that extra step, it would be easiest to just mount the partition on that drive at startup using /etc/fstab.  Doing that requires a bit of knowledge of partitions and file system types.  Are you familiar with the gparted utility?

---

### Post by xeddog on 2016-07-16
I have used gparted a couple of times, but I'm FAR from being an expert.  This is a test machine so I will look into fstab.  I was under the impression that an internal disk would be mounted upon boot, but I guess that ain't necessarily so.

Wayne

---

### Post by xeddog on 2016-07-16
I have added it to fstab and it is now working great.  Thank you.

But.  Why did the Unity launcher show the device when it wasn't mounted yet?  Why did Nautilus mount it, and how did Nautilus know anything about WHERE to mount it (meaning the mount point)?  And why is the drive shown as "492 GB Volume" in the Unity launcher, and the nautilus tree both before and after mounting?

---

### Post by Keith_Helms on 2016-07-16
/media/yourid/hexcodefordrive is just a default location for mounting stuff.  Ubuntu's file manager shows all the partitions that aren't explicitly mounted by fstab as "nnGB volume".

---

