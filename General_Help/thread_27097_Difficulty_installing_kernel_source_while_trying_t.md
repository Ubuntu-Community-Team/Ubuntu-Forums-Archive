---
title: "Difficulty installing kernel source while trying to get wireless working"
date: 2005-04-14
forum: General Help
---

### Post by ortazel on 2005-04-14
Hi, I'm trying to get my Trendnet TEW-421PC wireless card working on my laptop with Hoary. I'm following this guide- 

[http://www.houseofcraig.net/acx100_howto.php#trouble_compiling](http://www.houseofcraig.net/acx100_howto.php#trouble_compiling)

(My card is based on the ACX111 chipset)
However, I get to the part where I try to install the kernel source, and this command-
```
ls /lib/modules/`uname -r`/build/include/linux/version.h
```
returns No Such File or Directory. I've tried every different kernel source installed through apt-get and Synaptic, and nothing puts a folder called build inside my /lib/modules/2.6.10-5-386 directory.

Any help is much appreciated, and thanks to everyone here for all the help I've used so far :)

---

### Post by ortazel on 2005-04-14
Solution! (thanks bob2 in #ubuntu :) )

To install kernel-source, use this instead-
```
 apt-get install linux-headers-$(uname -r)
```

---

