---
title: "Flash problems with gutsy 7.10"
date: 2008-02-18
forum: General Help
---

### Post by Moonfrost on 2008-02-18
I'm having a probem primarily with youtube videos, it seems every time I want to go into full screen instead of just going into it the normal way with the caption buttons (like pause and play etc) it opens a little windows on the lower left corner of the screen which I have to maximize to watch and it doesn't allow me to rewind, pause and such. I been having this problem for like a month now, tried re-installing both flash plugin non=free and flash player non-free and no luck...anybody know what could be causing this?

---

### Post by Curtisc on 2008-02-19
Do you have compiz installed?  Check out this thread:
[http://ubuntuforums.org/showthread.php?p=4362867](http://ubuntuforums.org/showthread.php?p=4362867)
- Basically, go to System->Advanced Desktop Effects Settings, click on "Workarounds", and uncheck "Legacy Fullscreen Support".  If you don't have the Advanced Desktop Effects menu option, you get it by installing "compizconfig-settings-manager"

If you're not using compiz, then I'm not sure what is causing your problem...

---

### Post by Moonfrost on 2008-02-19
> **Curtisc said:**
> Do you have compiz installed?  Check out this thread:
[http://ubuntuforums.org/showthread.php?p=4362867](http://ubuntuforums.org/showthread.php?p=4362867)
- Basically, go to System->Advanced Desktop Effects Settings, click on "Workarounds", and uncheck "Legacy Fullscreen Support".  If you don't have the Advanced Desktop Effects menu option, you get it by installing "compizconfig-settings-manager"

If you're not using compiz, then I'm not sure what is causing your problem...

Without compiz it works perfectly, but when I turned it on and unchecked the option you said the full screen window appears for one second and it disappears...

---

### Post by Curtisc on 2008-02-20
That is very strange.  It does seem that compiz is the root of the problem, although why the workaround doesn't work for you is a mystery to me.  I'm afraid I'm not going to be of much more help - I filed a bug about it ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/193375](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/193375)) but apparently it's already fixed in Hardy.

---

