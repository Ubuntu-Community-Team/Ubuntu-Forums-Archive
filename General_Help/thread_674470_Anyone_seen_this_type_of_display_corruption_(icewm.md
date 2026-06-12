---
title: "Anyone seen this type of display corruption? (icewm titlebar)"
date: 2008-01-21
forum: General Help
---

### Post by tsoutherwood on 2008-01-21
Gutsy 71.0 x86...

[http://www.dionic.net/screen-icewm-broken.png](http://www.dionic.net/screen-icewm-broken.png)

I only get this with IceWM; KDE and Gnome work fine.

System is a Pentium 4 3GHz, Nvidia Geforce 7600, xorg 7.2,
nvidia proprietary driver 1.0-9639 based off an Ubuntu 7.10 Gusty
distro.

I've spent a night on this and been all over google. Tried various options
in xorg.conf such as turning these on and off:

[Device]
...
    Option      "RenderAccel"  "True"
    Option      "AllowGLXWithComposite"    "True"
    Option      "AddARGBVisuals" "True"
    Option      "AddARGBGLXVisuals" "True"


Tried 16 bit colordepth. Same hardware was working fine with Ubuntu 7.04
Feisty.

Some themes, notably ones with flat colours seem to render fine, others with
colour gradients such as IceQua (the one in the example screenshot) are
totally mashed. What seems to be happening is some parts of the titlebar
are rendered transparent, as can be seen if moving the window around.

Also, the mouse cannot "grab" the titlebar on a transparent patch.

This seems to me to be at a higher level than the graphics driver,
especially as I can grab a matching screenshot in gimp (or am I talking
b***ocks?).

No other video corruption is noted and googleearth works fine.

I'll direct this at the IceWM mailing list too, but I thought it was
worth a shot here...

TIA :)

Cheers

Tim

---

