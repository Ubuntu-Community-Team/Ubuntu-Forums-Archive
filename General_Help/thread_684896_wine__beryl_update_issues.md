---
title: "wine / beryl update issues"
date: 2008-02-01
forum: General Help
---

### Post by Xephrey on 2008-02-01
After trying to upgrade my distribution, I quickly discovered that I could not update my wine version or my beryl version. My guess is a needed source list update, I'm just not completely sure about that or what addresses I need. Also, whenever beryl is enabled, window borders are disabled and Emerald doesnt take effect either. I have solved this before, I just dont recall what's needed. I'm getting back into Ubuntu again after a long absence, so I need a bit of help

Thanks!

---

### Post by overdrank on 2008-02-01
> **Xephrey said:**
> After trying to upgrade my distribution, I quickly discovered that I could not update my wine version or my beryl version. My guess is a needed source list update, I'm just not completely sure about that or what addresses I need. Also, whenever beryl is enabled, window borders are disabled and Emerald doesnt take effect either. I have solved this before, I just dont recall what's needed. I'm getting back into Ubuntu again after a long absence, so I need a bit of help

Thanks!

Hi and yes as I understand during the upgrade it will remove the third party repos before the upgrade. For the title bars missing what is the model of the graphics card? If nvidia You may need
to add
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
In the device section.
Edit your xorg with this command ```
gksudo gedit /etc/X11/xorg.conf
``` You can use this command via alt, F2 key

---

