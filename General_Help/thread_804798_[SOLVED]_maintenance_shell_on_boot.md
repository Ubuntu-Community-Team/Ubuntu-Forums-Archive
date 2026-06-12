---
title: "[SOLVED] maintenance shell on boot"
date: 2008-05-23
forum: General Help
---

### Post by ainsworth on 2008-05-23
Recently my computer was scheduled to do the routine fschk on boot, however before it got a chance to do the scan on my second non-Ubuntu partition I installed another os on there and began dual booting again. The parition ID got changed in the process I assume as now everytime I boot fschk says it can't resolve it and dies. A maintenance shell then loads, which I can terminate with Ctrl-D and the boot then carries on no problems. How can I stop it trying to check the old partition? Thanks!

---

### Post by sisco311 on 2008-05-23
You need to change the UUID of the partition in fstab.
To get the uuid type:
```
sudo blkid /dev/sd**XY**
```
(Replace XY with the proper partition number)
Edit the fstab:
```
gksu gedit /etc/fstab
```and replace the old uuid of the partition with the new one.
for example:
```
sudo blkid /dev/sdXY
```> /dev/sda1: UUID="**XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX**" TYPE="ext3" ----->
> # /dev/sd**XY**
UUID=**XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX** /media/mountpoint  ext3    defaults        0       2

---

### Post by ainsworth on 2008-05-23
Thanks a lot for that, working perfectly again! :)

---

