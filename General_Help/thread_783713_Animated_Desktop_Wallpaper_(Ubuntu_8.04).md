---
title: "Animated Desktop Wallpaper (Ubuntu 8.04)"
date: 2008-05-06
forum: General Help
---

### Post by captainhowdy705 on 2008-05-06
I have searched and searched for how to animate my desktop wallpaper for Ubuntu 8.04, but so far none of them have worked as most of the help was for older versions. 
If anyone can help me in this department, it would be much appreciated.

---

### Post by mano cazalet on 2008-05-06
what exactly do you mean with animated?

something like this?
[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)

---

### Post by captainhowdy705 on 2008-05-06
Kind of. 
An example would be that falling Matrix numbers that everyone seems to use as their background.

---

### Post by mano cazalet on 2008-05-06
Check [this]("http://blog.prashanthellina.com/2007/08/22/matrix-desktop/") blog

---

### Post by pingpongboss on 2008-05-06
> **captainhowdy705 said:**
> Kind of. 
An example would be that falling Matrix numbers that everyone seems to use as their background.

[http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)
worked perfectly for me in Hardy

---

### Post by hollerith on 2008-05-13
It doesn't work for me under Hardy Heron!  I had this working a while back on Feisty and Beryl on this box so I know what it looks like.  I can use mplayer video onto the root window and it works fine but the screensavers don't work properly - they're not on the root window they're just like screensavers with flickers of the desktop.  If I try to rotate the cube with them on it says 'blocked event processing'.  This is a brand new install of Hardy.  The graphics card an ATI x200M.  I'm using fglrx.  

Any ideas welcome.

---

### Post by damis648 on 2008-05-13
just install xwinwrap like it says on that page and then in terminal enter
```
xwinwrap -ni -argb -fs -s -st -sp -nf -b -o 75 -- /usr/lib/xscreensaver/glmatrix -window-id WID
```
and make sure it is working. If it does, just press alt+f2 and type the same thing. Also add this command to "sessions" under preferencs so it will start automatically on every boot

---

### Post by hollerith on 2008-05-13
Okay I tried it - it looks a lot like all the others I tried.

It runs as a screensaver - hides everything - not on the cubeface, the -b flag is set.  It flickers/flashes/pages.  If I rotate the cube the dark screen disappears and I can see the desktop again until I let the mouse go.  

It works with mplayer video though.  Any of the GL screensavers seems to have this problem, xmatrix runs okay.

Thanks anyway,


(BTW Your -o opacity setting should be .75 for 75%)

---

### Post by hollerith on 2008-05-23
> **pingpongboss said:**
> [http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/](http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/)
worked perfectly for me in Hardy

Is this true at all?  Can anyone do this - xwinwrap + glmatrix + hardy heron?  The best I can do is get mplayer and xscreensaver xmatrix running.  The glmatrix stuff doesn't work or its related to the using git rather than repo.  I don't know.  It seems a strange claim to make.

---

### Post by PinkFloyd102489 on 2008-05-23
Try installing the GL packages associated with Xscreensaver.

---

### Post by hollerith on 2008-05-23
> **PinkFloyd102489 said:**
> Try installing the GL packages associated with Xscreensaver.

Serenity now!  have you done this?  They don't work.  They take over the whole thing. xmatrix works fine.  glmatrix - honk!

Okay - apart from the obvious has anyone gotten glmatrix to work with xwinwrap on hardy heron?

---

### Post by SerafeimG on 2008-11-08
Does anyone know how to uninstall the animated desktop and turn it back to the default??

---

