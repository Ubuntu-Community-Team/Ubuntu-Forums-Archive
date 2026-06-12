---
title: "Help with OpenGL / ATI video card"
date: 2007-05-02
forum: General Help
---

### Post by ideswa on 2007-05-02
Hi,

I have a 128 mb ATI radeon 9600 video card, I have installed apt-get install xserver-xorg-video-ati, and my xorg.conf seems all right:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

But I get very slow, FPS (with Ubuntu games, like gl-117. How can I fix it? I have tried to install the driver from the ATI site, but that didn't help either.

---

### Post by BPilgrim on 2007-05-03
Hopefully this will help: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by ianprinz on 2007-05-03
This guide might also help [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

