---
title: "How can I format a HDD partition w/o messing up my linux installation?"
date: 2013-01-04
forum: General Help
---

### Post by arashiko28 on 2013-01-04
I have a partition with windows 8, I installed it just to check it out and now I don't want it. How can I delete it (format) without damaging my Ubuntu installation?

In Gparted I see sda1 (system reserved), sda2 and sda3 (extended), but sda3 is linked to the ubuntu install, probably because windows 8 does not allow to make HDD partitions via ubuntu installer an hugs 1/2 of the HDD capacity for itself, which is one of the reasons I don't want it anymore.

Do I really have to reinstall Ubuntu?

---

### Post by grahammechanical on 2013-01-04
> Do I really have to reinstall Ubuntu?

I do not think so. You need to clearly identify those Windows partitions and the Ubuntu partitions. There should be at least two for Ubuntu. One for Ubuntu that is formatted as EXT3 or EXT4 and the other for Swap.

Do not delete that Extended partition because If Ubuntu is not inside the extended partition then swap will most certainly be there.

If you are sure that you have two Windows partitions and Ubuntu is inside the Extended partition,  then you can

1) delete one of the two Windows partitions.

2) shrink but do not delete the remaining or last Windows partition.

3) Expand the Extended partition to take up the unallocated space.

4) Expand the Ubuntu partition to take up all the space in the Extended partition.

If Ubuntu is in one of those partitions outside of the Extended partition then it is in a primary partition and you can expanded it to take up all the unallocated space left over from deleting the Windows partitions.

Do not forget to run

```
sudo update-grub
```

to remove the Windows entry from the Grub menu.

Regards.

---

### Post by offgridguy on 2013-01-04
grahammechanical; thank's for the grub update tip, this is a step i have been missing.

---

