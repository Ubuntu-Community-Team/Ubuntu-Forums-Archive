---
title: "Multi boot system but no Grub Menu"
date: 2024-04-26
forum: General Help
---

### Post by SUPERFITTER on 2024-04-26
I have three Linux systems installed, but I do not have a Grub Menu at boot.  I ran repair Boot Loader and it says that the Grub is repaired, but I still do not have a Menu?


```


boot-repair-4ppa2075                                              [20240426_1324]

============================= Boot Repair Summary ==============================





This will modify the mount point of sdc3 in order to remove spaces and special characters. Do you want to continue?
This will modify the mount point of sdc3 in order to remove spaces and special characters. Do you want to continue?
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-28-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
sda3,
using the following options:  sda1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /boot/efi/efi/Boot/bootx64.efi
mv /boot/efi/efi/Boot/bkpbootx64.efi /boot/efi/efi/Boot/bootx64.efi
/dev/sda3/boot/efi not empty

Unhide GRUB boot menu in sda3/etc/default/grub

===================== Reinstall the grub-efi of /dev/sda3 ======================

grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-28-generic
modprobe efivars

efibootmgr -v before grub install
BootCurrent: 0001
Timeout: 3 seconds
BootOrder: 0002,0000,0001
Boot0000* EFI DVD/CDROM    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(0,0,0)
Boot0001* OsLoader0000    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(1,0,0)/HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(EFIBOOTBOOTX64.EFI)
Boot0002* ubuntu    HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(EFIubuntushimx64.efi)

uname -r
6.5.0-28-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v after grub install
BootCurrent: 0001
Timeout: 3 seconds
BootOrder: 0002,0000,0001
Boot0000* EFI DVD/CDROM    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(0,0,0)
Boot0001* OsLoader0000    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(1,0,0)/HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(EFIBOOTBOOTX64.EFI)
Boot0002* ubuntu    HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(EFIubuntushimx64.efi)
Warning: NVram was not modified.

update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.5.0-28-generic
Found initrd image: /boot/initrd.img-6.5.0-28-generic
Found linux image: /boot/vmlinuz-6.5.0-18-generic
Found initrd image: /boot/initrd.img-6.5.0-18-generic
Found Zorin OS 17.1 (17) on /dev/sda2
Found Linux Mint 21.3 Virginia (21.3) on /dev/sda4
This will modify the mount point of sdc3 in order to remove spaces and special characters. Do you want to continue?

Unhide GRUB boot menu in sda3/boot/grub/grub.cfg

Unhide GRUB boot menu in sda4/boot/grub/grub.cfg

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 22.04.4 LTS entry (sda1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 140fd5ab-7ba5-4002-a664-7692bbd08750 root hd1,msdos1 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda2 
                       and looks at sector 168711056 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt2)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_gpt biosdisk
                       -------------------------------------------------------
    Operating System:  Zorin OS 17.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda3 
                       and looks at sector 1030863072 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt3)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_gpt biosdisk
                       -------------------------------------------------------
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda4 
                       and looks at sector 1822863072 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt4)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_gpt biosdisk
                       -------------------------------------------------------
    Operating System:  Linux Mint 21.3
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v2.00) in the file 
                       /xubuntu-22.04.2-desktop-amd64.iso looks at sector 0 
                       of the same hard drive for core.img, but core.img can 
                       not be found at this location.
    Operating System:  
    Boot files:        


================================ 3 OS detected =================================

OS#1:   The OS now in use - Ubuntu 22.04.4 LTS on sda3
OS#2:   Zorin OS 17.1 (17) on sda2
OS#3:   Linux Mint 21.3 Virginia (21.3) on sda4

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GF119 [GeForce GT 520] 2nd Generation Core Processor Family Integrated Graphics Controller from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.5.0-28-generic root=UUID=40abfad6-9825-4d38-bc44-c1cb1f8e48d1 ro quiet splash vt.handoff=7
df -Th / : /dev/sda3      ext4  231G   12G  208G   6% /

===================================== UEFI =====================================

BIOS/UEFI firmware: F10 from Award Software International, Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
No EFI in dmseg.
SecureBoot disabled - This system doesn't support Secure Boot.
BootCurrent: 0001
Timeout: 3 seconds
BootOrder: 0002,0000,0001
Boot0000* EFI DVD/CDROM    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(0,0,0)
Boot0001* OsLoader0000    PcieRoot(0x0)/Pci(0x1f,0x5)/Ata(1,0,0)/HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0002* ubuntu    HD(1,GPT,f7767dec-d7bf-4aab-ba3e-36612c137960,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdc    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda4    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ng,    update-grub,    end-after-100GB
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sda4    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 149E9D15-B64E-49B1-846C-5859202D29D1
          Start        End   Sectors   Size Type
sda1        2048    1050623   1048576   512M EFI System
sda2     1050624  975993983 974943360 464.9G Linux filesystem
sda3   975994880 1469562879 493568000 235.4G Microsoft basic data
sda4  1469562880 1953523817 483960938 230.8G Microsoft basic data
Disk sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0xb35c20c3
     Boot Start       End   Sectors   Size Id Type
sdb1        2048 976773119 976771072 465.8G 83 Linux
Disk sdc: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0xb3a00018
     Boot      Start        End    Sectors   Size Id Type
sdc1  *          2048     206847     204800   100M  7 HPFS/NTFS/exFAT
sdc2           206848 1014282239 1014075392 483.5G  7 HPFS/NTFS/exFAT
sdc3       1014282240 1953519615  939237376 447.9G  7 HPFS/NTFS/exFAT

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:512:gpt:ATA Samsung SSD 870:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:500GB:499GB:ext4::;
3:500GB:752GB:253GB:ext4::msftdata;
4:752GB:1000GB:248GB:ext4::msftdata;
sdb:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKS-0:;
1:1049kB:500GB:500GB:ext4::;
sdc:1000GB:scsi:512:4096:msdos:ATA WDC WD10EZEX-00W:;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:519GB:519GB:ntfs::;
3:519GB:1000GB:481GB:ntfs::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                       
&#9500;&#9472;sda1 vfat     C37D-75AD                            f7767dec-d7bf-4aab-ba3e-36612c137960                 EFI System Partition
&#9500;&#9472;sda2 ext4     2df6acb3-3b03-4e8c-b475-e4b78cbf9522 455d1945-5508-4cf4-963f-0c57f7a28b15                 
&#9500;&#9472;sda3 ext4     40abfad6-9825-4d38-bc44-c1cb1f8e48d1 b9e5319a-772f-4ce4-9d59-efe179aa88f1                 
&#9492;&#9472;sda4 ext4     7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d c7520445-79da-482b-a269-d6eee912cb73                 
sdb                                                                                                       
&#9492;&#9472;sdb1 ext4     fc6a8a81-4408-4920-8c49-ca7aaa8810d4 b35c20c3-01                                          
sdc                                                                                                       
&#9500;&#9472;sdc1 ntfs     0A68C36D68C3565B                     b3a00018-01                          System Reserved 
&#9500;&#9472;sdc2 ntfs     626EAB593C1543F4                     b3a00018-02                                          
&#9492;&#9472;sdc3 ntfs     CAEC52AAEC529095                     b3a00018-03                          New Volume      
sdd                                                                                                       
sde                                                                                                       
sdf                                                                                                       
sdg                                                                                                       

Mount points (filtered): _______________________________________________________

                                Avail Use% Mounted on
/dev/sda2                        421G   3% /mnt/boot-sav/sda2
/dev/sda3                      207.2G   5% /
/dev/sda4                      200.4G   6% /mnt/boot-sav/sda4
/dev/sdb1                      434.1G   0% /media/me/fc6a8a81-4408-4920-8c49-ca7aaa8810d4
/dev/sdc1                         73M  27% /mnt/boot-sav/sdc1
/dev/sdc2                      483.5G   0% /media/me/626EAB593C1543F4
/dev/sdc3                      369.4G  18% /media/me/New Volume
efivarfs                        57.6K   2% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/sda2                      ext4            rw,relatime
/dev/sda3                      ext4            rw,relatime,errors=remount-ro
/dev/sda4                      ext4            rw,relatime
/dev/sdb1                      ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sdc1                      fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc2                      ntfs3           rw,nosuid,nodev,relatime,uid=1000,gid=1000,windows_names,iocharset=utf8
/dev/sdc3                      ntfs3           rw,nosuid,nodev,relatime,uid=1000,gid=1000,windows_names,iocharset=utf8

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 40abfad6-9825-4d38-bc44-c1cb1f8e48d1 root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Zorin   2df6acb3-3b03-4e8c-b475-e4b78cbf9522
Linux Mint 21.3 Virginia (21.3) (on sda4)   7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=2df6acb3-3b03-4e8c-b475-e4b78cbf9522 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C37D-75AD  /boot/efi       vfat    umask=0077      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
  80.447723389 = 86.380085248   boot/grub/i386-pc/core.img                     1
   1.029857635 = 1.105801216    boot/vmlinuz                                   1
 322.420482635 = 346.196357120  boot/vmlinuz-6.5.0-27-generic                  2
   1.029857635 = 1.105801216    boot/vmlinuz-6.5.0-28-generic                  1
 322.420482635 = 346.196357120  boot/vmlinuz.old                               2
 389.750972748 = 418.491920384  boot/initrd.img                                2
 414.335151672 = 444.888981504  boot/initrd.img-6.5.0-27-generic               1
 389.750972748 = 418.491920384  boot/initrd.img-6.5.0-28-generic               2
 414.335151672 = 444.888981504  boot/initrd.img.old                            1

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18673 May 10  2023 10_linux
-rwxr-xr-x 1 root root 43021 May 10  2023 10_linux_zfs
-rwxr-xr-x 1 root root 14387 May 10  2023 20_linux_xen
-rwxr-xr-x 1 root root 13369 May 10  2023 30_os-prober
-rwxr-xr-x 1 root root  1372 May 10  2023 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 May 10  2023 40_custom
-rwxr-xr-x 1 root root   215 May 10  2023 41_custom

====================== sda3/boot/grub/grub.cfg (filtered) ======================

Ubuntu   40abfad6-9825-4d38-bc44-c1cb1f8e48d1
Zorin OS 17.1 (17) (on sda2)   2df6acb3-3b03-4e8c-b475-e4b78cbf9522
Linux Mint 21.3 Virginia (21.3) (on sda4)   7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda3/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=40abfad6-9825-4d38-bc44-c1cb1f8e48d1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C37D-75AD  /boot/efi       vfat    umask=0077      0       1

======================= sda3/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda3: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 477.156234741 = 512.342605824  boot/grub/grub.cfg                             1
 491.553840637 = 527.801917440  boot/grub/i386-pc/core.img                     1
 623.786693573 = 669.785862144  boot/vmlinuz                                   1
 491.302310944 = 527.531839488  boot/vmlinuz-6.5.0-18-generic                  1
 623.786693573 = 669.785862144  boot/vmlinuz-6.5.0-28-generic                  1
 491.302310944 = 527.531839488  boot/vmlinuz.old                               1
 467.370079041 = 501.834801152  boot/initrd.img                                1
 495.367183685 = 531.896463360  boot/initrd.img-6.5.0-18-generic               5
 467.370079041 = 501.834801152  boot/initrd.img-6.5.0-28-generic               1
 495.367183685 = 531.896463360  boot/initrd.img.old                            5

===================== sda3: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

====================== sda4/boot/grub/grub.cfg (filtered) ======================

Linux Mint 21.3 Cinnamon   7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d
Zorin OS 17.1 (17) (on sda2)   2df6acb3-3b03-4e8c-b475-e4b78cbf9522
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda4/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C37D-75AD  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda4/etc/default/grub (filtered) =======================

GRUB_DEFAULT="saved"
GRUB_TIMEOUT="20"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE="1920x1080x16"
GRUB_DISABLE_OS_PROBER="false"
GRUB_SAVEDEFAULT="true"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"
==================== sda4: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 869.208869934 = 933.305917440  boot/grub/i386-pc/core.img                     1
 730.253055573 = 784.103247872  boot/vmlinuz                                   1
 854.885868073 = 917.926711296  boot/vmlinuz-5.15.0-102-generic                1
 730.253055573 = 784.103247872  boot/vmlinuz-5.15.0-105-generic                1
 867.070308685 = 931.009654784  boot/vmlinuz-5.15.0-91-generic                 2
 854.885868073 = 917.926711296  boot/vmlinuz.old                               1
 841.234477997 = 903.268642816  boot/initrd.img                                1
 844.226661682 = 906.481475584  boot/initrd.img-5.15.0-102-generic             1
 841.234477997 = 903.268642816  boot/initrd.img-5.15.0-105-generic             1
 843.742244720 = 905.961336832  boot/initrd.img-5.15.0-91-generic              1
 844.226661682 = 906.481475584  boot/initrd.img.old                            1

===================== sda4: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom
drwxr-xr-x 4 root root  4096 Apr 22 04:42 backup


```

