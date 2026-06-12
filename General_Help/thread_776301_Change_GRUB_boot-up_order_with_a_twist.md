---
title: "Change GRUB boot-up order with a twist"
date: 2008-04-30
forum: General Help
---

### Post by Taifuu on 2008-04-30
I managed to change my bootup order on GRUB (because I cant use my keyboard/mouse during bootup because they are usb) but I wrote the wrong number because I didnt think that *Other Operating Systems:* was an actual option that counted.

So Im stuck with that one looping every time I start the computer, the only way for me to get past that is to boot with the ubuntu cd in my reader, so Im sitting on the test version atm.

Im wondering if its possible to change the GRUB boot-up order from where I am now? Or to get it reset so I can get back into my real version.

---

### Post by smoker on 2008-04-30
have a look here for help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

i would also check that all your usb options are enabled in your bios, this way should hopefully allow you to use the keyboard at the grub stage in future,

---

### Post by strabes on 2008-04-30
The easiest thing would be to boot from the live CD, mount the partition, and edit /boot/grub/menu.lst.

To do this, run these commands, assuming your root partition is /dev/sda1.

```
sudo mkdir /media/rootpartition
sudo mount /dev/sda1 /media/rootpartition
sudo gedit /media/rootpartition/boot/grub/menu.lst
```

---

