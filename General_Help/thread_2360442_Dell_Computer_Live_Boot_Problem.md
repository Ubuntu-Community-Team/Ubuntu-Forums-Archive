---
title: "Dell Computer Live Boot Problem"
date: 2017-05-04
forum: General Help
---

### Post by michael359 on 2017-05-04
Hello everyone,

 I'm having issues with booting Ubuntu and other Linux OS's from a Live USB on my laptop. On my key chain, I have 3 USB devices that I often use for my lab computer - with Ubuntu, Tails, and Kali Linux. All three of them are 32bit versions to increase compatibility with systems and I know they work. However, like all of the other OS's, Ubuntu freezes at the loading screen once the system boots on my personal laptop. I have messed around with my BIOS UEFI settings multiple times but nothing I change seems to work. Yes, secure and fast boot is disabled and my BIOS is up to date from the manufacturer's website. 

I contacted Dell about the issue and they directed me to you guys saying it's not their problem (my warranty is expired)

**Here are my specs:**
Dell Inspiron 15 7559
Windows 10 64bit Host OS
BIOS (UEFI): Dell Inc. 1.2.2 
Intel i5-6300HQ
1 x 8GB DDR3

More information can be provided upon request. 

This has been an issue with my laptop for a very long time now and its getting very frustrating. Please help me!

---

### Post by oldfred on 2017-05-04
The 32 bit version does not support UEFI.
If your system is 64bit UEFI, better to have another flash drive that is 64 bit UEFI.

I use one flash drive for many ISO, mostly for quick test or as repair.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

Creating a Full install that is UEFI bootable from USB external drive is a bit more complicated.
You have to manually partition in advance with the ESP - efi system partition (FAT32) as first partition. But grub never installs to it, and you have to manually copy files and rename them back onto flash drive. UEFI only boots USB external devices from /EFI/Boot/bootx64.efi. If you look at any UEFI installer that can install in UEFI mode it will have that path & file name.

---

### Post by michael359 on 2017-05-08
I was able to figure out how to finally install Ubuntu onto my system. Once you see the GRUB boot menu, press "e" to view a few lines of commands. At the end of the "linux" line, add the command "acpi=off". I was then able to successfully boot into Ubuntu. However, my keyboard drivers were not detected and I cannot turn off the back light or use the volume, screen brightness buttons.

---

### Post by oldfred on 2017-05-08
Some of your issues may be video driver related.
Have you installed the nVidia driver from the repository?

Some other Dell, may have similar issues?
  Dell XPS 8910  16.04.1 works, 16.04 did not
[https://ubuntuforums.org/showthread.php?t=2351949](https://ubuntuforums.org/showthread.php?t=2351949)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Black Screen on Install (15.04 & 15.10) Dell XPS 8900 
[http://ubuntuforums.org/showthread.php?t=2303880](http://ubuntuforums.org/showthread.php?t=2303880)
Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359)
Uses Intel Wi-Fi adaptors
[http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/](http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/)
Dell with Ubuntu pre-installed loopmount ISO for recovery
[http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu](http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)

---

