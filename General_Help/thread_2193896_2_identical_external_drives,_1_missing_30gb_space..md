---
title: "2 identical external drives, 1 missing 30gb space."
date: 2013-12-15
forum: General Help
---

### Post by tiggy2040 on 2013-12-15
Ubuntu 12.04 TLS

*Note* i did use "tune2fs -m 0" on both drives to set the reserved blocks to 0% so i assume it can not be due to this.

I have 2 external 2TB HDD's, both formatted with ext3.


```

df -h
/dev/sdb1       1.8T  1.8T   53G  98% /media/GAMES
/dev/sdc1       1.8T  1.8T   24G  99% /media/GAMES_

29GB difference

```

running "du" as root on both drives gives exact same file usage, both trash folders are empty, so trying "df" without -h i got the following.

```

Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sdb1      1922857776 1867923964  54933812  98% /media/GAMES
/dev/sdc1      1892330288 1867756624  24573664  99% /media/GAMES_

So here i assumed; 

1922857776 - 1892330288 = 30527488 Blocks

30527488 x 1024 = 31260147712 bytes

31260147712 bytes are around 29GB 

```

How do i get these 29GB back ?  i can't find whats using it and ii really don't wanna wipe the partition again and copy, as it takes around 40 hours :(

Thanks for any help.

**Drive1 sdb1:**
```
tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   GAMES
Last mounted on:          <not available>
Filesystem UUID:          a8e139a8-ca14-4a32-ac26-73c762242a21
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              122101760
Block count:              488377856
Reserved block count:     0
Free blocks:              13733453
Free inodes:              122101276
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      907
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Filesystem created:       Sat Jan  7 04:54:40 2012
Last mount time:          Sun Dec 15 05:37:41 2013
Last write time:          Sun Dec 15 05:37:41 2013
Mount count:              99
Maximum mount count:      -1
Last checked:             Sat Jan  7 04:54:40 2012
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      b5cfe04f-1d74-4717-b59e-b221c857fa09
Journal backup:           inode blocks

```

**Drive2 sdc1:**
```
tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   GAMES
Last mounted on:          <not available>
Filesystem UUID:          b461b7b0-c114-7b2f-aad8-17adc93ae067
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244203520
Block count:              488377344
Reserved block count:     0
Free blocks:              6143416
Free inodes:              244203036
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   1024
Filesystem created:       Tue Dec 10 13:49:22 2013
Last mount time:          Sun Dec 15 05:37:43 2013
Last write time:          Sun Dec 15 05:37:43 2013
Mount count:              7
Maximum mount count:      20
Last checked:             Tue Dec 10 13:49:22 2013
Check interval:           15552000 (6 months)
Next check after:         Sun Jun  8 14:49:22 2014
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      40d2270f-b8a8-bbb9-f559-d66d26879e5d
Journal backup:           inode blocks

```

---

### Post by ajgreeny on 2013-12-15
There are some differences in your tune2fs outputs, and I note in sdb there is a line
```
Reserved GDT blocks:      907
```
but I can not find anything about what gdt blocks do, though they seem to be involved in some way in filesystem resizing.

There is also this difference in group info, which again means nothing to me, but I wonder if the filesystems were made using different utilities; they were certainly made almost two years apart.
This output is from diff -y with sdb on the left and sdc on the right.
```
Blocks per group:         32768                    Blocks per group:         32768
Fragments per group:      32768                    Fragments per group:      32768
Inodes per group:         8192                      |    Inodes per group:         16384
Inode blocks per group:   512                      |    Inode blocks per group:   1024
Filesystem created:       Sat Jan  7 04:54:40 2012          |    Filesystem created:       Tue Dec 10 13:49:22 2013

```

---

### Post by tiggy2040 on 2013-12-15
> **ajgreeny said:**
> There are some differences in your tune2fs outputs, and I note in sdb there is a line


you are correct, the "newest" hdd was purchased a few weeks ago and formatted on windows with acronis as ext3.

There is a small difference in the filesystem, but i can't believe this would affect the size too much, but i could be wrong. 

gparted output is as so:

[Disk 1]("http://imgur.com/jnlp5nK")
[Disk 2]("http://imgur.com/vV7N2d2")

as you can see, even gparted reports that somehow Disk 2 is using 29gb more as disk 1, but i can't find at all where its gone.

---

### Post by tiggy2040 on 2013-12-16
So i formatted the drive under ubuntu and i am still missing 29GB i have no clue what i should do, i can format it NTFS in windows and get the entire 2TB why is linux taking 29GB ? and for what ?

```
sudo mkfs.ext3 -m 0 /dev/sdb1

mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
122101760 inodes, 488377856 blocks
0 blocks (0.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
14905 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848


Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done
```

df -h shows correct size
> 
/dev/sdb1       1.8T  196M  1.8T   1% /media/3f8c5f46-8dea-43e1-93fb-59f6c24da9a3


Gparted again shows 29gb used for something.
[Drive Fresh Formatted]("http://imgur.com/XL7r8QV")

---

### Post by Impavidus on 2013-12-16
Drive 1 has 122101760 inodes, drive 2 has 244203520 inodes, twice as many. If I'm correct, the inode table is statically allocated at the time of filesystem creation and subtracted from the available space. I really don't know the size of an inode, but the difference of 122101760 inodes can explain the 29GB difference if it's about 250 bytes/inode. Apparently, you used different (versions of) programs to format the drives and they used different defaults for the number of inodes.

I wouldn't really bother about 1.5% of your disk space. Getting it available wouldn't buy you much time until you need a bigger drive anyway. Two weeks or so.

---

