---
title: "Graphics issue can't log into Xubuntu"
date: 2012-12-20
forum: General Help
---

### Post by desesperado on 2012-12-20
Hi. I hope you'll be able to help me. I have a Toshiba Tecra A7 dual-booting Windows XP Professional with Xubuntu 12.10, and today I've made a mess in it when trying to update me ATI Radeon Mobility X1400 graphics driver.

What I did is that I tried to install the lastest drivers for Linux from the ATI site and couldn't do it, so I went to Synaptics and tried to install fglrx but after rebooting I manage to go as far as the grub but whern I select ubuntu the monitor just remains black and Xububtu doesn't start

Can you help me?

---

### Post by desesperado on 2012-12-20
I've tried to follow [effenberg0x0 post]("http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati") but when I get to Wait for the download to finish and run:
Code:
```
sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric
**sudo dpkg -i ati*.deb**
sudo aticonfig --initial -f
``` when I enter the command sudo dpkd -i ati*.deb I get a message saying:

**dpkb: error processing ati*.deb (--install): cannot access archive: No such file or directory**

And I don't know what to do know. Won't somebody be able to help me, please

---

### Post by desesperado on 2012-12-20
> **desesperado said:**
> I've tried to follow [effenberg0x0 post]("http://ubuntuforums.org/showthread.php?t=1857059&highlight=effenberg+ati") but when I get to Wait for the download to finish and run:
Code:
```
sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/oneiric
**sudo dpkg -i ati*.deb**
sudo aticonfig --initial -f
``` when I enter the command sudo dpkd -i ati*.deb I get a message saying:

**dpkb: error processing ati*.deb (--install): cannot access archive: No such file or directory**

And I don't know what to do know. Won't somebody be able to help me, please

Just wanted to say that the only thing I've made different was:
sudo sh ati-driver-installer-11-9-x86.x86_64.run --buildpkg Ubuntu/quantal instead of Ubuntu/oneiric

---

### Post by desesperado on 2012-12-20
Pretty please, with sugar on top!

---

### Post by ajgreeny on 2012-12-20
That card will only work with the open source radeon driver that you should have got at installation.  Any attempt to install the catalyst fglrx driver from any other source will fail, I'm afraid, so you need to uninstall any driver you have added, and then delete any /etc/X11/xorg.conf file you have and run with the radeon driver.
```
sudo apt-get remove fglrx
```if you have not already done so, from a command line if necessary, then try a reboot.

---

### Post by desesperado on 2012-12-20
> **ajgreeny said:**
> That card will only work with the open source radeon driver that you should have got at installation.  Any attempt to install the catalyst fglrx driver from any other source will fail, I'm afraid, so you need to uninstall any driver you have added, and then delete any /etc/X11/xorg.conf file you have and run with the radeon driver.
```
sudo apt-get remove fglrx
```if you have not already done so, from a command line if necessary, then try a reboot.

I've remove fglrx as you explain but in /etc/X11/ there was no xorg.conf.
 
Can you help me further more and tell me what to do now?

---

### Post by desesperado on 2012-12-20
Now I'm stuck with a poor resolution 1024x768 with a refresh rate of 61Hz.

How do I install the open source radeon drivers drivers, after I have removed fglrx?

---

### Post by slickymaster on 2012-12-20
If you already manage to log into your system (at least that's what is understood in your last post) open a terminal and type:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
That way you'll update your drivers once they are already installed, otherwise you wouldn't have logged in.

---

