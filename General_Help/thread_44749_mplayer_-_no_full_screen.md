---
title: "mplayer - no full screen"
date: 2005-06-27
forum: General Help
---

### Post by picaboo on 2005-06-27
hi everyone
when i turn on full screen in mplayer movie doesn't resize. i see only big black screen and movie in original small size. i've tried -vo=xv and it doesn't work. also i compiled mplayer with --enable-xv. in preferences in gmplayer in video option i have only two video driver (x11 and xvidix).
thank for help

---

### Post by angkor on 2005-06-27
I think the correct syntax is:

mplayer -vo xv [movie.avi] without the =

But anyone correct me if I'm wrong ;)

---

### Post by Bo Rosén on 2005-06-28
[QUOTE=angkor]I think the correct syntax is:

mplayer -vo xv [movie.avi] without the =

But anyone correct me if I'm wrong ;)[/QUOTE]

Depends :-)
On the command line mplayer -vo xv is correct, but in ~/.mplayer/config you would enter vo=xv

However, I had the exact same problem when I compiled mplayer myself. Then I uninstalled it (sudo make uninstall) and used apt-get instead and everything works fine. I think I used the instructions from the excellent [Unofficial Ubuntu 5.04 starter Guide](http://ubuntuguide.org/#mplayer) 

good luck.

---

### Post by arnieboy on 2005-06-28
[QUOTE=picaboo]hi everyone
when i turn on full screen in mplayer movie doesn't resize. i see only big black screen and movie in original small size. i've tried -vo=xv and it doesn't work. also i compiled mplayer with --enable-xv. in preferences in gmplayer in video option i have only two video driver (x11 and xvidix).
thank for help[/QUOTE]
The correct way to do it would be to put "zoom = yes" (the default is "no") in the mplayer.conf file.

---

### Post by picaboo on 2005-06-28
of course -vo xv is correct :) but its still doesn't work.
when I added this line (vo_driver = "xv") in .mplayer/config i see this line in terminal: Warning unknown option vo_driver at line 2.
with this line (zoom=yes) movie is resizing on full screen correct but its very very slowly then.

---

### Post by arnieboy on 2005-06-28
when u are running an OS like ubuntu with movie players like mplayer, u need 2 things:
1) a fast comp.
2) a fast net conn.
or else, everything starting from compiling programs to running openoffice to running updates on ur comp will drive u nuts

---

### Post by picaboo on 2005-06-28
well actually i haven't fast computer, but a few month ago i had red hat on my computer. and there mplayer was really fast.

---

### Post by cutOff on 2005-06-28
[QUOTE=picaboo]hi everyone
when i turn on full screen in mplayer movie doesn't resize. i see only big black screen and movie in original small size. i've tried -vo=xv and it doesn't work. also i compiled mplayer with --enable-xv. in preferences in gmplayer in video option i have only two video driver (x11 and xvidix).
thank for help[/QUOTE]
Did you install either Nvidia or ATI drivers??

---

### Post by picaboo on 2005-06-28
i have nvidia driver from apt-get

---

### Post by remin8 on 2005-08-01
I have the same problem... here is my solution... in mPlayer go to prefrences then video, then select the gl (X11 (openGL)) driver... hope that works! it did for me.

---

### Post by f76 on 2005-08-07
[QUOTE=arnieboy]The correct way to do it would be to put "zoom = yes" (the default is "no") in the mplayer.conf file.[/QUOTE]

Thank you..!!!! i spent 20 mins looking around in the mplayer-man and now u fixed it for me....
[B]
so with nvidia gfx card the x11 driver in gmplayers settings and adding zoom=yes in the .conf seem to work[/B]

---

