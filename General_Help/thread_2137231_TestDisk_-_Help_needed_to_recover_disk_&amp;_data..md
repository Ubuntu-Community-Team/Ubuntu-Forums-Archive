---
title: "TestDisk - Help needed to recover disk &amp; data."
date: 2013-04-20
forum: General Help
---

### Post by Tom_T on 2013-04-20
Hi
Yesterday my Western Digital My World Book White Light NAS Drive stopped working.
This has a single 1TB Disk.

At first I started getting the following error:
Volume Status - Volume 'DataVolume' doesn't exist

Then the NAS refused to boot.

So I've removed the disk from the NAS and connected it to my Ubuntu laptop using a SATA to USB Cable.

Running test disk returns this :


```
Sat Apr 20 08:40:11 2013
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.0.0-21-generic (#35-Ubuntu SMP Fri May 25 17:58:20 UTC 2012)
Compiler: GCC 4.5 - Oct 17 2010 20:12:36

ext2fs lib: 1.41.14, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none

/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       312581808 sectors
/dev/sda: user_max   312581808 sectors
/dev/sda: native_max 312581808 sectors
/dev/sda: dco        312581808 sectors

Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512

Hard disk list
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - ATA ST9160310AS
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63, sector size=512 - WDC WD10 EARS-00MVWB0

Partition table type (auto): EFI GPT
Disk /dev/sdb - 1000 GB / 931 GiB - WDC WD10 EARS-00MVWB0
Partition table type: EFI GPT

Analyse Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
hdr_size=92
hdr_lba_self=1
hdr_lba_alt=1953525167 (expected 1953525167)
hdr_lba_start=34
hdr_lba_end=1953525134
hdr_lba_table=2
hdr_entries=128
hdr_entsz=128

check_part_gpt failed for partition
 1 P MS Reserved                   34     262177     262144 [Microsoft reserved partition]

Current partition structure:
No FAT, NTFS, EXT2, JFS, Reiser, cramfs or XFS marker
 1 P MS Reserved                   34     262177     262144 [Microsoft reserved partition]
 1 P MS Reserved                   34     262177     262144 [Microsoft reserved partition]

search_part()
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63

recover_EXT2: s_block_group_nr=0/14, s_mnt_count=100/33, s_blocks_per_group=32768, s_inodes_per_group=16352
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 489968
recover_EXT2: part_size 3919744
     MS Data                    64320    3984063    3919744
     EXT3 Sparse superblock, 2006 MB / 1913 MiB

Raid magic value at 247/254/8
Raid apparent size: 3919744 sectors
Raid chunk size: 0 bytes
md0 md 0.90.0 Raid 1: devices 0(8,1)*
     Linux Raid                 64320    3984191    3919872 [md0]
     md 0.90.0 Raid 1: devices 0(8,1)*, 2006 MB / 1914 MiB
     Linux Swap               3984192    4497967     513776
     SWAP2 version 1, 263 MB / 250 MiB

Raid magic value at 279/251/37
Raid apparent size: 513792 sectors
Raid chunk size: 0 bytes
md1 md 0.90.0 Raid 1: devices 0(8,2)*
     Linux Raid               3984192    4498111     513920 [md1]
     md 0.90.0 Raid 1: devices 0(8,2)*, 263 MB / 250 MiB

recover_EXT2: s_block_group_nr=0/7, s_mnt_count=82/23, s_blocks_per_group=32768, s_inodes_per_group=7728
recover_EXT2: s_blocksize=4096
recover_EXT2: s_blocks_count 246976
recover_EXT2: part_size 1975808
     MS Data                  4498176    6473983    1975808
     EXT3 Large file Sparse superblock, 1011 MB / 964 MiB

Raid magic value at 402/251/42
Raid apparent size: 1975808 sectors
Raid chunk size: 0 bytes
md3 md 0.90.0 Raid 1: devices 0(8,3)*
     Linux Raid               4498176    6474111    1975936 [md3]
     md 0.90.0 Raid 1: devices 0(8,3)*, 1011 MB / 964 MiB

Raid magic value at 402/254/45
Raid apparent size: 3733254810 sectors
MyBookWorld:2 md 1.x Raid 1 - Array Slot : 0 (0)
     Linux Raid               6474176 1953524869 1947050694 [MyBookWorld:2]
     md 1.x Raid 1 - Array Slot : 0 (0), 996 GB / 928 GiB

Results
     MS Data                    64320    3984063    3919744
     EXT3 Sparse superblock, 2006 MB / 1913 MiB
     Linux Raid                 64320    3984191    3919872 [md0]
     md 0.90.0 Raid 1: devices 0(8,1)*, 2006 MB / 1914 MiB
     Linux Swap               3984192    4497967     513776
     SWAP2 version 1, 263 MB / 250 MiB
     Linux Raid               3984192    4498111     513920 [md1]
     md 0.90.0 Raid 1: devices 0(8,2)*, 263 MB / 250 MiB
     MS Data                  4498176    6473983    1975808
     EXT3 Large file Sparse superblock, 1011 MB / 964 MiB
     Linux Raid               4498176    6474111    1975936 [md3]
     md 0.90.0 Raid 1: devices 0(8,3)*, 1011 MB / 964 MiB
   P Linux Raid               6474176 1953524869 1947050694 [MyBookWorld:2]
     md 1.x Raid 1 - Array Slot : 0 (0), 996 GB / 928 GiB

```

