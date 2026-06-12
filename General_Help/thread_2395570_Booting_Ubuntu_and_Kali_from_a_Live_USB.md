---
title: "Booting Ubuntu and Kali from a Live USB"
date: 2018-07-03
forum: General Help
---

### Post by robbykeh on 2018-07-03
Hi everyone, 

I installed Kali Linux and Ubuntu on a portable SSD, but after a week of trying, I was not able to successfully boot from from this portable drive. I was however, able to boot from the computers in which I installed the distributions on (grub was installed on my computer's reserved EFI Windows partitions), but NOT from the portable SSD solely. The only solution to boot the two linux distributions from the external SSD on multiple computers from my portable drive was to boot from a Live USB (either an Ubuntu installation disk or a Kali Linux, I tested with both) and select Live installation. So my question is, if I boot into the Live installation of Ubuntu/Kali Linux, do I have to change any settings to install packages, apps, software, etc. to my external SSD instead of unintentionally installing all these items to the bootable USB space? Or do I just boot from the Live system and continue to use Ubuntu as normal? Also, once I boot into the Live system with my external SSD plugged in, can I unplug the bootable USB without any consequence? Thanks.

---

### Post by yancek on 2018-07-04
Did you install Kali and Ubuntu on the SSD, doing a full installation either from a DVD or another usb drive?  OR, did you use some software to create a bootable Kali and Ubuntu?

If you actually did a full install of both Kali and Ubuntu on a computer which already had a windows OS with an already existing EFI partition, in all likelihood both the Kali and Ubuntu EFI files are on that machine.  If you want an EFI boot on a portable SSD/usb drive, you need to create an EFI partition on that SSD/usb drive and put your Kali and Ubuntu EFI files on the EFI partition of that SSD/usb drive.  If you then want to boot from another computer, you will need to enter the BIOS and select that drive.

The other option is to do Legacy (non-EFI) installs of both Ubuntu and Kali to the SSD, make sure you install the Grub boot code to the MBR of the SSD.  THis way, you should be able to boot either system by selecting that physical SSD drive from the BIOS of other computers and setting it to first boot priority.  If you have/want GPT and EFI, don't use this method.

 A Live installation of either Kali or Ubuntu will not save anything on reboot unless you have persistence, that's the design.  I'm not sure I understand the last part of your post about booting the Live system and installing software on the systems on the SSD.  You can copy data from a Live system to your SSD but you need to take some steps to do that each boot.  You might be able to chroot into the installed system from the Live system but that would need to be done manually on each boot.

---

### Post by oldfred on 2018-07-04
Grub typically installs its boot files into the first drive, usually sda and an internal drive.
You have to use Something Else to install grub boot loader to any other drive. But that only works with BIOS installs.

If you want or have UEFI system, you need to partition external drive in advance with an ESP - efi system partition as FAT32 with boot flag. UEFI only boots external drives from /EFI/Boot/bootx64.efi. So we end up copying /EFI/ubuntu twice to ESP on external device, once to /EFI/ubuntu as grub or shim need certain files from that path, and again to /EFI/Boot and rename shimx64.efi to bootx64.efi as UEFI only uses that to boot.

[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by robbykeh on 2018-07-05
Yeah, I installed Kali Linux via a Bootable USB on a live system on my Desktop computer and then Ubuntu on my laptop via a Bootable USB. I do have an EFI reserved partition on the SSD, but there is nothing on it, and I believe its the very first partition, /sda. Would I just copy the EFI boot files from /boot from both root directories of Ubuntu and Kali Linux into the EFI reserved partition of the SSD and then install GRUB to that partition? Thanks for the response.

---

### Post by robbykeh on 2018-07-05
Okay, so I have to copy the folders and subfolders, /EFI/boot/ and /EFI/ubuntu/ to the SSD EFI partition, and rename the bootx64.efi to shimx64.efi? Thanks for the response.

---

### Post by oldfred on 2018-07-05
Not its change shimx64.efi into /EFI/Boot/bootx64.efi

UEFI only boots external drives and fallback or hard drive entries from /EFI/Boot/bootx64.efi.
But we make bootx64.efi a copy of shimx64.efi so it boots Ubuntu, but shimx64.efi has hard coded internals that must be able to look into /EFI/ubuntu.

---

### Post by robbykeh on 2018-07-06
Okay, I should follow this subsection in your "UEFI Installing-Tips" guide **Systems that only boot Windows from UEFI** in order to copy the boot files from Ubuntu into the EFI partition?

---

### Post by oldfred on 2018-07-06
That section is for those brands (many it seems) that only boot by description and only valid description is "Windows Boot Manager".
But even those systems boot external drives from /EFI/Boot/bootx64.efi. But most UEFI must have a setting to allow USB or external drive boot. Often UEFI's Secure boot setting also must be off, as allowing USB boot is not "secure".

There is a section on two drive boots, mostly links to more details.

While Ubuntu installer does not let you change drive from its default, I believe Boot-Repair will work with UEFI install to another drive. But I have not tried it. ESP partition must exist on that drive as Boot-Repair does not create partitions.

---

### Post by robbykeh on 2018-07-06
Okay, I will try some of the things you said and see if I can figure it out thanks.

---

