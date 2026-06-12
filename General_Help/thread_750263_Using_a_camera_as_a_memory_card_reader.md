---
title: "Using a camera as a memory card reader"
date: 2008-04-09
forum: General Help
---

### Post by LandonSmithie on 2008-04-09
I have a Fujifilm FinePix S700 which shows up as a USB PTP Class camera in gthumb. Is it possible to mount the sd card like a flash drive or something so I can write to it without buying a memory card reader?

---

### Post by jken146 on 2008-04-09
It might be.  Please open a terminal and type ```
sudo fdisk -l
``` then plug your camera in with a (formatted) memory card in it, turn it on and type ```
sudo fdisk -l
``` again.  Compare the outputs from the first and second times, looking for a new device appearing (the memory card).

---

### Post by LandonSmithie on 2008-04-09
No other devices popped up :\

Would that have been the only way to see if it was possible?

---

