---
title: "Cannot run Feisty 7.4 liveCD in Compaq nc6400 notebook"
date: 2007-07-18
forum: General Help
---

### Post by sarc on 2007-07-18
Brand new HP Compaq nc 6400, when I run the liveCD (either normal or safe graphics mode) Gnome will not load, and I get a message that Xserver cannot run and is disabled.  I suppose the graphics card is not supported.  How to install Feisty?  I don't know much about Linux.  Thanks

p.s. Just booted in Windows and noted the graphic chipset: ATI Mobility Radeon X1300.  I can boot liveCD with Edgy.


p.p.s.s. ^%&$##!!  Just saw this on a search: 

For those unaware: Trying to boot a feisty or gutsy cd with an ATI x-series vidcard leads to x crashing. There is no way to get X running without installing fglrx from the terminal: real fun...particularly from wifi.

THAT SOUNDS BAD!  What the dickens is a fgrlx?????

---

### Post by sarc on 2007-07-19
Triple Bumb!  Bump cubed!!  

Someone?!!??  Helloooooo!

---

### Post by gnoel on 2007-07-19
fglrx is an ATI driver that is not fully open source, and allows advanced functions such as 3-D and the use of external monitors in laptops.  My understanding, which is admittedly pretty limited, is that it is problematic to install and limited in which chipsets it will support.  In addition, legacy versions of the driver may not work with Feisty.

Sorry I can't add more - hopefully this answer will help you refine your research parameters.

---

