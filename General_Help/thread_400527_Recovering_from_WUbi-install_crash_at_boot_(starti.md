---
title: "Recovering from WUbi-install crash at boot (starting the graphical shell)"
date: 2007-04-03
forum: General Help
---

### Post by cro on 2007-04-03
This is a little bunch of tips for working with Feisty 7.04 beta under wubi that I've figured out through trying to get Ubuntu working on various hardware platforms/configurations. One thing wubi has really allowed if the ability to play with installations, trying new things out, wiping and easily re-starting if needed.

One of the biggest problems I've had is with proprietary drivers for my ATI X1950, especially as that machine has a dual0head configuration with a secondary dual-head Matrox card in it. Unfortunately installing fglrx and the proporietary drivers regularly cause a full system crash at boot, forcing a power down or a motherboard BIOS reboot (alt-sysreq-b) to restart.

To help debugging, i modifed the wubi-installed changes to menu.lst in the following way. This file is located at the root of your C: drive:

```
#### MENU ITEMS BELOW HERE ####

title Ubuntu
find --set-root /wubi/linux
kernel /wubi/linux find=/wubi/linux quiet ro **single**
initrd /wubi/initrd.gz
boot
```Adding the word **single** to the end of that line forces Ubuntu to stop booting once you get to the first login prompt (as root). This means that you will need to manually boot into Xorg (the graphical shell). To do this, type the following:```
telinit 3
```You can also use the following instead:```
startx
```The reason for this is that stopping the boot at this point gives you access to configuration files to repair X to stop X fro loading any broken drivers (usually ATI drivers :) ) that are incompatible with the version of Ubuntu you are installing.

The configuration file you want is this one:```
/etc/X11/xorg.conf
```Typically, if you boot Ubuntu under a wubi install and, after going through the boot process your monitor vaguely flashes, then switches off and pressing ctrl+alt+backspace does not give you a text prompt, you will need to reboot and change xorg.conf to use a different video driver.

The safest is 'vesa', so at the boot prompt, type ```
vi /etc/X11/xorg.conf
``` (or, if you have logged in with your username+password, ```
sudo vi /etc/X11/corg.conf
```) and change any instance of 'fglrx' to 'vesa'. Once you've changed the setting back, you should be able to run startx to start the Ubuntu window manager to keep installing, updating or doing whatever.

Hope this is of some help.

---

### Post by dc_atkinson on 2010-02-24
Hi,

I have a similar problem and am trying to exit the xorg.conf file.  However, it doesn't exist - there is no such file in /etc/X11.    I have used the wubi installer.  I am not sure if Xorg just doesn't have a config file.   

What should I do?  The problem I am having is with my monitor so want to edit the xorg.conf file.   Perhaps I can just create one from a template and put in /ext/X11 ??

Thanks

---

