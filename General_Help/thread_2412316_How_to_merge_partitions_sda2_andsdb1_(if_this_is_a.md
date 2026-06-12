---
title: "How to merge partitions /sda2 and/sdb1 (if this is a sensible idea)?"
date: 2019-02-11
forum: General Help
---

### Post by Bobby_James on 2019-02-11
I was surprised to see I was running out of hard drive space. A fdisk -l command showed:

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 976771071 975720448 465.3G Linux filesystem

However, I also have:

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1          63 1953520064 1953520002 931.5G 83 Linux

I am using /sda2 for my hard drive space. How would I access /sdb1 and - ideally - merge it with /sda2?

/etc/fstab (not sure if this is relevant) shows:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=xxx-yyy-zzz /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=aaa-bbb  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

Thanks!

---

### Post by yancek on 2019-02-11
In order to merge two partitions they need to be contiguous which is not possible in your case as the two partitions in question are on separate hard drives.  You might be able to do something with LVM but I've never used it so can't help with that.  lf the second drive partition (sdb1) is always attached you can simply create a mount point for it and an entry in fstab to mount on boot.  You can create a data partition on sdb1 on which you can put personal data and non-system files.

---

### Post by Impavidus on 2019-02-11
You can't really merge partitions on different hard drives. Well, there are some tricks using LVM and things like that, but that's another layer of complexity with the disadvantage that if one drive breaks, you lose the files from both, and you have to set it up before installation. You can't even merge partitions on the same drive, the best you can do is delete one and expand the other to take its place.

What you can do is mount sdb1 at some convenient place and store files there. Add it to your fstab:```
UUID=xxx-xxx-xxx /some/mountpoint ext4 some,options 0 2
```or something like that. Then all files you store in the directory used as a mountpoint will end up on sdb1.

It's usually recommended that you keep the OS in a relatively small partition (30GB or thereabouts) and store your documents on a larger one, used as a data partition or a /home partition. But you have at least 2 large partitions, so you'll have to choose what to put where.

---

### Post by oldfred on 2019-02-11
I have multiple Ubuntu installs and want same data in all of them. 
So I use a large data partition on HDD and smaller / (root) partition on SSD.

       [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Bobby_James on 2019-02-11
Thanks for the advice. Oddly, I can no longer find /dev/sdb1 with fdisk or gparted. Only /dev/sda.

I note from the details I saved earlier that dev/sdb1 appears to be a dos partition. The disk identifier does not look like the the UUID as for /dev/sda2.

Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00068d29

So what does this mean exactly? How do I find and use this partition when it no longer is discoverable? Thanks.

---

### Post by yancek on 2019-02-11
> Oddly, I can no longer find /dev/sdb1 with fdisk or gparted. Only /dev/sda.


The most likely reasons for this are the drive is not attached, the partition was deleted or the drive is going bad.  It is generally better to post the entire output of commands like fdisk.  Have you tried parted command to see if the partition shows, or the blkid command?  If fdisk and gparted don't show it I doubt the other commands will but no harm in checking.

> The disk identifier does not look like the the UUID as for /dev/sda2.

It's not expected to as disk identifier is for the drive and UUID for partitions.

---

