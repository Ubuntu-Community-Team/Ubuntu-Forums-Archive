---
title: "I can has opengl + xwinwrap + hardy heron?"
date: 2008-05-14
forum: General Help
---

### Post by hollerith on 2008-05-14
Fresh Hardy Heron install.  ATI fglrx.  Gnome.

I've got xwinwrap running xmatrix and mplayer but none of the opengl screensavers seem to work properly - they just take over/run like a screensaver instead of an animated wallpaper.  Well not quite like a screensaver with all the flickering and flashing.  

This used to work with Beryl and Feisty on this box and all the tutorials use glmatrix as an example.  

I've been through the forums and tutorials (some of which I used the first time).  

Anyone know of any other apps that run can be xwinwrap'ed?

---

### Post by overdrank on 2008-05-14
> **hollerith said:**
> Fresh Hardy Heron install.  ATI fglrx.  Gnome.

I've got xwinwrap running xmatrix and mplayer but none of the opengl screensavers seem to work properly - they just take over/run like a screensaver instead of an animated wallpaper.  Well not quite like a screensaver with all the flickering and flashing.  

This used to work with Beryl and Feisty on this box and all the tutorials use glmatrix as an example.  

I've been through the forums and tutorials (some of which I used the first time).  

Anyone know of any other apps that run can be xwinwrap'ed?

HI and have you tried to change the code for xwinwrap like
```
xwinwrap -ni -argb -fs -s -st -sp -a -nf -- /usr/lib/misc/xscreensaver/glmatrix -root -window-id WID
```
If you change the -a to -b this will allow the screen saver to run below. Also you may need to add -o       opacity=#   Between 0 and 1
example  -o 0.6
```
xwinwrap -ni -argb -fs -s -st -sp [COLOR="Red"]-b[/COLOR] [COLOR="Red"]-o 0.6 [/COLOR]-nf -- /usr/lib/misc/xscreensaver/glmatrix -root -window-id WID
```

---

### Post by bmdavis on 2008-05-17
Yeah, mine does the same thing (same problem).  Tried the -b option or some other xwinwrap options, nothing..

ati x1400, compiz, hardy.... no xwinwrap

---

### Post by hollerith on 2008-05-19
I used to have Beryl and this working - I had flying toasters in a transparent cube and even the fan joined in to add to the flyby effect.  t sort of appeared inside like the atlantis plugin.  Compiz draws on a virtual root window obscuring the actual root window.  Mplayer and xmatrix are fine.  Various others such as webcollage (uses xscreensaver-getimage), xplanet &c don't work for me.  I can't help thinking its some compositing setting I'm missing, or some compiz setting.  I'm using Xgl, fglrx driving an ATIx200.  My xorg.conf is unmodified from a clean install of Hardy Heron.  I used to have all sorts of switches set to get Beryl to work.  

any ideas

---

### Post by cosmicharade on 2009-07-17
Has anyone got xwinwrap working with xplanet?

---

### Post by hollerith on 2010-03-06
Of course I'm not on Hardy any more but is not working in just the same way on Intrepid and now Jaunty and it is now.

Oh and sorry about the lolcat, some screensavers behave like galaxy but the gl ones flicker.  Video works okay.

---

