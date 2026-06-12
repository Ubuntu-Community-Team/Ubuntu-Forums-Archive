---
title: "Data recovery from unmountable HDD showing up as &quot;Free space&quot;"
date: 2013-01-29
forum: General Help
---

### Post by theonetruelord on 2013-01-29
Hello!
I have an issue with a hard drive. I know there is data on it, but it is showing up in Windows Disk Management as "Unallocated space" and in Disk Utility as "Free space"
I have scanned it with Testdisk (output below). I'm pretty sure all of my data should still be on there, but I have no idea why it isn't showing up, and the drive isn't mountable in either OS. I'm hoping someone has a clever way I can change a few properties to make it magically work, but I am dubious such a solution exists!
Is my best bet to try to run Photorec, recover all my files onto the various other hard drives I have, and then reformat and repartition my drive?

Testdisk output:

```

Mon Jan 28 19:31:20 2013
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-24-generic (#39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       1953525168 sectors
/dev/sda: user_max   1953525168 sectors
/dev/sda: native_max 7368112 sectors
/dev/sda: dco        1953525168 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       3907029168 sectors
/dev/sdb: user_max   3907029168 sectors
/dev/sdb: native_max 14715056 sectors
/dev/sdb: dco        18446744073321613488 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - ATA ST31000528AS
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63, sector size=512 - ATA WDC WD20EARX-00P
Disk /dev/sdg - 7743 MB / 7385 MiB - CHS 1020 239 62, sector size=512 -  USB DISK 2.0

Partition table type (auto): Intel
/dev/sdb: Device Configuration Overlay (DCO) present.
Disk /dev/sdb - 2000 GB / 1863 GiB - ATA WDC WD20EARX-00P
Partition table type: None

Analyse Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
Current partition structure:
   P Unknown                  0   0  1 243201  80 63 3907029168

search_part()
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
FAT32 at 0/0/7
FAT1 : 32-953431
FAT2 : 953432-1906831
start_rootdir : 1906832 root cluster : 2
Data : 1906832-3907029167
sectors : 3907029168
cluster_size : 32
no_of_cluster : 122035073 (2 - 122035074)
fat_length 953400 calculated 953400
set_FAT_info: name from BS used

FAT32 at 0/0/7
     FAT32                    0   0  7 243201  81  6 3907029168 [Turboptera]
     FAT32, 2000 GB / 1863 GiB
This partition ends after the disk limits. (start=6, size=3907029168, end=3907029173, disk end=3907029168)

HFS magic value at 4670/39/17
part_size 2918482870
     HFS                   4670  39 17 186337  79 11 2918482870 [ß;¥ÄË¹9^Q&#338;&#8216;&#402;ÿ~]
     HFS, 1494 GB / 1391 GiB

HFS magic value at 194377/23/5
part_size 107785493
     HFS                  194377  23  5 201086 108 57  107785493 ["&Ä/k¶óýòÛLK&#376;BÆ¶&#382;ÊÖ9jçÞ.]
     HFS, 55 GB / 51 GiB

LVM magic value at 201514/30/25

recover_EXT2: s_block_group_nr=0/6, s_mnt_count=4/4294967295, s_blocks_per_group=32768, s_inodes_per_group=7776
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 217600
recover_EXT2: part_size 1740800
     ext2                 201574  92  7 201682 183 53    1740800 [C-ROOT]
     EXT2 Large file Sparse superblock, 891 MB / 850 MiB

recover_EXT2: s_block_group_nr=0/8, s_mnt_count=4/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 262144
recover_EXT2: part_size 2097152
     ext4                 201683 188 58 201814  72  2    2097152 [C-STATE]
     EXT4 Large file Sparse superblock, 1073 MB / 1024 MiB
FAT16 at 201816/82/11
check_FAT: Unusual number of reserved sectors 4 (FAT), should be 1.
FAT1 : 4-35
FAT2 : 36-67
start_rootdir : 68
Data : 100-32767
sectors : 32768
cluster_size : 4
no_of_cluster : 8167 (2 - 8168)
fat_length 32 calculated 32
heads/cylinder 64 (FAT) != 255 (HD)
sect/track 32 (FAT) != 63 (HD)

FAT16 at 201816/82/11
     FAT16                201816  82 11 201818  92 18      32768
     FAT16, 16 MB / 16 MiB
Search for partition aborted
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (2000 GB / 1863 GiB) seems too small! (< 2000 GB / 1863 GiB)
The following partition can't be recovered:
     FAT32                    0   0  7 243201  81  6 3907029168 [Turboptera]
     FAT32, 2000 GB / 1863 GiB

Results
   P HFS                   4670  39 17 186337  79 11 2918482870 [ß;¥ÄË¹9^Q&#338;&#8216;&#402;ÿ~]
     HFS, 1494 GB / 1391 GiB
   P HFS                  194377  23  5 201086 108 57  107785493 ["&Ä/k¶óýòÛLK&#376;BÆ¶&#382;ÊÖ9jçÞ.]
     HFS, 55 GB / 51 GiB
   P ext2                 201574  92  7 201682 183 53    1740800 [C-ROOT]
     EXT2 Large file Sparse superblock, 891 MB / 850 MiB
   P ext4                 201683 188 58 201814  72  2    2097152 [C-STATE]
     EXT4 Large file Sparse superblock, 1073 MB / 1024 MiB
   P FAT16                201816  82 11 201818  92 18      32768
     FAT16, 16 MB / 16 MiB


dir_partition inode=2
   P ext2                 201574  92  7 201682 183 53    1740800 [C-ROOT]
     EXT2 Large file Sparse superblock, 891 MB / 850 MiB
Directory /
       2 drwxr-xr-x     0      0      4096 16-Jan-2012 16:48 .
       2 drwxr-xr-x     0      0      4096 16-Jan-2012 16:48 ..
      11 drwx------     0      0     16384 16-Jan-2012 16:41 lost+found
    7777 drwxr-xr-x     0      0      4096 16-Jan-2012 16:42 usr
   15553 drwxr-xr-x     0      0      4096 16-Jan-2012 16:41 var
   23329 drwxr-xr-x     0      0      4096 16-Jan-2012 16:43 dev
   38881 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 lib
   31105 drwxr-xr-x     0      0      4096 16-Jan-2012 16:46 sbin
   15554 drwxr-xr-x     0      0      4096 16-Jan-2012 16:50 etc
   23330 drwxrwxrwt     0      0      4096 16-Jan-2012 16:47 tmp
   31107 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 bin
   31336 drwxr-xr-x     0      0      4096 16-Jan-2012 16:48 boot
      12 drwxr-xr-x     0      0      4096 16-Jan-2012 16:46 opt
   46657 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 home
   46658 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 media
   46659 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 mnt
   46661 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 proc
   46662 drwxr-xr-x     0      0      4096 16-Jan-2012 16:50 root
      16 drwxr-xr-x     0      0      4096 16-Jan-2012 16:45 sys
   46663 drwxr-xr-x     0      0      4096 16-Jan-2012 16:46 debugd
      30 lrwxrwxrwx     0      0        26 16-Jan-2012 16:46 postinst


dir_partition inode=2
   P ext4                 201683 188 58 201814  72  2    2097152 [C-STATE]
     EXT4 Large file Sparse superblock, 1073 MB / 1024 MiB
Directory /
       2 drwxr-xr-x     0      0      4096 16-Jan-2012 16:48 .
       2 drwxr-xr-x     0      0      4096 16-Jan-2012 16:48 ..
      11 drwx------     0      0     16384 16-Jan-2012 16:41 lost+found
      12 drwxr-xr-x     0      0      4096 16-Jan-2012 16:51 dev_image
    8193 drwxr-xr-x     0      0      4096 16-Jan-2012 16:46 var
     302 -rw-r--r--     0      0     65536 16-Jan-2012 16:50 vmlinuz_hd.vblock


dir_partition inode=0
   P FAT16                201816  82 11 201818  92 18      32768
     FAT16, 16 MB / 16 MiB
Directory /
       3 drwxr-xr-x     0      0         0 16-Jan-2012 16:48 efi
     143 drwxr-xr-x     0      0         0 16-Jan-2012 16:48 syslinux
X    144 -rwxr-xr-x     0      0     14966 16-Jan-2012 16:50 ldlinux.sys

interface_write()
   P HFS                   4670  39 17 186337  79 11 2918482870 [ß;¥ÄË¹9^Q&#338;&#8216;&#402;ÿ~]
   P HFS                  194377  23  5 201086 108 57  107785493 ["&Ä/k¶óýòÛLK&#376;BÆ¶&#382;ÊÖ9jçÞ.]
   P ext2                 201574  92  7 201682 183 53    1740800 [C-ROOT]
   P ext4                 201683 188 58 201814  72  2    2097152 [C-STATE]
   P FAT16                201816  82 11 201818  92 18      32768
 
Write isn't available because the partition table type "None" has been selected.
Partition table type (auto): None
/dev/sdb: Device Configuration Overlay (DCO) present.
Disk /dev/sdb - 2000 GB / 1863 GiB - ATA WDC WD20EARX-00P
Partition table type: Intel

Analyse Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
Current partition structure:
No partition is bootable
```

