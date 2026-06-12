---
title: "GRUB2 doesn't install while setting up Dual Boot alongside Windows 8"
date: 2017-02-12
forum: General Help
---

### Post by morphior on 2017-02-12
Hello,

so I've been trying to install Ubuntu alongside Windows. I created a USB drive with the ISO and booted from it. I hit "Install Ubuntu" and followed the instructions. I then used the partition table to create an EXT4 partition (50GB) mounted to /, one EXT4 partition mounted to /home and a swap partition (16GB). So far, so good. The boot loader is supposed to install in /dev/sda. When I hit install, it runs through the installer up to the point where it wants to install GRUB - and then it aborts. It says "Fatal Error". What can I do?

This is my boot info:
[http://paste2.org/LZ0LNdwH](http://paste2.org/LZ0LNdwH)

Thanks for any help!

---

### Post by oldfred on 2017-02-12
I can see where grub might be confused.
You have 3 ESP - efi system partitions, sda2, sda6 & sda8.
You are supposed to only have one per device, or just sda2.
Use gparted and remove boot flags from sda6 & sda8.

With UEFI you have only one ESP which is a FAT32 formatted partition with the boot flag. That is where UEFI will look for .efi boot files to boot system. All installs share one ESP per device.

Then rerun Boot-Repair to install Ubuntu/grub's entry in to UEFI and folder in ESP for grub's boot files.

But you have an Acer, which has unique requirements on setting an UEFI password and enabling trust on the .efi boot files in /EFI/ubuntu from within UEFI.
Some older threads mention downgrading UEFI from Acer as it had issue. But newer threads say newest Acer UEFI works. So make sure you have newest UEFI from Acer.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431) 

        Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
            Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by morphior on 2017-02-12
I just tried that and it still fails. I'm kind of lost.

---

### Post by oldfred on 2017-02-12
What specifically did you try?

Only one ESP by using gparted to remove boot flag on others?
Reinstall grub using Boot-Repair?
Using Acer EFI to set password & trust?

---

