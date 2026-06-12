---
title: "Fix GUID partition Table Header signature is wrong"
date: 2019-02-01
forum: General Help
---

### Post by Briga on 2019-02-01
Hi, every time I update grub (like today) I get an error like in the title of this post:

```
Setting up grub-efi-amd64-signed (1.93.11+2.02-2ubuntu8.10) ...
Installing for x86_64-efi platform.
GUID Partition Table Header signature is wrong: be5608740128e852 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: be5608740128e852 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: be5608740128e852 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
Installation finished. No error reported.
```

It seems not an issue, because all works fine, and googling it yield no results, only posts on how to fix grub when not working. What is that error? Is there a way to fix it anyway?

---

### Post by oldfred on 2019-02-01
What does this show, if sda.
sudo gdisk -l /dev/sda

You usually can run gdisk and have it update gpt primary, gpt secondary & MBR protective partition tables.

 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

---

### Post by Briga on 2019-02-05
> **oldfred said:**
> What does this show, if sda.
sudo gdisk -l /dev/sda


Never used gdisk before (other tools only) and it picked up an error immediately:

```
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 488397168 sectors, 232.9 GiB
Model: Samsung SSD 840 
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 7F1F4BAD-4FBD-4FB8-AB46-79E89CF074A7
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 10780 sectors (5.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          976656   475.9 MiB   EF00  EFI System
   5          978944          980991   1024.0 KiB  8300  Linux filesystem
   6          983040        40042495   18.6 GiB    8300  Linux filesystem
   7        40044544       484491263   211.9 GiB   8300  Linux filesystem
   8       484493312       488396799   1.9 GiB     8200  Linux swap

```

I am missing the GPT apparently.

> **oldfred said:**
> You usually can run gdisk and have it update gpt primary, gpt secondary & MBR protective partition tables.

 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

I read about it and it seems a little risky ... I think I need to have the time to do it.... I am not sure I want to go through it now since it's not a real problem... but could lead into, plus I need to find my live disk somewhere :)

Thanks for the help, you really pointed me in the right direction, much appreciated.

---

### Post by oldfred on 2019-02-05
UEFI's standard is gpt partitioning, but you have MBR(msdos).
And it looks like you converted your gpt to MBR, somehow.
Windows only installs in UEFI boot mode to gpt partitioning, but Ubuntu will let you use MBR.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface

      [/URL]
 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 
    [URL="http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface"]
[/URL]

---

