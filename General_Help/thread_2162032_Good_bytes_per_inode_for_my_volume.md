---
title: "Good bytes per inode for my volume?"
date: 2013-07-12
forum: General Help
---

### Post by gregom on 2013-07-12
I have a 4.5 TB RAID array that I will be saving billions (possibly more) of 8-15 KB average size JPEGs to (DVR server recording security cameras). I'm running Ubuntu 12.04.2 server and want to set this up using an Ext4 partition. Previous tests have yielded negative results, running out of inodes well before disk space. My current attempt, which has me at 73% inodes used while only utilizing 59% of disk space is still not good enough. I'm struggling to find the easiest way to calculate this. Does anyone have a specific formula in mind?

Here is a dumpe2fs -h output on my volume:
```
dumpe2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /var/cache/zoneminder/events
Filesystem UUID:          bb1005f2-f645-4bdb-893c-a25017f0ff09
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              274702336
Block count:              1098792960
Reserved block count:     54939648
Free blocks:              509712454
Free inodes:              85361678
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      762
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Jun 13 11:05:07 2013
Last mount time:          Thu Jul 11 09:08:24 2013
Last write time:          Thu Jul 11 09:08:24 2013
Mount count:              5
Maximum mount count:      -1
Last checked:             Thu Jun 13 11:05:07 2013
Check interval:           0 (<none>)
Lifetime writes:          2195 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      39547745-de01-45ff-9e0c-01a90c64fd66
Journal backup:           inode blocks
Journal features:         journal_incompat_revoke
Journal size:             128M
Journal length:           32768
Journal sequence:         0x00079838
Journal start:            829

```

Thanks in advance for any help on this...

---

