---
title: "Boot partition not found"
date: 2008-07-01
forum: General Help
---

### Post by todak on 2008-07-01
On my first hard drive I have installed Hardy as an encrypted logical volume. I copied all pertinent and important files from my second hard drive to my home folder on the encrypted drive while I was booted into the encrypted drive. Then I installed openSUSE 11.0 onto the second hard drive. I let openSUSE install its grub to the MBR of my first drive. Being as the /boot partition on my first drive is not encrypted, openSUSE should have found Ubuntu's boot parameters and installed them in its grub menu. However, that is not the case. Only openSUSE is visible in grub. I rebooted with the Hardy live CD and issued the sudo grub command in a terminal to see if I could find stage1 in grub. only (hd1,1) was found. (hd0,0), my unencrypted /boot for Ubuntu was not found. I checked with gparted and it shows /dev/sda1 as an unknown partition! It was an ext3 partition when I installed it. Apparently, when I let openSUSE overwrite the MBR of /dev/sda1, it caused something to go wrong. Here is menu.lst from openSUSE grub: ```
# Modified by YaST2. Last modification on Tue Jul  1 05:49:08 EDT 2008
default 0
timeout 8
gfxmenu (hd1,1)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_WDC_WD400BB-75DWD-WMAD16043178-part2 resume=/dev/sdb1 splash=silent showopts vga=0x314
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (hd1,1)
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0
    root (hd1,1)
    kernel /boot/vmlinuz root=/dev/disk/by-id/scsi-SATA_WDC_WD400BB-75DWD-WMAD16043178-part2 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off  x11failsafe vga=0x314
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: Kernel-2.6.25.5-1.1-default###
title Kernel-2.6.25.5-1.1-default
    root (hd1,1)
    kernel /boot/vmlinuz-2.6.25.5-1.1-default root=/dev/disk/by-id/scsi-SATA_WDC_WD400BB-75DWD-WMAD16043178-part2 resume=/dev/sdb1 splash=silent showopts vga=0x314
    initrd /boot/initrd-2.6.25.5-1.1-default
```
Now I cannot get into the /boot partition of either ```
(hd0,0) or /dev/sda1
``` Is there any tool to repair or recover that partition without overwriting the information on it? If not, then I will not be able to access my encrypted partition. Should have I installed openSUSE first and then Ubuntu? I think that should not matter as I have done the same thing on another computer and I can open the /boot partition from any live CD and I can do the same thing from the installed openSUSE when I boot it up. Any clues?

---

### Post by adam_kimber on 2008-07-01
Thought I would reply with a few suggestions. However as I have never encrypted a drive / partition before, let alone the entire operating system I am not quite sure what you can do..... 

I expect when grub updated its list of boot options it did not recongise your encrypted partition. This page might help.... [Encrypted File System how to]("https://help.ubuntu.com/community/EncryptedFilesystemHowto4")

I would however ask, can you mount the partition /dev/sda1 when you boot into another OS? That would make sure that it actaully works. You might not have a / the driver for the encryption running on the other OS SUSE or Ubuntu live CD. hence gparted does not recongnise it. modprobe dm-crypt might not the trick. 

Keep me posted. :D

---

### Post by todak on 2008-07-01
I cannot mount the partition at all. Grub should have recognized the partition. When encrypting a drive, a small bit is left unencrypted so that when you boot, it will know where to look for the encrypted partition and it will ask for the passphrase to unlock the drive. However, I cannot open the unencrypted /boot folder so that I can add it to grub. Apparently it got corrupted. Even a partition editor shows it as an unknown partition type.

---

### Post by adam_kimber on 2008-07-01
> **todak said:**
> Even a partition editor shows it as an unknown partition type.

So the modprobe driver load does not help?

---

### Post by todak on 2008-07-01
No, modprobe does not work. Using testdisk I can see the files in the /boot partition, so it cannot be corrupt. The volume shows as LVM2 in testdisk and the file system in it as ext3. However, I cannot  understand how it changed from an ext3 to an LVM2. Is there a process that will let me change it to an ext3 (without destroying the date) so that it is bootable? It is only a 254 Mb unencrypted partition. I cannot copy the files using testdisk and I cannot see the files or mount the partition using any other tools that I have.

---

### Post by todak on 2008-07-01
Bump

---

### Post by adam_kimber on 2008-07-01
Have a look at [LiveCD recovery ]("https://help.ubuntu.com/community/LiveCdRecovery") as it tells you how to mount an LVM2 partition and then access the files. That way you might be able to copy the date or even unencrypt it.

---

