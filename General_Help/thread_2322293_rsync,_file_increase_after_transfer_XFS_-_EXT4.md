---
title: "rsync, file increase after transfer XFS - EXT4"
date: 2016-04-27
forum: General Help
---

### Post by Drenriza on 2016-04-27
Hi all

I am trying to transfer a series of files from one system to another, but when i do this the file size at the destination increase to above 2T (destination) from 1.4T (source).
And i don't understand what can create this behavior when the sector size at both systems is the same, and i have no sparse files.

Anyone who has a suggestion to what i could / should check?

```

fdisk -l /dev/device

```

Source
2181.8 GB in size
XFS
sector size 512 bytes

Destination
2147.5 GB
EXT4
sector size 512 bytes

Files to transfer from source 1.4T
Files increase to +2T at destination (rsync runs out of disk space and exit)

Command
```

rsync -a --itemize-changes --recursive --compress --sparse --delete --rsync-path="sudo rsync" -v -e "ssh -t -v" /path1/ USER@IP:/newServer/

```

When i want to confirm the filesystem block size by running (source)
```

dumpe2fs /dev/xvdc1 |fgrep -e "Block size"

```
I get the error
> 
dumpe2fs: Bad magic number in super-block while trying to open /dev/xvdc1


Hope someone can give a suggestion to what can cause this.
Thanks on advance all!

---

### Post by T.J. on 2016-04-27
Sector size is one thing, but minimum block size is quite another.    The block use can vary by file system, while the physical sectors remain the same. There are also whatever conditions are set up on your volumes.  I'd consider verifying the block size as a possible place to start looking.

I'd think you are getting a superblock error because you might be trying to use a EXT 2/3/4 tool on an XFS filesystem. If I am missing something obvious I apologise.

---

### Post by Drenriza on 2016-04-28
> 
I'd think you are getting a superblock error because you might be trying to use a EXT 2/3/4 tool on an XFS filesystem

Thanks! 

So i ran the filesystem specific commands, to get info about their setup.

EXT4 (destination)
```

sudo dumpe2fs /dev/xvdb1 |grep -i "size"

```

> 
Block size:               4096
Fragment size:            4096
Flex block group size:    16
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal size:             128M


XFS (source)
```

xfs_info /dev/xvdc1

```

> 
meta-data=/dev/xvdc1             isize=256    agcount=4, agsize=133169088 blks
         =                       sectsz=512   attr=2
data     =                       bsize=4096   blocks=532676352, imaxpct=5
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0
log      =internal               bsize=4096   blocks=260095, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0


From what i can tell both filesystems says that they have a block size of 4096.

---

### Post by Drenriza on 2016-04-28
-H, --hard-links            preserve hard links

Faceplam

---

### Post by HermanAB on 2016-04-28
Using rsync means that the files are guaranteed identical.  The main difference I think, would be the size of the Ext4 journal.

It may help to use btrfs or openzfs and deduplicate blocks.

---

