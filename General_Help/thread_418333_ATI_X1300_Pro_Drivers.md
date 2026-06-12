---
title: "ATI X1300 Pro Drivers"
date: 2007-04-01
forum: General Help
---

### Post by jay_highlands on 2007-04-01
Hi, 

I have been trying to get the ATI driver working for a ATI X1300 pro card but without any success. 

I followed the guide below, both method 1 and method 2, the out come is always the same I get a black screen when it tries to load X. I tried the troubleshooting tips but I just got the same results. 

Has anyone managed to get the ATI drivers working with this card? Is the guide I am using the best one to follow?

My computer is a Dell Dimension E521

The guide I used : 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Thanks for any advice :)

---

### Post by Vorian on 2007-04-22
*cough*

Moved from the archived feisty forum.

---

### Post by tygr on 2007-06-11
I have the same computer (E521, ATI x1300) and have tried both methods without success on Feisty.  Using the builtin restricted driver cause X to crash to the point where a hard boot is required.  

Snip of Xorg.0.log

(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3

Using any of the ATI drivers ( 8.37.6, 8.36.5, 8.35.5, 8.34.8 ) does not cause X to crash, but 3d rendering does not work.

Does anyone have this working, especially with the Ubuntu restricted driver or have any tips?

Thanks

---

### Post by chrisN_uk on 2007-06-12
Nope, it seems that our card just doesn't work with the current drvers and xorg version. I have tried many many different guides to no avail. Its in launchpad under Bug #117013 so posting on there might speed things up a little.

---

### Post by timcredible on 2007-06-12
i'm currently running a dell with ati x1300/x1500 card at work, it works ok, although beryl was a pain to setup.  i just installed the ati driver from synaptic and it worked.  personally, i only buy nvidia cards, they're much easier to setup in linux.

---

### Post by Crafty Kisses on 2007-06-12
> **jay_highlands said:**
> Hi, 

I have been trying to get the ATI driver working for a ATI X1300 pro card but without any success. 

I followed the guide below, both method 1 and method 2, the out come is always the same I get a black screen when it tries to load X. I tried the troubleshooting tips but I just got the same results. 

Has anyone managed to get the ATI drivers working with this card? Is the guide I am using the best one to follow?

My computer is a Dell Dimension E521

The guide I used : 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Thanks for any advice :)

I've been having so much trouble installing my NVIDIA Drivers, it's pretty insane, but other than that Ubuntu is a great OS, and I'll stick with it. :D

---

### Post by RedSquirrel on 2007-06-12
> **chrisN_uk said:**
> Nope, it seems that our card just doesn't work with the current drvers and xorg version. I have tried many many different guides to no avail. Its in launchpad under Bug #117013 so posting on there might speed things up a little.
Have you tried this guide:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

??

It may be no different than the others or maybe you have already tried it, but I just thought I'd mention it just in case.

---

