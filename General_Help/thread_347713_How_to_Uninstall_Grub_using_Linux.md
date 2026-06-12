---
title: "How to Uninstall Grub using Linux"
date: 2007-01-27
forum: General Help
---

### Post by joelbryan on 2007-01-27
Alot of people are still wondering how to uninstall grub using Linux.
It's really easy.

1. Create a backup of your MBR

```

dd if=/dev/hda of=MyMBR.img bs=446 count=1

```

2. Clear your MBR (note: I use /dev/null, not /dev/zero)

```

dd if=/dev/null of=/dev/hda bs=446 count=1

```

3. Reboot


Troubleshooting

Incase of a disaster, boot from a live cd, backup your data, or 
restore your mbr and run dos fdisk /mbr

dd if=MyMBR.img of=/dev/hda bs=446 count=1

To use rescue mode, use a live-CD/Rescue-CD
then from the command prompt,

fdisk -l (to list your linux partition, hda2 is an example)
mount /dev/hda2 /mnt
chroot /mnt
from there, perform the dd operations to restore your MBR, or backup your data.

If your partition table had been altered, use gpart, [http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

you can install gpart by enabling multiverse, and spt-get install gpart.

---

