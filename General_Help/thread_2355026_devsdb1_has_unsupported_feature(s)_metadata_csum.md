---
title: "/dev/sdb1 has unsupported feature(s): metadata_csum"
date: 2017-03-08
forum: General Help
---

### Post by efflandt on 2017-03-08
I am not on a UPS anymore because it failed, we are having a windy day, and power failed in the middle of having a bunch of programs up. I wanted to check my drive. But whether running 14.04 on my other drive or 16.04 live/install on USB I get this error when I try to fsck 16.10 on SSD:```
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sdb1
/dev/sdb1 has unsupported feature(s): metadata_csum
e2fsck: Get a newer version of e2fsck!
```

The drive is pretty standard SSD with msdos partitioning and ext4 partition (why does parted show all drives when sdb specified?):```
efflandt@msata512-1610:~$ sudo parted -l /dev/sdb
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  57.6MB  57.5MB  primary  fat32        diag
 2      57.6MB  12.7GB  12.6GB  primary  ntfs
 3      12.7GB  549GB   537GB   primary  ntfs
 4      549GB   1000GB  451GB   primary  ext4         boot


Model: ATA Crucial_CT512M55 (scsi)
Disk /dev/sdb: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  512GB  512GB  primary  ext4         boot
```

When I booted 16.10 on sdb1 it appeared to do its own disk check during boot and everything seems fine.

But why are 14.04 or 16.04 unable to fsck a 16.10 ext4 partition (mSATA SSD card in SATA adapter) and is there a newer fsck available for them?

---

