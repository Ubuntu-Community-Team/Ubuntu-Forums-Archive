---
title: "Installed ubuntu on it's own HDD and it overwrote my WIN7 boot sector. Restorable?"
date: 2019-01-10
forum: General Help
---

### Post by 777funk on 2019-01-10
I don't know how this happened but now even if the Win 7 drive is the only one plugged in, the BIOS doesn't pick it up as bootable. GParted still shows that it's there, Is there a way to get Windows to boot once again?

---

### Post by yancek on 2019-01-10
If you didn't install Grub, what bootloader are you using?  You need to have some type of bootloader because the BIOS won't boot your system but merely point to where the boot files should be on a specific sector of the drive and the bootloader takes over from there.

Did you install whichever bootloader you are using with Ubuntu to the MBR of its drive (sdb) or leave the defaults or something else?
What did you change because the default with an Ubuntu install is to install Grub code to the MBR of the first drive and the rest of the Grub files on the Ubuntu partition.  That is what would have happened unless you changed it.

If you can boot Ubuntu, do you see a menuentry for windows in the grub.cfg file?

---

### Post by oldfred on 2019-01-10
We need to see all the details:

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 777funk on 2019-01-15
> **oldfred said:**
> We need to see all the details:

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for the tip. Here's what I end up with:
[http://paste.ubuntu.com/p/SWKNJKmJh3/](http://paste.ubuntu.com/p/SWKNJKmJh3/)

---

### Post by jdeca57 on 2019-01-15
You're looking at it from the wrong side. Use a Windows restore DVD or USB and you will get a booting Windows back. The problem is of course that most probably you won't get Ubuntu anymore and then you revert to the earlier problem: what did you do to lose Windows because from the Linux side another OS is always respected and it should be in a Grub menu.

---

### Post by oldfred on 2019-01-15
You have a new UEFI system.
It looks like  you installed Ubuntu in UEFI boot mode (originally) and have the live installer running Boot-Repair in UEFI boot mode.
You have Windows installed in the now 35 year old BIOS/MBR. And have a BIOS boot grub in MBR of sdc. But since sdc is gpt, it really wants a bios_grub partition for grub to correctly install.
UEFI has CSM for backwards compatibility, but Microsoft has required vendors to install all new systems with UEFI/gpt since Windows 8 released 5 years ago.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
UEFI and BIOS are not really compatible. Once you start booting in one mode you cannot switch to another boot mode. Or grub will only boot another install whether Ubuntu or Windows if installed in same boot mode.
If Secure boot is on (which it looks like yours is), you cannot boot in BIOS mode. Turn off UEFI Secure Boot.

You can reinstall Windows in UEFI mode, or add a tiny 1 or 2MB unformatted partition with the bios_grub flag, so you can boot Ubuntu on sdc in BIOS mode. You can shrink your ESP - EFI system partition (sdc1) by 3 or 4MB and create a new 1MB unformatted bios_grub partition. Then use Boot-Repair to reinstall grub to sdc (only). Do not use any auto fix with Boot-Repair, only advanced mode. Autofix will try to install grub to MBR of every drive and you want to keep the Windows boot loader in the MBR of sda.

With UEFI Secure boot off, and system set for Legacy/CSM/BIOS boot, you should be able to choose sda and boot Windows. UEFI boot may work for Ubuntu, if you installed UEFI boot files for grub, but then may have to change boot mode to switch systems.
If using Windows a lot, I would stay with BIOS for now. Keep ESP partition on sdc and later you can easily convert it to UEFI boot. I have both ESP & bios_grub on multiple systems, but normally only use one or the other.

Turn off UEFI Secure Boot.
Check if Windows then boots, otherwise you may need other Windows repairs.
Shrink sdc1 and create 1MB bios_grub partition.
Use Boot-Repair's advanced mode (booted in BIOS mode) to reinstall grub to sdc, only.
Set UEFI/BIOS to boot sdc first and you should be able to boot Ubuntu or Windows from grub menu. But grub only boots working Windows. So if hibernated or needs chkdsk, you may be able to directly boot using Windows boot loader on sda. But still best to have Windows repair flash drive.

---

