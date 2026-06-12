---
title: "Boot repair - how to proceed?"
date: 2024-01-24
forum: General Help
---

### Post by mdevon on 2024-01-24
Hi my Ubuntu stopped booting, boot-repair generates the following:
```
boot-repair-4ppa2075                                              [20240125_0103]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on sda1

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.2 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.00(4.6) from American Megatrends Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ng,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk identifier: 0x14eb2669
       Boot Start     End Sectors  Size Id Type
loop6p1 *        0 5138431 5138432  2.5G  0 Empty
loop6p2        572    9067    8496  4.2M ef EFI (FAT-12/16/32)
Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x00011b35
     Boot     Start       End   Sectors   Size Id Type
sda1  *         2048 943448063 943446016 449.9G 83 Linux
sda2       943450110 976771071  33320962  15.9G  5 Extended
sda5       943450112 976771071  33320960  15.9G 82 Linux swap / Solaris
Disk sdb: 7.62 GiB, 8166703104 bytes, 15950592 sectors
Disk identifier: 0x03eb95f8
     Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 15950591 15948544  7.6G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:msdos:ATA Samsung SSD 850:;
1:1049kB:483GB:483GB:ext4::boot;
2:483GB:500GB:17.1GB:::;
5:483GB:500GB:17.1GB:linux-swap(v1)::;
sdb:8167MB:scsi:512:512:msdos:PNY USB 2.0 FD:;
1:1049kB:8167MB:8166MB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME      FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                                 
&#9500;&#9472;sda1    ext4     f33e33c3-a54e-4c53-975d-a0f5f3deb212 00011b35-01                                                 
&#9500;&#9472;sda2                                                  00011b35-02                                                 
&#9492;&#9472;sda5    swap     660e555b-e399-453c-bd48-83cc6b73aa2d 00011b35-05                                                 
sdb                                                                                                                 
&#9492;&#9472;sdb1    vfat     AE2B-7301                            03eb95f8-01                          UBUNTU 20_0            

Mount points (filtered): _______________________________________________________

                       Avail Use% Mounted on
/dev/sda1               225G  44% /media/ubuntu/f33e33c3-a54e-4c53-975d-a0f5f3deb212
/dev/sdb1              74.4M  99% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1              ext4            rw,nosuid,nodev,relatime
/dev/sdb1              vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda1/boot/grub/grub.cfg (filtered) ======================

Ubuntu   f33e33c3-a54e-4c53-975d-a0f5f3deb212
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda1/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f33e33c3-a54e-4c53-975d-a0f5f3deb212 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=660e555b-e399-453c-bd48-83cc6b73aa2d none            swap    sw              0       0

======================= sda1/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   5.130393982 = 5.508718592    boot/grub/grub.cfg                             1
  80.271125793 = 86.190465024   boot/grub/i386-pc/core.img                     1
 319.313472748 = 342.860230656  boot/vmlinuz                                   2
  49.238357544 = 52.869283840   boot/vmlinuz-5.15.0-89-generic                 1
 319.313472748 = 342.860230656  boot/vmlinuz-5.15.0-91-generic                 2
  49.238357544 = 52.869283840   boot/vmlinuz.old                               1
 157.280914307 = 168.879095808  boot/initrd.img                                4
 206.547847748 = 221.779062784  boot/initrd.img-5.15.0-89-generic              6
 157.280914307 = 168.879095808  boot/initrd.img-5.15.0-91-generic              4
 206.547847748 = 221.779062784  boot/initrd.img.old                            6

===================== sda1: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 17  2015 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to reset grubenv) and reinstall the grub2 of
sda1 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Final advice in case of suggested repair: ______________________________________


The boot files of [sda1 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

```

Any advice would be appreciated

---

### Post by TheFu on 2024-01-27
> Any advice would be appreciated 

The output is hard to read because you didn't wrap it in forum code tags.  Edit the post above, use the "Advanced Editor" and select all the output from the report, press the "#" button like you would the bold or quote buttons and that will make everything line up.

Don't make helping you hard.  That's my first advice.

---

### Post by ajgreeny on 2024-01-27
I have added the code tags for you so you can see the difference it makes to the text layout.

In future please always use code tags for any terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 
See my signature below for a **How-to** of Code-Tags

---

