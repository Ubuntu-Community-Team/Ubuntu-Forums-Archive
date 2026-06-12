---
title: "Overwrote Windows partition"
date: 2014-05-04
forum: General Help
---

### Post by vonix on 2014-05-04
Yesterday I managed to completely overwrite my Windows partition(s) in a dualbooted system when switching distros

**Some Backstory:**
My Laptop was dualbooted with Windows 8 [~650GB] and xUbuntu [100GB], to dualboot it I had to fight with UEFI/Secureboot that came loaded on my laptop, and I figure that had part in the overwrite of the Windows partition. 
Yesterday I decided I wanted to jump off of Xubuntu and try some other Distros on my dualbooted HP Pavilion [Windows 8]. Now I had done this before on other machines with little, to no fuss. Atleast not to this severity. So I booted up Ubuntu Gnome and told it to overwrite my old Xubuntu partition. Little did I know it also decided to overwrite all the Windows partitions. I did not figure this out until the next day and after I installed updates and programs. However when I booted up the computer it skipped GRUB and went straight to GnoBuntu. I figured that this was due to UEFI/Secureboot putting up a fuss/a botched GRUB install, so I ran Ubuntu's Boot Repair tool which fixed GRUB but also tipped me off to Window's non-existance. 

**Where I am now:**
So I rifled around the Internet and found [this tutorial]("http://www.dedoimedo.com/computers/linux-data-recovery.html"). I booted up from usb and ran Testdisk and after a quick scan turned up nothing but the already installed GnoBuntu partition, I sent it off to perform a deeper scan on the now single Ubuntu Partition. Several hours later it returned this screen 
[ATTACH=CONFIG]252867[/ATTACH]
Now I have labeled what I figure some the different listed Partitions are, and I have no idea what the FAT32 partitions are from either, for they are only ~400mb.


Now where I go from here is why I'm posting. I need to recover those Windows partitions, the Linux partitions are expendable for they have been cleared/have no useful data on them. I do not want to mess up even further or make this whole attempt for naught, and the Testdisk tutorials don't aren't really helping with this part of the scenario. And I guess if the partitions aren't salvageable, I guess I will have to at least try to reclaim data with Photorec.

