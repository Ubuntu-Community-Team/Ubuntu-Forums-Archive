---
title: "Dual booting question"
date: 2018-05-14
forum: General Help
---

### Post by moonlit1 on 2018-05-14
Hi, I have a 60gb SSD with windows installed on it and I use a 1TB Hard drive for storage on windows. I was wondering if I can install ubuntu on the 1TB Hard drive instead of the SSD but still be able to use part of the hard drive for windows storage. Or do both OS partitions have to be on the SSD for it to dual boot?

---

### Post by oldfred on 2018-05-14
UEFI or BIOS?
Even 60GB is not large for Windows.

You can install Ubuntu on the HDD. 
But if Windows is UEFI on gpt partitioned drive, best to have Ubuntu boot in UEFI mode from gpt partitioned drive.
If BIOS just install grub2's boot loader to HDD, not SSD. 
With UEFI, grub will automatically install to first ESP - efi system partition probably your SSD.

Be sure to use Windows to shrink NTFS partition on HDD, and reboot and run chkdsk. 

If Windows 8 or 10 make sure fast start up is off, otherwise Ubuntu install will not see or correctly see NTFS hibernated partitions.
I like to use a smaller / (root) partition often 25 or 30GB and then have a large shared data partition. If newer user, it will be easier to have a separate /home partition as then format, mount, and ownership & permissions are automatically set with /home. And you still can share NTFS data partition(s) as long as fast start up is off. Windows update also may turn fast start back on, so if grub does not boot Windows or your cannot access the NTFS partition that would be the first thing to check.

Only use Something Else install option, auto install options may try to shrink the wrong partition or try to install to incorrect drive. Do not use LVM or encryption as that erases entire drive or erases all existing partitions and data.

---

