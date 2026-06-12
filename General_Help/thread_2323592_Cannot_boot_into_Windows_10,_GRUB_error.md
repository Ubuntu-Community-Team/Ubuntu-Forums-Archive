---
title: "Cannot boot into Windows 10, GRUB error"
date: 2016-05-06
forum: General Help
---

### Post by Juub on 2016-05-06
Hello everyone, first post here. I have come into some sort of issue after I installed Linux on a USB Drive.

1. I created a bootable Ubuntu 15.10 on an external USB stick.
2. I then used the stick to install Linux onto my external Seagate HDD
3. During the install, by default, the bootloader was selected to be installed on my SSD which also contains Windows 10
4. Install completed but since then whenever I boot to my internal SSD which contains Windows 10 I get the following error

error: no such device "several numbers" grub rescue>

I looked around online on about 10 different websites and nothing worked. I attempted to delete any traces of Linux from my internal and external drives, unplugged every devices, reset my CMOS and I keep getting that error. I attempted to repair Windows 10 using the Windows 8 Install DVD. I have attempted to erase the Linux volumes using command prompt on Windows but nothing does it. I keep getting that error over and over again and there is simply no way for me to boot into Windows 10. It seems grub is inside my UEFI or something as it messes up to boot order and prevents Windows 10 from booting.

Any help would be greatly appreciated. Been fighting with this for about 3 hours.

---

### Post by oldfred on 2016-05-06
If system is UEFI, you should be able to use UEFI menu or one time boot key like f10 or f12 check your manual to choose Windows.
But if you turned on legacy/CSM/BIOS and are booting in BIOS mode Windows will not boot if it is UEFI.

What brand/model system?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

Install in UEFI mode to external drive requires a bit of extra effort. You have to partition in advance so you have the ESP on external drive. Grub in UEFI mode only installs to sda. And then you have to copy /EFI/ubuntu folder to ESP on external and create /EFI/Boot folder with a copy of shimx64.efi renamed to bootx64.efi. External drives only boot in UEFI mode from /EFI/Boot/bootx64.efi in an ESP - efi system partiiton. Both Windows installer & Ubuntu installer use that same convention, but each has its own bootx64.efi.

---

### Post by Juub on 2016-05-06
> **oldfred said:**
> If system is UEFI, you should be able to use UEFI menu or one time boot key like f10 or f12 check your manual to choose Windows.
But if you turned on legacy/CSM/BIOS and are booting in BIOS mode Windows will not boot if it is UEFI.

What brand/model system?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

Install in UEFI mode to external drive requires a bit of extra effort. You have to partition in advance so you have the ESP on external drive. Grub in UEFI mode only installs to sda. And then you have to copy /EFI/ubuntu folder to ESP on external and create /EFI/Boot folder with a copy of shimx64.efi renamed to bootx64.efi. External drives only boot in UEFI mode from /EFI/Boot/bootx64.efi in an ESP - efi system partiiton. Both Windows installer & Ubuntu installer use that same convention, but each has its own bootx64.efi.

Thanks a lot for your reply.

I can choose Windows 10 in the boot menu but still get the same error.

My motherboard is an Asus Sabretooth Mark II Z97.

Exactly, it did install to sda but the default location was my internal drive containing Windows 10 and I think it screwed up the boot loader.

I used Boot Repair and still nothing. This is the log file I got. Funny because I can boot into Ubuntu on my USB Flash Drive easily.

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ec7c2e84-77a1-45d7-ad1d-60853dc605fe root hd3,gpt4 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03 2014-10-06................................................2....0............A20 gate n
    Boot sector info:  Syslinux looks at sector 10846322 of /dev/sde1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   975,849,471   975,130,624   7 NTFS / exFAT / HPFS
