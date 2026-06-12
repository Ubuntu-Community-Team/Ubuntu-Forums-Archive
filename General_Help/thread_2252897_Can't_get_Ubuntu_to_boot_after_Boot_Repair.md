---
title: "Can't get Ubuntu to boot after Boot Repair"
date: 2014-11-15
forum: General Help
---

### Post by Seamless in Northampton on 2014-11-15
I just re-installed Windows XP (only in order to run a game), and then set out to repair Grub. I've done it manually and I've used boot repair. Yet still I boot up and only get Windows. Holding shift or pushing esc do nothing. I'm at a loss. I have Windows on sda, Ubuntu on sdb-- wondering if the machine is stuck on Windows because that drive is set to boot first, but in the BIOS, I see no way to change the boot device order. Not at all sure where to go from here. Seems like Grub is installed properly, so why won't it boot?

Here's the URL from Boot Repair:  [http://paste.ubuntu.com/9028401](http://paste.ubuntu.com/9028401)   (and you get to see my over-partitioned madness, complete with old, broken 10.04 install...)

Any help would be much appreciated-- I sort of know what I'm doing, but sometimes I miss simple stuff!

---

### Post by grahammechanical on 2014-11-15
> You can now reboot your computer.
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sdb [COLOR=#666666]([/COLOR]500GB[COLOR=#666666])[/COLOR] disk!

That is what you need to do. I would be very surprised if the BIOS did not have an option to change the boot order. And yet Boot Repair did install Grub into the MBR of the three hard disks so it should not matter which one has boot priority and you should be getting a Boot menu showing Ubuntu 12.04, Ubuntu 10.04, Windows XP and maybe another Windows.

> Reinstall the GRUB of sdb2 into the MBR of sdc
grub-install /dev/sdc: Installation finished. No error reported.

> Reinstall the GRUB of sdb2 into the MBR of sdb
grub-install /dev/sdb: Installation finished. No error reported.

But then there  is this

> Reinstall the GRUB of sdb2 into the MBR of sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: error: embedding is not possible, but this is required [COLOR=#AA22FF]**for **[/COLOR]cross-disk install.

What kind of a hard disk is sda? Is it very old? Try swapping the disks around on the motherboard connectors so that the XP disk is not sda. Linux gives each disk a unique identifier which is a long string of alpha-numeric characters and it is that unique identifier that Grub uses to locate it configuration file and the OS selected for loading. So, swapping the drives around should break Grub.

Regards.

---

### Post by oldfred on 2014-11-15
So your BIOS does not allow changing boot order?
If that is the case, you have to install grub to sda.
I normally suggest keeping Windows boot loader on Windows drive and grub boot loader on Ubuntu drive and set BISO to boot Ubuntu drive.

You still show Windows boot loader in sda. If that is only bootable device then you need to install grub to sda. Or if you can boot from flash drive you even could install grub to a flash drive.
Boot-Repairs auto fix which I normally do not suggest for multiple drives as you may want different boot loaders in each drive will install grub to the MBR of every drive.

But this may be blocking install of grub.

> Extended partition linking to another extended partition.
Empty Partition.

The error is not quite what it says. You have sda3 inside the extended partition. But sda1 thru sda4 must be primary partitions and all logical partitions must start with sda5.
So either extended partition was changed to include sda3 incorrectly or sda3 got renumbers?

You should be able to fix that with fixparts.
       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by Seamless in Northampton on 2014-11-15
Thank you, thank you. I will get to work and see how it goes.

Oh, and sda is an old SATA drive, so old I can't remember exactly what the specs are.

---

### Post by oldfred on 2014-11-15
If it is Northampton in England, I have my Grandmother's nursing school diploma framed on the wall. It says 1910 Northampton General Hospital.

---

### Post by Seamless in Northampton on 2014-11-15
I swapped sda and sdb on the motherboard-- 100% success! Still can't understand why there's no way to switch the boot drive via BIOS, but hey, whatever works. Now I can fix the weird partition issues and I'm back in business.

Many thanks to both of you for the help.

Though I'd rather it were Northampton, England, it's Northampton, Massachusetts. Which ain't half-bad either! Cool that you have that piece of your history.

---

### Post by oldfred on 2014-11-15
Is system very old IDE/PATA drives?
If a bit newer it could be that either you have an incorrect cable or jumpers. You have to have a 80 conductor cable for cable select to work and then drive jumpered for cable select.
But if old system, drives are just set for primary master & slave and jumper on hard drive controls which drive will boot.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

