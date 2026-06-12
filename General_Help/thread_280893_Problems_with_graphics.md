---
title: "Problems with graphics"
date: 2006-10-20
forum: General Help
---

### Post by Chillster on 2006-10-20
Dont know if this is the right place to but this thread but here goes...
Just installed ATI drivers for my 9800Pro and beryl/xgl. Installed them both using cut and paste guides so i dont know exactly what ive done. 

when i run  fglrxinfo in regular gnome all looks well:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

But when i log in to XGl things arent working at all well for example it takes for ever for the letters to appear when i type i FF. When i run fglrxinfo whe logged into XGl i get this:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Seems like something is wrong but i cant tell what, anyone got any ideas ?

---

### Post by pay on 2006-10-20
You need the 3d fglrx driver, not the 2d mesa driver. I like this guide [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

