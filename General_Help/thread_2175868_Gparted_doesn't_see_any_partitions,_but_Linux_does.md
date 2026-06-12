---
title: "Gparted doesn't see any partitions, but Linux does"
date: 2013-09-21
forum: General Help
---

### Post by skamarla on 2013-09-21
I have an external USB disk, with one ext4 partition; the rest is unassigned. I can mount the partition just fine. Now, I want to create a second partition with the rest of the disk. So I fire up gparted, and, surprise, it reports the whole disk as "unallocated" (1.36 TiB).

Any ideas?

The relevant part of df -k:
```
/dev/sdb1             720944648 313806116  370509932  46% /mnt/wd

```

Fdisk says:
```

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002828e

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1              63  1465144064   732572001    0  Buida
/dev/sdb4   *           0           0           0    0  Buida
```

and mount says:
```
/dev/sdb1 on /mnt/wd type ext4 (rw)
```

This is a gparted screenshot:
[ATTACH=CONFIG]246412[/ATTACH]

Please help!

---

### Post by oldfred on 2013-09-21
Most of reasons for installer not partitions
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

If it was NTFS it could be chkdsk needed, but if you can mount the ext4, I would think gparted would show it. Was drive ever RAID or gpt partitioned? But usually it is Windows that does not handle gpt correctly.

If old RAID data.

 Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sdb

---

### Post by skamarla on 2013-09-21
I've tried fixparts on it, and I get the following:
```

$ sudo fixparts /dev/sdc
FixParts 0.8.4

Loading MBR data from /dev/sdc
Problem opening /dev/sdc for reading! Error is 2.
The specified file does not exist!

Unable to read MBR data from '/dev/sdc'! Exiting!

```
So the MBR is missing! Should I try the rescue option inside Gparted?

---

### Post by deadflowr on 2013-09-21
Does /dev/sdc exist?
I thought the disk was /dev/sdb.

---

### Post by skamarla on 2013-09-21
Oooops!!!!
My mistake. I had tried the disk on another system, where it was /dev/sdc. It's /dev/sdb now, of course, thanks for pointing it out!. This the *real* output of fixparts
```

FixParts 0.8.4

Loading MBR data from /dev/sdb

MBR command (? for help): ?
a       toggle the active/boot flag
c       recompute all CHS values
l       set partition as logical
o       omit partition
p       print the MBR partition table
q       quit without saving changes
r       set partition as primary
s       sort MBR partitions
t       change partition type code
w       write the MBR partition table to disk and exit

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 2930277168 sectors (1.4 TiB)
MBR disk identifier: 0x0002828E
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    63   1465144064   primary     Y        Y      0x00

```

---

### Post by oldfred on 2013-09-21
That does not look like any error. I might write just to refresh data.

---

### Post by skamarla on 2013-09-21
I can access data just fine. The only thing I can't do is to add a partition...

I've tried to write from Fixparts, and it's still the same. 

BTW, parted's output is:
```

$ sudo parted /dev/sdb print
Model: WD 15EADS External (scsi)
Disk /dev/sdb: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

```

I think I know what the problem is, though. The partition type is 0; shouldn't that be 83 (Linux native), according to [documentation]("http://www.win.tue.nl/~aeb/partitions/partition_types-1.html")?
```

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002828e

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1              63  1465144064   732572001    0  Buida
/dev/sdb4   *           0           0           0    0  Buida

```
"Buida" means empty in my language, BTW.

---

### Post by oldfred on 2013-09-21
You can use Disks or Disk Utility to change type but do not reformat.

Also command line if MBR.
 change sdb1 to type 83
sudo sfdisk --change-id /dev/sdb 1 83

---

### Post by skamarla on 2013-09-21
That did the trick!!!

Thanks a lot

---

### Post by oldfred on 2013-09-21
Glad you noticed the type discrepancy, I should have but missed it.

---

