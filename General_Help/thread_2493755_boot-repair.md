---
title: "boot-repair"
date: 2023-12-23
forum: General Help
---

### Post by mehdikerbelae on 2023-12-23
Hi Sir,
I did the boot-repair several times but it does not solve the problem. Please help me.
[http://paste.ubuntu.com/p/34XjMM8Y8d/](http://paste.ubuntu.com/p/34XjMM8Y8d/)
thank you

---

### Post by oldfred on 2023-12-23
You are showing 18.04 which is End of Standard support.
You should reinstall with 22.04. Make sure you have good backups including list of installed apps. But change from 18.04 to 22.04 may not be exactly same.

You also show the Microsoft Reserved partition sda2 as ext4. That has to be unformatted. Use gparted & change to unformatted.

You have old Linpus lite entries in UEFI.
You can remove those with efibootmgr.

man efibootmgr
sudo efibootmgr -v
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

---

### Post by QIII on 2023-12-23
Moved ti General Help

---

