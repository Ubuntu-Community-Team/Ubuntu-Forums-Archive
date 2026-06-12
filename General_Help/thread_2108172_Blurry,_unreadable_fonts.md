---
title: "Blurry, unreadable fonts"
date: 2013-01-23
forum: General Help
---

### Post by AussieGuy on 2013-01-23
I'm running KDE 4.8.4 on Ubuntu 12.04.1 LTS. I have an occasional menu font problem, which I used to only see in firefox, although for all I know it may affect other applications (which I don't use) as well. The attached picture shows what I mean - the fonts are all but unreadable. At the same time, the fonts in Google Chrome are fine.  However, today, and after a recent reboot, the problem is in Chrome and emacs, whereas firefox is fine!

I can usually fix this by logging out of KDE and back in again (which means having to restart all my current applications), but I'm wondering if there's an easier solution? Also, what causes this font blurriness?

Note that restarting firefox doesn't fix the problem, so it seems to be something to do with the underlying font engine.

Thanks,
-A.

---

### Post by Impavidus on 2013-01-24
Looks like sometimes your video memory gets corrupted. This usually indicates a buggy video driver. Have you installed the proprietary drivers (if available)? What kind of graphics card do you have? If it's very recent the open source drivers may still be buggy, which will probably be solved soon. In the meantime, the less video memory you use, the less likely the problems are to happen.

---

### Post by AussieGuy on 2013-01-24
I never would have thought of the problem being the video driver - that's an excellent suggestion.  I'm using an oldish laptop - a Lenovo ThinkPad T500 - but with a fairly new distribution.  So I might see if there are better proprietary video drivers than the generic ones provided by Ubuntu.

-A.

---

