---
title: "installing ubuntu 14.04 parallel desktop with mac and install nvidia &amp; intel drivers"
date: 2014-11-29
forum: General Help
---

### Post by AbhimanyuAryan on 2014-11-29
I want to install Ubuntu 14.04 in my Macbook pro retina 15 inch but without installing nvidia and intel drivers, ubuntu looks very ugly. I want to improve these graphics. Also i want to keep using OSX as my primary laptop. So, I am installing ubuntu in parallel with OSX. I don't want to partition my only single 512 gb SSD on mac. Is it possible to install graphic drivers? So, ubuntu look a little good with retina.

---

### Post by grahammechanical on 2014-11-29
Please explain how you intend to install Ubuntu "in parallel with OSX" but without partitioning the 512GB SSD. Where will you be installing Ubuntu to? Please also describe the graphic adapters in that machine. Is it Intel? Is it Nvidia? Or both?

Unless we are using a machine without a monitor as a server we will need a video driver. When we install Ubuntu if we tick the box "Install third party software" a proprietary video driver will be installed. If we do not tick that box then Ubuntu will be installed using the default open source video driver, which with Nvidia graphic adapters is called Nouveau.

If all we have in the machine is an Intel graphic adapter then an open source video driver provided by Intel will be used. 

[http://www.omgubuntu.co.uk/2012/06/what-does-ubuntu-look-like-on-a-retina-display-bad](http://www.omgubuntu.co.uk/2012/06/what-does-ubuntu-look-like-on-a-retina-display-bad)

[http://www.omgubuntu.co.uk/2014/02/ubuntu-14-04-high-resolution-retina-screen](http://www.omgubuntu.co.uk/2014/02/ubuntu-14-04-high-resolution-retina-screen)

To use scalling in Ubuntu 14.04 if we are using Nouveau (as I am) go to System Settings>Screen Display and there we will find a slider and we can set the scale for Menus and Title bars. We can also Scale all windows contents to match either Display with largest controls or Display with smallest controls.

At System Settings>Appearance we can also adjust the Launcher icon size.

If we install an Nvidia driver then it will come with its own settings manager. What we can do with that I do not know.

[http://www.makeuseof.com/tag/install-linux-macbook-pro/](http://www.makeuseof.com/tag/install-linux-macbook-pro/)

Regards.

---

