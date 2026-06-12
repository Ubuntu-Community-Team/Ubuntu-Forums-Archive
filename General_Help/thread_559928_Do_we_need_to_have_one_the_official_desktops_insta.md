---
title: "Do we need to have one the official desktops installed to upgrade?"
date: 2007-09-25
forum: General Help
---

### Post by mindtrick on 2007-09-25
To successfully upgrade an Ubuntu system do we need one of the desktops installed (Ubuntu, Kubuntu, Xubuntu)

I'm asking this because I want to install a base system first then add xorg and a light window manager or a DE like XFCE. 

How do you upgrade such a system?

---

### Post by pointone on 2007-09-25
You can edit your /etc/apt/sources.list file to point to the desired upgrade (i.e., change Edgy to Feisty or Feisty to Gusty, for example) and then simply run:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by mindtrick on 2007-09-25
Thanks a bunch. Didn't imagine it would be so easy as that.

---

### Post by yabbadabbadont on 2007-09-25
I believe that the only *supported* method of upgrading is to use the update-manager and to have one of the (x)(k)ubuntu-desktop packages installed.  The method listed previously may work, but it isn't guaranteed to.  I plan on waiting two or three weeks after release and then do a clean, minimal install, using the net installation image.

---

### Post by mindtrick on 2007-09-25
> **yabbadabbadont said:**
> I believe that the only *supported* method of upgrading is to use the update-manager and to have one of the (x)(k)ubuntu-desktop packages installed.  The method listed previously may work, but it isn't guaranteed to.  I plan on waiting two or three weeks after release and then do a clean, minimal install, using the net installation image.

That looks rational as well. Most of the time I don't keep any valuable files on my computer. I can try to upgrade, if fails, do a clean install. 

"net installation image"

Is this the server edition? I was planning to download the alternate CD. Is there a smaller option?

---

### Post by mindtrick on 2007-09-25
OK I found this. 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by yabbadabbadont on 2007-09-26
> **mindtrick said:**
> OK I found this. 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

That is the one that I use.  However, you have to skip a step in the installer if you don't want the entire ubuntu-desktop package installed.  ;)  For some strange reason, the minimal install CD does not (explicitly) allow you to install a command line only system.  For that, you have to get the alternate installation CD.  To install a command line only system with this CD, you have to perform each of the steps of the installer in order, until you get to the "Select and Install Packages" step.  Skip that one.  It doesn't let you select anything (unlike the same option in the Debian installer) but instead, downloads and installs all of ubuntu-desktop.  If you just skip that step and finish the installation, you will end up with a text only system that has ubuntu-minimal installed upon it.  To get the official command line only system, install the ubuntu-standard package once you have booted into the new system.  Then you can add/remove whichever packages you like using either apt-get or aptitude.  On a side note, be aware that aptitude, by default, installs recommended packages automatically without asking.  You can change that in the options menu of the ncurses interface.

---

### Post by Cryptog on 2007-09-26
It might be easier to just use the Ubuntu-server CD - it installs a very minimal command-line based system. From that point it would be easy to install a minimum desktop, ie: 

apt-get install fluxbox


(Xorg should get pulled in automatically when installing fluxbox).

---

### Post by rsambuca on 2007-09-26
> **Cryptog said:**
> It might be easier to just use the Ubuntu-server CD - it installs a very minimal command-line based system. From that point it would be easy to install a minimum desktop, ie: 

apt-get install fluxbox


(Xorg should get pulled in automatically when installing fluxbox).

I think the minimal installation from the alternate CD is actually a better option for desktop use.  The Ubuntu Server CD uses a kernel optimized for servers as opposed to desktop usage.

---

### Post by RedSquirrel on 2007-09-26
> **Cryptog said:**
> (Xorg should get pulled in automatically when installing fluxbox).

I'm not sure that it does. 

In any case, if you know the video driver you need, I think it's better to install xorg explicitly and specify the driver up front so that apt will only install that one.

```
sudo apt-get install xserver-xorg-video-ati xorg
```Just replace the ati with the one for your card.

With regard to kernels, if someone has installed the server edition and then wants the generic kernel, it's only an apt-get away. Pick one of:

- linux-generic
- linux-image-generic

I install the latter on my system because the former installs 'linux-restricted-modules-generic' which I don't need. ;)

---

### Post by yabbadabbadont on 2007-09-27
> **RedSquirrel said:**
> I'm not sure that it does. 

It doesn't.  I've reported it before, but the fluxbox package in the repositories does not have proper Xorg dependencies.  (I just can't remember if I reported it on launchpad though...)

```
Package: fluxbox
State: not installed
Automatically installed: no
Version: 0.9.15.1+1.0rc2-1
Priority: optional
Section: universe/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 2957k
Architecture: i386
Compressed Size: 922k
Filename: pool/universe/f/fluxbox/fluxbox_0.9.15.1+1.0rc2-1_i386.deb
MD5sum: 43c54b4310dc9941bdcbe2528c53e5d5
Archive: feisty
Depends: menu (>= 2.1.19), libc6 (>= 2.4-1), libfontconfig1 (>= 2.3.0), libgcc1 (>= 1:4.1.1-12), libice6, libsm6, libstdc++6
         (>= 4.1.1-12), libx11-6, libxext6, libxft2 (> 2.1.1), libxinerama1, libxpm4, libxrandr2, libxrender1
Suggests: fluxconf, fbpager, fbdesk, xfonts-artwiz
Conflicts: menu (< 2.1.9-1)
Provides: x-window-manager
Description: Highly configurable and low resource X11 Window manager
 Fairly similar to blackbox, from which it is derived, but has been extended with features such as pwm-style window tabs,
 configurable key bindings, toolbar, and an iconbar. It also includes some cosmetic fixes over blackbox. 
 
 This package contains support for Gnome and KDE.

```

---

