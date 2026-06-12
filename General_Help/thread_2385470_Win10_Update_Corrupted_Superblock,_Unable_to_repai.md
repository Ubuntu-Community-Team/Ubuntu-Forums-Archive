---
title: "Win10 Update Corrupted Superblock, Unable to repair"
date: 2018-02-20
forum: General Help
---

### Post by wilhelmryan on 2018-02-20
Hi All, 


Quick recap:


Dual boot of Win10 and Ubuntu 16.04 worked flawlessly until Win10 Creator Update a few weeks ago. 


Got locked out of both Win10 and Ubuntu but was able to recover Windows using liveCD and repairing GRUB2. 


The system no longer uses Grub2 and instead goes straight to windows boot screen. 


Installed another HDD with a fresh install of Ubuntu to work from while trying to recover the broken partition. 


/dev/sda4 is where my old installation of Ubuntu WAS; Windows changed it from EXT4 to extended
/dev/sdc is new HDD with fresh install of 16.04 on it. 


fdisk -l:

[INDENT]Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors[/INDENT]
[INDENT]Units: sectors of 1 * 512 = 512 bytes[/INDENT]
[INDENT]Sector size (logical/physical): 512 bytes / 512 bytes[/INDENT]
[INDENT]I/O size (minimum/optimal): 512 bytes / 512 bytes[/INDENT]
[INDENT]Disklabel type: dos[/INDENT]
[INDENT]Disk identifier: 0x41563b26[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Device     Boot     Start       End   Sectors   Size Id Type[/INDENT]
[INDENT]/dev/sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT[/INDENT]
[INDENT]/dev/sda2         1026048 203836405 202810358  96.7G  7 HPFS/NTFS/exFAT[/INDENT]
[INDENT]/dev/sda3       203837440 204799999    962560   470M 27 Hidden NTFS WinRE[/INDENT]
[INDENT]**/dev/sda4       204804094 468860927 264056834 125.9G  5 Extended**[/INDENT]
[INDENT]/dev/sda5       435515392 468860927  33345536  15.9G 82 Linux swap / Solaris[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Disk /dev/sdc: 223.6 GiB, 240065183744 bytes, 468877312 sectors[/INDENT]
[INDENT]Units: sectors of 1 * 512 = 512 bytes[/INDENT]
[INDENT]Sector size (logical/physical): 512 bytes / 512 bytes[/INDENT]
[INDENT]I/O size (minimum/optimal): 512 bytes / 512 bytes[/INDENT]
[INDENT]Disklabel type: dos[/INDENT]
[INDENT]Disk identifier: 0xde5282ae[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Device     Boot     Start       End   Sectors   Size Id Type[/INDENT]
[INDENT]/dev/sdc1  *         2048 435529727 435527680 207.7G 83 Linux[/INDENT]
[INDENT]/dev/sdc2       435531774 468875263  33343490  15.9G  5 Extended[/INDENT]
[INDENT]/dev/sdc5       435531776 468875263  33343488  15.9G 82 Linux swap / Solaris[/INDENT]
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Disk /dev/mapper/cryptswap1: 15.9 GiB, 17071341568 bytes, 33342464 sectors[/INDENT]
[INDENT]Units: sectors of 1 * 512 = 512 bytes[/INDENT]
[INDENT]Sector size (logical/physical): 512 bytes / 512 bytes[/INDENT]
[INDENT]I/O size (minimum/optimal): 512 bytes / 512 bytes[/INDENT]


What I've tried (according to this site: [https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/))


*e2fsck -f /dev/sda4 

[INDENT]e2fsck 1.42.13 (17-May-2015)[/INDENT]
[INDENT]e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4[/INDENT]
[INDENT]Could this be a zero-length partition?[/INDENT]




*mke2fs -n /dev/sda4

[INDENT]mke2fs 1.42.13 (17-May-2015)[/INDENT]
[INDENT]Found a dos partition table in /dev/sda4[/INDENT]
[INDENT]Proceed anyway? (y,n) y[/INDENT]
[INDENT]mke2fs: inode_size (128) * inodes_count (0) too big for a[/INDENT]
[INDENT]    filesystem with 0 blocks, specify higher inode_ratio (-i)[/INDENT]
[INDENT]    or lower inode count (-N).[/INDENT]


*using testdisk suite to repair partition (here's where I'm confused), required deeper search and yielded the following:[INDENT]TestDisk 7.0, Data Recovery Utility, April 2015[/INDENT]
[INDENT]Christophe GRENIER <grenier@cgsecurity.org>[/INDENT]
[INDENT][http://www.cgsecurity.org](http://www.cgsecurity.org)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]Disk /dev/sda - 240 GB / 223 GiB - CHS 29185 255 63[/INDENT]
[INDENT]     Partition               Start        End    Size in sectors[/INDENT]
[INDENT] D HPFS - NTFS              0  32 33    63 221 30    1024000[/INDENT]
[INDENT] D HPFS - NTFS             63 221 30   127 155 27    1024000[/INDENT]
[INDENT] D HPFS - NTFS             63 221 31 12688  74 58  202811392[/INDENT]
[INDENT] D HPFS - NTFS             63 221 31 12748  86 10  203776000[/INDENT]
[INDENT] D HPFS - NTFS          12688  74 59 12748  53 41     962560[/INDENT]
[INDENT] D Linux                12748 118 43 27109 147 46  230711296[/INDENT]
[INDENT] D Linux                15484  58 63 16789 165 16   20971520[/INDENT]
[INDENT] D Linux                15842 213 52 17148  65  5   20971520[/INDENT]
[INDENT] D Linux                15875  88 22 17180 194 38   20971520[/INDENT]
[INDENT] D Linux                16142  74 61 17447 181 14   20971520[/INDENT]
[INDENT] D Linux                16174 204 31 17480  55 47   20971520[/INDENT]
[INDENT] D Linux                16207  79  1 17512 185 17   20971520[/INDENT]
[INDENT] D Linux                16239 208 34 17545  59 50   20971520[/INDENT]
[INDENT] D Linux                16272  83  4 17577 189 20   20971520[/INDENT]
[INDENT] D Linux Swap           16287 224  2 16809 168 63    8382464[/INDENT]
[INDENT] D Linux                16288   1 34 17593 107 50   20971520[/INDENT]
[INDENT] D Linux                16310 112 59 17615 219 12   20971520[/INDENT]
[INDENT] D Linux                16475 135 45 17780 241 61   20971520[/INDENT]
[INDENT] D Linux                17473 150 22 18778 224  6   20969472 [Downloads][/INDENT]
[INDENT] D Linux                17489 231 23 18795  50  7   20969472 [Downloads][/INDENT]
[INDENT] D Linux                17619 109 27 18924 183 11   20969472 [Downloads][/INDENT]
[INDENT] D FAT16 LBA            19477 155  7 19490  90 56     204800 [NO NAME][/INDENT]
[INDENT] D Linux                19702 124  7 19936 203 43    3764224[/INDENT]
[INDENT] D Linux                19703 129 11 19937 208 47    3764224[/INDENT]
[INDENT] D Linux                19776 238 47 20011  63 20    3764224[/INDENT]
[INDENT]>* Linux Swap           27109 147 47 29185  61 60   33345536[/INDENT]


Any pointers to repair my old partition and pull some files off? I didn't realize my nextcloud sync folder didn't include a single directory that I need :(

Thanks in advance!

---

