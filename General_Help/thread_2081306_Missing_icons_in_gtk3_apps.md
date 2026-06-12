---
title: "Missing icons in gtk3 apps"
date: 2012-11-06
forum: General Help
---

### Post by papa33170 on 2012-11-06
Hi,

many apllications, like totem or palimpsest have a lot of missing icons.
This occurs ONLY when I run them as normal user, if I run them as root, everything looks ok.
The package gnome-icon-theme-symbolic is installed, and if I delete the gtk-3.0 folder
in /home/.config, icons are back but the oxygen theme is not apllied anymore.

Any help appreciated,
thanks in advance,
papa

---

### Post by papa33170 on 2012-11-08
So basically there were some icons missing in /home/user/.icons. Which ones, I don't know, so I made a copy of /usr/share/icons into it, and it works.

---

