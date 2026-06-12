---
title: "Expanding Computer Memory with a USB Flash Drive's Memory"
date: 2018-11-25
forum: General Help
---

### Post by nathanstrain on 2018-11-25
I'm just wondering, am I able to expand my computer's memory with the memory on a USB Flash Drive (or any other types of flash/hard drives)? If yes, then how are you able to do it?

---

### Post by TheFu on 2018-11-25
People are often confused about "memory."

There are 2 major sorts of memory - RAM which is very, very, fast and storage which is very, very, slow.  USB Flash storage is often the slowest type of storage memory possible.

All modern OSes have something called "virtual memory", which lets the OS add to the RAM using storage.  That is what a swap partition is all about.  You can put swap onto any storage medium, but it is best to use the fastest storage possible. USB flash storage would be the last choice since it is often 5x slower than a slow spinning HDD. Plus, virtual memory will cause many more read/write cycles, which will burn through flash memory cycles in less than a year. On an SSD system I had, the SSD was toast in about 18 months, but it was a cheap SSD, not one of the enterprise versions.

You can monitor the different types of memory use using the "free" command.  Try 
```
free -hm
```
There are other commands like vmstat and top.

---

