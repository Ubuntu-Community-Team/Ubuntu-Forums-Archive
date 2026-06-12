---
title: "Installing Linux generic-pae kernel"
date: 2012-11-30
forum: General Help
---

### Post by kleenex on 2012-11-30
Hi, short question; If I use the generic kernel and I want to change it to the generic-pae, I only must install e.g. [COLOR=SeaGreen]linux-image-3.2.0-34-generic-pae[/COLOR] package and reboot computer, right? I'm asking, because I found computer with Intel Celeron dual core 2.40 GHz and I thought, that it will be better to install/use pae kernel instead of generic. 

Thanks!

---

### Post by Lyfang on 2012-11-30
Since nobody replied. Is done at your own risk and I take no responsibility for any loss or damage (as usual). I would download the latest PAE Linux kernel available and reboot. I would use caution when removing any old kernel, especially before trying the new PAE kernel. You could also (backup your personal files and) install a Xubuntu 64-bit system.

---

### Post by kleenex on 2012-11-30
Hello **Lyfang**. Thanks for the answer. I'm asking, because, if I remember correctly, I've read on the Linux Mint website, that it is enough to install pae kernel and reboot. I thought that maybe someone on the forum has already done something similar.

---

### Post by dino99 on 2012-11-30
installing a kernel means to install BOTH image & headers of such kernel (dkms also might already installed)

is that cpu able to use pae ?

cat  /proc/cpuinfo 
(you might find pae in the list, otherwise it cant use pae)

do you need pae ?
a pae kernel allow to use more than 3 Gib of ram; meaning that if your pc have less than 4 Gib of ram, no need to install a pae kernel.

---

### Post by kleenex on 2012-11-30
Hi **dino**. Yes, my computer support PAE. That's for sure. I know all those thing about PAE. I want to install pae kernel, because of; two cores and NX bit, which seems to not work, now etc. I also know, that amount of RAM memory, really does not matter and pae kernel can be install even on system with 1 GB of RAM memory. 

Regards!

---

