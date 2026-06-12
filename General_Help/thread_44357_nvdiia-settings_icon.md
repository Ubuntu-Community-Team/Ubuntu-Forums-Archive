---
title: "nvdiia-settings icon"
date: 2005-06-25
forum: General Help
---

### Post by arnieboy on 2005-06-25
does anybody have a nice 32x32 icon for NVIDIA-settings in Gnome Menu? Will be great if somebody could share it with me.

---

### Post by skoal on 2005-06-25
Here ya go sir! - see attached -

---

### Post by arnieboy on 2005-06-25
Thanks a lot! I really appreciate it.

---

### Post by skoal on 2005-06-25
no problemo.  I didn't notice until afterwards you said 32x32.  That whole icon set is in 48x48 and all .png(s), but they should scale just fine.  I use 'em just fine in Gnome, XFCE4, and KDE as well.

\\//_

---

### Post by TristanMike on 2005-06-25
Hi, thanks too for the icons.  Mind if i ask, how do I apply the icon?  I'm still very technically new, sorry.
TristanMike

---

### Post by skoal on 2005-06-25
I don't use any menu editors, so I'm probably the wrong person to ask, but here's how I do it.  I think you should already have an entry (.desktop file) in /usr/share/applications called 'NVIDIA-Settings.desktop'.  Here's what mine looks like:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
[COLOR=DarkRed]Icon=/usr/share/pixmaps/nvsphere.png[/COLOR]
Terminal=false
Type=Application
Categories=Application;System;

Just copy those nvidia .png files into some directory - you can see that I used /usr/share/pixmaps above (in red).  Then, just modify the "Icon=" line to point to which icon you want to use.

\\//_

---

### Post by TristanMike on 2005-06-25
Thank you, I thought it might be something like that, but better safe than sorry, you guys are the shiz-nit!
Thanx
TristanMike

---

### Post by skoal on 2005-06-25
[QUOTE=TristanMike][...] you guys are the shiz-nit![/QUOTE]
lmao. yeah yeah yeah...that's how we roll g...

\\//_

---

### Post by arnieboy on 2005-06-25
hey skoal.. the icons scaled just fine. thanks a lot again

---

