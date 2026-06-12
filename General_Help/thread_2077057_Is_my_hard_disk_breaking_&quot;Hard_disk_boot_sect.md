---
title: "Is my hard disk breaking? &quot;Hard disk boot sector invalid&quot;"
date: 2012-10-27
forum: General Help
---

### Post by 25tom on 2012-10-27
I've just installed CrunchBang Linux Statler alongside my existing Ubuntu Natty Narwhal and when I rebooted after the install I got a "Hard disk boot sector invalid" message. Suspecting that installing grub during the CrunchBang install had caused this problem, I used the Super Grub2 Disc to boot (both operating systems work fine, just can't use HDD to boot) and in Ubuntu ran ```
sudo update-grub
``` and also ```
sudo grub-install /dev/sda
``` but the problem persists. I'm not sure whether this is a hardware error or a software error, but any advice on how to fix it would be much appreciated; thanks in advance :)

---

### Post by oldfred on 2012-10-27
Grub does not use boot flag. 
Windows has to have a boot flag on a primary NTFS partition to boot.

But some BIOS throw a boot error if no boot flag is shown on a primary partition. So check that you have a boot flag on any primary partition. (for Linux it does not even have to be the one you use to boot from).

---

### Post by 25tom on 2012-10-27
> **oldfred said:**
> Grub does not use boot flag. 
Windows has to have a boot flag on a primary NTFS partition to boot.

But some BIOS throw a boot error if no boot flag is shown on a primary partition. So check that you have a boot flag on any primary partition. (for Linux it does not even have to be the one you use to boot from).

I assume that the following means that sda6 has the boot flag; it used to be on sda1... could this be the cause of my problem, and if so, how do I rectify it? I assume it's safe just to move the boot flag in GParted, but I don't want to make things worse... would that be safe or not?

```
Disk /dev/sda: 50.0 GB, 50018393088 bytes
255 heads, 63 sectors/track, 6081 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000be212

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5031    40408442+  83  Linux
/dev/sda2            5031        6082     8435713    5  Extended
/dev/sda5            6021        6082      489472   82  Linux swap / Solaris
/dev/sda6   *        5031        5974     7569408   83  Linux
/dev/sda7            5974        6020      374784   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by oldfred on 2012-10-27
You can use gparted, Disk Utility, Boot-Repair or command line to change boot flag.

Windows MBR only boots primary partitions, so I think that is what some BIOS check for. The older Lilo boot loader works like Windows to use boot flag to know what partition to continue booting from, but will boot from a logical so a boot flag can be valid on a logical partition, just not for Windows.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
or
parted /dev/sda set 2 boot on

Change above 2 to 1 if you want flag on sda1.

---

### Post by 25tom on 2012-10-27
> **oldfred said:**
> You can use gparted, Disk Utility, Boot-Repair or command line to change boot flag.

Windows MBR only boots primary partitions, so I think that is what some BIOS check for. The older Lilo boot loader works like Windows to use boot flag to know what partition to continue booting from, but will boot from a logical so a boot flag can be valid on a logical partition, just not for Windows.

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
or
parted /dev/sda set 2 boot on

Change above 2 to 1 if you want flag on sda1.


OK, thanks, I'll change it and see what happens :)

---

### Post by 25tom on 2012-10-27
It works! Thankyou very much! :) :)

---

