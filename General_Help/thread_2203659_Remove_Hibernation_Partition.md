---
title: "Remove Hibernation Partition"
date: 2014-02-04
forum: General Help
---

### Post by magikarp2 on 2014-02-04
I have two extra partitions on my first drive. One entitled 'Extended Partition' and the other 'Swap'. I no longer wish to be able to hibernate as I usually use suspend or shutdown and would like to free that space back up. I've removed the hibernate package but are unsure on the two partitions. Do I need both for just using suspend?

---

### Post by grahammechanical on 2014-02-04
I do know that the swap partition is used to store the system memory state when we hibernate Ubuntu. I also know that Hibernation is not enabled by default. But the swap partition is also used to page out data from RAM when system memory gets used up. Removing the swap partition should not cause Ubuntu to stop working but it is traditional to have some swap space especially if the machine does not have massive amounts of RAM.

The Extended partition is a special kind of primary partition that allows those of us on MBR boot systems to work around the 4 primary partition limit that MBR boot systems have.

Suspend is actually suspend to RAM. Most of the hardware is switched off but the RAM is still powered up. We do not need swap space when using suspend.

[https://wiki.archlinux.org/index.php/Suspend_and_Hibernate](https://wiki.archlinux.org/index.php/Suspend_and_Hibernate)

Regards.

---

