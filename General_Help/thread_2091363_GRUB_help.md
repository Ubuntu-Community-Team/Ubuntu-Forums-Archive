---
title: "GRUB help"
date: 2012-12-04
forum: General Help
---

### Post by LifeWithoutWindows on 2012-12-04
so I accidentally my Ubuntu partition, which somehow killed GRUB. Now when I turn on my computer, even though I have verified that the HDD is the last thing on the boot order, it will still go directly to the GRUB rescue prompt. I cannot load anything off a USB key without removing the hard drive. the only thing I know with the GRUB command line is ls.

when I enter ls, it returns:
```
(hd0) (msdos5) (msdos4) (msdos3) (msdos2) (msdos1)
```

how do I boot windows?

---

### Post by oldfred on 2012-12-04
Easier to reinstall Windows boot loader from your Windows repairCD which you made of course when Windows was working. It is now $10 to download.
Or from Ubuntu install a Windows work alike boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

     
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

