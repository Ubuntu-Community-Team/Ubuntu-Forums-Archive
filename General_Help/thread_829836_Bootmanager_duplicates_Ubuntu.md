---
title: "Bootmanager duplicates Ubuntu"
date: 2008-06-15
forum: General Help
---

### Post by robinzxp on 2008-06-15
Hi, I use bootmanager Ubuntu installed. I recently updated my my Ubuntu to latest and now bootmanager duplicates Ubuntu 3 times. e.g

Ubuntu (Ver)
Ubuntu Recovery
Ubuntu (Ver)
Ubuntu Recovery
Ubuntu (Ver)
Ubuntu Recovery
Other OS's:
Windows

Is there way to get rid of them? I did bit of searching round and some people with similar problems seems to get reply that it is not duplicate but older kernal? Space is issue for me so how can I check if it is keeping older files and how can I delete it? Thanks

---

### Post by 505 on 2008-06-15
Yes, those are older kernels. Usually it is recommended to keep at least two kernels installed. The most recent, and an older one that you know for sure is working.
That being said, you can remove kernels using Synaptic. Search for "linux-image" and unselect the ones you want to remove. It will automatically remove some connected packages. Just make sure you do not remove the kernel you're running now.

---

### Post by drs305 on 2008-06-15
Each time a new kernel is introduced it is added to the grub menu. By far the safest way to edit what you see in the menu during boot is with Startup-Manager. You install it with:
```
sudo aptitude install startupmanager
```

It gives you lots of options for tweaking your boot menu. Here are the details and some instructions of various ways to edit your menu.lst file:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by robinzxp on 2008-06-15
Thanks for replies, I got better understanding of what's going on now. I'm still not so sure about which ones I should remove from Synaptic package manger. Is it just a version of a kernal or any other files??

Ok sorted now no problem, thanks everyone

---

