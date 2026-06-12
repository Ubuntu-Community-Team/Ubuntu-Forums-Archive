---
title: "X800SE driver install problems!"
date: 2007-02-21
forum: General Help
---

### Post by Wil0 on 2007-02-21
Ive been trying to install the fglrx drivers without any luck, i just get this every time:
wil@slackbox:/etc/X11$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Im running x64 edgy and have set the xorg device driver to fglrx. why is it not working?!

---

### Post by kefir on 2007-04-11
Have pretty much the same system as you and also had a little trouble getting it to work at first, until i found this page

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Use the drivers from the ati homepage and follow the instructions on that page and u should be fine (i was atleast :) )

---

