---
title: "Optimizing ext4 for large files"
date: 2016-03-25
forum: General Help
---

### Post by jrmymllr on 2016-03-25
I have a 240GB SSD using ext4 that's used to hold security camera video when motion is detected.  It's used only for this purpose, and no file is smaller than about 10MB.  The OS is located on another drive.  I'm familiar with "allocation unit size" on NTFS and FAT and would format this drive with a large allocation unit size given the situation, but on extfs, I'm not so sure how this works.  

Currently the drive is essentially full; this is normal since the oldest files are automatically deleted to make room for new ones, and out of 14,655,488 inodes, 14,642,871 are free.  Inode size is 256.  Block size is 4096.  

It's clear I have many more inodes than I will ever need, and at 256 bytes each, that's about 3.5GB of wasted space.  However some research gives me the feeling my calculation is incorrect.  Is each free inode really consuming 256 bytes?

Soon I'll have the opportunity to reformat this drive.  Would increasing block size save space considering the relatively few number of large files stored on it? 

My goal is to recover more storage space if some is otherwise going to waste.

Here's the output of tune2fs -l /dev/sda3 if it helps:


tune2fs 1.42.9 (4-Feb-2014)
Filesystem volume name:   <none>
Last mounted on:          /data
Filesystem UUID:          5113d4d1-9c6c-48a9-a800-86757b5aec3c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              14655488
Block count:              58607360
Reserved block count:     0
Free blocks:              801055
Free inodes:              14642871
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1010
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
RAID stride:              32743
Flex block group size:    16
Filesystem created:       Thu Oct 29 16:35:03 2015
Last mount time:          Sun Mar 20 09:41:38 2016
Last write time:          Sun Mar 20 09:41:38 2016
Mount count:              7
Maximum mount count:      -1
Last checked:             Sat Mar 19 20:31:20 2016
Check interval:           0 (<none>)
Lifetime writes:          1968 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      479f7feb-51d8-41b0-a9f5-f489b74bfd55
Journal backup:           inode blocks

---

### Post by HermanAB on 2016-03-25
Howdy,
You may have more success with using a better video CODEC that will compress the video more, rather than trying to change the file system.  For example, if you are using MPEG2 now, then switch to MPEG4 part 10 (H.264).

---

### Post by jrmymllr on 2016-03-25
> **HermanAB said:**
> Howdy,
You may have more success with using a better video CODEC that will compress the video more, rather than trying to change the file system.  For example, if you are using MPEG2 now, then switch to MPEG4 part 10 (H.264).

I'm not necessarily trying to get more space because I need it, but rather simply wanted to free up space caused by a potentially inefficient filesystem given the unique situation.  I guess what I'm trying to say is things are ok how they are, but I'll take more space if it requires something transparent like a FS change.

Changing the CODEC isn't an option.  What's being recorded is straight off the camera, and is handled by a Video Management System running on the machine.  I'm not so sure my CPU could even handle transcoding all the streams.

---

### Post by jrmymllr on 2016-04-01
I answered my own question.  I did some research and decided to try formatting the drive with XFS.  Free space went from 220GB on ext4 to 224GB on XFS.  That's not a bad gain for "free".

---

