---
title: "Checking file systems on boot?"
date: 2007-02-08
forum: General Help
---

### Post by Red Knuckles on 2007-02-08
Is there any way to get rid of the annoying 'Checking file systems... /dev/hda# has been mounted 30 times... check forced' on boot?

---

### Post by taurus on 2007-02-08
Change the last digit in /etc/fstab from 1 or 2 to 0.  However, it is strongly recommended you have the fsck check thing in there to ensure the healthy of your ext3 partitions.

```
gksudo gedit /etc/fstab
```

---

### Post by ^rooker on 2007-02-08
I have a question regarding the opposite direction:
Where's the good old "**filesystem not cleanly unmounted - check forced**" in Ubuntu?

---

### Post by Red Knuckles on 2007-02-08
> **taurus said:**
> Change the last digit in /etc/fstab from 1 or 2 to 0.  However, it is strongly recommended you have the fsck check thing in there to ensure the healthy of your ext3 partitions.

```
gksudo gedit /etc/fstab
```

Thanks taurus. I do use fsck I just like to decide when instead of bootloader.

---

