---
title: "Ubuntu/Debian don't detect my Windows 7 Installation at all??"
date: 2013-08-13
forum: General Help
---

### Post by TheEliteNoob on 2013-08-13
So, I just got a new laptop (Lenovo U410 Ultrabook) the drives are in ACHI mode, and I've tried this with before uefi and legacy and it has a SSD and a HDD, now, I currently have windows 7 installed to the HDD. 

Note: HDD shows up on the ubuntu live-cd as /dev/sdb and SSD is the /dev/sda. On Windows I have the following setup shown from the disk utility:

[IMG]http://i.imgur.com/rNIbZsI.png[/IMG]


Now, On linux whenever i go to install the actual Linux OS on debian or windows and go for manual partitioning (or guided) it just sees the whole 1TB (HDD) as empty, which would overwrite windows. 

As for linux, for the boot info script i have this:

```
[COLOR=#000000]                  Boot Info Script 0.61      [1 April 2012][/COLOR]

============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System



GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2         929,523,712 1,953,521,663 1,023,997,952   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    31,266,815    31,264,768   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        4C429DF5429DE3CC                       ntfs       System Reserved
/dev/sdb2        E08EAA5D8EAA2C4A                       ntfs       
/dev/sdc1        B4AA-1FD6                              vfat       HYRULE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)
 [COLOR=#000000]            ?? = ??             boot/grub/grub.cfg                             1[/COLOR]
```

How can I make the linux OS see/and dualboot with windows 7 here? (possibly taking advantage of the ssd for speed purposes)

---

### Post by Slug71 on 2013-08-13
You should be choosing "Something Else", NOT guided.
It's the very last option with Ubuntu.

---

### Post by TheEliteNoob on 2013-08-14
> **Slug71 said:**
> You should be choosing "Something Else", NOT guided.
It's the very last option with Ubuntu.
I have, i'm trying to say that whether I do manual or guided, in either case the windows installation just seems to be totally ignored in either case.

---

### Post by oldfred on 2013-08-14
This is part of the issue.

       > GUID Partition Table detected, but does not seem to be used.

Was this a Windows 8 system installed in UEFI mode? And you installed Windows 7 in BIOS mode. Windows converts gpt to MBR, but only deletes primary gpt partition table. It leaves the backup gpt partition table and all Linux tools see both and get confused. You need to use fixparts to remove the backup gpt data.

      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Also with small SSD, is this an Ultrabook? The Intel SRT uses RAID somehow to implement the caching. You need to remove the RAID meta-data from the drives, to get grub to correctly install.
      
 sudo dmraid -E -r /dev/sda

 sudo dmraid -E -r /dev/sdb

If not using SSD, are you installing Ubuntu / (root) to SSD?

Since you have UEFI which can run in CSM/BIOS/Legacy you need to be sure to install Ubuntu in BIOS mode to be able to easily dual boot. When booting installer the UEFI/BIOS may present both. How you boot installer is how it installs, so boot in BIOS mode. If you get purple screen with accessibility icons you are in BIOS mode. If installer boots to grub menu that is UEFI mode.

Ultrabooks also have dual video. If set to nVidia mode you will need nomodeset to boot installer or after install. Otherwise you get a black screen. Some systems also need other boot parameters.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Different model but Lenovo so may be similar.

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive issues
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

### Post by crazymonkey05 on 2013-08-14
have you just tried unpluging your windows drives and then install ubuntu then plug the drives back in? or is your hdd partitioned?

---

### Post by TheEliteNoob on 2013-08-14
> **oldfred said:**
> This is part of the issue.

       

Was this a Windows 8 system installed in UEFI mode? And you installed Windows 7 in BIOS mode. Windows converts gpt to MBR, but only deletes primary gpt partition table. It leaves the backup gpt partition table and all Linux tools see both and get confused. You need to use fixparts to remove the backup gpt data.

      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Also with small SSD, is this an Ultrabook? The Intel SRT uses RAID somehow to implement the caching. You need to remove the RAID meta-data from the drives, to get grub to correctly install.
      
 sudo dmraid -E -r /dev/sda

 sudo dmraid -E -r /dev/sdb

If not using SSD, are you installing Ubuntu / (root) to SSD?

Since you have UEFI which can run in CSM/BIOS/Legacy you need to be sure to install Ubuntu in BIOS mode to be able to easily dual boot. When booting installer the UEFI/BIOS may present both. How you boot installer is how it installs, so boot in BIOS mode. If you get purple screen with accessibility icons you are in BIOS mode. If installer boots to grub menu that is UEFI mode.

Ultrabooks also have dual video. If set to nVidia mode you will need nomodeset to boot installer or after install. Otherwise you get a black screen. Some systems also need other boot parameters.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Different model but Lenovo so may be similar.

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System™ – for hard drive issues
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

I have to say, this worked perfectly, more so the part about fixpart, turns out it was the GPT table problem. For surety I also removed the dmraid thing, which may have helped as well. Now ubuntu does detect it and shows windows in the manual partition table! Thank you!

Now, if it's not too much to ask, could anyone tell me how I should partition my system so I can boot up fast with the ssd, and still have lots of space for programs?

I was thinking of putting / on my ssd, but then splitting up the 500gb on the hdd for /usr and /home? And how much space should i give /usr? 50 gb?

---

### Post by oldfred on 2013-08-14
I have never split /usr, so I cannot suggest on that.

I have a 60GB SSD drive with two 27GB installs of Ubuntu. My main working install uses 9GB of the 27GB including /home at 2GB of 9GB and most of that being .wine with Picasa. But I have all data including some of the normally hidden folders with data like Firefox & Thunderbird profiles in my data partitions on my hard drive. That way I have a fully bootable system on one drive. If hard drive fails it will give error on mounting data partitions but will boot. If part of system is on another drive then both drives always have to work. I also have other full instals of Ubuntu on each hard drive so every drive can be booted if necessary, but more as test installs of new versions.

---

