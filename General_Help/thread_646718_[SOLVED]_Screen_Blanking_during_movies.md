---
title: "[SOLVED] Screen Blanking during movies"
date: 2007-12-21
forum: General Help
---

### Post by cartisdm on 2007-12-21
I've tried searching around the forums as well as google but I keep finding the problem that their screen goes blank during installation or login so I gave up.

While trying to watch movies, dvds, etc my screen goes blank after like 10 minutes.  I've checked the power management settings and the screen saver stuff but theres nothing set in there that should allow the screen to go blank.  The backlight is still on and it doesn't log me out (such as when my screensaver kicks in) it's just annoying because I have to get up from my comfy chair and move the mouse around.

Any ideas?

---

### Post by jocko on 2007-12-21
> **cartisdm said:**
> I've tried searching around the forums as well as google but I keep finding the problem that their screen goes blank during installation or login so I gave up.

While trying to watch movies, dvds, etc my screen goes blank after like 10 minutes.  I've checked the power management settings and the screen saver stuff but theres nothing set in there that should allow the screen to go blank.  The backlight is still on and it doesn't log me out (such as when my screensaver kicks in) it's just annoying because I have to get up from my comfy chair and move the mouse around.

Any ideas?

This happens when you run xgl on an ATI graphics card. To fix it, you can do this:```
gksudo gedit /etc/X11/xorg.conf
```Add this section to the file and save it:
```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection 
```If you already have a section called "ServerFlags", just add the four "Option" lines before the "EndSection" line.
Restart the xserver (ctrl-alt-backspace) and the new settings should take effect.

---

### Post by cartisdm on 2007-12-22
awesome, that fixed it perfectly thanks:)

---

