---
title: "Recover ext4 partition deleted during Windows update"
date: 2017-05-30
forum: General Help
---

### Post by dapb26 on 2017-05-30
Hello,


After updating the Windows I've got a pleasant surprise: All my disks were gone :shock:


Although I can access my 2 NTFS partitions using a live USB, my ext4 Ubuntu partition still inaccessible.


Here is what I get running fdisk:


```
sudo fdisk -lu


Disque /dev/sda : 698,7 GiB, 750156374016 octets, 1465149168 secteursUnités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x38601c96




Périphérique Amorçage      Start        Fin   Secteurs   Size Id Type
/dev/sda1                   2048   52430847   52428800    25G  c W95 FAT32 (LBA)
/dev/sda2    *          52430848  240250879  187820032  89,6G  7 HPFS/NTFS/exFAT
/dev/sda3              240250880  241172479     921600   450M 27 Hidden NTFS Win
/dev/sda4              241176574 1465145343 1223968770 583,6G  f Étendue W95 (LB
/dev/sda5              638490624 1456379903  817889280   390G  7 HPFS/NTFS/exFAT
/dev/sda6             1456381952 1465145343    8763392   4,2G 82 partition d'éch






Partition 4 does not start on physical sector boundary.
```


Running Testdisk gives me this:
```
TestDisk 7.0, Data Recovery Utility, April 2015Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org




Disk /dev/sda - 750 GB / 698 GiB - CHS 91202 255 63
    Partition               Start        End    Size in sectors
* FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
P HPFS - NTFS           3263 170 44 14954 236  2  187820032
P HPFS - NTFS          14954 236  3 15012  74 38     921600
>L Linux                15012 107  8 39744  19 19  397314048


L HPFS - NTFS          39744  51 52 90655 116 21  817889280


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files
```


Here are the details testdisk gives about the Linux partition:


```
ext4 blocksize=4096 Large_file Sparse_SB, 203 GB / 189 GiB
```


I'm not sure how to interpret those results. Could someone help me with that?


I've run a"deeper research" and here is the result (txt compressed because of size limitation):[ATTACH]275357[/ATTACH]

This deep research apparently doesn't recognize well my one ext4 partition and then I have this message:

```
Warning: the current number of heads per cylinder is 255 but the correct value may be 128
```

So when I change the numbers of head, I got this doing a quick research (pretty much the same result when the number of heads per cylinder was 255 per default):

```
TestDisk 7.0, Data Recovery Utility, April 2015Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 750 GB / 698 GiB - CHS 181692 128 63
     Partition               Start        End    Size in sectors
 * FAT32 LBA                0  32 33  6501 107 43   52428800 [RECOVERY]
 P HPFS - NTFS           6501 107 44 29793   2  2  187820032
 P HPFS - NTFS          29793   2  3 29907  38 38     921600
>L Linux                29907  71  8 79177  83 19  397314048
 L HPFS - NTFS          79177 115 52 180602  85 21  817889280






Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB, 203 GB / 189 GiB
```

Thanks for your help if you can let me know what I should do next to safely recover my partition table and so my data.

---

### Post by oldfred on 2017-05-30
I have had trouble using testdisk as it still uses the now very old CHS cylinders, heads, sectors notation. Drives have used LBA sectors for years.

Windows does not include all or any Linux partitions when it rewrites a partition table. It has done this for years. While we consider that bug, they probably consider it a required feature.

You should be able to use testdisk or parted rescue.

       Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[URL="http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462"]http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462
[/URL]
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545) 

[URL="http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462"]
[/URL]

---

