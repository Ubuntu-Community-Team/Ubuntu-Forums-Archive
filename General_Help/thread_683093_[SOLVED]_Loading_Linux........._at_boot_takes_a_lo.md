---
title: "[SOLVED] Loading Linux......... at boot takes a long time"
date: 2008-01-30
forum: General Help
---

### Post by uconnkoala on 2008-01-30
After my bootloader (LILO), the Linux kernel takes forever to load

On the screen I get the

boot: Linux
Loading Linux................................................................................................
................................................................................................................
..................................................................

And the dots continue to progress outward for about 5 minutes, after which my kernel is loaded and the system boots fine.

Hard disk is OK, lots of memory on the system (Thinkpad T40).

At a loss for answers....

---

### Post by danwood76 on 2008-01-30
Is it the standard kernel image?

if the kernel image is custom and contains a lot of added features then it can take longer to load, though I doubt as long as you are saying.
Just a thought.

regards,
Danny

---

### Post by uconnkoala on 2008-01-30
Yep - its the stock Ubuntu image (2.6.20-15-386)

---

### Post by uconnkoala on 2008-01-30
I made some changes to my lilo.conf - and miraculously it worked

Loading the kernel takes about 10 seconds now

I added the following:

```

# lilo.conf

compact
map=/boot/System.map-2.6.20-15-386

```

---

