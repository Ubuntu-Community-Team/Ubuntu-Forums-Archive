---
title: "&quot;No bootable devices&quot; when booting from internal MMC!"
date: 2017-07-17
forum: General Help
---

### Post by chrisk0 on 2017-07-17
Trying to install Xubuntu 16.04 on a Dell Inspiron 3000 laptop, after having considerable problems with Windows 10. This laptop has a 32 gig flash storage instead of a hard drive.

Can run the Xubuntu liveUSB on a 16 gig MicroSD card fine, and installed from there. (Used Rufus to set up the microSD card from the 64bit ISO.)

However, when I try to boot directly from Flash storage, I always get:
No bootable devices -- 
strike F1 to retry boot, F2 for setup utility. Press F5 to run onboard diagnostics.

What I've tried so far:
Grub boot-repair: [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)
Looking in BIOS to make sure that it can see the MMC flash storage, that's fine.
Wiping out all partitions from the MMC using gparted in liveUSB and installing again.
Using fdisk (from the liveUSB) to make sure that the main partition of the MMC is marked as boot

I found a few very old threads here talking about similar problems, and even solving them, but many referred to an 'advanced button' in the installer, which my version didn't seem to have anymore. So I thought I would start a brand new thread. If you need more information, then tell me what to look for!

And thank you very much in advance for any assistance!

---

### Post by oldfred on 2017-07-17
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by chrisk0 on 2017-07-17
Thank you very much!

Boot-Info report is here: [https://paste2.org/ykn4zWI1]("https://paste2.org/ykn4zWI1")

---

### Post by oldfred on 2017-07-17
Report does not fully show mmcblk devices.
But it looks like you have just / & swap with swap in the extended partition. So it must be a BIOS/MBR install.

Boot-Repair also says you may have UEFI Secure Boot on. Make sure it is off.
In UEFI mode with secure boot on, it would not see a BIOS boot option.

---

### Post by chrisk0 on 2017-07-17
Thank you.

Secure Boot is definitely off and UEFI/Legacy is set to Legacy in the BIOS setup. Without those, I can't get it to boot off the liveUSB card.

I've tried turning UEFI/Legacy on in the BIOS, and get a different "No bootable devices" Dell screen.

Any ideas for where to go next? Can I do something to give you a report with full data on mmcblk devices?

---

### Post by oldfred on 2017-07-17
Boot-Repair uses bootinfoscript for the first part of the report. And bootinfoscript does not yet include mmc & NVMe devices.

I would first let Boot-Repair reinstall grub to MBR, or perhaps in Advanced mode the full uninstall/reinstall of all of grub.

Since BIOS install make sure system is set for CSM/BIOS/Legacy and you also boot flash drive live installer in BIOS mode.

---

### Post by chrisk0 on 2017-07-17
Thank you.

I believe this issue has now been solved... I've gone from 16.04 to 17.04, and figured out how to install using UEFI. Now I have a few new issues to sort out, but it's definitely booting from the onboard flash. Thanks for all your help!

---

