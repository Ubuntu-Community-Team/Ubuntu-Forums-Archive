---
title: "Duel install windows 8 and ubuntu..windows is fine ubuntu doesnt boot. help!"
date: 2013-10-30
forum: General Help
---

### Post by daleec on 2013-10-30
Mostly what i said in the title, I just installed ubuntu 13.10 along side my windows installation and windows boots up just fine.  However when I try to boot ubuntu the screen goes blank, looses signal and a few seconds the pc just shuts off.  does it everytime.  Anyone help?

---

### Post by oldfred on 2013-10-30
Pre-Installed Windows 8 with UEFI and gpt partitions or your own install with BIOS & MBR partitions?

What computer and what video card. Often black screen is a video issue and nomodeset works, but some need other settings. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by david98 on 2013-10-30
[I] I Recommend always disabling UEFI before installing linux it was mainely designed for window's machines and has been known to cause problem's with certain manufactures samsung being the main one which on some model's completely bricked your system always read up on your system before installing any os windows included 
 [/I]

---

