---
title: "fsck"
date: 2013-12-24
forum: General Help
---

### Post by hiig on 2013-12-24
Exactly how do I use this when the drive is mounted? Basically, I want to do the equivalent chkdsk /r on an Ubuntu-server virtual machine, and since I can't unmount the drive, how do I schedule one on boot?

I tried the instructions here:

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

But the 'check' was no more than 5 seconds. I'm pretty sure it takes more than 5 seconds to go through 80 GB

---

### Post by Lars Noodén on 2013-12-24
fsck would likely break the filesystem if run on a mounted system.

What file system are you using?  EXT4 is journalled and as such fsck can blow through the partition [quite fast](http://kernelnewbies.org/Ext4#head-9a25213c5b924bdb8b33efbcb91bfa1279bd2b00).  As a result, the checking might really take only a few seconds.  That was one of the design goals of the file system.

---

### Post by hiig on 2013-12-24
I don't remember, but I think it was EXT4. It was EXTsomething, anyway. In any case, I've got two hard drives. My host is Windows on drive 1 in the C partition. My virtual machine program runs off the D partition in drive 1, and I have the entire drive 2 unmounted and dedicated to the virtual machine. I've already checked both partitions on drive 1, and they are clean, and all symptoms point to something being wrong on drive 2. Or at least, something wrong with the data in drive 2. After disk activity starts up, the entire system becomes horrendously sluggish, on both the guest and the host, to the point that the mouse doesn't even move on the host for many seconds at a time. I was in the middle of upgrading to 13.10 when I was forced to do a hard reset, so I think I've also killed it.

---

### Post by ajgreeny on 2013-12-24
fsck will only really work on Linux filesystems such as ext#, not on windows filesystems.

I do not know if the fact that this seems to be a virtual filesystem OS will make any difference, but you can make fsck run at next boot by using command ```
sudo touch /forcefsck
```
I am also completely baffled by your description of the drives you have, so it may be simplest to run the command ```
sudo fdisk -l
``` and show us the output of that before we tell you to do something that is not possible

---

### Post by oldfred on 2013-12-24
I think the typical fsck with ext4 only runs the full fsck if the partition has issues flagged.

You have to run fsck from a liveDVD or flash version.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by hiig on 2013-12-24
It had its own dedicated drive, so it was a proper EXT partition, not EXT on NTFS.

Regardless, my hard drive just died, so I found the cause.

---

