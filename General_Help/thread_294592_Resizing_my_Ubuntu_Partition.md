---
title: "Resizing my Ubuntu Partition"
date: 2006-11-06
forum: General Help
---

### Post by 00Sven on 2006-11-06
I am trying to resize my Ubuntu partition on my hard drive. (less space for Windows!)  I keep running into errors when trying to resize though.  Example:> Error #1225
Block 590337 used, but not marked used in bitmap> Error #1201
Ext2 superblock contains illegal informationIs there a "scandisk"-like utility for Ubuntu that would fix this?

---

### Post by ReaderRat on 2006-11-06
Are you trying to resize from the right side of the partition or the left side? I know, with Windoze, you cannot resize from the right.

---

### Post by 00Sven on 2006-11-06
I have my Windows partition and then free space and then my Ubuntu partition.  I am trying to add the free space my ext3 partition.  Is there any way to do this from Ubuntu?

---

### Post by chalex on 2006-11-06
You can look into the command resize2fs.  Ext3 filesystems can be grown online, that is, without having to be unmounted.

Keep in mind that you have to resize the partition, then resize the filesystem, unless you're using LVM, in which case you also have to adjust the the volume groups and logical volumes.

I'm not familiar with the graphical tools.

---

