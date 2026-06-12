---
title: "Is it still possible to have the magic lamp/genie effect for minimizing windows?"
date: 2018-06-01
forum: General Help
---

### Post by jonathan90 on 2018-06-01
Is it still possible to have the magic genie/lamp effect when you minimize a Window like on OS X? There seem to be [old threads]("https://ubuntuforums.org/showthread.php?t=1605569") on it, but they're from 2009/2010 and I can't find the settings in CCSM that they mentioned.

---

### Post by deadflowr on 2018-06-01
Yes.
But you need to run the unity desktop.
Ubuntu 18.04 switched to gnome's gnome-shell as the default desktop.
gnome-shell does not use compiz or ccsm.

What is the current version of Ubuntu you're using, by the way.

---

### Post by again? on 2018-06-01
If you are using a desktop environment that allows you to use compiz as the window manager,
the setting is still in CCSM.
CCSM > Effects > Animations > Minimize animations tab
Double click on the current animation to bring up a dialog to choose animation and duration.

---

### Post by jonathan90 on 2018-06-08
Wait, so what does gnome-shell use as its window manager?

---

### Post by again? on 2018-06-08
[**gnome-shell**]("https://en.wikipedia.org/wiki/GNOME_Shell") uses [**mutter**]("https://en.wikipedia.org/wiki/Mutter_(software)") as the window manager.
In gnome-shell however, mutter is an integral part of [**gnome3**]("https://en.wikipedia.org/wiki/GNOME#GNOME_3") and if replaced you lose the graphical shell (dock, panel, apps overlay etc).
In gnome2 everything was separate and mostly interchangeable. (panel window manager dock etc)

Best to use compiz in desktop environments where the window manager isn't integrated.
The unity interface was a compiz plugin.

---

