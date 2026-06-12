---
title: "Cannot mount external drive."
date: 2007-12-13
forum: General Help
---

### Post by schreckles on 2007-12-13
I woke up this morning to find out that my external had somehow unmounted, and for whatever reason, I now can't get it to mount out all. Here's the basic scenario:

it's located at dev/sda1/ and up until today, it auto-mounted just fine under /media/external/ so I know hal/my fstab isn't the problem in this case. It's ext3 filesystem. The problem shows itself when I run ```
dmesg | tail
```

[  135.048000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  135.048000] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[  135.048000] sd 0:0:0:0: [sda] Write Protect is off
[  135.048000] sd 0:0:0:0: [sda] Mode Sense: 17 00 00 00
[  135.048000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  135.048000]  sda: sda1
[  135.068000] sd 0:0:0:0: [sda] Attached SCSI disk
[  135.084000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  136.332000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 128 not in group (block 368520712)!
[  136.340000] EXT3-fs: group descriptors corrupted!

So am I entirely screwed out of the blue all of a sudden, or is there something I can do to fix this and recover my data?

---

### Post by schreckles on 2007-12-13
Well, I've actually, as per usual, fixed the problem within an hour of posting it and now feel dumb. Anyway, for anyone that runs into this problem, first try this:

```
fsck.ext3 -y /dev/sda1
```

(obviously, just use your device's location in place of sda1 for your individual case.) What this does is tried to rebuild/repair the existing journal on that partition.

and if that doesn't work, try to rebuild a new journal using 

```
tune2fs -j /dev/sda1
```

obviously for both of these you'll want to use sudo, unless you're logged in as root.

---

