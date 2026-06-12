---
title: "Printing to LX-310 from Wine Issue"
date: 2021-08-28
forum: General Help
---

### Post by amidis on 2021-08-28
I have a Win32 POS application that need to print receipt to Epson LX 310 printer using RAW ASCII text. In Windows the receipt printed nicely, but when I ran it in a station (running lubuntu + Wine), the printed receipt cannot print ASCII extended characters. I got garbled chars instead of lines made using ASCII 196.


Any idea how to solve this issue? I haven't change any default printer setting (just plug in USB port, and that's it).

Edit:
It also appears the printed receipt always missing a couple of characters in leftmost. I'm not sure it's paper size problem since RAW print should not affected by paper size.

---

### Post by grahammechanical on 2021-08-28
A Windows program will be using Microsoft fonts which are not installed in Ubuntu. But there is a way to download and install a set of Microsoft True Type fonts and it is not illegal.

[https://linuxconfig.org/install-microsoft-fonts-on-ubuntu-20-04-focal-fossa-desktop](https://linuxconfig.org/install-microsoft-fonts-on-ubuntu-20-04-focal-fossa-desktop)

There is one catch to doing this. At some point the installation will pause to allow us to tick that we have accepted the Microsoft End User License Agreement. If we do not tick either the "yes" or "no" box the install will hang there. So, do not leave the installation unattended. The mouse will not work with the dialog box that is presented. So, use the tab key to move to the box you wish to tick.

Regards

---

### Post by amidis on 2021-08-28
I believe RAW print doesn't need any font since font used will be printer built-in fonts (any dot-matrix have machine font)

---

### Post by amidis on 2021-08-30
Just got answer from LXQ forum, it appears the printer must be set to print using RAW driver. Solution provided in this link:
[https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux](https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux)

---

