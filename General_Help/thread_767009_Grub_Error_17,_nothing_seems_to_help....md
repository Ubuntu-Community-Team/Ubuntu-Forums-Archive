---
title: "Grub: Error 17, nothing seems to help..."
date: 2008-04-25
forum: General Help
---

### Post by poisonborz on 2008-04-25
Hola, I'm kinda at the point of desperation: I've installed hardy from livecd, wanted to dual boot, but Grub gave error 17 :( 
My partition list is simple as stick, and trough the livecd I can tell that everything should work... I've read tons of info, but nothing helped.

The boot order is the same in grub and in the bios, and I can see all drives properly in the livecd.

I also tried to reinstall ubuntu, and grub too (via this tutorial: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) but error 17 always appears.

the **---grub find /boot/grub/stage1** results in **(hd0,2)** as it should (?)


```
drives/partitions:
sda
 1-win
 2- -
 3-linux
sdb
 -
sdc
 -
```

```
device.map contents:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```

*(I know I could just pop in a Supergrub cd, but I can't burn since I'm in livecd, and also can't install to usb (I don't know where/why/how to mount it after file extraction) and the above facts suggest that this could be solved with a simple text edit anyway... )*

---

### Post by poisonborz on 2008-05-10
Okay, for anyone interested, I've finally found the solution, partly by mistake. In the bios, AHCPI mode (so in fact, SATA itself) was not turned on, this caused GRUB somehow not to see any Linux partitions. So, if you install to SATA drives, remember to check in the BIOS if they're set as SATA.

---

