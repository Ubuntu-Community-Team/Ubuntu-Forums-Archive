---
title: "Install nVidia driver (GeForce PCX 5300) failed."
date: 2006-11-07
forum: General Help
---

### Post by realtiger on 2006-11-07
I have just installed nVidia driver by following this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After pressing Ctrl-Alt_BackSpace, I got an error: can't detect device at PCI:1:0:0
Now, there is only a black screen with a login prompt. :???: 

Any one helps me?

---

### Post by Paul41 on 2006-11-07
You reset you drivers by running:
```
sudo dpkg-reconfigure xserver-xorg
```
You should just be able to press enter on each selection until you get to the video driver selection. There choose the nv driver. This  should allow you to log in, but without the nvidia driver.

If you post you xorg file someone might be able to help you get the nvidia drivers working.
```
gedit /etc/X11/xorg.conf
```

---