I also have the log that TestDisk gives:
```





Sun May  4 21:15:34 2014
Command line: TestDisk


TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.13.0-24-generic (#46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014) x86_64
Compiler: GCC 4.8
Compilation date: 2013-10-29T01:29:29
ext2fs lib: 1.42.9, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sdb: LBA, LBA48, DCO support
/dev/sdb: size       1465149168 sectors
/dev/sdb: user_max   1465149168 sectors
/dev/sdb: dco        1465149168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 1 sectors, sector size=512
Hard disk list
Disk /dev/sda - 4102 MB / 3912 MiB - CHS 3912 64 32, sector size=512 - BestBuy Geek Squad U3, FW:4.05
Disk /dev/sdb - 750 GB / 698 GiB - CHS 91201 255 63, sector size=512 - ST750LM022 HN-M750MBB, S/N:S2SUJ9AC615347, FW:2AR10002
Disk /dev/sr0 - 7340 KB / 7168 KiB - 3584 sectors (RO), sector size=2048 - BestBuy Geek Squad U3, FW:4.05


Partition table type (auto): EFI GPT
Disk /dev/sdb - 750 GB / 698 GiB - ST750LM022 HN-M750MBB
Partition table type: Intel


Analyse Disk /dev/sdb - 750 GB / 698 GiB - CHS 91201 255 63
Geometry from i386 MBR: head=255 sector=63
BAD_RS LBA=1 0
check_part_i386 1 type EE: no test
Current partition structure:
 1 P EFI GPT                  0   0  2 91201  80 63 1465149167


Bad relative sector.
No partition is bootable


search_part()
Disk /dev/sdb - 750 GB / 698 GiB - CHS 91201 255 63
FAT32 at 0/32/33
FAT1 : 32-1053
FAT2 : 1054-2075
start_rootdir : 2076 root cluster : 2
Data : 2076-1048571
sectors : 1048576
cluster_size : 8
no_of_cluster : 130812 (2 - 130813)
fat_length 1022 calculated 1022
set_FAT_info: name from BS used


FAT32 at 0/32/33
     FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
     FAT32, blocksize=4096, 536 MB / 512 MiB


recover_EXT2: s_block_group_nr=0/5557, s_mnt_count=10/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock, 745 GB / 694 GiB
     Linux Swap           90748  67  8 91201  52 35    7276528
     SWAP2 version 1, pagesize=4096, 3725 MB / 3552 MiB


Results
   * FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
     FAT32, blocksize=4096, 536 MB / 512 MiB
   P Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock, 745 GB / 694 GiB
   P Linux Swap           90748  67  8 91201  52 51    7276544
     SWAP2 version 1, pagesize=4096, 3725 MB / 3553 MiB


interface_write()
 1 * FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
 2 P Linux                   65 101 37 90748  67  7 1456820224
 3 P Linux Swap           90748  67  8 91201  52 51    7276544


search_part()
Disk /dev/sdb - 750 GB / 698 GiB - CHS 91201 255 63
FAT32 at 0/32/33
FAT1 : 32-1053
FAT2 : 1054-2075
start_rootdir : 2076 root cluster : 2
Data : 2076-1048571
sectors : 1048576
cluster_size : 8
no_of_cluster : 130812 (2 - 130813)
fat_length 1022 calculated 1022
set_FAT_info: name from BS used


FAT32 at 0/32/33
     FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
     FAT32, blocksize=4096, 536 MB / 512 MiB
FAT32 at 0/32/39
FAT1 : 32-1053
FAT2 : 1054-2075
start_rootdir : 2076 root cluster : 2
Data : 2076-1048571
sectors : 1048576
cluster_size : 8
no_of_cluster : 130812 (2 - 130813)
fat_length 1022 calculated 1022
set_FAT_info: name from BS used


FAT32 at 0/32/39
     FAT32                    0  32 33    65 101 36    1048576 [NO NAME]
     FAT32, blocksize=4096, 536 MB / 512 MiB
NTFS at 51/30/43
filesystem size           819200
sectors_per_cluster       8
mft_lcn                   34133
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS              0  32 33    51  30 43     819200 [WINRE]
     NTFS found using backup sector, blocksize=4096, 419 MB / 400 MiB
FAT32 at 51/30/44
FAT1 : 7166-7678
FAT2 : 7679-8191
start_rootdir : 8192 root cluster : 2
Data : 8192-532479
sectors : 532480
cluster_size : 8
no_of_cluster : 65536 (2 - 65537)
fat_length 513 calculated 513
set_FAT_info: name from BS used


FAT32 at 51/30/44
     FAT32                   51  30 44    84  67 47     532480 [NO NAME]
     FAT32, blocksize=4096, 272 MB / 260 MiB
FAT32 at 51/30/50
FAT1 : 7166-7678
FAT2 : 7679-8191
start_rootdir : 8192 root cluster : 2
Data : 8192-532479
sectors : 532480
cluster_size : 8
no_of_cluster : 65536 (2 - 65537)
fat_length 513 calculated 513
FAT differs, FAT sectors=496-512/513
set_FAT_info: name from BS used


FAT32 at 51/30/50
     FAT32                   51  30 44    84  67 47     532480 [NO NAME]
     FAT32, blocksize=4096, 272 MB / 260 MiB


recover_EXT2: s_block_group_nr=0/5557, s_mnt_count=10/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock, 745 GB / 694 GiB


block_group_nr 1


recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=1/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 3


recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 5


recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=5/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 7


recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 9


recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=9/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 25


recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=25/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 27


recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=27/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 49


recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=49/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 81


recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=81/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 125


recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=125/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 243


recover_EXT2: "e2fsck -b 7962624 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=243/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 343


recover_EXT2: "e2fsck -b 11239424 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=343/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 625


recover_EXT2: "e2fsck -b 20480000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=625/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 729


recover_EXT2: "e2fsck -b 23887872 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=729/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 2187


recover_EXT2: "e2fsck -b 71663616 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=2187/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


block_group_nr 2401


recover_EXT2: "e2fsck -b 78675968 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=2401/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


recover_EXT2: s_block_group_nr=0/5557, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                45255  97 27 135938  62 60 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Recover, 745 GB / 694 GiB
This partition ends after the disk limits. (start=727027712, size=1456820224, end=2183847935, disk end=1465149168)


recover_EXT2: s_block_group_nr=0/5557, s_mnt_count=7/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                45257 172 36 135940 138  6 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Recover, 745 GB / 694 GiB
This partition ends after the disk limits. (start=727064576, size=1456820224, end=2183884799, disk end=1465149168)


block_group_nr 3125


recover_EXT2: "e2fsck -b 102400000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3125/5557, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 182102528
recover_EXT2: part_size 1456820224
     Linux                   65 101 37 90748  67  7 1456820224
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 745 GB / 694 GiB


recover_EXT2: s_block_group_nr=0/1095, s_mnt_count=66/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock, 146 GB / 136 GiB


block_group_nr 1


recover_EXT2: "e2fsck -b 32768 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=1/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 3


recover_EXT2: "e2fsck -b 98304 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=3/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 5


recover_EXT2: "e2fsck -b 163840 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=5/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 7


recover_EXT2: "e2fsck -b 229376 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=7/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 9


recover_EXT2: "e2fsck -b 294912 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=9/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 25


recover_EXT2: "e2fsck -b 819200 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=25/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 27


recover_EXT2: "e2fsck -b 884736 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=27/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 49


recover_EXT2: "e2fsck -b 1605632 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=49/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 81


recover_EXT2: "e2fsck -b 2654208 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=81/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 125


recover_EXT2: "e2fsck -b 4096000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=125/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 243


recover_EXT2: "e2fsck -b 7962624 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=243/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 343


recover_EXT2: "e2fsck -b 11239424 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=343/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


recover_EXT2: s_block_group_nr=0/1095, s_mnt_count=66/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                78529 123 59 96400  78 62  287094784
     ext4 blocksize=4096 Large file Sparse superblock Recover, 146 GB / 136 GiB
This partition ends after the disk limits. (start=1261576192, size=287094784, end=1548670975, disk end=1465149168)


recover_EXT2: s_block_group_nr=0/1095, s_mnt_count=66/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                78529 253 61 96400 209  1  287094784
     ext4 blocksize=4096 Large file Sparse superblock Recover, 146 GB / 136 GiB
This partition ends after the disk limits. (start=1261584384, size=287094784, end=1548679167, disk end=1465149168)


recover_EXT2: s_block_group_nr=0/1095, s_mnt_count=66/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                78530  96 31 96401  51 34  287094784
     ext4 blocksize=4096 Large file Sparse superblock Recover, 146 GB / 136 GiB
This partition ends after the disk limits. (start=1261590528, size=287094784, end=1548685311, disk end=1465149168)


recover_EXT2: s_block_group_nr=0/1095, s_mnt_count=65/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                78539 142  4 96410  97  7  287094784
     ext4 blocksize=4096 Large file Sparse superblock Recover, 146 GB / 136 GiB
This partition ends after the disk limits. (start=1261737984, size=287094784, end=1548832767, disk end=1465149168)


block_group_nr 625


recover_EXT2: "e2fsck -b 20480000 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=625/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB


block_group_nr 729


recover_EXT2: "e2fsck -b 23887872 -B 4096 device" may be needed
recover_EXT2: s_block_group_nr=729/1095, s_mnt_count=0/4294967295, s_blocks_per_group=32768, s_inodes_per_group=8192
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 35886848
recover_EXT2: part_size 287094784
     Linux                69635  80 14 87506  35 17  287094784
     ext4 blocksize=4096 Large file Sparse superblock Backup superblock, 146 GB / 136 GiB
     Linux Swap           87506  35 18 87960  25 49    7292912
     SWAP2 version 1, pagesize=4096, 3733 MB / 3560 MiB
NTFS at 87960/26/2
filesystem size           1411463168
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS            100 148 49 87960  26  2 1411463168
     NTFS found using backup sector, blocksize=4096, 722 GB / 673 GiB
NTFS at 87960/26/3
filesystem size           52068352
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
     HPFS - NTFS          87960  26  3 91201  52 51   52068352 [RECOVERY]
     NTFS, blocksize=4096, 26 GB / 24 GiB
     Linux Swap           90748 
```

---

