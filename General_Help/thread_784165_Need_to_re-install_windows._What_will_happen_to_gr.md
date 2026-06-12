---
title: "Need to re-install windows. What will happen to grub-loader?"
date: 2008-05-06
forum: General Help
---

### Post by sipickles on 2008-05-06
Hi,

At work, I use Hardy 8.04 (and have succeeded in converting a few folk! ;) )

Unfortunately, I need to keep dual boot with windows XP, since some USB hardware I have to use is not supported by Linux (picoscope, MPLAB ICD2).

Now, my winXP installation is old and choked  - you know how windows gets after a while, and I need to use the recovery CD to start afresh.

I think I can get the recovery CD to only install windows onto the first partition, thus preserving my Ubuntu partitions. However the MBR will be reset.

Is there a tool I can use afterwards to find the Ubuntu boot and restore the grub loader?

Thanks

Simon

---

### Post by warp99 on 2008-05-06
You can use the Ubuntu CD to restore Grub or use the Super Grub Disc:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Instructions can be found here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29)

Please see my signature for more helpful tips.

---

### Post by kellemes on 2008-05-06
> **sipickles said:**
> Hi,

At work, I use Hardy 8.04 (and have succeeded in converting a few folk! ;) )

Unfortunately, I need to keep dual boot with windows XP, since some USB hardware I have to use is not supported by Linux (picoscope, MPLAB ICD2).

Now, my winXP installation is old and choked  - you know how windows gets after a while, and I need to use the recovery CD to start afresh.

I think I can get the recovery CD to only install windows onto the first partition, thus preserving my Ubuntu partitions. However the MBR will be reset.

Is there a tool I can use afterwards to find the Ubuntu boot and restore the grub loader?

Thanks

Simon

[Super Grub Disk]("http://www.supergrubdisk.org/")
Boot from it.. it will give you a hole bunch of cool options to play around with the MBR.
Windows will overwrite the MBR but obviously not the Grub config-file (/boot/menu.lst) so you can use Super Grub Disk to reinstall Grub based on the /boot/menu.lst from your current Linux install.
Works great.

---

