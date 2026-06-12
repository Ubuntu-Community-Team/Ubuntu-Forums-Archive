---
title: "3d rendering issues after update"
date: 2007-04-06
forum: General Help
---

### Post by UpperNinety89 on 2007-04-06
I'm getting some odd problems after updating my nVidia / x.org binary drivers from the repositories. The first one i noticed when I was toying around with my screensaver options. A few basic, 2D screensavers still work correctly, but any that use any 3d rendering of any kind just don't work. Another issue that I just noticed now that I'm typing in a text box is that when I use the arrows to go back and fix a typo, the text bar leaves an echo image of itself after each letter. This may have been around before the update, I'm not sure, but I do know that the 3D rendering is a new error.

For your information, I'm running an nVidia GeForce 6200 PCI-E card and I just isntalled the nVidia-glx package v1.0.8776 + 2.6.17.7 x.org driver.

---

### Post by UpperNinety89 on 2007-04-06
Oh and yeah, its 6.10 Edgy Eft

---

### Post by UpperNinety89 on 2007-04-07
Any help at all?

---

### Post by Nachimir on 2007-04-07
A number of people including me have had problems with nvidia drivers after a recent update interfered with them.

I suggest checking your /var/log/Xorg.0.log to see if GLX is loading. Also see these threads: [1](http://ubuntuforums.org/showthread.php?t=403164) - [2](http://ubuntuforums.org/showthread.php?t=402185) - [3](http://ubuntuforums.org/showthread.php?t=400989)

---

