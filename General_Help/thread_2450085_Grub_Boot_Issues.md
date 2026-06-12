---
title: "Grub Boot Issues"
date: 2020-09-07
forum: General Help
---

### Post by No_Gate$ on 2020-09-07
Have issues with boot between Ubuntu 20, Zorin & Windows.
 
Background: recently upgraded PC (new MB, processor,  RAM and hard drive) to allow move from Zorin back to Ubuntu while still retaining Win10 for some specific programs and a bit of online gaming. Ubuntu 20 installed in new hard drive on its own. All appeared to go well including the re-activation of the Windows licence.

However, for the last couple of weeks, keep getting error which is generally boot to Grub Rescue prompt. 
Run boot repair a couple of times which fixes things enough to let me load Ubuntu, but as soon as Grub-Update is run to pick up Windows. I get 1 boot to an OS, if I'm lucky, then it's back to Grub Rescue when I want to go load a different OS.

Latest Boot Repair file is at [http://paste.ubuntu.com/p/FmKPhgPBdP/](http://paste.ubuntu.com/p/FmKPhgPBdP/)

Attached files generated from BootInfo after running Grub-Update following Boot Repair today.

Any help greatly appreciated

Paul

---

### Post by oldfred on 2020-09-07
With multiple drives & multiple installs, do not run Boot-Repairs auto fix with BIOS based systems.
It install one grub to MBR of all drives. You typically want the Windows boot loader in the Windows drive or maybe another grub for your other install. 

Also system is now the new UEFI system and you booted Boot-Repair in UEFI boot mode. But all installs are the old BIOS boot MBR partitioning.

Only use Boot-Repair's advanced mode and choose an install and then that install's drive's MBR on where to install boot loader.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows requires MBR(msdos) partitioning with BIOS boot, but you can install Ubuntu in BIOS or UEFI boot mode to a gpt partitioned drive. If you have both a bios_grub for BIOS boot and for future use an ESP, you then can easily convert drive to UEFI booting without having to do major reconfiguration.

You also have grub installed to the PBR partition boot sector or BS boot sector of sdd3. You may be able to use test disk to restore backup PBR as it has to have its own info there.

You also have sdb5 full, and need to houseclean or resolve that issue.

---

### Post by No_Gate$ on 2020-09-12
Sorry for the late response, been busy. Thank you for your reply and the link to the UEFI thread which I have read several times and must confess didn't understand all of it. However as the Ubuntu was a new install anyway, reinstalled with an EFI partition with all the other drives disconnected and at least I now have a working computer that boots every time. :p
The sdb5 which is full is the Zorin install which will be deleted once I can get Windows booting. The space will then be used to increase the size of the Windows partition to the whole disk. I have reconnected sdb which has the Windows and Zorin partitions and run update-grub. The Zorin install is recognised and added to grub but not Windows. I assume that this is related to BIOS vs EFI but don't know or understand how or what to change to make it work
I haven't run boot repair again but attached is the output from the boot repair report with current configuration.

Thanks again

Paul

---

### Post by oldfred on 2020-09-12
It looks like you reinstalled in UEFI boot mode, but but to MBR partitioned drive.
UEFI strongly suggests gpt and Windows only installs in UEFI boot mode to gpt and only in BIOS boot mode to MBR.
Converting with gparted will erase drive. You can convert, but have to reinstall grub at minimum.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

I started using gpt with my BIOS only system in 2010.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by No_Gate$ on 2020-09-12
> **oldfred said:**
> It looks like you reinstalled in UEFI boot mode, but but to MBR partitioned drive.
UEFI strongly suggests gpt and Windows only installs in UEFI boot mode to gpt and only in BIOS boot mode to MBR.
Converting with gparted will erase drive. You can convert, but have to reinstall grub at minimum.
As sdb will be a Windows only drive, I assume that I can install a fresh copy of Windows with UEFI. Would it be worth disconnecting sda so that there is only 1 disk for the Windows installation? If I change BIOS setting to legacy & EFI, boot fails hence wanting to get everything to UEFI.
> Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
Read this and tried using mbr2gpt from the Windows boot USB under the repair option but the validate failed for some reason, hence the question on new installation. Have copies of all data from Windows on USB.
If I install clean Windows to sdb with sda unplugged, I assume that grub will need either reinstalling or after plugging sda back in, running update-grub be sufficient?

Again thanks for your help

Paul

---

### Post by oldfred on 2020-09-12
I have not installed Windows, but if it sees MBR, it will not install in UEFI mode.
You may need to just erase drive.

If you use gparted, and change to gpt that removes all partitions effectively erasing it.

You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

Older screenshot but still same.

---

### Post by No_Gate$ on 2020-09-16
> **oldfred said:**
> I have not installed Windows, but if it sees MBR, it will not install in UEFI mode.
You may need to just erase drive.
Did this but before I'd created the Windows installation USB in Windows. Even though the burn was OK according to BalenaEtcher and Unetbootin, there were some files missing so wouldn't install. Had to install old copy of Windows 32bit I had on CD in order to burn the new USB in Windows using the Microsoft tool. Took me 2 days on and off to discover I needed to do this. Once the USB was created with the Windows Media Creator selecting 64bit OS which automatically install in UEFI I assume if supported, installation was about 60 minutes.

Ran update-grub this morning and after changing the boot priority in the BIOS, dual boot now back working :)

Thanks again for your help

---

### Post by oldfred on 2020-09-16
Glad you got it working.

Most of the instructions on the Internet for making a Windows installer from Linux are now wrong. They have you extract ISO to FAT32 partition. Only a few newer instructions have ways to deal with newest Windows.

Microsoft made the .wim file larger than 4GB on latest Windows versions, so cannot be just extracted to FAT32. And UEFI requires FAT32 to boot. The Microsoft tool splits the .wim file to make it work. I just do not know why they do not just split it in the ISO.

---

### Post by CelticWarrior on 2020-09-16
You could've used [MKUSB ]("https://help.ubuntu.com/community/mkusb")or [WoeUSB]("https://www.omgubuntu.co.uk/2017/06/create-bootable-windows-10-usb-ubuntu").

And no, Windows 10 64-bit supports both modes. If installed in a MBR drive it surely is Legacy.

---

