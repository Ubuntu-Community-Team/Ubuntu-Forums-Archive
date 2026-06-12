---
title: "Desktop Effects Problem"
date: 2008-04-11
forum: General Help
---

### Post by death soldier on 2008-04-11
hello i have probelem with destop effects when i enable the desktop efects my title bar dissapear...pls quick answer i can move anything......!!!

---

### Post by tamoneya on 2008-04-11
first of all to solve the moving you can just hold down alt and then click anywhere with in the window to drag it.  Take a look inside system -> preferences -> advanced desktop effects settings.  Look in the general options plugin.  Make sure that Hide skip taskbar window is checked.

---

### Post by erginemr on 2008-04-11
To have the advanced desktop settings, you need to install compizconfig-settings-manager (ccsm) with:
```
sudo aptitude install compizconfig-settings-manager
```
from a terminal or finding and installing the package from Synaptic.

Also make sure that "Window Decoration" under Effects has been checked.

---

### Post by ryanhaigh on 2008-04-11
If you have the advanced settings app installed make sure window decorations are enabled

---

### Post by erginemr on 2008-04-11
If you still don't get the title bars, then please read the posts in:
[http://ubuntuforums.org/showthread.php?t=620521](http://ubuntuforums.org/showthread.php?t=620521)

and make sure that you have the following lines in your X config file (xorg.conf) with:
```
less /etc/X11/xorg.conf
```

```
Section "Device"
        ...
[COLOR="Red"][B]        Option          "AllowGLXWithComposite" "true"
        Option 		"AddARGBGLXVisuals" "True"
[/B][/COLOR]        ...
EndSection

Section "Module"
        ...
**[COLOR="Red"]        Load "glx"[/COLOR]**
        ...
EndSection
```

Otherwise, edit this file with:
```
gksudo gedit /etc/X11/xorg.conf
```
add the above lines, save and exit. Kill and restart your X server with **Ctrl+Alt+BackSpace** to see if there is any improvement.

---

