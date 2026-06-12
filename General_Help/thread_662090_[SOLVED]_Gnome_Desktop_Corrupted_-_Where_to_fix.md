---
title: "[SOLVED] Gnome Desktop Corrupted - Where to fix?"
date: 2008-01-08
forum: General Help
---

### Post by MoebusNet on 2008-01-08
The main panel bar at the top of my gnome desktop got messed up when I tried to use the nvidia-glx-legacy driver for my fx5200pci video card. Any ideas on where to go to fix this?

Thanks in advance!

---

### Post by MoebusNet on 2008-01-09
Applications>Accessories>Terminal

*Code*
~$ gnome-session-remove gnome-panel
~$ gconftool-2 --recursive-unset /apps/panel
~$ gnome-panel &
*End Code*

Thanks to Utkarshraj Atmaram. This solved my problem.

---

