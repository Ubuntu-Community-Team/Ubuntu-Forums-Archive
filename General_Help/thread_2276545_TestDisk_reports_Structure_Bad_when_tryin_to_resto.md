---
title: "TestDisk reports Structure: Bad when tryin to restore partition characteristics"
date: 2015-05-03
forum: General Help
---

### Post by Phoenix87 on 2015-05-03
After losing my ext4 partition by accidentally booting into the Windows Recovery Tool I am now trying to restore the partition table to the origina state using TestDisk. Said tool is detecting all the partitions correctly, but I am unable to set the Linux partitition as Extended. This way I'm only capable of restoring 4 of the 5 partitions that I now have.

The following is what I see when I try to use TestDisk

```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
     Partition               Start        End    Size in sectors
 P FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 * HPFS - NTFS           3263 170 44 15421  97 36  195313664 [OS]
>L Linux                15421  97 37 35423 180 21  321337344
 L Linux Swap           35423 212 54 36469 112 59   16797696
 P HPFS - NTFS          36469 112 60 77825  70  5  664381440 [DATA]







Structure: Bad. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large file Sparse superblock, 164 GB / 153 GiB

```

Everything seems to be intact because yesterday I managed to make a backup copy of all the files in the Linux partition on an external hard drive using PhotoRec. My current partition table looks something like

```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 E extended LBA             0  32 32  3263 170 43   52428801
 2 P HPFS - NTFS           3263 170 44 15421  97 36  195313664 [OS]
 3 * Linux                15421  97 37 35423 180 21  321337344
 4 P HPFS - NTFS          36469 112 60 77825  70  5  664381440 [DATA]
 5 L FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]

```

Any help on how to enclose Linux and Linux Swap back into the Extended partition is very much appreciated.

---

### Post by pmi2 on 2015-05-03
This may be a stupid q, since you obviously moved on to TestDisk, but have you tried using Boot-Repair?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It seems to do a good job recovering a working system after some of the Windows tools are run.

---

### Post by Phoenix87 on 2015-05-03
My Linux partition was showing up as "unallocated" in gparted, so I presume that by just fixing grub I might have made the Windows partition available to boot again somehow, but not the Linux partition.

---

### Post by Phoenix87 on 2015-05-03
As a temporary workaround I went for

```

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
     Partition               Start        End    Size in sectors
   FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 * HPFS - NTFS           3263 170 44 15421  97 36  195313664 [OS]
>P Linux                15421  97 37 35423 180 21  321337344
 L Linux Swap           35423 212 54 36469 112 59   16797696
 P HPFS - NTFS          36469 112 60 77825  70  5  664381440 [DATA]

```

which means that the RECOVERY partition now appears as unallocated. After writing changes to disk with testdisk and restoring the boot loader I now have access to everything again. However I'd prefer to restore my machine to the previous state if that is at all possible at this point. So I'm still looking for help here.

---

### Post by oldfred on 2015-05-03
Generally testdisk is the best choice.

If just changing primary & logical, you may be able to use fixparts. But all the rules on partitions apply. I know only can have one extended partition which counts as one of the 4 available primary. Only 4 primary partitions and all logical must be adjacent and in extended.

       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Fixparts is often used to correct gpt/MBR issues, but also has some other features.

---

### Post by Phoenix87 on 2015-05-04
This seems good, but the problem is that I can't "activate" all the 5 partitions with testdisk, so that I will always end up with one being left as "unallocated". I suppose that if I could find a way to restore all the partition then I might be able to use fixparts to change their characteristics. Any suggestions on how to achieve this are greatly welcomed.

---

### Post by oldfred on 2015-05-04
There is a brute force method, but you have to know start sector & size. Testdisk still uses the old CHS and most tools show start & end of partitions, so a little math.
And you have to be sure to follow all partition table rules.

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt


If you can use testdisk to give two versions then  you can combine them?

Several threads with examples, old but has not changed as long as you have MBR not gpt.
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