How do you :
Unhide GRUB boot menu in sda3/boot/grub/grub.cfg?

Unhide GRUB boot menu in sda4/boot/grub/grub.cfg?

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg? 
Thank You for any help

---

### Post by #&amp;thj^% on 2024-04-26
Right now for the one your booted to, show us this:
```
cat /etc/default/grub

```

---

### Post by SUPERFITTER on 2024-04-26
> 

me@me1:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""



# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt

---

### Post by #&amp;thj^% on 2024-04-26
Ok this 
```
GRUB_TIMEOUT_STYLE=hidden
```
needs to be:
```
GRUB_TIMEOUT_STYLE=menu
```
and this one I've have found works better with out "quiet splash'
so it would now look like:
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```
Please use 
```
sudoedit /etc/default/grub
```
To make those changes and save that file, and run:
```
sudo update-grub
```

You may in the future find rEFInd a useful tool when using more than one OS.

I'm not one that will use os-prober, been burned too many times by that non-sense.

---

### Post by yancek on 2024-04-26
Based on the information you have posted, your 3 systems (mint, ubuntu,zorin) are all on the sda drive which is a gpt drive and has an efi partition  The first questions I have is didthis ever work, meaning did all 3 systems boot successfully from the same grub menu?  If so, which OS was the boot OS?    Boot repair shows the grub.cfg file on your EFI partition pointing to:

```
 search.fs_uuid 40abfad6-9825-4d38-bc44-c1cb1f8e48d1 root hd0,gpt3 
