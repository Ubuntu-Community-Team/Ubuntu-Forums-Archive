---
title: "Hard Drive Issue"
date: 2012-12-24
forum: General Help
---

### Post by stonkers on 2012-12-24
Hi all!  I have a machine built with 2 1 TB hard drives.   I'd like to mount this as available but pretty new to the unix admin stuff.  Can someone give me a little advise on how to go about this?
```

root@fetzerUbuntu:/# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc2e04504

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120330   966550693+  83  Linux
/dev/sda2          120331      121601    10209307+   5  Extended
/dev/sda5          120331      121601    10209276   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
```

So I need to what?  Format sdb, mkfs with sdb, mount sdb, put sdb in fstab?  Any direction would be awesome!

Thanks,
Eric

---

### Post by ryanyeah on 2012-12-24
> **stonkers said:**
> 
So I need to what?  Format sdb, mkfs with sdb, mount sdb, put sdb in fstab?  Any direction would be awesome!


You will need to create a partition, format it, then you can try mounting it manually and then add it to /etc/fstab. You can use gui tools to do this, else cli. So, you could just run fdisk /dev/sdb and then press "n" to create a new partition, and then follow the prompts (use defaults if you're going only making a single partition, and make sure it's a primary one (not logical). 

Then you can run mkfs -t ext4 /dev/sdb1 (replace ext4 with whatever fs you want).

Then you can run "mount /dev/sdb1 /exampledirectory". 

Next you can use the "blkid" command to bring up the UUID of the drives to add the line to fstab. There are some good instructions: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Bashing-om on 2012-12-24
eric; Hi !

You have the right ideas. No one can tell you exactly how you want to set up your system. Partitioning is a personal use thing.
Pointer: If you intend to use the additional disk for only storage, I suggest that you do not mount it (after prep and filesystem and files copied to it) to fstab. But to mount it manually on demand; thereby isolating it from the filesystem in general- if the system crashes does not take the data with it. That way the data is always accessable in any event. But, I am multi-booting.

These links provide the instructions and tutorials on all you need.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
I prefer the command line method myself(in the 1st link) using fdisk and mkfs to prep my disk. Easy as 1-2-3, just be sure of what you do before you do it (the 7 p's always apply !)
[INDENT][INDENT]good reading <== BDQ

[/INDENT][/INDENT]

---

### Post by Mopar1973Man on 2012-12-24
Give you an idea... Like you I'm also close to you in design I've got both a 1.0 TB and 1.5 TB drives. I use the 1.0 TB for my Windows and Linux partitions and then the remaining is left for storage partitions.

This is the layout but on my laptop (640 GB) but the partitions are just larger on my main machine...

[IMG]http://forum.mopar1973man.com/attachment.php?attachmentid=4820&d=1355945290[/IMG]

Then I left the 1.5 TB drive alone and using Grsync / Rsync to backup the partitions to the 1.5 TB as a backup drive. 

Instead of manually editing Fstab I fell in love with Webmin for doing most of my Admin Control Work. ;) (Great for Noobies to be able to get the job done)
[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by stonkers on 2012-12-29
Sweet, thanks for all the replies.  It's all mounted and persistent!

---

