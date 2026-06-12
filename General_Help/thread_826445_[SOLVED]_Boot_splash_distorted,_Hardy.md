---
title: "[SOLVED] Boot splash distorted, Hardy"
date: 2008-06-11
forum: General Help
---

### Post by wsmoser2004 on 2008-06-11
I recently upgraded to Hardy, and one thing I noticed was that my boot splash screen is now somewhat distorted.  It's kind of shifted to the left, and it looks like the wrong resolution.

I checked /etc/usplash.conf, and that has the right resolution.  (I have a widescreen laptop, 1280x800.)  Also possibly related, my virtual terminals didn't work in Gutsy.  Well, I should say they worked, but I couldn't see what I was typing.  Anyway, they now work in Hardy.  I don't know if that is related.  I'd much rather have virtual terminals than a normal-looking splash screen though...

I have an ATI Mobility Radeon 9200, which is pretty much a pain in Linux.  I wouldn't be surprised if that's the problem...

Any thoughts?

---

### Post by wsmoser2004 on 2008-06-12
Never fails, I post on here, and I find the solution a day later. :)  I took out the "vga=791" on the end of the GRUB boot line, and somehow Linux figures everything else out.  *shrugs*

---

