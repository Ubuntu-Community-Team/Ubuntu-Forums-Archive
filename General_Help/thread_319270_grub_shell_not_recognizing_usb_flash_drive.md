---
title: "grub shell not recognizing usb flash drive"
date: 2006-12-15
forum: General Help
---

### Post by paridoth on 2006-12-15
i am attempting to install grub on my flash drive however grub isn't even recognizing it, or my usb hard rive for that matter. i am running it with the grub command from my command line in ubuntu, and have tried several different methods to get grub to see the drive, including using find to locate the stage files i have placed in the usb drive, but nada. if i remember correctly in order to get grub, which is installed on a linux machine, to recognize a drive you must edit device.map and add the drives. which i have done like so

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
```

the first two drives being my internal sata drives which grub recognizes perfectly, and the last two being my usb drives which grub is not recognizing at all, i cant even root to them. is there something i am missing?

---

### Post by paridoth on 2006-12-16
both of the usb drives are being mounted automaticly, and i edited them into the device.map after i installed the system, as they wheren't conected while i was installing ubuntu and wherent in the device.map could this have anything to do with it?

---

### Post by paridoth on 2006-12-17
well i just remembered that i could bypass the hd0 ECT. naming system and use linux naming for disks and simply ran sudo grub-install /dev/sdd which installed it just fine

---

