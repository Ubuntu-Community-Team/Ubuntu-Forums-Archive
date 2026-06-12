---
title: "Corrupted MDADM Raid6"
date: 2014-06-12
forum: General Help
---

### Post by ptschack on 2014-06-12
Hi,

I fear I may have messed up my RAID. Some info:

The RAID consists of 11 hard drives (3 TB each), 2 of which are spares. It used to be 6 drives, no spares.

This happened: one drive (/dev/sdg) kept giving me SMART warnings (failure imminent). As I was trying to do a fresh install at the time, i restored a backup of my system drive (an ssd which is is wholly independent of the RAID) and booted off of that.
I hadn't realized that the backup was too old, from the time before i grew the raid... Apparently mdadm tried to mount the raid as it used to be (6 drives), and now it says the raid consists of 6 drives, all spares!

Plus the drive /dev/sdg seems to have totally failed now.

**mdadm.conf:**
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=2d18f556:0cbad263:017a87af:aadac8f7 name=brain:0

# This file was auto-generated on Sun, 03 Mar 2013 20:58:22 +0100
# by mkconf $Id$
```

**mdadm --examine outputs:**
```

mdadm: No md superblock detected on /dev/sda1.

mdadm: No md superblock detected on /dev/sdb1.

mdadm: No md superblock detected on /dev/sdc1.

mdadm: No md superblock detected on /dev/sdd1.

mdadm: No md superblock detected on /dev/sde1.

mdadm: No md superblock detected on /dev/sdf1.

mdadm: cannot open /dev/sdg1: No such file or directory

mdadm: No md superblock detected on /dev/sdh1.

mdadm: No md superblock detected on /dev/sdi1.

mdadm: No md superblock detected on /dev/sdj1.

