---
title: "Recover deleted partitions on external drive"
date: 2008-05-14
forum: General Help
---

### Post by dirtmaster88 on 2008-05-14
I was trying to diagnose and repair a hard disk so I could clone it with the image on my external drive. I booted into a dos-like tool and saw two partitions that I thought were on the hard disk. Not knowing that it was detecting only my external drive, I deleted both of the partitions. I need these partitions as they are backups for all of our images.

One partitions is NTFS and the other is EXT3. Is there a good tool out there to recover the partition table?


Thanks

---

### Post by cdenley on 2008-05-14
testdisk
```

sudo apt-get install testdisk
sudo testdisk

```

It sounds like you will need to run it from a livecd.

---

