---
title: "splash screen broken?"
date: 2008-05-04
forum: General Help
---

### Post by stubblepoo on 2008-05-04
last month i hard reinstalled gutsy and for the first time ever the splash screen, the one with the orange load bar was fuzzy. there were ghosted lines all over the place. i accepted this and knowing i would upgrade soon just let it lie, however the problem has move on into hardy too. using start up manager i changed the .so to another to see if that would fix it. now there is a new theme with the same issues but now it is also off-center as well. don't know how to fix it help would be appreciated.

---

### Post by Aearenda on 2008-05-04
Is the screen resolution set to a usable value in /etc/usplash.conf?

You need to run ```
sudo update-initramfs -u
``` after changing it, to make it take effect.

---

### Post by stubblepoo on 2008-05-04
changing the resolution made it centred again but every line still has a double 3 pixels the side.

---

### Post by Aearenda on 2008-05-04
Sounds like it's still refreshing too fast for the monitor then - but you don't get any direct control over that - I'd keep trying different resolution settings.

---

