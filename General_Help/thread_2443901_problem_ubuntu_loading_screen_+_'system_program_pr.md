---
title: "problem ubuntu loading screen + 'system program problem detected'"
date: 2020-05-21
forum: General Help
---

### Post by stavis on 2020-05-21
Hey. (I tried to check if this was already posted but it didn't work. I searched, but didn't find anything close to it)
So, I'm a new ubuntu user and yesterday I installed anaconda and flash. Today when I booted, the loading screen was black and those little dots were inside purple squares (like the screenshots, but in a black screen). Some time later, the regular ubuntu screen showed up with the desktop, taskbar and so on. But the little dots were still blinking inside the purple squares (screenshots), the system problem error appeared. But I couldn't click or do anything at all. If I decide to wait, it comes back to the black screen + dots and if I keep waiting nothing happens. I don't know if this problem has to do with installing flash or anaconda (for flash I had to enable canonical partners). After installing those, I did sudo apt-get upgrade and update. The only way I found to turn the pc off was by holding the case's button, I know that is not very good but I didn't know what to do. 

I then tried: 
- pressing 'E' in the GRUB and entering "systemd.unit=rescue.target" in the line that starts with "linux", then sudo apt-get autoremove (I also tried 'mount -n -o remount,rw /' but nothing happened)
- in the GRUB, going to 'Advanced options for Ubuntu', choosing a recovery mode kernel and 'network - enable networking' and 'dpkg repair broken packages'
both those options booted my ubuntu screen without the blinking dots, but I couldn't click or do anything with my keyboard.

Could anyone help me please?
I might just reinstall ubuntu

[ATTACH=CONFIG]285958[/ATTACH][ATTACH=CONFIG]285959[/ATTACH]

---

### Post by stavis on 2020-05-28
up

---

### Post by dino99 on 2020-05-28
no idea what anaconda is or do (not an ubuntu genuine package) , but [https://docs.anaconda.com/anaconda/install/linux/](https://docs.anaconda.com/anaconda/install/linux/) give you some hints
about flash, its outdated and nobody use it nowadays

---

### Post by stavis on 2020-05-28
> **dino99 said:**
> no idea what anaconda is or do (not an ubuntu genuine package) , but [https://docs.anaconda.com/anaconda/install/linux/](https://docs.anaconda.com/anaconda/install/linux/) give you some hints
about flash, its outdated and nobody use it nowadays

Hey! I already installed those; anaconda is a python platform. I know flash is outdated but I bought a course that needs it to run :/

---

