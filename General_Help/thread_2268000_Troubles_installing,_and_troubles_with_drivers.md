---
title: "Troubles installing, and troubles with drivers"
date: 2015-03-05
forum: General Help
---

### Post by Gandem on 2015-03-05
Hello,

It's been one week that i've been having issues with installing and getting ubuntu to work properly.

I have:
**Model:** Asus G751JT with an intel haswell chipset
**CPU:** Intel core i7-4710HQ
**Graphic card:** Nvidia GTX 970M

First of all, I have ubuntu 14.10 on a bootable usb (i've tried all following step with ubuntu 14.04 LTS, it didn't work either). When I try to boot from the usb, and install or try ubuntu, all I get is an empty black screen.

I googled the issue, and used the usual workaround which is booting with **nomodeset**. Ubuntu boots properly, and I install it normally on one of my hard drives partitions (a different partition than windows' partition).
One ubuntu is installed, I still cannot boot without using **nomodeset**. So to fix the issue, I tried to install nvidia newest proprietary drivers, to get my graphic card to work with ubuntu:

1- I tried to install nvidia proprietary drivers from _nvidia's website_, chmodding the .run, shutting down xserver, and installing the drivers. Once the drivers are installed, i reboot the laptop (with quiet splash only), and after inputting my login password, I get stuck on ubuntu desktop purplish background screen. CTRL + ALT + F1 to F6 only lead to a completely black screen. The end.

2- I tried to install nvidia drivers from _xorg-edgers ppa_. Once I reboot (with quiet splash only), after inputting my login, everything works **except **when I kill X (lighdm stop) or when i try to access the tty (CTRL + ALT + F1 to F6) the only thing I get is a completely black screen !

These issues are driving me mad, and I desperately need your help!

Thanks in advance,

Gandem

---

### Post by dino99 on 2015-03-05
my two cents:
- you are using recent hardware, so you will get better luck using recent software; i mean Vivid (15.04) which have a kernel compatible with your hardware.
- as the driver (346.35) from the xorg-edgers ppa is the best i've found since i'm also using nvidia gpu: open a terminal and run:
  sudo apt-get purge nvidia*
  sudo apt-get install synaptic (to use a userfriendly tool for updating/upgrading/view changelog)
  sudo gedit /etc/apt/sources.list  (here change all the distro-name to get vivid (take care of typo here, no error allowed), and save before exiting)
  sudo apt-get update
  sudo synaptic  (you will get a few hundred packages to upgrade, select the cpp, python, ubuntu-destop to upgrade first, then the others (a few each time)

 then when done, sudo apt-get install nvidia-346  (the ppa needs to be activated first indeed ), then from synaptic, disable the ppa  and then close all opened apps
  sudo reboot

---

### Post by Gandem on 2015-03-05
First, thank you very much for your answer. 

So, I updated to vivid, and installed nvidia driver, but I still can't access tty, all i get is a blank screen.

---

### Post by Gandem on 2015-03-06
Up? I still can't get running tty and nvidia drivers correctly. 

When the pc is booting, I also see first a grey screen, then the nvidia logo flashes, then a black screen, before getting to login. Booting in nomodeset or setting vga=xxx in grub doesn't seem to change anything!

---

