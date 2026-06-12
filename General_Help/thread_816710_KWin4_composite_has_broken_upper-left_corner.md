---
title: "KWin4 composite has broken upper-left corner"
date: 2008-06-02
forum: General Help
---

### Post by PaladinOfKaos on 2008-06-02
I'm having a strange issue with KDE4 4.0.3 on Hardy.

I have an nvidia GeForce 6600, with the latest drivers available from the Ubuntu repositories.

When I enable compositing, I get a block of pixels in the upper-left corner. If there is no window in that area, the desktop background is shown, otherwise it's simply a black square. An example is at [http://picasaweb.google.com/branan/Screenshots/photo#5207497796806236146]("http://picasaweb.google.com/branan/Screenshots/photo#5207497796806236146")

When an animation (such as a minimizing or maximizing window) is run, the area is refreshed. But if a window is moved around, it simply stays at whatever state it was in after the last animation that was run.

---

### Post by PaladinOfKaos on 2008-06-03
Sorry for the double-post, but it seems to be working now. I restarted X and then enabled compositing, and everything started working fine.

---

