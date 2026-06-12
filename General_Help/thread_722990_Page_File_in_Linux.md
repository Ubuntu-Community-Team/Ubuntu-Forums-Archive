---
title: "Page File in Linux?"
date: 2008-03-13
forum: General Help
---

### Post by jordoex on 2008-03-13
According to [the wikipedia article on paging]("http://en.wikipedia.org/wiki/Swapfile#Swapping_in_Linux"), it's possible to use swapfiles(like windows) in Linux.

So tell me, why hasn't Ubuntu enabled this yet, at least as an option?  I personally would find it useful as I wouldn't need to have a gig of space sitting at the back of my hard drive.

So? Can anyone provide some input?

---

### Post by scragar on 2008-03-13
linux uses swap files, it just avoids them unless it needs them since reading from disk is so much slower than from ram.

---

### Post by jrusso2 on 2008-03-13
A swap file is not as good as a swap partition.  A swap file runs a regular Linux partition whereas a swap partition can run on a light swap file system.

Also a swap file can lead to fragmentation.

If you don't want to use a gig then make your /swap smaller.  It depends on how much physical ram you have.

---

