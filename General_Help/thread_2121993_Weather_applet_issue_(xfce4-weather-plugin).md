---
title: "Weather applet issue (xfce4-weather-plugin)"
date: 2013-03-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-03-03
when i click my applet to get a forecast and it is set to show 7 days it just sits there eating CPU (maxing  core)
it was working fine the other day
i tried changing my location, but i cant get any new temperature (unless it is below 40 F in Abbott, TX, where according to google it is 70 F)
anyone else having issues with it?
xubuntu 12.10 64bit

---

### Post by pqwoerituytrueiwoq on 2013-03-04
Solution:
upgrade all xfce4 stuff to the raring version
Apply patch to theme:
[https://github.com/shimmerproject/Albatross/commit/38edcd9baf2206e92e77f776c15f4bc23f4906ad](https://github.com/shimmerproject/Albatross/commit/38edcd9baf2206e92e77f776c15f4bc23f4906ad)
File to patch:
/usr/share/themes/Albatross/gtk-2.0/gtkrc

---

