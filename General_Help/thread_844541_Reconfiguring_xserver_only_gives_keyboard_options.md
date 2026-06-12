---
title: "Reconfiguring xserver only gives keyboard options"
date: 2008-06-29
forum: General Help
---

### Post by MangasColoradas on 2008-06-29
When I do ```
sudo dpkg-reconfigure xserver-xorg
``` I only get options to configure the keyboard and that is all. When I have reconfigured the xserver previously I got options for the monitor and graphics card etc, why not now?

---

### Post by ajgreeny on 2008-06-29
Try ```
sudo displayconfig-gtk
``` in terminal and you may be able to change things here.  It will depend on your driver which resolutions are available, but it may do whatever you need.  This is actually in the menus, but hidden by default, in my system it was under **Applications>>Other>>Screens and graphics** but it could be elsewhere on yours as I use the main gnome menu, not the menu bar as ubuntu does.

---

