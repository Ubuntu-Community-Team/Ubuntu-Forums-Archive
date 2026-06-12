---
title: "Screen resolution keeps changing and proper resolution unavailable"
date: 2018-05-28
forum: General Help
---

### Post by Jotaro on 2018-05-28
Hello, ever since I updated to the latest version of Lubuntu, my computer's resolution has been acting weird. First, when I turn the computer on, the resolution makes everything really big and bloated. Then, when I set the resolution to auto and reboot, the resolution changes to 1024x768, which is slightly better, but still has everything too big. I checked and my monitors proper resolution is supposed to be 1920x1080. My monitor is a HP 27es Display 68.6 cm, 27-inch IPS LED Backlit Monitor. Sorry if this topic already exists, I looked around and could only find ones for Ubuntu instead of Lubuntu. Any other information needed, just ask.

---

### Post by Autodave on 2018-05-28
Ubuntu cures should also work for Lubuntu: it is the same operating system, just different desk top.

Do you happen to know what Video card is in the machine? Have you installed any drivers for it? If so, what one and where did you get it from?

---

### Post by Jotaro on 2018-05-28
Video Card is NVIDIA GeForce GTX770 2GB
Wouldn't know how to install drivers for it
I've been using Nouveau display driver from xserver-xorg-video-nouveau, because I assume the graphics card might be outdated by now. Would switching it to NVIDIA driver metapackage from nvidia-driver-390 under Software & Updates fix it? Didn't want to accidentally switch to a outdated card.

---

### Post by Mark_in_Hollywood on 2018-06-12
I am having the same problem. 

This developed after a re-install of 16.04 to enlarge /  

The re-install, via LiveUSB, ran this way: boot to usb, use GParted to "blank" ssd. Reinstall 16.04 Update all.

This is a completely stock install. No prop Nvidia drivers.

Also, the dejadup runs daily, even though it's configged to run weekly.

---

### Post by Autodave on 2018-06-12
Go to SETTINGS -> ADDITIONAL DRIVERS and let it search. Start by using the recommended one.

---

