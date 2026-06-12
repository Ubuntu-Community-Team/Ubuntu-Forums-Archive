---
title: "Create Bootable Live Disk Partition"
date: 2017-05-25
forum: General Help
---

### Post by emilward on 2017-05-25
My laptop has a 120GB SSD (/dev/sda) that has Xubuntu 16.04 installed on it. My laptop also has a 16GB mSATA SSD (/dev/sdb) that is not being used for anything. What I would like to do is separate this into 2 partitions: a 2GB partition (/dev/sdb1) and a 14GB partition (/dev/sdb2). Then I want to create a bootable live disc from the 2GB partition (/dev/sdb1) and leave the the other (/dev/sdb2) as free space. I would like to be able to boot into sdb1 whenever I need a live environment to boot into and I would like to be able to have sdb2 for backup files. I tried using the Gnome-Disks-Utility to create the 2 partitions and then I chose the "Restore Image" option to burn the Xubuntu installation image to sdb1. But obviously there's no bootloader so my system couldn't boot into it. I tried the "Restore Image" option for the entire drive (/dev/sdb) but Gparted flagged in error with the remaining 15GB of free space on the drive. Is there any way I can accomplish this?

---

### Post by yancek on 2017-05-25
You can create your first partition and then create a boot directory on it and install Grub to that boot directory as explained at the link below.

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

After installing Grub, create a grub.cfg file with an entry pointing to the iso file for Xubuntu.  You can just copy the iso file to the same partition on which you have the /boot/grub directory and boot the iso directly.  The link below has a number of examples you might use.

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

The example below is what I used to boot an Xubuntu iso file directly which worked.  The example below is booted from the root of sdb1 (hd1,1) so you might have to change that.  You also need the "exact" correct name of the iso and the correct path.  If you copy your Xubuntu iso to the partition with the boot directory and your device is sdb, the entry below should work.

> menuentry "Xubuntu" {
    loopback loop (hd1,1)/xubuntu-16.04-desktop-amd64.iso
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper iso-scan/filename=/xubuntu-16.04-desktop-amd64.iso nomodeset quiet splash --
    initrd (loop)/casper/initrd.lz
}

After doing this, you can use GParted to create another partition with the remaining space on the usb for data.  If you are using an iso or a Live system on the first partition, in order to access the second partition on the usb, you would need to create the mount point and mount it each time you use it as it is a read-only fileystem and no changes are saved on reboot.  That's a very simple process so shouldn't be a problem.

---

### Post by oldfred on 2017-05-25
UEFI or BIOS?
Bit more complicated with UEFI, but I have done both.

With 16GB you have space for a full install.
And even with a full install on a 16GB flash drive I have modified my grub like yancek posted above to boot several ISO in my data partition. I used 8 for / and 8 for data. With 8GB you do not have space to add much, but you can then update it.

       [http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484)
[URL="http://askubuntu.com/questions/46624/how-to-create-a-bootable-usb-with-multiple-iso-images-in-it"]http://askubuntu.com/questions/46624/how-to-create-a-bootable-usb-with-multiple-iso-images-in-it
[/URL]Multiboot flash drive with second partition 
[http://ubuntuforums.org/showthread.php?t=2260697](http://ubuntuforums.org/showthread.php?t=2260697) 

This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows [URL="http://askubuntu.com/questions/46624/how-to-create-a-bootable-usb-with-multiple-iso-images-in-it"]
[/URL]

---

### Post by emilward on 2017-05-26
Thank you for the responses. I will definitely try these out.

---

### Post by cuthead on 2017-05-26
what is the file system of your image?if it is 9660 it is CDFS for CDROM,so UEFI will think HDD CDFS is CDROM but it is HDD so it fail.the live ubuntu file system is msdos,under uefi converter 9660 to msdos and copy efi and grub and ubuntu to usb flash drive and done. if you under bios dd the boot loader sector.maybe you fail dd img but it is working for me.
you can also use usb cdrom for live cd,use livecd to create live usb.
that is for bios
for uefi
you can create msdos file system,copy ubuntu file to msdos file system,remember copy the efi folder,boot the uefi and select efi.

best wishes

---

