---
title: "Boots to initramfs prompt, btrfs.fsck returns signal 11"
date: 2013-04-30
forum: General Help
---

### Post by JebusWankel on 2013-04-30
My fairly new Raring install doesn't boot past the initramfs prompt. When I run fsck on a LiveUSB it returns with signal 11 every time. The partition in question is btrfs.

I don't see anything that sticks out as an error in the output before the prompt. Where would I find a relevant error/sys log? What can I do to fix my boot?

---

### Post by oldfred on 2013-05-01
I do not remember if it was btrfs or one of the other odd filesystems, but you have to use synaptic and download its equivalent for fsck as fsck does not support btrfs.

 BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE)

---

### Post by JebusWankel on 2013-05-01
Thanks but I don't think that's the case anymore. Signal 11 according to the man page means errors were found and fixed and a reboot is necessary.

I am thinking about just going back to ext4. I wanted btrfs for subvolumes and snapshots but ended up not using either. btrfs really lacks when it comes to fsck though.

---

