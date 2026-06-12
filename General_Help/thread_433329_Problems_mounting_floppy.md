---
title: "Problems mounting floppy"
date: 2007-05-04
forum: General Help
---

### Post by juantovarm on 2007-05-04
Ok, can anyone help me? i have some serious problems with my floppy device, it simply doesn't mount, here is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3834dc4-24dd-496f-bb78-e528d5b502b7 /               ext3    defaults,erro$
# /dev/sda5
UUID=591bf617-fec5-45dc-918f-d86e3cc2e5e3 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto rw,user,noauto     0       0

When i try to mount using sudo mount /media/floppy0, it tels me /dev/fd0 is not a valid block device (sorry, translating from spanish)
:confused: :confused: :confused: 

Thanks

---

### Post by crispy_420 on 2007-05-05
Is there data on it? If blank, you may to format it first. When unmounted, right click and select format. Go for dos format, no need for linux format. Then try and mount again.

---

