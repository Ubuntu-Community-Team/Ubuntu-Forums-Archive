---
title: "Gutsy xorg-intel video driver broken resuming from suspend?"
date: 2007-10-09
forum: General Help
---

### Post by rockyrobin on 2007-10-09
In the last few days following a kernel upgrade via update manager I have found that upon resuming from suspend the desktop display is showing up as torn, in that when I try to scroll in the likes of Firefox only parts of the page scroll and the page becomes torn horizontally.
Upon rebooting the display is fine but breaks when suspend is used again.

My video is Intel integrated 855 chipset.

Is anyone else noticing this?

RR

---

### Post by jabberwork on 2008-01-22
Hi! I had a very similar issue with my intel adapter, but my pages were corrupted by thin stripes as I was scrolling them up. The problem has gone after installing this drivers (from the developer's branch): [http://people.ubuntu.com/~bryce/Testing/bug127101/xserver-xorg-video-intel_2.1.1~git20071004-0ubuntu1_i386.deb](http://people.ubuntu.com/~bryce/Testing/bug127101/xserver-xorg-video-intel_2.1.1~git20071004-0ubuntu1_i386.deb)

Sergey.

---

