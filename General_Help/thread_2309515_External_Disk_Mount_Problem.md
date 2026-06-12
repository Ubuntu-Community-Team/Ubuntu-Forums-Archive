---
title: "External Disk Mount Problem"
date: 2016-01-11
forum: General Help
---

### Post by secoonder on 2016-01-11
Hello
i am using ubuntu 12.04.I attach an external hard drive to my Desktop Pc.
i entered this command.> mount -t ntfs-3g /dev/sdb2 /backup.
this is mounted succesfully.
But after 20-30 minutes,The mount isnt disable.
when is fdisk -l command
my external disk is sdc1? or sde1 or sdf1?

i changed external disk.but the error is not changed.
what can &#305; do
thank you very much for your help

---

### Post by yancek on 2016-01-11
> But after 20-30 minutes,The mount isnt disable.

Why would it be disabled after a certain amount of time?  If you want to unmount, use the umount command on the mount point.

> when is fdisk -l command

It displays drive/partition information.

> my external disk is sdc1? or sde1 or sdf1?

There is no way for anyone here to tell you that.  sdc1 is the first partition on the thrid drive, sde1 is the first partition on the the fifth drive. 

> i changed external disk.but the error is not changed.

What error?

---

### Post by secoonder on 2016-01-11
Hello 
thank you for your answer.
i couldnt tell.I can not express myself well.So sorry. :(
i take backup to /dev/sdb1 by crontab (daily)
mount -t ntfs-3g /dev/sdb1 /backup

when i came to business next day, i cant see /backup.So &#305; dont take backup.Crontab is not found the path.
When i entered command
cd /backup
i took an error : input/output error.

when i fdisk -l command
my external disk is a /dev/sdc1.
and then i am entered 
mount -t ntfs-3g /dev/sdc1 /backup..

Every morning i entered this command. :)
What can &#305; do ?
Thank u very Much for your help

---

### Post by yancek on 2016-01-11
You need to first determine on which drive/partition your backup directory is, sdb1 or sdc1.  In order for your backup to work, you would need the correct partition mounted when you run the backup script.  If the drive you backup to is always attached, the simplest way to do this is to have an entry in the /etc/fstab file.  You are backing up to a windows partition, do you have windows installed?  

The command:  cd /backup will only work if you are in the directory immediately above it, otherwise you need the full path.  With current Ubuntu releases, partitions on external drives are usually available under the /media/user directory.  Have you created another mount point elsewhere?

How are you running the cron backup?  The simplest way to do it is to create an executable script and make an entry in cron to run it at a specified time with the entry containing the full path to the script.  If you have a script, post it here.  Also post the cron entry and someone should be able to help.

---

### Post by secoonder on 2016-01-12
Hello
My backup directory is : /backup
((mount -t ntfs-3g /dev/sdb1 /backup)
cron job is:
00 23 * * * cp /home/joe/ade.mdf /backup2/
because of the mount is changed(sdc or sde or sdf ) ,the backup script is not running correctly.
how to prevent changing sda,sdb,sdc?
i am not sure,when i write the command(mount -t ntfs-3g /dev/sdb1 /backup) and reboot,the problem is solved ?

---

### Post by yancek on 2016-01-12
If your mount point on the external drive partition is backup you should see it when your run:  ls / because what you posted indicates the backup mount point is in the root of the filesystem.  You shown running the mount command to backup while your cron entry shows backup2?  If the device changes, use a UUID for the partition which you can get with the command:  sudo blkid.

---

### Post by secoonder on 2016-01-17
yancek thank you
The problem is electrical.When the power is loss,the mounted was changed.
i plugin the external disk to UPS.The problem is solved.
Thank you very Much for your help

---

