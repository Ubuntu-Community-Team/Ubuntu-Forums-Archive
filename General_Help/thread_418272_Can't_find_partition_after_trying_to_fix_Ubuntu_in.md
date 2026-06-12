---
title: "Can't find partition after trying to fix Ubuntu installation"
date: 2007-04-22
forum: General Help
---

### Post by Ventura87 on 2007-04-22
My Ubuntu installation won't boot after what seems as a powerdown where i live, my computer was even running Windows at the time, but when i try to boot Ubuntu (Edgy Eft) i get this error: /bin/SH: can't access TTY; job control turned off.

I did some googling around and discovered that it might had something to do with the bootloader(grub). Then i popped in the Ubuntu live cd and reinstalled grub. That did not work, and i got the same error when i boot. 
After that i booted into Windows and found out that one of my partitions weren't available, i get the "The disk is not formatted, format now ?" message when i try to access it. 

The disk is partitioned like this :
 E: (Windows install)@60GB---Linux swap@4GB---Linux Ext3(Ubuntu install)@60GB---M:NTFS@114GB

M: is the partition I can't access. I know it's a little messed up, but I don't want to lose the files on it.

As you can see i've actually got two problems here, and I really hope that someone cant help me :confused:

---

