---
title: "EXT4 to XFS?"
date: 2012-12-13
forum: General Help
---

### Post by Phixion on 2012-12-13
Hey guys, I currently use a 10GB "/" and remainder in "/home"

I am looking to change my "/home" directory from ext4 to XFS.

Can anyone please advise on how to do this please?

Many thanks.

---

### Post by CharlesA on 2012-12-13
Why do you want to change?

---

### Post by Phixion on 2012-12-13
Because I've attempted to tune EXT4 and I'm still not happy with the results, I'd like to try XFS before I settle with EXT4.

---

### Post by Cheesemill on 2012-12-13
There is no way to do an in place conversion, you would have to:

[LIST]
[*]Boot from a Live CD
[*]Copy all your data to a new device.
[*]Reformat the partition as XFS.
[*]Copy all of the data back.
[*]Update /etc/fstab on your root partition with the new UUID of the XFS partition.
[*]Reboot and keep your fingers crossed :)
[/LIST]

---

### Post by oldfred on 2012-12-13
You may  also have to manually download some other tools to run things like fsck as e2fsck is only for ext4.

Overall ext4 seems best, only for very specific tasks do other file systems win on a test.
       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by LewisTM on 2012-12-13
The **xfsprogs** package contain the check/repair tools as well as xfs dump utilities for backup purposes. You'll need it eventually because Ubuntu schedules periodic disk checks on boot. Without the packaged fsck.xfs (which does nothing, successfully), your home partition will refuse to mount at boot.

Cheers!

---

### Post by Phixion on 2012-12-13
OK so I managed to change my /home partition from EXT4 to XFS, problem is when creating the XFS partition I get the following error:

warning: device is not properly aligned /dev/md2

I've read up on this but for the life of me can't find a solution.

Anyone? :(

---

### Post by CharlesA on 2012-12-13
Is the home partition a raid array?

---

### Post by Phixion on 2012-12-13
Yes it is, "/" is RAID1 and "/home" is RAID0

---

