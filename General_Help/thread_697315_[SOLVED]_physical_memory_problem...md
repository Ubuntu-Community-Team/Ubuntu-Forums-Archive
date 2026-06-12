---
title: "[SOLVED] physical memory problem.."
date: 2008-02-15
forum: General Help
---

### Post by Mia_tech on 2008-02-15
I just installed kubuntu 7.10 on my desktop and when I login everything seems ok, but I check my pc an hour later and find physical memory usage all the way up hugging all my memory, I ran top and I don't see a relevant process using up a lot of memory and I dont' have many apps running only firefox, xterm, konqueror,and superkaramba..

has this happened to anyone...help

---

### Post by mbsullivan on 2008-02-15
Hi!

Could you give the output of:

```
free -m
```

as well as

```
cat /proc/meminfo
```

and

```
/proc/swaps
```

This may not be a problem in the first place... One deceptive thing is that writes to the harddrive are cached in memory and counted as "used memory" in many memory reporting places. This space, although technically "allocated", should not be counted as program memory, as such.  These buffers and caches will often fill just about all of your available memory, but if you need any of it they will be flushed and the memory made available.

So... it could be that some program is logging a lot of data or something, and these harddrive writes are simply residing in free memory. We'll see what the numbers say.

Cheers! Get back to me with that.
Mike

---

### Post by kerry_s on 2008-02-15
in linux unused memory is wasted memory. applications you've used stay in memory until the space is needed, this is to make things faster, ram is faster than hd, so if you launch the same application again it will just load it from ram. something like that :)

---

### Post by Mia_tech on 2008-02-15
> **mbsullivan said:**
> Hi!

Could you give the output of:

```
free -m
```

as well as

```
cat /proc/meminfo
```

and

```
/proc/swaps
```

This may not be a problem in the first place... One deceptive thing is that writes to the harddrive are cached in memory and counted as "used memory" in many memory reporting places. This space, although technically "allocated", should not be counted as program memory, as such.  These buffers and caches will often fill just about all of your available memory, but if you need any of it they will be flushed and the memory made available.

So... it could be that some program is logging a lot of data or something, and these harddrive writes are simply residing in free memory. We'll see what the numbers say.

Cheers! Get back to me with that.
Mike

if that's true, I guess linux handles memory different than windows.. anyway thanks for the info and here's the output you requested.. could you dissected for me? thanks

..```
jorge@kubuntu-box:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1264       1195         69          0         18        796
-/+ buffers/cache:        380        884
Swap:         1929         31       1897
jorge@kubuntu-box:~$
jorge@kubuntu-box:~$
jorge@kubuntu-box:~$ cat /proc/meminfo
MemTotal:      1295020 kB
MemFree:         70660 kB
Buffers:         19376 kB
Cached:         815196 kB
SwapCached:      32528 kB
Active:         575460 kB
Inactive:       502064 kB
HighTotal:      392448 kB
HighFree:        17860 kB
LowTotal:       902572 kB
LowFree:         52800 kB
SwapTotal:     1975952 kB
SwapFree:      1943424 kB
Dirty:             124 kB
Writeback:           0 kB
AnonPages:      210464 kB
Mapped:          71428 kB
Slab:           126212 kB
SReclaimable:   114956 kB
SUnreclaim:      11256 kB
PageTables:       1936 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2623460 kB
Committed_AS:   407848 kB
VmallocTotal:   114680 kB
VmallocUsed:      7928 kB
VmallocChunk:   105460 kB
jorge@kubuntu-box:~$
jorge@kubuntu-box:~$
jorge@kubuntu-box:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda2                               partition       1975952 32528   -1
jorge@kubuntu-box:~$

```

---

### Post by kerry_s on 2008-02-15
looks alright to me, most of your stuff is buffered.

the only thing i would recommend, is maybe adjust your swappiness, you have what, more than a gig of ram. so you could adjust your swappiness to only use swap when it really needs it, it will prevent any lagging due to swapping.

sudo kwrite /etc/sysctl.conf

vm.swappiness=10

higher numbers for more swap use, kde has a lot of parts that run and they always stay in ram, so the desktop can feel quick. this may sometimes lead to other applications that aren't part of kde feeling slower. kde is qt based, using qt based apps will work better on kde, for example: instead of firefox, which is gtk based, you might want to try opera, which is qt based.

---

### Post by mbsullivan on 2008-02-15
Yep, your memory's not filling up... just getting full of buffers and caches (which don't really "matter").

You can (easily) tell how much memory is used by looking at the following line of free -m:

```
-/+ buffers/cache:        380        884
```

This means that you're using 380/884 MB for running programs. The rest is used by buffers and caches, which can be seen by:

```
Buffers:         19376 kB
Cached:         815196 kB
```

As for an explanation, buffers are allocated by various processes to read in data, store intermediary results, etc. A large amount of the time, buffers are "file buffers", which store part of a program's output to the disk until it is written. Cache is typically frequently requested disk I/O. If multiple processes are accessing the same file, or if a file is accessed repeatedly, caching the file to RAM will speed up file access drastically. 

This is all well and good, so long as you're not using the majority of your memory for programs (as you aren't)... As soon as your cache and buffer memory is needed for real programs, the kernel needs to make a decision. In order to free this memory, the kernel can either remove the oldest entries in the disk cache (which eliminates them altogether, though a disk access will have to "start all over again" if something is needed from the harddrive). Or, the kernel may swap some less used memory to the swap partition on disk, which consumes more time (for the write), but can save some time for a repeated access. The balance between ditching old memory and swapping it to disk is controlled (as kerry_s said) by vm.swappiness. With your amount of memory, less swapping will probably speed up the system, so I agree that a swappiness of 10 may help you. An added benefit (for laptops) is that a lower swappiness will reduce the sporatic harddrive writes that accompany writing to the swap file, which allows your harddrive to spin down (sit idle) more often, reducing battery usage. 

But, in summation... you're okay! Nothing's wrong!
Mike

---

