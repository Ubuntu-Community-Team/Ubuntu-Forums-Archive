---
title: "kernel panic upon trying to start ubuntu 6.10 from CD"
date: 2007-03-18
forum: General Help
---

### Post by CoRnJuLiOx on 2007-03-18
[http://i6.photobucket.com/albums/y229/teh_sAbEr/CIMG2029.jpg](http://i6.photobucket.com/albums/y229/teh_sAbEr/CIMG2029.jpg)
[http://i6.photobucket.com/albums/y229/teh_sAbEr/CIMG2030.jpg](http://i6.photobucket.com/albums/y229/teh_sAbEr/CIMG2030.jpg)

Ok, heres the thing. I just burned an Ubuntu 6.10 CD, and when I tried to 'start or install ubuntu' from the menu, it gives me this (see pic above). 
- I checked the md5sum on the ISO, everything is fine.
- I've already tried adding 'acpi=off', 'noacpi', 'noapic', and 'nolapic' to the boot options with no luck.
- I burned the CD at the slowest possible setting to avoid a bad burn. 
- I've tried the CD on another PC, and what happens is that it doesn't kernel panic, but it doesn't load. It just sits there at the XP-like loading screen, and not loading.

My current specs:
- Pentium 4, 1.7ghz socket 478
- VIA P4MA Pro motherboard
- 256 MB RAM
- one 40 GB HD, XP install (not working)
- one 30 GB HD, Ubuntu 6.06 (currently using this one right now)
- one CD burner
- 32 MB nvidia Riva TNT2 video card

Does anyone have any ideas as to what this is and how to fix it?

---

### Post by Kaah on 2007-03-23
I have the same problem and i can't boot with the server cd.
Memtest has been running for 9 hours, no problem.

---

### Post by jdong on 2007-04-07
Could this be an instance of bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63134](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63134)

Try booting with "acpi=force irqpoll"?

---

