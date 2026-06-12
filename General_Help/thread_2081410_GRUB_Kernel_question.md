---
title: "GRUB Kernel question"
date: 2012-11-06
forum: General Help
---

### Post by brichert01 on 2012-11-06
I am new to linux and purchased a Dell Optiplex 760 from my school to install linux on and become familiar with it.  This wasn't my first linux install but I had a lot of problems with it.  When I finally got it installed and selected Ubuntu from the GRUB the screen would go black and a cursor in the top right would flash but I couldn't do anything.  After much searching around I found I needed to edit Ubuntu in the GRUB and I took away the line about splash and added in edd=on and nolapic and the system booted properly which was great.

Now every time I reboot I have to edit the Ubuntu and retype the information.  Is there a way to save what I edited in the GRUB so I don't have to retype that every time I restart my machine?

---

### Post by wojox on 2012-11-06
Sure, here you go:
```
gksudo gedit /etc/default/grub
```

Look for ** GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** 
and add it between "quiet" and "splash". Then run:
```
sudo update-grub
```

---

### Post by brichert01 on 2012-11-06
Thanks wojox that worked perfectly.

---

