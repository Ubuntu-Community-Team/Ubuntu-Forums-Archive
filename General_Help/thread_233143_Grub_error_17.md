---
title: "Grub error 17"
date: 2006-08-09
forum: General Help
---

### Post by cyclister on 2006-08-09
So now I found something that might be useful.
Did run this command in knoppix less /etc/fstab


/proc      /proc       proc   defaults            0 0
/sys       /sys        sysfs  noauto              0 0
/dev/pts   /dev/pts    devpts mode=0622           0 0
/dev/fd0   /mnt/auto/floppy auto   user,noauto,exec,umask=000    0 0
/dev/cdrom /mnt/auto/cdrom  auto   user,noauto,exec,ro 0 0
# Added by KNOPPIX
/dev/hda5 /mnt/hda5 auto noauto,users,exec 0 0
# Added by KNOPPIX
/dev/hda6 none swap defaults 0 0
# Added by KNOPPIX
/dev/hda7 /mnt/hda7 ext3 noauto,users,exec 0 0
 swap swap defaults 0 0

Do not really know what do do?

---

### Post by vijirajan on 2006-08-09
Can you explain the error in little more detail? I am not able to comprehend the problem from your descriptions.

---

