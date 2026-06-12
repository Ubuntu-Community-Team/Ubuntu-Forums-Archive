---
title: "Bootable Linux on a FlashDrive"
date: 2015-09-29
forum: General Help
---

### Post by Spud37 on 2015-09-29
What I would like to do is make a USB drive that I can use to recover both linux and windows. Either by scanning for viruses. Or just fixing the boot partition that happens to me alot when ever I install Linux. I am hoping that I can get help to choose the right distro and perhaps what apps to install onto said USB Drive. This would mostly be a recovery installation, Diskchecks, Ram checks. Basically find out why a computer may either not be booting or be having issues with any OS.

Any Help would be very much appreciated. Thanks

---

### Post by oldfred on 2015-09-29
How familiar with installing Linux are you?

Simple solution would be two flash drives, one Windows & one Linux.

Your Linux install can be just the normal liveCD installer with persistence so you can save some data or if flash drive is larger, a full install.

Some info on full vs live installer.
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

But my solution when I only had BIOS was to create a Windows 7 flash repair drive, then install grub to same partition, being careful to not overwrite /Boot/BCD so Windows could still be booted. Then I added a bunch of repair ISO and directly booted ISO & chained to Windows. 

Easier to have the two flash drives, and you still can create a multi-boot ISO flash drive. But now with UEFI & BIOS on some computers that adds another complication. I now have three repair flash drives. Two Linux only, one UEFI & one BIOS. I still have old Windows, but no older Windows to use it on. :)

[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)       

 Multiboot flash drive with second partition 
[http://ubuntuforums.org/showthread.php?t=2260697](http://ubuntuforums.org/showthread.php?t=2260697)
Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

 Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by Spud37 on 2015-09-30
> **oldfred said:**
> How familiar with installing Linux are you?

Simple solution would be two flash drives, one Windows & one Linux.

Your Linux install can be just the normal liveCD installer with persistence so you can save some data or if flash drive is larger, a full install.

Some info on full vs live installer.
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

But my solution when I only had BIOS was to create a Windows 7 flash repair drive, then install grub to same partition, being careful to not overwrite /Boot/BCD so Windows could still be booted. Then I added a bunch of repair ISO and directly booted ISO & chained to Windows. 

Easier to have the two flash drives, and you still can create a multi-boot ISO flash drive. But now with UEFI & BIOS on some computers that adds another complication. I now have three repair flash drives. Two Linux only, one UEFI & one BIOS. I still have old Windows, but no older Windows to use it on. :)

[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)       

 Multiboot flash drive with second partition 
[http://ubuntuforums.org/showthread.php?t=2260697](http://ubuntuforums.org/showthread.php?t=2260697)
Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

 Bootable UEFI USB Key
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)


I am fairly familiar with normal installation of linux. I have a large USB so installing ubuntu fully would be no problem onto would be no problem. also possible to partition it to have both ubuntu and windows on it. currently it just has a suite of portable apps to scan for problems on windows itself, however hardware checking is something i have been having trouble finding in a portable form i.e. checking hard drive, checking RAM.. etc. So my plan was to partition it with two partitions one with that suite and then a linux partition that could resolve issues like grub, checking ram, checking for other hard ware errors. It would be nice to be able to have it be both a full installation and almost a liveCD version incase i wanted/needed to install said linux onto the computer from the thumbdrive. I'm currently going though the threads and reading them, I do like the idea of having more then one. That actually sounds really useful. At this time I only have one. Thank you for your help. After I have read and done a bit more investigation given your leads I might post with another question looking for help on this thread.

---

### Post by oldfred on 2015-09-30
If you have Ubuntu or add the Disks tool to whatever flavor you install, you also have SMART tools. 
I think link shows the older Disk Utility. Smart data is now in tiny icon in upper right corner, and looks somewhat different.

 Disk Utility screen shots
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)
Top 5 Smart hard drive failure issues 5, 187, 188, 197 & 198 
[http://www.computerworld.com/article/2846009/the-5-smart-stats-that-actually-predict-hard-drive-failure.html](http://www.computerworld.com/article/2846009/the-5-smart-stats-that-actually-predict-hard-drive-failure.html)

There are many, many other Linux tools, some users like one or the other. But you use the one you know best. 

My problem is that Microcenter has a store just down the road. And behind counter is flash drives, their own house brand that is lower in cost and works. May not be fastest. I originally purchased one and it worked well. But then every time I would go into store, price was lower and/or capacity larger for similar price. Now USB3 are only slightly more than USB2. And with old system USB3 flash drive was still 10% faster on old USB2 port. Or I now have many flash drives. :)

---

