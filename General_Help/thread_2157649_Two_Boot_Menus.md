---
title: "Two Boot Menus"
date: 2013-06-26
forum: General Help
---

### Post by thesolis on 2013-06-26
My system is working fine dual-booting Windows 8 and Ubuntu 13.04 so this is just an annoyance issue more than anything:

From the Ubuntu OS selection screen (which appears when I start my computer) I can choose to boot into Ubuntu which works fine but if I try booting to Windows I get a file not found error. Luckily I have the option from the Ubuntu OS selection screen to go into the Windows OS selection screen. From there I can boot into Windows without a problem but I get a file not found error when I try to boot into Ubuntu.

Any way to consolidate these OS selectioin screens? I'd prefer to use the Windows 8 one with the GUI instead of the Ubuntu screen but it doesn't matter too much.

---

### Post by oldfred on 2013-06-26
Welcome to the forums.
Not sure what you are seeing. May be best just to post all the details. If you boot into your Ubuntu you can download this into your install or download into the Ubuntu live installer or as a repairCD or DVD.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by thesolis on 2013-06-26
Here are the results to the Boot-Info:
[http://paste.ubuntu.com/5802606/](http://paste.ubuntu.com/5802606/)

Hope this clears things up! Let me know if there's anything else I should provide.

---

### Post by oldfred on 2013-06-26
Are you starting at a UEFI menu not directly booting the ubuntu entry in UEFI as default?

Also does your computer boot Windows with secure boot off? 

Boot-Repair has renamed the Windows file as many UEFI secure boot systems only boot with Secure boot on and then (not per UEFI standard) will only boot the Windows efi file. The work around is to rename grub2's shim file which has the Microsoft key to the Windows name. Then you are actually booting grub which system thinks it is booting Windows and grub then lets you boot Windows by chainloading to the renamed Windows file.

This is what has been done.
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

But if you can boot without secure boot on, you can undo the rename.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by thesolis on 2013-06-26
Thank you for the help!

---

