---
title: "Kernel module size"
date: 2007-05-20
forum: General Help
---

### Post by Nakah on 2007-05-20
Hi,
When I'm building my custom kernel (I need it in order to boot with intelfb module), generated modules are too big if we compare it with the original ubuntu modules. For example, intelfb.ko  :
2.6.20-15-generic :    46392
2.6.21.1 :                422981

It's almost 10 times bigger, not only for intelfb module but for **all**.

I tried to compile with CONFIG_CC_OPTIMIZE_FOR_SIZE but it doesn't work.

My question is : How should I compile my kernel in order to reduce module size.

---

### Post by Bachstelze on 2007-05-20
Could you please tell ust what commands you ran to get those figures ?

---

### Post by Nakah on 2007-05-20
I'm just using ls command :
ls -l /lib/modules/2.6.20-15-generic/kernel/drivers/video/intelfb 
ls -l /lib/modules/2.6.21.1/kernel/drivers/video/intelfb

---

### Post by antiplex on 2007-06-01
i'm having similar issues and described them [here (posts # 378 & 379)]("http://ubuntuforums.org/showthread.php?t=311158&page=38") but haven't found any soultion so far :(
hints are very welcome...

edit: i found others have asked something like this before (like in [this thread]("http://ubuntuforums.org/showthread.php?t=417138") for instance) but nobody seemed to bother, either most people don't check the sizes of their built kernels/modules/initrds or this is a very rare problem that only happens to bloody kernel-compile-beginners...

---

### Post by antiplex on 2007-06-05
issue solved, check the 2nd link of my prev posting. ;)

---

