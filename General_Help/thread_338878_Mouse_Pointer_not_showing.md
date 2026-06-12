---
title: "Mouse Pointer not showing"
date: 2007-01-15
forum: General Help
---

### Post by smeagoly1 on 2007-01-15
HI, new to Ubuntu and Linux in general, before installing fully Ubuntu/Linux i tried out both the 32bit and 64bit 6.10 versions from a boot cd.

Both boot up fantastic, Main display screen, icons etc.

But the mouse  pointer does not show up, but I can see that the mouse works as it highlights the sections when the mouse is moved performs the actions when the mouse button is clicked.

AMD 64, 1G DDR, Nvidia 6600 Graphics.  The mouse and Keyboard are both USB, does this matter?

Many Thanks
Smee

---

### Post by nox.freak on 2007-02-01
I'm having the same problem you find a fix?

---

### Post by nox.freak on 2007-02-03
Found the fix you have to add the fallowing line to you xorg.conf under the "Device" section
Option "HWCursor" "off"

---

