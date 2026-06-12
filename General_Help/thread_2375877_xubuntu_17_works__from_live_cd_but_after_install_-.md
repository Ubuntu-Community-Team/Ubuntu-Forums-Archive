---
title: "xubuntu 17 works  from live cd but after install -  a black square on 90% of desktop"
date: 2017-10-28
forum: General Help
---

### Post by montagproject on 2017-10-28
I have installed xubuntu 17 on an old HP 530 laptop (which was before  running windows vista). The problem that I have with the installation is  the following. When I run Xubuntu 17 from a live CD ("Try" mode). My  screen resolution is detected normally, the picture is sharp and clean.  But when I perform the install, after login I have a weird effect of having a  black square, filling around 90% of the screen (top left) - and  underneath the system seems to work perfectly, and the uncovered part of the  screen (a strip on the right and on the bottom) looks normal. But there  is no way to remove the black part of the desktop, and with movement of  the mouse the part seems to be filling with some very scrambled  characters. They appear also during boot, right before the login.

  How can I get the Live CD "Try" settings to work with the installed Xubuntu???
  I tried to look for various post like "black screen after login" but  nothing quite describes my case. In recovery mode system boots but the  image is blurry and distorted (forced down to 1024x...). One more thing. Inserting nomodeset into boot config, also boots xubuntu into this lower blurred resolution, but then no way to convince the system to try switching to 1280x800 (which is the correct resolution for this machine)

I'm puzzled....

---

### Post by ajgreeny on 2017-10-28
Is your version of Xubuntu 17.04 or 17.10?

It could make a huge difference and we need as much info as possible.

Can you also tell us as much as you can about the hardware in that old HP 530 laptop.

---

### Post by montagproject on 2017-10-28
Hello

First. Thanks for replying. My version of xubuntu is 17.10. My hardware is quite dated, here I paste some specs (however I run now in safe mode and display resolution is not accurate - normally it is 1280x800:

-Computer-
Processor        : Intel(R) Celeron(R) M CPU        530  @ 1.73GHz
Memory        : 2052MB (832MB used)
Machine Type        : Notebook
Operating System        : Ubuntu 17.10

Date/Time        : sob, 28 pa&#378; 2017, 13:43:21
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : llvmpipe (LLVM 5.0, 128 bits)
X11 Vendor        : The X.Org Foundation
-Audio Devices-
Audio Adapter        : HDA-Intel - HDA Intel
-Input Devices-
 Sleep Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 SynPS/2 Synaptics TouchPad
 HP WMI hotkeys
 HDA Intel Mic
 HDA Intel Headphone
-Printers-
No printers found
-Storage-
-SCSI Disks-
TSSTcorp CDDVDW TS-L632H
ATA FUJITSU MHZ2120B

The graphic card is integrated - more details:

-PCI Devices-
Host bridge        : Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
VGA compatible controller        : Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Display controller        : Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by sudodus on 2017-10-28
If I remember correctly, problems have been reported also with previous versions of Ubuntu with the Intel Corporation Mobile 945GSE Express Integrated Graphics. I think some of them were solved after installing **xserver-xorg-video-intel**

```
sudo apt update
sudo apt install xserver-xorg-video-intel
```

and rebooting.

It is worth trying, but I *don't know* if it will solve your problem.

---

### Post by ajgreeny on 2017-10-28
Good possible catch sudodus.

I had that exact problem on an old Intel Atom netbook which booted to a totally black screen and I had to boot using **nomodeset** option then install that missing xorg package.  I think it was Lubuntu 14.04 that was hardest hit by the problem, but once you knew how, it was easily solved.

---

### Post by montagproject on 2017-10-28
Thank you for the suggestions!

@Sudodus - I think I already have this driver, but somehow it does not work after the command I got: "xserver-xorg-video-intel is already the newest version (2:2.99.917+git20170309-0ubuntu1)." 

Do you have any other suggestion what to do?


Thanks!

---

### Post by mörgæs on 2017-10-28
If you click the old hardware link in my signature and search the text for 'uxa' there is some advice. Does it help?

---

### Post by sudodus on 2017-10-28
> **mörgæs said:**
> If you click the old hardware link in my signature and search the text for 'uxa' there is some advice. Does it help?
+1

Yes, uxa acceleration would be the next thing to try.

---

