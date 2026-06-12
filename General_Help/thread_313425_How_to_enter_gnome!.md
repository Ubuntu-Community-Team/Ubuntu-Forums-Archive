---
title: "How to enter gnome!"
date: 2006-12-06
forum: General Help
---

### Post by LaoLiulaoliu on 2006-12-06
I install ubuntu 6.10 server-amd64
I have already install gnome and X server
(sudo apt-get install gnome-desktop
sudo apt-get install xserver-xorg)
,but still I don't know how to enter the gnome environment!
Is there a commond?Or other method?:D

---

### Post by aysiu on 2006-12-06
Try this: ```
sudo aptitude update
sudo aptitude install gnome-core x-window-system-core gdm
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` If you want the full Ubuntu deal (not just basic Gnome), you can do this instead: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by LaoLiulaoliu on 2006-12-06
What I want to say is thank you very much!But there is still a small problem.
The gnome login in interface come,when I enter the user name and password,it turn dark first,then enter gnome.Does it no matter?
:D

---

### Post by Sef on 2006-12-06
> The gnome login in interface come,when I enter the user name and password,it turn dark first,then enter gnome.Does it no matter?


No, it doesn't, if it just lasts a few seconds.

---

