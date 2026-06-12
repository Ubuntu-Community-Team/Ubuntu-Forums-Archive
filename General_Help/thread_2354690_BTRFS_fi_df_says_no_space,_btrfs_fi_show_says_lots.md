---
title: "BTRFS fi df says no space, btrfs fi show says lots of space"
date: 2017-03-05
forum: General Help
---

### Post by 2twisty on 2017-03-05
I've been googling this for a while and searching the forum and I can't seem to find an answer.


Ubuntu 16.04 LTS
btrfs-progs v4.4
4x 4tb drives (WD Red), all identical
4x 2tb drives (Seagate), all identical
data and metadata in btrfs-raid10
compression enabled (zlib) in fstab
Last rebalance completed: about 10 minutes ago (it took 4 days! OUCH!)

The actual amount of data stored on the array ( according to du -h ) is 8.1TB

According to btrfs filesystem show, I have 21.84TB of disks and only 17.82TB used, which should leave about 4.02TB. Since I am in RAID10, I should have about half of that amount available for files, or 2.01TB. Since all 4 2 TB drives are identical, I'm not sure why they don't all report the same amount of space used. Perhaps that has something to do with this?

```
Label: none  uuid: 1280f222-55ee-48ea-9d4c-677c9cb2a022
    Total devices 8 FS bytes used 8.04TiB
    devid    1 size 3.64TiB used 2.24TiB path /dev/sdb
    devid    2 size 3.64TiB used 2.24TiB path /dev/sdc
    devid    3 size 1.82TiB used 1.74TiB path /dev/sdi
    devid    4 size 3.64TiB used 2.24TiB path /dev/sde
    devid    5 size 1.82TiB used 1.74TiB path /dev/sdh
    devid    6 size 3.64TiB used 2.24TiB path /dev/sdd
    devid    7 size 1.82TiB used 1.82TiB path /dev/sdf
    devid    8 size 1.82TiB used 1.82TiB path /dev/sdg


```

regular df reports that I have 2.8T remaining. I know that df is not reliable in btrfs systems, but this is here as a datapoint.

```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb         11T  8.1T  2.8T  75% /media/data

```


However, according to btrfs filesystem df, it says that my data partition is totally full (total == used).  I'm not getting any "out of space" errors when I copy files onto the array.

```

Data, RAID10: total=8.03TiB, used=8.03TiB
System, RAID10: total=64.00MiB, used=736.00KiB
Metadata, RAID10: total=11.09GiB, used=9.89GiB
GlobalReserve, single: total=512.00MiB, used=0.00B

```

I must be missing something here.  Am I misinterpreting what I'm seeing?  If this is correctly displaying, how can I determine how much free space I have on the array with some degree of accuracy?

Thank you for taking time to consider this.

---

