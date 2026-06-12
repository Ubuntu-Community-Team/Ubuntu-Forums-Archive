---
title: "Resolution will not change to 1280x800 even after manual reconfiguration of xorg.conf"
date: 2007-07-04
forum: General Help
---

### Post by Kodfish on 2007-07-04
Installing on my mom's old laptop, but ubuntu will not go past 1024x768, even after a dpkg-reconfigure xserver-xorg.

Any ideas?

---

### Post by FuturePilot on 2007-07-04
```
gksudo gedit /etc/X11/xorg.conf
```
Go towards the bottom where it lists all of the resolutions and add your resolution to the beginning of each line so it looks something like this```
Mode    "1280x800" "somethingxsomething" "somethingxsomething"
```
Save then restart X.

---

### Post by Kodfish on 2007-07-04
Been done. I've manually hacked the xorg config, and after that failed i moved over another xorg.conf with identicle video settings. I'm trying an update right now, but i don't think old software is the issue. The "Screen Resolution" tool in System > Preferences will only allow me to choose 1024x768 regardless of what is in xorg.conf.

---

### Post by confused57 on 2007-07-04
> **Kodfish said:**
> Been done. I've manually hacked the xorg config, and after that failed i moved over another xorg.conf with identicle video settings. I'm trying an update right now, but i don't think old software is the issue. The "Screen Resolution" tool in System > Preferences will only allow me to choose 1024x768 regardless of what is in xorg.conf.
What video card and video driver in xorg are you using?

If you're not sure, post the output of:
```
lspci
```

---

