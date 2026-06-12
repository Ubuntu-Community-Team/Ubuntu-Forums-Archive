---
title: "backup (rsync) problems"
date: 2007-09-11
forum: General Help
---

### Post by tjk on 2007-09-11
I've tried to backup my internal harddrive to a USB external using sbackup and grsync.  And I can't get either to work!
Also, it appears that this has somehow filled up my "/" partition and my /var folder has a huge backup file.  In both backup systems I pointed the backup to /media/backup (my ext usb drive), but in both instances no files/folders get to that location -- although with grsync it created a backup folder.
Question:
1) can I safely just delete the /var/backup folder (nearly 14Gb)?
2) how can I get either backup program to copy files directly to the ext usb harddrive?

---

### Post by southernman on 2007-09-11
With your usb drive plugged in, post the output of "mount" and/or "ls /media"

---

### Post by tjk on 2007-09-11
> **southernman said:**
> With your usb drive plugged in, post the output of "mount" and/or "ls /media"

/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw)
/dev/hda5 on /home type ext3 (rw)
/dev/hda7 on /media/oldroot type ext3 (rw)
/dev/hda2 on /media/windows type vfat (rw,utf8,umask=007,uid=0,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/LACIE type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=lower)

---

### Post by southernman on 2007-09-11
> **tjk said:**
> I've tried to backup my internal harddrive to a USB external using sbackup and grsync.  And I can't get either to work!
Also, it appears that this has somehow filled up my "/" partition and my /var folder has a huge backup file.  In both backup systems I pointed the backup to /media/backup (my ext usb drive), but in both instances no files/folders get to that location -- although with grsync it created a backup folder.
Question:
1) can I safely just delete the /var/backup folder (nearly 14Gb)?
2) how can I get either backup program to copy files directly to the ext usb harddrive?

Thanks for the output... according to that you should point your backup to /media/LACIE/backup. That should take care of #2.

#1 - **Shouldn't** hurt to delete the /var/backup folder.


> **/dev/sda1 on /media/LACIE type vfat (rw,nosuid,nodev,noatime,uid=1000,utf8,shortname=l ower)** This is your usb drive.

---

### Post by tjk on 2007-09-11
> **southernman said:**
> Thanks for the output... according to that you should point your backup to /media/LACIE/backup. That should take care of #2.

That's exactly my problem.. I have directed it to the above directory with both grsync and sbackup and the backup files never get there.

---

### Post by southernman on 2007-09-11
Not quite according to your OP. And I quote:

> In both backup systems I pointed the backup to /media/backup (my ext usb drive),

My suggestion used almost the same path but with "LACIE" added. Your external drive is mounted at /media/LACIE so doing just /media/backup should have put it in /media/backup.

It would be save to delete the /var/backup and try it again as I suggested... sure can't hurt.

Strange though it put the backup in /var/backup *scratches head*

**What does "ls /media" show us?**

---

