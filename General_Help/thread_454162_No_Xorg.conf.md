---
title: "No Xorg.conf"
date: 2007-05-25
forum: General Help
---

### Post by m.g.scott on 2007-05-25
Ok I really need some help here.  I had a friend, notice had, that thought it would be great to modify my colour depth from 24 to 16 in the xorg.conf file to speed up my ati 200m video card.  Now my screen is completely black after the Ubuntu load screen.  I am using ati drivers with Ubuntu 7.04.  I have tried to edit xorg.conf from the recovery console but I cannot find /etc/x11/xorg.conf.  Can anyone help?

---

### Post by Viskovitz on 2007-05-25
Maybe it's a silly thing, but have you checked the case of the path? It's:

/etc/X11/xorg.conf

with uppercase X.

If still you can't find it, do:

```

cd /etc/X11/
ls -A

```

you may see some backed-up xorgs.conf. Look at them, find one with the 24 bits and then:
```

cp xorg.conf.2007whatever xorg.conf

```

---

### Post by m.g.scott on 2007-05-25
Ok I have fixed it.  All I did was drop in a copy of Kubuntu 7.04, then mounted my Ubuntu partition, found xorg.conf and edited as root with kwrite.  Man too much work.  now everything is working again.

---

