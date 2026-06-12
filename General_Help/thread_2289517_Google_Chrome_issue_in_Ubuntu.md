---
title: "Google Chrome issue in Ubuntu"
date: 2015-08-04
forum: General Help
---

### Post by AtomicPenguin on 2015-08-04
I'm running Ubuntu v14.04.  The version of Chrome I have installed is 44.0.2403.125 (64-bit).  More often than not when I right-click in Chrome the context menu is completely black.  Even when passing over it with the mouse.  There are times when even the bookmarks menu - submenus off of that will be black.

Any ideas?

---

### Post by Vladlenin5000 on 2015-08-04
Such symptom, more often than not, has to do with graphics drivers.
Which graphics card/chip do you have? What driver are you using?

---

### Post by speartip on 2015-08-04
Could have something to do with hardware acceleration.
Try unticking the "enable hardware acceleration" box in chrome's advanced settings.

---

### Post by AtomicPenguin on 2015-08-04
[FONT=Courier New]01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310] (rev a2)[/FONT]

Unchecking the 'Use hardware acceleration when available' option did the trick.  Is there a loss with this?  I wonder what that helps?

---

### Post by Vladlenin5000 on 2015-08-04
That working tells me you're using the open source (and default driver). Perhaps you should consider installing the recommended proprietary drivers.

System Settings > Software & Updates, Additional Drivers tab.

---

### Post by AtomicPenguin on 2015-08-04
Just did that Vladlenin5000 and it's working like a charm now with the 'Use hardware acceleration' enabled!

Thanks for the help!

---

### Post by AtomicPenguin on 2015-08-04
The collateral damage to this seems to be Minecraft.  It crashes when I try to run it with anything but the open source driver?  Should I post a new thread?


I'm good.  A reboot seems to have resolved it.

---

