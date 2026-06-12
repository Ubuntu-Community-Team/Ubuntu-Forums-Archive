---
title: "Copying my partition to a new drive."
date: 2007-09-03
forum: General Help
---

### Post by Jriske on 2007-09-03
Right now I have two IDE drives. I dual boot Windows XP on HDA, and Linux on HDB. I just bought a 500gb SATA drive. I would like to switch Linux over to the 500gb drive along with other partitions. I can partition it fine. How do I move Linux/Grub over to the new drive? I installed grub in HDA and linux is on HDB. I would also have to edit fstab too, correct?

---

### Post by Rui Pais on 2007-09-03
Hi,

[here a thread on the same topic]("http://ubuntuforums.org/showthread.php?p=2867276#post2867276"), that should give you some help.

good luck.

---

### Post by Jriske on 2007-09-03
Thanks, are the steps almost the same for IDE > SATA?

The main concern is grub is install on my Windows partition, not my Linux partition. How do I reinstall grub so it's no longer on HDA, and it loads on my SATA drive?

---

### Post by Rui Pais on 2007-09-03
> **Jriske said:**
> Thanks, are the steps almost the same for IDE > SATA?
yes, the only thing is that /etc/fstab must have the correct /dev/sdxx or the equivalent UUID.

> The main concern is grub is install on my Windows partition, not my Linux partition. How do I reinstall grub so it's no longer on HDA, and it loads on my SATA drive?

You mean that grub loader is installed on MBR of drive that contain Windows. Grub is installed under your /boot partition or on some ext3 dedicated partition.

To reinstall grub loader, just check some of those links:
[Restore grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-7fb1c88570b006aa14b7daaef2238b432b7f73c8")
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)
or those threads, with plenty info:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

:)

---

### Post by Jriske on 2007-09-03
Thanks, The search feature is strong in you Ubuntu Master. ;)

---

