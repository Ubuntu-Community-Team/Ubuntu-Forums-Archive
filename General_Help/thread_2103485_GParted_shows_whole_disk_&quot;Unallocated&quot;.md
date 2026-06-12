---
title: "GParted shows whole disk &quot;Unallocated&quot;"
date: 2013-01-10
forum: General Help
---

### Post by faustism on 2013-01-10
Hello all,

I have had a little trouble installing GRUB thorugh which I cleared the MBR with:
```
dd if=/dev/zero of=/dev/sdc bs=512 count=1
```

When I attempted to reinstall GRUB I got an error that the chosen install location could not be found at boot time.

Upon further investigation, I found that GParted (via LiveCD) says that the entire disk is unallocated with the error message ```
Can't have a partition outside of the disk.
```

TestDisk is successful in finding my partitions and writing them to the partition table (I don't know that they were ever deleted). The log is:
```
Thu Jan 10 08:06:46 2013
Command line: TestDisk

TestDisk 6.12, Data Recovery Utility, May 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.0.0-pmagic (#1 SMP Fri Jul 29 19:06:18 CDT 2011) i686
Compiler: GCC 4.5
Compilation date: 2011-05-15T12:36:01
ext2fs lib: 1.41.14, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       1250263728 sectors
/dev/sda: user_max   1250263728 sectors
/dev/sda: native_max 1250263728 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63, sector size=512 - ATA Hitachi HTS54756
Disk /dev/sr0 - 377 MB / 360 MiB - CHS 184364 1 1 (RO), sector size=2048 - MATSHITA DVD-RAM UJ8A0ASW

Partition table type (auto): Intel
Disk /dev/sda - 640 GB / 596 GiB - ATA Hitachi HTS54756
Partition table type: Intel

Analyse Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32 at 0/32/33
Info: size boot_sector 52428800, partition 52428800
FAT1 : 7182-19974
FAT2 : 19975-32767
start_rootdir : 32768 root cluster : 2
Data : 32768-52428799
sectors : 52428800
cluster_size : 32
no_of_cluster : 1637376 (2 - 1637377)
fat_length 12793 calculated 12793
NTFS at 3263/170/44
NTFS at 47191/180/30
Current partition structure:
 1 * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 2 P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
 3 P Linux                29372  33 38 29437 102 41    1048576 [Boot]
 4 E extended LBA         29437 103  1 77825 254 63  777362796
 5 L Linux Swap           29437 135 11 30481 219 58   16777200
   X extended             30481 251  1 31526  82 28   16777306
 6 L Linux Swap           30481 252 44 31526  82 28   16777200
   X extended             31526 114  1 39358 242 52  125829196
 7 L Linux                31526 115 14 39358 242 52  125829120
   X extended             39359  19  1 47191 147 60  125829204
 8 L Linux                39359  20 22 47191 147 60  125829120
   X extended             47191 179  1 77825  70  5  492128348
 9 L HPFS - NTFS          47191 180 30 77825  70  5  492128256
Computes LBA from CHS for Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
FAT32 at 0/32/33
FAT1 : 7182-19974
FAT2 : 19975-32767
start_rootdir : 32768 root cluster : 2
Data : 32768-52428799
sectors : 52428800
cluster_size : 32
no_of_cluster : 1637376 (2 - 1637377)
fat_length 12793 calculated 12793

FAT32 at 0/32/33
     FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
     FAT32, 26 GB / 25 GiB
NTFS at 3263/170/44
filesystem size           419430393
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
     NTFS, 214 GB / 199 GiB

recover_EXT2: s_block_group_nr=0/4, s_mnt_count=31/37, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 131072
recover_EXT2: part_size 1048576
     Linux                29372  33 38 29437 102 41    1048576 [Boot]
     EXT2 Large file Sparse superblock, 536 MB / 512 MiB
     Linux Swap           29437 135 11 30481 219 58   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
     Linux Swap           30481 252 44 31526  82 28   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB

recover_EXT2: s_block_group_nr=0/480, s_mnt_count=12/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 15728640
recover_EXT2: part_size 125829120
     Linux                31526 115 14 39358 242 52  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB

recover_EXT2: s_block_group_nr=0/480, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 15728640
recover_EXT2: part_size 125829120
     Linux                39359  20 22 47191 147 60  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
NTFS at 47191/180/30
filesystem size           492128256
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               30758015
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB

Results
   * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
     FAT32, 26 GB / 25 GiB
   P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
     NTFS, 214 GB / 199 GiB
   P Linux                29372  33 38 29437 102 41    1048576 [Boot]
     EXT2 Large file Sparse superblock, 536 MB / 512 MiB
   L Linux Swap           29437 135 11 30481 219 58   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   L Linux Swap           30481 252 44 31526  82 28   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   L Linux                31526 115 14 39358 242 52  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   L Linux                39359  20 22 47191 147 60  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   L HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB
ntfs_device_testdisk_io_ioctl() unimplemented


dir_partition inode=5
   L HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB
Directory /
       5 dr-xr-xr-x     0      0         0  9-Jan-2013 14:00 .
       5 dr-xr-xr-x     0      0         0  9-Jan-2013 14:00 ..
      40 dr-xr-xr-x     0      0         0 26-Aug-2012 16:10 $RECYCLE.BIN
     329 dr-xr-xr-x     0      0         0  8-Jan-2013 20:31 ConfigFiles
    6331 dr-xr-xr-x     0      0         0  8-Jun-2012 19:26 Desktop
   29266 dr-xr-xr-x     0      0         0  8-Jan-2013 21:33 Documents
   29253 dr-xr-xr-x     0      0         0  8-Jan-2013 21:32 Downloads
   15804 dr-xr-xr-x     0      0         0  8-Jan-2013 21:31 Media
   29246 dr-xr-xr-x     0      0         0  8-Jan-2013 21:32 Pictures
    7093 dr-xr-xr-x     0      0         0  8-Jan-2013 21:22 Random
    6914 dr-xr-xr-x     0      0         0  1-Dec-2012 18:48 Records
      36 dr-xr-xr-x     0      0         0  9-Jan-2013 19:04 System Volume Information
      17 dr-xr-xr-x     0      0         0 29-Sep-2012 00:39 found.000

interface_write()
 1 * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 2 P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
 3 P Linux                29372  33 38 29437 102 41    1048576 [Boot]
 4 E extended LBA         29437 103  1 77825 254 63  777362796
 5 L Linux Swap           29437 135 11 30481 219 58   16777200
 6 L Linux Swap           30481 252 44 31526  82 28   16777200
 7 L Linux                31526 115 14 39358 242 52  125829120
 8 L Linux                39359  20 22 47191 147 60  125829120
 9 L HPFS - NTFS          47191 180 30 77825  70  5  492128256
simulate write!

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
FAT32 at 0/32/33
Info: size boot_sector 52428800, partition 52428800
FAT1 : 7182-19974
FAT2 : 19975-32767
start_rootdir : 32768 root cluster : 2
Data : 32768-52428799
sectors : 52428800
cluster_size : 32
no_of_cluster : 1637376 (2 - 1637377)
fat_length 12793 calculated 12793
NTFS at 3263/170/44
NTFS at 47191/180/30
 1 * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
     FAT32, 26 GB / 25 GiB
 2 P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
     NTFS, 214 GB / 199 GiB
 3 P Linux                29372  33 38 29437 102 41    1048576 [Boot]
     EXT2 Large file Sparse superblock, 536 MB / 512 MiB
 4 E extended LBA         29437 103  1 77825 254 63  777362796
 5 L Linux Swap           29437 135 11 30481 219 58   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   X extended             30481 251  1 31526  82 28   16777306
 6 L Linux Swap           30481 252 44 31526  82 28   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   X extended             31526 114  1 39358 242 52  125829196
 7 L Linux                31526 115 14 39358 242 52  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   X extended             39359  19  1 47191 147 60  125829204
 8 L Linux                39359  20 22 47191 147 60  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   X extended             47191 179  1 77825  70  5  492128348
 9 L HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB

Analyse Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
Geometry from i386 MBR: head=255 sector=63
FAT32 at 0/32/33
Info: size boot_sector 52428800, partition 52428800
FAT1 : 7182-19974
FAT2 : 19975-32767
start_rootdir : 32768 root cluster : 2
Data : 32768-52428799
sectors : 52428800
cluster_size : 32
no_of_cluster : 1637376 (2 - 1637377)
fat_length 12793 calculated 12793
NTFS at 3263/170/44
NTFS at 47191/180/30
Current partition structure:
 1 * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 2 P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
 3 P Linux                29372  33 38 29437 102 41    1048576 [Boot]
 4 E extended LBA         29437 103  1 77825 254 63  777362796
 5 L Linux Swap           29437 135 11 30481 219 58   16777200
   X extended             30481 251  1 31526  82 28   16777306
 6 L Linux Swap           30481 252 44 31526  82 28   16777200
   X extended             31526 114  1 39358 242 52  125829196
 7 L Linux                31526 115 14 39358 242 52  125829120
   X extended             39359  19  1 47191 147 60  125829204
 8 L Linux                39359  20 22 47191 147 60  125829120
   X extended             47191 179  1 77825  70  5  492128348
 9 L HPFS - NTFS          47191 180 30 77825  70  5  492128256
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63
FAT32 at 0/32/33
FAT1 : 7182-19974
FAT2 : 19975-32767
start_rootdir : 32768 root cluster : 2
Data : 32768-52428799
sectors : 52428800
cluster_size : 32
no_of_cluster : 1637376 (2 - 1637377)
fat_length 12793 calculated 12793

FAT32 at 0/32/33
     FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
     FAT32, 26 GB / 25 GiB
NTFS at 3263/170/44
filesystem size           419430393
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
     NTFS, 214 GB / 199 GiB

recover_EXT2: s_block_group_nr=0/4, s_mnt_count=31/37, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 131072
recover_EXT2: part_size 1048576
     Linux                29372  33 38 29437 102 41    1048576 [Boot]
     EXT2 Large file Sparse superblock, 536 MB / 512 MiB
     Linux Swap           29437 135 11 30481 219 58   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
     Linux Swap           30481 252 44 31526  82 28   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB

recover_EXT2: s_block_group_nr=0/480, s_mnt_count=12/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 15728640
recover_EXT2: part_size 125829120
     Linux                31526 115 14 39358 242 52  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB

recover_EXT2: s_block_group_nr=0/480, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 15728640
recover_EXT2: part_size 125829120
     Linux                39359  20 22 47191 147 60  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
NTFS at 47191/180/30
filesystem size           492128256
sectors_per_cluster       8
mft_lcn                   4
mftmirr_lcn               30758015
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB

Results
   * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
     FAT32, 26 GB / 25 GiB
   P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
     NTFS, 214 GB / 199 GiB
   P Linux                29372  33 38 29437 102 41    1048576 [Boot]
     EXT2 Large file Sparse superblock, 536 MB / 512 MiB
   L Linux Swap           29437 135 11 30481 219 58   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   L Linux Swap           30481 252 44 31526  82 28   16777200
     SWAP2 version 1, 8589 MB / 8191 MiB
   L Linux                31526 115 14 39358 242 52  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   L Linux                39359  20 22 47191 147 60  125829120
     EXT4 Large file Sparse superblock, 64 GB / 60 GiB
   L HPFS - NTFS          47191 180 30 77825  70  5  492128256
     NTFS, 251 GB / 234 GiB

interface_write()
 1 * FAT32 LBA                0  32 33  3263 170 43   52428800 [RECOVERY]
 2 P HPFS - NTFS           3263 170 44 29372   0 61  419430393 [OS]
 3 P Linux                29372  33 38 29437 102 41    1048576 [Boot]
 4 E extended LBA         29437 103  1 77825 254 63  777362796
 5 L Linux Swap           29437 135 11 30481 219 58   16777200
 6 L Linux Swap           30481 252 44 31526  82 28   16777200
 7 L Linux                31526 115 14 39358 242 52  125829120
 8 L Linux                39359  20 22 47191 147 60  125829120
 9 L HPFS - NTFS          47191 180 30 77825  70  5  492128256
simulate write!
```

I restarted and still GParted shows the same error.

fdisk shows all of my partitions the way the should be:
```
root@PartedMagic:~# fdisk -l /dev/sda

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    52430847    26214400    c  W95 FAT32 (LBA)
/dev/sda2        52430848   471861240   209715196+   7  HPFS/NTFS/exFAT
/dev/sda3       471863296   472911871      524288   83  Linux
/dev/sda4       472911894  1250274689   388681398    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       472913920   489691119     8388600   82  Linux swap
/dev/sda6       489693184   506470383     8388600   82  Linux swap
/dev/sda7       506472448   632301567    62914560   83  Linux
/dev/sda8       632303616   758132735    62914560   83  Linux
/dev/sda9       758134784  1250263039   246064128    7  HPFS/NTFS/exFAT
```

Can anyone help me figure out exactly what is wrong? Any help would be greatly appreciated. I'd rather not have to reinstall everything.

-Derek

---

### Post by Wim Sturkenboom on 2013-01-10
> 
... (I don't know that they were ever deleted). ...

Your first command (dd) wiped the partition table of /dev/sdc. The last 64 bytes of the 512 bytes that you wiped is the partition table; see e.g. [http://www.cyberciti.biz/faq/howto-copy-mbr/](http://www.cyberciti.biz/faq/howto-copy-mbr/)

I can't help you further with gparted; if it's about installing grub, maybe a supergrub disk or the boot-repair utility (plenty of info about the latter can be found here on the forum) can help.

---

### Post by faustism on 2013-01-10
Thanks, that's good to know. Although, I could have sworn I've done that before and just wiped the bootloader. Maybe I wiped fewer bytes in the past.

I do know how to install grub, and I have a multitude of repair disks, but the fact that I got that error, and GParted shows an issue is a concern to me.

Could someone tell me if they see anything wrong with the fdisk and TestDisk outputs?

---

### Post by sudodus on 2013-01-10
I'm no super-expert, but the output of fdisk looks good to me. I suggest try and mount the partitions! If that works and you can read the content, you can use the partition table as it is now (repaired by Testdisk).

Then the next step would be to re-install grub. I think you have a fair chance to succeed.

Good luck :-)

---

### Post by faustism on 2013-01-10
Thanks for looking at the fdisk output.

I forgot to mention that I am able to mount all of the partitions without a problem.

The only time I encounter an issue is when I try to look at the disk with GParted, or try to install GRUB

In addition to the warning about not having a partition outside of the disk, GParted outputs "Partition Table: Unrecognized"

---

### Post by sudodus on 2013-01-10
The extended partition seems to end outside the drive, but the last partition, /dev/sda9, is inside, if I get i right.

```
root@PartedMagic:~# fdisk -l /dev/sda

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250[COLOR="SeaGreen"]263728[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
...
/dev/sda4       472911894  1250[COLOR="Red"]274689  [/COLOR] 388681398    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
...
/dev/sda9       758134784  1250[COLOR="Seagreen"]263039[/COLOR]   246064128    7  HPFS/NTFS/exFAT
```

I guess gparted doesn't like that the extended partition ends outside the drive, but I think the logical partitions will work anyway. I don't know how to fix it without risking the data. If you get another drive, I'd know how to fix it (and/or to make a backup).

But maybe you can live with it, as long as the partitions work properly.

---

### Post by oldfred on 2013-01-10
Fixparts is good for extended partitions outside disk error. Both Windows & sometimes testdisk make extended beyond end. Internally they use the old CHS and in conversion round incorrectly.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

It looked like you ran the dd zero out on sdc, but testdisk on sda?

       Backup the MBR,change sdX to correct drive  e.g. sda 
sudo dd if=/dev/sdX of=mbr.bin bs=446 count=1
Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446.
dd if=/dev/zero of=/dev/sdX bs=446 count=1

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

There is almost no reason to zero out MBR as you have to overwrite it with something to be able to boot. And if not boot drive, it does not matter what is in MBR.

---

