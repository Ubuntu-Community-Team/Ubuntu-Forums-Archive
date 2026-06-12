---
title: "Help with deleted partition"
date: 2013-11-26
forum: General Help
---

### Post by theller on 2013-11-26
Yes, I know...backup, anyway gparted crashed and killed the hard drive that had my user data (Ubuntu 12.04 is on a separate ssd). The drive had 2 partitions, one ext4 and one ntfs. I really want the ext4 (i never used the windows side but it would be nice to get my iTunes library back). BTW Win7 is also on a separate ssd. I tried testdisk and here is the output:

```
Mon Nov 25 18:27:38 2013
Command line: TestDisk

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 3.2.0-56-generic (#86-Ubuntu SMP Wed Oct 23 09:20:45 UTC 2013) x86_64
Compiler: GCC 4.6
Compilation date: 2012-02-05T07:15:52
ext2fs lib: 1.42, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       58626288 sectors
/dev/sda: user_max   58626288 sectors
/dev/sda: native_max 58626288 sectors
/dev/sda: dco        58626288 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       125045424 sectors
/dev/sdb: user_max   125045424 sectors
/dev/sdb: native_max 125045424 sectors
/dev/sdb: dco        125045424 sectors
/dev/sdc: LBA, HPA, LBA48, DCO support
/dev/sdc: size       2930277168 sectors
/dev/sdc: user_max   2930277168 sectors
/dev/sdc: native_max 2930277168 sectors
/dev/sdc: dco        2930277168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 30 GB / 27 GiB - CHS 3649 255 63, sector size=512 - KINGSTON SSDNOW 30GB, S/N:40FM104UM83Z, FW:AJXA0202
Disk /dev/sdb - 64 GB / 59 GiB - CHS 7783 255 63, sector size=512 - M4-CT064M4SSD2, S/N:0000000011490324B81B, FW:0309
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182401 255 63, sector size=512 - ST1500DL003-9VT16L, S/N:5YD4GNYG, FW:CC32
Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121600 255 63, sector size=512 - WD Ext HDD 1021, FW:2002

Partition table type (auto): Intel
Disk /dev/sdc - 1500 GB / 1397 GiB - ST1500DL003-9VT16L
Partition table type: Intel

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
 1 E extended LBA         148862  97  1 182401 254 63  538813989
 5 L HPFS - NTFS          148862  97 51 182401 254 63  538813939

Analyse Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182401 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
Current partition structure:
 1 E extended LBA         148862  97  1 182401 254 63  538813989
No partition is bootable
Invalid NTFS or EXFAT boot
 5 L HPFS - NTFS          148862  97 51 182401 254 63  538813939
 5 L HPFS - NTFS          148862  97 51 182401 254 63  538813939
Ask the user for vista mode
Computes LBA from CHS for Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63
Search for partition aborted

Results

interface_write()
 
No partition found or selected for recovery

search_part()
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63

block_group_nr 3

recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/5468, s_mnt_count=0/27, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 179200248
recover_EXT2: part_size 1433601984
     Linux                    0   1  1 89237 153  3 1433601984 [shared_drive]
     EXT4 Large file Sparse superblock Backup superblock, 734 GB / 683 GiB
NTFS at 89237/153/5
filesystem size           538802161
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               34331452
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          89237 153  5 122776 123 20  538802161
     NTFS, 275 GB / 256 GiB
BAD_RS LBA=4192795945 11129726
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 01
     FAT12                260989 121 38 439142  63 18 2862024272
This partition ends after the disk limits. (start=4192795945, size=2862024272, end=7054820216, disk end=2930288130)
check_part_i386 failed for partition type 07
     HPFS - NTFS          148862  97 51 182401 254 63  538813939
NTFS at 182401/68/3
filesystem size           538802161
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               34331452
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          148862  97 51 182401  68  3  538802161
     NTFS found using backup sector!, 275 GB / 256 GiB
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (1500 GB / 1397 GiB) seems too small! (< 3612 GB / 3364 GiB)
The following partition can't be recovered:
     FAT12                260989 121 38 439142  63 18 2862024272
get_geometry_from_list_part_aux head=255 nbr=1
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=1

Results
     Linux                    0   1  1 89237 254 63 1433608407 [shared_drive]
     EXT4 Large file Sparse superblock Backup superblock, 734 GB / 683 GiB
     HPFS - NTFS          89237 153  5 122776 254 63  538810457
     NTFS, 275 GB / 256 GiB
     HPFS - NTFS          148862  97 51 182401 254 63  538813939
     NTFS found using backup sector!, 275 GB / 256 GiB
     HPFS - NTFS          148862  97 51 182401 254 63  538813939

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 failed for partition type 07
Current partition structure:
 1 E extended LBA         148862  97  1 182401 254 63  538813989
No partition is bootable
Invalid NTFS or EXFAT boot
 5 L HPFS - NTFS          148862  97 51 182401 254 63  538813939
 5 L HPFS - NTFS          148862  97 51 182401 254 63  538813939
Ask the user for vista mode
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdc - 1500 GB / 1397 GiB - CHS 182402 255 63
Search for partition aborted

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

TestDisk exited normally.
```

