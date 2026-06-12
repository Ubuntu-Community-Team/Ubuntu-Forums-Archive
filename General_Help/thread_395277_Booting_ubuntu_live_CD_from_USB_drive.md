---
title: "Booting ubuntu live CD from USB drive"
date: 2007-03-27
forum: General Help
---

### Post by musther on 2007-03-27
I'm trying to boot the ubuntu live system from my usb drive (along with other things) using grub.  I've copied the contents of the casper directory to /ubuntu on my drive, and added this to grub:

```
title Ubuntu 6.10
root (hd0,0)
kernel /ubuntu/vmlinuz root=/dev/ram0 PMEDIA=usbhd
initrd /ubuntu/initrd.gz 
boot
```

And although it starts to boot, it quickly grinds to a halt saying that it cant run some script or other.

Has anyone done this before?  If so, how can it be done?

Thanks.

---

### Post by dcstar on 2007-03-28
> **musther said:**
> I'm trying to boot the ubuntu live system from my usb drive (along with other things) using grub.  I've copied the contents of the casper directory to /ubuntu on my drive, and added this to grub:

```
title Ubuntu 6.10
root (hd0,0)
kernel /ubuntu/vmlinuz root=/dev/ram0 PMEDIA=usbhd
initrd /ubuntu/initrd.gz 
boot
```

And although it starts to boot, it quickly grinds to a halt saying that it cant run some script or other.

Has anyone done this before?  If so, how can it be done?

Thanks.

Do a forum search for usbpendrive.

---

### Post by mahiyar on 2007-03-28
Try this link it worked for me [http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160) , it even supports persistence.

---