/dev/sda3         975,849,472   976,771,071       921,600  27 Hidden NTFS (Recovery Environment)


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdc1                    34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdc2               264,192   937,701,375   937,437,184 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 2.7 TiB, 3000592977920 bytes, 732566645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sde _____________________________________________________________________
Disk /dev/sde: 115.7 GiB, 124218507264 bytes, 242614272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   242,614,271   242,612,224   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       984ed093-07a0-4546-bfd3-5346c7535dc4   ext2       
/dev/loop1                                              squashfs   
/dev/sda1        A27A81667A8137D5                       ntfs       
/dev/sda2        4628599728598739                       ntfs       
/dev/sda3        AE0E886D0E882FFF                       ntfs       
/dev/sdb1        C68463C48463B599                       ntfs       Games
/dev/sdc1                                                          
/dev/sdc2        8832E81532E809D0                       ntfs       Games
/dev/sde1        0C17-0C68                              vfat       MYLINUXLIVE
/dev/sr0         2013-08-22-12-28-08-00                 udf        IRM_CCSA_X64FRE_EN-US_DV5

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  6 23:44 ata-KINGSTON_SV300S37A480G_50026B725C055CDF -> ../../sdc
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-KINGSTON_SV300S37A480G_50026B725C055CDF-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-KINGSTON_SV300S37A480G_50026B725C055CDF-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 May  6 23:44 ata-ST3000DM001-1E6166_Z1F2LBTS -> ../../sdd
lrwxrwxrwx 1 root root  9 May  6 23:44 ata-Samsung_SSD_850_EVO_500GB_S21HNSAG119885J -> ../../sda
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-Samsung_SSD_850_EVO_500GB_S21HNSAG119885J-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-Samsung_SSD_850_EVO_500GB_S21HNSAG119885J-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-Samsung_SSD_850_EVO_500GB_S21HNSAG119885J-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 May  6 23:44 ata-WDC_WD5002AALX-00J37A0_WD-WMAYUJ588392 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  6 23:44 ata-WDC_WD5002AALX-00J37A0_WD-WMAYUJ588392-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  7  2016 usb-HP_DVD-ROM_rm475e_201100000000000042D-0:0 -> ../../sr0
lrwxrwxrwx 1 root root  9 May  6 23:44 usb-SanDisk_Ultra_Fit_4C530146150911115333-0:0 -> ../../sde
lrwxrwxrwx 1 root root 10 May  6 23:44 usb-SanDisk_Ultra_Fit_4C530146150911115333-0:0-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 May  6 23:44 wwn-0x5000c50050165c12 -> ../../sdd
lrwxrwxrwx 1 root root  9 May  6 23:44 wwn-0x50014ee1af447179 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x50014ee1af447179-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  6 23:44 wwn-0x5002538da013be41 -> ../../sda
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x5002538da013be41-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x5002538da013be41-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x5002538da013be41-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 May  6 23:44 wwn-0x50026b725c055cdf -> ../../sdc
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x50026b725c055cdf-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 May  6 23:44 wwn-0x50026b725c055cdf-part2 -> ../../sdc2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP \90dition familiale" /FASTDETECT
--------------------------------------------------------------------------------

========================= sde1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
# search path for the c32 support libraries (libcom32, libutil etc.)
path 
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             ldlinux.c32                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/ldlinux.c32                           1
            ?? = ??             syslinux/libcom32.c32                          1
            ?? = ??             syslinux/libutil.c32                           1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 ldlinux.c32                        :  not a COM32/COM32R module
 syslinux/chain.c32                 :  not a COM32/COM32R module
 syslinux/gfxboot.c32               :  not a COM32/COM32R module
 syslinux/ldlinux.c32               :  not a COM32/COM32R module
 syslinux/libcom32.c32              :  not a COM32/COM32R module
 syslinux/libutil.c32               :  not a COM32/COM32R module
 syslinux/vesamenu.c32              :  not a COM32/COM32R module