Many thanks,

Nick

EDIT: I'd also like to point out I have pretty much no idea what most of that means, and I am intending to use the tools and guidance from here: [http://www.lifehacker.com.au/2010/04/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/]("http://www.lifehacker.com.au/2010/04/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")
Does this seem like the best idea?

---

### Post by dino99 on 2013-01-29
what i should do in such case:

- check its bios settings (ide / ahci / compatible or so)
-watch logs to find something usefull

i suppose you also can try to fix the mbr with windows and/or ubuntu. The target is to set it mountable first. Can you list it into a formatting tool ? (to see possible warning/error, giving you an idea to go forward)

is that hdd part of an raid array ? (seen /dev/mapper/ above)
logical or hardware raid ? which raid ?

---

### Post by furything on 2013-01-29
What was the the format of the lost partition?

Linux ext3/4
or windows fat32 ntfs?

The reason I ask is if a linux partition you should be able to use fsck
[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)
or fdisk
[http://unix.stackexchange.com/questions/9156/how-can-i-restore-my-linux](http://unix.stackexchange.com/questions/9156/how-can-i-restore-my-linux)

If windows, there are free tools online - do a google search for deleted partition recovery.
Some of these tools work on both windows and linux partitions. Some will restore the partition for free but others will show what's there expecting you to buy a license before recovering the partition

---

### Post by LostFarmer on 2013-01-29
```
Write isn't available because the partition table type "None" has been selected. Partition table type (auto): None
 /dev/sdb: Device Configuration Overlay (DCO) present. Disk /dev/sdb - 2000 GB / 1863 GiB - ATA WDC WD20EARX-00P
```  from the end of testdisk data, 
First do not use 'NONE' as partition type , use 'INTEL or EFI GPT", if it is not from an Apple comp.
Next sdb has a DCO installed, if it is the problem hdd do a web search for "Device Configuration Overlay" before you do any thing else.

Give more info on the problem hdd, was it from a different computer ? Was it the master/boot hdd and now a slave/non boot ? (having a DCO installed  will make a big difference}  I think if it does have a DCO installed great care must be given .

---

### Post by theonetruelord on 2013-01-29
Thanks for the replies.
sdb is the problem HDD, it is a Fat32 filesystem, in use as a second drive in my PC connected by SATA, it is not part of a RAID. It is a new harddrive, which I have used to back up all of my data, whilst I installed my OSs on my old secondary hard drive, which needed doing because my hard drive which originally had my OSs on gave up the ghost.
When I first used it I formatted it under Ubuntu to Fat32, then transferred my files across, reinstalled my OSs (to sda, a separate HDD), and when I booted into Windows it was unmountable and showed only "Unallocated space". When I next booted into Ubuntu it was unmountable, and showing up as "free space" in Disk Utility.

I also ran Testdisk with partition type "Intel". Results follow:

```

Partition table type: Intel

Analyse Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
Current partition structure:
No partition is bootable
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243202 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243202 255 63

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.

```

---

### Post by LostFarmer on 2013-01-29
from linux in a terminal:
```
sudo dd if=/dev/sdb count=3 bs=512 |xxd
```most of it is not needed.  Is there any thing on lines x1b0 to 1f0 ?  if yes post, if not on line 1f0 last byte have "ffaa" ?

is there any thing on line 200 to end 5f0 ?  if so post it.

line 1b0 to 1f0 will be the mbr partition table.  lines 200 to 5f0 could be many things or nothing.  That is where a GPT partition would be, grub code if installed to hdd if not gpt or ?.

---

### Post by theonetruelord on 2013-01-29
I will try this when I am home from work. Thanks for your help so far!

---

### Post by theonetruelord on 2013-01-29
Well that was quite exciting! Results are in!

Lines x1b0 to 1f0:
```
00001b0: 0000 0000 002c 4463 d374 d354 0000 0000  .....,Dc.t.T....
00001c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.

```

Lines 200 to end:
```
0000200: 5252 6141 0000 0000 0000 0000 0000 0000  RRaA............
0000210: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000220: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000230: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000240: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000250: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000260: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000270: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000280: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000290: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000300: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000310: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000320: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000330: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000340: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000350: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000360: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000370: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000380: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000390: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003e0: 0000 0000 7272 4161 cffb 7c02 c607 1a06  ....rrAa..|.....
00003f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
0000400: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000410: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000420: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000430: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000440: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000450: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000460: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000470: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000480: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000490: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000500: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000510: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000520: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000530: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000540: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000550: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000560: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000570: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000580: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000590: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................

```

Is this part also of any use?

Lines 120 to 170

```
0000120: 32e4 8a56 00cd 13eb d661 f9c3 496e 7661  2..V.....a..Inva
0000130: 6c69 6420 7061 7274 6974 696f 6e20 7461  lid partition ta
0000140: 626c 6500 4572 726f 7220 6c6f 6164 696e  ble.Error loadin
0000150: 6720 6f70 6572 6174 696e 6720 7379 7374  g operating syst
0000160: 656d 004d 6973 7369 6e67 206f 7065 7261  em.Missing opera
0000170: 7469 6e67 2073 7973 7465 6d00 0000 0000  ting system.....

```

Looks interesting!!!

Entire output is below:

```
0000000: 33c0 8ed0 bc00 7cfb 5007 501f fcbe 1b7c  3.....|.P.P....|
0000010: bf1b 0650 57b9 e501 f3a4 cbbd be07 b104  ...PW...........
0000020: 386e 007c 0975 1383 c510 e2f4 cd18 8bf5  8n.|.u..........
0000030: 83c6 1049 7419 382c 74f6 a0b5 07b4 078b  ...It.8,t.......
0000040: f0ac 3c00 74fc bb07 00b4 0ecd 10eb f288  ..<.t...........
0000050: 4e10 e846 0073 2afe 4610 807e 040b 740b  N..F.s*.F..~..t.
0000060: 807e 040c 7405 a0b6 0775 d280 4602 0683  .~..t....u..F...
0000070: 4608 0683 560a 00e8 2100 7305 a0b6 07eb  F...V...!.s.....
0000080: bc81 3efe 7d55 aa74 0b80 7e10 0074 c8a0  ..>.}U.t..~..t..
0000090: b707 eba9 8bfc 1e57 8bf5 cbbf 0500 8a56  .......W.......V
00000a0: 00b4 08cd 1372 238a c124 3f98 8ade 8afc  .....r#..$?.....
00000b0: 43f7 e38b d186 d6b1 06d2 ee42 f7e2 3956  C..........B..9V
00000c0: 0a77 2372 0539 4608 731c b801 02bb 007c  .w#r.9F.s......|
00000d0: 8b4e 028b 5600 cd13 7351 4f74 4e32 e48a  .N..V...sQOtN2..
00000e0: 5600 cd13 ebe4 8a56 0060 bbaa 55b4 41cd  V......V.`..U.A.
00000f0: 1372 3681 fb55 aa75 30f6 c101 742b 6160  .r6..U.u0...t+a`
0000100: 6a00 6a00 ff76 0aff 7608 6a00 6800 7c6a  j.j..v..v.j.h.|j
0000110: 016a 10b4 428b f4cd 1361 6173 0e4f 740b  .j..B....aas.Ot.
0000120: 32e4 8a56 00cd 13eb d661 f9c3 496e 7661  2..V.....a..Inva
0000130: 6c69 6420 7061 7274 6974 696f 6e20 7461  lid partition ta
0000140: 626c 6500 4572 726f 7220 6c6f 6164 696e  ble.Error loadin
0000150: 6720 6f70 6572 6174 696e 6720 7379 7374  g operating syst
0000160: 656d 004d 6973 7369 6e67 206f 7065 7261  em.Missing opera
0000170: 7469 6e67 2073 7973 7465 6d00 0000 0000  ting system.....
0000180: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000190: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001b0: 0000 0000 002c 4463 d374 d354 0000 0000  .....,Dc.t.T....
00001c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
0000200: 5252 6141 0000 0000 0000 0000 0000 0000  RRaA............
0000210: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000220: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000230: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000240: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000250: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000260: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000270: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000280: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000290: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000300: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000310: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000320: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000330: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000340: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000350: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000360: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000370: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000380: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000390: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003e0: 0000 0000 7272 4161 cffb 7c02 c607 1a06  ....rrAa..|.....
00003f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
0000400: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000410: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000420: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000430: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000440: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000450: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000460: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000470: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000480: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000490: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00004f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000500: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000510: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000520: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000530: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000540: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000550: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000560: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000570: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000580: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000590: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00005f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................

```

---

### Post by LostFarmer on 2013-01-29
What I am seeing is not good nor can explain some of it.
 offset  0 to 17F is  a MBR boot strap code
 offset 1b5 to 1bb is the hdd ID code
offset 1bf to 1fe  is the mbr partition area--  no partitions
the next to byte 55AA is the security code

offset 200 to 3ff should not have that data, That data indicates the 2nd sector of a Fat32 partition.

I am going to have you test an assumption .

```
sudo dd if=/dev/sdb count=2 bs=512 skip=5 | xxd
```  do you see FAT32 listed on the right side of output , any where ?  if so post it.  On a FAT32 partition it has a backup Volume Boot Record on the 6th sector.   If the back up VBR is at sector 6, then some how you mounted the hdd as a partition, not as a hdd.  Atho that would not explain it having a MBR boot code.

---

### Post by theonetruelord on 2013-01-30
Fat32 is there! Line 250

```
0000000: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000010: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000020: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000030: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000040: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000050: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000060: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000070: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000080: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000090: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00000f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000100: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000110: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000120: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000130: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000140: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000150: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000160: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000170: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000180: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000190: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000200: eb58 906d 6b64 6f73 6673 0000 0220 2000  .X.mkdosfs...  .
0000210: 0200 0000 00f8 0000 3f00 ff00 0000 0000  ........?.......
0000220: b088 e0e8 388c 0e00 0000 0000 0200 0000  ....8...........
0000230: 0100 0600 0000 0000 0000 0000 0000 0000  ................
0000240: 0000 29c4 d580 7054 7572 626f 7074 6572  ..)...pTurbopter
0000250: 6120 4641 5433 3220 2020 0e1f be77 7cac  a FAT32   ...w|.
0000260: 22c0 740b 56b4 0ebb 0700 cd10 5eeb f032  ".t.V.......^..2
0000270: e4cd 16cd 19eb fe54 6869 7320 6973 206e  .......This is n
0000280: 6f74 2061 2062 6f6f 7461 626c 6520 6469  ot a bootable di
0000290: 736b 2e20 2050 6c65 6173 6520 696e 7365  sk.  Please inse
00002a0: 7274 2061 2062 6f6f 7461 626c 6520 666c  rt a bootable fl
00002b0: 6f70 7079 2061 6e64 0d0a 7072 6573 7320  oppy and..press 
00002c0: 616e 7920 6b65 7920 746f 2074 7279 2061  any key to try a
00002d0: 6761 696e 202e 2e2e 200d 0a00 0000 0000  gain ... .......
00002e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00002f0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000300: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000310: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000320: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000330: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000340: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000350: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000360: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000370: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000380: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000390: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003a0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003b0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003c0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003d0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00003f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.

```

---

### Post by LostFarmer on 2013-01-30
Do not have a lot of time today but will give you some sites to look at and .

[http://support.microsoft.com/kb/140418](http://support.microsoft.com/kb/140418)
[http://support.microsoft.com/kb/140418](http://support.microsoft.com/kb/140418)
[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)

read the site and compare/learn just what you are seening.  offset 200 -259 is in dead a FAT32 partition header data.  go to the above sites and check out the header might be correct for you partition. 
 ```
Total Number of Sectors',  "220: b088 e0e8"=e8e088b0 hex=3907029168 decimal
``````
sudo fdisk /dev/sda 
```  you posted both hdd are the same size, does the Total Number of Sectors above, less then that of sda reported by fdisk? if so likely OK,, if it is more , not good.

to help look at the fat header data :
```
 sudo dd if=/dev/sdb skip=6 count=1 bs=512 |xxd
```have never tried what I am going to suggest so can not be sure it will work.
```
sudo dd if=/dev/sdb of=VBR skip=6 count=1 bs=512
sudo dd if=VBR of=/dev/sdb

```the first code will read the sector into a file named VBR.
the next will write data in VBR file to sector 0.

The above will make the hdd as a partition , not Normal.

I would next do a reboot and see if linux will mount the hdd as a paritition or not.
if it will not auto mount it you will need to do so manually.
basic steps:
make a directory in /mnt then mount it in the new directory.
sudo mount /dev/sdb -t vfat /mnt/'dir made above'
copy the saved data from the /mnt/'dir made above' to where ever.


DO NOT boot into MS WIN till all the data is off, or you will have the same problem.
I have no idea how you formated the hdd  basically as a floppy, but that is what it is.  But when MS WIn sees a hdd it will write a hdd ID to the MBR area and must write a basic MBR boot code if there is not one.
  

If you have question will try to be back in 12 hours.  May be best to wait for some one with more knowledge to comment.  I know my explanations are poorly written but hopefully will do.

---

### Post by oldfred on 2013-01-30
We have seen several users not partition new hard drives and just start writing data. Which in effect makes it a very large floppy drive. But almost all partition tools expect partition tables either old MBR(msdos) or new gpt(GUID). 

It looks like photorec may be the only choice but am not sure if it will read a drive like this. And photorec is very time consuming. On my 640GB drive it took over 8 hours to scan drive. For 2GB it may take days. And it only recovers file extensions, not full file names. 

I do not suggest FAT32 for any larger partitions. If compatibility with Windows is required NTFS is better.

       NTFS and Fat info:
FAT 4GB file size max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)
[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

---

### Post by theonetruelord on 2013-01-30
Thanks for the replies.
oldfred: I formatted it as Fat32 out of habit really, if I can get my data recovered I'll make the drive NTFS for sure.

LostFarmer: Drives are all different sizes so the total number of sectors will be different.
Thanks for the codes - I think I'll give them a miss for now as I don't want to make anything worse - I'll wait and see if someone else can confirm whether it will work!

As I see it: The part of the HDD that tells the OSs how to mount it is broken, and if I can magically fix that (!) then I can just use my hard drive as normal (but back all my data up and reformat it and repartition it first).
If I can't fix that then it's time to bring out the big guns and do some slow recovery!
Has anyone any recommendations for Photorec vs Foremost vs Scalpel? I intend to follow the guide I found [HERE]("http://www.lifehacker.com.au/2010/04/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")

Thanks for all your help so far!

---

### Post by furything on 2013-02-01
I have not tried the ubuntu ones but as I said in my early reply there are many partition recovery tools out there that are free.

I have used this one before (see link below - it states free recovery) but cannot remember if it shows you everything on the drive and you have to pay a license to get it to actually recover it. I recovered an old laptop with freeware but cannot remember if it was this one (I tried about 6 and I know some required payment to do  the recovery).

try this
[http://www.easeus.com/partition-recovery/](http://www.easeus.com/partition-recovery/)

or try googling 'recover windows partition freeware'

---

### Post by greatsirkain on 2013-02-01
Gparted has an option to attempt data recovery

---

### Post by oldfred on 2013-02-01
Someone just posted this detail.
[https://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC16](https://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC16)

I use the loop mount with grub to mount in ISO directly. Wubi also uses the loop mount. 
So if drive does not have partition can it be mounted with loop instead of a partition mount to see data?

---

### Post by theonetruelord on 2013-02-01
Thanks, I'll have a read of that this weekend and see what I can do.

---

### Post by theonetruelord on 2013-02-04
This part scared me!> This command (normally) won't technically destroy your data, but it will make it basically unusable

I tried using just the "Rescue" command, but no dice.
Currently Easeus Partition Recovery is running a scan which will take 60 hours to finish, but it's looking pretty hopeful!

Thanks to everyone who has helped!

---

