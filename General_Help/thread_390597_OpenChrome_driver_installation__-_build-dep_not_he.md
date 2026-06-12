---
title: "OpenChrome driver installation  - build-dep not helpful"
date: 2007-03-22
forum: General Help
---

### Post by catnap on 2007-03-22
Hello,

I quite new to this game and am trying to install an Openchrome driver, as I have a VIA chipset which is running painfully slow under the default vesa driver.  

I am following the instructions at:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

The first of these is to get the build dependencies for the driver which I attempted: 

sudo apt-get build-dep xserver-xorg-video-via
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for xserver-xorg-video-via could not be satisfied.

This is not real helpful - xserver-xorg-video-via and it&#347; dependent packages are installed, so I think what this means is that the source dependencies cannot be satisfied - but shouldn´t the user be told which ones?

I´m really not sure where to go from here - any help would be much appreciated

---

### Post by catnap on 2007-03-23
This problem was fixed (essentially by trial and error) by setting the flags in Synaptic>Repositories> InternetUpdates so that Inmportant security updates, and more likely Recommended Updates were set.

The Openchrome installation procedure referrenced above then worked like a charm.

I still reckon build-dep could have been more helpful, and identified missing dependencies, thus saving heaps of time, and allowed a more logical approach to problem solving.

---

