---
title: "Can't completely remove LXDE and SLiM"
date: 2013-05-04
forum: General Help
---

### Post by AngJinhang on 2013-05-04
Hi, I'm (not very) new to Ubuntu, and I am using the 12.04.2 version (Precise Pangoline). It worked well and even better than Windows. But I am quite fed up with the Unity desktop's speed, I switched to Cinnamon, and succesfully removed it without leaving anything in my system. And I tried to remaster the system. So I installed LXDE and SLiM (the display manager) , and also custimized it, but I gave up because of the PPA problem (do-dist-upgrade). So, I runned this command in the terminal (CTRL+ALT+F1) because I could not enter the X window system because of SLiM.
sudo apt-get autoremove lxde- slim- ubuntu-desktop+
And...my unity desktop came back, but the problem is why slim is still inside the list when I choose the display manager during installation? And LXDE is still under the desktop environment list in LightDM.
Until one day I removed the package pcmanfm. It also removed lxde-core at the same time. But, hey, it's still there!! Shocker!
So, please, someone help to remove these annoying packages from my computer?
The whereis command:
whereis lxde
whereis slim
The output:
lxde: /usr/share/lxde
slim: /etc/slim.conf

Thanks.

---

