---
title: "Window scroll bars, buttons, etc do not render properly"
date: 2008-03-22
forum: General Help
---

### Post by maestrobwh1 on 2008-03-22
Just reinstalled Xubuntu Dapper on my laptop and I still have an odd issue:

Parts of windows are sort of "gone" until I mouse over them.  In desktop windows, sometimes the scroll bar is "invisible" until I mouse over it.  In firefox, as I type this message, the icons show, but there is no border, but if I scroll down in firefox, the border to this message appears, but only the part that was hidden before.  It seems as if parts of the screen do not "update."  This happened in my previous install after an update and I could not resolve it so that is why I reinstalled the lastest Dapper from CD.

The issue may be that the machine is really old.  Fujitsu lifebook 200 MHz Pentium II with 96 MB RAM.  The graphics card is a trident, and the driver is set to trident.  If I change this to "vesa" I can't get into X, which is odd.  I thought maybe that would help because DamnSmallLinux looks fine on the screen and I believe it uses "vesa."  

I have better hardware other than this machine, but it is a battle tank, still works and is a nice project.

Other stuff that might be helpful to know: The recent install tried a default depth of 24 and the screen was off center, so I had to reload my old xorg,conf.  They look exactly the same except for that item.  I do see that both files have "glx" loading under modules. 

It does seem as if my X is trying to run something that cannot render properly on this old machine.  I only want the X doing the very basic things.

Orignally, on the first install, it looked fine and these issues were not present.

---

