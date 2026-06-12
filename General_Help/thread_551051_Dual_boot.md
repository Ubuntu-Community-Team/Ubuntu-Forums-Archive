---
title: "Dual boot"
date: 2007-09-14
forum: General Help
---

### Post by Dracar on 2007-09-14
I had ubuntu installed, and i wanted a small windows partition for burning and playing with exe's from, so i installed a watered down xp pro but now it only boots to windows. Ubuntu feisty is still on its partition but i cannot choose it from the boot menu, i tried adding a line to e:/boot.ini. Basically i just coppied the windows line and made it say GNOME isntead of windows, Instead of working, it jsut says cant find windowsdir/system32/hal.dll, but i checked and the files is in the dir. any help?

---

### Post by rsambuca on 2007-09-14
Normally, if you have an existing ubuntu installation and install XP afterwords, you would re-install grub using a liveCD so that you have the option at bootup to install either XP or ubuntu.  I recommend restoring grub with this method, although I am not sure if XP will still work with the changes you made to the boot.ini

---

### Post by Dracar on 2007-09-14
I just replaced hal.dll and....well windows won't boot now -.-' so yea im going to reinstall it. How do i reinstall grub from live cd?

---

### Post by oilchangeguy on 2007-09-14
see this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by rsambuca on 2007-09-14
How old is your ubuntu install?  If you have to install XP, it is easiest if you do that first and then just install ubuntu afterwords, so that grub can detect everything and do it automatically.  However, if you want to just re-install XP, then after that you can use the ubuntu liveCD and enter```
sudo grub-install
```

---

### Post by Dracar on 2007-09-14
THe ubuntu install is fairly new but its the first one i got working right so i don't want to uninstall it.

---

### Post by Dracar on 2007-09-14
Ok, ubuntu should be on my first partition of this hard drive, but im not sure if it still is now for some reason, when i installed windows it showed like all my hd space was free... What would i type after the sudo grub-install command? cause it needs an isntall device or w/e (ubuntu should be on my first partition)

Oh yea, sorry for double post but i figured if i jsut edited it would probably still be donw a little ways and no one would notice it.

---

