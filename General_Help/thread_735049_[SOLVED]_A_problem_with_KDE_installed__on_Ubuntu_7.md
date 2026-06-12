---
title: "[SOLVED] A problem with KDE installed  on Ubuntu 7.10 (not Kubuntu)..."
date: 2008-03-25
forum: General Help
---

### Post by firedevilbg on 2008-03-25
Hi, to all...
I am  new in Ubuntu world so I have some problems...
I decided to install a KDE Desktop on my Ubuntu 7.10... (I was using Gnome before this step...) .  I use a 
```
sudo apt-get install kubuntu-desktop
``` to install KDE. After installing KDE my "User Switcher" in Gnome can't be loaded. (it's crashing on startup) and my "Turn of menu" don't have the 
ordinary  icons. (it have less than ordinary...)
I tried to remove KDE Desktop with 
```
sudo aptitude remove kubuntu-desktop
``` but it dosn't work, KDE is not removing and it works... 
My question is: How to remove KDE and repair my Gnome... :(
Please help...

---

### Post by sumguy231 on 2008-03-25
This page will tell you how to remove all the KDE-related packages, though I can't guarantee that it will help you with your GNOME problems.
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

My only suggestions with the problems you're having in GNOME is to look for the relevant hidden configuration directories in your home folder and delete them so it can make new ones and start fresh.

---

### Post by aysiu on 2008-03-25
By the way, using *aptitude* to remove *kubuntu-desktop* will work only if you used *aptitude* to install *kubuntu-desktop*.

---

### Post by firedevilbg on 2008-03-25
> **sumguy231 said:**
> This page will tell you how to remove all the KDE-related packages, though I can't guarantee that it will help you with your GNOME problems.
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

My only suggestions with the problems you're having in GNOME is to look for the relevant hidden configuration directories in your home folder and delete them so it can make new ones and start fresh.

10x a lot. It work and now I am with "Pure Gnome"  :guitar:

---

