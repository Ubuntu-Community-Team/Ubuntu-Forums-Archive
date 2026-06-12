---
title: "LVM Mounting problem"
date: 2006-09-09
forum: General Help
---

### Post by bothapn on 2006-09-09
Hi,
 
 I have the following problem:
 I cant mount my lvm
 My lvm consists of the following:
 fsx02:~ # lvm pvscan
 File descriptor 4 left open
 PV /dev/sda1 VG jackal lvm2 [232.88 GB / 0 free]
 PV /dev/sdc1 VG jackal lvm2 [232.88 GB / 48.00 MB free]
 
 Both partitions are ext3
 Mount cant determine the filesystem type. And fsck gives:
 Couldn't find ext2 superblock, trying backup blocks...
 e2fsck: Bad magic number in super-block while trying to open /dev/sdc1
 
 The superblock could not be read or does not describe a correct ext2
 filesystem. If the device is valid and it really contains an ext2
 filesystem (and not swap or ufs or something else), then the superblock
 is corrupt, and you might try running e2fsck with an alternate superblock:
 
 
 I need that data on those partitions. What can I do?
 I have numerously created and deleted the volume groups.. to no avail.
 
 If I could somehow convert the partition back to plain normal ext3 mount it, backup it and then redo the lvm.. it would be great.. is that possible?
 
 Plz! All ideas welcome!

---

### Post by KubuntuKilledMe on 2006-09-09
So it was working right up until you filled it up with your precious data and then stopped working? That's really bad luck.

Personally I did a 3 hard disk LVM volume for my storage server and then used reiserfs for the filesystem and never had a problem.

From what i understand, LVM does not significantly change the way data is stored on the disks, so common file recovery tools (for your ext3 filesystem) might save your data. 

Good Luck, i hate losing data myself.

---

