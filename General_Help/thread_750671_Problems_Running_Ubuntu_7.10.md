---
title: "Problems Running Ubuntu 7.10"
date: 2008-04-09
forum: General Help
---

### Post by BImCS on 2008-04-09
Hey, I have a really weird problem when I boot into Ubuntu, I see the ubuntu loading screen, it loads then my screen gets all messed up [[IMG]http://img149.imageshack.us/img149/5827/pict0057zx8.th.jpg[/IMG]](http://img149.imageshack.us/my.php?image=pict0057zx8.jpg)  . 
my specs are

MOBO - ASUS A8N-SLI
CPU - AMD Athlon 3500+ Clawhammer
Gpu - 2x GeForce 6800 (SLI)
MEM - 2gb DDR 

Thank you.

---

### Post by redbob on 2008-04-09
Try to do this: Press Ctrl-Alt-F1, so you're going to line-command. Login and type this command:
> sudo dpkg-reconfigure xserver-xorg
Seems to be your display doesn't support Refresh rate from Ubuntu actual configuration.

---

### Post by BImCS on 2008-04-09
Thank You soo much:) im on it right now and i love it!!

---

