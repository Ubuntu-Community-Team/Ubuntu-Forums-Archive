---
title: "Black login screen for 12.04"
date: 2013-02-20
forum: General Help
---

### Post by CatKiller on 2013-02-20
The other half has just upgraded from 10.04 to 12.04. Upgrade seemed to go smoothly but on boot the higher-res splash screen comes up nicely then just black. It's not possible to login blind, which suggests to me that there's no login manager there rather than it being there and being at the wrong resolution or whatever.

If I ssh from my machine I can ```
sudo service gdm start
``` and up it comes (no error messages or the like) which shows that there's nothing fundamentally wrong with the graphics system - just no login screen on boot.

It's moderately old and running some kind of onboard Intel graphics, if that helps. I can list more if it's necessary.

Any pointers?

---

### Post by CatKiller on 2013-02-20
In the end I did a ```
sudo dpkg-reconfigure gdm
``` and set GDM as the login manager rather than LightDM. Seems to have done the trick, although it's something of a sledgehammer solution.

---

