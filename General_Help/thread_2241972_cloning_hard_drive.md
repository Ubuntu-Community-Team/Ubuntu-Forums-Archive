---
title: "cloning hard drive"
date: 2014-08-29
forum: General Help
---

### Post by Autodave on 2014-08-29
I have a machine running Xubuntu 14.04. Everything works great, but the HD is very noisey.  I have another HD available that is a little smaller, but way big enough for what is needed.  I can either install it side by side in the machine or hook it up through a USB adapter.  What is the best way or program to use to make a copy that will have everything (files, pics, passwords, etc.) copied to replacement drive.

Thanks in advance!

---

### Post by TheFu on 2014-08-29
fsarchive

---

### Post by claracc on 2014-08-30
Perhaps clonezilla?: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by The Spectre on 2014-08-30
Redo Backup & Recovery...

[http://redobackup.org/](http://redobackup.org/)

[IMG]http://redobackup.org/media/screenshots/3.jpg[/IMG]

---

### Post by TheFu on 2014-08-30
He's trying to go from partition A+ to partition A-(smaller) - fsarchive is the only cloning tool that does that.

Backups that are NOT image based can be used too - so any backup/restore software can work. There are 500 of those. Which is the "best" is completely subjective.

Or - he could shrink the partition(s) on the current HDD to a size that fits on the new HDD, then use cloning software.  The tricks are:
* ensure both HDDs are either 4K sector or both 512b sector drives. This is important.
* create the exact same number, sized and types of partitions - primary for primary, logical for logical, and make the new partitions at least 1 sector larger than the source partition if there is any question.
* Put the exact data in each partition in the newly created, mirrored partition - sda1 --> sdb1, sda2 --> sdb2.  You get the idea.
* You'll get to re-install grub - so be prepared for that.
* And lastly, you'll get to edit the /etc/fstab on the new HDD for the new UUIDs.  Disks can be specified in the fstab by device, label, UUID, or path-to-the-disk.  Each of these are handy in different situations.  I suspect it is easiest to manually fix when we use /dev/sdb2 or /dev/sda1 for humans trying to fix a boot and get a system running.  UUIDs are smart a day or two later, but since a UUID will be unique based on drive information and partitioning, it is harder to get correct until after the system is running later.
* UEFI system might be a little harder - there will be more partitions involved.

Does all this make sense?

For more detailed help, posting the link to a **boot-info** run wuold be helpful, but if the stuff above makes sense to you - go for it - be certain to have a good backup -- oh - forget that - just don't trash the source disk. l)

---

