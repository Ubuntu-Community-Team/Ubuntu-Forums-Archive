---
title: "Swap Space Bigger Than Partition?"
date: 2007-04-25
forum: General Help
---

### Post by wsmoser2004 on 2007-04-25
Supposedly the partition where my swap space is located is 300-ish MB or so.  It is on an extended partition or whatever it is called (logical?)  However, when I do a 'free -m' from the command line, it reports that my swap space is ~720 MB!  How can this be?  Here is the output from fdisk -l and free -m, if it's of any use:

```

Laptop: sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3844    30875008+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3845        4818     7823655   83  Linux
/dev/sda3            4819        4864      369495    5  Extended
/dev/sda5            4819        4864      369463+  82  Linux swap / Solaris

```

```

Laptop: free -m
             total       used       free     shared    buffers     cached
Mem:           503        495          8          0         14        261
-/+ buffers/cache:        219        284
Swap:          721          0        721


```

---

### Post by rmemm on 2007-04-25
You might query swap space with:

swapon -s

Or alternatively:

cat /proc/swaps

This should list everything and where it came from.

Rob

---

### Post by wsmoser2004 on 2007-04-26
OK, I tested that out.  Here's what I get:

```

Laptop: cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       369452  4       -1
/dev/mapper/sda5                        partition       369452  0       -2

```

Does this mean the swap space is being counted twice?  Or do I magically have a new partition? :)

By the way, I might point out that I just upgraded to Feisty a few days ago...so maybe that could have something to do with this...

---

### Post by rmemm on 2007-04-26
Seems strange.  I personally don't think they should both be listed -- but I don't know anything about the mapper device -- so I'm not certain what it means.

I did a little search regarding /dev/mapper -- they were talking about encrypted swap files.  Could this have something to do with that some how?

Rob

---

### Post by wsmoser2004 on 2007-04-28
Well, I suppose it COULD have something to do with it...although I've never specifically set anything up for an encrypted swap space.  

I see two other posts here: [http://ubuntuforums.org/showthread.php?t=400203&highlight=mapper+device]("http://ubuntuforums.org/showthread.php?t=400203&highlight=mapper+device") and here: [http://ubuntuforums.org/showthread.php?t=392096]("http://ubuntuforums.org/showthread.php?t=392096").  I don't really see a solution to the problem other than that "swapoff" thing...but I'd rather fix the problem rather than work around it.

I did have a problem with my swap space after the upgrade to edgy.  My laptop tried to hibernate once when the battery died, and somehow it corrupted my swap space.  Then, I had to do some funny things to get it to recognize the swap space again.  Could this have something to do with it?

---

