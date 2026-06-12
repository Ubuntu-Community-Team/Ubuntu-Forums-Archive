---
title: "gnome-terminal geometry"
date: 2006-08-22
forum: General Help
---

### Post by etank on 2006-08-22
Im looking for a way to change the default size of the gnome-terminal. It defaults to 80x24 and for me that is too small. In KDE using konsole there was a place to make this change but I can not find it in Gnome. I looked in gconf-editor but couldn't figure out what setting to make.

Thanks

---

### Post by Sam on 2006-08-22
This is not the most convenient solution, but you can edit the launcher/menu item and add```
--geometry=[COLOR="Red"]X[/COLOR]x[COLOR="Red"]Y[/COLOR]
```at the end of the "Command" field.

---

### Post by etank on 2006-08-22
This works but I was just looking for a different way to do it.

---

### Post by nanotube on 2006-08-23
> **etank said:**
> This works but I was just looking for a different way to do it.

heh, back in the day, i was looking for a different way too, but that's the only way i found. 

also, you might want to edit the "preferred apps" control panel to add the geometry argument to the terminal, so that when you start it with a kb shortcut, it also is the size you want.

---

### Post by dtmilano on 2006-09-28
Well, there's another way of doing it.
Take a look at [gnome-terminal-launcher]("http://gnome-tla.sourceforge.net") and you will be able to specify geometry as well as other extra command line options in GConf.

There's also [Installation and configuration instructions]("http://gnome-tla.sourceforge.net/wiki/index.php/Gnome-terminal-launcher_installation_and_configuration").

---

