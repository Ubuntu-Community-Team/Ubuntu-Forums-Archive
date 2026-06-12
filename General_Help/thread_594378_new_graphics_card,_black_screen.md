---
title: "new graphics card, black screen"
date: 2007-10-27
forum: General Help
---

### Post by Digitallysick on 2007-10-27
I got a new ati graphics card, but i get just a blackscreen, how can i fix it? or at least get to fail safe

---

### Post by taurus on 2007-10-27
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
When you are done, reboot with

```
shutdown -r now
```

---

### Post by Digitallysick on 2007-10-27
i had to find the /etc/X11/xorg.failsafe , and rename it to xorg to at least get failsafe back, i can install the ati driver for my ati X1960 through envy, but still can't get out of failsafe, when i check "use restrictred driver and i restart, i get a black screen, sorry for typos im in failsafe now and cant read the screen

---

### Post by Digitallysick on 2007-10-28
i used envy to install the driver, but when i restart, i get the failsafe options box, so for now fail safe is all i have, can someone post an xorg.conf with a working X1950 ati card?

---

