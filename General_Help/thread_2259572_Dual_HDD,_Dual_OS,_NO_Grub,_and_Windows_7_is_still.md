---
title: "Dual HDD, Dual OS, NO Grub, and Windows 7 is still getting messed up."
date: 2015-01-05
forum: General Help
---

### Post by 777funk on 2015-01-05
What could be wrong? I set it up to boot up from the bios (now UFEI). I have the data on a different partition than Windows 7 (came this way from the factory with my new ASUS machine). I installed Xubuntu on it's own separate HDD and select between the two OS's at startup (from the bios). I have it set to use the Xubuntu drive as the first boot device. I have to manually boot from the Win 7 drive if I ever need it. 

But I noticed that things are getting damaged on Win 7 and that it always checks for errors on startup. 

Why is this?

---

### Post by oldfred on 2015-01-05
Do you have Windows hibernated? That will cause issues.

Otherwise lets just see if configuration looks ok for booting. 
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by 777funk on 2015-01-05
No Hibernating with the Win 7. I'm noticing some Win programs aren't working any more. 

There is no Grub but I figured since the two hard drives are separate, I wouldn't need one.

---

### Post by oldfred on 2015-01-05
Grub is both a boot manager or software to select which system to boot, and is the boot loader for Linux. There are ways with UEFI to not use grub2, but put kernel into efi partition, but that is not the standard method. 
You need grub to be installed.

---

### Post by 777funk on 2015-01-05
> **oldfred said:**
> ....
You need grub to be installed.


Thanks! So even with two separate hard drives? I don't quite understand how the Ubuntu drive could bother Win 7 when they're on separate hard drives. I'm curious on this.

---

### Post by yancek on 2015-01-05
If you are booting Xubuntu, you must have Grub2 installed.

> I don't quite understand how the Ubuntu drive could bother Win 7 when they're on separate hard drives.

I don't know what problems you are having but a Linux/Ubuntu systems shouldn't access or do anything to a windows partition in running normally.  A user can easily do that however.  Might be best to post the output of the Bootinfo Summary from the link posted by oldfred above.

---

### Post by 777funk on 2015-01-05
Here is that (just downloaded the boot info program):

[http://paste.ubuntu.com/9679004/](http://paste.ubuntu.com/9679004/)

---

### Post by oldfred on 2015-01-05
You have a BIOS boot of Windows on sda which is MBR partitioned, and either a UEFI boot or a BIOS boot of Ubuntu on sdb which is gpt partitioned. You have the efi partition, and grub installed to MBR. But I thought grub would not install in BIOS boot mode to MBR without a 1 or 2MB unformatted partition with the bios_grub flag. You do not show a bios_grub partition which is where core.img is stored. But it says you have core.img at sector 166530 which looks like it is then in the efi partition.

UEFI and BIOS are not compatible. Once you start booting in one mode you cannot change to the other mode. Or you cannot use grub menu to dual boot. If you want Ubuntu in UEFI mode and Windows in BIOS boot mode, you can only dual boot from UEFI menu or one time boot key.

If you want Ubuntu in BIOS boot mode, use gparted and create the bios_grub partition anywhere on drive. Then use Boot-Repair to reinstall grub to the MBR of sdb. Do not use any auto fix as that will install grub to every MBR. You want to keep the Windows boot loader in the MBR of sda.

BIOS mode does not work with secure boot. Boot-Repair says you have secure boot on, so make sure that is off. That may be related to the issues. If you start UEFI and then switch to BIOS mode it has to totally reboot and your UEFI may let you try to boot Windows with UEFI on but then realizes that is not correct & reboots but needs repairs?

There are ways to install Windows 7 in UEFI mode from a flash drive. And Windows 7 does not have secure boot, so it avoids all those issues.

---

### Post by yancek on 2015-01-05
You have windows code installed to the master boot record of the first drive where your windows system resides.
You have the Ubuntu Grub bootloader installed to the master boot record of sdb where Ubuntu resides.
On sdb, you also have an efi partition with the Ubuntu efi files which would not be expected to be there if you have Grub in the mbr.
There are no windows efi files on either drive.

I don't use UEFI so you'll need to wait for someone else to respond as to whether the suggestions at the end of the BootInfo summary would help.

---

### Post by 777funk on 2015-01-06
> **oldfred said:**
> You have a BIOS boot of Windows on sda which is MBR partitioned, and either a UEFI boot or a BIOS boot of Ubuntu on sdb which is gpt partitioned. You have the efi partition, and grub installed to MBR. But I thought grub would not install in BIOS boot mode to MBR without a 1 or 2MB unformatted partition with the bios_grub flag. You do not show a bios_grub partition which is where core.img is stored. But it says you have core.img at sector 166530 which looks like it is then in the efi partition.

UEFI and BIOS are not compatible. Once you start booting in one mode you cannot change to the other mode. Or you cannot use grub menu to dual boot. If you want Ubuntu in UEFI mode and Windows in BIOS boot mode, you can only dual boot from UEFI menu or one time boot key.

If you want Ubuntu in BIOS boot mode, use gparted and create the bios_grub partition anywhere on drive. Then use Boot-Repair to reinstall grub to the MBR of sdb. Do not use any auto fix as that will install grub to every MBR. You want to keep the Windows boot loader in the MBR of sda.

BIOS mode does not work with secure boot. Boot-Repair says you have secure boot on, so make sure that is off. That may be related to the issues. If you start UEFI and then switch to BIOS mode it has to totally reboot and your UEFI may let you try to boot Windows with UEFI on but then realizes that is not correct & reboots but needs repairs?

There are ways to install Windows 7 in UEFI mode from a flash drive. And Windows 7 does not have secure boot, so it avoids all those issues.

I'm currently auto booting into Ubuntu. I have to go to the bios to boot into Windows (manually select the sda drive). What I don't quite understand is how the Windows is getting broken.

---

### Post by oldfred on 2015-01-06
It may just be the switching back & forth from UEFI to BIOS and to UEFI again. 
It may not be broken per se, just that you are in UEFI mode and switch to boot sda which is in BIOS mode.

Generally better to have both UEFI or both BIOS boot. And at this point since Windows is BIOS, and you can use Boot-Repair to convert Ubuntu to BIOS boot with an uninstall of grub-pc (BIOS) and install of grub-efi-amd64(UEFI) then easier to convert Ubuntu to BIOS.

There are some advantages to UEFI.
       UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

