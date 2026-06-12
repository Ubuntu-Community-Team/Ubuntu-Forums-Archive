---
title: "Predicament with GRUB..."
date: 2006-07-04
forum: General Help
---

### Post by Mazza558 on 2006-07-04
I want to replace GRUB with the original XP MBR, but I cannot use the FIXMBR command due to me not having the original XP CD (Recovery Partition). I also do not have a floppy disk drive, but I can burn a CD. Is there any boot disk I can use that will allow me to use the FIXMBR command?

---

### Post by Jagot on 2006-07-04
Download and burn the iso for the FreeDOS bootdisk:

[http://www.freedos.org/](http://www.freedos.org/)  

Put the disk in and reboot and work your way to the command prompt - it's fairly easy from the menu system.  Then at the prompt, type:

```
fdisk /mbr
```

---

### Post by Mazza558 on 2006-07-04
[QUOTE=Jagot]Download and burn the iso for the FreeDOS bootdisk:

[http://www.freedos.org/](http://www.freedos.org/)  

Put the disk in and reboot and work your way to the command prompt - it's fairly easy from the menu system.  Then at the prompt, type:

```
fdisk /mbr
```[/QUOTE]


Thanks, I'll give it a try.

---

