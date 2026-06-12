---
title: "ext3-partition is fsck-checked every bootup although configured otherwise"
date: 2008-06-13
forum: General Help
---

### Post by Verzweifler on 2008-06-13
Not sure if this is related to all variants...

The first partition of my IDE secondary master drive (i.e. /dev/sdc1) is checked by fsck every single bootup although I configured it to be checked only every 24 mounts. This is just a waste of time during each bootup sequence and is annoying since it takes two additional minutes to have the machine available for no apparent reason...

That particular partition was used as a "backup" of my previous KnoppMyth-system root-partition so I would have been able to just move the whole /dev/sdc/-drive to the primary IDE bus and could boot a working copy of KnoppMyth in case there was something crashing on the original installation. 
I do not need that "backup feature" anymore (switched to MythBuntu instead) but just use the drive (/dev/sdc3) as diskspace. 

I already tried different things to prevent the partition's check, i.e. I configured it using tune2fs to have no checking interval and a max mount count of 30:
```
michael@mythserver:~$ sudo tune2fs -l /dev/sdc1
[sudo] password for michael: 
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   Root
Last mounted on:          /
Filesystem UUID:          ef5b1729-4ba0-4cce-a97c-d1e70af4d08a
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              398400
Block count:              971924
Reserved block count:     48596
Free blocks:              338313
Free inodes:              274919
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      237
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         13280
Inode blocks per group:   415
Filesystem created:       Sat May 12 17:20:42 2007
Last mount time:          Fri Jun 13 12:22:13 2008
Last write time:          Fri Jun 13 12:22:13 2008
[B]Mount count:              1
Maximum mount count:      [COLOR="Red"]24[/COLOR]
Last checked:             Fri Jun 13 12:21:19 2008
Check interval:           [COLOR="Red"]0[/COLOR] (<none>)[/B]
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      f8e02158-4647-47fc-a116-9442c2e702ed
Journal backup:           inode blocks

```
However, after each boot, the mount count is rest to 1 (and during boot, the partition is checked)

I also modified my /etc/fstab to have the fsck-value set to 2 just like all the other partitions that behave as expected.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#
# PRIMARY MASTER
#
# /dev/sda1
UUID=ac6014f5-db1b-4501-9cf7-159c3cb98006 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d95f4146-32a7-4271-891b-7d46fc59fa8a /var/lib        ext3    relatime        0       2
# /dev/sda5
UUID=faa771d1-368a-4cdc-9377-df9cd9ab1887 none            swap    sw              0       0

#
# PRIMARY SLAVE (no fsck)
#
# /dev/sdb1
UUID=633832e0-11e4-4a8a-b43b-b75d90caf061 /var/lib/mythtv/music    xfs     defaults        0       0

#
# SECONDARY MASTER
#
# /dev/sdc1
UUID=ef5b1729-4ba0-4cce-a97c-d1e70af4d08a /media/sdc1     ext3    defaults        0       2
# /dev/sdc3
UUID=2a7e94b8-d1db-4327-b759-ea0433f7cc46 /media/sdc3     ext3    defaults        0      2

/dev/scd0                                 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Furthermore, I considered the settings made by fdisk and removed the bootable-flag from sdc1.

None of those changes had an effect on the partition's check during boot.

Any ideas or hints that probably may get rid off this "unwanted feature"?

I really appreciate the communities help!

---

### Post by Herman on 2008-06-13
I would first try running e2fsck manually from a terminal in a live CD and see if that clears up the problem.  
Try 'sudo e2fsck -C0 -p -v -f /dev/sdc1'  as in the following link, [Running a filesystem check on an ext3  filesystem.]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

If that doesn't do it you could try changing the '2' to a '0' in the 'pass' column in your /etc/fstab line for that file system.
```
# /dev/sdc1
UUID=ef5b1729-4ba0-4cce-a97c-d1e70af4d08a /media/sdc1     ext3    defaults        0       2
``````
# /dev/sdc1
UUID=ef5b1729-4ba0-4cce-a97c-d1e70af4d08a /media/sdc1     ext3    defaults        0       0
```That's not really the ideal thing to do, because after that you'll need to remember to run a file system check yourself frequently on that partition, if you forget and it gets corrupted after a while, you might lose data.
It should turn off the file system checking at boot-up for the time being, at least.

I hope my first suggestion will work.

Regards, Herman :)

---

### Post by Verzweifler on 2008-06-13
Thanks for your suggestions, Herman...

Unfortunately, the e2fsck-way did not change anything. The output was not surprising; the partition just looks ok. 

Well, I decided to completely exclude that partition from my system, until I found a solution. As I wrote, the partition is no longer required.

---

