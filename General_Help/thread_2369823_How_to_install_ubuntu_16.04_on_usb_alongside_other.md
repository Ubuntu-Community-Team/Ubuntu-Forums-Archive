---
title: "How to install ubuntu 16.04 on usb alongside other stuff"
date: 2017-08-27
forum: General Help
---

### Post by xxfoofyxx on 2017-08-27
I have a (legit) 256gb USB flash drive and i would like to install ubuntu 16.04 alongside a partition used for coding and whatnot (must be NTFS for second partition)

---

### Post by oldfred on 2017-08-27
I think Windows still only reads the first partition on a USB flash drive, but that is not an issue, just how you must partition it. Then add the Ubuntu partition(s).

UEFI or BIOS full install?
Be sure to only use a USB3 flash drive, which will be somewhat slow loading & writing. Change some settings to reduce writes.

I have done both, but BIOS is a bit easier as during install you specify boot loader to sdb (or whatever flash drive is). 
With UEFI if offers that same choice, but only installs boot files into the ESP - efi system partition seen as sda. 
You then have to manually copy from hard drive's ESP to ESP on flash drive to /EFI/ubuntu to /EFI/ubuntu on flash drive & then copy again to /EFI/Boot. Then rename shimx64.efi to bootx64.efi in /EFI/Boot on flash drive. That is because UEFI only boots from /EFI/Boot/bootx64.efi and Ubuntu's shim/grub is hard coded to find more boot files in /EFI/ubuntu.

 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

I only use gpt whether UEFI or BIOS boot. And on my larger flash drives I usually put both the ESP & bios_grub as first two partitions.

You would want a NTFS partition first.
My partitions on a 64GB flash drive:

```
Disk /dev/sdc: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub
 3      213MB   22.9GB  22.6GB  ext4         system
 4      22.9GB  61.9GB  39.1GB  ext4         data

```

---

### Post by C.S.Cameron on 2017-08-28
> **oldfred said:**
> I think Windows still only reads the first partition on a USB flash drive,

Windows 10 now seems to be able to see multiple partitions on a flash drive as long as they are FAT32 or NTFS.

I still make the first partition either NTFS, (larger drives) or FAT32, (smaller drives), so that it can be seen by older Windows versions.

---

