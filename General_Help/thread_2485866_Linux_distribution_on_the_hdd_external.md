---
title: "Linux distribution on the hdd external"
date: 2023-04-12
forum: General Help
---

### Post by tuturazvan on 2023-04-12
[COLOR=#333333][FONT=&amp]Hi,[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]This topic has probably been discussed before and I apologize in advance if so. I would need to have the linux distribution on the hdd external to be able to use it anywhere.I installed the system, it tells me that it is a complete installation, the files exist and the partition does not boot. I don't want to have dual boot, I want the boot loader to be on the hard drive and to be a functional system wherever I connect it.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Thank you in advance.[/FONT][/COLOR]

---

### Post by oldfred on 2023-04-12
If UEFI system which all systems since 2012 are, you need an ESP - efi system partition on external drive with boot files.
Ubuntu only installs UEFI boot files to ESP on first drive, normally your internal Windows drive's ESP.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Has multiple work arounds when installing.

If already installed & you have ESP, change fstab to use the external drive's ESP and reinstall grub either with Boot-Repair or chroot.
If no ESP, create a FAT32 partition with esp,boot flags using gparted and update fstab with that new UUID.

cat /etc/fstab
lsblk -e 7 -o name,mountpoint,label,size,fstype,uuid,partuuid

---

### Post by dragonfly41 on 2023-04-12
Install an EFI partition inside the portable SSD at time of installation.
Create boot flags thtough GParted on EFI.
Then optionaly instaal rEFInd into that EFI.
Read many liks pubished by "OldFred" et al. (P.S. he got here 1 minite earlier. Read his stuff.)

Here is a screenshot of one ext SSD I use. Taken from Gparted view of SSD.

Clipped screenshot taken by Flameshot.

[https://i.imgur.com/1gmoqMy.png](https://i.imgur.com/1gmoqMy.png)

---

### Post by sudodus on 2023-04-14
You can extract and clone an Ubuntu Server installed system from a compressed image file. This system is portable between many computers and fits well on an external drive.

If you wish, after booting into the Ubuntu Server you can install a graphical desktop environment and get Ubuntu Desktop or one of the Ubuntu community flavours. Read the whole thread via [this link](https://ubuntuforums.org/showthread.php?t=2474692).

---

