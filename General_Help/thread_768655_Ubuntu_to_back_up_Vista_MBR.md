---
title: "Ubuntu to back up Vista MBR?"
date: 2008-04-26
forum: General Help
---

### Post by Zacha on 2008-04-26
Short version:
Now: Vista and Ubuntu dual-boot with Vista bootloader
Want: Vista, XP and Ubuntu triple-boot with Vista bootloader
Problem: XP will overwrite Vista MBR.
Possible solution?: Use Ubuntu to back up Vista MBR, install XP, boot into Ubuntu through CD, restore Vista MBR from backup. Triple boot with Vista MBR.

Long version:
If you want the long version ask for it =P

(It's the "Possible Solution?" that is my "question")

---

### Post by SOULRiDER on 2008-04-26
Why dont you install XP, and thenw ith the Ubuntu Live CD install GRUB? It will automagically give you options for Ubuntu, vita and xp and its less of a hssle to set up.

---

### Post by Zacha on 2008-04-26
Because I don't like GRUB ;)

Jokes aside, I want to be able to remove Ubuntu and XP if I need to and have Vista working by itself. It just feels better to keep the Vista bootloader as Vista is and will be my main OS for a long time probably.

---

### Post by SOULRiDER on 2008-04-26
But it will probably be a pain in the *** everytime you get a new kernel.

---

### Post by Zacha on 2008-04-26
Why? I don't understand what a kernel upgrade would care if my GRUB is in the MBR or on the partition?

---

### Post by ryanhaigh on 2008-04-26
[http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html](http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html)

---

### Post by Zacha on 2008-04-26
> **ryanhaigh said:**
> [http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html](http://www.cyberciti.biz/tips/linux-how-to-backup-hard-disk-partition-table-mbr.html)
Thanks.

It will work fine even with Vista's MBR then?

---

### Post by ryanhaigh on 2008-04-26
The MBR size and location should be standard as far as I know, although this is vista, they have probably found a way to bloat it (sorry couldn't resist)

---

### Post by Zacha on 2008-04-26
No offence taken at all. You probably are right ;)

But about the "If you keep Vista MBR you will have problems updating kernel" thing. What's the problem and why?

---

