---
title: "Default boot for XP"
date: 2008-06-27
forum: General Help
---

### Post by gkiteguy on 2008-06-27
I have a running Dual-Boot system, but my wife can't scroll to select XP. How can I default to boot in Windows XP to keep her happy. <Sigh>

Gkiteguy

---

### Post by drs305 on 2008-06-27
If you are using Grub, set the default OS in StartUp-Manager. You don't have to edit menu.lst and risk messing it up.

Install Startup-Manager:
```
sudo aptitude install startupmanager
```

Run: System, Administration, Startup-Manager

On the main tab, select Windows as the default OS.

You can also set a variety of other grub settings:

[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by chex_m8 on 2008-06-27
or you edit the menu.lst
sudo gedit /boot/grub/menu.lst

now locate the section that says "default" change the number to match that of XP remember counting starts at 0. so if xp is the 5th title change the number to 4. also when you count the titles you must count all of them even the one that says other operating systems. I have mine set up that way too so xp is default for other people that use my comp. i also hide the grub menu so they dont even see it, its better if they just don't know it's there.

---