/dev/sdk1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 5860272128 (2794.40 GiB 3000.46 GB)
     Array Size : 11720541440 (11177.58 GiB 12001.83 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 258048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 41eecef8:f5c16378:0c42cbb7:a66262d7

Internal Bitmap : 8 sectors from superblock
    Update Time : Sun Apr  6 12:36:57 2014
       Checksum : d4129908 - correct
         Events : 3848

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : spare
   Array State : AAAAAA ('A' == active, '.' == missing)

```

**dumpe2fs outputs:**
```
**/dev/sda1:**
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          5f78aca0-0621-4fad-a983-7230935b1b6b
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:19:36 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:19:37 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:19:36 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      a51a2206-3adb-4e90-89a2-4d0e69bd6da2
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdb1:**
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          438ac068-902a-42fd-a6a0-1352da761cac
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:21:42 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:21:44 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:21:42 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      70b15171-13bc-4dec-8638-b8aa4f01f9b0
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdc1:**
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4775ff03-ad4f-4a7b-87c5-d675a5f9092a
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:22:00 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:22:02 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:22:00 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      d5a04c56-e394-462e-b89c-a9ce1c509eb7
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdd1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4ffd6b00-4a71-48d5-a7e4-97822db89fb7
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:22:19 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:22:20 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:22:19 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      5f3b5e6f-eeb6-42ab-a4c9-f5fa828bd8a7
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sde1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          fda7509c-7ad3-4d63-b67b-f2ede3c55701
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:22:34 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:22:36 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:22:34 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      91b25ca7-4847-4cc8-b076-947a58d44794
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdf1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          b6bd7f6f-a2be-4bf3-bb48-f3e3bd03155d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Mar  3 02:22:51 2013
Last mount time:          n/a
Last write time:          Sun Mar  3 02:22:52 2013
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Mar  3 02:22:51 2013
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      641bfcef-ce8c-49bd-af2f-f505fec137ea
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdg1:**
Cannot find superblock

**/dev/sdh1:**
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          e3e0fe2f-5898-4035-b772-43c79670d82d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Apr 20 10:06:40 2014
Last mount time:          n/a
Last write time:          Sun Apr 20 10:06:42 2014
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Apr 20 10:06:40 2014
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      700aaa9e-e4f7-4002-9ced-9e064f88d2f0
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdi1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          c47385ef-9140-4266-80da-a0641f9c1199
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Apr 20 10:07:57 2014
Last mount time:          n/a
Last write time:          Sun Apr 20 10:07:59 2014
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Apr 20 10:07:57 2014
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      747654a9-35b5-465c-aee5-3da187ed40dd
Journal backup:           inode blocks
Journal superblock magic number invalid!

**/dev/sdj1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          0f9b6506-8703-4673-b856-35a6ea36b0ea
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Apr 20 10:08:51 2014
Last mount time:          n/a
Last write time:          Sun Apr 20 10:08:52 2014
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Apr 20 10:08:51 2014
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      c02a71ea-def8-4679-88dd-c485879eca8a
Journal backup:           inode blocks
Jounaleigenschaften:         (none)
Journalgrösse:            128M
Journal-Länge:            32768
Journal-Sequenz:          0x00000001
Journal-Start:            0
[Bunch of info about Inodes and such here]

**/dev/sdk1:**
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          3c3969e7-b556-4acd-a57a-9082e275dad8
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              183148544
Block count:              732566272
Reserved block count:     36628313
Free blocks:              721019450
Free inodes:              183148533
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      849
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Apr  6 12:35:30 2014
Last mount time:          n/a
Last write time:          Sun Apr  6 12:35:32 2014
Mount count:              0
Maximum mount count:      -1
Last checked:             Sun Apr  6 12:35:30 2014
Check interval:           0 (<none>)
Lifetime writes:          137 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      9ea8b5a1-aa8e-4902-aaa7-7760df1c5b40
Journal backup:           inode blocks
dumpe2fs: Corrupt extent header while reading Journal-Superblock
```

So the current situation is: only one drive has a valid superblock for  mdadm, and the info on that superblock is out of date (wrong number of  drives in the raid). Can anyone help?

---

### Post by ptschack on 2014-06-14
I ran **mdadm --examine /dev/sd[abcdefghijk]** and was surprised!
Apparently the superblocks are present on some the devices, even if I remember differently:

```
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 205e9ef8:deb77ef0:c1616f65:488ee07b

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : 2b351b38 - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f8150037:720c981f:f6a476e2:b98fd23a

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : d4a96c49 - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 138fa882:0164da5b:5efea797:bddf6041

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : 1853e661 - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 96eb8a2f:03191596:5f97190b:60d0967e

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : b018818a - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6886190c:e41800e8:452f1d0e:0f68dab6

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : 19d94bd4 - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 4
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 2d18f556:0cbad263:017a87af:aadac8f7
           Name : brain:0  (local to host brain)
  Creation Time : Sun Mar  3 02:34:30 2013
     Raid Level : raid6
   Raid Devices : 9

 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 20510947520 (19560.76 GiB 21003.21 GB)
  Used Dev Size : 5860270720 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fa319bfb:ffe914f0:36423faf:33634092

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Jun  9 21:52:48 2014
       Checksum : 8df7d698 - correct
         Events : 39295

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 5
   Array State : AAAAAAAAA ('A' == active, '.' == missing)

/dev/sdg:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

/dev/sdh:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

/dev/sdi:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

/dev/sdj:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

/dev/sdk:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
```


For the sake of clarity, this is how the raid looked like before it
all went wrong:

11 Drives (/dev/sd[abcdefghijk]) alltogether as a RAID 6.
2 of those are spares (/dev/sd[jk]).
1 is either close to failing of has failed (/dev/sdg).

I tried

**mdadm --assemble --run /dev/md0 -v /dev/sd[abcdefghi]**

which gave me

```
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdg
mdadm: /dev/sdg has no superblock - assembly aborted

```

So it seems I somehow have to restore the superblocks on drives
/dev/sd[ghijk], or at least on /dev/sd[ghi].
Is this possible? Any help would be greatly appreciated!

---

