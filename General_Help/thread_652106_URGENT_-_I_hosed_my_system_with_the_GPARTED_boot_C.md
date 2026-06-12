---
title: "URGENT - I hosed my system with the GPARTED boot CD"
date: 2007-12-28
forum: General Help
---

### Post by sefs on 2007-12-28
Hi

I was trying to resize a partition and make the swap file bigger with GPARTED someone during the rezied for swap it got an error and i clicked on close, Now when I run Gparted it shows all the partition space as unallocated.

The system still boots as normal and the files still seems to be there... for the most part....How do undo this thing that Gparted has done.

Thanks.

---

### Post by NoVista on 2007-12-28
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Where_to_get_Your_Super_Grub_Disk)

Hope it helps you.

---

### Post by ThrashJazzAssassin on 2007-12-28
If you've lost data due to partition problems, look in to a program called TestDisk.

---

### Post by ugm6hr on 2007-12-28
```
sudo fdisk -l
```

If your data is intact, but GParted can't see the partitions properly, your partition table is probably messed up.

This command will list the partitions for you.  If it returns an error, then that is the problem.

I can't remember for sure - but I think there is a way to fix it, I'm just not sure how.

---

### Post by sefs on 2007-12-28
Hi again,

I remembered i had backed up the partition and extended with dd.  And restored it with dd.  But is this enought?

Because when I run fdisk -l  it returns no data at all

cronkey seems to be picking up the partitions somehow.  And the partitions are showning up in qparted and gpareted correctly again after the restore.  

But as I said no results are returned from an fdisk -l

Did i have to specifiy a disk with that like /dev/hda?

Thanks.

---

### Post by ugm6hr on 2007-12-28
On my system *sudo fdisk -l* returns all drives.

You can add* /dev/sda* or *dev/hda* to the end to see if it helps.

```
man fdisk
```
tells you everything you need to know about fdisk.

---

### Post by sefs on 2007-12-28
I think i forgot the sudo... will try later.

---

