---
title: "How to activate the vertical synchronization ?"
date: 2015-06-07
forum: General Help
---

### Post by michel15 on 2015-06-07
[FONT=arial]Hi,
I'm on ubuntu 14.04 LTS and i have a nvidia Geforce 820M. Since the beginnig,when I watch videos, there is striation. After searches, the cause is the vertical synchronization. But when I go in nvidia settings, The compartment which allows to activate it does not appear. How I need to do ?

Sorry for my english (i'm french) et thank you.[/FONT]

---

### Post by Keith_Helms on 2015-06-07
Is this a laptop with Optimus graphics (dual Intel and Nvidia GPUs)?  If so, unfortunately you can't enable vsync when using the Nvidia card.

---

### Post by michel15 on 2015-06-08
Yeah I think, i have a Intel core i7 and a nvidia geforce, but there are not other solutions?

---

### Post by Keith_Helms on 2015-06-08
The only way I've gotten my laptop to play videos relatively tear free  is to uninstall the Nvidia drivers and run using only the Intel GPU.  If  you use Nvidia Prime to switch to the Intel GPU (Power saving instead  of performance), these is a xorg bug that causes the xorg.conf file to  get renamed at every boot, so you can't use xorg.conf with Nvidia Prime.

If you  remove the Nvidia drivers and Prime and use only the Intel GPU, then you can use  an xorg.conf file and add the Tearfree option to it.  I have my laptop  set up to dual boot Xubuntu 14.04 with the Nvidia drivers and Nvidia  Prime installed and Ubuntu 14.04 with no Nvidia drivers installed.  This  is the xorg.conf file I use on the Ubuntu install:
```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
    Option "Tearfree" "true"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

```

Sorry this isn't a simple solution.  Support for hybrid graphics also known as Nvidia Optimus is better than it was a couple of years ago, but it's still not perfect.  Until Nvidia releases a driver that allows you to set vertical sync to blank for systems with these types of graphics, videos played on them will not look as good as they should.

---

