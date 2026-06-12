---
title: "Error 11 in Grub - nothing changed ???"
date: 2007-06-04
forum: General Help
---

### Post by pete222 on 2007-06-04
maybe someone could give me some advice-
this is my menu.lst file entry for my second hd that is XP- was working perfect before the .16 upgrade I am including both of the configurations I have tried both error 11

title		Windows XP 
rootnoverify
map		(hd0) (hd1)
map 		(hd1) (hd0)
rootnoverify	(hd1,0)
chainloader	+1

title		Windows XP second test config
root 		(hd1,0)
makeactive
map		(hd0) (hd1)
map 		(hd1) (hd0)
chainloader	+1

---

### Post by confused57 on 2007-06-04
You need a space between the (hd0) (hd1) & (hd1) (hd0):

title Windows XP second test config
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by pete222 on 2007-06-05
duh. thanks you are right- I guess I needed a second set of eyes on it. thanks!!!!!

---

### Post by confused57 on 2007-06-05
> **pete222 said:**
> there are spaces between everything- its when I copied and pasted it changed.
What may have happened is that your Window's hard drive may have been changed from sdx to hdx, with the new kernel.

You might want to open a terminal, check the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

then check the output of:
```
gedit /boot/grub/device.map
```

You might need to change the hard drive designation in your device.map, according to what "fdisk -l" shows...I'm not sure if this is what happened or not, but worth a try.

---

### Post by pete222 on 2007-06-05
thanks but it was a silly oversite - I forgot to add spaces- edited grub and all is good now. thanks!!

---

