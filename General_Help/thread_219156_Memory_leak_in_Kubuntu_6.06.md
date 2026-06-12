---
title: "Memory leak in Kubuntu 6.06"
date: 2006-07-19
forum: General Help
---

### Post by tcollogne on 2006-07-19
Hi all,

I am using Kubuntu 6.06 and have trouble with some kind of memory leak.
I have 1 GB RAM and when I look at my free memory it states 10 mb free.

I have monitored this and it seems to keep going up and then starts eating away my swap memory.

When I use the top command there is no application that uses more then 120 mb. One uses 120 mb: amarok.

Does anyone have an idea how I can find out which app is causing this?

Thank you

---

### Post by Hanj on 2006-07-19
This isn't anything wrong, but rather the way Linux is constructed. The Linux kernel is made to take advantage of all RAM that isn't being used by any other process. You can read more about it [here]("http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html")

---

### Post by tcollogne on 2006-07-19
So if I understand it correctly, there is now way of telling how much memory is actually being used? But then I still wonder how it gets to use 1 GB in the first place.

---

### Post by ThrobbingBrain66 on 2006-07-19
Kmenu>System>KInfoCenter>Memory should give you an accurate account of how much memory you have and hows its being used.

---

### Post by Jucato on 2006-07-19
Unlike Windows, Linux uses up the memory space that is available. In allocating memory, top priority goes to applications. If no other applications need RAM, Linux then most the remaining RAM for disk cache so that read/write access will be faster. Once more programs need more RAM than what was initially allocated, Linux frees up the needed space from the disk cache and allocates it to the applications. AFAIK, it will always keep a certain minimum amount of RAM for disk cache, and that it always keeps a certain amount (2MB or more) of RAM unallocated. Once the total of these three (applications, disk cache, and minimal free RAM) exceeds your RAM, then it starts using the swap memory.

You'll know when there's a memory leak if one single program alone uses up more memory than it should. 120MB for Amarok is, IIRC, quite normal.

---

### Post by Hanj on 2006-07-20
> You'll know when there's a memory leak if one single program alone uses up more memory than it should. 120MB for Amarok is, IIRC, quite normal.Probably so. I your programs aren't running unusually slowly, you probably don't have anything to worry about. When it comes to determining the memory usage of individual programs, [this article]("http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html") is quite interesting.

---

