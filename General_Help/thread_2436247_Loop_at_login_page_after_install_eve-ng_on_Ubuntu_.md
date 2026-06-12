---
title: "Loop at login page after install eve-ng on Ubuntu Desktop"
date: 2020-02-03
forum: General Help
---

### Post by heinzaw on 2020-02-03
Hello Experts,


I'm newcomer to Ubuntu. I'm trying to install eve-ng community version on Ubuntu desktop 16.0.4 as bare installation. ( Please read about at eve-ng at [https://www.eve-ng.net/](https://www.eve-ng.net/) )  
First I installed Ubuntu 16.04 desktop version on my ASUS laptop dual boot with windows 10. I did "apt-get update" , "apt-get upgrade" from Ubuntu main server. I edited hosts files, interfaces files etc.. as per [https://www.eve-ng.net/index.php/documentation/installation/bare-install/](https://www.eve-ng.net/index.php/documentation/installation/bare-install/)  Everything is fine till this step. I can reboot or shutdown and power on.
Problem started from after eve-ng bare installation. After eve-ng bare installation, I rebooted the Ubuntu. After reboot, at login page. Ubuntu re-start automatically, after hit the password. When I press the Ctrl+Alt+F1 at login page, it show below error codes:


[ 3.217286] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 6013d4
[ IBUS]
[ 3.233743] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 10ac08
[ IBUS]
[ 4.516353] nouveau 0000:01:00.0: DRM: Pointer to TMDS table invalid


I've tried to remove NVIDIA graphic drive by running "sudo apt-get purge nvidia* "
I've checked that I have permission on my /$user$/home folder
I've checked that I have permission on ~/.Xauthority and ~/.ICEauthority files under my home folder
I've checked that I have permission on /tmp
I also tried to restart lightdm by running "dpkg-reconfigure lightdm" .
at Ubuntu system recovery terminal.


But problem still occur. Pleas help me. Thank you in advance. :P


MY ASUS laptop description.
CPU : intel Core i5 8th gen.
RAM: 24G DDR4 (2400 MHz).
Graphic Intel on board + Nvidia Gforce X940MX

---

