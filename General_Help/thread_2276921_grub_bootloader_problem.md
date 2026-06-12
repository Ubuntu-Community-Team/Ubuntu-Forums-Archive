---
title: "grub bootloader problem"
date: 2015-05-05
forum: General Help
---

### Post by boydadam17 on 2015-05-05
Hi there, I have a laptop which I had setup to dual boot Windows and Ubuntu but I deleted the Ubuntu partition and was attempting to boot into gprated using a disc I created but now I can't seem to get into the bios to change the boot sequence it justs goes strait to the grub bootloader and says: "error no such partition Entering rescue mode". So now I'm stumped, stuck, and frustrated and need to get my computer working again or I'm screwed. Please help

Adam B.

---

### Post by yancek on 2015-05-05
Which windows?
Deleting a partition as you did will not have any effect on the BIOS.  You need to enter "setup" immediately on boot and change the boot priority.  If you get the error you mention, you are booting to the hard drive and haven't saved any change you made.

---

### Post by grahammechanical on 2015-05-05
You need to restore the Windows boot loader to load Windows.

During the installation of Ubuntu the Grub boot loader is installed into the MBR of the hard disk (assuming a BIOS motherboard) but it looks for its configuration files in a folder on the partition that Ubuntu is installed in. By deleting that partition you deleted the Grub configuration files and now it cannot draw a boot menu on the screen.

Do you have a Windows repair disk? That is the way to fix this. What would be the purpose of running Gparted? To re-create the deleted partition? That will not restore the data on it.

Re-installing Ubuntu would get you a working computer but you would be back to where you started from. You would still need to restore the Windows boot loader and then delete the Ubuntu partition. I have no idea how to restore a Windows boot loader.

If the partition was deleted by accident  then you might try Test Disk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Regards.

---

