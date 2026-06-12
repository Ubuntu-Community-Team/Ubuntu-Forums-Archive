---
title: "Very slow login after compiling xorg 6.8.2"
date: 2005-09-29
forum: General Help
---

### Post by mcguolo on 2005-09-29
I've recompiled Xorg 6.8.2 from original source, because i didn't manage to make dri work. Now my glxgears runs at 927/928 FPS, but xfce and gnome (and failsafe terminal too) have very slow startup, and application do the same (from gnibbles to xterm). With the original Xorg 6.8.2 from Hoary this didn't happen. The strange thing is that if i log in as root all is normal.

This happens using gdm, startx or startxfce4 with no differences.

Any ideas?
Thanks.

---

### Post by mcguolo on 2005-10-08
Seems i've solved the problem deleting the file .ICEauthoriry in my home directory.

---

### Post by mac-duff on 2008-01-05
thanks. it helped me but for what do we need this file?

---

