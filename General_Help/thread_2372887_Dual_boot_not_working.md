---
title: "Dual boot not working"
date: 2017-09-29
forum: General Help
---

### Post by makez on 2017-09-29
I have a SSD with Windows 10, and a HDD with two partitions: one of them is to store Windows applications and games, and the other one has Ubuntu.

This is the HDD:

[IMG]https://i.imgur.com/g5gZZH6.png[/IMG]

The problem: If I tell BIOS boot priority has the SDD Windows 10 gets loaded, on the other hand, if HDD has boot priority Ubuntu gets loaded without loading any GRUB.

What should I do? I want the GRUB to be loaded each time I turn on the PC.

---

### Post by yancek on 2017-09-29
It would seem that your windows install is UEFI (default for pre-installed windows 10) and Ubuntu is an MBR install.  When you boot windows and go to computer management, do you see an EFI partition.  Your Ubuntu drive is MBR.  You might try installing Ubuntu again EFI if your windows is.  All explained at the Ubuntu site below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-09-30
Grub is being loaded, but grub can only boot other systems installed in same boot mode.
So if Ubuntu is BIOS/MBR which it looks like, and Windows is UEFI grub only sees Ubuntu and does not show menu by default. Pre-installed Windows 10 is UEFI. Only if you upgraded Windows 7 that was BIOS/MBR would then Windows 10 be BIOS boot.

If you hold shift key from UEFI/BIOS does menu appear?
Or with UEFI you press escape key, perhaps several times. 
Since UEFI hardware with BIOS install not sure which key you use.

---

### Post by makez on 2017-09-30
I made it!

I want to install BURG now, should I select the SSD or the HDD in the installation? Ubuntu is in the HDD but /boot/efi is in the SSD so I don't know which one to choose

---

### Post by oldfred on 2017-09-30
Burg has not been maintained for years. Not recommended. Also will not work with UEFI booting.

If you have UEFI you can use rEFInd.
       Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

