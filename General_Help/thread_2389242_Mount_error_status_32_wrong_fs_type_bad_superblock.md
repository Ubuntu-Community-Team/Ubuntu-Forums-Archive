---
title: "Mount error status 32 wrong fs type bad superblock missing codepage"
date: 2018-04-13
forum: General Help
---

### Post by dez93_2000 on 2018-04-13
Hi all. I recently bought a 3TB sata drive to replace 2*500mb satas; none were booters. Having formatted the 3tb as ext4 and half filled it, I then used gparted to shrink it a bit, make a new partition and make that partition NTFS for games. Then the fun started. Because I didn't have "nobootwait" entries in fstab, the machine wouldn't start because it couldn't find the old HDDs. Having fixed that with a liveUSB, it boots fine but gives the following error when I click to mount the ext4 partition (the NTFS automounts per the line I added in fstab):

```
Error mounting system-managed device /dev/sda1:
Command-line `mount "/media/Seagate"' exited with non-zero exit status 32:
mount: /media/Seagate:
wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error.
```

Based on other people's similar problems I tried:

```
sudo fdisk -l
Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 630F2C0B-1256-4FD7-8792-552C4130EB0F
Device          Start        End    Sectors  Size Type
/dev/sda1        2048 4631732223 4631730176  2.2T Linux filesystem
/dev/sda2  4631732224 5860532223 1228800000  586G Microsoft basic data
```

```
sudo tune2fs -l /dev/sda1 | grep feature
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file dir_nlink extra_isize metadata_csum
```

```

sudo fsck.ext4 /dev/sda1
e2fsck 1.43.5 (04-Aug-2017)
Seagate: clean, 691020/144744448 files, 383798705/578966272 blocks
```

```
sudo fsck.ext4 -f /dev/sda1
e2fsck 1.43.5 (04-Aug-2017)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Seagate: 691020/144744448 files (2.5% non-contiguous), 383798705/578966272 blocks
```

And used gparted's check:

```
GParted 0.28.1 --enable-libparted-dmraid --enable-online-resize
 Libparted 3.2
  [TABLE]
[TR]
[TD="colspan: 2"] **Check and repair file system (ext4) on /dev/sda1**  00:00:19    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda1 (partition)
start: 2048
end: 4631732223
size: 4631730176 (2.16 TiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] check file system on /dev/sda1 for errors and (if possible) fix them  00:00:19    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***e2fsck -f -y -v -C 0 /dev/sda1***  00:00:19    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
                                                                               
      691020 inodes used (0.48%, out of 144744448)
       16860 non-contiguous files (2.4%)
          90 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 689957/1055
   383798705 blocks used (66.29%, out of 578966272)
           0 bad blocks
          16 large files

      650710 regular files
       40301 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
      691011 files
[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]e2fsck 1.43.5 (04-Aug-2017)
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] grow file system to fill the partition  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***resize2fs -p /dev/sda1***  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]resize2fs 1.43.5 (04-Aug-2017)
The filesystem is already 578966272 (4k) blocks long.  Nothing to do![/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

Thus: I'm lost! It looks fine based on every diagnostic I've seen online, and IIRC the expected folders were in the Seagate partition when I booted to the liveUSB. I can use gparted to mount it to media/Seagate but then there are 2 Seagate folders and they're both blank.

Any ideas very much appreciated! Thanks.

---

### Post by dez93_2000 on 2018-04-13
Solved: in the thread which tipped me off about fstab being the reason the machine wouldn't boot before, someone advised adding "nofail" and "nobootwait" after "default" i.e.
```
 default,nobootwait,nofail 
```

BUT after trying to mount the drive, failing, then typing ```
 dmesg | tail 
``` into the terminal, I saw that apparently "nobootwait" isn't a recognised command and this was preventing the partition from mounting (bot not preventing the NTFS partitions from mounting, oddly).

Hopefully this will prevent others from trying nobootwait.

---

