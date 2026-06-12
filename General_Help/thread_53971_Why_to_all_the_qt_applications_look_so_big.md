---
title: "Why to all the qt applications look so big?"
date: 2005-08-02
forum: General Help
---

### Post by sk545 on 2005-08-02
For example, kaffeine (see attachment).

I have tried other qt based apps (ksensors) and that looks huge too.  Any way to fix this?  I am using Ubuntu, not Kubuntu, btw.

Thx.

---

### Post by amohanty on 2005-08-02
install KDE Control Center and setup the fonts to your liking.

AM

---

### Post by kiddyfurby on 2005-08-03
install qt3-qtconfig, it allows configuration without kde-control-center

---

### Post by nocturn on 2005-08-03
check your resolution with 
```
xdpyinfo |grep reso
```

Now go in to the Gnome font properties and correct the resolution there to match.  Your fonts should look OK now.

---

### Post by sk545 on 2005-08-03
> install qt3-qtconfig, it allows configuration without kde-control-center 
Tried it, but it only changed the qtconfig dialog, kaffeine stayed the same.  What should i be changing in qtconfig exactly?  Maybe i changed the wrong settings...

> xdpyinfo |grep reso 

That only worked for the gnome desktop/apps.  No effect on the QT apps at all.

---

