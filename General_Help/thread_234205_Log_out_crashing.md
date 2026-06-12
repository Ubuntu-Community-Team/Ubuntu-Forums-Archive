---
title: "Log out crashing"
date: 2006-08-11
forum: General Help
---

### Post by Polygon on 2006-08-11
Ok this is REALLY making me mad.

Basically twice a day, when i log out of ubuntu, instead of going back to the login screen, the screen turns white and the whole system locks up. cant restart X, cant do anything, and i have to hard restart my computer to get it to work again

ive been doing various stuff before it crashes, and i havent seen a pattern

and ive also been using two types of kernels (i was using 386 and switched to k7 today, and i got the crash 5 seconds ago)

is there ANY way to fix this, or find out whats wrong? its REALLY annoying!

---

### Post by jordilin on 2006-08-11
It could be related to your graphics card driver. The fglrx ati driver is reported to have issues like the ones you are talking.

---

### Post by Polygon on 2006-08-11
so there is really no fix for this until flgrx or whatever is fixed?

---

### Post by jordilin on 2006-08-12
> **Polygon said:**
> so there is really no fix for this until flgrx or whatever is fixed?

Well, I have an ati card, with the generic ati driver and works well.

---

### Post by h00s on 2006-08-12
> **Polygon said:**
> so there is really no fix for this until flgrx or whatever is fixed?
I'm experiencing same problem (I have ATI 9600) and solution is quite stupid :D 

When you click log off button on gnome panel DO NOT move mouse until you see screen with log out button, lock screen button etc. When you click log out button, again, do not move mouse and the problem is solved. 

I know it's kinda stupid, but for me, using this instructions i didn't see 'white screen of death' for long.
Try this and let me know if you solved the problem :)

---

### Post by clint1010 on 2006-08-12
Yes this fix sounds quite ridiculous, but I was ahving the same "white screen hang" after logging out. 

Dapper was working fine with the originally created user, but after adding my wife as a user, her log out always caused the login screen to go blank and then hang the machine

Definatly an ATI driver issue

But this tip works a treat, till it is sorted out

Cheers

---

### Post by Polygon on 2006-08-12
i shall try this, and it obviously cant be a silly fix if it works!

thanks

---

### Post by cptnapalm on 2006-08-12
[http://ati.cchtml.com/show_bug.cgi?id=239](http://ati.cchtml.com/show_bug.cgi?id=239)

This is an unofficial ATi Linux driver bug report blog type thing.

There are variations, such as those who get a white screen and those who don't.  Some are able to ssh into the machine, while for others, the machine has totally crashed.

I think I'm going to take to punching people who talk about the quality assurance of closed source software.

---

### Post by Polygon on 2006-08-12
i guess all we can hope is for AMD to open source the ati drivers.

---

