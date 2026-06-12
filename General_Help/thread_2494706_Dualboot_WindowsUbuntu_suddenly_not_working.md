---
title: "Dualboot Windows/Ubuntu suddenly not working"
date: 2024-01-24
forum: General Help
---

### Post by warhorus on 2024-01-24
Hello all,

I have a dualboot Windows / Ubuntu setup that up until I performed a BIOS upgrade yesterday had been happily working just fine. After the upgrade, attempting to start Windows from the Grub menu results in the following error:

```

error: no such device: 6A8B-5E21.
error: file `/efi/Microsoft/Boot/bootmgfw.efi' not found

Press any key to continue...
```

At first I was afraid I'd somehow borked my Windows installation, but if I manually tell BIOS to boot off my Windows disk, instead of my Ubuntu disk, it works just fine.

I've included my boot-info results below, as well as the contents of my grub.cfg. Hopefully someone's seeing something I'm not.

Thank you so much for taking the time to look this over!

Boot-info:
```

boot-info-4ppa2075                                              [20240123_1417]

============================== Boot Info Summary ===============================

 => Windows is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

nvme0n1p1: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p2: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 23.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/cbmr_driver.efi

sdb3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdd2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdd3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdd3 starts 
                       at sector 264192. But according to the info from 
                       fdisk, sdd3 starts at sector 32768. According to the 
                       info in the boot sector, sdd3 has 2743115775 sectors, 
                       but according to the info from fdisk, it has 
                       15628020366 sectors.
    Operating System:  
    Boot files:        


================================ 2 OS detected =================================

OS#1:   The OS now in use - Ubuntu 23.10 on sda2
OS#2:   Windows 8 or 10 on sdb4

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP104 [GeForce GTX 1080] EFI VGA from NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.5.0-14-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro quiet splash vt.handoff=7
df -Th / : /dev/sda2      ext4  915G   67G  802G   8% /

===================================== UEFI =====================================

