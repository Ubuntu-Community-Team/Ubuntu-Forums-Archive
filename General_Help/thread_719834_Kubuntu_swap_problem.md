---
title: "Kubuntu swap problem"
date: 2008-03-09
forum: General Help
---

### Post by aaron321 on 2008-03-09
I have a problem with my computer, it never uses swap, and gets progressively slower as more stuff is cached into physical memory.
I am running Kubuntu 7.10.
I allocated 8gb into a swap partition, which is located on my raid0 on an nvidia raid controller.
In my /etc/fstab, I have the following line to initiate the swap partition:

/dev/mapper/nvidia_defgceib5 swap sw 0 0

but that doesn't seem to work on boot, so I have to initialize it manually using

swapon /dev/mapper/nvidia_defgceib5

After this, the system sees the swap file but never uses it. Here is a screenshot of ksysguard:

[http://i25.tinypic.com/331ftvt.png](http://i25.tinypic.com/331ftvt.png)

here are the outputs of cat /proc/swaps and cat /proc/meminfo:

$cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/nvidia_defgceib5            partition       8361792 0       -1

$cat /proc/meminfo
MemTotal:      2856276 kB
MemFree:       2161912 kB
Buffers:         25064 kB
Cached:         441308 kB
SwapCached:          0 kB
Active:         358132 kB
Inactive:       261388 kB
HighTotal:     1966016 kB
HighFree:      1353188 kB
LowTotal:       890260 kB
LowFree:        808724 kB
SwapTotal:     8361792 kB
SwapFree:      8361792 kB
Dirty:              20 kB
Writeback:           0 kB
AnonPages:      153148 kB
Mapped:          75896 kB
Slab:            49568 kB
SReclaimable:    37868 kB
SUnreclaim:      11700 kB
PageTables:       1956 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   9789928 kB
Committed_AS:   465532 kB
VmallocTotal:   114680 kB
VmallocUsed:     82736 kB
VmallocChunk:    27636 kB

Any help please?

---

### Post by fjgaude on 2008-03-09
Well, AFAIK, swap is only used when appication needs memory, not nice, i.e., not cache.

The only thing I see wrong in your fstab is:


```
/dev/mapper/nvidia_defgceib5 **none** swap sw 0 0
```

You left the "none" out.

Your computer is slowing donw, maybe, for other reasons than swap.

---

### Post by soldats on 2008-03-09
How mych memory do you have? If I recall correctly, the swap should be twice the size of the RAM. I've heard that if it is significantly more it doesnt recognize it or use it. 8Gb seems like a lot. It may have something to do with it being on Raid.

Because at least for me a year ago i mistakenly made the swap 3 times the size it should have been and it was never used. So I adjusted it accordingly and it was fine from then on out.

---

