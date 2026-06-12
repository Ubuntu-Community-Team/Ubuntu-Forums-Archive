---
title: "Is it safe to resize my root partition?"
date: 2007-09-19
forum: General Help
---

### Post by jalanbuntu on 2007-09-19
Hi all... I need to resize my root partition, because when I install my ubuntu I don't create the swap partition. So, I want to resize it and give a little space for swap.

What I want to ask is that safe to resize my root partition using feisty live cd/gparted live cd?
This my partition table,
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              26G   17G  8.1G  68% /
varrun                490M  276K  490M   1% /var/run
varlock               490M  4.0K  490M   1% /var/lock
procbususb            490M  124K  490M   1% /proc/bus/usb
udev                  490M  124K  490M   1% /dev
devshm                490M     0  490M   0% /dev/shm
lrm                   490M   33M  457M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda5              50G   50G  468M 100% /media/sda5
```

I want to resize /dev/sda1 and create the swap partition on it?
Please give your advice. I'm just worried that I will mess things up by resizing my root partition :D
Thanks

---

### Post by AusIV4 on 2007-09-19
You should be fine to resize it. I've heard stories of things going wrong, but I've never had any problem resizing partitions. Worst thing that's happened to me is that I tried to resize a partition and make it smaller than the data it held, and the partition editor flat out refused to do it.

Like I say, there are stories of things going wrong, but I think they're pretty rare.

---

### Post by jalanbuntu on 2007-09-19
Thanks AusIV4, you really convince me :)
I'll try it now. Wish that all things going smoothly. I'll report the result. Thanks again ;)

---

### Post by jalanbuntu on 2007-09-24
Finally, I don't resize my partition for swap. A friend of mine has gave me an advice to create a swap file in my ext partition. Then, violllllaaa.... now I get my swaps :D

---

### Post by strabes on 2007-09-24
Just in case you end up doing it, make sure you back up anything important because when shrinking partitions, things can and sometimes do go wrong.

---

