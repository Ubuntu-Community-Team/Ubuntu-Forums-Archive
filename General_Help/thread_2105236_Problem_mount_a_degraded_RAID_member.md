---
title: "Problem mount a degraded RAID member"
date: 2013-01-15
forum: General Help
---

### Post by lprofil on 2013-01-15
Hello folks,

i run into a serious problem mounting a degraded raid 1 member.

```
sudo mdadm --detail /dev/md
```

shows me

```
/dev/md0:
        Version : 1.2
  Creation Time : Tue Jan 15 18:52:40 2013
     Raid Level : raid1
     Array Size : 48794496 (46.53 GiB 49.97 GB)
  Used Dev Size : 48794496 (46.53 GiB 49.97 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Tue Jan 15 18:57:58 2013
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : garden:0  (local to host machine)
           UUID : 7b2fed24:d9bc8394:9326810c:587fdf3b
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       65        1      active sync   /dev/sde1
```

but when i try to mount the raid member it does not seem to find the filesystem type:

```
sudo mount /dev/md0 /media/home-root
mount: you must specify the filesystem type
```

Since i do not have the second RAID member because that drive 
died due to an CRC error, i'm now stuck in a terrible situation 
and need to get the data from the remaining one to transfer it 
to two new healthy drives.

**Your help is appreciated. Thanks in advance!**

**EDIT:** With gparted i just found out that there is a 
problem with the inode table:
[IMG]http://rimdrive.de/inode.png[/IMG]

And there seems something to be wrong with the **UUID **
of the Filesystem. Anybody any clue?

/lprofil

---

### Post by lprofil on 2013-01-15
it seems to be an inode issue of the filesystem after reading [this thread in an parallel forum]("https://bbs.archlinux.org/viewtopic.php?id=139271"):

sudo dumpe2fs /dev/sde1

shows:

```
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   boot-n-root
Last mounted on:          /
Filesystem UUID:          35331ee1-5c9b-4677-b85e-3f286f39167b
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              3055616
Block count:              12206832
Reserved block count:     610341
Free blocks:              1825419
Free inodes:              3016537
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1021
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Aug  1 00:36:05 2010
Last mount time:          Tue Sep  6 21:11:38 2011
Last write time:          Fri Jul 17 02:00:17 2009
Mount count:              7
Maximum mount count:      29
Last checked:             Thu May 26 18:35:16 2011
Check interval:           15552000 (6 months)
Next check after:         Tue Nov 22 17:35:16 2011
Lifetime writes:          504 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
First orphan inode:       1318902
Default directory hash:   half_md4
Directory Hash Seed:      7735c4b2-9cf0-4c31-8644-ee1ff03ec122
Journal backup:           inode blocks
dumpe2fs: A block group is missing an inode table while reading journal inode
```

Who can give me a hint how to fix this?

/lprofil

---

### Post by lprofil on 2013-01-15
Here is my plan: since the data on the messed up disk is
very important to me, it is crucial to have a backup of it.

This is easily done since i still have to new blank hdds.

```
dd if=/dev/sde1 | pv | dd of=/dev/sdf1
```


Run this command after 

```
sudo -s
```

otherwise you run into an "Permission denied" error because
you are piping commands which are not run as root.

the "pv" part in the command is a nice feature i [found here]("http://konstantin.filtschew.de/blog/2007/07/22/partitionen-mit-dd-unter-linux-sichern-und-auch-mal-per-ssh-uber-das-netzwerk/").

After the partition is copied i will mess around on the copy
with fdisk.

I'll keep you posted on the results.


Edit: Solved!

After reading the manpage for fsck.ext4 
i finally fixed the inode-table problem
simply by:

```
fsck.ext4 /dev/sdf1
```

That easy? Piece of cake! ;)

/lprofil

---

