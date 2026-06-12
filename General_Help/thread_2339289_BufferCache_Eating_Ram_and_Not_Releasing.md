---
title: "Buffer/Cache Eating Ram and Not Releasing"
date: 2016-10-07
forum: General Help
---

### Post by ndstate on 2016-10-07
Hello,

Too much memory is being assigned to buffer/cache and it is not being released properly when my browser/other programs need more ram. This results in my computer freezing. For example right now my memory usage is as follows:

Total 15916
Used 5742
Free 157
Shared 8442
buff/cache 10016
available 1360

It also looks like I have a ton of shared memory usage (8 gigs).

How do I troubleshoot this so my computer stops locking up on me? This only started happening in the past month or so on 16.04. Thanks in advance.

---

### Post by ndstate on 2016-10-10
Any ideas? This is continuing to kill my computer. Thanks

---

### Post by mcduck on 2016-10-10
What makes you think the browser and other programs are asking for more RAM than what they are already using? Buffers and cache are *supposed* to fill any RAM that isn't used by something else.

How does your swap use look like? If the swap isn't filling, then your freezing problem is caused by something else than memory issues. (freezing is more likely to be something esle than RAM issue anyway, memory filling up would cause noticable slowdown far before freezing as your system would start swapping to hard drive. For locking issues I'd start with CPU and graphics drivers first)

---

### Post by ndstate on 2016-10-13
The browser and other programs are asking for ram because the freeze corresponds with opening a new tab/starting a video/etc. When everything starts to slow down/freeze I look and note that the system is reporting that all 16 gigs of ram are being used. It starts with the mouse being slow to respond followed by a complete freeze (most of the time). I look at individual programs and they come no where to adding up to 16 gigs. I have no swap, running on an SSD and have never had problems until the past month or so... after some update. Running out of ram and the buffer/cache not allowing programs to have more ram is the issue. I have tested this at least 20 times and the same issues occur each time.

Thanks for any additional troubleshooting advice.

---

### Post by jerome1232 on 2016-10-13
First, I would use a swap. I know, even if you have a ton of ram. You even create a swap file instead of a partition.

 Have you tried rolling back to a previous kernel and seeing if the problem exists under the previous kernel?

---

