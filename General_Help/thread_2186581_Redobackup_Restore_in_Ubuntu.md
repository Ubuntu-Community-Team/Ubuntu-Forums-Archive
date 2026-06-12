---
title: "Redobackup Restore in Ubuntu"
date: 2013-11-08
forum: General Help
---

### Post by Redalien0304 on 2013-11-08
I have made 2 Backups. 1st Cloned my Ubuntu 13.04 Partition - Swap Partition. Used Gparted 16 Livecd/usb & just cloned my partition to my External Usb Drive. 2nd Used RedoBackup to make a Backup my Ubuntu 13.04 partition + Swap Partition to External Usb Drive. Now Question is with RedoBackup can i Restore my Partition or Individual Files from Ubuntu itself not the livecd?? can i extract individual files??  Thanks in Advance.

---

### Post by mastablasta on 2013-11-08
i am not sure about individual files (i've been wondering about this myself just today), but yes you can restore the whole partition.
[http://linuxtweaking.blogspot.com/2011/01/how-to-use-redo-backup-and-recovery-to.html](http://linuxtweaking.blogspot.com/2011/01/how-to-use-redo-backup-and-recovery-to.html)

it would be best to run restore option and then see what options it gives you.

also for individual files you might be able to extract them out form the image with some archive manager. i never tried it.

---

### Post by Paddy Landau on 2013-11-08
RedoBackup is designed *only* for full-disk backup and restore.

It cannot restore individual files, nor can it restore individual partitions.

If you restore to a disk, RedoBackup will erase the *entire* target disk before restoring.

You can use [CloneZilla]("http://clonezilla.org/") (not as user-friendly as RedoBackup) to back up and restore individual partitions as well as entire disks.

For individual files, you need a different backup program.

---

