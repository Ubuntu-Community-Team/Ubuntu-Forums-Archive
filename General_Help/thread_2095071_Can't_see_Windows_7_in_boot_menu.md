---
title: "Can't see Windows 7 in boot menu?"
date: 2012-12-15
forum: General Help
---

### Post by VerneJules on 2012-12-15
Sorry, I'm not really familiar with Unix or Linux. I tried to install dual boot of Windows 7 and Ubuntu 12.10 in different partitions but when I boot, it doesn't seem to detect Windows 7. I also can't mount the partition where Windows 7 is installed. Is the fact that it's encrypted a factor for this? If so, what should I do?

When I run sudo fdisk -l, this shows. Windows 7 is installed in sda1 while Ubuntu is installed in sda6.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb5288382

Device 		Boot		Start		End		Blocks		Id	System
/dev/sda1				2048		330512383	165255168		7	HPFS/NTFS/exFAT
/dev/sda2				414603264	624521215	104958976		7	HPFS/NTFS/exFAT
/dev/sda3		*		624523264	625140399	308568		7	HPFS/NTFS/exFAT
/dev/sda4				330514430	414603263	42044417		5	Extended
/dev/sda5				330514432	330903551	194560		82	Linux swap / Solaris
/dev/sda6				330905600	414603263	41848832		83	Linux

Disk /dev/mappercryptswap1:199 MB, 199229440 bytes
255 heads, 63 sectors/track, 24 cylinders, total 389120 sectors
Units = sectors of 1 * 512 = 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifer: 0xee42c404

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Please help me, I really need to get *that* Windows 7 as I have important files there. I didn't think I would no longer be able to access those files so I didn't back it up.

I tried doing these even though I'm not familiar but they didn't seem to work.

[http://ubuntuforums.org/showthread.php?t=1664134&page=2](http://ubuntuforums.org/showthread.php?t=1664134&page=2)

This code doesn't see Windows 7:
```
sudo update-grub
```

Adding this code doesn't seem to work either as it says "Bootmgr is missing. Press Ctrl+Alt+Del"
```
menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
```

---

### Post by oldfred on 2012-12-17
Best to see all the details of your configuration.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

Boot-Repair will not fix most Windows issues but BootInfo report may show what is wrong.
Do you have Windows repairCD or USB?

---

