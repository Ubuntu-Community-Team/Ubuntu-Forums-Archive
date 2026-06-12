---
title: "Looking for backup options"
date: 2007-09-29
forum: General Help
---

### Post by sippyCUP on 2007-09-29
I run a fesity fawn/winxp laptop with linux as my primary OS. It's taken me a lot of work to get everything just how I like it, and I want to perform weekly full backups. I have acronis trueimage on my xp install and had been using that, but it's been flaky lately and rebooting spontaneously.

To be clear, I want something that will make an exact image of my disk. NTFS partition, ext3 partition, mbr, partition tables, everything.

I'm definitely not afraid of using dd, but I read that you have to restore it to the exact same size and type of disk, and if my disk fails it's unlikely that I'd want to or even be able to get an exact replacement. I read about Tivoli but it seems very network oriented and I don't even know if it'll do a regular ide disk to usb2 disk backup.

Anyone have any suggestions?

---

### Post by bodhi.zazen on 2007-09-29
I personally use partimage , which will back up your partitions.

I then :

```
sudo sh -c "fdisk -l > partion_table"
```

Save a copy of partition_table.

You can use this information to restore your partition table with fdisk in a snap

 [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Restore the partitions with partimage, restore grub

If this is too much for you, I understand, you might want to look at Clonezilla:

Clonezilla : [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

g4l (ghost for linux) : [http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

[http://ubuntuforums.org/showthread.php?t=500621](http://ubuntuforums.org/showthread.php?t=500621)

Loop mounted backups : [http://ubuntuforums.org/showthread.php?t=535669](http://ubuntuforums.org/showthread.php?t=535669)

---

