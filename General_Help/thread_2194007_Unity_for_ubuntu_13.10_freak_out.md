---
title: "Unity for ubuntu 13.10 freak out"
date: 2013-12-15
forum: General Help
---

### Post by crazymonkey05 on 2013-12-15
well as the title states unity for ubuntu 13.10 is freaking out i have tried to reset unity and lightDM with no luck this video is by me and shows whats wrong. so help me out. [http://youtu.be/TWy96_SryOU](http://youtu.be/TWy96_SryOU)

---

### Post by oldos2er on 2013-12-15
It might help if you list your hardware specs.

---

### Post by deadflowr on 2013-12-15
Well, I noticed your display manager was kdm.
Did you install something that would bring that in?
You can switch back to lightdm by running
```
sudo dpkg-reconfigure lightdm
```
then choose lightdm out of the options available.
Then reboot.
Don't know how much that will help your overall problems, though.

---

### Post by crazymonkey05 on 2013-12-17
My computer specs are as followed:

```
Intel Celeron D 3.46
2GB DDR2 RAM clocked at 533 Mhz
80GB HDD
Intel 945g Express Chipset Family

``` if you need other info just ask. and also the default Display manager is in fact LightDM

---

### Post by crazymonkey05 on 2013-12-21
ok so for right now i have found a minor fix. this is what i did.

i set the screen timeout to two minutes then i set it to not show the lock screen and whalla no more flashy...thanks everyone for trying i would still like to find a more permanent solution for this problem though.

---