```

If you look at the blkid output you will see that is sda3, the Ubuntu install.  I would expect Ubuntu to boot by default, is that what happens?  If not what do you get and in which order did you install the 3 systems?

---

### Post by SUPERFITTER on 2024-04-26
There is no grub menu. All three will boot individually, if I tap the down arrow when booting and then hit enter. One of the three will then boot. It's a crap shot as to which one will boot. I need to restore the boot loader.

---

### Post by SUPERFITTER on 2024-04-26
1fallen

I was able to change hidden to menu.  I could change "quit splash" to "sudoedit /etc/default/grub" but could not save.   I ran sudo update-grub at bottom of  sudoedit /etc/default/grub.   I must be doing something wrong?  I am not familiar with that page.

---

### Post by oldfred on 2024-04-26
You are not changing quiet splash, you are changing it to blank per 1fallan's suggestion. Which is good.
But I prefer to use these settings over the defaults. noplymounth is an alternate to the "". You see the boot process.
[FONT=monospace][COLOR=#000000]GRUB_TIMEOUT_STYLE=menu[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

I once set default line to a blank line I added for spacing. I had  to blindly use down arrow also.
But enter should boot first entry in grub menu.[/COLOR]

If you added this line to Ubuntu's boot, that is the problem. it only is valid for zorin.
[/FONT]GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt 				[FONT=monospace]

[/FONT]

---

### Post by #&amp;thj^% on 2024-04-26
> **SUPERFITTER said:**
> 1fallen

I was able to change hidden to menu.  I could change "quit splash" to "sudoedit /etc/default/grub" but could not save. 
After the changes are made use key combo [Ctrl + o] to exit after the save use [Ctrl + x] Now update grub again.

The important bits should look like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

```

Or as oldfred suggests like this "GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

---

### Post by SUPERFITTER on 2024-04-26
I get to this point but nothing gets saved.   
Where to I enter these commands?  
After the changes are made use key combo [Ctrl + o] to exit after the save use [Ctrl + x] Now update grub again.  
This is what I see:

