---
title: "My problem using boot-repair"
date: 2022-03-06
forum: General Help
---

### Post by duytanvo on 2022-03-06
Hi all,

I currently installed ubuntu alongside with windows 7 on my computer but then i ran into problem with windows 7 unable to boot. I tried to use boot-repair to fix it but the recommended repair notifies "Please use this software in a live-session (live-CD or live-USB). This will enable this feature."

What can i do to enable that?

Also my boot info from the boot-repair here: [https://paste.ubuntu.com/p/4YhsHdGqHQ/](https://paste.ubuntu.com/p/4YhsHdGqHQ/) If possible, can you tell me where's the problem with that and can i fix it with the boot-repair?

---

### Post by wyattwhiteeagle on 2022-03-06
> **duytanvo said:**
> Hi all,

I currently installed ubuntu alongside with windows 7 on my computer but then i ran into problem with windows 7 unable to boot. I tried to use boot-repair to fix it but the recommended repair notifies "Please use this software in a live-session (live-CD or live-USB). This will enable this feature."

What can i do to enable that?

Also my boot info from the boot-repair here: [https://paste.ubuntu.com/p/4YhsHdGqHQ/](https://paste.ubuntu.com/p/4YhsHdGqHQ/) If possible, can you tell me where's the problem with that and can i fix it with the boot-repair?

Have you tried something from one of these two guides?
[https://help.ubuntu.com/community/Grub2/Installing#:~:text=Open%20a%20terminal%20by%20selecting,MBR%20of%20the%20designated%20device](https://help.ubuntu.com/community/Grub2/Installing#:~:text=Open%20a%20terminal%20by%20selecting,MBR%20of%20the%20designated%20device).
[https://www.ubuntupit.com/how-to-repair-the-grub-bootloader-using-a-ubuntu-live-usb-drive/](https://www.ubuntupit.com/how-to-repair-the-grub-bootloader-using-a-ubuntu-live-usb-drive/)

---

### Post by oldfred on 2022-03-06
Partitions have a PBR that is structured like the MBR. Also called BS or Boot Sector.
But Windows PBR must have Windows info in it. You installed grub to NTFS PBR.

While you should not normally install grub to PBR, and never to NTFS PBR, testdisk may say it is ok, since you can install grub to PBR.
NTFS does keep a backup PBR and you usually can restore backup.

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by duytanvo on 2022-03-06
It worked! Thanks a lot for your help

---

