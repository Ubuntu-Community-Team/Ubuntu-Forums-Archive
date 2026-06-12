---
title: "Grub broken"
date: 2015-07-09
forum: General Help
---

### Post by joe_schmo2 on 2015-07-09
I have an Acer laptop which I have dual bool Ubuntu 15.04 and Windows 7.  It took me forever to get Ubuntu installed apparently because of a faulty hard drive.  While trying to repair my hard drive using HDD Regenerator I broke Windows 7.  Well I finally got Windows working again but in the process broke my Grub install, ie I boot directly to Windows 7 now.  I'm 99% sure it was when I ran, from a DOS window, the command BootRec.exe , I ran it using all options, /FixMBR, /FixBoot, /ScanOS.

Is there a way to get my Grub menu back?

Thanks.

---

### Post by oldfred on 2015-07-09
If Ubuntu is ok, and all you did was install the Windows boot loader to the MBR, you should just need to restore grub to MBR.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Above assumes BIOS, If UEFI it should still be a boot option in UEFI boot tab menu.

---

