---
title: "clone an LVM drive"
date: 2013-02-09
forum: General Help
---

### Post by ulao on 2013-02-09
Trying to clone an LVM drive with clonezilla. It was able to close the grub sda1 but when attempting the sda2 it says /dev/sda2 not found? then failed to find this partition in this system /dev/sda1. It goes on to make a few guess attempts and eventually gives up. 

Also during the booting of clonezilla live CD it failed to mount the LVM.

Any other tools out there?

---

### Post by ulao on 2013-02-09
Apparently Clonezilla made changes to my grub. I rebooted and tried again and it worked.

---

