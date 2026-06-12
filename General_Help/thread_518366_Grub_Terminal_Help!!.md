---
title: "Grub Terminal Help!!"
date: 2007-08-05
forum: General Help
---

### Post by Ub1476 on 2007-08-05
Hi, I did some messing around with a new grub theme and such, and when booting I now end up in the grub command line. Could anyone tell me how to get into a *_normal_* command line, so I can edit menu.lts? I tried super-grub several times but I allways end up at th same destination. 

Thanks in advance.

---

### Post by Happy_Man on 2007-08-05
> **Ub1476 said:**
> Hi, I did some messing around with a new grub theme and such, and when booting I now end up in the grub command line. Could anyone tell me how to get into a *_normal_* command line, so I can edit menu.lts? I tried super-grub several times but I allways end up at th same destination. 

Thanks in advance.
I think the command is "boot".... but if that doesn't work, you can always boot a LiveCD to access your files. To do so, boot into the LiveCD, open a terminal, and enter these commands:

```
sudo mkdir /media/Install
sudo mount -t ext3 /dev/sda<partition number> /media/Install
```

Then you will be able to get to and edit your file.

---

### Post by Ub1476 on 2007-08-06
Yep, I fixed it. Just edited from media/disk/boot/grub, and changed menu.lts_backup to menu.lts:D

---

