---
title: "ORiNOCO causes a lockup on connect"
date: 2007-05-29
forum: General Help
---

### Post by WeeJeWel on 2007-05-29
Hi there!

I just managed to install orinoco yesterday on my Kubuntu partition. The driver works fine (it seems it does, it detects AP's including mine) but when I open KNetwork Manager and connect to my AP the whole system freezes. Somewhere at 28% on the progress bar.

It happens every time, even after a shutdown-start and reset, whatever.

I have a SpeedTouch 120 that does work fine on windows, but on Linux it's a hell.
Oh, i modified the source of orinoco cause it wasn't able to make. > You might just try amending orinoco.c with gedit or kate to edit both lines 4287 and 4288 of orinoco.c replacing dev->dev.parent with dev->class_dev.dev. Then try make again.

Thanks in advance!

---

### Post by WeeJeWel on 2007-05-29
~bump

---

