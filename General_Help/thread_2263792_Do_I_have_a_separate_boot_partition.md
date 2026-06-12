---
title: "Do I have a separate boot partition?"
date: 2015-02-03
forum: General Help
---

### Post by alasdair3 on 2015-02-03
I have ubuntu server 14 on a 16gb usb and have been unable to get the system to boot for an unknown reason. At the moment it loads the GRUB menu but the only item is "system setting" which it loads automatically. It doesn't seem to see any kernels. 

I'm trying to reinstall grub but am slightly confused by my disk partitions which were setup automatically using guided lvm partitioning during the install. I have two main queries:

1) there is a 512mb fat32 partition at the beginning of the disk with a "boot" flag. Is this supposed to contain data and is this a separate boot partition?

2) there is a 256mb ext2 partition next that contains grub and efi directories and what look like kernel files. Is this a separate boot partition?

My system files are on a third partition in the /root logical volume with a /boot directory. Essentially I am confused about exactly where I should reinstall grub and where the kernels should be for grub to load them. 

I'd be very grateful for some help as my system has been unusable for the past 10d and I'm really struggling to fix it. 

Many thanks

---

### Post by yancek on 2015-02-03
The kernels are usually in the boot directory which may or may not be on a separate partition.  I don't use LVM myself but from what I have read, there usually needs to be a separate boot partition.  Using efi, there is usually a FAT32 partition at the beginning of the disk to contain the system efi boot files.  I don't use EFI either, but my understanding is these files need to be on a FAT32 partition.  You might try a search for UEFI with LVM while you are waiting for a response from someone who has a little more knowledge on the subjects.

---

### Post by alasdair3 on 2015-02-03
Thanks for your help. 
From what you have said and my inderstanding from reading around, the fat32 partition is a separate boot partition. So I guess this should contain grub and the system kernels. At the moment it only seems to contain grub related files. 

I still don't understand what this 256mb ext2 partition that also seems to contain grub files in addition to kernels is though. Why would there be two separate boot partitions?

---

### Post by grahammechanical on 2015-02-03
It is my understanding that Grub is not installed to a boot partition. We install Grub to the MBR of a selected disk. And grub then looks for its configuration files in a boot partition, if there is one or in the /boot directory of the partition where Ubuntu is installed.

We can install Grub to a partition. But it is not necessary to do that. We can install Ubuntu with a boot partition but not it is not necessary to do that. I have two hard  drives without UEFI or GPT and when I want to re-install Grub I run either of these commands depending on the drive I want Grub installed to.

```
sudo grub-install /dev/sda
```
```
sudo grub-install /dev/sdb
```

I do not have any boot partitions.

Regards.

---

### Post by oldfred on 2015-02-03
Gparted has confused the issue with UEFI. It uses the boot flag to indicate the efi partition. But with gpt partitioning it really is a very long GUID and gparted is just using the boot flag as a shortcut or simple way to assign the GUID. Other partition tools like gdisk use a code ef02 as the similar short way to assign the long GUID.
Windows uses boot flag to define bootable Windows install. But again with UEFI the boot flag is on the efi(ESP) partition.
Grub does not use boot flag.

But then with LVM you do have a /boot partition that is ext2 by default. That has grub.cfg & files & kernels. The part of grub in the efi partition is more equivalent to the parts of grub that are in MBR and sectors after MBR(core.img) in BIOS boot. And there is a tiny grub.cfg in the efi partition that really is just a configfile that refers to the real grub.cfg in /boot.

---

### Post by alasdair3 on 2015-02-03
Part of my problem is that I am unsure about whether or not I have a boot partition and exactly what files should be where in order to get the system to boot. I suppose I have only myself to blame for just using the default guided partitioning on install without knowing exactly what was what. The use of Uefi and lvm has further complicated matters. 

Does anyone know exactly what the partitions I previously described are for and what they should contain for a system to boot?

---

### Post by alasdair3 on 2015-02-03
Ok. So from what I understand, the 256mb ext 2 partition is effectively the /boot partition and should contain grub and kernels. The 512mb fat32 partition at the beginning of the disk is the efi partitition and should contain a small part of grub to load the main part in the /boot partition. Presumably then, the /boot directory in my /root logical volume is not required for the booting process at all?

If I reinstall grub to the 255mb ext2 /boot partition, how do I put the necessary files(s) in the efi partition?

Thanks again.

---

### Post by oldfred on 2015-02-03
Posted answer about same time as your question. See post above.

If a new user and not really familiar with LVM, I would not suggest using it. I do not use it, but some users like it. It is an advanced partitioning system and does not use standard partition tools. You have to use LVM tools. It requires the separate /boot partition.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

If doing a standard partitioned install, I do not suggest a separate /boot partition. LVM, encryption and some server type installs may need a /boot and some very old BIOS may need it, but most users with desktop installs do not need it.

---

### Post by alasdair3 on 2015-02-03
Unfortunately I just followed the default settings during install, assuming it was the standard. In retrospect it was a mistake. 

Unfortunately there isn't much I can do about it now, I just need a way to repair the booting. Unless there's a way to reinstall ubuntu without losing all my current system setup?

---

### Post by oldfred on 2015-02-03
You should be backing up all your configuration & data anyway. Then reinstall is not a big issue.
But since you have LVM, it does become a total reinstall. And LVM is not the standard default, it is just an option on the install menu.

No idea why you are not booting. Did you run Boot-Repair?

---

### Post by alasdair3 on 2015-02-03
Yeah, tried boot-repair but it gave me errors because the disk contained GPT. Presumably I can still make a backup of my system as I can access it via a live USB. Not entirely sure how to make the backup and then copy it to a new install though.

---

### Post by alasdair3 on 2015-02-03
Reading through lots of guides on reinstalling grub efi, the majority have a step where the efi partition is mounted in /boot/efi.

Two questions about this:
 1) Is the "efi partition" the 512mb fat32 partition?
 2) if I have a separate /boot partition do I mount the efi partition within this /boot partition at the efi directory?

---

### Post by oldfred on 2015-02-03
Both partitions are auto mounted by the installer.

Your FAT32 efi partition is mounted at /boot/efi and your ext2 /boot at /boot. They are not mounted inside each other as they are totally separate and have different formats & functions.

To see yours current entries:
cat /etc/fstab

---

