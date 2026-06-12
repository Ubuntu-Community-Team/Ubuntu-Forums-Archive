---
title: "Uninstall Ubuntu"
date: 2007-09-27
forum: General Help
---

### Post by psychicpanda on 2007-09-27
If I just format all partitions that Ubuntu is using, why does it not get rid of GRUB 1.5 on startup, as this causes an error 22, and prevents me from doing anything until i reinstall Ubuntu
So how do I get rid of GRUB 1.5???

---

### Post by lisati on 2007-09-27
Grub uses a separate part of the disk, sometimes called the "Master Boot Record", to get started. Deleting the Ubuntu partitions doesn't usually wipe or reset this area. You will (edit: might) need to use something like the "fixmbr" tool that comes with some versions of Windows

edit: Other people might have other ideas which might help

---

### Post by hessiess on 2007-09-27
use your windows restore cd, get to the recovery termanal and run fixmbr, to restore the windows bootloader

---

### Post by foxmulder881 on 2007-09-27
If you're not comfortable using the Windows Recovery Console solution, you can also boot from Super GRUB disk and restore your Windows Master Boot Record from it.

Google "**Super Grub Disc**" and you'll be sure to find it.

---

