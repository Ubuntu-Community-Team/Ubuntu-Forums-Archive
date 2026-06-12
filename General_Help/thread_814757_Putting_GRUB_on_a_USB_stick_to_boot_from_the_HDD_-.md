---
title: "Putting GRUB on a USB stick to boot from the HDD - how?"
date: 2008-06-01
forum: General Help
---

### Post by theophile on 2008-06-01
I have a Dell desktop with the worst BIOS in the world - you cannot boot off of IDE hard drives, SATA only. Now, in order to boot, I have to hit F12 at startup to get the boot menu, then manually select "Primary Master" form the list.

Anyway, since it CAN boot from a USB device, I want to install GRUB an an old 32MB pen drive I found so it will boot off the IDE hard drive without user intervention.

I'm not trying to make a bootable USB drive knoppix thing, I'm just trying to get a USB device to "hand off" to the HDD. Can I do this?

---

### Post by quelx on 2008-06-01
This may get you in the right direction (like syslinux but for ext3/2 formated partitions)

[http://syslinux.zytor.com/extlinux.php](http://syslinux.zytor.com/extlinux.php)

It looks like you will also need info from syslinux (it uses many of the same options)

[http://syslinux.zytor.com/faq.php](http://syslinux.zytor.com/faq.php)

---

### Post by Unix_Slayer on 2008-06-01
Try this..... ==>[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

