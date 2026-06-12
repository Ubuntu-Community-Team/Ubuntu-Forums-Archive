---
title: "Boot to Terminal"
date: 2021-11-07
forum: General Help
---

### Post by jekep2008 on 2021-11-07
Hi I’m working with an older PC with 14.04LTS. Installed when logging into the main account it would log in and show a blank desktop mouse and keyboard would still work after messing around in the terminal for a bit playing with files X.Authority and lightgdm possibly? I believe I messed something up because now it’s booting to terminal asking for credentials the only way to get to the GUI is running “startx” and then it takes me to an empty desktop where mouse keyboard work and I can get into the settings the HDD is nearly full which I believe is causing some of these issues if someone could possibly help me out that be great!

---

### Post by grahammechanical on 2021-11-07
Here is a little bit of help.


At the Grub boot menu select Advanced options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Clean - Try to make free space. That may help just a little bit.

What user interface is 14.04 using? If it is Unity 7 then LightDM would be the display manager. If the user interface is Gnome 3 shell then the display manager is GDM3

Regards

---

### Post by ajgreeny on 2021-11-07
Is it really worth fussing with 14.04, I think not.

Just download a new version, eg 20.04 and make a clean install after bac,ing up any files you need to keep, but perhaps using a lower resource DE version such as Mate or Xubuntu if your hardware is  a bit older  as Ubuntu requires fairly high specs to run well.

---

