---
title: "[SOLVED] Install eduntu on Ubuntu with the edubuntu cd?"
date: 2007-08-25
forum: General Help
---

### Post by DamjanDimitrioski on 2007-08-25
Hi, i want to install only the programs from edubuntu, on my Ubuntu Feisty Fawn 7.04, or is there any update options, or something to make ubuntu to edubuntu, without internet connection?

---

### Post by Darkhack on 2007-08-25
Unfortunately you need at least one box that does have a connection on it.  Then you can use APTonCD to create a .deb with all the edubuntu packages and transfer it over to the other machine with either a CD or USB flash drive.

---

### Post by flipjarg on 2007-08-25
You could go about it like this:

Put in the Edubuntu CD and type...
```
sudo apt-get install edubuntu-desktop
```

and then type


```
[color=red]*This is optional[/color]
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

It will give you the edubuntu desktop environment and apps.

---