```

  GNU nano 6.2                                                                                   /var/tmp/grub.XXWl0qUl *                                                                                          
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10[COLOR=#ff0000]
[/COLOR][COLOR=#000000]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`        [/COLOR][COLOR=#0000ff]
[/COLOR][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false
GRUB_DISABLE_OS_PROBER=false














^G Help          ^O Write Out     ^W Where Is      ^K Cut           ^T Execute       ^C Location      M-U Undo         M-A Set Mark     M-] To Bracket   M-Q Previous     ^B Back          ^&#9666; Prev Word
^X Exit          ^R Read File     ^\ Replace       ^U Paste         ^J Justify       ^/ Go To Line    M-E Redo         M-6 Copy         ^Q Where Was     M-W Next         ^F Forward       ^&#9656; Next Word

```

---

### Post by ajgreeny on 2024-04-26
@ 1fallen

Surely with the line
GRUB_TIMEOUT=0
you will still not see the grub menu. I always change it to 2 in place of 0.

---

### Post by #&amp;thj^% on 2024-04-26
Where to start, Please use Code tags to paste terminal returns. I need you to that in the last post you made #10
And please don't add your questions in that file.
Right Now before anything else, while you are in the terminal and click it to be sure it's in focus.....Now use "Ctl x"
to close without saving, that one is a mess...:P
Next reply you have just run:
```
sudoedit /etc/default/grub
```
And show all of it back here ****In Code Tags.. Thanks

---

### Post by #&amp;thj^% on 2024-04-26
> **ajgreeny said:**
> @ 1fallen

Surely with the line
GRUB_TIMEOUT=0
you will still not see the grub menu. I always change it to 2 in place of 0.

I see it all the time, plus I have 5 other Boot-able OS's on different drives....No Multi-Boots Allowed here.
My Bootl loader is rEFInd! just to be clear.

But your suggestion should be considered by the OP and not me...I'm just fine, :)

To the OP, I'm going offline now see you tomorrow.

---

### Post by oldfred on 2024-04-26
My grub with commented (#) lines excluded.

```
[FONT=monospace][COLOR=#54ff54][B]
fred@Z170-jammy[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/default/grub | grep -v '#' [/COLOR]
GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=menu 
GRUB_TIMEOUT=3 
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth" 
GRUB_CMDLINE_LINUX="" 
GRUB_DISABLE_OS_PROBER=true 
GRUB_DISTRIBUTOR=jammy
[/FONT]
```

I have multiple installs so I change [FONT=monospace]GRUB_DISTRIBUTOR=  to version I have.
I change timeout to 3 seconds just to have enough time to change if desired.
And I want menu so I can choose another install. 
I turn os-prober off, as I add entries I really want in 40_custom. I have some old obsolete installs that i do not need nor want in grub menu. Update of grub is also a lot faster with os-prober off.
[/FONT]

---

### Post by SUPERFITTER on 2024-04-27
```


GNU nano 6.2                                                                                   /var/tmp/grub.XXF1yTsL                                                                                            
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false
GRUB_DISABLE_OS_PROBER=false

^G Help          ^O Write Out     ^W Where Is      ^K Cut           ^T Execute       ^C Location      M-U Undo         M-A Set Mark     M-] To Bracket   M-Q Previous     ^B Back          ^&#9666; Prev Word
^X Exit          ^R Read File     ^\ Replace       ^U Paste         ^J Justify       ^/ Go To Line    M-E Redo         M-6 Copy         ^Q Where Was     M-W Next         ^F Forward       ^&#9656; Next Word 
```

---

### Post by #&amp;thj^% on 2024-04-27
Change this line
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
To this
```
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```
And at the bottom remove one of these lines "GRUB_DISABLE_OS_PROBER=false"

Just me venting but i really really HATE os-prober, but that's up to you. :)

Now after the change, and still in the terminal use this first>>>"Ctrl +o" then press enter that writes the changes, next pres "Ctrl + x" That closes sudoedit, with the saved changes.
Next "update-grub"
```
sudo update-grub
``` 
Reboot and fingers crossed

---

### Post by SUPERFITTER on 2024-04-27
I followed your instructions (I see what I was doing wrong). 
 I rebooted twice and still no Grub Menu.   
I did not have this problem with my old hard drives, started with this SSD.  
Thank you for sticking with me with this problem. 


 ```

 GNU nano 6.2                                                                                   /var/tmp/grub.XXWo3Az5                                                                                            
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false















^G Help          ^O Write Out     ^W Where Is      ^K Cut           ^T Execute       ^C Location      M-U Undo         M-A Set Mark     M-] To Bracket   M-Q Previous     ^B Back          ^&#9666; Prev Word
^X Exit          ^R Read File     ^\ Replace       ^U Paste         ^J Justify       ^/ Go To Line    M-E Redo         M-6 Copy         ^Q Where Was     M-W Next         ^F Forward       ^&#9656; Next Word 
```

---

### Post by SUPERFITTER on 2024-04-27
Would rEFind Boot Manager be better then Grub in this case?

---

### Post by #&amp;thj^% on 2024-04-27
> **SUPERFITTER said:**
> Would rEFind Boot Manager be better then Grub in this case?

Opinionated, but since you asked Yes.

But I would install rEFInd on USB Thumb Drive, and set your Bios to boot to that first. That Link is here: [https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download](https://sourceforge.net/projects/refind/files/0.12.0/refind-flashdrive-0.12.0.zip/download)

It then will present you with all shown OS's 

To be fair though there is no telling what installed OS you have is handling Grub though. (Zorin Ububtu or any others that you now have)

That's the os-prober that takes over.

---

### Post by SUPERFITTER on 2024-04-27
Loaded to a Thumb drive, and set  Bios to boot to that first.  Boot Menu came up switched to the USB drive, entered and booted right back into Ubuntu.

---

### Post by #&amp;thj^% on 2024-04-27
You don't load it to a USB drive, Gnome Disks will install it to your USB drive though

I assume you unziped it, and inside that Folder you will see a ".img"
ie:
```
cd /home/me/Downloads/refind-flashdrive-0.12.0/ && ls
COPYING.txt  LICENSE.txt  README-flashdrive.txt         SHELLS.txt
CREDITS.txt  NEWS.txt    **_ refind-flashdrive-0.12.0.img_**
```
Point that with Gnome Disks and in the top right hand corner you see 3 vertical Dots Select Restore Disk Img

I'm sorry I'm so assuming, it's hard for me to know everyone's Skill Set

Please see my Screenshot to help But Use Restore Disk Image Not Create Image, I'm very tired today....LOL

---

### Post by oldfred on 2024-04-27
I use rEFInd on a tiny old too small for anything else flash drive for emergency boot. Saved me a couple of times.

But I see a newer version is available.
[https://sourceforge.net/projects/refind/](https://sourceforge.net/projects/refind/)
refind_0.14.2-1_amd64.deb

---

### Post by SUPERFITTER on 2024-04-28
I followed your instructions and got the img file on the thumb drive.  I booted to the thumb drive  at startup and it just kept rebooting the computer.  After 4 attempts I unplugged the thumb drive and  booted to Ubuntu.  I then formatted the thumb drive and reinstalled the img.  Retried booting from the thumb drive, same problem kept rebooting computer.

---

### Post by #&amp;thj^% on 2024-04-28
Weird, but will you now show this:
```
df -hT
```
We will try a reinstall of Grub,
Just an example on "my" system, but clipped for easy viewing.
```
df -hT
### Mine is
/dev/sda1                                        vfat      1.1G  6.2M  1.1G   1% /boot/efi

```
So I now run:
```
 sudo grub-install /dev/sda
[sudo] password for me: 
Installing for x86_64-efi platform.
Installation finished. No error reported.

```
If there are errors please post them back here please.

---

### Post by #&amp;thj^% on 2024-04-28
BTW, You did first format the Thumb Drive to "fat32" first though Right?

---

### Post by SUPERFITTER on 2024-04-28
```

me@me1:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     1.2G  2.1M  1.2G   1% /run
/dev/sda3      ext4      231G   13G  207G   6% /
tmpfs          tmpfs     5.8G     0  5.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
efivarfs       efivarfs   64K  1.6K   58K   3% /sys/firmware/efi/efivars
/dev/sda1      vfat      511M  8.2M  503M   2% /boot/efi
tmpfs          tmpfs     1.2G  1.7M  1.2G   1% /run/user/1000
/dev/sdb1      ext4      458G   28K  435G   1% /media/me/fc6a8a81-4408-4920-8c49-ca7aaa8810d4
/dev/sdc3      ntfs3     448G   79G  370G  18% /media/me/New Volume
/dev/sdc2      ntfs3     484G   80M  484G   1% /media/me/626EAB593C1543F4
me@me1:~$  sudo grub-install /dev/sda
[sudo] password for me: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
me@me1:~$ Installing for x86_64-efi platform
Installing: command not found
me@me1:~$ Installation finished. No error reported
Installation: command not found
me@me1:~$ 
```

Formatted to fat 32

---

### Post by #&amp;thj^% on 2024-04-28
> **SUPERFITTER said:**
> 

Formatted to fat 32
Oh goodness I hope that format was to the Thumb Drive, for rEFInd, and nothing Else.

Any way what now will this show, paste back here to see please:
```
sudo update-grub
```
Ive been outside in my garden.

---

### Post by yancek on 2024-04-28
Has the editing you have been doing all been while booted into Ubuntu as that should be the primary boot OS according to the boot repair report (/dev/sda3)?  In an earlier post you show zorin themes in the /etc/default/grub file.  Were you booted into Zorin?  Or do you have that entry in the Ubuntu file?

> GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt 

Your boot repair report shows Zorin on sda2, Ubuntu on sda3 and Mint on sda4.  Have you run sudo update-grub while booted into Ubuntu?  If you have, you should have watched the output to see if entries are detected and added to the Ubuntu Grub menu.  This is because your grub.cfg file on the EFI partition is pointing to the grub.cfg file on sda3, Ubuntu and that is the menu you should see if you have made the proper change in the /etc/default/grub file on Ubuntu.

If you had Grub installed to Zorin and Mint, the entries below when added to the grub.cfg file on Ubuntu should boot Zorin and Mint.  Copy the entries there and save the change in the Ubuntu grub.cfg file.  Save the changes and reboot.  Do NOT run update-grub.  If the entries boot, you can then put the changes in the 40_custom file of /etc/grub.d, save the changes and update Grub.

>  menuentry "Zorin-sda2"{
search.fs_uuid 2df6acb3-3b03-4e8c-b475-e4b78cbf9522  root hd0,gpt2
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
} 

menuentry "Mint-sda4"{
search.fs_uuid 7d6bc9c1-ea82-4aa6-9f87-8bf205487a4d  root hd0,gpt4
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
} 

---

### Post by #&amp;thj^% on 2024-04-28
I'm out now way too many cooks here>

Good Luck

---

### Post by SUPERFITTER on 2024-04-28
```

me@me1:~$ sudo update-grub
[sudo] password for me: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.5.0-28-generic
Found initrd image: /boot/initrd.img-6.5.0-28-generic
Found linux image: /boot/vmlinuz-6.5.0-18-generic
Found initrd image: /boot/initrd.img-6.5.0-18-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Zorin OS 17.1 (17) on /dev/sda2
Found Linux Mint 21.3 Virginia (21.3) on /dev/sda4
done
me@me1:~$ 

```

---

### Post by SUPERFITTER on 2024-04-28
Should I just delete and format Mint and Zorin drives and start over?

---

### Post by SUPERFITTER on 2024-04-28
Should I just stay with one system?

---

### Post by yancek on 2024-04-29
Whether you use only one systems or several is your choice.  What reason would you want to do that?  The problems you are seeing are the result of the default options being changed in the /etc/default/grub file.  You should not have 'hidden' on the TIMEOUT_STYLE line nor should you have  0 on the TIMEOUT line.  The information you posted in your initial post from boot repair shows that the Grub bootloader from the Ubuntu install was being used.  Explained in post 5.   Therefore, all the editing to the various files needed to be done in Ubuntu and as root (using sudo).

Another part of your problem is that you are using an EFI install of Ubuntu and its derivatives which use the directory name "ubuntu" on the EFI partition.  If you install one of the 3 systems you have then install a second, the second will overwrite the ubuntu boot files on the EFI partition which were used by the first.  If you want multiple systems to test/try, don't use other major Ubuntu derivatives.  Some may not overwrite the EFI files but I don't know which do not.

If you are going to test other systems, familiarize yourself with UEFI and check the various options in the BIOS firmware and probably Grub if you plan to use it.  The Grub Manual is available online.  

I'm not sure why you were trying to install Grub again.  Your boot repair showed Grub installed and pointing to sda3 (Ubuntu) and if you had the correct settings in /etc/default/grub for the menu, you should have seen the Grub menu on boot.  Your post 6 is a bit confusing as you seem to indicate you have some sort of menu but say it is not Grub.  Do you have multiple entries for ubuntu in your BIOS UEFI settings?

I asked in post 5 if this triple boot system had ever worked properly and you never responded??

In post 30, you show the output of update-grub run from Ubuntu and it detects both Zorin and MInt so that if you have correct setting in the Ubuntu /etc/default/grub file, you should see them on boot if you have the correct entry for Ubuntu set to first boot priority in the BIOS firmware.  Do you see that?

---

### Post by SUPERFITTER on 2024-04-29
yancek

I never had a Grub menu since I started with a duel boot then moved to a triple boot.  I tried Repair Boot loader:  
sudo apt-add-repository ppa:yannubuntu/boot-repair
 Once the repository is added, update apt with the command:
 sudo apt-get update
 After the apt update completes, install boot-repair with the command:
 sudo apt-get install boot-repair -y
 Start the newly installed app with the command:
 boot-repair

I never had a problem with multi boots on other computers. Some of these places and  commands are new to me, because I have never had this problem in the past.  Any suggestions are welcome. 




```

  GNU nano 6.2                                                                                   /var/tmp/grub.XXuxPMvj                                                                                            
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

```

---

### Post by yancek on 2024-04-29
In your initial post, you asked how to unhide the Grub boot menu for each OS and that was explained to you in the various posts.  You need to edit the /etc/grub/default file so that you do not have 'hidden' on the TIMEOUT_STYLE line nor should you have  0 on the TIMEOUT line.  Since your boot repair info showed the default boot was to Ubuntu on sda3, you should have edited that file on Ubuntu.

You also said you did not have a Grub menu but indicated that you would see some options.  So what was that if not Grub?  Were you selecting from the EFI options in the BIOS firmware?

>  I never had a problem with multi boots on other computers.

Were these other computers UEFI?  Were these other computers with multiple systems all Ubuntu systems?  Have you done any reading to get a basic understanding of UEFI and how it differs from a Legacy boot?

QUESTIONS:  I asked earlier and you did not respons, did this system with Ubuntu, Zorin and Mint ever work so that you could select to boot any of the three??
AGAIN, in post 30 you show the output of update-grub which includes entries for both Zorin and Mint.  Do you have a menu now?
If the /etc/default/grub file you posted in your last post is from Ubuntu, you should see a menu if Ubuntu  is set to boot first in the BIOS.

I'm not sure why you posted an explanation of how you got and ran boot repair?
So what is the status now?  Can you boot Ubuntu?  Does it show a menu?  Are Zorin and Mint on it?  Have all the edits you have done been while booted into the installed Ubuntu system?

---

### Post by SUPERFITTER on 2024-04-29
The computer boots to Ubuntu, but there is no Menu to select Ubuntu, Mint or Zorin and there never was a Menu.  All I want is a Boot Menu.

---

### Post by ajgreeny on 2024-04-30
I suspect that grub is being managed and run from the wrong OS partition and that the /etc/default/grub file you have edited is not the file in use by grub.

Can you show us the /etc/default/grub files from all of the OSs on the machine as that may give us more clues as to what is really going on here.

---

### Post by #&amp;thj^% on 2024-04-30
> **ajgreeny said:**
> I suspect that grub is being managed and run from the wrong OS partition and that the /etc/default/grub file you have edited is not the file in use by grub.


+1, I don't suspect though, three Ubuntu based OS's and knowing grub, that's our culprit here. :)
What was the last OS you installed? We need to know that first, before following my next suggestions.

While on Ubuntu please install "efibootmgr"

Then run it:
```
efibootmgr

```
Paste all that back here

---

### Post by yancek on 2024-04-30
>  I suspect that grub is being managed and run from the wrong OS partition  and that the /etc/default/grub file you have edited is not the file in  use by grub.

Probably which is why I posted what I did in post 5.  I haven't seen a response indicating which OS is being modified.

---

### Post by #&amp;thj^% on 2024-04-30
> **yancek said:**
>  I haven't seen a response indicating which OS is being modified.

OP has said a few times now It boots straight to Ubuntu, But you know how that goes. ;)

---

### Post by dragonfly41 on 2024-05-01
It might help understanding if OP boots up LiveUSB, Try UBuntu, runs gparted, and reports what is seen in each of the three OS partitions, in particular EFI partitions.

---

### Post by yancek on 2024-05-01
>  OP has said a few times now It boots straight to Ubuntu, But you know how that goes.


The boot repair output in the first post indicates that Ubuntu on sda3 is the default but the first direct mention by the OP that it is in fact booting Ubuntu was post 36.  Although asked and never answered, were the modifications/edits done in Ubuntu?

> It might help understanding if OP boots up LiveUSB, Try UBuntu, runs gparted, and reports what is seen in each of the three OS partitions, in particular EFI partitions. 

All that information is in the boot repair output in the initial post and all 3 OS's are on the same drive with only one EFI partition. It also indicates the grub.cfg file on that EFI partition is pointing to Ubuntu on sda3.  Also shown are the Hidden option in the /etc/default/grub file of Zorin and the saved option in the same file on Mint.  I don't believe those are default settings.  Booting into Ubuntu and making the edits there should have resolved the problems but it is an unknown if that was done or what other changes may have been made.

---

### Post by dragonfly41 on 2024-05-01
I see .. > [COLOR=#000000]and all 3 OS's are on the same drive with only one EFI partition.[/COLOR][COLOR=#000000].
Just an observation .. I have triple boot setup and I make a point at LiveUSB time of creating a unique EFI partition for each OS (on a partition or separate SSD in external docking bay/caddy). And also in each EFI partition I install rEFInd. I know that this redundancy isn't necessary and one EFI partition will suffice. [/COLOR]

---

### Post by SUPERFITTER on 2024-05-01
```
me@me1:~$ efibootmgr
BootCurrent: 0001
Timeout: 3 seconds
BootOrder: 0003,0002,0000,0001
Boot0000* EFI DVD/CDROM
Boot0001* OsLoader0000
Boot0002* ubuntu
Boot0003* rEFInd Boot Manager
me@me1:~$ 

```

---

### Post by #&amp;thj^% on 2024-05-01
**EDIT: I'll assume you now have good back-ups in place before proceeding with my suggestions below.**

This should get you to Ubuntu first, and then as a second option shows rEFInd
```
 sudo efibootmgr -o 0002 0003
``` 
Now reboot, Do you now have a Grub menu?

I have not seen an entry like you now show>>>"Boot0001* OsLoader0000"

---

### Post by SUPERFITTER on 2024-05-01
1fallen

Sorry no Grub menu, straight into Ubuntu.

---

### Post by dragonfly41 on 2024-05-01
When you reboot and immediately go into BIOS (hit F2 ??) what options do you see in boot order?
Any other settings in there report back.

---

### Post by SUPERFITTER on 2024-05-01
My BIOS

---

### Post by #&amp;thj^% on 2024-05-01
That Picture is way to small for my aging eyes :)

Do you have a boot priority with F12 when  immediately booting up? (Spam your F12 when it first begins to restart)

EDIT I did see First Boot device is a USB drive, not what we want though.

---

### Post by dragonfly41 on 2024-05-01
[SIZE=4]**+1**[/SIZE] "That Picture is way to small for my aging eyes"

Take time to write it down for old codgers like me.

---

### Post by dragonfly41 on 2024-05-01
This is what I see when I bootup Dell Inspiron using F2. A few minutes ago.
Left panel:
Settings
    |
    General
        - System Information
        - Boot Sequence
        
        
Right Panel (see below)


Boot sequences


[LIST]
[*]&#9745; rEFInd Boot Manager
[*]&#9744; Windows Boot Manager
&#9744; Ubuntu-SATA-HD
[*]&#9745; ubuntu
[*]&#9745; ubuntu
[*]&#9745; USB1
[*]&#9745; USB2
[/LIST]
[TABLE="class: table"]
[TR]
[TH]rEFInd boot manager[/TH]
[/TR]
[TR]
[TD]ubuntu[/TD]
[/TR]
[TR]
[TD]ubuntu[/TD]
[/TR]
[TR]
[TD]USB1[/TD]
[/TR]
[TR]
[TD]USB2[/TD]
[/TR]
[/TABLE]


The lower case &#8220;ubuntu's&#8221; are in fact Ubuntu 20.04 and Ubuntu 22.04. Windows appears with two versions of Ubuntu in one GUI. Simples.
To find the appropriate boot loader you click on &#8220;Add Boot Option&#8221; although the long names are dificult to decipher - so some trial and error.
Finally
Boot List Options

[LIST]
[*]&#9744; Legacy
[*]&#9745; UEFI
[/LIST]
Your BIOS might differ from Dell Inspiron.

Take note that rEFInd should be a top of boot options. I have other USB expanders seen in list.

---

### Post by SUPERFITTER on 2024-05-01
> **1fallen said:**
> That Picture is way to small for my aging eyes :)

Do you have a boot priority with F12 when  immediately booting up? (Spam your F12 when it first begins to restart)

EDIT I did see First Boot device is a USB drive, not what we want though.

I changed boot order to SSD first.

---

### Post by dragonfly41 on 2024-05-01
Did you **see** rEFInd as top boot option?

---

### Post by SUPERFITTER on 2024-05-01
I never got rEFInd to install.

Would it be faster to just reinstall Mint and Zorin.  They were just fresh installs that I must have just messed up on after I tried to get the Boot Menu?

---

### Post by dragonfly41 on 2024-05-01
Reinstall rEFInd from LiveUSB. ReInstall REFInd into one of your SSD's EFI partition. I presume you have set boot flags in EFI partition which is why I suggested GParted to inspect. And you have ignored request to show BIOS (other than a difficult to read photo).

---

### Post by #&amp;thj^% on 2024-05-01
My rEFInd thumb drive shows as 
```
Boot0002* EFI USB Device (SanDisk Cruzer U)	UsbWwid(781,55a5,0,20053954100F1DB33DE)/HD(1,GPT,eb0ef56a-4816-4dd1-9067-dfd783891989,0x800,0x301f)RC
```

EDIT OR
```
 sudo blkid | grep /dev/sdc1
/dev/sdc1: SEC_TYPE="msdos" LABEL_FATBOOT="ElTorito" LABEL="ElTorito" UUID="BF5A-E479" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="eb0ef56a-4816-4dd1-9067-dfd783891989"

```

---

### Post by SUPERFITTER on 2024-05-01
> **dragonfly41 said:**
> Reinstall rEFInd from LiveUSB. ReInstall REFInd into one of your SSD's EFI partition. I presume you have set boot flags in EFI partition which is why I suggested GParted to inspect. And you have ignored request to show BIOS (other than a difficult to read photo).

REFInd will not boot, times out and reboots Ubuntu.

---

### Post by #&amp;thj^% on 2024-05-01
> **SUPERFITTER said:**
> REFInd will not boot, times out and reboots Ubuntu.

Then something is amuck, I had asked you a while back>>>Is the Thumb drive formatted as Fat32?
With no clear answer....

---

### Post by ajgreeny on 2024-05-01
> **1fallen said:**
> OP has said a few times now It boots straight to Ubuntu, But you know how that goes. ;)
As we know, or at least I think we can say that we know with some certainty that the machine now just boots to Ubuntu each time, I wonder if it is worth running the command from the Ubuntu terminal to make sure that grub is managed by the Ubuntu OS and not some other currently unknown OS.
```
sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi \    --bootloader-id=ubuntu --recheck --no-floppy
```
After doing that /etc/default/grub could be edited again to ensure that the important lines are correct to get grub show every time if he wants it, ie 
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-22-04"  # My own edit to show the real OS, not just another Ubuntu listed.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false  # or true if you prefer.
```

---

### Post by SUPERFITTER on 2024-05-01
Thumb drive is formatted as Fat32.  When I put REFInd on it, it changes to this:

---

### Post by #&amp;thj^% on 2024-05-01
> **SUPERFITTER said:**
> Thumb drive is formatted as Fat32.  When I put REFInd on it, it changes to this:

Yep that looks right, will you just to be sure show me this currently:
```
 sudo blkid | grep /dev/sdh1
```

---

### Post by SUPERFITTER on 2024-05-01
```

me@me1:~$  sudo blkid | grep /dev/sdh1
[sudo] password for me: 
/dev/sdh1: SEC_TYPE="msdos" LABEL_FATBOOT="ElTorito" LABEL="ElTorito" UUID="BF5A-E479" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="eb0ef56a-4816-4dd1-9067-dfd783891989"
me@me1:~$ 

```

---

### Post by #&amp;thj^% on 2024-05-01
Ok Thanks, I'm going to suggest a possible show stopper now so you been warned.

But first see ajgreeny's and use his post #59
Now after that is done with no errors shown, please run this:
```
sudo efibootmgr --delete-bootnum --bootnum 0001
```
Reboot and fingers crossed.

---

### Post by SUPERFITTER on 2024-05-01
```

me@me1:~$ sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi \    --bootloader-id=ubuntu --recheck --no-floppy
[sudo] password for me: 
Installing for x86_64-efi platform.
Installation finished. No error reported.
me@me1:~$ sudo efibootmgr --delete-bootnum --bootnum 0001
BootCurrent: 0001
Timeout: 3 seconds
BootOrder: 0002,0003,0000
Boot0000* EFI DVD/CDROM
Boot0002* ubuntu
Boot0003* rEFInd Boot Manager
me@me1:~$ 


```

---

### Post by SUPERFITTER on 2024-05-01
Rebooted twice no Grub, booted back to Ubuntu.

---

### Post by #&amp;thj^% on 2024-05-01
Look again at:
```
less /etc/default/grub
```

Your machine is possessed....

---

### Post by SUPERFITTER on 2024-05-01
My problems started when I switched to a SSD from a HDD, I don't know why?


```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER=false

~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)

```

---

### Post by #&amp;thj^% on 2024-05-01
Looks like a re-install might be needed then..

Wait for our very wise oldfred to have a peek first.

---

### Post by SUPERFITTER on 2024-05-01
Thank You

How old is very wise oldfred?  
I'm 73 I hope he is younger than me (LOL)!

---

### Post by #&amp;thj^% on 2024-05-01
Your Very Welcome....I was hoping for a better outcome though. :(

---

### Post by dragonfly41 on 2024-05-01
Just guesswork  but since SSD was mentioned (HDD installation was o.k. I understand) does this separate thread raise any clue? Or a red herring?

[https://ubuntuforums.org/showthread.php?t=2342662](https://ubuntuforums.org/showthread.php?t=2342662)

I've read about Zorin now so at least I'm better informed.
[COLOR=#000000]


[/COLOR]

---

### Post by yancek on 2024-05-01
>  GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10

Above is your output of the  Ubuntu /etc/default/grub file which you posted in post 67.   That is the default and should allow the user to see a menu on boot.

>  Found Zorin OS 17.1 (17) on /dev/sda2
Found Linux Mint 21.3 Virginia (21.3) on /dev/sda4

Above is the output when you ran sudo update-grub while booted into Ubuntu which was in post 30.  That should put the Zorin and Mint entries in the Ubuntu grub.cfg menu.  When you boot into Ubuntu, go to the /boot/grub/grub.cfg file and see if those entries (Zorin and Mint) exist in that file.

You have indicated several times that you have no "grub' menu but apparently see somethng on screen when booting to make a selection.  Is that the case or have I not read correctly?  If it is the case, could you use a smart phone or digital camera to take a photo of the screen and post it here.  Or are you blindly hitting the down arrow key and then enter to see what happens?

---

### Post by SUPERFITTER on 2024-05-03
After wasting four hours reinstalling the three systems, I could not boot any of them.  
I formatted all of them and tried one at a time to see if they would boot after installation.  
I finally got Mint to work.  
I updated it and rebooted and it works. I'm going to stick with one system for now.
I loaded rEFind Boot Manager from a different computer and installed it to a Thumb Drive that was formatted to Fat32 same results as previously posted.

Thank you for the help!

---

### Post by #&amp;thj^% on 2024-05-03
Wise to stay with one OS.

If you want to play with more than one OS use KVM (Virt-manager) or Vbox it's much safer that way. :)

---

