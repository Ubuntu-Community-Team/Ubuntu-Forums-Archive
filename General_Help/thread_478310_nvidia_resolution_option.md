---
title: "nvidia resolution option"
date: 2007-06-19
forum: General Help
---

### Post by highenergy on 2007-06-19
hello,

I installed feisty on my desktop. I have nvidia geforce 5200 graphic card. Under Windows I can use my graphic card with 50-85 Hz refresh rate at 1024x768 resolution. On contrary I can only use 50-64 Hz refresh rate at 1024x768 resolution under feisty. Before doing that I already installed and tested nvidia restricted glx drivers. I can't get fine image uder windows below 75 Hz but 50 Hz does good job under linux. 

It seems that nvidia's glx drivers doesn't allow you to use all available refresh rates at all.


Does anyone has any clues?

regards
H.E.

---

### Post by Qu4k3R on 2007-06-19
Clue 1:
Change the xorg.conf file (carefully, and make a backup).

Clue 2:
Your drivers (linux and windows) have the same version?

---

### Post by highenergy on 2007-06-19
@Qu4k3R:


> 
Clue 2:
Your drivers (linux and windows) have the same version?


uhm,
I don't know if they have the same version or not. I enabled restricted drivers in ubuntu using restricted drivers manager. It means linux driver had came from repository. So it maybe a little out of date. On the windows side I didn't installed latest drivers too because XP automatically recognises nvidia card and uses it's own drivers.  

> 
Clue 1:
Change the xorg.conf file (carefully, and make a backup).


I don't know which fields of xorg.conf file I have to change to make my graphic card function properly. Is there any tutorial? 


regards
H.E.

---

### Post by Qu4k3R on 2007-06-19
Please read this topic, it will help you alot.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

xorg.conf is the file wich maintains your X11 (graphic mode) information.

Before editting your xorg.conf file :

Backup the file:
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_last_backup


The dir is /etc/**X11** , not /etc/**x11**

If you changed your "xorg.conf" file (manually)
And you want to repair it, replace the xorg.conf with your backup, or reconfigure it:

> 
sudo dpkg-reconfigure -phigh xserver-xorg



PS: 
To show your drivers information. (with glxinfo or glxheads)
> 
glxheads


To quit, just do Ctrl+C

You could also install the latest drivers (both for windows and Linux).
Your computer should "run" faster.

---

