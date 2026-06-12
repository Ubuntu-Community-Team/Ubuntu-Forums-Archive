---
title: "Stuck on GNU Grub, Cannot boot from USB or Live CD."
date: 2018-01-29
forum: General Help
---

### Post by davtk8 on 2018-01-29
Not sure if I am in the right thread to get answers.

I am stuck on the GNU GRUB command line because my MBR seems messed up.

I don't know which partition is my primary boot.

(hd0) (hd0,msdos1) (hd1) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (cd)

I am trying to get around the grub so I can boot from either Ubuntu or Windows CD to do a complete reformat of my hard drive. But cannot boot from them as I don't know what command I need to try to boot into it.

My Laptop is an Acer Aspire ES1-521, UEFI Bios. Dual Booted Windows and Ubuntu.


Both my Windows and Ubuntu are corrupted.
[ATTACH=CONFIG]278368[/ATTACH]

---

### Post by oldfred on 2018-01-29
If UEFI system you should not have MBR(msdos) drive, unless your flash drive (usually MBR for BIOS or UEFI boot) is promoted to sda/hd0. Normally flash drive is last in enumeration of drives.
UEFI uses gpt.
UEFI systems do not boot from MBR, but from ESP - efi system partition which is a FAT32 formatted partition with boot flag.

Are you booting in UEFI boot mode?
Did you set UEFI password and enable trust on Ubuntu UEFI boot files?
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
       Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269)
[https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533](https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533) 
            Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511) 
            Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

---

### Post by davtk8 on 2018-01-29
I switched to Legacy on BIOS, I've managed to boot a Windows USB Recovery so I can remove all the partitions using DiskPart on my SDHC.

---

