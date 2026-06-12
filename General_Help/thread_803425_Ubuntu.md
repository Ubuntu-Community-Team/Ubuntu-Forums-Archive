---
title: "Ubuntu"
date: 2008-05-22
forum: General Help
---

### Post by jras20 on 2008-05-22
Hi everyone, I'm starting to like Ubuntu more and more now.  A friend of mine recommended me try a diffrent o/s I booted it from cd, but I didnt like it much, so I am back to Ubuntu.  My only problem is, my laptop speakers are not working for some reason, but the headphone jack is.  And my Sandisk m240 doesnt work right, the strange thing is it reconizes it as a mp3 player but I cant find any of the files.  Is there a driver for it that I can install?  If I can get that working, there will really be no reason why I need windows any more.
Thanks for all the help you all gave me also.

---

### Post by jespdj on 2008-05-22
If you want help with solving the problem, it would be a good idea to provide some details, for example: What brand and model is your laptop? What version of Ubuntu are you running?

Also try searching for "<laptop brand name> speakers" or similar keywords.

Note that it's also a good idea to use a more descriptive title for your post than just "Ubuntu". How about: "Speakers not working on <laptop brand> <laptop model>"?

---

### Post by jras20 on 2008-05-22
I am running 8.04, My laptop is a Acer 5050, and the sound drivers are realtec high def audio drivers FOR VISTA (R170) that windows Vista used.  I got sound from the speakers using the other o/s.  And I can get sound using windows Vista.
Thanks

---

### Post by nick_h on 2008-05-22
Have you look at the stickies in the Multimedia & Video forum?

[Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by jras20 on 2008-05-22
That thread did the trick it works!!  Now I need to get my sandisk m240 mp3 player working!  Thanks a bunch!

---

### Post by nick_h on 2008-05-22
There is no driver you need to install.  Ubuntu will just treat your mp3 player as an external drive.  I saw your [other thread](http://ubuntuforums.org/showthread.php?t=802267), can you copy new files onto it?

Perhaps there are hidden files - have you tried CTRL+H in nautilus?

---

### Post by jras20 on 2008-05-22
I cant do anything with it, read or right.

---

### Post by nick_h on 2008-05-23
Have you checked the permissions?

To find the mount point, mount options and filesystem:
```
mount
```

Then check the permissions:
```
ls -ld /media/<mount point>
```
(replace <mount point> with the directory where it is mounted)

---

### Post by jras20 on 2008-05-23
> **nick_h said:**
> Have you checked the permissions?

To find the mount point, mount options and filesystem:
```
mount
```

Then check the permissions:
```
ls -ld /media/<mount point>
```
(replace <mount point> with the directory where it is mounted)

I'll check that out, that must be the problem, I just dont understand why my PSP works fine, digital camera, but that doesnt.  I can even load mp3s from my psp from windows to Ubuntu.  I'll look into that today and post results.
Thanks

---

### Post by jras20 on 2008-05-23
How do I find out where the directory is mounted?

---

### Post by nick_h on 2008-05-23
The output of the mount command will show you the mount point.

---

### Post by jras20 on 2008-05-23
> **nick_h said:**
> The output of the mount command will show you the mount point.

I guess you'll half to show me where it is:

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jras20/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jras20)

---

### Post by nick_h on 2008-05-23
I doesn't look like it is mounted.  Is it plugged in?

---

### Post by jras20 on 2008-05-23
> **nick_h said:**
> I doesn't look like it is mounted.  Is it plugged in?
oops no it wasnt..

---

### Post by jras20 on 2008-05-23
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jras20/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jras20)
/dev/sda2 on /media/ACER type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by nick_h on 2008-05-23
It is interesting that the device is just /dev/sdb and doesn't have a partition number.

What is the output of:
```
sudo fdisk -l
```

---

### Post by jras20 on 2008-05-23
I wonder if I am the only one using Ubuntu that has a Sandisk M240 mp3 player?

Here is the output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b6dd6a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275        5519    34097962+   6  FAT16
/dev/sda3            5520        9729    33816825    7  HPFS/NTFS

Disk /dev/sdb: 1016 MB, 1016856576 bytes
32 heads, 61 sectors/track, 1017 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by nick_h on 2008-05-23
It is interesting that no partitions are listed.

I did a search for "sandisk m240" and found a thread that may help - [Sansa m240 help?](http://ubuntuforums.org/showthread.php?t=480927).  Unfortunately it was solved by reformatting the device.

The good news is that there are some posts which say that the Sandisk M240 does work with Ubuntu.

---

### Post by jras20 on 2008-05-24
Unfortunately formating it didnt work either, it may not work for Ubuntu.  Everything else does.  My Digital camera, and the movie recorder, card reader, and my PSP.  I guess I could just start using my PSP as a mp3 player.

---

### Post by nick_h on 2008-05-24
I just found [this](http://ubuntuforums.org/showpost.php?p=3798461&postcount=118) post.  It's not for your model but may be worth a try.

Do a search for "sandisk m240" on these forums - it appears that some people have got it working.

---

### Post by jras20 on 2008-05-26
> **nick_h said:**
> I just found [this](http://ubuntuforums.org/showpost.php?p=3798461&postcount=118) post.  It's not for your model but may be worth a try.

Do a search for "sandisk m240" on these forums - it appears that some people have got it working.

Thanks I will look at it, the strange thing is, I can download mp3s to the mp3 player using it, but when I go to windows XP I cant see the mp3 files I downloaded, but on Ubuntu I can.  It loads the same thing in Ubuntu that it does in windows 2,000.

---

