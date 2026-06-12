---
title: "Define mount point from USB-live?"
date: 2015-09-04
forum: General Help
---

### Post by john458 on 2015-09-04
I'm trying to install Lubuntu 14.04 on a 13gb space I've got before a bigger ntfs partition with data I want to keep. I've managed to created a 2gb swap and a 11gb ext4 partition with gparted from the live USB I'm running. The only thing missing is the mount point. The /etc/fstab I can open is only two lines starting with overlayfs an tmpfs, so I guess editing this is is not the way to proceed?

How to squeeze in the installation before the ntfs partition?

It seems the option 'create partition table' in the 'something else' installation wizard ignores and overwrites existing partitions...

---

### Post by sudodus on 2015-09-04
Welcome to the Ubuntu Forums :-)

At **Something else**

Select the 11 GB ext4 partition and 'Change' it: You will use it as ext4, root partition '/' and if you have already formatted it, you need not do that again.

The swap should be selected automatically.

Finally, at the bottom of the partitioning Window, check that you install the bootloader into the correct drive (there should be no digit, only /dev/sda or /dev/sdb ... )

---

### Post by TheFu on 2015-09-04
The only issue is if the system is UEFI. Then another partition will be needed. If the system is using UEFI BIOS, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) is worth a read.

---

### Post by john458 on 2015-09-05
Thanks guys, it all works like a charm now :) Can't believe I missed that '-/+/Change' button...

---

### Post by sudodus on 2015-09-05
I'm glad it works for you now :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

