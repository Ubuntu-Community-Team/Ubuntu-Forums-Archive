---
title: "External USB drive on edgy server"
date: 2007-04-09
forum: General Help
---

### Post by stijn on 2007-04-09
I've attached a USB hard drive to my Edgy system, it's a server install. To access it, I use following line in /etc/fstab

/dev/sda1       /mnt/usbdrive   ext3    user,noauto     0       0

When I acces it with my portable, it gets autoloaded, and I transfered all my precious files to the disk. After plugging it back to the server system, only a small amount of the files is visible/mounted. Anyone any idea?

Thanks in advance.

---

### Post by CyBuzz on 2007-04-09
I would plug it back in to the 'portable' and see if all the files are there.  if they are, then I would check permissions on the ones that are missing when you plug it into the server.  if they arent there they are either lost or still in their original location and didnt get copied.

---

