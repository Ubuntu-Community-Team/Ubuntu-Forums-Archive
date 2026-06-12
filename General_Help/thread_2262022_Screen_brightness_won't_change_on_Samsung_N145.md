---
title: "Screen brightness won't change on Samsung N145"
date: 2015-01-22
forum: General Help
---

### Post by lisa5 on 2015-01-22
I downloaded Lubuntu 14.10 on my Samsung N145 netbook and the screen brightness won't change. The fn keys to change the brightness work but it doesn't change the actual brightness when I use them.

Thanks!

---

### Post by janimattitirkkonen on 2015-02-03
Are you able to you change the screen brightness by using xbacklight?  

```
sudo apt-get install xbacklight
```

and 

```
xbacklight =<percentage>
```, e.g. ```
xbacklight =10
```

Almost all the fn keys on my Samsung NP-N150 work after I added the repository [https://launchpad.net/~voria/+archive/ubuntu/ppa](https://launchpad.net/~voria/+archive/ubuntu/ppa) and installed samsung-tools.

EDIT: It seems that there is no samsung-tools for Ubuntu 14.10. However, following [this instruction]("https://wiki.archlinux.org/index.php/Samsung_N150#Backlight") from the Archwiki solved the problem for me (using Lubuntu 15.04):

Add the following in /etc/X11/xorg.conf.d/20-intel.conf:```

Section "Device"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        Identifier "card0"
EndSection

```

---

