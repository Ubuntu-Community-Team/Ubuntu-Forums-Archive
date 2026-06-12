---
title: "GRUB not showing, booting straight to Windows"
date: 2016-03-13
forum: General Help
---

### Post by Desetude on 2016-03-13
I have just attempted to dual boot my windows 10 and ubuntu 15.10 - for the first time. But when ever I turn on my PC, it boots straight to Windows even if I am holding shift.  I think it may be a problem with my disk as I wanted ubuntu to be installed onto my SSD but it looks like a bit of it was installed on to my harddrive (there's a folder on it called efi). Here's the boot info summary: [http://paste.ubuntu.com/15371061/](http://paste.ubuntu.com/15371061/)
I can boot to ubuntu also, as I can use the USB stick I used to install ubuntu to bring up grub.

---

### Post by Bucky Ball on 2016-03-13
Welcome. Try setting the machine to boot from sdb if you haven't already (the second hard drive). You'll need to enter the BIOS at boot and change the boot order (it won't be listed as sdb in there so you'll need to figure out which it is). You might be able to do it from a device list at boot. To get there press  F12 or some other key for you machine at the splash screen at boot.

---

### Post by Desetude on 2016-03-13
> **Bucky Ball said:**
> Welcome. Try setting the machine to boot from sdb if you haven't already (the second hard drive). You'll need to enter the BIOS at boot and change the boot order (it won't be listed as sdb in there so you'll need to figure out which it is). You might be able to do it from a device list at boot. To get there press F12 or some other key for you machine at the splash screen at boot.

But I'm wanting to boot from my SSD as that is where my Windows is, it will boot faster from it and I only want to use my second hard drive for games and other bulk data. I will try to see if that works though.

EDIT: That was strange.. when I booted from secondary hard drive, an old looking interface came up asking if I wanted to install ubuntu or try it out. Went on try it out and it didn't have any of my settings on it.

EDIT #2: Would it work if I just moved the efi on the HDD to the SSD?

---

### Post by fantab on 2016-03-13
> **Desetude said:**
> I have just attempted to dual boot my windows 10 and ubuntu 15.10 - for the first time. But when ever I turn on my PC, it boots straight to Windows ......
I can boot to ubuntu also, as I can use the USB stick I used to install ubuntu to bring up grub.

```
 parted -l:

Model: ATA WDC WD10EZEX-08M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  1000GB  1000GB  ntfs         Basic data partition  msftdata


Model: ATA SanDisk SDSSDA24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  473MB  472MB   ntfs            Basic data partition          hidden, diag
**[COLOR=#ff0000]2      473MB   578MB  105MB   fat32           EFI system partition          boot, esp[/COLOR]**
3      578MB   595MB  16.8MB                  Microsoft reserved partition  msftres
4      595MB   197GB  197GB   ntfs            Basic data partition          msftdata
5      197GB   223GB  25.8GB  ext4
6      223GB   240GB  17.1GB  linux-swap(v1)


Model: USB 2.0 Flash Disk (scsi)
Disk /dev/sdc: 2022MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system  Flags
1      0.00B  2022MB  2022MB  fat32
```

You have an ESP/ EFI System Partition on SanDisk, /dev/sdb2... and it appears you have ubuntu boot files in that partition as well so the problem could be with your default boot device... it sould be set to boot /dev/sdb or SanDisk first...
It is probably set to boot USB first...

Let us know how it goes..

---

### Post by oldfred on 2016-03-13
Generally Windows system is sda, and your data drives are sdb, sdc etc.

When you installed SSD, did you put it in a lower SATA port or a higher SATA port than hard drive?
And best to have boot drive in SATA0, and use each port in order. BIOS reports drives in order to operating system.
I had skipped a port and my sdf flash drive would change to sdb (skipped port?) and every other drive moved up a letter.

---

