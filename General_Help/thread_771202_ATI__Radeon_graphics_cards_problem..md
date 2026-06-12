---
title: "ATI  Radeon graphics cards problem."
date: 2008-04-27
forum: General Help
---

### Post by drbongo on 2008-04-27
Upgraded to Hardy hoping they had fixed the terrible problems I had with my ATI video cards (Radeon 7000/9250)with Gutsy. There is an improvement - it will now boot in safe mode, but if I try to change the resolution from 1280x1024 the screen gets seriously messed up. My Nvidia card would also only
 work in safe mode, but was fine once I installed the Nvidia driver. Anyone else having similar problems?

drbongo

---

### Post by Archimedes0212 on 2008-07-25
I had a somewhat similar problem.  Hardy was telling me I was using Mesa even though I had installed fglrx.  Turns out the fix to this problem to get rid of mesa was to just uninstall xserver-xgl and use the gnome session without xgl.

---

