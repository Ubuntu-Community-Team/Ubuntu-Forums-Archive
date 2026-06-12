---
title: "How to run Synaptics (Synclient) under Xubuntu 17.10"
date: 2017-12-17
forum: General Help
---

### Post by Ralph L on 2017-12-17
I am considering moving from Xubuntu 17.04 to Xubuntu 17.10.  My (new) computer is an Acer Aspire E5-575G 57D4 with a giant touchpad and only 1 physical button (the entire bottom of the touchpad).  I am a thumb clicker and a palm dragger with my left palm.  I don't use any "tap to click" or multi-finger gestures.  With the Synaptics driver and Synclient I was able to disable the left half of my touchpad, shrink the right-click area to about an inch wide, extend the left click area to the right so I could reach it with my thumb, and disable all tap clicking and multi-finger touching.  I tried to do this same thing with libinput , but was unable to do so.  It is my understanding that Xubuntu 17.10 uses Wayland, rather than xorg, and that Wayland uses libinput.  Does anybody know if libinput has been enhanced to have the Synaptics features that I need?  Does anybody know if I can install Synaptics into a Wayland system?  Does anybody know if I use xorg rather than wayland, if I can install Synaptics/ Synclient in it?  Does anybody know of any other approach to getting legacy touchpad behavior like I want????

Any help is appreciated.

---

### Post by ajgreeny on 2017-12-18
I think synclient requires a running X session so if using wayland it will not work.

I was not personally aware of this fact until yesterday, so thanks is due to **untrustytahr** in the thread at [https://ubuntuforums.org/showthread.php?t=2380045&p=13720345](https://ubuntuforums.org/showthread.php?t=2380045&p=13720345) who showed this to be so.

---

