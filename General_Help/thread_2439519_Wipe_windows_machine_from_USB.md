---
title: "Wipe windows machine from USB"
date: 2020-03-28
forum: General Help
---

### Post by anelson0528 on 2020-03-28
Hi all. I have a Windows machine (Dell XPS13) that got corrupted during an update. I cannot access the windows startup menu, but from the BIOS startup menu I can boot Ubuntu on a connected USB stick and access all the files on my hard drive. 

I want to wipe everything from the hard drives and replace the operating system with Ubuntu.  There are six partitions on the disk currently, and I cannot figure out how to wipe, remove or overwrite any of them. 

From the install Ubuntu workflow, I have tried to "Erase disk and install Ubuntu" - I get an "input/output error during write on /dev/sda" and eventually "the ext4 file system creation in partition #2 od SCSI3 (0,0,0) (sda) failed."

I've also tried to wipe the hard drive manually from the Ubuntu command line, but it does not appear to work:
 $ sudo dd if=/dev/zero of=/dev/sda1 bs=1024 count=1[INDENT]1+0 records in
1+0 records out
1024 bytes (1.0kB, 1.0KiB) copied, 0.443302 s, 2.3 kB/s
[/INDENT]

Is there a way to fully wipe the existing hard drive? Everything I've tried so far seems to be unable to access the partitions (I've also tried this to do this though a USB stick with Windows installed, but was again unable to delete partitions or reinstall the operating system.)

Thanks for any help.

---

### Post by yancek on 2020-03-28
I'm not sure why you would get the input/output error on the 2nd partition of the drive you are trying to format.  I would expect the ERase disk option to do just that.  The dd command you posted would overwrite the first partition on the disk (sda1) not the disk (sda).

When you boot the Ubuntu usb, have you tried opening GParted to see if the partitions from your windows install are available?  If you do that, are the windows partitions seen?  You could try creating a new partition table from the Device tab in GParted if you have no data on the computer.

---

### Post by anelson0528 on 2020-03-28
Thanks for the response yancek.

I have tried dd with /dev/sda as well, with no different effects. 

When I open up GParted, I immediately get a "Libparted warning" that reads "Error fsyncing/closing /dev/sda: Input/output error". If I ignore that, I am able to see all of the existing partitions. If I try Device > Create partition table... I end up with the same "Input/output error during write on /dev/sda" I also tried to manually delete and resize each partition using GParted with the same result. 

Any suggestions?

---

### Post by oldfred on 2020-03-28
Have you changed to AHCI in UEFI for drives?
And best to update UEFI and if SSD, SSD firmware.

Which model XPS13? But issues may be common across models.
Dell XPS13 9370 Developer Edition - Install Windows after Ubuntu
[https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp](https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp)
Dell Laptop XPS13 7390
[https://ubuntuforums.org/showthread.php?t=2438323](https://ubuntuforums.org/showthread.php?t=2438323)
[https://www.dell.com/community/XPS/XPS-13-Developers-edition-new-one-2019-won-t-boot-from-USB/td-p/7410750](https://www.dell.com/community/XPS/XPS-13-Developers-edition-new-one-2019-won-t-boot-from-USB/td-p/7410750)
[https://github.com/NixOS/nixpkgs/issues/72936](https://github.com/NixOS/nixpkgs/issues/72936)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](https://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)

---

### Post by anelson0528 on 2020-03-28
Thanks for the info oldfred. I'll spend some time looking through the links. 

I'm running on an XPS13 9350, and booting the Flash Disk with ubuntu on it from UEFI boot. Secure boot is off. 

I'm not sure what you mean by change to AHCI - I only have options for UEFI and Legacy Boot

---

### Post by aljames2 on 2020-03-28
You may have a failing drive or mobo controller.  you could try to boot from a Live USB “try ubuntu” and run some diagnostics.  Perhaps this info can help:  [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by anelson0528 on 2020-03-29
Thanks for the tip aljames2

However, I'm unable to run the smartmontools tests:
> ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-5.3.0-28-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Command "Execute SMART Extended self-test routine immediately in off-line mode" failed: scsi error badly formed scsi parameters

I should note that I did also try running a diagnostic from the BIOS boot menu, which said everything was fine

---

### Post by oldfred on 2020-03-29
AHCI setting is in your UEFI settings on drives.

[https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329](https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329)
XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
RAID to AHCI
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100)

You can update your UEFI from Ubuntu.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)

---

### Post by ipv on 2020-03-29
> **anelson0528 said:**
> Is there a way to fully wipe the existing hard drive?

use a dos software to wipe the disk.

also, as already suggested check the health of your hard disk.

---

### Post by anelson0528 on 2020-04-09
[COLOR=#000000][FONT=&quot]I ended up buying a new hard drive and replacing it, which seems to have worked well. Thanks everybody for the help![/FONT][/COLOR]

---

