---
title: "HP Spectre x360 Laptop - Black Screen After Installing Ubuntu Studio 24.10"
date: 2024-11-20
forum: General Help
---

### Post by spiritwind on 2024-11-20
[SIZE=4]Hi, [COLOR=#0C0D0E][FONT=-apple-system]I have a high-end HP Spectre x360 2-in-1 Laptop (16-aa0006nl). Every time I try to install Ubuntu Studio 24.10, I get a black screen on boot, and I end up having to reinstall Windows. It seems like my graphics cards aren&#8217;t being recognized. It&#8217;s a shame because I love Ubuntu Studio and all the extra capabilities it offers compared to Windows.[/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]The installation happens perfectly and then I get black screen after rebooting.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I also tried installing version 24.04 and had similar issues.[/FONT][/COLOR]
[/SIZE][COLOR=#0C0D0E][FONT=-apple-system][SIZE=4]Does anyone know how to fix this? Should I wait for the next release?[/SIZE]

[/FONT][/COLOR]if I update from 24.0.1 it works... but I had problems with qjack and my sound card, only the nvidia video card is detected by Jack and there is no way to change it, I tried many attempts but in the end I gave up so I uninstalled Ubuntu Studio 24.10 and put Windows again.. I'm so sad, with my old pc it worked fine, I hope they do an update and fix all the bugs
Thanks for any help!



----------------------------------------------------
SPECS:

PROCESSOR:
Name                           Manufacturer NumberOfCores NumberOfLogicalProcessors
----                           ------------ ------------- -------------------------
Intel(R) Core(TM) Ultra 7 155H GenuineIntel            16                        22

MOTHERBOARD:
Product Manufacturer SerialNumber
------- ------------ ------------
8C17    HP           PTMFR028JJB05W

RAM:
  Capacity Manufacturer PartNumber           Speed
   -------- ------------ ----------           -----
16GB         SK Hynix     H58G66BK7BX067        7467mhz/s
16GB         SK Hynix     H58G66BK7BX067        7467mhz/s

SSD:
Model                                  Size Manufacturer           SerialNumber
-----                                  ---- ------------           ------------
WD PC SN810 SDCPNRY-1T00-1006 1024203640320 (unità disco standard) E823_8FA6_BF53_0001_001B_448B_476E_6B1C.

GRAPHIC CARDS:

Name                               AdapterRAM
----                               ----------
NVIDIA GeForce RTX 4050 Laptop GPU 4293918720
Intel(R) Arc(TM) Graphics           134217728

---

### Post by grahammechanical on 2024-11-20
Why do you need to re-install Windows? You should be able to boot Windows from the UEFI settings utility. It seems that you are not dual booting Ubuntu Studio with Windows. Why not?

When you install Ubuntu Studio do you get asked if you want third party software to be installed as well? If you tick that box a proprietary video driver will be installed and that may be causing the problem. You have two video adapters - Nvidia GeForce RTX 4050 and Intel Arc. Try installing without ticking the box to install third party software. Then the first boot after installing will load Ubuntu studio using an open source video driver. Get a working operating system using the Intel video adapter and then try getting a working operating system using the Nvidia GeForce RTX 4050.

The problem is the hybrid graphics system.

Regards

---

### Post by spiritwind on 2024-11-21
it worked, I installed ubuntu 24.10 by unchecking third-party software but I still have the problem that when I insert my sound card and press boot in jack, even though I have set the external sound card to 192k it is automatically set at startup the nvidia graphics card at 48k.. how do I solve it?

[[img]https://i.postimg.cc/McHFdwVX/Whats-App-Image-2024-11-21-at-20-50-22.jpg[/img]](https://postimg.cc/McHFdwVX)

[[img]https://i.postimg.cc/ZWVQ8n91/Whats-App-Image-2024-11-21-at-20-50-22-1.jpg[/img]](https://postimg.cc/ZWVQ8n91)

---

