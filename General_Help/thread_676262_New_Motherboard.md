---
title: "New Motherboard"
date: 2008-01-23
forum: General Help
---

### Post by luckyhalo on 2008-01-23
I used to have Ubuntu 7.10 64 bit dual booted with Vista on my computer, but when i installed a new motherboard and memory Ubuntu would just start as a full screen command line, i can still access all my files but i cannot get the GUI. How can I fix this, should I just reinstall ubuntu?

---

### Post by cotcot on 2008-01-23
your info is a little bit short.
Seems to be a graphics card problem. You got grapghics on board ?
Reconfigure xorg.conf might help.```
sudo dpkg-reconfigure xserver-xorg
```
Any error messages when you type startx or gdm in terminal ?
Are you root at the command line ?

---

### Post by luckyhalo on 2008-01-23
Thanks typing startx works, but why is going to terminal whenever i boot?

---

### Post by solarwind on 2008-01-23
Sometimes, when there is a change in the chipset, operating systems need to be reconfigured/reinstalled.

---

