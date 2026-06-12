---
title: "boot to command line"
date: 2007-03-02
forum: General Help
---

### Post by ed_999 on 2007-03-02
How can I configure Ubuntu to boot directly to the command line?
I prefer to log in onto the command line, and then, if need be, to
start the GUI with startx.  Can this be done with Ubuntu? I hope so.
  What files do I have to configure and what do I write in them?

---

### Post by dcstar on 2007-03-02
> **ed_999 said:**
> How can I configure Ubuntu to boot directly to the command line?
I prefer to log in onto the command line, and then, if need be, to
start the GUI with startx.  Can this be done with Ubuntu? I hope so.
  What files do I have to configure and what do I write in them?

Remove the link to the init file that starts the GDM.

Mine is /etc/rc2.d/S13gdm

You can then manually start the GUI with:
```
sudo /etc/init.d/gdm restart
```

---

### Post by nereid on 2007-03-03
> **dcstar said:**
> Remove the link to the init file that starts the GDM.

Mine is /etc/rc2.d/S13gdm

You can then manually start the GUI with:
```
sudo /etc/init.d/gdm restart
```

This actually starts only the graphical login. Just type *startx* to start the Xserver from the console. Before you start the Xserver just enter this command in the console (only needed for the first time).

```

echo "exec gnome-session" > ~/.xinitrc

```

---

