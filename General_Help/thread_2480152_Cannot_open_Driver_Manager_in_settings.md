---
title: "Cannot open Driver Manager in settings"
date: 2022-10-20
forum: General Help
---

### Post by tips2448 on 2022-10-20
**THIS ISN'T TECHNICALLY SOLVED BECAUSE I UPGRADED FROM 22.04 TO 22.10 AND IS WORKING AS EXPECTED - If you want me to place as unsolved, please let me know and I will happily place it in the unsolved state.**

In the settings, when selecting the 'Driver Manager', it say's "Could not load plugin from /home/myusername/kcms/usr/share/kservices5/kcm_driver_manager.desktop: The shared library was not found."

Kubuntu 22.04, X11
Plasma 5.25.90, frameworks 5.98.0, QT 5.15.3, nvidia-driver-520
Kernel 6.0.1 generic 64
NVIDIA TU106 [GeForce RTX 2060 Rev. A] (rev a1)                 

Anyone able to fix this? it's been like this for possibly a year or more, but if it's the state of things, I can ignore it. 

 What I see screenshot:[URL="https://drive.proton.me/urls/493MXK49FG#BS5rBWUbtX1x"]
https://drive.proton.me/urls/493MXK49FG#BS5rBWUbtX1x[/URL]

var/log/syslog, plasmashell:
 kf.coreaddons: "Could not load plugin from /usr/share/kservices5/kcm_driver_manager.desktop: '/usr/share/kservices5/kcm_driver_manager.desktop' is not an ELF object"
kf.coreaddons.desktopparser: Error: Failed to open  "kcms//usr/share/kservices5/kcm_driver_manager.desktop"  
QFileDevice::seek: IODevice is not open
kf.coreaddons: "Could not load plugin from /home/myusername/kcms/usr/share/kservices5/kcm_driver_manager.desktop: The shared library was not found."

---

### Post by #&amp;thj^% on 2022-10-20
This happened to me very early on in development please try:
```
sudo cp ~/.Xauthority /root
```
I'm currently runing "DE: Plasma 5.26.1 
"
EDIT: If the above does not work and if you need to actually install non-free drivers
```
sudo ubuntu-drivers autoinstall
```

---

### Post by tips2448 on 2022-10-20
Thanks...
I've tried those before, and right now, but it doesn't work for me, lol, I'm perfectly fine though.
sudo ubuntu-drivers autoinstall has't worked for me, and also currently causes problems for me, because I get errors with nvidia-515, since half an hour ago after Muon update, and right now, but solved driver problems whenever I sudo apt install nvidia-driver-520..

---

### Post by #&amp;thj^% on 2022-10-20
Nice you have a work around, also I recall a bug first I've seen in 20.04 as well, some had good luck  with:
```
sudo update-apt-xapian-index
```
Also
```
 Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 520.56.06

```

---

### Post by tips2448 on 2022-10-20
Haha, at least these days, i haven't had black screens after release upgrades... they work!

NVIDIA TU106 [GeForce RTX 2060 Rev. A] (rev a1)

---

### Post by tips2448 on 2022-10-20
I'll try upgrading to 22:10 just saw it now...

---

### Post by tips2448 on 2022-10-20
> **tips2448 said:**
> I'll try upgrading to 22:10 just saw it now...

This just leads to a new problem asking me to use ppa-purge ?

I guess this is the Ubuntu's way of saying "I don't have a clue, please make a fresh install" , I haven't done this for perhaps 5 years...

---

