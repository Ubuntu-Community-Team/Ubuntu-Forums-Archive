---
title: "Somehow anything that I install is getting the kde configuration, I'm on Gnome"
date: 2006-07-14
forum: General Help
---

### Post by dhruv_1884 on 2006-07-14
Hi,

I tried installing wine and when i ran the wine configuration program, it crashed because it couldnt find the kde sound directory,
then i tried installing amule,
it crashed too because the default browser was Konqurer

I'm on Gnome
what do i do

thanks in advance

dhruv

---

### Post by slimdog360 on 2006-07-14
easy way is to go to synaptic and install the core-kde packages

---

### Post by dhruv_1884 on 2006-07-14
will that make kde as the default session manager, i dont want that, i'll install what u told me too anyway, but i wanna be on Gnome , and want all thedefaults for gnome

---

### Post by slimdog360 on 2006-07-14
nope, you will have the option to log into KDE if you feel like but it wont do anything to gnome or your usual settings. The difference will be that you will have a couple more packages on your computer.

just to make sure you install the correct one its in 
synaptic--->KDE desktop environment--->kde-core

---

### Post by dhruv_1884 on 2006-07-14
no, i dont want that , i want my defaults to be gnome when i install my programs, any suggestions

---

### Post by slimdog360 on 2006-07-14
I think you may be a little confused here. Some programs are made for kde and they leave out certain packages because of this. If you do not install the core libs for kde you can not run the programs. You do not install anything with gnome or kde as default. If you install the core files everything will remain the same except that you will be able to run the program that you couldnt before.
you wont even notice the core kde libs.

---

### Post by aysiu on 2006-07-14
Based on [these images](http://images.google.com/images?hl=en&q=amule&btnG=Google+Search&sa=N&tab=wi), aMule appears to be a KDE application. I didn't know WineCFG was, too.

Applications generally tend to be KDE (Qt) or Gnome (GTK) apps. It doesn't matter if you're running the application in KDE or Gnome.

For example, Scribus is a KDE application in terms of looks. When I run it in Gnome, it looks a little ugly, and it has to load a whole bunch of Qt libraries. I can't just change Scribus into a GTK application. I can run it in Gnome, but how it looks and which libraries it uses are predefined.

---

