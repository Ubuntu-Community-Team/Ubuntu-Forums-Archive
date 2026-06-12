---
title: "Confusion about contradicting info on memory usage"
date: 2015-01-15
forum: General Help
---

### Post by john294 on 2015-01-15
Hi,
some memory consuming process on my computer didn't finish, so I aborted it and checked the currently available memory.
using "free -g" I see that almost all of my 78 Gb RAM seems to have been allocated:
```
free -g
             total       used       free     shared    buffers     cached
Mem:            78         77          0          0          0         70
-/+ buffers/cache:          6         72
Swap:           14          0         14
```

so the 'Mem:' section shows that all memory is in use, while the '-/+ buffers/cache' section shows almost all memory as free.

I get similar info from top:
```
top - 10:31:26 up 10 days,  1:02, 14 users,  load average: 1.03, 0.83, 0.73
Tasks: 533 total,   2 running, 528 sleeping,   0 stopped,   3 zombie
%Cpu(s):  3.0 us,  0.2 sy,  0.0 ni, 96.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  82434608 total, 81723360 used,   711244 free,   486336 buffers
KiB Swap: 15624188 total,        0 used, 15624188 free. 74369024 cached Mem
```

however,
using gnome-system-monitor only about 6 Gb seem to be in use (corresponding to the '-/+ buffers/cache' column).

So what does it signify that "free" and "top" show most of my memory as "used"? Is the memory being reserved for some processes that are just currently sleeping?

---

### Post by Holger_Gehrke on 2015-01-15
The output of 'free' is misleading to people not used to it. The first line includes all uses as disk cache. That memory is available for programs to use. That's why the second line reports 72 GB available.

RAM not used is wasted, as they say.

---

### Post by Yellow Pasque on 2015-01-15
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by john294 on 2015-01-15
Thanks a lot!
 So, as far as I understand it from the link [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") posted, the cached memory is storing data from files that were read into memory and MIGHT be needed again later. This can speed up processes because the data would not have to be re-read into memory from the disk again when needed. But as soon as memory is needed by another process this cache is immediately overwritten and the memory is available for the other process.
That's not so complicated as I thought! Thanks for the cool link!

---

