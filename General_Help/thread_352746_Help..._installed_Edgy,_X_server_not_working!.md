---
title: "Help... installed Edgy, X server not working!"
date: 2007-02-03
forum: General Help
---

### Post by zeroblitzt on 2007-02-03
I'm in lynx now on the command line. 
Anyway I had just finished updating to Edgy (I had to reinstall my entire Ubuntu installation today), and I restarted and it said 'could not secure MMIO' or something. I tried typing startx, but it didnt help.
I am using an nVidia Geforce MX4000 and I can't remember the name of the package to download. It's along the lines of nvidia-glx-legacy, but I tried that and it didn't work.

Please help, I'd really rather not install my whole system again.

---

### Post by r4ik on 2007-02-03
Do a,

sudo dpkg-reconfigure xserver-xorg

follow the defaults and get you're drivers here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

