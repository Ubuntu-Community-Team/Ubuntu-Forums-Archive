---
title: "Keyboard/mouse-pad malfunctioning: asus q500a; ubuntu 12.04; unity"
date: 2013-08-25
forum: General Help
---

### Post by seth4 on 2013-08-25
I am using an asus q500a with ubuntu 12.04 unity; linux kernel 3.5.0.39 and windows 8. I will note that all of my hardware works flawlessly in windows 8 which came with the computer, I just don't like windows. I am running a dual boot with windows on ntfs and ubuntu on ext4. Windows on uefi.efi.
-When I boot to ubuntu the first time I press the h key it doesn't work, but it works fine after that. This problem is consistent.
-Sometimes certain on-board shortcuts on my keyboard will auto-press a key instead of performing their intended function. For example, fn+f12 is supposed to increase my volume. Sometimes it presses q repeatedly instead. Same problem with brightness controls for screen and keyboard (but other keys besides q like h). Logging out and logging back in fixes the problem temporarily. Tried kernels 3.5.0.36-39 as well as 3.9.11 and it doesn't seem to make much difference. Also tried gnome-panel and xubuntu-desktop. Not much difference except xubuntu seems to have slightly different issues with my hardware.
-The most annoying problem is sometimes (usually when opening or closing an app) my mouse will get stuck on "grab" mode. When this happens I cannot click, it just wants to grab windows and drag them around. When this happens I cannot click shutdown, or log off. Space and enter do not seem to work either. Most of the functionality of my keyboard fails when this happens. I am able to open terminal win ctrl+alt+t but when I try to type anything it starts opening tabs on top of the screen such as "file" or "edit". The only thing I have found to work is ctrl+alt+del to log out, then waiting 60 seconds for it to do so automatically. Logging temporarily fixes the problem. I have tried switching to gnome-panel and xubuntu-desktop, as well as the previously mentioned kernels with little difference although 3.5.0.39 seems to work the best.

---

### Post by seth4 on 2013-09-03
$ sudo apt-get update
$ sudo apt-get install xserver-xorg-input-multitouch
$ sudo apt-get install xserver-xorg-input-synpatics
Fixed the mouse "grabbing" problem right away. I believe I already had multitouch. I had a problem with broken packages so I had to manually install one of the dependencies. I have been using linux-kernel 3.5.0-39 with Unity and the keyboard problems seem to have stopped.

---

### Post by seth4 on 2013-09-13
Mouse "grabbing" problem is still occuring very rarely. Keyboard problems seem to have come back.

---

