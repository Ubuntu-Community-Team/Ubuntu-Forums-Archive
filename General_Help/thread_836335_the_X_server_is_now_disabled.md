---
title: "the X server is now disabled"
date: 2008-06-21
forum: General Help
---

### Post by ramadan on 2008-06-21
when booting ubuntu >>the x server is now disabled, restart GDM when it is configured correctly.
some one tell me to use: gksudo displayconfig-gtk and the result is: gtk warning: cant open display
any help is appreciated guys

---

### Post by sdennie on 2008-06-21
What version of Ubuntu are you using?  Sounds like an older version.  If so, try:

```

sudo dpkg-reconfigure xserver-xorg -phigh

```

If you are running Hardy, instead boot the machine into recovery mode (this can be selected when the machine starts and the grub messages appear) and select xfix when you get to the recovery menu.

---

