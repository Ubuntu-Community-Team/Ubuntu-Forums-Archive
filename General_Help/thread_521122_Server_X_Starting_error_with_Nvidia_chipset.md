---
title: "Server X Starting error with Nvidia chipset"
date: 2007-08-09
forum: General Help
---

### Post by bizzard4 on 2007-08-09
Hi, first sorry for my bad english I will do my best.

I have but a new PC with these spec :
Intel MotherBoard
Intel Dual-Core
Sata DD 250 GO
Nvidia 8600 GTS <-- Problem seem to be here

When I start ubuntu I get the error :

(EE): No Device Foudn

Fatal error..
No screen found

and i start in console. I read that a lot of people have problem with Nvidia chipset serie 8. First, i dont find my nvidia in the nvidia-glx or nvidia-glx-new so my first question is to know on witch one is on?

My second question is that is I try to install for exemple nvidia-glx I write : sudo install nvidia-glx and I got a message that ask me to put de Edgy CD In but i have wubi so no cd -_-.

If someone can help me plz I will be very happy :guitar:

---

### Post by z0mbie on 2007-08-09
Follow this guide here my friend. I got my 8600 working that way with drivers from Nvidia website:

[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

---

### Post by bizzard4 on 2007-08-09
I still have the same problem that when I type this command (the first to enter)
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

I got this :

Media change: please insert the disc labeled 'ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)' in the driver '/cdrom/' and press enter

I dont have this cd because i have installl with WUbi. The only thing i have it the iso image (ubuntu 7) in the wubi directory in windows.

Maybe i can mount this image from console.

---

### Post by bizzard4 on 2007-08-09
Ok all is fine !

I filanly find my problem with internet (got 2 cards and need to configure pppoe on one) after i download the new kernel I insall the nvidia Driver and Gnome Start :KS

After 16 hours of search i finaly fot Server X start

Thx For all and the nvidia 8600 link !

---

