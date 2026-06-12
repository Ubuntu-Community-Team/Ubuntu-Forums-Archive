---
title: "ndiswrapper"
date: 2007-03-28
forum: General Help
---

### Post by bkeithly on 2007-03-28
This is the third time this has happened...

I installed updates and boom ndiswrapper stops working....

My question is:

WHAT CAN I DO TO PREVENT UPGRADES FROM BREAKING MY WIFI? (some times nvidia drivers break as well)

Specs:

ubuntu 6.10
hp6040 dv laptop
broadcom chipsets

Ideas please, I have posted about this several times.  I really would appriciate advice.

---

### Post by acormack on 2007-03-28
It sounds like you are having problems with the bcm43xx module trying to load and conflicting with the ndiswrapper one you want to use.

Within /etc/modprobe.d/blacklist there should be a line that says:

blacklist bcm43xx

This should mean that once you have your ndiswrapper working again it continues working.  

Fingers crossed - I had to play around with my broadcom chipped card at first - but since then it has been OK.

I found this page useful

[http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/)

Alec

---

