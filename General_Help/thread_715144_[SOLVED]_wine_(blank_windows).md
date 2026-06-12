---
title: "[SOLVED] wine (blank windows)"
date: 2008-03-04
forum: General Help
---

### Post by billybag on 2008-03-04
i installed wine and wine doors with no problem but when i use WINE CONFIGURATION i just get a blank window. it have a title bar, but the window is just all gray. when i try to install an exe under wine, it is the same thing. the installation process window is just a square gray box with a title bar... i can post a screenshot if anyone needs some visual...

thanks

edit: it may be worth it to mention that i am running compiz and emerald.

---

### Post by Oldsoldier2003 on 2008-03-04
> **billybag said:**
> i installed wine and wine doors with no problem but when i use WINE CONFIGURATION i just get a blank window. it have a title bar, but the window is just all gray. when i try to install an exe under wine, it is the same thing. the installation process window is just a square gray box with a title bar... i can post a screenshot if anyone needs some visual...

thanks

try deleting and reinstalling wine without wine doors (wine-doors is still beta) also you mightwantto disable wineHQ as a repo and install the stable Ubuntu version. after you get it all working if you want to play around with newer version the feel free, but its best to start with something known to work on most systems.

```
sudo apt-get purge wine
sudoapt-get purge wine-doors
sudo apt-get install wine
winecfg
```

---

### Post by billybag on 2008-03-04
it worked. it didnt work at first when i tried to bring up the config through terminal but when i tried it through apps/wine/wine config through my menu... it worked.


thanks

---

