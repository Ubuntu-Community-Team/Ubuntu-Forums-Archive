---
title: "unable to boot xubuntu 20.04"
date: 2021-05-13
forum: General Help
---

### Post by Furycd001 on 2021-05-13
HI guys.. On Monday I done a fresh install of xubuntu 20.04. Everything was working just fine until this morning when my system completely locked up. I waited for a bit to see if it would come back and start responding, but no nothing happened. I held down the power button to power off and then reboot. Upon rebooting I get stuck at /dev/sda5: clean, 414951/61022208 files, 103882571/244058880 blocks. The system never moves on past this and I cannot get to the desktop or any of the ttys. I've booted to the installer usb and run fsck -f /dev/sda5 but there is no problems detected. Could someone please help me get back to my desktop without having to do another reinstall. Many thanks in advanced....

---

### Post by ajgreeny on 2021-05-13
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may show us what the problem is. 

You may also get more detailed information if you try pressing Esc after grub has finished as that may show you a scrolling text boot process giving some clue about what the freeze is all about. This will, however, depend on exactly where the boot process has got to and may not work at all.

---

### Post by Furycd001 on 2021-05-13
Ok So I installed & ran boot repair on my live usb. [Here is the output....]("https://paste.ubuntu.com/p/MB23pdcDz7/")

---

### Post by tea for one on 2021-05-13
You have a mixture of Legacy mode and UEFI mode installation.

sda is msdos table
sda1 is EFI System Partition (ESP)
sda2 is extended (i.e. Legacy format which only allows 4 primary partitions)

As you only installed a few days ago, it would be opportune to re-install cleanly to give you a future proof PC.
The modern practice is to use GPT and UEFI mode.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[COLOR="#0000FF"]Backup[/COLOR] your data

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Disable TPM

Boot into a live session in [COLOR="#0000FF"]UEFI[/COLOR] mode (how you boot determines the installation mode)
Use gparted to create a GPT (GUID Partition Table)
Allow the installer to automatically create the necessary partitions.

Happy days

---

### Post by Furycd001 on 2021-05-13
Thanks for the heads up, but is there no way I can recover my current installation without having to reinstall everything ??

---

### Post by tea for one on 2021-05-13
Have a look at the suggested repair in lines [COLOR="#0000FF"]264 - 285[/COLOR] of the boot-repair report.

It describes the situation of Legacy and UEFI of your PC.

---

### Post by Furycd001 on 2021-05-13
Just opted to do a reinstall....

---

