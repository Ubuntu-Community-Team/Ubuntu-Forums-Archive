---
title: "How to remove Windows 10 from Dual Boot with Kubuntu"
date: 2019-06-16
forum: General Help
---

### Post by quce on 2019-06-16
Hello, I dual booted Windows 10 and Kubuntu on my PC. I tested Kubuntu and right i want to remove Windows 10 from the dual boot and have only Kubuntu as my main OS :D:D;).

I would like to remove EVERYTHING that Windows 10 leaves, like windows boot loader, recovery partitions etc. Also I would like to completely remove the partition that Windows boot loader is located and create a new partition just for GRUB (like a normal Ubuntu installation, that is not dual boot). Here's a screenshot from KDE Partition Manager : [http://imgur.com/a/bKQywJT](http://imgur.com/a/bKQywJT)

I want just to have root(/) and GRUB, but I don't know how to install GRUB manually.

---

### Post by oldfred on 2019-06-16
Many users later find one application or game or then want to sell system and must have Windows.
I would suggest a full backup of Windows before you delete it.

Grub uses the same ESP - efi system partition as Windows. Your sdb2.
Is sda a flash drive or another hard drive? Normally the install drive is seen as sda.
Or did you add a drive and use a higher numbers SATA port so UEFI puts it later in drive order?

Often easier to do a total new install & restore from your backup. It does not look like you have a separate /home partition which can make new installs easier.

You can remove the UEFI boot entries in UEFI with efibootmgr and remove the /EFI/Microsoft folder in the ESP. But you need the Ubuntu boot entries in UEFI and /EFI/ubuntu & /EFI/Boot in the ESP to be able to boot.
You do then only need / (root), but many suggest separating system from data. For a newer user, creating /home is easier than creating data partitions, creating mount for data partition and giving yourself ownership & permissions to use the data partition. A /home does all that automatically.

Delete UEFI entries:
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
# see also
man efibootmgr 

        Uninstall Ubuntu from menu, Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

