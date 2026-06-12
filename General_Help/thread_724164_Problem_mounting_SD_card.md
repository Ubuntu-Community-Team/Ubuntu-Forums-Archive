---
title: "Problem mounting SD card"
date: 2008-03-14
forum: General Help
---

### Post by datatek on 2008-03-14
Even after an entirely fresh 7.10 (eeeXubuntu rc3) install on, I can't access my 2gb SD card on my eeepc's card reader.

I put it in, the "2G Removable Volume" icon shows up on the desktop but when I try to open it I get

Unable to mount "2G Removable Volume": Unknown error

I know the card is physically fine because if I manually mount the card in the console, then I can access the card and see its contents, but also ONLY from the console: even after successfully manually mounting it in the console I still can't access it with the graphical file manager.

On previous eeexubuntu 3 installations it worked fine.

Please help :S

My fstab is as follows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0486021d-e608-4765-a617-9035fd37e431 /               ext2    defaults,noatime,errors=remount-ro 0       1
# /dev/sda2
UUID=e3213201-4029-4fdf-9025-9922e5369aac none            swap    sw              0       0
# /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Note, sdc1 is/was the usb stick I installed eeexubuntu from. My SD card is sdb1.

---

