---
title: "Lost Partitions"
date: 2017-02-13
forum: General Help
---

### Post by disabled_July202024 on 2017-02-13
Hi,

i lost my win7 and ubuntu mate installation when i try to shrink some data from win7 partition to be able to use as swap,in the process i lost my access to both my os and i'm currently at no boot disk error

my gparted and testdisk results are attached and the fdisk -l output is given below

how to recover atleast my win7 i can reinstall my linux installation from scratch with additional swap and home partitions.

ThankYou

```
it@it:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.5 GiB, 1593864192 bytes, 3113016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x4a5c2cb0

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1            2048   1026047   1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 146831359 145805312 69.5G  7 HPFS/NTFS/exFAT
/dev/sda3       146834163 188763749  41929587   20G  7 HPFS/NTFS/exFAT

Partition 3 does not start on physical sector boundary.


Disk /dev/sdb: 7.5 GiB, 8004304896 bytes, 15633408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x003cbe50

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15633407 15631360  7.5G  b W95 FAT32

```

---

### Post by howefield on 2017-02-13
Moved to the "*General Help*" forum as requested.

---

### Post by yancek on 2017-02-13
If you want to modify a windows partition, the best way to do that is to use the windows Disk Management tool to shrink a partition to create unallocated space and then immediatly run chkdsk from windows.  Not knowing specifically what you did to "shrink some data" it is difficult to suggest a way to 'undo' it.  Your fdisk and gparted output does not show any Linux partitions although testdisk shows that a Linux partition.  If you want to repair your windows system, the best option is to use the Repair option on the windows installation DVD.  Posting more specifics on what you did exactly might give someone familiar with windows an idea of something you could try.

---

### Post by disabled_July202024 on 2017-02-13
@yancek
i did try startup repair from win7 disc but it didn't find any win7 installations.

anyway to recover the partitions using testdisk

---

### Post by oldfred on 2017-02-13
Windows boots from MBR to PBR, partition boot sector. And PBR has more boot code.
But MBR has to tell Windows boot loader which PBR to use and that is the boot flag.

You show no boot flag for any NTFS partition. You can use gparted, set flags , or Windows repair console and make active command. Active is the boot partition.
First try to put boot flag on NTFS partition. If you have a Windows partition with these files it may boot or else it needs chkdsk. After any resize Windows must run chkdsk as PBR has start & size of partition and that must match partition table.

Windows in BIOS boot mode typically has a small 100MB boot partition with 
 /bootmgr /Boot/BCD.
And main install has        
 /Windows/System32/winload.exe 

But separate boot partition is not required if boot flag is on main ( c: drive) partition and all 3 boot files are in that partition. But I think repair console f8 is also in boot partition so you want t separate repair/install disk with repair tools.

---

### Post by disabled_July202024 on 2017-02-13
if i set first 3 ntfs partition on P and the remaing on L and write will this work

and where to set it on extended volume on testdisk.

---

### Post by oldfred on 2017-02-13
Always backup current partition table and save to another device. Then you can go back if first selection is not correct.

 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sda > parts_sda.txt

---

### Post by disabled_July202024 on 2017-02-13
is this ok

---

### Post by disabled_July202024 on 2017-02-13
here is the testdisk.log file

