---
title: "GTK 2 themes in a WM other than Gnome?"
date: 2005-07-26
forum: General Help
---

### Post by GnuBee on 2005-07-26
How do I change my GTK 2 theme in a Window manager so that my apps don't look like old GTK 1 apps?
I am currently using Window Maker and I can run the theme manager but there is no way to get my theme to stick on start up. I have to run the gnome theme manager manualy to get my apps to look right.

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=GnuBee]How do I change my GTK 2 theme in a Window manager so that my apps don't look like old GTK 1 apps?
I am currently using Window Maker and I can run the theme manager but there is no way to get my theme to stick on start up. I have to run the gnome theme manager manualy to get my apps to look right.[/QUOTE]

I'm moving this, as no true beginner uses Window Maker.

---

### Post by Kimm on 2005-07-26
install gtk-theme-switch

then run gtk-theme-switch2 and select the theme you want... my experiance is that is stays.

---

### Post by varunus on 2005-07-26
You can also set your session (not sure how to do that in windowmaker, probably involves editing the Xsession script that starts it) to load "gnome-settings-daemon"; this will make your GNOME selected icon theme and gtk2 theme stick.  (The control center loads this by default if it isn't open already, which is why that works for you.)

---

