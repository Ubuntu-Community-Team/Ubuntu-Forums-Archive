---
title: "help with fglrx"
date: 2006-12-20
forum: General Help
---

### Post by Choad on 2006-12-20
```
richard@fleurs-computer:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

also, glxgears gives me piss poor performance. somethings not right!

---

### Post by Choad on 2006-12-20
bump!

---

### Post by madcow72 on 2006-12-20
If fglrxinfo is saying that mesa is being used for rendering, then it would seem that the ATI driver is not properly installed.  You may want to try re-installing the correct driver for your card.  I use [COLOR="Blue"][this howto]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")[/COLOR] on my ATI card, but switch their 8.32 driver for the 8.28.8 driver I downloaded from ATI.

Actually, I should say that I use Method 2 from that site specifically.

---

### Post by meng on 2006-12-20
I also recommend that howto.

---

### Post by Choad on 2006-12-20
ahh the howto helped. i needed to disable composite

---

### Post by Choad on 2006-12-20
ok is it possible to have beryl going with composite disabled?

i cant seem to find a single howto aimed at getting beryl running with fglrx

---

### Post by madcow72 on 2006-12-20
I believe it is possible.  I've had beryl running on this computer with my Radeon 9250 after installing the driver with the method I suggested earlier.  However, it didn't work in dual-head mode for me and I need both monitors for my work - also things were rather unstable - and so I uninstalled.  In any case, [[COLOR="Blue"]this[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7") may be a good howto on the subject.  Also, PriceChild has a sticky on installing Compiz and Beryl [[COLOR="Blue"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=272104")

---

