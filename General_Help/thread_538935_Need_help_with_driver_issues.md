---
title: "Need help with driver issues"
date: 2007-08-30
forum: General Help
---

### Post by bbqsauced on 2007-08-30
I just installed Ubuntu on a desktop which I custom made.  I put a Geforce 8800 GTS in it, and I wanted to be able to use it in the linux environment.  I tried enabling the nvidia restricted drivers, but it completely destroyed the install.  I can only log in to access the terminal, and I'm not sure how to go about fixing it.  Any help would be greatly appreciated.

---

### Post by reckless2k2 on 2007-08-30
i think the newer cards you have to use source at nvidias site. restricted drivers won't work in repos. remove nvidia and edit xorg.conf to put vesa back there instead of nvidia. or put nv.

---

### Post by phibit on 2007-08-30
If it only let's you boot up in terminal, login and do that following:

```
sudo nano /etc/X11/xorg.conf
```

then look around until you see the Drivers section

change the word "nvidia" to nv, then press Ctrl-X to save. Then reboot, and that should allow you to get desktop mode back. In the future, when changing your xorg.conf file, remember to create a backup with

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

After that, you can follow this guide to install the latest nvidia drivers: 
[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

### Post by r4ik on 2007-08-30
When you are back in the graphical interface again try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by bbqsauced on 2007-08-30
I managed to get back into the desktop and restore my old xorg.conf.  I tried all those links, and they all met with the same result.  The only one that didn't was using Envy, but it came up with an error instead.

---

