---
title: "Currently running Ubuntu, but need Windows dual boot"
date: 2018-06-04
forum: General Help
---

### Post by zulubanshee on 2018-06-04
I'm running the current version of Ubuntu, but I need to create a Windows 10 dual boot. 

All the tutorials I've seen are with Ubuntu being the second OS. 

I'm preparing a Windows boot as we speak. 

[FONT=Verdana]Is there anything special I need to do/know before proceeding? [/FONT]

---

### Post by Autodave on 2018-06-04
I have never heard of anyone successfully installing Windows after having Ubuntu already on the machine. Windows has to be on there first.

---

### Post by zulubanshee on 2018-06-04
> **Autodave said:**
> I have never heard of anyone successfully installing Windows after having Ubuntu already on the machine. Windows has to be on there first.

For clarity: you say "successfully." Does that mean you have heard of people trying but failing?

Also, is there a particular reason Windows has to be the "parent" OS.

---

### Post by Impavidus on 2018-06-04
Windows wouldn't be the parent, it would be the elder sibling. They are installed side-by-side as equals. The problem is that the Windows installer has the unfortunate habit of damaging Linux.

If you have a second hard drive in that computer, you can disconnect the Linux drive, install Windows on the second drive, then reconnect the Linux drive, move the Linux drive to top in boot order and update grub to allow the Linux boot loader to boot Windows. If your computer is powerful enough and you don't want to run anything heavy (in particular graphics) on the Windows side, you could try Windows in a virtual machine. But for a dual boot on a single drive, it's best to install Windows first.

---

### Post by SeijiSensei on 2018-06-04
Another option is [VirtualBox]("https://www.virtualbox.org/").  It's what I use to run the occasional Windows app like Microsoft Access or my tax software.  VB won't let Windows talk directly to the video hardware, though, so if you want to use Windows for gaming, this isn't an alternative.

---

### Post by nlee2 on 2018-06-04
> **zulubanshee said:**
> I'm running the current version of Ubuntu, but I need to create a Windows 10 dual boot. 

All the tutorials I've seen are with Ubuntu being the second OS. 

I'm preparing a Windows boot as we speak. 

[FONT=Verdana]Is there anything special I need to do/know before proceeding? [/FONT]

Would be interesting to know what is the current partition layout.

---

### Post by oldfred on 2018-06-04
Makes a big difference if UEFI or BIOS. And if drive is gpt or MBR currently.

Windows only boots from MBR(msdos) partitioned drives with BIOS boot mode. And it must boot from a primary NTFS partition with boot flag. It also has a bug where it may erase a Linux logical partition when it updates partition table. Partition is still there, just not in partition table. 

Windows only boots from gpt(GUID) partition tables with UEFI. It will set itself as default boot (which grub also does), but has fast start up/hibernation which must be turned off if dual booting.

Post this:
sudo parted -l

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by monkeybrain20122 on 2018-06-04
+1 for VB. You never tell us what you need Windows for, VB may be the best option if it fulfills your need. Dualboot with Win10 is tricky to setup and hard to maintain even if you started off with just Windows.

---

### Post by Frogs Hair on 2018-06-04
> **zulubanshee said:**
> For clarity: you say "successfully." Does that mean you have heard of people trying but failing?

Also, is there a particular reason Windows has to be the "parent" OS.

I have two dual boots and Windows first has always been successful. I've not tried the other way based on recommendations not to.

---

### Post by zulubanshee on 2018-06-04
VirtualBox isn't an option. It literally grinds my machine to a halt--even when I'm not running any programs. Same for VMWare. 

I need the dual boot for Photoshop and ABBYY FineReader, that's pretty much it. I can run Photoshop on Wine, but I can't use 3D effects because my card isn't supported. It's true that it's not, but it always worked on my dedicated Windows installation. FineReader does not work in any way shape or form with Wine. 

I have another hard drive, what if I put Windows on that. Or does that not make a difference.
EDIT: I can see now that it does not make a difference.

