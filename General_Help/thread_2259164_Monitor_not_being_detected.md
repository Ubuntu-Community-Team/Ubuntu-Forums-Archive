---
title: "Monitor not being detected"
date: 2015-01-02
forum: General Help
---

### Post by wovoka on 2015-01-02
Installed ubuntu, and the only monitor detected is the one that is plugged into my integrated graphics card. The other two that are connected to my NVIDIA graphics card are not being detected by ubuntu at all.

I tried to google for an answer but ultimately find nothing useful

1)  Additional drivers shows nothing (Meaning i have nvidia drivers?)

2) Nvidia x server settings doesn't work for me. I installed it and only application profiles and nvidia settings configuration menus appear. Nothing that allows me to get my monitors to work.

Frustrated beyond belief. Why is everything so utterly broken on ubuntu?

---

### Post by deadflowr on 2015-01-02
What's 
```
lspci
```
show
Please post
It'll be a good starting point, to better understand what cards are in the mix.

---

### Post by grahammechanical on 2015-01-02
> [COLOR=#000000]Why is everything so utterly broken on ubuntu?[/COLOR]

That is not accurate. You have hybrid graphics so do not blame Linux developers when It was Nvidia that took more than a year to produce a Linux driver that did anything thing with Nvidia's Optimus technology. And even then it does not match up with what you get under Windows.

What version of Ubuntu are you using? To get anywhere with Nvidia drivers in a hybrid graphic setup you need Ubuntu 14.04.1 at least. Nvidia Xserver settings utility is installed when the Nvidia driver is installed. It may have a "detect monitors" function. Have you set the BIOS/UEFI to work from the Nvidia adapter and not the integrated video adapter? When using the integrated video adapter then we will be using the video driver for that adapter (usually Intel). IN this case we can use System Settings>Displays to detect monitors.

Additional Drivers will only show video drivers if we are connected to the Internet because the drivers are proprietary. Additional drivers will show the driver installed as well as four alternatives including an open source driver.

---

### Post by wovoka on 2015-01-14
[http://i.imgur.com/COym3Ow.png](http://i.imgur.com/COym3Ow.png)

---

