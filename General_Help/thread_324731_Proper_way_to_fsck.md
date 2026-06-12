---
title: "Proper way to fsck"
date: 2006-12-24
forum: General Help
---

### Post by Didjit on 2006-12-24
Every now and then when my cpu wakes up from Suspend to Ram, I get a SATA Drive I/O error which causes me to reboot and fsck to run. It never runs automatically and requries a manual run. When I run it manually, I just select "YES" for every repair option.

Question, what is the proper way to run (w/switches) fsck so it automatically repairs?

Tx

Didjit

---

### Post by meng on 2006-12-24
Googling for "man fsck" (or running man fsck on your own system!) gave this answer:
fsck -y ....
[effect - assume answer of yes to any question]

---

### Post by viper on 2006-12-24
Is running fsck -y ok to run periodically like for eg scandisk or defrag  is for windows, just curious.

---

### Post by dcstar on 2006-12-24
> **Didjit said:**
> Every now and then when my cpu wakes up from Suspend to Ram, I get a SATA Drive I/O error which causes me to reboot and fsck to run. It never runs automatically and requries a manual run. When I run it manually, I just select "YES" for every repair option.

Question, what is the proper way to run (w/switches) fsck so it automatically repairs?

Edit /etc/default/rcS with:
```
FSCKFIX=yes
```
and it will automatically fsck with "Y" on boot (if required).

---

### Post by dcstar on 2006-12-24
> **viper said:**
> Is running fsck -y ok to run periodically like for eg scandisk or defrag  is for windows, just curious.

Yes, you can actually "tune" your EXT2/3 filesystem to run fsck after X reboots or N period (hours, days, weeks etc.)

See: ```
man tune2fs
``` for more info

---

### Post by viper on 2006-12-28
> **dcstar said:**
> Yes, you can actually "tune" your EXT2/3 filesystem to run fsck after X reboots or N period (hours, days, weeks etc.)

See: ```
man tune2fs
``` for more info

Thanks dcstar.........

---

