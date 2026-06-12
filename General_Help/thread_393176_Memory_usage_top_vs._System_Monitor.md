---
title: "Memory usage: top vs. System Monitor"
date: 2007-03-25
forum: General Help
---

### Post by MeneK on 2007-03-25
Hello,
Why the System Monitor and top (on a terminal) give different memory usage results? Which one is the correct?

For example, just now, top gives:

```

**Mem:   2076100k total,   552704k used,  1523396k free,    11416k buffers**
Swap:  3148732k total,        0k used,  3148732k free,   247856k cached
```

while, the System Monitor gives:

**User memory: 286.0 MB of 2 GB 14.1%**
Swap memory: 0 bytes of 3 GB 0.0%

Thanks!

---

### Post by SuSUntu on 2007-03-25
From the 'htop' FAQ ('htop' is an alternative to 'top'):

> 
**The memory meter in htop says a low number, such as 9%, when top shows something like 90%! (Or: the MEM% number is low, but the bar looks almost full. What's going on?)**

*The number showed by the memory meter is the total memory used by processes. The additional available memory is used by the Linux kernel for buffering and disk cache, so in total almost the entire memory is in use by the kernel.* I believe the number displayed by htop is a more meaningful metric of resources used: the number corresponds to the green bars; the blue and brown bars correspond to buffers and cache, respectively (as explained in the Help screen accessible through the F1 key). Numeric data about these is also available when configuring the memory meter to display as text (in the Setup screen, F2).


So, in a nutshell:

- 'top' is showing memory actually in use by apps + buffers + cache; Sys Mon is only showing memory used by apps (though you can set Sys Mon panel applets to show the various types)

I posted this as relevant since my 'htop' memory output matches System Monitor, but of course, per the above info and our own personal experiences, top does not match. Give 'htop' a try, if you like; it's in the repos.

----------

Examples:

- top =  Mem:   1035480k total,  1013316k used,    22164k free,   449908k buffers

- htop =  Mem: 1011M     used: 288M      buffers: 439M       cache: 259M

- System Monitor =  User Memory: 288.3 MiB of 1011.2 Mib

---

### Post by MeneK on 2007-03-27
Thanks!

---

