---
title: "Gparted creates or leaves unmarked space in USB sticks"
date: 2016-01-24
forum: General Help
---

### Post by jtl2 on 2016-01-24
Recently Gparted has started to create or leave unmarked empty space in USB sticks. In two sticks the corrupted(?) space is 8 MB and 17 MB respectively.
This space is not empty but is rendered unusable. Is there a bug that corrupts USB sticks in this way?

I have overrun the sticks by writing zeros on them. After I try to create new partitions with Gparted, the mysterious region reappears and is seen 
in USB stick properties (have a look at the attached image).

The problem seems to affect ext4 partitions in particular.

I reinstalled Gparted with no improvement. Should I change Gparted settings - and how should I do that?

I am using an up-todate Linux hp 3.16.0-59-generic #79~14.04.1-Ubuntu with (also u-ptodate Gparted 0.18.0.0-1
that comes with the distribution.



Thanks very much for you help.

---

### Post by HermanAB on 2016-01-24
1. If you are using the schticks on Linux, then you don't really need partitions at all, you can just run mkfs.ext4 or whatever and format them without a partition.

2. Try fdisk.

---

### Post by pqwoerituytrueiwoq on 2016-01-24
if you are referring to a part of the storage that shows up used even with no files that is normal for all storage devices
you may be referring to a 1mb it does not allocate at the start of a partition, i think that was done for SSDs or something
if you really need that single MB so badly you can use a old version of gparted, say on a old 10.04 live cd

---

### Post by jtl2 on 2016-01-24
Ok, thanks for your good-natured comments.

I found a reasonable solution:

sudo tune2fs -m 1.0 /dev/sdxy

at [http://forums.fedoraforum.org/showthread.php?t=300961](http://forums.fedoraforum.org/showthread.php?t=300961)

The command above reduces the amount of space the ext4 file
system reserves for itself. The reserved space goes down from 5% to 1%
of the USB schtyckie volume.

I think previously my Nautilus did not show that space in the
USB szticke properties.

Hereby, I consider the issue solved and feel much relieved.

---

