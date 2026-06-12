---
title: "Ubuntu won't boot up from external hard drive"
date: 2015-04-19
forum: General Help
---

### Post by benjamin40 on 2015-04-19
So, I have been trying for the past day and a half to install Ubuntu on my computer (HP Pavilion G6). I have done everything people have said to do in order to boot up Ubuntu from my hard drive (change BIOS Boot order, etc.) but whenever I restart my computer, it just keeps booting up to Windows 8.1. Does anyone know why this keeps happening? Thanks for the help.

---

### Post by oldfred on 2015-04-19
Pre-Installed Windows 8? Or then it is UEFI.
HP modifies UEFI to only boot Windows which is not per UEFI standards.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

Most copy grub into /EFI/Boot and rename bootx64.efi and then name grub or shim to be bootx64.efi. Then you can boot the hard drive entry which still works in HP's UEFI. Details if needed in link in my signature.

If not post the link to the Summary report:
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by rrnbtter on 2015-04-20
Greetings,
I have personally never liked the way that Grub "screws around" with partitions on it's own without asking for user input. Hence, when I install to USB flash or HD I remove my internal drive from the machine so that Grub "must" install the boot loader to the external drive. No USB plugged in it boots to internal drive, plug in USB and it boots USB and without messing with the partition of the internal drive.

---

