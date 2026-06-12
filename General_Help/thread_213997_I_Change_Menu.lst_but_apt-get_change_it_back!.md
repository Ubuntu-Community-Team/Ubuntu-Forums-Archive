---
title: "I Change Menu.lst but apt-get change it back!"
date: 2006-07-12
forum: General Help
---

### Post by house001 on 2006-07-12
First , I install ubuntu in hda5 and windows in hda1. but later I changed partition structure so ubuntu is on hda7 and grub was fail to boot.
I used live cd to manual change  menu.lst and  it work well.

but after I update my kernel, apt-get install had changed my menu.lst to the old one and I must use live cd to change it back to work again.
how can I solve this problem , I don't want to manually edit menu.lst everytime I upgrade kernel.:-? 

Oh, last thing sorry for my horrible english.

---

### Post by RAOF on 2006-07-12
Near the top of your menu.lst, you'll fine some lines like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/storage-breezy--root ro

```
What you want to do is edit that kopt line, rather than each of the kernels individually.  Specifically, you want to have the final line there to look something like:
```

# kopt=root=/dev/hda7 ro

```
and then run **sudo update-grub**.  In future, any new kernels installed will use those options.

---

