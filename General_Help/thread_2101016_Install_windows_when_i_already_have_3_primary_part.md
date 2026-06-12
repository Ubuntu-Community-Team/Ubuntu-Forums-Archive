---
title: "Install windows when i already have 3 primary partitions?"
date: 2013-01-03
forum: General Help
---

### Post by ELD on 2013-01-03
I understand that you can only have 4 primary partitions on a drive, I  already have ubuntu on the first partition labelled as boot, then i have  an extended area filled with a /home partition, swap space partition  and then free space.

Is there a way to get windows onto that free space without giving me an error because of the partitions?

---

### Post by oldfred on 2013-01-03
Are you really only using two primary partitions? Windows will install to any primary partition sda1 thru sda4 formatted NTFS with the boot flag.

But a few have reported issues with Windows primary partition after the logical partitions. While Windows works with logical partitions and reads a shared NTFS data partition as a logical partition,  it has sometimes corrupted the partition table during install. Best to have good backups.

You may want to shrink extended & create new NTFS primary partition, but also backup partition table so you can restore it if necessary. You will also have to reinstall the grub2 boot loader to the MBR as Windows will install its boot loader.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2


       
 Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

