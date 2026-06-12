---
title: "Windows 8 dual boot problem?"
date: 2013-06-25
forum: General Help
---

### Post by community on 2013-06-25
I installed Ubuntu 12.04 immediately after installing Windows 8 on my Dell laptop. The installation was successful. I installed Ubuntu to entirely different partition with swap area. And made the remaining harddisk free space. But on restarting it directly got into Win 8 without showing the grub. What should I do? Whether to reinstall grub from live usb or something else? I need to know whether Win 8 Secure Boot and UEFI cause problems for installing of Ubuntu?

---

### Post by oldfred on 2013-06-25
Best to see details. Did you install both in UEFI mode or both in BIOS mode?

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

### Post by community on 2013-06-25
Ok. I will try BootRepair to recover Ubuntu. Will post the results after using the same.

---

