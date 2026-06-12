---
title: "Windows Emulators?"
date: 2007-10-19
forum: General Help
---

### Post by cad2blender on 2007-10-19
Ok guys I am really looking forward to completely rid of XP out of my life ( at least as much as I can). I know there is a way to run XP apps in Ubuntu. I would like to know what would be a good program to use. I have heard of WINE, Cedega, QUEMU (I believe that is what it is called), are there any others? I would also like to know the pros and cons of these. Most of the stuff I looked at does not really tell me exactly what I want. Do any of these NEED XP to be installed? I have used crossover on my mac and I can run many programs without XP.

Thanks in advance

---

### Post by bionnaki on 2007-10-19
wine is the best if you just want to simply run (some) windows apps. personally, I run virtualbox which is basically running windows on top of linux.

search the forums for installation guide. very easy to do.

---

### Post by Nunu on 2007-10-19
There is also Crossover office, and TransGaming's Cedega for gaming. best is to try them and see which works better for you. When it comes to migrating from MS to Linux you need to find the software that works for you and fits your requirements best

---

### Post by Spenzer4Hire on 2007-10-19
WINE, Crossover Office and Cadega are compatibility layers.  They allow you to install and run Windows applications directly onto Linux, more or less.

VmWare Server/Workstation, Virtualbox and Qemu are virtual machines.  They allow you to install Windows (or most other OSs) in a "virtual machine".  You run a complete copy of Windows on top of Linux.

Running in a virtual machine will give you the best compatibility.  As far as the applications and Windows know, they are running on their own computer.  Downsides are the extra overhead of running two operating systems and you will have poor 3D performance if you are a gamer.

Running with a compatibility layer often provides native speed or better.  There are some games that run quite well under WINE/Cadega.  Unfortunately the compatibility layers are always playing catch-up, so they can not possibly support every application.  Their respective websites should list which applications they support.

---

### Post by Nunu on 2007-10-19
I have also noticed that when you run games through cedega the games are running in a window. I don't know if that is because i configured the app wrong though. I must say that the game did run better under Linux then the native OS

---

