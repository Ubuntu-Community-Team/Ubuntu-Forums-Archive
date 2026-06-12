---
title: "After grub EFI boot loader installation booting the windows partition is gone"
date: 2019-07-23
forum: General Help
---

### Post by Krischu on 2019-07-23
I have a Windows 10 partition on my system disk. I created a 100 GB Ubuntu partition after the Windows 10 partition (using gparted). The disk has a GPT partition table.

The only boot loader that no still exists is the grub boot loader which only shows the Ubuntu partition (and 2 memory tests).


How can I get back the options to boot into Windows? I have added another Windows partition also which I would like to add to the boot menu. How can I achieve this?

--
Christoph

---

### Post by oldfred on 2019-07-23
Windows only boots in UEFI mode from gpt, was it originally installed in UEFI boot mode? Not particular easy to convert a BIOS Windows system to UEFI Windows system. 
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) 

    How you boot install media UEFI or BIOS, is then how it installs and repairs for both Windows & Ubuntu. 
You may need to boot your Windows repair flash drive or installer with repair console and run Windows fixes.

Windows boot files are in the ESP - efi system partition or the FAT32 partition with boot flag which is the same partition Ubuntu/grub will use. Only ESP one per drive, but you can have other FAT32 if small partition.

       Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