---

### Post by monkeybrain20122 on 2018-06-04
> **zulubanshee said:**
> VirtualBox isn't an option. It literally grinds my machine to a halt--even when I'm not running any programs. Same for VMWare. 



Well if your machine is that weak Windows 10 is not going to work great. Maybe try Win7 or even god forbids XP if you have an old disk lying around (just cut off internet access) It is a lot easier to set up a dualboot with Win < 8 anyway.

---

### Post by zulubanshee on 2018-06-04
> **oldfred said:**
> Makes a big difference if UEFI or BIOS. And if drive is gpt or MBR currently.

Windows only boots from MBR(msdos) partitioned drives with BIOS boot mode. And it must boot from a primary NTFS partition with boot flag. It also has a bug where it may erase a Linux logical partition when it updates partition table. Partition is still there, just not in partition table. 

Windows only boots from gpt(GUID) partition tables with UEFI. It will set itself as default boot (which grub also does), but has fast start up/hibernation which must be turned off if dual booting.

Post this:
sudo parted -l

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

```
Model: ATA TOSHIBA DT01ACA2 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1305MB  768MB   ext4
 3      1305MB  2000GB  1999GB




Model: ASMT ASM1156-PM (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   4001GB  4001GB  ntfs         Basic data partition          msftdata




Model: ASMT ASM1156-PM (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  420MB   419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   735MB   315MB   fat32        EFI system partition          boot, esp
 3      735MB   869MB   134MB                Microsoft reserved partition  msftres
 4      869MB   983GB   982GB   ntfs         Basic data partition          msftdata
 5      983GB   983GB   472MB   ntfs                                       hidden, diag
 6      983GB   1000GB  16.8GB  ntfs         Basic data partition          hidden, diag




Model: WDC WD10 EZEX-00BN5A0 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  991GB   991GB   primary   ntfs            boot
 2      991GB   1000GB  9287MB  extended
 5      991GB   1000GB  9287MB  logical   linux-swap(v1)




Model: WDC WD20 EZRX-00D8PB0 (scsi)
Disk /dev/sde: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 1998GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  1998GB  1998GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 1023MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  1023MB  1023MB  linux-swap(v1)




Error: /dev/mapper/sda3_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/sda3_crypt: 1999GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: Slimtype DVD A DA8AESH (scsi)                                      
Disk /dev/sr0: 1785MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 


Model: SanDisk Cruzer Fit (scsi)
Disk /dev/sdg: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.0GB  16.0GB  primary  fat32        boot, lba




Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdh: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      4194kB  15.7GB  15.7GB  primary  fat32        lba
```

---

### Post by oldfred on 2018-06-04
You have gpt partitioning and Windows will need to be in UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.

Often better to disconnect other drives, so Windows installs just to the one drive.  And it will make itself first in boot order.

---

### Post by zulubanshee on 2018-06-05
^ OK thanks for your help. I'm only somewhat familiar with this stuff so it's a lot of reading to make sure I get it right. 

There will be more questions in coming days, so don't leave town. :lolflag:

---

### Post by oldrocker99 on 2018-06-05
What is the reason you "need" to use the malware magnet that is Windows? Aside from running certain Windows programs, i have not yet found a task I've been unable to accomplish using Linux, and wine to run the few Windows games I want to run. This is a partial list: [https://www.tecmint.com/windows-alternatives-for-linux/](https://www.tecmint.com/windows-alternatives-for-linux/)

You should also see what PlayOnLinux, a great frontend for wine, which will run a raft of programs, not just games:
```
sudo apt install playonlinux
```

Good luck!

---

### Post by QIII on 2018-06-05
The user's reasons are their own.  That is enough for us to know.

---

### Post by zulubanshee on 2018-06-05
^^Really I need Photoshop. That's the only thing I can't compromise on. GIMP is good for everyday stuff, but Photoshop does a number of things GIMP can't.

---

