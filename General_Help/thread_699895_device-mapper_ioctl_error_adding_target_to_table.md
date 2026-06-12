---
title: "device-mapper: ioctl: error adding target to table"
date: 2008-02-17
forum: General Help
---

### Post by FishFoot on 2008-02-17
I'm getting a strange issue when booting my Dapper Server:

1) I see messages that read:
device-mapper: table: 254:2: linear: dm-linear: Device lookup failed
device-mapper: ioctl: error adding target to table

2) The system boots, but to a recovery shell.  I'm told the superblock is bad on the boot partition (/dev/hda) and that I should try to recover it.  I have tried with mixed success (it seems to work but I continue to see this problem). However, whether I try to repair or not, if I press control-D the system will boot fine.  The /boot partition will not be mounted.

3) Here's what's really wierd, sometimes when I boot the primary hdd is seen as "hda" other times "sda".  It is a Parallel ATA (PATA) disk.

4) The root partition is LVM, the boot partition is not.  They are on the same physical disk.

-----
The machine is in a strange state.  I have an eSATA drive connected to the machine but Dapper doesn't fully support hot-swapping eSATA connections.  To remedy this I tried building a custom kernel but I couldn't get support for my SATA card to build into the kernel.  Since the Gutsy Kernel supports my hardware I just grabbed the Gutsy Kernel Package and used dpkg to install it.  This worked surprisingly well and the system seemed fine for a while.

After doing some research I'm pretty sure the problem is similar to what people are talking about on this thread:
[http://ubuntuforums.org/showthread.php?t=587450](http://ubuntuforums.org/showthread.php?t=587450)

Basically they say to remove evms as it isn't necessary anymore, they all seem to agree that this fixes the problem.  I attempted this and ended up with a non-bootable system.  My root (LVM) partition was not seen.  I was able to remedy this with a recovery console by re-installing evms and running dpkg-reconfigure on the lvm package.  That returned me to the state described above.

I'm fairly certain that evms is the problem here, and I'm also fairly certain that I can't remove it because the rest of the (dapper) system is dependent on evms (in some way).

If anybody could help out with a thought as to how to fix this (or even what is going on) I would be most appreciative.

Thanks
FishFoot

---

