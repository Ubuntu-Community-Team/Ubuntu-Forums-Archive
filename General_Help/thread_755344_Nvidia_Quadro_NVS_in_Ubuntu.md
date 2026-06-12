---
title: "Nvidia Quadro NVS in Ubuntu"
date: 2008-04-14
forum: General Help
---

### Post by zeeple on 2008-04-14
I have a dell workstation that has been running Fedora (6, 7, and 8, in that order) with my current graphics cards with dual monitors for many months very happily.  I decided to give Ubuntu a try and installed in some free space on the drive.  I am having a difficult time getting Ubuntu to handle my card well.  Here is my card:

Nvidia Quadro NVS 285.

The OS does not recognize the card automatically, and I have tried selecting Nvidia Legacy to see if that would help. When I use that built in driver, I have one monitor with an acceptable resolution, but when I choose to enable dual monitors, I get mirrored monitors with a resolution of 800x600, and a warning that I am in low graphics mode.

I have downloaded the Nvidia linux drivers and went to install them from the command line but get the error that I needed to install the libc development package. libc is already installed, though.  Has anyone here already gotten their ubuntu install to work with this card?  I'd appreciate any advice. Thanks.

---

### Post by zeeple on 2008-04-15
I figured this out:

For Nvidia Quadro NVS Cards your best bet is going to be to download the following app: 'Envy' and run it. Once installed, run it, selecting the appropriate card. Then, from a terminal do: 'gksudo nvidia-settings' and configure the card how you please. If you just run the nvidia-settings app from the Applications menu you will find, after spending time tweaking the settings, that the program will not be able to save the settings to the xconfig file. This is because you did not launch the app as root. This is the need to launch it via gksudo.

---

