---
title: "Grow partition without moving data?"
date: 2013-12-06
forum: General Help
---

### Post by blazie151 on 2013-12-06
So after a huge amount of work getting this external HDD where I need it by changing around filesystems, moving data, creating and deleting partitions, etc., I'm now stuck with 170GB of unallocated space inbetwwen my 2nd and 3rd partitions, and would like to grow my 3rd partiton (EXT3) to use up the free space before it. However, since I've already had to do an insanely large amount of read/write operations to this disc, I'm trying to find out if I can simply extend the partition over to the left without moving the data as gparted is trying to do. I can use any livecd or OS required to do this, just want to prevent another 90GB of useless file transfering. I understand gparted uses resize2fs which doesn't allow a grow without a move first, so another method is required. My partition table is listed below...

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60c7b90b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     2162687     1080320   83  Linux
/dev/sdc2         2162688     2293759       65536   82  Linux swap / Solaris
/dev/sdc3       360263680  1324490751   482113536   83  Linux
/dev/sdc4      1324490752  1953523711   314516480   83  Linux

The partition I'd like to extend to the left is /dev/sdc3 to fill the free sectors bewteen it's own start at 360263680 and sdc2's end at 2293759. I'd like a way to do this non-destructively. Any ideas?

---

### Post by blazie151 on 2013-12-06
bump... This is a data only partition, so no boot problems, just simply resize a partition.

---

### Post by VMC on 2013-12-06
A suggestion would be to clone sdc3 using Clonezilla. Then delete sdc3, and grow it to its fullest. Then using clonezilla, restore the partition. If you do that you need to copy the UUID, and afterward using 'tune2fs -U' to copy the original UUID back. I've done it this way before with success.

Or another route is just increase the size to the back-end of sdc2. I would advise NOT to use Gparted to do this. It takes forever.

'cfdisk' is another tool to do this. Its what I use, but you need to precede with caution.

Cloneing with Clonezilla will at least save your data. But Clonezilla needs to restore to the same partition that it cloned. Or partclone can move it to another number.

---

### Post by blazie151 on 2013-12-06
Method A with Clonezilla appears to be what I'm avoiding - unnecessary wear and tear on the disk by needlessly copying it off the partition then copying it right back a few (thousand) sectors earlier.

Increasing the size to the back end of sdc2 is what I'm trying to accomplish, but I'm avoiding gparted and resize2fs as they both seem to require needlessly moving the existing data to the beginning of the newly enlarged partition.

I looked up cfdisk and didn't see how it would let me accomplish this without data loss or data migration to the beginning of the partition, maybe I missed something?

---

### Post by blazie151 on 2013-12-07
Anyone else trying to do this just create a new partition in the blank  space to the left, then transfer the data over, delete the later  partition and grow the space to the new free space on the right. Even  though you can resize the PARTITION with other tools in an attempt to  avoid moving the data around, you cannot resize the FILESYSTEM without  resize2fs, which I could not find a way to avoid moving data around with  (or even get it to work when the beginning of a partition was moved  instead of the end of one). Long story and a headache short, if you don't  want to lose it, transfer it off and back or do what I described above.

And  if all your partitions are out of order when you're done (like mine  were, sda4 was before sda1), run "sudo fdisk /dev/sdx" where x is your  drive, type "x" + enter, "f" + enter", then "w" + enter. It will reorder  your partition table to match the partition order on the disk without losing  any information. VERY useful after using gparted, parted, partition  wizard, or any other partitioning software that leaves your partitions  out of order (though keep in mind moving your partition number also  requires changing your boot.ini or fstab to reflect the change, so  beware on boot partitions). Anyway, thanks for the help, I'm all sorted  out now. Hope this helps others in my scenario.

---

