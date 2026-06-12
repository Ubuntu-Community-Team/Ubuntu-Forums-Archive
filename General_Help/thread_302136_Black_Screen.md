---
title: "Black Screen"
date: 2006-11-18
forum: General Help
---

### Post by TheKing on 2006-11-18
Two days ago I decided to try Ubuntu Edgy, and installing it I got a problem...a very common problem, the blank screen after finishing the loading. For this problem I couldn't install ubuntu, so I tried the Kubuntu Alternative CD and it worked: now Kubuntu is installed on my computer. But I have the same problem: a blank screen when I try to load it, so it doesn't load KDM and any thing related to GUI. My monitor wants a 1280 x 1024 res with a frequency of 60 Hz, so I entered the recovery mode from Grub and in the console I tried to modify the xorg.conf file to make it work, using first ```
dpkg-reconfigure xserver-xorg
```
and running startx, then tried to modify the file by editing it manually via nano, but nothing happened: after leaving text mode the screen goes blank and I get angry. KDM doesn't load and I can only use the console. Surfing the web I found a lot of people with this problem, but few ways to solve it...anyone can help me?
Here's my settings:
AMD Athlon 64 3200+
ATI Radeon 9600 SE 256 MB
512 MB Ram
Asus k8v deluxe motherboard
Maxtor 6Y160P0 160GB HD
Windows XP Pro installed on an other partition ( but I use it only for work :neutral: )
Anyone can help me?

---

### Post by an.echte.trilingue on 2006-11-18
You need to do this (assuming you have an internet connection):

1. Follow the instructions [at this link]("https://help.ubuntu.com/community/Repositories/CommandLine") to enable the multiverse and universe repositories.

2.  Install the ATI driver.
```
sudo apt-get update
sudo apt-get install *fglrx*
```

3.  Configure your grafic card to use the ATI driver (fglrx)
```
sudo dpkg-reconfigure xserver-xorg
```
be sure to select the proper driver (fglrx)

4.  Enjoy ubuntu.

Take care,

-mat

---

### Post by TheKing on 2006-11-18
Thanks a lot! :) 
I'm going to try it!

---

