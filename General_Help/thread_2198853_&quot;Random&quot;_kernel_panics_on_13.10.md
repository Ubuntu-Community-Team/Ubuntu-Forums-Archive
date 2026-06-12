---
title: "&quot;Random&quot; kernel panics on 13.10"
date: 2014-01-10
forum: General Help
---

### Post by john_p_peters on 2014-01-10
Hello all,

For the past few months I've been having kernel panics (ie. everything freezes, no mouse visible, indicator lights on keyboard flashing, need to reboot). I'm currently using Ubuntu 13.10, but I've had it with previous versions (don't remember off-hand which one). The problems started once I upgraded from a LTS release (again, don't remember off-hand which one, can look it up if need be). Using a 32-bit machine, if that makes a difference.

What's infuriating about these crashes is how impossible they are to reproduce. Nearly all the time they happen when I'm using Firefox, but then Firefox is my most used application (other than Firefox, Netbeans, and GIMP, I mostly work from the terminal). Currently using Firefox 26.0, but I've had the issue with previous versions. A lot of the time, it crashes when I'm scrolling through some large page. It shouldn't be a memory issue: I've added a memory monitor to my taskbar, and I get crashes when there's still available resources. Besides, I've upgraded my RAM from 2 GB to 4 GB, and that didn't solve anything. I'm pretty sure it's not a Flash issue. I have a bunch of add-ons installed, but I've gotten kernel panics with a clean install too. I _think_ I got them when I switched over to Chrome as well, though that was months back and I don't remember for sure.

I tried installing linux-crashdump, following the instructions here: [https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe) ... however, I can't seem to get the secondary kernel to load. Whenever a kernel panic does happen, after a reboot I go to the GRUB menu, and then the primary kernel gets loaded. So no luck there.

I'm sorry I can't give more details -- again, it's been impossible for me to reproduce the problem. Has anyone come across anything similar?

---

### Post by sanderj on 2014-01-11
I would run memtest for a few hours. It's in the GRUB boot menu.

---

