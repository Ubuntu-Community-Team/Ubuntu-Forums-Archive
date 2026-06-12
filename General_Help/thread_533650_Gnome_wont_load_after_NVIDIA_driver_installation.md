---
title: "Gnome wont load after NVIDIA driver installation"
date: 2007-08-24
forum: General Help
---

### Post by 2pacalypse on 2007-08-24
I got a problem with my GNOME enviroment, I installed a fresh ubuntu install in the morning, booted it up and everything went fine. I installed build-essentials and the official NVIDIA driver (from [www.nvidia.com](www.nvidia.com)) and did X-Restart, After this GNOME Stopped working! It simply showed the gnome login screen, and then after login simply showed the default background color (that orange like color) and the mouse, thats it no splash screen or anything else... I tried waiting for half an hour but there was no change, I installed KDE (Via TTY) and run the computer with it and it works fine, but I still prefure to use GNOME (Since I am used to it). Anyone has any Idea how to help?

My computer:

Intel Dual Core E2140 (1.6G)
1GB DDR2 RAM (533MHZ)
Graphics: WinFastPX 8400 (Geforce 8400GS)

---

### Post by 2pacalypse on 2007-08-29
sorry to bump but I still need help... Gnome still wont load although I did everythin I could think of, reinstalling Gnome, uninstalling nvidia+build-essentials (which basicly reverted all the installations I did, making it the same as it was after inital installation

---

### Post by jusmurph on 2007-08-29
Do a fresh install and use the nividea drivers from the repo (Add Remove Progs is the easiest thing i can suggest.

---

### Post by bogdan_5844 on 2007-08-29
or use Envy to  get the NVIDIA drivers,it is totally automatic

---

### Post by 2pacalypse on 2007-08-29
> **jusmurph said:**
> Do a fresh install and use the nividea drivers from the repo (Add Remove Progs is the easiest thing i can suggest.

you mean like re-install all of Ubuntu... I'll stick to KDE in that case. I already tried to clean out nvidia and install it from repo (nvidia-glx) but its still the same problem.

> **bogdan_5844 said:**
> or use Envy to  get the NVIDIA drivers,it is totally automatic

Theres no need, I already installed the NVIDIA drivers normally. It works perfect with KDE but Gnome, and ONLY gnome has some issue with it.

---

### Post by fragos on 2007-08-29
You never told us what Nvidia chip set you have.  That makes a difference in which driver is installed.  You don't have to re-install Ubuntu to change the Nvidia driver.  A check of Nivia video problems in the forums will show that they frequently relate to not using Ubuntu repo drivers and non-Ubuntu installation programs like EasyUbuntu and Envy.  These work for some but not all.  The Nvidia package to install is most likely "nvidia-glx".

---

### Post by 2pacalypse on 2007-08-30
Actually I did... assuming by chipset you mean the actual GPU Model:

> **2pacalypse said:**
> 
Graphics: WinFastPX 8400 (Geforce 8400GS)

---

### Post by angryfirelord on 2007-08-30
First, remember to apply all updates to your system.

While this may not help, try using the newest driver from nvidia's site. Remember to uninstall the old one first.

---

### Post by 2pacalypse on 2007-09-01
nothing seems to helped... Gnome still freezes.

---

