---
title: "3ware RAID 5 issue (need advice before I blow up array by mistake)"
date: 2018-10-16
forum: General Help
---

### Post by Andrew_Benjamin on 2018-10-16
Thanks for taking the time to read, and hopefully to calm my fears (I think the answer really may be the obvious).

I have a RAID array which is reporting unused space via fdisk -l and gparted.  I'd like to reclaim the space, but before I do, I'd like to assure myself that I'm not going to blow up my array because I made an idiot move.

Details:
I have a 3Ware 9750-8i hardware RAID controller in my basement server.  Attached to the card are 4 4TB WD RED NAS drives.
I ran 'sudo fdisk -l' and it reports the following:

Disk /dev/sdc: 10.9 TiB, 11999967707136 bytes, 23437436928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B5A1A48A-215E-4856-BC21-E197F57EC89D


Device     Start         End     Sectors  Size Type
/dev/sdc1   2048 15624955903 15624953856  7.3T Linux filesystem

In the 3ware utility 3dm2, each drive reports itself to be 3.64 TB.

This tells me that I created a 4 drive array (3 data, 1 parity) but that 1 drive is not being used for the array storage on /sdc1 (10.91 - 3.64 = 7.3).

If I run gparted, it informs me that there is unused space available (the 3.64) and that it can 'fix' the problem by expanding the partition.

Question:  Is there *any* reason why the array topped out at 7.3TB and that I *shouldn't* do the expansion?

I've got a lot of data on the array and if I blow it up, my wife will be searching for divorce lawyers.  I presently don't have a machine to which I can offload the RAID array data, so a backup is not possible at this time.

Help?

Andrew

---