When I run testdisk the results table shows all the entries with a D in front of them, apart from the last one which has aP

Could someone please advise what this means and more importantly if my data is recoverable and how ??

Many Thanks

---

### Post by Tom_T on 2013-04-20
Any one any advise ?

I really need to save this data :(

Thanks.

---

### Post by oldfred on 2013-04-20
I do not understand the /mapper issue. Does the NAS use LVM or RAID? Or something proprietary?

Was NAS drive msdos(MBR) or gpt. It looks like you used gpt and that give different results than msdos would. But I do not know if /mapper is on top of gpt or has gpt  inside it??

If deeper search which may take a long time on a 1TB drive does not work, then you may need photorec.

       repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Tom_T on 2013-04-20
Hi
Many thanks for the reply.

I'm not sure what the disk format is.. I left all that as default and let the NAS do it..

I've done a deeper scan, took all day..

and this is the result :

```
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (1000 GB / 931 GiB) seems too small! (< 1965 GB / 1830 GiB)
The following partitions can't be recovered:
     MS Data                 67319776 2014370271 1947050496
     XFS 6.2+ - bitmap version, 996 GB / 928 GiB
     MS Data                128165104 2075215599 1947050496
     XFS 6.2+ - bitmap version, 996 GB / 928 GiB
     Mac HFS                128167720 2074956007 1946788288
     HFSX, 996 GB / 928 GiB
     Mac HFS                128190436 2074978723 1946788288

```

This goes on for thousands of lines........

Any help will be very gratefully appreciated

---

### Post by oldfred on 2013-04-20
I do not know anything about NAS and how they might be configured. It could be testdisk is just finding random data and trying to retranslate back into a partition table. Or the table structure is different enough that it seems that way. 

Some have had new drives and never partitioned them. They then are like very large floppy drives, but all disk tools expect partition table and have issues. 

Does vendor of NAS have recovery software or info on how it is configured?

I found this, but it looks like you need Windows to run it.
[http://wdc.custhelp.com/app/answers/detail/a_id/940/p/228,209,263/c/130/session/L3RpbWUvMTM2NjQ4MTE3Ny9zaWQvMkxtN3Fjb2w%3D](http://wdc.custhelp.com/app/answers/detail/a_id/940/p/228,209,263/c/130/session/L3RpbWUvMTM2NjQ4MTE3Ny9zaWQvMkxtN3Fjb2w%3D)

---

### Post by Tom_T on 2013-04-20
Thanks
I'll try the WDC Util and see how I get on !

---

### Post by Tom_T on 2013-04-22
Hi
The WDC disk util wouldn't detect the disk if it was in the NAS or via SATA/USB

Any other ideas ?

---

### Post by oldfred on 2013-04-22
I am out of ideas. Does the vendor site have any more info, since it is a bit different than just standard drive configuration.

---

### Post by Tom_T on 2013-04-23
The disk is an XFS disk
[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

Using either 

NAS Data Recovery 
[http://www.runtime.org/nas-recovery.htm](http://www.runtime.org/nas-recovery.htm)

or 
Raise Data Recovery for XFS 5.8
[http://www.softpedia.com/get/System/Back-Up-and-Recovery/Raise-Data-Recovery-for-XFS.shtml](http://www.softpedia.com/get/System/Back-Up-and-Recovery/Raise-Data-Recovery-for-XFS.shtml)

I can see my data.. Raise is only around £20.00 for a licence.
So that seems to be the way to go.

Hope this helps someone else.

---

### Post by oldfred on 2013-04-23
Thanks for update, that is good to know.

Some more info on file systems.

 Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[URL="http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1"]http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1

[/URL]  xfsprogs needed for xfs partitions, new install may not add.

[URL="http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1"]
[/URL]

---

