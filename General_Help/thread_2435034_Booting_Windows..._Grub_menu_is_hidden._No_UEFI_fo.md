---
title: "Booting Windows... Grub menu is hidden. No UEFI for Windows 10"
date: 2020-01-15
forum: General Help
---

### Post by fluxburn2 on 2020-01-15
So I did it the hard way. Yah because it would have been easy to just install ubuntu auto, but I chose custom. 
when I pull an fdisk -l I see 2 partions

/dev/nvme0n1p1 Microsoft basic data
/dev/nvme0n1p2 Linux filesystem
/dev/nvme0n1p3 EFI system

I think I deleted the partions the UEFI file was for Windows
So I also noticed that mount is no longer really used or is it.. the same with bootcfg, and grub-config
I tried editing grub in /etc/defaults and making a grub.cfg file 
my grub file is configured to hide menu. 

I would like to get into Windows by Friday. But this has been a good exercise back into current linux, Good old linux. Been a couple years. Lots of work done. 
Thanks for the help in advanced.

---

### Post by oldfred on 2020-01-15
That is not a typical UEFI install of Windows, nor is it really a BIOS/MBR install?

Windows only boots in UEFI mode from gpt partitioned drives.
Windows only boots in BIOS mode from MBR partitioned drives.
Ubuntu will let you install either way to either partitioning, but should not as it needs to be in same boot mode as Windows.

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

This has not be updated to see all the details on NVMe drives, but shows a lot.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fluxburn2 on 2020-01-15
Yah, I'm pretty technical but this things a pain the the ass. I'm to the point I'm just going to reinstall windows 10. All I have to do is change a directory from hidden then I'm set. 

I tried for hours trying to get grub to recognize the Windows. Man I tried like so much stuff on ubuntu to get it to work. All I got was a to the point in boot mode for ubunut it goes into a loop. Have to hit ESC and load ubuntu that way now. I could fix it but whats the point.

---

### Post by fluxburn2 on 2020-01-16
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup) 
was interesting but doesn't fix it. Man

---

### Post by oldfred on 2020-01-16
Grub only boots working Windows that is installed in the same boot mode UEFI or BIOS as Ubuntu.
And working means Windows cannot need chkdsk nor be hibernated. 

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2020-01-16
> I tried for hours trying to get grub to recognize the Windows.

Apparently you haven't seen the site below which is the official Ubuntu documentation on dual booting with a windows UEFI system.
 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

