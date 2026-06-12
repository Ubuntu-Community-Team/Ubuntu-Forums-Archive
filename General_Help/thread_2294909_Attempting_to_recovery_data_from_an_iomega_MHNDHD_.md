---
title: "Attempting to recovery data from an iomega MHNDHD NAS Drive"
date: 2015-09-14
forum: General Help
---

### Post by trinsic1 on 2015-09-14
Hi I have an iomega MHNDHD NAS Drive that smart diagnostics showed was on its way to fail so I did a ddrescue on the data partition and saved the data to an image. There was quite a few bad sectors, but the drive but it completed successfully. Now Im trying to get the partition in a state where I can recover the data but I am having trouble with that. I was wondering if anyone can help me with this.

Here is the information of the whole drive from testdisk:
```
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Invalid RAID superblock
 1 P Linux RAID               3   0  1   514 254 63    8225280
 1 P Linux RAID               3   0  1   514 254 63    8225280
Invalid RAID superblock
 2 P Linux RAID             515   0  1 121600 254 63 1945246590
 2 P Linux RAID             515   0  1 121600 254 63 1945246590
 3 P Sys=DA                   0   0  2     2 254 63      48194
No partition is bootable

```

The drive I imaged was the 2nd partition.
fdisk had said it was an XFS file system. Its a single drive setup as Raid i guess. Im not sure If I have to assemble an array for a single drive?
Naturally the partition had missing partition information so I fixed that with fdisk,

```
root@bench:/home/trinsic# fdisk /media/mybook/rescue/jessica-back2.img
Command (m for help): p

Disk /media/mybook/rescue/jessica-back2.img: 995.4 GB, 995359151616 bytes
49 heads, 39 sectors/track, 1017300 cylinders, total 1944060843 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfcc404f9

                                 Device Boot      Start         End      Blocks   Id  System
/media/mybook/rescue/jessica-back2.img2   *      121600  1944060842   971969621+  83  Linux

Command (m for help): 
```

I could not extend the block ssize beyond the size of the image.

When I try to mount the image or check the file system for errors I get  an error message:
```

root@bench:/home/trinsic# sudo mount -o loop,offset=62259200 -t xfs /media/mybook/rescue/jessica-back2.img /media/image
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmsg | tail
```
[ 3072.786701] XFS (loop0): bad magic number
[ 3072.786707] XFS (loop0): SB validate failed with error 22.
```

I probabley should have imaged the whole drive, but I wanted to get the most important stuff off first. Is there anyway to get this image into a state where I can read the partition? I tried to use photorec on it and it recovers files but all the names are gone and that is worthless to me right now.

---

### Post by trinsic1 on 2015-09-14
bumping this, trying to find any answer any help would be appreciated.

---

### Post by trinsic1 on 2015-09-15
bump, for help.

---