=============================== StdErr Messages: ===============================

ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
File descriptor 9 (/proc/15279/mounts) leaked on lvs invocation. Parent PID 24280: bash
File descriptor 63 (pipe:[112739]) leaked on lvs invocation. Parent PID 24280: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-05-06__23h43 ===================
boot-repair version : 4ppa37
boot-sav version : 4ppa37
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa37
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
ERROR: unsupported sector size 4096 on /dev/sdd.
Error: /dev/sdd: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Error: /dev/sdd: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label
boot-repair is executed in live-session (Ubuntu 15.10, wily, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys locale=us_us  persistent noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash -- maybe-ubiquity
ls: cannot access /home/usr/.config: No such file or directory
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2

=================== os-prober:
/dev/sdb1:Windows 8 (loader):Windows:chain

=================== blkid:
/dev/sda1: UUID="A27A81667A8137D5" TYPE="ntfs" PARTUUID="0a332f11-01"
/dev/sda2: UUID="4628599728598739" TYPE="ntfs" PARTUUID="0a332f11-02"
/dev/sda3: UUID="AE0E886D0E882FFF" TYPE="ntfs" PARTUUID="0a332f11-03"
/dev/sdb1: LABEL="Games" UUID="C68463C48463B599" TYPE="ntfs" PARTUUID="ab9bfef3-01"
/dev/sdc2: LABEL="Games" UUID="8832E81532E809D0" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="89d93967-49ce-4183-b105-6cf87a73c7d9"
/dev/sde1: LABEL="MYLINUXLIVE" UUID="0C17-0C68" TYPE="vfat" PARTUUID="000820b0-01"
/dev/sr0: UUID="2013-08-22-12-28-08-00" LABEL="IRM_CCSA_X64FRE_EN-US_DV5" TYPE="udf"
/dev/loop0: UUID="984ed093-07a0-4546-bfd3-5346c7535dc4" TYPE="ext2"
/dev/loop1: TYPE="squashfs"
/dev/sdc1: PARTLABEL="Microsoft reserved partition" PARTUUID="06c05adf-e2ab-418f-89b0-1266df37ca38"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdc2    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc2.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes


=================== parted -l:

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
1      1049kB  368MB  367MB  primary  ntfs         boot
2      368MB   500GB  499GB  primary  ntfs
3      500GB   500GB  472MB  primary  ntfs         diag


Model: ATA WDC WD5002AALX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sdc: 480GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name                          Flags
1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres
2      135MB   480GB  480GB  ntfs         Basic data partition          msftdata


Model: Seagate Expansion Desk (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 4096B/4096B
Partition Table: unknown
Disk Flags:

Model: SanDisk Ultra Fit (scsi)
Disk /dev/sde: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
1      1049kB  124GB  124GB  primary  fat32        boot, lba


Model: HP DVD-ROM rm475e (scsi)
Disk /dev/sr0: 3899MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA Samsung SSD 850:;
1:1049kB:368MB:367MB:ntfs::boot;
2:368MB:500GB:499GB:ntfs::;
3:500GB:500GB:472MB:ntfs::diag;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA WDC WD5002AALX-0:;
1:1049kB:500GB:500GB:ntfs::boot;

BYT;
/dev/sdc:480GB:scsi:512:512:gpt:ATA KINGSTON SV300S3:;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:480GB:480GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdd:3001GB:scsi:4096:4096:unknown:Seagate Expansion Desk:;

BYT;
/dev/sde:124GB:scsi:512:512:msdos:SanDisk Ultra Fit:;
1:1049kB:124GB:124GB:fat32::boot, lba;

BYT;
/dev/sr0:3899MB:scsi:2048:2048:unknown:HP DVD-ROM rm475e:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          465.8G
sda1  part ntfs       350M
sda2  part ntfs       465G
sda3  part ntfs       450M
sdb   disk          465.8G
sdb1  part ntfs     465.8G Games
sdc   disk          447.1G
sdc1  part            128M
sdc2  part ntfs       447G Games
sdd   disk            2.7T
sde   disk          115.7G
sde1  part vfat     115.7G MYLINUXLIVE
sr0   rom  udf        3.6G IRM_CCSA_X64FRE_EN-US_DV5
loop0 loop ext2         4G
loop1 loop squashfs   1.1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0         /mnt/boot-sav/sda2
sda3     0  0  0         /mnt/boot-sav/sda3
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdc      0  0  0 running
sdc1     0  0  0
sdc2     0  0  0         /mnt/boot-sav/sdc2
sdd      1  0  0 running
sde      1  0  1 running
sde1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  0  0
loop1    1  0  0         /rofs


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8257228k,nr_inodes=177583,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1653944k,mode=755)
/dev/sde1 on /cdrom type vfat (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=21,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1653944k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc2 on /mnt/boot-sav/sdc2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-19 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg log mapper mcelog mei0 mem memory_bandwidth mqueue ndctl0 net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdc sdc1 sdc2 sdd sde sde1 sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net xconsole zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  d5 37 81 7a 66 81 7a a2  |.........7.zf.z.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f8 0a 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 1f 3a 00 00 00 00  |.........O.:....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  39 87 59 28 97 59 28 46  |........9.Y(.Y(F|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 2a 3a  |........?....H*:|
00000020  00 00 00 00 80 00 80 00  ff 0f 0e 00 00 00 00 00  |................|
00000030  00 96 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ff 2f 88 0e 6d 88 0e ae  |........./..m...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 38 3a 00 00 00 00  |.........O8:....|
00000030  00 00 0c 00 00 00 00 00  ff 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  99 b5 63 84 c4 63 84 c6  |..........c..c..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 27 e0 37 00 00 00 00  |.........'.7....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d0 09 e8 32 15 e8 32 88  |...........2..2.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.9G     0  7.9G   0% /dev
tmpfs          tmpfs     1.6G  9.9M  1.6G   1% /run
/dev/sde1      vfat      116G  5.4G  111G   5% /cdrom
/dev/loop1     squashfs  1.2G  1.2G     0 100% /rofs
/cow           overlay   3.9G  188M  3.5G   5% /
tmpfs          tmpfs     7.9G   84K  7.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     7.9G  1.2M  7.9G   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     1.6G   52K  1.6G   1% /run/user/999
/dev/sda1      fuseblk   350M   26M  325M   8% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   465G  148G  318G  32% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   450M   29M  422M   7% /mnt/boot-sav/sda3
/dev/sdb1      fuseblk   466G  448G   18G  97% /mnt/boot-sav/sdb1
/dev/sdc2      fuseblk   448G  444G  3.3G 100% /mnt/boot-sav/sdc2

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 4 GiB, 4288675840 bytes, 8376320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 1.1 GiB, 1186353152 bytes, 2317096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab9bfef3

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *     2048 976771071 976769024 465.8G  7 HPFS/NTFS/exFAT


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0a332f11

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    718847    716800  350M  7 HPFS/NTFS/exFAT
/dev/sda2          718848 975849471 975130624  465G  7 HPFS/NTFS/exFAT
/dev/sda3       975849472 976771071    921600  450M 27 Hidden NTFS WinRE


Disk /dev/sdc: 447.1 GiB, 480103981056 bytes, 937703088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 80E12F26-E903-4295-B3CF-6D617E79F005

Device      Start       End   Sectors  Size Type
/dev/sdc1      34    262177    262144  128M Microsoft reserved
/dev/sdc2  264192 937701375 937437184  447G Microsoft basic data


Disk /dev/sdd: 2.7 TiB, 3000592977920 bytes, 732566645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sde: 115.7 GiB, 124218507264 bytes, 242614272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000820b0

Device     Boot Start       End   Sectors   Size Id Type
/dev/sde1  *     2048 242614271 242612224 115.7G  c W95 FAT32 (LBA)


No OS or WinEFI system
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems  fix-windows-boot


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.

ntfsfix /dev/sda2
Refusing to operate on read-write mounted device /dev/sda2.

ntfsfix /dev/sda3
Refusing to operate on read-write mounted device /dev/sda3.

ntfsfix /dev/sdb1
Refusing to operate on read-write mounted device /dev/sdb1.

fsck -fyM /dev/sdc2
fsck from util-linux 2.26.2
Quantity of real Windows: 1

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by Juub on 2016-05-07
I figured out using Windows command prompt. First I fixed my mbr and boot. Then I set the right disk as active and repaired the computer using Windows 10 startup repair. Thanks a lot for your help. Everything works now.

---

### Post by oldfred on 2016-05-07
Glad you have it working. 

But you have a new Z97 UEFI system and have installed all systems in the 35 year old BIOS/MBR configuration. That will work and you need to be sure to always boot in CSM/BIOS/Legacy mode.

Your sdd drive looks like it is not partitioned & formatted. Be sure to use gpt partitioning as that is required for all drives over 2TiB or for UEFI boot.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

