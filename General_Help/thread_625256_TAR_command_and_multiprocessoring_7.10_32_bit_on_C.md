---
title: "TAR command and multiprocessoring? 7.10 32 bit on C2D"
date: 2007-11-27
forum: General Help
---

### Post by minksj on 2007-11-27
Hi, I'm probably asking question wrongly, yet this is what I'd need:

when I do a complete backup with tar, one of my cores is always idling. Is there a way to employ both? I don't think the question is particular to tar, though. Could you please share your knowledge on that or redirect me?


Ubuntu Gutsy  7.10 32 bit on C2D 7100

Thanks a lot!  Jakub

---

### Post by bettlebrox on 2007-11-27
Tar probably isn't multi-threaded so won't run on 2 core at once. But, if you break your backup into multiple tar file then you could run multiple instances of tar to take advantage of the multiple core.

Or, just play some games and keep the other core busy! ;)

---

### Post by minksj on 2007-11-27
Sounds good, can do :-). So this is just question of linux newbie - is there likely going to be a multithreaded version? I'd presume tarring/compressing is one of the most obvious tasks where you'd want all your cores to get warm...

---

### Post by bettlebrox on 2007-11-28
I'd guess there probably won't be a multi-threaded version in the near future (correct me if I'm work). I'd also imagine a multi-threaded version could be hard to implement to avoid threads stomping on each other!

---

