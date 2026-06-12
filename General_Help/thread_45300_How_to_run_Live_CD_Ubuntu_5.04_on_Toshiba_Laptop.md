---
title: "How to run Live CD Ubuntu 5.04 on Toshiba Laptop?"
date: 2005-06-29
forum: General Help
---

### Post by wuselbox on 2005-06-29
Hi,

I want to test Ubuntu Linux 5.04 on a Toshiba Notebook, its model number is M30X165. 
The problem is, that it sooner or later hangs up during booting. I tried to vary kernel parameters during boot screen but this doesn't help. The farest level i reached was booting gnome while system hang up.

The hardware specs of my notebook are (as I know) the following:

CPU: Intel Centrino 1.6
RAM: 1 GB DDR
Harddrive: 80 GB Toshiba 4200 rpm
Graphic chip: ATI Mobility Radeon 9700 128Mo (M11)
Ethernet Chip: Realtek RTL8139
WiFi Chip: Intel Pro/Wireless 2200BG
Sound Chip: Realtek AC97 Audio
PCMCIA Controller: ENE CB-714 (compatible Yenta)
IEEE 1394 Controller:  VIA OHCI
DVD Drive: Matshita DVD-RAM UJ-831S
IrDA: SMSC IrCC
Touchpad: ALPS

Can someone tell me how to start from the live cd with this toshiba? I want to try first if all the hardware is supported and will be identified by the kernel before i do a harddisk installation.

Thank you for assistance!

Sascha

---

### Post by henriette_holm on 2005-07-07
Have you tried checking the md5sum of the cd - or is it an "official" one? You could try downloading it againg or even try another dist. live cd.

-Henriette

---

### Post by wuselbox on 2005-07-11
Hi Henriette,

no I haven't compared the md5sum. I downloaded the dvd-image with bittorent and trusted on the chunks check by bittorent.
well, it also seems to me, that not the image is the problem than some hardware issue. because as i tried the first boot with this dvd-image and entered no kernel parameters, the system hang up in a very early stage.
with all the additional kernel parameters (e.g. vga=771, noacpi, nolapi ...) the system reached the gdm-start sequence but freezed at it.

maybe i still wait until i receive the official cd package by mail.

have you already installed ubuntu on this kind of laptop? experiences during install would be interesting for me.

sascha.

---

