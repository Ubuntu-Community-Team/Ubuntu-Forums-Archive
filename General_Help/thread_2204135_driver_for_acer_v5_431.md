---
title: "driver for acer v5 431"
date: 2014-02-06
forum: General Help
---

### Post by AbhimanyuAryan on 2014-02-06
i have used ubuntu for a while on my last dell laptop but now i broke that laptop and bought a new laptop acer v5 431 with pre-installed windows7 can i get intel graphic card+ wifi+Lan drivers ? for it....if yes where? will they be installed during ubuntu installation automatically? plz plz):P):P

---

### Post by PotatoHead007 on 2014-02-07
Um yea it should work. To be sure, just boot into a LiveCD and check :P But i checke the specs, and i am sure it will work.

---

### Post by AbhimanyuAryan on 2014-02-08
> **PotatoHead007 said:**
> Um yea it should work. To be sure, just boot into a LiveCD and check :P But i checke the specs, and i am sure it will work.

yaa its working i installed it....but can you tell where can i install install intel graphic card driver...and touchpad glitches a bit....what should be the ideal setting for it?:o

---

### Post by prasys on 2014-02-09
Can you post your 

```
 lspci 
``` 

```
 lsusb
``` (I am not sure if your touchpad is connected to the system via PS2 or USB) but just post this as well 

output and as well as 

```
lspci -vn | grep 'VGA'
``` - I just want to capture the device id and vendor id

---

### Post by PotatoHead007 on 2014-02-13
Ah sorry for not answering earlier :( Do what **prasys **said :)

---

