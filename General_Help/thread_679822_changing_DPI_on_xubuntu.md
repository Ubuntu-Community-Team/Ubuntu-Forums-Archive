---
title: "changing DPI on xubuntu"
date: 2008-01-27
forum: General Help
---

### Post by abcdfv on 2008-01-27
how do i change the dpi on xubuntu?
i've tried doing the
sudo xrandr --dpi <value>

in terminal, but i did not see any change even after a restart

---

### Post by chewearn on 2008-01-28
Add to /etc/X11/xorg.conf, under Section "Monitor":

   DisplaySize <x> <y>

where
<x> is the horizontal size of your display, in millimeter
<y> is the vertical size of your display, in millimeter

---

