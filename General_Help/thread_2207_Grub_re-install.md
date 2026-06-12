---
title: "Grub re-install"
date: 2004-10-26
forum: General Help
---

### Post by matgorb on 2004-10-26
My flatmate had some problem with an Ubuntu install "eating" its mbr, he managed to fix windows boot, but now it is the other way arround as grub is absent. I can't figure how to re-install grub in ubuntu, and how, as I don't see any rescue option on the live CD. Last time this kind of stuff happend to me, it was with FC2 and booting from the CD in rescue mode I managed to re-install Grub, but there he booted with the FC2 CD but obviously it does't work. Do we have to chroot or something to re-install? I'm totally lost.

mat

---

### Post by Kopf on 2004-10-26
Is the entire Ubuntu installation on 1 partition or multiple partitions?

Kopf

---

### Post by FLeiXiuS on 2004-10-26
This should be the correct way, it may be one dash instead of two.  
 
```
apt-get install grub --reinstall
```

---

### Post by nutty on 2004-10-26
You could use MEPIS linux's CD to boot. The CD (MEPIS Installation --- something) allows you to install GRUB separately. You don't need to install MEPIS at all.

---

