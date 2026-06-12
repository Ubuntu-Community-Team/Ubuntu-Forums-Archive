---
title: "edgy eft: udf discs wrongly automounted as iso9660"
date: 2007-02-02
forum: General Help
---

### Post by stefano75 on 2007-02-02
Hi,
When I put a UDF formatted DVD or CD disc in the drive of ny laptop, the disc is always auto-mounted as a normal iso 9660 disk.
If I want mount udf I have to manually unmount it and remount with:
mount -t udf ...etc.

In my fstab I have the line:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

but it seems useless because I think that some daemon, probably HAL, gets rid of it.

Anyone has the same experience?

TIA.
Stefano

---

### Post by apfsdsdu on 2007-02-05
I have a similar problem with UDF formatted USB sticks. They automount as vfat, and must be manually remounted as UDF. Does any UDF formatted media automount correctly?

---

### Post by satanius on 2007-02-08
I had the same problem. When manually mounting udf disk, it says that can mount only in read only mode. So i thought i could try adding read only option into fstab, and it worked! My fstab dvdrom line now looks like this:

/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0

and it all works ok, it mounts udf and iso9600 disks automatically when inserted, and burning also works (i tried only cd burning, haven't got any rw dvds at the moment). I hope this helps.

---

