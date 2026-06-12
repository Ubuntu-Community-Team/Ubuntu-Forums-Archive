---
title: "(Ubuntu 18.04 LTS) system crashes when opening system settings"
date: 2018-05-13
forum: General Help
---

### Post by sethtaylor112 on 2018-05-13
Just installed Ubuntu alongside windows 10, since then I can use most of the apps within the OS. However, when I attempt to change the background the system instantly crashes. Also, when I try to open the system settings the system freezes. I can only move my mouse but I can't open anything. I've tried changing my GPU driver within the additional drivers option to the propietary, but nothing happens and I get a internal error pop-up. This is probably the 10th time I have reinstalled Ubuntu trying to fix my problems. 

As long as I don't try to do those 2 things then everything works good.


My specs
HP Pavilion power laptop
Ram- 12GB
CPU- Intel I5 7300q
GPU- Nvidia GeForce 1050 2gb

---

### Post by Jail on 2018-06-16
I had similar problem. Whenever I tried to open system settings display manager crashed and returned me to login screen. For me the solution was to install proprietary nvidia-driver-396 from [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) repository. After adding this ppa I entered commands in terminal:
ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
Notice that > sudo ubuntu-drivers autoinstall installs only recommended driver. For me it was nvidia-driver-396 from ppa. I also couldn't  change drivers with the additional drivers option but ubuntu-drivers managed to do it.

---

