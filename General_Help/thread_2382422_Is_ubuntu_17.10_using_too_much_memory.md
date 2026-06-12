---
title: "Is ubuntu 17.10 using too much memory?"
date: 2018-01-13
forum: General Help
---

### Post by mamboze on 2018-01-13
I've recently installed ubuntu 17.10. With Firefox Quantum running and only one tab (this site), the System Monitor shows memory usage at 2.1 GiB (58.7%) of 3.7 GiB. Without the browser running, the usage is 1.9 Gib (52.3%). This seems to be a crazy amount for the OS and one browser to need.

I checked this out online and came on this site  [http://www.ubuntubuzz.com/2017/10/reducing-ubuntu-1710-memory-usage-down-to-600mib.html](http://www.ubuntubuzz.com/2017/10/reducing-ubuntu-1710-memory-usage-down-to-600mib.html)

I've tried deleting some of the entries listed in System Monitor>Processes and recommended by this site but ubuntu crashed and had to be rebooted.

Any help would be most welcome TIA

---

### Post by cruzer001 on 2018-01-13
Interesting article, I may have to try some of that on 16.04.

How much of your ram is going for cache?  Cache can eat all available ram, but the system can take it back when needed.

Easy way to find out is:

```
free -m
```

The breakdown can be found here:

```
cat /proc/meminfo
```

I'm not running 17.10, but thought that may help you in your search.

Good luck

---

### Post by mamboze on 2018-01-13
Hi,

Thanks for your comments. cat /proc/meminfo yielded this output
```

roy@medea:~$ cat /proc/meminfo
MemTotal:        3834144 kB
MemFree:          175512 kB
MemAvailable:    1177784 kB
Buffers:           79832 kB
**Cached:          1078648 kB**
SwapCached:            0 kB
Active:          2389656 kB
Inactive:        1030212 kB
Active(anon):    1807272 kB
Inactive(anon):   439344 kB
Active(file):     582384 kB
Inactive(file):   590868 kB
Unevictable:          56 kB
Mlocked:              56 kB
SwapTotal:       1949692 kB
SwapFree:        1949692 kB
Dirty:                16 kB
Writeback:             0 kB
AnonPages:       2261452 kB
Mapped:           553380 kB
Shmem:            352732 kB
Slab:             117176 kB
SReclaimable:      61648 kB
SUnreclaim:        55528 kB
KernelStack:       13632 kB
PageTables:        57676 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3866764 kB
Committed_AS:    8718424 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      146388 kB
DirectMap2M:     3840000 kB

```

The cache (in bold) is around 10 GIB. This seems very large, can it be reduced?

---

### Post by Holger_Gehrke on 2018-01-13
Let's put a few commas in there for readability, ok ?
> **mamboze said:**
> 
[...]
```

**Cached:          1,078,648 kB**

```
[...]
The cache (in bold) is around 10 GIB. This seems very large, can it be reduced?

So, no it's not 10 GB, it's 1 GB. And since it's disk cache and will be automatically reduced if there's a better use for the RAM, why would you want to reduce it manually ? Unused RAM just sits there consuming power and not doing a thing for you, cache helps to speed up work.

Holger

---

