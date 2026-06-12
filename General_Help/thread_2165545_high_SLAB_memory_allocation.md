---
title: "high SLAB memory allocation"
date: 2013-08-05
forum: General Help
---

### Post by DXKhTkJ on 2013-08-05
I have a VM which is seems low on memory, and when looking into it I seem to be pointed towards the kernel's SLAB allocation.  I understand cache, and used memory is useful.  I don't believe this is just memory in cache.

Free indicates that most of my memory is used, even when considering cache/buffers.

```

free -m
                  total       used       free     shared    buffers     cached
Mem:           995        839        155          0         10        108
-/+ buffers/cache:        720        274
Swap:            0          0          0

```

So looking to see what is using the memory I ran top/atop and none of my processes are actually USING that much ram.  Maybe a couple hundred megs all said and done.  I did notice that in atop, my SLAB allocation is very high.  I checked meminfo and the SLAB is indeed very large AND most of it is not reclaimable.  

```
cat /proc/meminfo
Slab:             584436 kB
SReclaimable:      10164 kB
SUnreclaim:       574272 kB

```

Comparing this to another 12.0.4 Ubuntu system running similar services with a SLAB that is very small and mostly reclaimable.

```
cat /proc/memstat
Slab:              39580 kB
SReclaimable:      26980 kB
SUnreclaim:        12600 kB

```

The system in question is on the order of 45 TIMES more Slab in use (SUnreclaim).  If this were an application I would call that a probable memory leak as those numbers are vastly different.

The system which I am seeing this problem on is: 3.2.0-36-generic #57-Ubuntu SMP
while the comparison system which seems ok is: 3.2.0-23-generic #36-Ubuntu SMP

I really don't want to have to reboot my box to try and fix this, but it is using over half the ram given to the VM.  I know I can add more ram to a VM, but this doesn't look like it should be happening and I hate to band-aid it.

It is also concerning that the "newer" machine is the one with the problem.

P.S. sorry about the user name, apparently I can't edit my profile until I have 25 posts... so I get this random one until such a time that I can change it.

---

