---
title: "ubuntu start up problem"
date: 2007-03-02
forum: General Help
---

### Post by RUGUNIT on 2007-03-02
Im having a problem booting to ubuntu 2.11. When i start it, it just scrolls a bunch of consecutive numbers, then gets held up at 437, pauses a bit then goes to 507:cc/59 stops and says:

"Not Automatically Fixing This"

It then flickers around a bit and starts a screen thats red and blue and very basic that says something like:

"Failed to start the X server (your graphical interface). Would you like to view problem."

If i fool around with it i can get XP to start up (giving me the chance to ask for help with this issue.) I attempted to update my video card drivers, but that had no effect.

Any help with this is greatly appreciated.

Thanks,

Rug

---

### Post by zvacet on 2007-03-03
```
  sudo dpkg-reconfigure xserver-xorg
```
and try with** vesa**graphic card

---

### Post by RUGUNIT on 2007-03-03
Im not quite sure what you mean by vesagraphic card...is that a brand or something?

and i cant even get into ubuntu to run the terminal

---

### Post by RUGUNIT on 2007-03-03
Also, before this happened i had ubuntu up and working properly.

---

### Post by bulldog on 2007-03-03
Probably an update or what ever caused this trouble.
Boot into the recovery mode and perform this command```
sudo dpkg-reconfigure xserver-xorg
``` to see if it's reconfiguring things for you.
It will ask some questions which you have to answer and one is the type of graphics you use.
That's were you can say vesa,but I should try first your own graphics driver ie.nvidia or ATI.
Only when it's not working you can choose the vesa instead.

---

### Post by RUGUNIT on 2007-03-03
okay that worked to get ubuntu back working, but now the refresh rate is super slow, it takes a while jsut to scroll a page down in firefox. is there an easy way to fix this? This didnt happen before so i know its could work correctly but its not now. I am not too experienced as you may have noticed.

Thanks

---

