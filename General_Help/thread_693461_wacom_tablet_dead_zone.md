---
title: "wacom tablet dead zone"
date: 2008-02-11
forum: General Help
---

### Post by Cha1n5aW on 2008-02-11
Hi, I'm not sure if ths is the proper forum for this thread, but it seemed to be the best fit.  I sometimes use an old wacom graphire drawing tablet, and noticed that there is considerable "jitter" even when the pen is still.  Is there a "dead zone" setting for this?  I cannot seem to find any tablet specific settings anywhere, from what I can tell, Ubuntu just seems to treat it as a mouse.  I noticed while using the gimp that the pressure sensitivity feature works, so that leads me to believe the OS does in fact have tablet feature support.  Any help with this would be great.

Thanks
- Shawn

---

### Post by DoctorMO on 2008-02-11
The wacom tablet support is based in X11, the reason it works at all is that ubuntu comes with /etc/X11/xorg.conf filled with wacom configuration which works with "most" but not all Wacom tablets.

In order to configure Dead zone and other options you must edit the xorg.conf file and add in the required options as documented here:

[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

Sorry it isn't easy, tablets have been neglected and the current situation is a hack to get them working. You'll also notice that if you unplug and plug in your wacom while logged in it'll no longer be able to sense the presure in gimp.

---

### Post by Cha1n5aW on 2008-02-11
Thanks for the info, considering what I've gone through with builds like Sabayon and Backtrack, I'm no stranger to editing the xorg.conf.  Also a great tip about the unplug-replug pressure thing.  Thanks for the new sig too (^-^)

Thanks
- Shawn

42 is a product of "Deep Thought" not the universe, thus gramatically it's really Deep Thought saying 'Error 42: meaning to universe not found' or IMO 'Error 42: syntax "universe" is an invalid operator'

---

