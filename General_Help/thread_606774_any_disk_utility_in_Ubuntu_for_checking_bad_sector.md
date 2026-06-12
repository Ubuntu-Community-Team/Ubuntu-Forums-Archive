---
title: "any disk utility in Ubuntu for checking bad sectors?"
date: 2007-11-08
forum: General Help
---

### Post by ayet on 2007-11-08
just want to ask this if theres any, inwindows you have scandisk, what about ubuntu

---

### Post by etola on 2007-11-08
have you tried fsck ?

---

### Post by az on 2007-11-08
Fsck only looks at the filesystem.  Badblocks checks the media itself.

sudo badblocks -s -n /dev/sda1

Where sda1 is the partition you want to check.

Blocks are what some people call sectors.  A block is the smallest functional unit of a hard drive.  Technically, a sector is like a slice of pie.  A block is one slice from one track.

---

### Post by Niniel on 2007-11-08
When I fired up my machine yesterday, it did an fsck by itself during boot claiming it was doing it because it was the 25th time that the system had been booted without having run fsck. I thought that was kind of stupid. :) I never check my NTFS partitions, so why would Ubuntu insist on doing this every so many starts? Is the fs that vulnerable?

---

### Post by etola on 2007-11-08
> **Niniel said:**
> When I fired up my machine yesterday, it did an fsck by itself during boot claiming it was doing it because it was the 25th time that the system had been booted without having run fsck. I thought that was kind of stupid. :) I never check my NTFS partitions, so why would Ubuntu insist on doing this every so many starts? Is the fs that vulnerable?

I guess you never lost any data before due to disk failure... i did so it is ok with me....

---

### Post by atlfalcons866 on 2007-11-13
Modern Hard disk drives will automatically reallocate bad sectors to spare ones. It is useless running bad block scan.

---

### Post by Niniel on 2007-11-13
> **etola said:**
> I guess you never lost any data before due to disk failure... i did so it is ok with me....

Disk *failure* is something completely different. No software going to protect you against it. All you can do is minimize data loss with RAID and/or frequent backups.

---

### Post by fjgaude on 2007-11-13
> **Niniel said:**
> When I fired up my machine yesterday, it did an fsck by itself during boot claiming it was doing it because it was the 25th time that the system had been booted without having run fsck. I thought that was kind of stupid. :) I never check my NTFS partitions, so why would Ubuntu insist on doing this every so many starts? Is the fs that vulnerable?

The filesystem itself is super reliable, it's your drives that may not be. If you wish to ckeck less often do this for checking every 70 boots:

```
sudo tune2fs -c 70 /dev/sd[nn] (0 turns it off)
```

where [nn] is your drive letter and partition number for the boot disk.

Have fun.

---

### Post by Niniel on 2007-11-14
Oh, that's neat trick. I shall most certainly put this to good use, thanks a lot!

---

