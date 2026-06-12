---
title: "Delete all partitions on hard drive"
date: 2006-12-19
forum: General Help
---

### Post by shane_on_u on 2006-12-19
I have an external Acomdata E5 HybridDrive. The drive came preloaded with a bunch of junk on a separate partition (I think). The partition mounts as a CD-ROM drive which they intended to do so that it would remain read-only. Since I don't use windows I really don't have any use for the stuff on this CD partition. I would really love to recover that 200MB that this partition is eating up. Anyone know how I can get rid of it? Under gparted I only see the main partition for the hard drive. The CD-Rom partition obviously doesn't appear. I do see it under my fstab listed as this however:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Anyone have any ideas?

---

### Post by raul_ on 2006-12-19
Maybe formatting the whole disk? Did you try to unmount the drive in GParted?

---

### Post by Sef on 2006-12-19
It's a permissions issue if it is read only.  Would have to change it to read/write.   Not sure how to do it, and don't have the time to seach now.  Check the forums or check [google.com/linux]("http://www.google.com/linux") or [ask.com]("http://www.ask.com"), if you can't find it in the search here.

---

### Post by shane_on_u on 2006-12-19
> **raul_ said:**
> Maybe formatting the whole disk? Did you try to unmount the drive in GParted?

Tried that. Problem is the cdrom partition doesn't show up here, so when I unmount the drive, it only unmounts the hard drive portion. The "cdrom" is still mounted.

---

