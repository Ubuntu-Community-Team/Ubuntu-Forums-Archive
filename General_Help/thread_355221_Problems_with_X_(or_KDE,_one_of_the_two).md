---
title: "Problems with X (or KDE, one of the two)"
date: 2007-02-06
forum: General Help
---

### Post by Jarn on 2007-02-06
I've had this problem ever since I installed Linux. When I run anything fullscreen, as soon as it runs my resolution (for everything) changes to the resolution of the program (usually a game) and I get scanlines across the screen. It persists both in and out of the program in use. The only way to fix it is to log out and back in. Changing my resolution does not work after this happens until I log out and log back in. When I move the slider, it shows a different resolution but nothing happens. And the scanlines, which are the worst part, persist. If I could get rid of those, the resolution wouldn't bother me so much.

---

### Post by Stephen Howard on 2007-02-07
X outputs error messages in /var/log/Xorg*  Can you provide a copy of it?

Also, provide the make/model video card and the make/model of monitor.

Also, from the command line, enter:  xrandr  and provide the output (you may not necessarily have this command, if not skip this).

---

### Post by Jarn on 2007-02-08
Xorg.0.log: [http://pastebin.us/13832](http://pastebin.us/13832)

nVidia Geforce 6800 (video card)
eMachines eView 17f3 (monitor)

(Before I open a fullscreen game)
```
jarn@legion:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1280 x 960    ( 439mm x 329mm )  *60
 1   1280 x 1024   ( 439mm x 329mm )   60
 2   1280 x 854    ( 439mm x 329mm )   54
 3   1152 x 768    ( 439mm x 329mm )   55
 4   1152 x 864    ( 439mm x 329mm )   75
 5   1024 x 768    ( 439mm x 329mm )   87   60   70   75   85
 6    832 x 624    ( 439mm x 329mm )   75
 7    800 x 600    ( 439mm x 329mm )   60   85   75   72   56
 8    640 x 480    ( 439mm x 329mm )   85   75   73   60
 9   1400 x 1050   ( 439mm x 329mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
```

(After I open a fullscreen game)
```
jarn@legion:~$ xrandr
 SZ:    Pixels          Physical       Refresh
 0   1280 x 960    ( 439mm x 329mm )   60
 1   1280 x 1024   ( 439mm x 329mm )   60
 2   1280 x 854    ( 439mm x 329mm )   54
 3   1152 x 768    ( 439mm x 329mm )   55
 4   1152 x 864    ( 439mm x 329mm )   75
*5   1024 x 768    ( 439mm x 329mm )  *87   60   70   75   85
 6    832 x 624    ( 439mm x 329mm )   75
 7    800 x 600    ( 439mm x 329mm )   60   85   75   72   56
 8    640 x 480    ( 439mm x 329mm )   85   75   73   60
 9   1400 x 1050   ( 439mm x 329mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
```

---

### Post by Jarn on 2007-02-08
Bump. :(

---

### Post by Stephen Howard on 2007-02-08
"Setting mode "1024x768@43" has a weirdly low Hz rate.

Can you also provide a copy of your /etc/X11/xorg.conf file?

---

### Post by Arisna on 2007-02-09
I'm not entirely sure what you mean by scanlines, but I think they might be what I get with KPDF.  Try right clicking your KDE desktop and clicking "Refresh Desktop."  That fixes it on a per-incident basis for me.

---

### Post by Jarn on 2007-02-12
By scanlines I mean black lines through everything. Attached is my xorg.conf file. And "Refresh Desktop" did not help.

---

### Post by Jarn on 2007-02-16
Bump.

---

