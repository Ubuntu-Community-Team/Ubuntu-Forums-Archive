---
title: "Dell 11 Ubuntu MATE touchpad reacts to pad of finger, but not tip + other issues"
date: 2015-07-04
forum: General Help
---

### Post by Jonathan_Cox on 2015-07-04
I just installed Ubuntu 14.04 MATE on a Dell 11 Chromebook, and since booting for the first time, the touchpad has stopped responding unless I use the pad of my finger. 

Before wiping the SSD and installing MATE I had been running Ubuntu XFCE alongside Chrome OS using Chrouton, and the touchpad worked like a dream. But since installing MATE I've been experiencing the weirdest issue. The touchpad reacts to pad of my finger - where the fingerprint is - but not the tip: If I use the pad of my finger to move the cursor, it works OK. But if I use the tip of my finger (the part you usually use to tap a touchscreen, and the part you normally use to move the cursor with a touchpad), the cursor won't budge. And even when I use the pad of my finger, the cursor doesn't always register the contact. 

It seems that more finger surface has to be in contact with the trackpad for it to register. I've tried every combination of acceleration, speed, and sensitivity in the mouse settings and in `gpointed`, turned off "disable touchpad while typing," etc, but nothing works. According to `xinput list` it's a Cypress APA Trackpad.  

EDIT: I tried adding a regular physical mouse, and it works fine. But I don't think my problems are caused by a hardware malfunction, because the touchpad was working fine yesterday when I used Chrome OS and XFCE.

---