So it looks like the data is still there? I then tried 
sudo mke2fs -n /dev/sdc
```
mke2fs 1.42 (29-Nov-2011)
/dev/sdc is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
91578368 inodes, 366284646 blocks
18314232 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
11179 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848
```

Then:
sudo e2fsck -b 8193 -B 4096 /dev/sdc
and got:

```
e2fsck 1.42 (29-Nov-2011)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

I used photorec and it could recover files so something is on the disc but I would love to recover the partition. The whole drive is 1.5 TB but the partition was about half. I now have a 1TB drive I am going to put in the computer but it's still not big enough to copy the damaged drive.

Help? What next? I feel like I am not using testdisk properly.
I looked at [http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock ]("http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock")and I don't see the SUPERBLOCK option.

From this site: [http://www.cgsecurity.org/wiki/Menu_Analyse ]("http://www.cgsecurity.org/wiki/Menu_Analyse")I saw the Load Backup option and I think I was supposed to press L before enter?
```
TestDisk 6.5-WIP, Data Recovery Utility, November 2006
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
     Partition               Start        End    Size in sectors
* FAT32                    0   1  1  1010 254 63   16241652 [NO NAME]
P Linux                 1011   0  1  1023 254 63     208845 [/boot]
D Linux                 1024   1  1  3573 254 63   40965687
D Linux RAID            1024   1  1  3573 254 63   40965687 [md0]
D Linux                 3574   1  1  4210 254 63   10233342
D Linux RAID            3574   1  1  4210 254 63   10233342 [md1]
L Linux                 4211   1  1 14592 254 63  166786767

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use LEFT/RIGHT Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     ENTER: to continue
FAT32, 8315 MB / 7930 MiB
```
What else can I share or do?

---

### Post by varunendra on 2013-11-26
Probably the best option at hand is to use testdisk (Deep Search if required) to list your partitions and files in them, then copy whole directory structure using "C" option when it is listing the files, then simply delete the partitions and recreate them.

Even if the corrupt partitions could be recovered by testdisk, they are often not recognized correctly by gparted, which means either it doesn't follow all the standards of partition table, or some discrepancy remains in the repaired partition.

---

### Post by theller on 2013-11-26
Thanks varunendra! I ran the deep search before I left for work so it should be done when I get home. I will try the copy option and post how it goes.

---

### Post by den_ on 2013-11-26
I am not sure, if I got this right, but it looks to me that only partition table was altered? In that case testdisk should be able to recover it (I did it once, for a while.).

Regarding your observastion 'something is on the disk', well it is always something on a used disk. photorec does a pretty low level looking for a files, and it finds tents or hundreds of copies of the same document, depending on how often it got edited, or saved to disk actually. It also finds data after partition format, and writing to it. If you look mainly for text files, I suggest you type a script which will search for some text pattern, found in the last version of the document. If you search for videos, that's good because it recognizes the type of the file, and if you do not edit video files, there should be no more then only one version of the file.

---

### Post by theller on 2013-11-26
[COLOR=#8b4513]I ran the testdisk deep search and asked to list the files of the ext4 partition and the response was:
[/COLOR]
No file found, filesystem may be damaged.

[COLOR=#8b4513]As for the files I found with photorec, I think they are the files from the ntfs partition (many mp3 and no flac).

Anyone know why I don't have the SuperBlock option?
[/COLOR]

---

### Post by varunendra on 2013-11-26
> **theller said:**
> No file found, filesystem may be damaged.

..quite certainly it is. Since you said gparted "crashed" and didn't say doing what, we don't know in what state the data/partition table was when it crashed. If even deeper search failed to list previously existing partitions, there is nothing more I can suggest.

Usually, it lists more than one entry for certain partitions if they were altered. Did you get such a list after deeper search? If yes, did you try listing contents in each listed partition?

A few more things that I ignored earlier, I don't think you used mke2fs -n command properly. Its man page says -
> This can be used to determine the location of the backup superblocks for a particular filesystem, **so long as the mke2fs parameters that were passed when the filesystem was originally created are used again**.
..and I don't think the device can be /dev/sdc. It should have been **/dev/sdc[COLOR="#FF0000"]x[/COLOR]**, where x is a number denoting the partition number.

Similarly, "e2fsck" should be run on a **_device that contains the filesystem_**, which means a partition, which further means **/dev/sdc[COLOR="#FF0000"]x[/COLOR]** like above, not /dev/sdc.

Anyway, assuming you followed these steps to run testdisk (running on Ubuntu, since it seems to perform better on Linux) : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) , I don't think the above corrections are going to make much difference.

---

### Post by theller on 2013-11-29
[COLOR=#8b4513]I was using gparted to make the windows partition smaller and the ext4 larger. Since ubuntu is on a separate ssd I just unmounted the hdd drive and tried to move the partitions. Ubuntu gave me a popup (report system error?) then gparted just closed. 

Your response was similar to one from testdisk forums:[/COLOR]

Did you already write your ext4-partion into your partition table?
You must first use TestDisk / Analyse and Quick or Deeper Search until your partition is found.
Then you have to write it to your partition table.
Your partition must be set as Primary and if you press enter, you'll get to the screen to confirm with write.
Only if your ext4-partition is in your partition table, you can make a diagnose of your superblock using the menu Advanced.

[COLOR=#8b4513]And I was wondering if I needed to use sdc0. I will try that tomorrow. Actually, I might wait a few days. I just ordered a 2TB WD hdd and I think the safest thing would be to copy the segate 1.5TB with damaged/missing partitions. I haven't done this yet because I did not have a hd big enough.[/COLOR]

---

### Post by varunendra on 2013-12-01
> **theller said:**
> And I was wondering if I needed to use sdc0..

Partition names start with 1, not 0. So they can be sdc1, sdc2.. etc.

Also, if the partition table is legacy type (MBR), the '[COLOR="#0000CD"]**Logical**[/COLOR]' partition (those inside an 'Extended' partition) numbers will always be 5 and higher, even if there is only one '[COLOR="#006400"]**Primary**[/COLOR]' partition. For example, if there are two Primary and two 'Logical' partitions in the drive /dev/sdc, there names would be - [COLOR="#006400"]**sdc1, sdc2**[/COLOR], [COLOR="#0000CD"]**sdc5,sdc6**[/COLOR].

However, if the partition table is modern (GPT) type, the partition numbers will count normally, starting from 1 (sdc1, sdc2, sdc3, sdc4.... etc.).

---

