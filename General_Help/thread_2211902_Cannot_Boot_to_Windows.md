---
title: "Cannot Boot to Windows"
date: 2014-03-18
forum: General Help
---

### Post by pensword on 2014-03-18
Hey folks. Just updated to Ubuntu 13.10. I am running Ubuntu and Window from the same hard drive. I currently cannot boot to Windows.

My hard drive is partitioned. sda2 is windows. Originally, the laptop was set to boot automatically to Windows 8. Now, although it is available as an option in the GRUB, choosing it simply does nothing. No warning messages, nothing. Because there is no warning message or anything, I've got specific lead on where to look for a solution. 

The source information for the Windows 8 option via Grub Customizer:

```
insmod part_msdos
insmod ntfs
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  56D64BDBD64BBA4F
else
  search --no-floppy --fs-uuid --set=root 56D64BDBD64BBA4F
fi
drivemap -s (hd0) ${root}
chainloader +1


```

Any help on this issue would be appreciated.

ASUS u-43f laptop

---

### Post by oldfred on 2014-03-18
Grub only boots working Windows.

Since Windows 8, did you leave it hibernated or the always on hibernation called fast boot?
Also after a resize or any issue Windows needs to run chkdsk and that can cause issues.

Best to use your Windows repair flash drive to fix your Windows. You may be able to temporarily install a Windows boot loader with Boot-Repair or your Windows repairCD and use f8 to get to repair console.

Boot-Repair can only do minor fixes to Windows. You need Windows repair tools.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

