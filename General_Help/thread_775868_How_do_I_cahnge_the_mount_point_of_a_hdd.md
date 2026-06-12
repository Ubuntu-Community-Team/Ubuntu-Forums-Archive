---
title: "How do I cahnge the mount point of a hdd?"
date: 2008-04-30
forum: General Help
---

### Post by krelverehan on 2008-04-30
I have this brand new 160GB hard drive, and I have it working fine. But I have to manually mount it every time I log in. And the permissions are set for root user only. :(

Is there any way to get it to automatically mount at /home/username/storage ?? And also, what is that magic command that changes the permissions of a series of files so I can use it without being root?

Thanks!

---

### Post by warp99 on 2008-04-30
> **krelverehan said:**
> I have this brand new 160GB hard drive, and I have it working fine. But I have to manually mount it every time I log in. And the permissions are set for root user only. :(

Is there any way to get it to automatically mount at /home/username/storage ?? And also, what is that magic command that changes the permissions of a series of files so I can use it without being root?

Thanks!
Here is some information on installing a new hard drive for mounting at boot time:

[https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28new%29#head-4cf3116dcfc30495ffcb3500c37659c8e7ec301b](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28new%29#head-4cf3116dcfc30495ffcb3500c37659c8e7ec301b)

the only caveat is to replace the 'dev/hdd1' mount point with a UUID number. When you open the fstab config file to add the drive per the instructions you'll see what I'm talking about, so issue the following:
```
sudo vol_id -u /dev/<name_of_new_drive_device>
```
and out will come a UUID number. Use this number in your fstab file for the new drive.

Edit:
Also backup your fstab file just in-case of a failure.

---

### Post by agim on 2008-04-30
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

This post should do it. You are going to have to edit the fstab file (short for file system table).
Good luck

---

