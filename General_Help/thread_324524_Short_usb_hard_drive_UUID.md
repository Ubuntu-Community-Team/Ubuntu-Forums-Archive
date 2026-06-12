---
title: "Short usb hard drive UUID"
date: 2006-12-23
forum: General Help
---

### Post by Manuito on 2006-12-23
Hello,

Is it normal to have an only 8-digits UUID in a hard drive ??
```

manu@cuac:~$ ls -l /dev/disk/by-uuid/

lrwxrwxrwx 1 root root 10 2006-12-24 02:55 **[COLOR="Blue"]4900-4780[/COLOR]** -> [COLOR="SandyBrown"]../../sdb1[/COLOR]
```

I have had to change fstab to "/dev/sdb1" instead of "UUID=4900-4780" (as it was set up during installation), because otherwise system doesn't work properly (the hard drive actually mounts, system starts but I experience some strange behaviours).

All other drives mount properly, but they all use UUID that vary from 16 to 32 digits.

As I want to move the hard drive from one computer to another I'm thinking about setting "LABEL=" both in fstab and Grub (menu.lst), so I can use it everywhere... but I would like to know why I can't use UUID= on that specific drive. Why does it have such a short ID?? Is it because of an installation problem (no matter how many times you format the drive, you always get a short UUID)??

Thanks!!

---

### Post by TuxCrafter on 2006-12-26
Want to know the answer to.

It think that fat is limited to 2 byte section.

I tried gparted to generate a new vfat partition for my usbstick. It also generate a short uuid.

```
sudo vol_id /dev/sda1
```

```
blkid
```

They all gave me a screwed up info. I manually reformatted the usbdisk with this command:

```
sudo mkfs.vfat -n usbstick /dev/sda1
```

Now the info is ok but still a short uuid

fstab will not take my ID , LABEL or UUID only /dev/sda1 I think it is buggy

Noting I could do to fix it.

---

