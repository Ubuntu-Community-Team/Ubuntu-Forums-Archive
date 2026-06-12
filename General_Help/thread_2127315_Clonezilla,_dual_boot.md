---
title: "Clonezilla, dual boot"
date: 2013-03-19
forum: General Help
---

### Post by cscj01 on 2013-03-19
I have a cloned image of my system HD made with Clonezilla which contains 3 partitions:> [LIST=1]
[*]sda1 - Win XP;
[*]sda2 - Ubuntu 12.04 x64;
[*]sda3 - swap
[*]
[/LIST]
I am building a new PC and want to use my existing configuration with UEFI.  My current system uses Legacy boot.  Here is what I propose to do on my new PC:> [LIST=1]
[*]Restore my sda2 and sda3 partitions to my new system HD using Clonezilla;
[*]Set my BIOS to Legacy;
[*]Reboot and resize my partitions;
[*]Create my /boot/efi directory;
[*]Convert my new system HD to EFI boot by running Boot-Repair;
[*]Set my BIOS to Enable UEFI;
[*]Reboot.
[/LIST]I will be running XP in a Virtualbox VM which is already set up in my existing Ubuntu system.  I am new to UEFI, so if anyone sees a problem with my procedure, I will appreciate you pointing it out to me.  Also, please let me know if this will work.  Thanks.

---

### Post by cscj01 on 2013-03-21
bump

---

### Post by tancrackers on 2013-03-21
I don't see why not? I assume the Ubuntu partition will be / right? That's fine, just mark it bootable.
Place the bootloader in /dev/sda. Did Windows XP really create just 1 partition?

---

### Post by mörgæs on 2013-03-21
Changed the title to a more informative one.

---

### Post by cscj01 on 2013-03-21
> **tancrackers said:**
> I don't see why not? I assume the Ubuntu partition will be / right? That's fine, just mark it bootable.
Place the bootloader in /dev/sda. Did Windows XP really create just 1 partition?

Yes, Ubuntu will be /, and XP only created one partition.  Another question I thought of is this: if I restore sda2 (Ubuntu) and sda3 (swap), can I reassign them as sda1 and sda2 with Gparted (or something else) since I won't be restoring sda1 (XP)?  Thanks.

---

### Post by Slim Odds on 2013-03-21
> **cscj01 said:**
> Yes, Ubuntu will be /, and XP only created one partition.  Another question I thought of is this: if I restore sda2 (Ubuntu) and sda3 (swap), can I reassign them as sda1 and sda2 with Gparted (or something else) since I won't be restoring sda1 (XP)?  Thanks.
It depends on how you use Clonezilla. If you did a full disk image, then it's going to want to restore the entire drive. That includes the partition table and MBR.

If you save individual partitions, then it's a little more flexible. There is also an option to resize the partition on restore. It can be a little tricky, depending on the partition type and the OS in it.

---

