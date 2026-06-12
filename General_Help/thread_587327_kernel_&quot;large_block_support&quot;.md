---
title: "kernel &quot;large block support&quot;?"
date: 2007-10-22
forum: General Help
---

### Post by IndieRockSteve on 2007-10-22
my current debian install has a kernel that does not seem to have large block support enabled which it looks like I need to expand my RAID 5 array past 2TB. I'm wondering i the Ubuntu kernel is compiled with this enabled?

also, its a software RAID array, so I assume booting off the Ubuntu cd should let me finish reshaping the array even if its under a different kernel?


thanks!!

---

### Post by fjgaude on 2007-10-22
All the Ubuntu kernels, including the latest, use 1K blocks which leaves us with a 2TB filesystem size and 16 GB file size, maximum.

Yes, any kernel should permit the array to assemble, at least that's Linux MD controlled by MDADM.

---

### Post by IndieRockSteve on 2007-10-23
so if I want to create a 2.5TB raid array how would i go about that?

---

### Post by fjgaude on 2007-10-24
Well, this is beyond me but I think you need to use a filesystem other than the standard ext3, something like jfs or xfs. I know nothing of these filesystems. Have google to find out the limits of the various filesystems...

---

### Post by anaconda on 2007-10-24
ext3 doesnt have a 2TB limitation.

Maybe it has with 1K block size, but you can also select a bigger block size!

with 4k blocksize the max size is 8TB


[http://lwn.net/Articles/187321/](http://lwn.net/Articles/187321/)

You can set the blocksize when you format your partition with mke2fs -j -b 4096 /dev/XXX

---

### Post by fjgaude on 2007-10-24
> **anaconda said:**
> ext3 doesnt have a 2TB limitation.

Maybe it has with 1K block size, but you can also select a bigger block size!

with 4k blocksize the max size is 8TB

[http://lwn.net/Articles/187321/](http://lwn.net/Articles/187321/)

You can set the blocksize when you format your partition with mke2fs -j -b 4096 /dev/XXX

Great, thanks for the information... likely many of us will be having to use the extents soon.

---

### Post by atlfalcons866 on 2007-10-26
block sizes for ext3 are default to 4094 which is 4KB block sizes.

Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          c9eb221a-b135-431c-bb99-8c200e02e258
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype n
eeds_recovery sparse_super large_file
Filesystem flags:         signed directory hash
Default mount options:    journal_data_writeback
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1465920
Block count:              2929846
Reserved block count:     146492
Free blocks:              1742599
Free inodes:              1222732
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      715
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16288
Inode blocks per group:   509
Filesystem created:       Wed Oct 24 16:17:16 2007
Last mount time:          Fri Oct 26 07:19:28 2007
Last write time:          Fri Oct 26 07:19:28 2007
Mount count:              5
Maximum mount count:      75
Last checked:             Thu Oct 25 14:50:26 2007
Check interval:           15552000 (6 months)
Next check after:         Tue Apr 22 14:50:26 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       814601
Default directory hash:   tea
Directory Hash Seed:      0315b4d2-7191-4272-a7ac-16a0af94cd3e
Journal backup:           inode blocks

Where it says fragment and block size that is 4KB blocks

---

### Post by fjgaude on 2007-10-26
Say, what command did you use to get your printout?

---

### Post by atlfalcons866 on 2007-10-27
sudo tune2fs -l /dev/sda1

---

### Post by fjgaude on 2007-10-28
Thanks, and this is good news... to have 8TB capacity, default. Learn something new every day.

---

