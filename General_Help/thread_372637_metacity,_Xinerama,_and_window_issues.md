---
title: "metacity, Xinerama, and window issues"
date: 2007-02-28
forum: General Help
---

### Post by harty83 on 2007-02-28
I have finally gotten dual monitor setup working between my laptop (with intel 945GM graphics card) and an external LCD.

I am using xinerama.

My laptops resolution is 1280x800 and my external monitor's is 1280x1024.  

The problem is that metacity will not allow me to drag windows horizontally past a certain point on my second monitor.  It will also not allow me drag vertically past a certain point.  

However, if I use openbox, everything works just fine.  

Anyone know how to remedy this in metacity or is it a bug that needs to be dealt with?  I'm fine with using openbox when I dual monitor but thought I would ask if others are experiencing similar problems with metacity and know how to fix it.  I've just set up two icons one for openbox and one for metacity which i can use to quickly alternate between the two.

---

### Post by veloce on 2007-02-28
I had similar issue and it was to do with gnome remembering stuff about the screen that it shouldn't.  The fix was to delete the directory:

~/.gconf/desktop/gnome/screen  (where ~ is your home directory).

Not sure the equivalent fix this for your system.

---

