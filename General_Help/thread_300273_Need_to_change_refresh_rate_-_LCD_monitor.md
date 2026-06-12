---
title: "Need to change refresh rate - LCD monitor"
date: 2006-11-15
forum: General Help
---

### Post by KedarWolf on 2006-11-15
Hi,

I have an Aopen F2925 19 inch LCD monitor. Most of the info found online suggests it supports a 75 hz refresh rate.

I want to run it at 1024x768 @ 75 hz.

I tried changing the HoriSync to 30-75 and the VertRefresh to 50-85 in the xorg.conf file under the the Monitor section but when i restarted the xserver, it said on the Apen monitor 'out of range'

I had made a backup of the xorg.conf file and went to the backup to get the desktop working again but any advice on how to change the refresh rate would be appreciated.

I setup another PC with an 85 hz refesh rate the same way with HorizSync 30-85 and VertRefresh 50-120 and it worked fine at 85 hz.

Thank you in advance,

Peace,

KedarWolf 8)

---

### Post by emuman on 2006-11-15
LCDs doesn't flicker at any refresh rate. You have no advantage when running @75 hz instead of @60 hz. LCDs should be used at their native resolution. Normally 19 inch displays have a resolution of 1280x1024. Smaller resolution have to be scaled and the result is a blurred output.

---

### Post by KedarWolf on 2006-11-15
Thank you for your help. I'll check on the Aopen site to find the optimal resolution (which is likely as you said) and will change it asap. :D

---

