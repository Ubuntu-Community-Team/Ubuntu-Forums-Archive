---
title: "Grub rescue"
date: 2013-10-31
forum: General Help
---

### Post by tom36 on 2013-10-31
Hi, yesterday I deleted my Ubuntu 13.04 partition because I made some huge mistakes. When I wanted to boot Windows 8, a error message popped up saying: 
"error: no such device (some different letters)
grub rescue"
There was some kind of comand-prompt.
I googled after this error and found different methods to solve this.
I tried to repait it with Boot-Repair -> didn't worked.
I tried to reinstall Ubuntu -> didn't worked.
I booted a Win8 Iso and typed /FixMbr(worked), /FixBoot(worked) and /RebuildBcd. But it answerd me the systemdevice wasn't fount. -> didn't worked.
And I tried also this tutorial -> [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) -> It gave me different errors.
Anyone knows how I can boot into Windows?
Please help me, 
thanks, Tom.
(Sorry for my bad English)

---

### Post by oldfred on 2013-10-31
Is this a pre-Installed Windows with UEFI and gpt partitioning or your install with the BIOS and MBR partitioning?
Is secure boot on or off? Did you turn fast boot off?

If UEFI install you should be able to boot Windows from UEFI menu. But some UEFI have been modified by vendor to only boot the Windows efi file. Boot-Repair in those cases renames the Windows file to be grub2's shim that has the Microsoft signing key. Then when choosing Windows from UEFI you get grub menu and from grub menu you should be able to boot Windows. But if Windows was still hibernated (Fast Boot) it will not work.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by tom36 on 2013-10-31
Thanks for answer,
Theoretically the Windows 8 is preinstalled with UEFI (sorry but I don't know what gpt is). But when I tried today to revert changes with an older system image of win8, it told me that that it's not possible, because the old image was efi and actually it's bios. Secure and fastboot is turned off.
How should I go now? Sorry, I'm new in Linux.
Edit:I istalled Ubuntu on a second partition with Unetbootin, not with Wubi.

---

### Post by oldfred on 2013-10-31
From Live installer run Boot-Repair. You should normally install with unetbootin to a flash drive as it totally erases a drive. Never tried a partition, did it say it would totally overwrite drive?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by tom36 on 2013-10-31
Ok, give me 5 min to flash it on a stick and start the boot repair.

Edit: Somehow it tells me that BOOTMGR is missing!
This never happened before!
I cant start boot repair!

---

### Post by tom36 on 2013-11-01
So what could I do?

---

### Post by fantab on 2013-11-01
Boot with your Ubuntu USB and 'Try Ubuntu without installing'. If you get to the desktop connect to internet and get back here.

---

### Post by tom36 on 2013-11-01
Thanks, but I already said that it's not working. When I choose to boot from my USB-flash drive it tells me: BOOTMGR missing.

---

### Post by fantab on 2013-11-01
Try Burning the ubuntu.iso again to the USB. Before that do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on the downloaded .iso to confirm that nothing is missing or corrupt in your download.

Check in your UEFI/BIOS and confirm if you are booting in UEFI or Legacy/BIOS/CSM.

---

### Post by tom36 on 2013-11-01
I burned it already again and checked the MD5Sum. It's correct. The .zip also worked before, but after I tried to edit the bootloader with a Windows iso, it wasn't working anymore.
In the BIOS is written launch CSM -> enabled.

---

### Post by fantab on 2013-11-01
Then probably your windows is not installed in uefi. 
I have found [http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html](http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html), perhaps it may help you. Let us know.

Also see this: [http://superuser.com/questions/524205/how-to-fix-windows-8-boot-manager](http://superuser.com/questions/524205/how-to-fix-windows-8-boot-manager)

---

### Post by tom36 on 2013-11-01
Thanks, I'm trying now your first links. It describes more or less my problem.

---

### Post by tom36 on 2013-11-01
Well, the first link didn't helped.

---

### Post by tom36 on 2013-11-01
I found the solution!
Thanks to all who helped!
Here is the link to the solution: [http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader](http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader)

---

### Post by fantab on 2013-11-01
So you were afterall using Efi then? 
Glad you found the solution.

---

### Post by tom36 on 2013-11-01
It's seems so, even if Windows told me I would use BIOS... You know-Windows -.-

---

