---
title: "Installing Ubuntu in Windows 8"
date: 2013-01-27
forum: General Help
---

### Post by northwestern on 2013-01-27
HI
I have just had limited success installing Ubuntu 12.10 onto an external disk on my new Samsung (series 3) Windows 8 laptop.
The secure boot has been disabled.
The situation now is that Windows or Ubuntu will not boot up after pressing the START button, when doing this I get a dark screen with the following message:
**error: no such device: 6dada016-95df-4ef5-a343-4a77e8afd396**
**grub rescue >_**
I can now only boot up in either program by hitting the F10 key directly after pressing the power button, I then have to select one of the options before the machine will boot (both systems boot up as normal when following this option).
 Ideally, if the external drive is not plugged into the USB port I want my laptop to boot directly into Windows 8. Can this be achieved?
Regards
Northwestern

---

### Post by oldfred on 2013-01-27
If a new system with Windows 8 pre-installed you have secure boot. Have you turned secure boot off?
Also with some systems critical to turn off fast boot in UEFI menu. 

Best to see details, run this with external drive plugged in either from install or liveCD/DVD/flash drive used to install.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
    
Should not matter if internal or externel drive. Did you install Ubuntu in UEFI mode or Legacy/BIOS/CSM mode? BootInfo report will tell us if not sure.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

