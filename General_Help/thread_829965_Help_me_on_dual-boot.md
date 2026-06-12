---
title: "Help me on dual-boot"
date: 2008-06-15
forum: General Help
---

### Post by babylon2233 on 2008-06-15
I want to install Fedora on my second partition. Now, I already have Ubuntu install on my first partition.Based on what I heard from some forum, Fedora installer will overwrite the MBR. So, what I need to do to make sure I still able to boot Ubuntu.

---

### Post by melopsittacus on 2008-06-15
You can install Fedora's boot loader on a floppy instead of the MBR

or

you could let Fedora overwrite the MBR: I think Fedora's GRUB will include an item also for Ubuntu
(at least it worked for me like that, though the other way round:
I already had Fedora installed and when I added Gutsy, its bootloader included Fedora)

---

### Post by babylon2233 on 2008-06-15
If you installed Fedora first then it should be alright but now I already have Ubuntu installed and not willing to completely reinstall everything.

---

### Post by meierfra. on 2008-06-15
During installation, Fedora lets you choose the location  for Grub. Just choose grub to be installed on the fedora partition. 

Then edit the Ubuntu menu.lst as follows:

```
gksudo gedit /boot/grub/menu.lst
```

and add this to the end of the file:

title Fedora
root (hd1,3)
chainloader +1

Of  course you will have to use different numbers.  Grub starts counting at zero. (hd1,3) means 4th partition on the 2nd hard drive. Choose the numbers appropriate for your fedora partition.



But melopsittacus is also right. You can just install the Fedora Grub to the MBR. This overwrites the Ubuntu Grub, but Fedora will add Ubuntu to the Fedora menu.lst. So you will be able to boot into Fedora and Ubuntu from the Fedora Grub menu.

---

