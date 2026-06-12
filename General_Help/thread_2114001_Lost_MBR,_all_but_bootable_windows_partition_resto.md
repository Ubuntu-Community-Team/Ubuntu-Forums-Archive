---
title: "Lost MBR, all but bootable windows partition restored."
date: 2013-02-08
forum: General Help
---

### Post by narnie on 2013-02-08
Hello,

Today my MBR was borked. I used SystemRescueCD and testdisk/fixpart to get all my partitions working except the bootable windows partition.

I can't mount the problem partition even though I initially could.

I will post info below. Please tell me what other info one might need to help me recover. I don't have recovery CDs/DVDs.

Initially I thought all was well since everything mounted so I booted into Linux. All great. Booted into Windows, and it wouldn't boot. I then ran update-grub thinking it just needed to find the windows boot partition. Sadly, I was wrong and sadly, I didn't backup the grub.cfg before doing that (hindsight 20/20?)

Here is my fdisk -l info:

```
dell-desktop mnt # fdisk -l /dev/sda

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17287e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80321       40129+   6  FAT16
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30801920   212738032    90968056+   7  HPFS/NTFS/exFAT
/dev/sda4       212748857  1465144048   626197596    f  W95 Ext'd (LBA)
/dev/sda5       212748858   422461304   104856223+   7  HPFS/NTFS/exFAT
/dev/sda6       422461368   527317559    52428096   83  Linux
/dev/sda7       527317623  1452565166   462623772   83  Linux
```

Here it is in cylinders:

```
dell-desktop mnt # fdisk -u=cylinders -l /dev/sda

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17287e8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40129+   6  FAT16
/dev/sda2               6        1918    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *        1918       13243    90968056+   7  HPFS/NTFS/exFAT
/dev/sda4           13244       91201   626197596    f  W95 Ext'd (LBA)
/dev/sda5           13244       26297   104856223+   7  HPFS/NTFS/exFAT
/dev/sda6           26298       32824    52428096   83  Linux
/dev/sda7           32825       90418   462623772   83  Linux
```

sda1 is DellUtility
sda2 is a Recovery partition (that I never could get to work in the first place to make CD/DVD disks or to even boot into).
sda3 is the main booting Windows OS
sda4 is an extended parition
sda5 is Windows User data and some Program data
sda6 is Linux OS
sda7 is Linux Home

my swap won't work right either so I tried deleting it, but gparted won't let me add it back even using SystemRestoreCD live.

Here is the error I get when trying to mount:

```
ntfs_mst_post_read_fixup_warn: magic: 0x6eaca328  size: 1024   usa_ofs: 1572  usa_count: 461: Invalid argument
Record 0 has no FILE magic (0x6eaca328)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```

I would be extremely grateful for any help.

Thanks,
Narnie

---

### Post by jannk on 2013-02-08
If i understand correctly you want to boot into win yeah?

If so try this [boot repair]("http://fixitwizkid.com/threads/boot-repair-in-ubuntu-fixed-my-windows-7-master-boot-record.9718/"). Done it myself and it works in ubuntu.

---

### Post by Mark Phelps on 2013-02-09
IF boot-repair doesn't work, you could be in a real bind.

The error message means you need to run CHKDSK on the NTFS partition and there is no equivalent for that in Linux; instead, you will have to hook this drive up to a Windows PC and run chkdsk from there.

---

### Post by oldfred on 2013-02-09
I have run chkdsk from a Windows 7 repair flash drive on my XP. But only the current version Windows repair will fully repair that same version of Windows, so best to have same version. 

If you have access to another PC, or a friend with the same version.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
       How to restore the Ubuntu/XP/Vista/7 bootloader Also see link to repairs
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by narnie on 2013-02-09
> **jannk said:**
> If i understand correctly you want to boot into win yeah?

If so try this [boot repair]("http://fixitwizkid.com/threads/boot-repair-in-ubuntu-fixed-my-windows-7-master-boot-record.9718/"). Done it myself and it works in ubuntu.

Sadly, it didn't work for me.

---

### Post by narnie on 2013-02-09
> **Mark Phelps said:**
> IF boot-repair doesn't work, you could be in a real bind.

The error message means you need to run CHKDSK on the NTFS partition and there is no equivalent for that in Linux; instead, you will have to hook this drive up to a Windows PC and run chkdsk from there.

I downloaded a Windows environment and ran chkdsk /f. It couldn't do anything with the partition.

---

