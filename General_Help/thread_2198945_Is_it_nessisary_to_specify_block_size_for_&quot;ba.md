---
title: "Is it nessisary to specify block size for &quot;badblocks&quot;?"
date: 2014-01-11
forum: General Help
---

### Post by nstgc379 on 2014-01-11
I've been running badblocks on a number of drives but I've never stopped to think if I need to specify the blocksize in order to get meaningful results. As far as I know, I'm not getting any errors because I have the wrong size specified (default of 1024). I doubt its an issue, and if it was I would be getting more errors not fewer, or so I reason. Also I'm not running it on a partition but rather an entire drive.

sudo badblocks -nsv /dev/sdX

---

### Post by tgalati4 on 2014-01-11
I don't think it really matters.  You can specify both the block size and the number of blocks read during each pass.  To the disk drive, the seek commands just spit out data.  If a data block cannot be read, then it will be listed, but the block number will be incorrect (because of the incorrect block size).  So if you are not seeing any output--that is a good sign--no bad blocks.  You can verify the sector size using *fdisk* or *smartctl*.

tgalati4@Mint14-Extensa ~ $ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
[B]Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes[/B]
Disk identifier: 0x66d07300

---

