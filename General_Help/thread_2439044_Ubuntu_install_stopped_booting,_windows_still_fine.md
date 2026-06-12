---
title: "Ubuntu install stopped booting, windows still fine"
date: 2020-03-22
forum: General Help
---

### Post by merockstar on 2020-03-22
I have a terabyte harddrive with ubuntu installed, and an ssd with windows.  I've been dual booting a while now just fine, but this morning randomly I woke up to an error on my ubuntu install:

```

Unexpected return from inital read: Volume corrupt, buffersize 400
Failed to load image \EFI\UBUNTU\grubx64.efi: Volume corrupt
start_image() return volume corrupt

```

so, searching around a little, i decided to try makes a boot USB, installing boot-repair, and running that. it failed. now instead of the above error i go to a grub screen.
heres the url boot-repair gave me: [http://paste.ubuntu.com/p/rSMwMXh4WK/](http://paste.ubuntu.com/p/rSMwMXh4WK/)

I'd hate to have to reinstall. Finally got everything set up the way I like it.
Windows boots just fine normally.
Am I hosed?

---

### Post by yancek on 2020-03-22
The end of the boot repair output starting at linee 1320 tells you to set the boot in your BIOS to boot from the Ubuntu file on the EFI partition on sdb2.  Problem is that you have installed Ubuntu in Legacy mode on the larger drive and windows is EFI on the smaller drive.  A legacy install of Ubuntu with GRub will not boot a windows EFI system.  You should have installed Ubuntu in UEFI mode.  See the Ubuntu documentation at the link below.  You have Ubuntu Grub code in the MBR of the larger drive so you should be able to boot it by selecting that drive from the Boot Options in the BIOS firmware.  Unless you install Ubuntu UEFI , you will need to switch drives in the BIOS each time you want to go from Ubuntu to windows or windows to Ubuntu.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-03-22
It looks like you installed Ubuntu to the 35 year old MBR configuration, but have UEFI boot files in the ESP on sdb2.
Since Ubiquity only installs UEFI boot loader to first drive, did you swap drives? Or was this from Boot-Repair re-installing grub which can install it to another drive. Your fstab shows mount of ESP for UEFI boot. And it shows Linux drive as sda when you installed.

And then it looks like at some point you did install in BIOS boot mode as you have or still have grub in MBR of drives for BIOS boot.

UEFI strongly suggests you use gpt partitioning. Windows requires gpt partitioning for UEFI boot. But Ubuntu lets you install to MBR with UEFI, and maybe it should not.

If you have good backups, reinstall should not be an issue. Good backups let you reinstall Ubuntu, restore /home, reinstall your applications from exported & backed up list & maybe some system wide settings that would be in /etc. The settings I change in /etc are mostly grub related & I copy those into /home so I back those up also.

You also can convert a drive from MBR to gpt. You still need good backups & at minimum have to reinstall grub. You may need to update UUIDs in fstab & other places.
Converting to or from GPT - must have good system backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR, backup partition table just in case
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
sudo sfdisk -d /dev/sda > backup_sda.txt

---

