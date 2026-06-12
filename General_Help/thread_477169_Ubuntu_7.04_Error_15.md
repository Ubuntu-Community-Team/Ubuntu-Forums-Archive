---
title: "Ubuntu 7.04 Error 15"
date: 2007-06-18
forum: General Help
---

### Post by namanbagga on 2007-06-18
I was using Windows Xp and I installed Ubuntu 7.04 in dual booting with XP.I lost GRUB after messing up my MBR by using the Windows XP cd,so I reinstalled GRUB.But the partition locations have changed
/dev/sda6 has become /dev/sda9 and vice versa.
Whenever I try to start ubuntu an error is displayed-
Error 17:The selected partition can't be mounted.

I've edited th fstab file according to the new names.But it still isn't working .I need help!!!!!

---

### Post by confused57 on 2007-06-18
> **namanbagga said:**
> I was using Windows Xp and I installed Ubuntu 7.04 in dual booting with XP.I lost GRUB after messing up my MBR by using the Windows XP cd,so I reinstalled GRUB.But the partition locations have changed
/dev/sda6 has become /dev/sda9 and vice versa.
Whenever I try to start ubuntu an error is displayed-
Error 17:The selected partition can't be mounted.

I've edited th fstab file according to the new names.But it still isn't working .I need help!!!!!
Boot the live cd and post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Your menu.lst root entry and the kernel root(UUID or /dev/sdx)  has probably changed.

---

