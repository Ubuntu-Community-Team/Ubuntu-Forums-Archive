---
title: "X server won't start after driver install"
date: 2007-07-11
forum: General Help
---

### Post by themerchant on 2007-07-11
I just bought a new video card (nvidia 8800 320 mb) and new harddrive. So I reinstalled ubuntu, then let ubuntu  install 3d drivers for me. I rebooted and xserver had failed. I realize I should've installed the drivers from nividia's site itself, because this is a new video card and it would've had better support, now how do I disable that 3d driver without the xserver?

---

### Post by themerchant on 2007-07-11
bump!

---

### Post by confused57 on 2007-07-11
Press "Ctrl+Alt+F1" when you get the xserver error message...login...then enter:
```
sudo /etc/init.d/gdm stop
```
then
```
sudo dpkg-reconfigure xserver-xorg
```
you can probably go with the defaults for most screens, but choose "vesa" or "nv" for your video driver...when you're finished, enter:
```
startx
```
if this doesn't work, then:
```
sudo /etc/init.d/gdm start
```

With your newer nvidia card, you might want to read through this thread:
[http://ubuntuforums.org/showthread.php?t=495464](http://ubuntuforums.org/showthread.php?t=495464)

I think there are instructions by bodhi.zazen for removing the nvidia drivers that you've already installed and he's provided instructions for installing the new nvidia drivers from the Nvidia site.

---