```


Tue Feb 14 03:39:14 2017
Command line: TestDisk

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 4.4.0-31-generic (#50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016) x86_64
Compiler: GCC 5.3
ext2fs lib: 1.42.13, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none, curses lib: ncurses 6.0
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       1953525168 sectors
/dev/sda: user_max   1953525168 sectors
/dev/sda: native_max 1953525168 sectors
/dev/sda: dco        1953525168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 0 sectors, sector size=512
Hard disk list
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - WDC WD10EZRX-00L4HB0, S/N:WD-WCC4JRAJ8HZZ, FW:01.01A01
Disk /dev/sdb - 8004 MB / 7633 MiB - CHS 1020 247 62, sector size=512 - SanDisk Cruzer Blade, FW:1.27

Partition table type (auto): Intel
Disk /dev/sda - 1000 GB / 931 GiB - WDC WD10EZRX-00L4HB0
Partition table type: Intel

Analyse Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/32/33
NTFS at 63/221/31
NTFS at 9140/1/1
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 P HPFS - NTFS              0  32 33    63 221 30    1024000
 2 P HPFS - NTFS             63 221 31  9139 211 32  145805312
 3 P HPFS - NTFS           9140   1  1 11749 254 63   41929587
No partition is bootable

search_part()
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
NTFS at 0/32/33
filesystem size           1024000
sectors_per_cluster       8
mft_lcn                   42666
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
NTFS at 63/221/31
filesystem size           145805312
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS             63 221 31  9139 211 32  145805312
     NTFS, blocksize=4096, 74 GB / 69 GiB
NTFS at 9140/1/1
filesystem size           41929587
sectors_per_cluster       8
mft_lcn                   3
mftmirr_lcn               2620599
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS           9140   1  1 11749 254 63   41929587
     NTFS, blocksize=4096, 21 GB / 19 GiB

recover_EXT2: s_block_group_nr=0/79, s_mnt_count=1/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 2617920
recover_EXT2: part_size 20943360
     Linux                11750 136 35 13054  50 52   20943360
     ext4 blocksize=4096 Large_file Sparse_SB, 10723 MB / 10226 MiB
NTFS at 13054/75/14
filesystem size           209715200
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          13054  75 14 26108 117 57  209715200
     NTFS, blocksize=4096, 107 GB / 100 GiB
NTFS at 26108/150/27
filesystem size           209715200
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          26108 150 27 39162 193  7  209715200
     NTFS, blocksize=4096, 107 GB / 100 GiB
NTFS at 39162/225/40
filesystem size           419430400
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          39162 225 40 65271  56  1  419430400
     NTFS, blocksize=4096, 214 GB / 200 GiB
NTFS at 65271/88/34
filesystem size           419430400
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          65271  88 34 91379 173 58  419430400
     NTFS, blocksize=4096, 214 GB / 200 GiB
NTFS at 91379/206/28
filesystem size           485505024
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          91379 206 28 121601  25 24  485505024
     NTFS, blocksize=4096, 248 GB / 231 GiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=255 nbr=2

Results
     HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
     HPFS - NTFS             63 221 31  9139 211 32  145805312
     NTFS, blocksize=4096, 74 GB / 69 GiB
     HPFS - NTFS           9140   1  1 11749 254 63   41929587
     NTFS, blocksize=4096, 21 GB / 19 GiB
     Linux                11750 136 35 13054  75 13   20944896
     ext4 blocksize=4096 Large_file Sparse_SB, 10723 MB / 10227 MiB
     HPFS - NTFS          13054  75 14 26108 117 57  209715200
     NTFS, blocksize=4096, 107 GB / 100 GiB
     HPFS - NTFS          26108 150 27 39162 193  7  209715200
     NTFS, blocksize=4096, 107 GB / 100 GiB
     HPFS - NTFS          39162 225 40 65271  56  1  419430400
     NTFS, blocksize=4096, 214 GB / 200 GiB
     HPFS - NTFS          65271  88 34 91379 173 58  419430400
     NTFS, blocksize=4096, 214 GB / 200 GiB
     HPFS - NTFS          91379 206 28 121601  25 24  485505024
     NTFS, blocksize=4096, 248 GB / 231 GiB

Hint for advanced users. dmsetup may be used if you prefer to avoid to rewrite the partition table for the moment:
echo "0 1024000 linear /dev/sda 2048" | dmsetup create test0
echo "0 145805312 linear /dev/sda 1026048" | dmsetup create test1
echo "0 41929587 linear /dev/sda 146834163" | dmsetup create test2
echo "0 20944896 linear /dev/sda 188772352" | dmsetup create test3
echo "0 209715200 linear /dev/sda 209717248" | dmsetup create test4
echo "0 209715200 linear /dev/sda 419434496" | dmsetup create test5
echo "0 419430400 linear /dev/sda 629151744" | dmsetup create test6
echo "0 419430400 linear /dev/sda 1048584192" | dmsetup create test7
echo "0 485505024 linear /dev/sda 1468016640" | dmsetup create test8
ntfs_device_testdisk_io_ioctl() unimplemented


dir_partition inode=5
     HPFS - NTFS             63 221 31  9139 211 32  145805312
     NTFS, blocksize=4096, 74 GB / 69 GiB
Directory /
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 .
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 ..
      57 dr-xr-xr-x     0      0         0 30-Mar-2016 07:12 $Recycle.Bin
    5321 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 6awrap68
  149112 dr-xr-xr-x     0      0         0 29-Nov-2016 16:11 6b2a0d656378b8604969199d
   98894 dr-xr-xr-x     0      0         0 24-Aug-2016 05:13 AnuSM
     183 dr-xr-xr-x     0      0         0 19-Jan-2017 14:58 Boot
  148050 dr-xr-xr-x     0      0         0 12-Feb-2017 14:55 Config.Msi
  103844 dr-xr-xr-x     0      0         0  9-Jan-2017 13:16 CryptoPreventQuarantine
   97601 dr-xr-xr-x     0      0         0 28-Feb-2016 13:36 Intel
   85184 dr-xr-xr-x     0      0         0  4-Mar-2016 07:35 LJM1005_MFP_Full_Solution
   85829 dr-xr-xr-x     0      0         0 29-Feb-2016 15:34 MSOCache
   96128 dr-xr-xr-x     0      0         0  8-Feb-2017 13:51 NST
      58 dr-xr-xr-x     0      0         0 14-Jul-2009 03:20 PerfLogs
      60 dr-xr-xr-x     0      0         0  9-Feb-2017 14:50 Program Files
     274 dr-xr-xr-x     0      0         0  1-Feb-2017 04:19 Program Files (x86)
     392 dr-xr-xr-x     0      0         0 12-Feb-2017 15:28 ProgramData
   84284 dr-xr-xr-x     0      0         0 30-Apr-2016 13:12 Recovery
   84904 dr-xr-xr-x     0      0         0 12-Feb-2017 14:41 System Volume Information
     496 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Users
     686 dr-xr-xr-x     0      0         0  5-Feb-2017 14:35 Windows
  148066 dr-xr-xr-x     0      0         0  1-Dec-2016 10:16 XiaoMi
   24069 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Ypackage69
  135163 dr-xr-xr-x     0      0         0 27-May-2016 15:29 adb
  135454 dr-xr-xr-x     0      0         0 29-Nov-2016 14:40 cb0430bfb0222b7d1b88378a
  156489 dr-xr-xr-x     0      0         0  1-Dec-2016 11:34 mi
  103304 -r--r--r--     0      0      1024  8-Jun-2016 13:10 AMTAG.BIN
   94675 -r--r--r--     0      0    274596  8-Feb-2017 13:51 ANG0
   85448 -r--r--r--     0      0    274596 29-Feb-2016 07:31 ANG0.tmp
   84100 -r--r--r--     0      0    271158  1-Aug-2016 11:23 DUMP3004.tmp
   86154 -r--r--r--     0      0    272150  1-Aug-2016 11:36 DUMP642e.tmp
   97685 -r--r--r--     0      0    361868  8-Feb-2017 13:03 LEOPT
   86212 -r--r--r--     0      0    446865  3-Feb-2017 15:15 MXLUE
  155774 -r--r--r--     0      0      1521 29-Nov-2016 15:17 MicRooCerAut2011_2011_03_22.crt
   90841 -r--r--r--     0      0    441601 30-Apr-2016 00:04 NMIBK
  139523 -r--r--r--     0      0    464888  6-Feb-2017 12:29 PSZWB
   24484 -r--r--r--     0      0    393991 31-Jan-2017 15:10 PUBOF
   91082 -r--r--r--     0      0    449226 20-Aug-2016 23:01 QBLVU
  138441 -r--r--r--     0      0    298243  6-Feb-2017 08:31 ZWONT
    1279 -r--r--r--     0      0         0 19-Jan-2017 14:58 asc_rdflag
   85315 -r--r--r--     0      0    383786 21-Nov-2010 03:23 bootmgr
   85384 -r--r--r--     0      0    383786 29-Feb-2016 07:08 bootmgr.tmp
      20 -r--r--r--     0      0     10168 24-Nov-2016 10:53 bootsqm.dat
   87442 -r--r--r--     0      0 3453214720 12-Feb-2017 15:24 pagefile.sys
ntfs_device_testdisk_io_ioctl() unimplemented


dir_partition inode=5
   P HPFS - NTFS              0  32 33    63 221 30    1024000
     NTFS, blocksize=4096, 524 MB / 500 MiB
Directory /
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 .
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 ..
     189 dr-xr-xr-x     0      0         0 13-May-2016 02:59 $RECYCLE.BIN
     197 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Adocuments11
      35 dr-xr-xr-x     0      0         0 29-Feb-2016 00:31 Boot
     106 dr-xr-xr-x     0      0         0  5-Mar-2016 13:45 Kaspersky Rescue Disk 10.0
     196 dr-xr-xr-x     0      0         0 30-May-2016 03:11 Program Files
     101 dr-xr-xr-x     0      0         0 29-Feb-2016 20:57 Recovery
      97 dr-xr-xr-x     0      0         0 29-Feb-2016 00:33 System Volume Information
     208 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Tstore62
      96 -r--r--r--     0      0      8192 29-Feb-2016 00:31 BOOTSECT.BAK
      99 -r--r--r--     0      0    405508 28-Apr-2016 10:55 RPIYN
     188 -r--r--r--     0      0         0 30-Apr-2016 12:54 Recovery.txt
      85 -r--r--r--     0      0    383786 21-Nov-2010 03:23 bootmgr
ntfs_device_testdisk_io_ioctl() unimplemented


dir_partition inode=5
   P HPFS - NTFS             63 221 31  9139 211 32  145805312
     NTFS, blocksize=4096, 74 GB / 69 GiB
Directory /
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 .
       5 dr-xr-xr-x     0      0         0 12-Feb-2017 15:27 ..
      57 dr-xr-xr-x     0      0         0 30-Mar-2016 07:12 $Recycle.Bin
    5321 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 6awrap68
  149112 dr-xr-xr-x     0      0         0 29-Nov-2016 16:11 6b2a0d656378b8604969199d
   98894 dr-xr-xr-x     0      0         0 24-Aug-2016 05:13 AnuSM
     183 dr-xr-xr-x     0      0         0 19-Jan-2017 14:58 Boot
  148050 dr-xr-xr-x     0      0         0 12-Feb-2017 14:55 Config.Msi
  103844 dr-xr-xr-x     0      0         0  9-Jan-2017 13:16 CryptoPreventQuarantine
   97601 dr-xr-xr-x     0      0         0 28-Feb-2016 13:36 Intel
   85184 dr-xr-xr-x     0      0         0  4-Mar-2016 07:35 LJM1005_MFP_Full_Solution
   85829 dr-xr-xr-x     0      0         0 29-Feb-2016 15:34 MSOCache
   96128 dr-xr-xr-x     0      0         0  8-Feb-2017 13:51 NST
      58 dr-xr-xr-x     0      0         0 14-Jul-2009 03:20 PerfLogs
      60 dr-xr-xr-x     0      0         0  9-Feb-2017 14:50 Program Files
     274 dr-xr-xr-x     0      0         0  1-Feb-2017 04:19 Program Files (x86)
     392 dr-xr-xr-x     0      0         0 12-Feb-2017 15:28 ProgramData
   84284 dr-xr-xr-x     0      0         0 30-Apr-2016 13:12 Recovery
   84904 dr-xr-xr-x     0      0         0 12-Feb-2017 14:41 System Volume Information
     496 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Users
     686 dr-xr-xr-x     0      0         0  5-Feb-2017 14:35 Windows
  148066 dr-xr-xr-x     0      0         0  1-Dec-2016 10:16 XiaoMi
   24069 dr-xr-xr-x     0      0         0 12-Feb-2017 15:24 Ypackage69
  135163 dr-xr-xr-x     0      0         0 27-May-2016 15:29 adb
  135454 dr-xr-xr-x     0      0         0 29-Nov-2016 14:40 cb0430bfb0222b7d1b88378a
  156489 dr-xr-xr-x     0      0         0  1-Dec-2016 11:34 mi
  103304 -r--r--r--     0      0      1024  8-Jun-2016 13:10 AMTAG.BIN
   94675 -r--r--r--     0      0    274596  8-Feb-2017 13:51 ANG0
   85448 -r--r--r--     0      0    274596 29-Feb-2016 07:31 ANG0.tmp
   84100 -r--r--r--     0      0    271158  1-Aug-2016 11:23 DUMP3004.tmp
   86154 -r--r--r--     0      0    272150  1-Aug-2016 11:36 DUMP642e.tmp
   97685 -r--r--r--     0      0    361868  8-Feb-2017 13:03 LEOPT
   86212 -r--r--r--     0      0    446865  3-Feb-2017 15:15 MXLUE
  155774 -r--r--r--     0      0      1521 29-Nov-2016 15:17 MicRooCerAut2011_2011_03_22.crt
   90841 -r--r--r--     0      0    441601 30-Apr-2016 00:04 NMIBK
  139523 -r--r--r--     0      0    464888  6-Feb-2017 12:29 PSZWB
   24484 -r--r--r--     0      0    393991 31-Jan-2017 15:10 PUBOF
   91082 -r--r--r--     0      0    449226 20-Aug-2016 23:01 QBLVU
  138441 -r--r--r--     0      0    298243  6-Feb-2017 08:31 ZWONT
    1279 -r--r--r--     0      0         0 19-Jan-2017 14:5
```

---

### Post by oldfred on 2017-02-13
I have not idea. 
If you reboot do you see correct partitions?
Did you backup original partition table?
Do you have good backups of your data, so whatever happens is not the end of the world?

---

### Post by disabled_July202024 on 2017-02-14
after setting every thing above as shown in the above picture ihave now recovered everything is working ok except the linux which i will to reinstall again.Thankyou all for the help.and how do set it as solved.

---

### Post by disabled_July202024 on 2017-02-14
after setting every thing above as shown in the above picture ihave now recovered everything is working ok except the linux which i will to reinstall again.Thankyou all for the help.

---

### Post by disabled_July202024 on 2017-02-14
after setting every thing above as shown in the above picture ihave now recovered everything is working ok except the linux which i will to reinstall again.Thankyou all for the help.

---

