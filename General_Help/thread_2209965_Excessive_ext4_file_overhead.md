---
title: "Excessive ext4 file overhead"
date: 2014-03-08
forum: General Help
---

### Post by Marcello_Marques on 2014-03-08
I'm experiencing a baffling problem with two 12.04.4 servers I've just installed - there is what appears to be excessive file system overhead for anything I save on its folders; for example, a single 4120-byte text file results in 1.1MB used space:

```
ubuntu@storage02:/backup/NirSoft$ls
total 1.1M
drwxr-xr-x 2 nobody nogroup  32K Mar  8 09:15 .
drwxrwxrwx 4 root   root    4.0K Mar  8 08:58 ..
-rwxr--r-- 1 nobody nogroup 4.1K Oct 14  2010 RegFileExport_readme.txt
ubuntu@storage02:/backup/NirSoft$du -h
1.1M
```    

If I add another file of roughly the same size, the used space rises to 2.1MB, and so forth:

```
ubuntu@storage02:/backup/NirSoft$ls
total 2.1M
drwxr-xr-x 2 nobody nogroup  32K Mar  8 09:31 .
drwxrwxrwx 4 root   root    4.0K Mar  8 08:58 ..
-rwxr--r-- 1 nobody nogroup 4.1K Oct 14  2010 RegFileExport_readme.txt
-rwxr--r-- 1 nobody nogroup 4.0K Jan  4 21:34 whosip_readme.txt
ubuntu@storage02:/backup/NirSoft$du -h
2.1M
```

This is the result of running tune2fs on the affected partition:

```
ubuntu@storage02:/backup/NirSoft$sudo tune2fs -l /dev/mapper/storage02--vg-root
tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /
Filesystem UUID:          1ff9c84f-e11b-4b55-8b68-1451cc68f05e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              60899328
Block count:              243594240
Reserved block count:     12179712
Free blocks:              239168340
Free inodes:              60749233
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      965
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Thu Mar  6 11:35:56 2014
Last mount time:          Fri Mar  7 12:30:16 2014
Last write time:          Thu Mar  6 11:49:02 2014
Mount count:              6
Maximum mount count:      -1
Last checked:             Thu Mar  6 11:35:56 2014
Check interval:           0 (<none>)
Lifetime writes:          12 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      d22a76e0-2480-4607-805f-d7710cbb8dbd
Journal backup:           inode blocks
```

Can anyone help me, or at least explain what could be causing this?

TIA

Marcello Marques
São Paulo - SP - Brazil

---

