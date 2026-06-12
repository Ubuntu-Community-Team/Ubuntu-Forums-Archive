---
title: "[SOLVED] Monitoring memory usage in KDE"
date: 2008-06-24
forum: General Help
---

### Post by achelis on 2008-06-24
Hi

I've been using KDE over the last few days and generally like it.
Just recently though I noticed in KDE System Guard that I use:

```

Memory: 3,475,552 KB used, 155,504 KB free
Swap: 38,268 KB used, 11,841,760 free

```

and I want to find out what program is using so much memory.. is there a tool for this (I imagine KDE System Guard does, but I haven't been able to figure out how to see individual programs memory usage..)

Thanks :)

---

### Post by Greyed on 2008-06-24
It is probably nothing.

This page has a good, non-distribution specific answer on why this is the case:
[http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html](http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html)

KSysGuard can do it, there should be another tab showing you which programs are running and how much they are using.  However, the quick way to check if it is programs vs. cache is to run the following in a Konsole window:

```

free

```

You'll get something like this:

```

             total       used       free     shared    buffers     cached
Mem:        514652     464616      50036          0     139640     140396
-/+ buffers/cache:     184580     330072                                 
Swap:      2040244        104    2040140                                 

```

The line you want to pay attention to is -/+ buffers/cache.  If you have a ton of memory free there and not the line above then it is your cache using up resources and that's a good thing.

---

### Post by achelis on 2008-06-24
Ah thanks - it is. 

```

             total       used       free     shared    buffers     cached
Mem:       3631056    3423912     207144          0      15316    2898596
-/+ buffers/cache:     510000    3121056
Swap:     11880028      38268   11841760

```

I just got worried when I heard the hard disk start using the swap disk - but it has stopped now and everything is running smoothly again :)

---

### Post by Greyed on 2008-06-24
You're welcome.  Anything for Belkar on a rubbery ducky!  ;)

---

