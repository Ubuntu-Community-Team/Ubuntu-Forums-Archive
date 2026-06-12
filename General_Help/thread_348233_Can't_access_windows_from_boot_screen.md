---
title: "Can't access windows from boot screen?"
date: 2007-01-28
forum: General Help
---

### Post by taliesin_the_alchemist on 2007-01-28
Hello all.  
I'm having a problem accessing windows from the boot screen.  For some reason the computer doesn't  recognize the keyboard. I've tried buying a new keyboard and had no success with it. Some one told me to use a non-USB keyboard but my computer is old and is only compatable with USB keyboards, so I'm at a total loss...

There are still somethings in windows I need to have access to. Can any one help me figure this out?:confused:

PS. Ubuntu boots just fine (as far as I can tell).  When the boot screen comes up it counts down and loads Ubuntu, meanwhile I cannot  use the arrow keys to navigate they boot menu...

---

### Post by kosmic on 2007-01-28
If you can use your keyboard in linux then go to a Terminal and edit the file :

sudo gedit /boot/grub/menu.lst

and change it so that Windows starts instead of Ubuntu

---

### Post by taliesin_the_alchemist on 2007-02-04
If I change the boot up will I still be able to access Ubuntu? I still want use Ubuntu too, I would like to have access to both systems.:KS

---

