---
title: "Can't mount drive after zeroing superblocks"
date: 2013-01-16
forum: General Help
---

### Post by kwbbpc on 2013-01-16
So, for whatever reason that I can't now remember, I zeroed out the superblocks on a Raid-1 array that I had on an old system before moving the drives to a different system.  Now, some months later, I'm trying to get the data off just one of the disks that was part of the Raid array on a different system.  The drive shows up as /dev/sda1 and 'Linux raid autodetect' type drive with fdisk.  

However, I can't mount the drive at all, even when I specify the filesystem type with "mount -t ext4 /dev/sda1 /mnt/mntpt".

I've tried to re-create the Raid array with mdadm by using "mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 missing".  The array gets created, but when I try to mount it with "mount -t ext4 /dev/md0 /mnt/mntpt", I get claims that the fs isn't correct.

I've also tried to use "e2fsck -f -b XXXX /dev/sda1" to try to repair the superblock on the device (XXXX is any of the blocks specified by mke2fs), but none of the blocks listed appear to work - e2fsck claims the superblock can't be read or does not describe a correct ext2 filesystem...

I'm running dry on ideas for what can be done to get the drive back in working order... any help would be appreciated.

---

### Post by SaturnusDJ on 2013-01-24
You are mixing up raid and filesystems now.

When zeroing a superblock we're talking about the raid part.
The (re)create is the safest fix, but you also need to do this in the right order, with the correct superblock version (read about this) and preferable with the --assume-clean flag.

Try this:
```
mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sda1 --assume-clean
```
If this doesn't work, chances are small you'll get your stuff back. But because this is raid1 there might be a way of omitting the raid portion.

---

