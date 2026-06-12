---
title: "Annoying X-Screen Pointer (4.10 Laptop)"
date: 2004-11-27
forum: General Help
---

### Post by grille357 on 2004-11-27
Hallo!

I have installed Ubuntu (4.10) on a Asus 8400K Laptop (so far no greater problems, although no optimal harddisk parameters). 
After login the X-Screen pointer (cross) is stucked in the middle and foreground of the desktop in addition to the normal gnome pointer moveable by the mouse.
Even on the screensaver I see this black cross.
Is there a known solution to this problem (normally I prefer the KDE manager and have not much experience with gnome) ?

Greetings,

Carsten

---

### Post by daniels on 2004-11-27
Edit /etc/X11/XF86Config-4, and in the Device section, add 'Option "SWCursor"'.

---

### Post by grille357 on 2004-11-27
Thank you. Fast answer and it works.

Carsten

---

