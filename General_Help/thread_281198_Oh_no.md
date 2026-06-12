---
title: "Oh no"
date: 2006-10-20
forum: General Help
---

### Post by Dawar on 2006-10-20
I was installing ati drivers and that.
But when i went editing this
sudo gedit /etc/X11/xorg.conf 
and replaced the name of driver after the restart i see only black screen. How could i restore default configuration?

---

### Post by bsussman on 2006-10-20
<ctl><alt>F1 should give you a text console.

you can then sudo vi (or nano) the file and fix it. you cannot use a graphical editor until you get x working again...

Or copy the backup copy back, if you made one, using cp (copy pgm)

---

