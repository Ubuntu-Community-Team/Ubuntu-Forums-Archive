---
title: "Resize drive and install Windows for Dual Boot"
date: 2012-11-06
forum: General Help
---

### Post by CrusaderAD on 2012-11-06
Any tips on how to take a full Ubuntu installation and resize it, installing windows in the new partition?

---

### Post by Mark Phelps on 2012-11-06
You can't resize a partition while it's in use, so you have to boot from a CD or USB and use GParted (Gnome Partition Editor) to shrink down the Ubuntu partition.

Then, you should be able to boot from the Windows installation media, create the partition needed, and install it.

Windows will overwrite the GRUB code in the MBR when it installs, so you will have to use an Ubuntu LiveCD or LiveUSB to restore that.

---

### Post by jroa on 2012-11-06
What Mark Phelps said.  Also, don't try to put the free space at the beginning.  You will likely have trouble booting Ubuntu if you do.  Put the free space at the end.

In addition, if you don't have a problem with re-installing Ubuntu, you might want to think about installing Windows on the whole drive, then partition and install Ubuntu.  It is not necessarily to do it that way, but you won't have to deal with the Grub issue afterwards.

And lastly, make sure the partition for Windows is a primary partition, not a logical one.

---

### Post by CrusaderAD on 2012-11-06
Thanks for the tips. I ended up using jroa's suggestion and installing Windows, then re-installing Ubuntu.

---

