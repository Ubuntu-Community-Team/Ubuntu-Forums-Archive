---
title: "filesystem on a thumb drive?"
date: 2008-05-14
forum: General Help
---

### Post by bodhidharma on 2008-05-14
Friends,

I have a thumb drive I use to carry files around between Ubuntuboxes,
and I have, just by reasons of inertia, kept the original formatting,
filesystem types, etc.  I wonder -- can I reformat this, repartition
it, yaddayadda?  Could I make a small vfat partition (in case I need
to transfer something to a Windoze box) and then a large ext3
partition, so that it is easier to transfer files back and forth
between Linux boxes?  Or is there some problem with multiple partitions
on a thumb drive... in which case I would go with one big ext3
partition... unless there is some problem with re-typing the partition,
or with ext3 on flash memory drives, or something else anyone can think
of that would advocate against that.

Any thoughts?

Thanks!

---

### Post by az on 2008-05-14
You certainly can partition a usb flash drive.

I would recommend you make the fat16 first at the begining of the drive and then make the rest an ext3 partition.  Windows will not see the fat partition if it comes after the ext3 one.


You can even put a bootable live cd on a fat partition and a persistent home on the ext partition.

---

