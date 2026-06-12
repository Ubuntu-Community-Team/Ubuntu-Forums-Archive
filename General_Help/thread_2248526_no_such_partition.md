---
title: "no such partition"
date: 2014-10-15
forum: General Help
---

### Post by thierrytheunsvangemert on 2014-10-15
I had Win8.1 running with a dual boot option for Ubuntu. Today I was resetting my PC  for selling it, and I reinstalled Win8. Then I wanted to delete Ubuntu. I looked up a tutorial and it told me to delete the partition and then reboot the PC. When I rebooted I was greeted with the following error: 

Error: No such partition
Entering rescue mode...

Some important details:
I don't have a Win8 disk. Don't have the product key email anymore, and the only way for me to get the product key is to run Belarc Advisor, but for that I have to boot into Windows 8, which I can't. Any advice? I have a live USB with Ubuntu if that helps.

---

### Post by Michael_McKenney on 2014-10-15
If you no longer have the product key, call Microsoft and see if you registered it.   Media kits are $50+.  Other option is purchase a new one.  Hit F11 or F12 and see if the partition to rebuild Windows 8 still exists.

---

### Post by thierrytheunsvangemert on 2014-10-15
Where would I hit F11 or 12? Inside Ubuntu, the BIOS or during the error?

EDIT: I found out the Windows primary and secondary partition are intact, as well as the SYSTEM partition and the recovery partition.

---

### Post by yancek on 2014-10-15
How did you re-install windows 8 if you don't have a windows 8 disk?  Did you just do a recovery option?  If you were using Grub to boot Ubuntu and windows, when you deleted the Ubuntu partition, you also deleted almost all of the Grub files needed for booting.  You need to get the windows boot code in the mbr or on your EFI partition BEFORE you delete Ubuntu.  Most windows users haven't got a clue about bootloaders.  Bad advice from wherever.

You could probably do an online search for repairing windows 8 bootloader after removing Linux/Ubuntu.

---

### Post by thierrytheunsvangemert on 2014-10-15
> **yancek said:**
> How did you re-install windows 8 if you don't have a windows 8 disk?  Did you just do a recovery option?  If you were using Grub to boot Ubuntu and windows, when you deleted the Ubuntu partition, you also deleted almost all of the Grub files needed for booting.  You need to get the windows boot code in the mbr or on your EFI partition BEFORE you delete Ubuntu.  Most windows users haven't got a clue about bootloaders.  Bad advice from wherever.

You could probably do an online search for repairing windows 8 bootloader after removing Linux/Ubuntu.

I installed it using the Win8 installer on Microsofts website.

---

### Post by oldfred on 2014-10-15
That version requires a new product key as it is a new purchase.

The product key your system came with if a new system is in the UEFI and only is valid with the OEM vendor version of Windows.

If an older system, you have product key on bottom of system, but again that is for the vendor version.

You use the DVD set you made when you first booted system from recovery partition on your drive. Vendors do not normally provide separate DVDs to reinstall Windows any more. Or not since XP.

---

### Post by rbmorse on 2014-10-16
You can also get the "no such partition" error if the Windows boot partition is not marked as an "active partition" in the partition table. You might be able to set this from the Linux session with Gparted and setting the "boot" flag for that partition.

---

