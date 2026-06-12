---
title: "Dual monitors: how do i set different resolutions?"
date: 2008-04-11
forum: General Help
---

### Post by Playa1313 on 2008-04-11
I have a regular laptop LCD screen that is resolution 1280x800 and I have a 26" HDTV that is run through a VGA that only accepts 1024x768.

How do I set up my xorg.conf for my ATI radeon 1150 fglrx driver to use the different resolutions?

Thank you!
~ Brian

---

### Post by SorryGoFish on 2008-04-12
Have you checked out XrandR? I'm not sure about ATI, but it's a great tool for my IBM video card, it allows you to hot plug your external monitor. [http://www.x.org/wiki/Projects/XRandR]("http://www.x.org/wiki/Projects/XRandR")

---

### Post by Playa1313 on 2008-04-13
Thank you, that was something I did not know about and haven't tried before.

I still think it should be easier than this, but maybe my setup is just limiting that.

---

### Post by SorryGoFish on 2008-04-13
Yeah, I agree, and so do many others. In my searches I found a number of bug report / feature requests to support this common functionality better in the display configuration wizards. If you feel up to it also check out the "Sample Fn-F7 Script" on there which gets you started towards having a working hot-key to change display settings. That's pretty advanced though.

---

