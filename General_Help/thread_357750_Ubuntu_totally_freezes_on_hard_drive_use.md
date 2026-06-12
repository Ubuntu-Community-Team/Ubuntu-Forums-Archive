---
title: "Ubuntu totally freezes on hard drive use"
date: 2007-02-10
forum: General Help
---

### Post by Havlock on 2007-02-10
OK, this problem, it's not a complete showstopper, but it does prevent me from using the system to its fullest. Whenever the system reads/writes to hdc more than minorly, the whole server locks up hard. No response from keyboard, no cursor blink, nothing, just whatever was in the frame buffer being shown on the screen. I have to hit it with a hard reset to unfreeze it. I'd like to be able to use that hard drive for Bittorrent downloads and other storage.

I installed Ubuntu 6.10 Server on my oldest PC, a Pentium II 400Mhz with 256MB RAM, with the intention of using it as a general print/scan/UPS monitor/whatever server system for my home LAN. Here's the specs for the system:

[LIST][*]Motherboard: Supermicro P6SBA[*]Chipset: Intel 440BX[*]BIOS: American Megatrends version R3.1[*]IDE Primary master: WD AC28400R ~8.5GB hard drive[*]IDE Primary slave: WD AC28400R ~8.5GB hard drive[*]IDE Secondary master: Seagate ST320014A 20GB hard drive[*]IDE Secondary slave: CD-ROM drive
[/LIST]
File system structure:
[LIST][*]hda: hda5: 255MB: /boot[*]hda: hda6: ~8.2GB: LVM partition[*]hdb: hdb5: 386MB: swap[*]hdb: hdb6: ~8.1GB: LVM partition[*]hdc: hdc5: 20GB: /media/hdc5[*]LVM: krosp: hda6 + hdb6: ~16.3GB: / (root)
[/LIST]
The motherboard does have ACPI, but I have to put "acpi=force" in the GRUB boot entry to use it.

I set the file system up during the install of Ubuntu and it didn't cause any troubles. It wasn't until I installed torrentflux and tried using the Seagate 20GB for download storage that things froze up. Tried removing and recreating the partition on the drive, but it would always hang on ext2 or ext3 format after writing the inodes to the partition. If I made the partition on the drive 500MB, it could format that, but a 1000MB one it balked at and locked up again.

Right now I've commented out the fstab entry for the hdc Seagate drive, and things are running just fine. I'd just like that extra storage so I can offload my 24/7 bittorrents from my main machine to the server and not have to leave both systems up all the time. Any support would be really appreciated.

---

### Post by Jussi Kukkonen on 2007-02-10
Old BIOSes have strange restrictions on hard drive sizes (mostly related to number of cylinders). I've never heard of a partly working disk in a situation like that. so it's probably not related -- you might want to do some searches on that anyway.

[http://www.storagereview.com/guide2000/ref/hdd/bios/size.html](http://www.storagereview.com/guide2000/ref/hdd/bios/size.html)

---

### Post by Havlock on 2007-02-10
Well, I read the information on int13h, then poked my drives with "hdparm -I" and compared the results. It looks like the two WD drives have "CHS current addressable sectors" equal to "LBA user addressable sectors," so they're both using the old int13h method to address the drives. For the Seagate "hdparm -I" returned that the drive's "LBA user addressable sectors" is larger than its "CHS current addressable sectors," so it's trying to use int13h extensions to address the drive. I'll have to see if I can dig up some more information on my motherboard's BIOS and if I can enable int13h extensions or not.

---

### Post by Havlock on 2007-02-10
Downloaded SeaTools, the Seagate disk diagnostics utility, and made a bootable diagnostics floppy. I then ran through all the tests available for my 20GB Seagate drive, followed by zeroing out the drive. It passed through all the tests and the zeroing, so I don't know what to think about the BIOS support for int 13h extensions, since it could read and write out to sectors that it shouldn't be able to with just LBA + int 13h.

I also found some information on GRUB that says that the AMIBIOS in the Supermicro P6SBA motherboard doesn't correctly report something or other for int 13h, AH=41h. If that's the case, then I'm outta luck. I'm thinking that I'll just bypass the whole mess and get a PCI PATA interface card. Unless there's some magic GRUB option or something that'll fix this it's just not worth the headache of fighting with it.

---

