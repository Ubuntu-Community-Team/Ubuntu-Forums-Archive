---
title: "Software update knocked out my wireless"
date: 2006-07-12
forum: General Help
---

### Post by macktheknife on 2006-07-12
i did a software update last night and it knocked out my Dlink wireless card.  It's not detecting it and i don't know if there is a way to manually add it.  I can't remember the 2 programs i updated...i know one was automatix and the other one was linux-? (can't remember that, that is why it has a "?")

---

### Post by Dr. Nick on 2006-07-13
The linux- sounds like the kernel which would explain the wireless drop.

were you using ndiswrapper before? a native kernel module for wireless would conflict and cause your problem

If it was your kernel you updated then restart and look at the grub screen, pick the old kernel (probably 3rd from top) and see if wireless works then.

---

### Post by macktheknife on 2006-07-14
nope never used ndiswrapper...but i did go to the other kernel on the grub screen and got it to work..now it works fine.  don't ask me how i got it, cuz i still don't know yet.  Thanks

---

