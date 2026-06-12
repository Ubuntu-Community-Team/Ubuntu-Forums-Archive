---
title: "Partitioning external drive for backups"
date: 2007-07-31
forum: General Help
---

### Post by Steven_B on 2007-07-31
A similar question was asked here, but didn't get any response: [http://ubuntuforums.org/showthread.php?t=451373]("http://ubuntuforums.org/showthread.php?t=451373")

Note that this is a hypothetical question; I don't have any of the mentioned hardware yet.
I have a 120 GB external USB hard drive.  I would like to use 80GB of it as an exact backup of my internal drive (which will include a dual-boot setup).  Can I do this, and still leave the remaining 40GB for other use?

I would also like to be able to boot Ubuntu from the drive.  This would be separate from the above backup.  It would need to run on many computers - I assume I would do something like copying a LiveCD onto a bootable partition?

I also want to keep my main and external boots synchronized: The same home folder data, same software installed, etc.  However, I do not want these two copies of Ubuntu to be identical - they might need different graphics drivers, GRUB configurations, etc.
How would I go about doing this?

Thanks!

---

### Post by eggdeng on 2007-07-31
```
I would like to use 80GB of it as an exact backup of my internal drive (which will include a dual-boot setup).
```
You might look into using partimage to create this, I know it has an option to include the MBR with the image, which you could store on a logical partition on your external disk. I don't know if it can deal with partitions of that size though.

---

### Post by Steven_B on 2007-08-01
It looks like dd may be what I'm looking for the backup part, since it can make a bit-for-bit copy of the source drive.  [http://wiki.linuxquestions.org/wiki/Dd]("http://wiki.linuxquestions.org/wiki/Dd")

Any ideas for keeping two copies of Ubuntu synchronized?

---

