---
title: "OpenOffice Impress Problem"
date: 2007-10-30
forum: General Help
---

### Post by natewiebe13 on 2007-10-30
I'm using Ubuntu Studio 7.10 and when OpenOffice starts a full screen presentation the transitions are very choppy. For instants I need the "smooth fade" transition for the presentation. Instead of it fading, it pauses for a second then the next slide appears as if there is no transition. Could someone help please.
thanks in advance

---

### Post by neoraptor on 2007-11-26
I have the same problem.

My computer is a Dell Precision M6300 (Core 2 Duo 2.2Ghz, 3Go RAM, Geforce FX1600M).
Nvidia drivers are installed. Compiz-fusion runs really well.

But in OpenOffice Impress, it is really slow, even if I create a new presentation from scratch.
I try to turns on the openGL and hardware acceleration in the menu, but it barely changed.

I wonder if there is a way to run powerful effects (like in Compiz-Fusion), but for a presentation software.

I already take a look at keyjnote, but it only render pdf files, and it is not a complete presentation software.


Looking forward your answer

---

### Post by tak1150 on 2007-12-12
> **neoraptor said:**
> I have the same problem.

My computer is a Dell Precision M6300 (Core 2 Duo 2.2Ghz, 3Go RAM, Geforce FX1600M).
Nvidia drivers are installed. Compiz-fusion runs really well.

But in OpenOffice Impress, it is really slow, even if I create a new presentation from scratch.
I try to turns on the openGL and hardware acceleration in the menu, but it barely changed.

I wonder if there is a way to run powerful effects (like in Compiz-Fusion), but for a presentation software.

I already take a look at keyjnote, but it only render pdf files, and it is not a complete presentation software.


Looking forward your answer

I don't use transitions, but have the same problem with animations.
I have not solved the problem, but I was able to improve the situation by:

1) uninstall Ubuntu OO and install the native OO from OOo.
2) in xorg.conf, changed the colordepth from 24 to 16

But we need a REAL solution for this.

---

