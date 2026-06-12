---
title: "Screen Resolution"
date: 2006-10-14
forum: General Help
---

### Post by frenchfry929 on 2006-10-14
My girlfriend has a widescreen laptop with a 1280x800 resoltion, and we haven't been able to find that resolution on Ubuntu. The resolution Ubuntu is currently set to on her laptop is 1024x768. Could someone please let us know how to get the 1280x800 resolution on her laptop?:confused:

---

### Post by taurus on 2006-10-14
Have you played around with the options in 

```
sudo dpkg-reconfigure xserver-xorg
```
And before you run that command, better make a backup copy of your /etc/X11/xorg.conf in case you need it later...

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by ivanp on 2006-10-17
Hi

I have the 5.10 version and can't go higher than 1024x768, when tried 

```
sudo dpkg-reconfigure xserver.xorg
```

i got for answer

the package xserver.xorg is not installed and there is not any information avaible

might be the ubuntu version?

any help is welcome

regards

Ivan

---

