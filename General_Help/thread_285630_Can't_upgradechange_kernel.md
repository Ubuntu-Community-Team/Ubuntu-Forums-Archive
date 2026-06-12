---
title: "Can't upgrade/change kernel"
date: 2006-10-27
forum: General Help
---

### Post by nj_ub on 2006-10-27
I'm running Ubuntu Dapper Drake 6.06 on my Intel MacBook (non pro).  Everything is almost 100%, but I can't seem to get the other core on my CPU working.

Currently, I'm running the 2.6.15-27-386 kernel.  This kernel doesn't support SMP.  

So, I've tried EVERYTHING trying to update my kernel to a 686-smp version.  Literally everything.

I tried apt-get install linux-686-smp, with all the headers and restricteds.

I've also tried removing /vmlinuz and /initrd.img, and having them linked directly to /boot/[smp versions] using ln -s, but still, when I reboot and run uname -r, it still shows up as 2.6.15-27-386.

I don't know what to do at this point.  Nothing seems to work.  What is the prefered method for changing your kernel?  I can't seem to find any useful information on this anywhere.

Does anyone have any suggestions?  Ubuntu is pretty amazing, and this is my first long term experience with Linux.  Everything would be perfect if I could just get my other core working.

---

