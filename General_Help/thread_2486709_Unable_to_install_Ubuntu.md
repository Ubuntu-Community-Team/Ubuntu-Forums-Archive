---
title: "Unable to install Ubuntu"
date: 2023-05-08
forum: General Help
---

### Post by robertwalls78 on 2023-05-08
Good evening I tried to install Ubuntu 23.04 on my Dell Latitude 3580 laptop, the installation went through but when the laptop restarted my bios went into a memory test mode. Windows 11 works perfectly on it and all memory test are fine. Some reason Ubuntu will not start. Can anyone help me in figuring out what it could be. CPU is an I5 7200U. Thanks in advance.

---

### Post by aljames2 on 2023-05-08
Have you gone in to your bios and set Ubuntu as your first boot priority?  Doing so allows the system to boot to Grub, thereby allowing you to select the OS you want to load.

---

### Post by yancek on 2023-05-09
In addition to the suggestion above, did you select to install Ubuntu in UEFI mode?  Windows 11 almost certainly is so if you want to boot both systems from Grub, the Ubuntu Grub must be UEFI.  You can check this by either looking in the motherboard BIOS boot options to see if there is an entry for 'ubuntu' or by using the USB installer and mounting the EFI partition to check for an ubuntu directory.

---

### Post by robertwalls78 on 2023-05-09
I've done a clean install of Ubuntu and Windows 11 has been removed from the SSD. In my bios I've noticed a part that has RAID-ON and ACHI. Raid-on is ticked on. Could this be the problem.

---

### Post by aljames2 on 2023-05-09
What are you trying to achieve, you goal?  By your OP, it sounded like you were wanting a dual boot system.  Now you have removed W11, is your goal to have an Ubuntu only system?  If so, your SSD likely still has the windows boot loader on it which can continue to interfere with Ubuntu booting unless dealt with.

---

### Post by tea for one on 2023-05-09
> **robertwalls78 said:**
> I've done a clean install of Ubuntu and Windows 11 has been removed from the SSD. In my bios I've noticed a part that has RAID-ON and ACHI. Raid-on is ticked on. Could this be the problem.
Change sata mode to AHCI.
Reboot
Any Luck?

---

### Post by robertwalls78 on 2023-05-09
I wanted a Linux machine sorry for the confusion.

---

### Post by robertwalls78 on 2023-05-09
I will change to bios to ACHI. Thanks for that. Will let you know if that worked.

---

### Post by oldfred on 2023-05-09
With my gen 11 Intel based Dell, 22.04 installed with RAID on. I frankly forgot to change it as we always have said we had to change to AHCI.
It turns out kernel has a VMD driver. Not sure if only for NVMe drives or not which my Dell has.
And I do not think the VMD driver was implemented in Ubuntu's older distributions.

---

### Post by #&amp;thj^% on 2023-05-09
I can't remember either oldfred, but:
```
inxi -p | grep nvme
    dev: /dev/nvme0n1p1

```
EDIT: Here it is: "found in Linux kernels: 4.18&#8211;4.20, 5.0&#8211;5.19, 6.0&#8211;6.3, 6.4-rc+HEAD modules built: vmd, vmd, vmd"
Source: [https://cateee.net/lkddb/web-lkddb/VMD.html](https://cateee.net/lkddb/web-lkddb/VMD.html)

---

