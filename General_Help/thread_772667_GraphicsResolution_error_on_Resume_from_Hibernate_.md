---
title: "Graphics/Resolution error on Resume from Hibernate (Hardy)"
date: 2008-04-28
forum: General Help
---

### Post by fifth_rune on 2008-04-28
Just upgraded to Hardy from Gutsy.  Suspend works fine.  When I hibernate, the screen goes dark like usual but then this line appears:

[ 8.769976]drm_sysfs_suspend

Hibernates, then when I try to resume, the graphics are screwy.  I see my desktop and everything, but everything is literally zoomed in and has poor resolution.  I can't see my whole desktop unless I use the mouse to 'scroll' to the other parts of it.  Everything else works fine though.  Any ideas or suggestions?

***

Solved

Had to uninstall 915resolution and make a new Xorg.  Used this command:

sudo dpkg-reconfigure xserver-xorg

---

### Post by fifth_rune on 2008-04-29
Anybody else have this problem?

---

### Post by fifth_rune on 2008-04-30
Bueller?

---

