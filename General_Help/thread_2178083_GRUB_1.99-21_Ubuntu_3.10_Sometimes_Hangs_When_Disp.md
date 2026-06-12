---
title: "GRUB 1.99-21 Ubuntu 3.10 Sometimes Hangs When Displaying Boot Menu"
date: 2013-10-01
forum: General Help
---

### Post by 8link on 2013-10-01
Hello all,

I have a dual boot ubuntu 12.04/windows 8 laptop that runs grub2.  More often than not after the laptop finishes POST and when grub attempts to load and display the boot menu the laptop will hang.  Sometimes this happens with only partial text of the menu displayed, sometimes the entire menu is displayed but accepts no input.  The only resolution is to hard power off the laptop and try again.  Sometimes it takes many tries to get it to boot.  With enough patience I can always get it to boot.  All the boot options will boot completely if I get grub not to hang.

I've tried to reinstall grub multiple times, I've tried various grub options like nomodeset, I've tried boot-repair, etc, but nothing has worked.
My boot repair summary suggests moving the /boot/efi partition closer to the beginning of the drive.  I'm hesitant as the windows recovery partition is currently the first 1GB of the drive.  If it will not make a difference I will do but would rather go on real information rather than a guess.

Here is my boot-repair summary: [http://paste.ubuntu.com/6181603/](http://paste.ubuntu.com/6181603/)


Any and all help is appreciated.

Thanks,

8

---

### Post by oldfred on 2013-10-01
I have not seen any new UEFI systems need boot files moved. Maybe because of UEFI?

You have both a BIOS grub installed in protective MBR and grub efi in efi partition. It looks like you currently have it configured for UEFI boot as fstab shows mounting of /boot/efi partition. There are two versions of grub. 
grub-pc is for BIOS boot
grub-efi is for UEFI boot.
Then there are also signed versions of grub & kernels for UEFI secure boot.

So are you booting in UEFI mode not in BIOS/CSM/Legacy mode?
Line 567 shows 0019 as first boot device and that is ubuntu with efi.

---

### Post by 8link on 2013-10-02
Thanks much for the analysis!

Originally, Windows 8 was booting UEFI in secure mode.  I disabled secure mode in order to install 12.04.

I am booting in UEFI mode as Windows 8 would not boot any other way.
I took another look at BIOS settings and found that it was configured to allow only UEFI but CSM was enabled for some reason.  Disabling CSM seems to have changed boot menu behavior for the better.  Both windows 8 and 12.04 are still booting correctly.  I will give it a few more boots and if I do not experience the hang will close this thread.

I believe grub-pc was installed during one of my attempts to correct the problem.  I should remove grub-pc.

Thanks again,

8

---

### Post by oldfred on 2013-10-02
If Boot-Repair converted you to UEFI from BIOS then grub-pc is uninstalled. And you cannot easily erase MBR, but it is not used with UEFI so does not really matter.

Perhaps with CSM/BIOS/Legacy mode on it was checking to see which way to boot. Some progress thru the alternatives but I thought they looked for efi partition first, but thay may vary by vendor and/or settings.

---

### Post by 8link on 2013-10-02
Yup, grub-pc is not installed.
That must be what was happening, getting confused on which way to boot.

Seems to boot reliably now.
Thanks!

---