BIOS/UEFI firmware: 3101(31.1) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0003,0001,0002,0004
Boot0000* ubuntu    HD(1,GPT,a3bdc405-b7de-6e40-bae1-41dd2c4d16e8,0x800,0x219800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* UEFI:CD/DVD Drive    BBS(129,,0x0)
Boot0002* UEFI:Removable Device    BBS(130,,0x0)
Boot0003* Windows Boot Manager    HD(2,GPT,72e411de-9564-4f96-92da-a618632cd639,0xe1800,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...5................
Boot0004* UEFI:Network Device    BBS(131,,0x0)

2d20ed0d3e457a66b52486dbc47f90a8   sdb2/Boot/bootx64.efi
2d20ed0d3e457a66b52486dbc47f90a8   sdb2/Microsoft/Boot/bootmgfw.efi
592685834cbb082c044d21845b0ba7ed   sdb2/Microsoft/Boot/bootmgr.efi
b8796e68099026aabcebb8fcf75b21f6   sdb2/Microsoft/Boot/cbmr_driver.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
nvme0n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes
sdd    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    34 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ng,    update-grub,    end-after-100GB
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdd3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdb5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdd1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    fstab-has-bad-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sdd3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot
sdb2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdd1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
nvme0n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sdd3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd
sdb4    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdd1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 37B65054-447D-4CE4-8111-1207B4FDB2B1
         Start        End    Sectors   Size Type
nvme0n1p1    34      32767      32734    16M Microsoft reserved
nvme0n1p2 32823 1953520064 1953487242 931.5G Microsoft basic data
Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 7916BB8D-C659-2B4E-AFDC-F9DD2001F0C0
       Start        End    Sectors   Size Type
sda1     2048    2203647    2201600     1G EFI System
sda2  2203648 1953521663 1951318016 930.5G Linux filesystem
Disk sdb: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: BDE5BA88-11C9-447F-93AD-78AEBBE4DDA6
         Start        End   Sectors   Size Type
sdb1       2048     923647    921600   450M Windows recovery environment
sdb2     923648    1126399    202752    99M EFI System
sdb3    1126400    1159167     32768    16M Microsoft reserved
sdb4    1159168  998872661 997713494 475.7G Microsoft basic data
sdb5  998873088 1000210431   1337344   653M Windows recovery environment
Disk sdc: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 8CF824E3-DC89-4511-B13A-86C837C0556E
      Start        End    Sectors  Size Type
sdc1      34     262177     262144  128M Microsoft reserved
sdc2  264192 3907028991 3906764800  1.8T Microsoft basic data
Disk sdd: 7.28 TiB, 8001563222016 bytes, 15628053168 sectors
Disk identifier: 5F21AA99-C726-4507-8CFF-083ACD6E626C
     Start         End     Sectors  Size Type
sdd1     34        2081        2048    1M Microsoft LDM metadata
sdd2   2082       32767       30686   15M Microsoft reserved
sdd3  32768 15628053134 15628020367  7.3T Microsoft LDM data

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA Samsung SSD 870:;
1:1049kB:1128MB:1127MB:fat32::boot, esp;
2:1128MB:1000GB:999GB:ext4::;
sdb:512GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:473MB:472MB:ntfs:Basic data partition:hidden, diag, no_automount;
2:473MB:577MB:104MB:fat32:EFI system partition:boot, esp, no_automount;
3:577MB:593MB:16.8MB::Microsoft reserved partition:msftres, no_automount;
4:593MB:511GB:511GB:ntfs:Basic data partition:msftdata;
5:511GB:512GB:685MB:ntfs::hidden, diag, no_automount;
sdc:2000GB:scsi:512:4096:gpt:ATA WDC WD2003FZEX-0:;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
sdd:8002GB:scsi:512:4096:gpt:ATA WDC WD80EFBX-68A:;
1:17.4kB:1066kB:1049kB::LDM metadata partition:;
2:1066kB:16.8MB:15.7MB::Microsoft reserved partition:msftres;
3:16.8MB:8002GB:8002GB:ntfs:LDM data partition:;
nvme0n1:1000GB:nvme:512:512:gpt:Samsung SSD 970 EVO Plus 1TB:;
1:17.4kB:16.8MB:16.8MB::Microsoft reserved partition:msftres;
2:16.8MB:1000GB:1000GB:ntfs:Basic data partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL  PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1      vfat     3DD1-24CD                            a3bdc405-b7de-6e40-bae1-41dd2c4d16e8        
&#9492;&#9472;sda2      ext4     ff01a110-85f9-4a5f-afaf-6de384016eaf 90ad30b0-613f-a44f-9f65-fd112306fcb8        
sdb                                                                                                   
&#9500;&#9472;sdb1      ntfs     A21638151637E8C5                     210ca235-8646-40b7-8847-642857283aec        Basic data partition
&#9500;&#9472;sdb2      vfat     6A8B-5E21                            72e411de-9564-4f96-92da-a618632cd639        EFI system partition
&#9500;&#9472;sdb3                                                    1853280c-8513-4ff3-8a1c-6762ac0457a1        Microsoft reserved partition
&#9500;&#9472;sdb4      ntfs     4C8C942D8C941414                     37b6bfe7-fe38-44b3-b8de-acfdecb015d0 System Basic data partition
&#9492;&#9472;sdb5      ntfs     EEF6A882F6A84CA1                     8571a3cc-0755-4453-8861-35dcf926857a        
sdc                                                                                                   
&#9500;&#9472;sdc1                                                    fa642c95-302c-11ec-a31d-80a58916f1c9        Microsoft reserved partition
&#9492;&#9472;sdc2      ntfs     5E20972B209708E3                     88e74a15-1d2d-4ee6-a812-d75384ec76af        Basic data partition
sdd                                                                                                   
&#9500;&#9472;sdd1                                                    fa642ca2-302c-11ec-a31d-80a58916f1c9        LDM metadata partition
&#9500;&#9472;sdd2                                                    41ca893c-7ab4-40a7-8bcf-2dd5e5cca892        Microsoft reserved partition
&#9492;&#9472;sdd3      ntfs     CC808ECF808EBF86                     fa642ca5-302c-11ec-a31d-80a58916f1c9 Media  LDM data partition
nvme0n1                                                                                               
&#9500;&#9472;nvme0n1p1                                               f69385d6-7f35-11ea-a2d4-80a58916f1c9        Microsoft reserved partition
&#9492;&#9472;nvme0n1p2 ntfs     A4CAEF24CAEEF18A                     c69902f1-662e-45a9-8a46-21ee6cf9d58f Games  Basic data partition

Mount points (filtered): _______________________________________________________

                                Avail Use% Mounted on
/dev/nvme0n1p2                  86.3G  91% /mnt/boot-sav/nvme0n1p2
/dev/sda2                      801.8G   7% /
/dev/sdb1                      440.1M   2% /mnt/boot-sav/sdb1
/dev/sdb2                       66.4M  30% /mnt/boot-sav/sdb2
/dev/sdb4                       66.4G  86% /mnt/boot-sav/sdb4
/dev/sdb5                       42.4M  94% /mnt/boot-sav/sdb5
/dev/sdc2                        1.8T   0% /mnt/boot-sav/sdc2
/dev/sdd3                        3.4T  54% /mnt/boot-sav/sdd3
efivarfs                        34.4K  79% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p2                 fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2                      ext4            rw,relatime
/dev/sdb1                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb2                      vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb4                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb5                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc2                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdd3                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid ff01a110-85f9-4a5f-afaf-6de384016eaf root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   ff01a110-85f9-4a5f-afaf-6de384016eaf
Windows Boot Manager (on sdb2)   osprober-efi-6A8B-5E21
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/ff01a110-85f9-4a5f-afaf-6de384016eaf / ext4 defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
/dev/disk/by-uuid/3DD1-24CD /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=saved
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 553.686168671 = 594.515996672  boot/grub/grub.cfg                             1
 174.720317841 = 187.604512768  boot/vmlinuz                                   1
  17.837100983 = 19.152441344   boot/vmlinuz-6.2.0-39-generic                  2
 174.720317841 = 187.604512768  boot/vmlinuz-6.5.0-14-generic                  1
  17.837100983 = 19.152441344   boot/vmlinuz.old                               2
 384.816402435 = 413.193465856  boot/initrd.img                                5
 563.667964935 = 605.233868800  boot/initrd.img-6.2.0-39-generic               4
 384.816402435 = 413.193465856  boot/initrd.img-6.5.0-14-generic               5
 563.667964935 = 605.233868800  boot/initrd.img.old                            4

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18228 Oct  2 10:23 10_linux
-rwxr-xr-x 1 root root 43202 Oct  2 10:23 10_linux_zfs
-rwxr-xr-x 1 root root 14459 Oct  2 10:23 20_linux_xen
-rwxr-xr-x 1 root root   786 Oct  2 10:23 25_bli
-rwxr-xr-x 1 root root 13120 Oct  2 10:23 30_os-prober
-rwxr-xr-x 1 root root  1174 Oct  2 10:23 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Feb 26  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec  9  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec  9  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub-efi of
sda2,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 23.10 entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

```

Grub.cfg:
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${saved_entry}"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
else
  search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if [ ${grub_platform} != pc ]; then
      set linux_gfx_mode=keep
    elif hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
    else
      search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
    fi
    linux    /boot/vmlinuz-6.5.0-14-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-6.5.0-14-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
    menuentry 'Ubuntu, with Linux 6.5.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.5.0-14-generic-advanced-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
        else
          search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
        fi
        echo    'Loading Linux 6.5.0-14-generic ...'
        linux    /boot/vmlinuz-6.5.0-14-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-6.5.0-14-generic
    }
    menuentry 'Ubuntu, with Linux 6.5.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.5.0-14-generic-recovery-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
        else
          search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
        fi
        echo    'Loading Linux 6.5.0-14-generic ...'
        linux    /boot/vmlinuz-6.5.0-14-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro single recovery nomodeset dis_ucode_ldr 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-6.5.0-14-generic
    }
    menuentry 'Ubuntu, with Linux 6.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.2.0-39-generic-advanced-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
        else
          search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
        fi
        echo    'Loading Linux 6.2.0-39-generic ...'
        linux    /boot/vmlinuz-6.2.0-39-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-6.2.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 6.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-6.2.0-39-generic-recovery-ff01a110-85f9-4a5f-afaf-6de384016eaf' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
        else
          search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
        fi
        echo    'Loading Linux 6.2.0-39-generic ...'
        linux    /boot/vmlinuz-6.2.0-39-generic root=UUID=ff01a110-85f9-4a5f-afaf-6de384016eaf ro single recovery nomodeset dis_ucode_ldr 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-6.2.0-39-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+x64.efi)" --class memtest $menuentry_id_option 'memtest86+' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
    else
      search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
    fi
        linux    /boot/memtest86+x64.efi
}
menuentry 'Memory test (memtest86+x64.efi, serial console)' --class memtest $menuentry_id_option 'memtest86+-serial' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  ff01a110-85f9-4a5f-afaf-6de384016eaf
    else
      search --no-floppy --fs-uuid --set=root ff01a110-85f9-4a5f-afaf-6de384016eaf
    fi
        linux   /boot/memtest86+x64.efi console=ttyS0,115200
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_bli ###
if [ "$grub_platform" = "efi" ]; then
  insmod bli
fi
### END /etc/grub.d/25_bli ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sdb2)' --class windows --class os $menuentry_id_option 'osprober-efi-6A8B-5E21' {
    insmod part_gpt
    insmod fat
    set root='hd1,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  6A8B-5E21
    else
      search --no-floppy --fs-uuid --set=root 6A8B-5E21
    fi
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
if [ "$grub_platform" = "efi" ]; then
    fwsetup --is-supported
    if [ "$?" = 0 ]; then
        menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
            fwsetup
        }
    fi
fi
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/35_fwupd ###
### END /etc/grub.d/35_fwupd ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg
fi
### END /etc/grub.d/41_custom ###

```

---

### Post by tea for one on 2024-01-24
You confirmed that you can boot Windows 8/10 via your PC boot menu.
Can you boot into Ubuntu 23.10?

---

### Post by oldfred on 2024-01-24
All your drives are gpt which is good.
But Windows only boots in UEFI mode from gpt partitioned drives, and you have old Windows BIOS boot in MBR of several drives.

You also have LDM on sdd??
LDM is a Microsoft work around for the 4 primary partition limit on MBR partitioned drives. No need for it with gpt.
Not sure how you would even get that, but others have had it also.
Microsoft has no undo, easy to convert to LDM (even though not required).
Whatever you do have good backups. Even some Windows tools do not work with LDM.

Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM

This is now older info as LDM not really required anymore. 
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

Other options also Aomei or even testdisk if only 4 dynamic partitions:
[http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by warhorus on 2024-01-24
> **tea for one said:**
> You confirmed that you can boot Windows 8/10 via your PC boot menu.
Can you boot into Ubuntu 23.10?

I'm sorry, yes, I should have mentioned that. I can boot into Ubuntu just fine via the Grub menu, no issues there. And I can boot into Windows 11 by telling BIOS to boot off the appropriate drive. I don't have any issue other than trying to boot to windows from the Grub menu.

> **oldfred said:**
> All your drives are gpt which is good.
But Windows only boots in UEFI mode from gpt partitioned drives, and you have old Windows BIOS boot in MBR of several drives.

You also have LDM on sdd??

The LDM-bearing drive is just a media drive I've got sitting on my PC, no OS on it. The only drive that should have an actual Windows install on it should be sdb which, to my untrained eye, looks put together correctly?

This setup was working for months, so I'm not sure why Grub's suddenly unhappy with it.

---

### Post by oldfred on 2024-01-24
Did a Windows update turn on fast startup or do an UEFI firmware update.
Those Windows updates often reset to defaults.
If Windows fast start up is on, grub will not boot it. Some firmware settings in UEFI may also make a difference, but those more often are issues then with Ubuntu.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

### Post by tea for one on 2024-01-24
> **warhorus said:**
>  I don't have any issue other than trying to boot to windows from the Grub menu.
Your grub menu is missing the OS_PROBER line.
Boot into Ubuntu and open a terminal
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0 [COLOR="#0000FF"]# originally saved[/COLOR]
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]# originally hidden[/COLOR]
GRUB_TIMEOUT=5 [COLOR="#0000FF"]# originally 0[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"] # add this line[/COLOR]
```
```
sudo update-grub
```
Was the Windows Boot Manager found?

---

### Post by warhorus on 2024-01-24
Running update-grub seems to have fixed it! Thank you both very much for taking the time to help!

---

