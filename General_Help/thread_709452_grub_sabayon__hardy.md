---
title: "grub sabayon / hardy"
date: 2008-02-27
forum: General Help
---

### Post by 1fl on 2008-02-27
Sabayon  on sda Hardy on sdb.  This is a 2nd box connected by a usb kvm switch, If I try to get at a command line on a live cd I lose the usb keyboard.  Looks like I need to fix with cl in ubuntu/ hardy, as that is what it boots to. Never had to repair grub before, any help would be appreciated. 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x859977fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        4865    38973690   8e  Linux LVM

Disk /dev/sdb: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af50af4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1578    12675253+  83  Linux
/dev/sdb2            1579        1653      602437+   5  Extended
/dev/sdb5

---

### Post by jken146 on 2008-02-28
Which distro did you install last?  Whose GRUB is on the MBR -- Ubuntu's or Sabayon's (I'm guessing it's Ubuntu's as that's what you say you're booting to)?  Please post the contents of /boot/grub/menu.lst for both distros.

---

### Post by 1fl on 2008-02-28
Yes, it was ubuntu's grub. Seems to be a common problem with sabayon and, there is a lot of info in their forums to fix this. So last night I reinstalled sabayon. And it did not pick up the ubuntu/hardy distro. It is not a hardy issue as it is the same with debian, gutsy, and kubuntu. On my main box I run sabayon/xp and, had no issues with grub.
Thanks for the reply I will go to the sabayon forums and have a multitude of previous  answers for this problem. Just wonder why gentoo does not play well with others.

---

