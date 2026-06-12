---
title: "how to configure grub to boot on windows 11"
date: 2023-12-29
forum: General Help
---

### Post by rodride on 2023-12-29
hi,

I have ubuntu and windows 11 on my pc. After installing windows 11, I can't add it to the grub menu.

The partition table for "ubuntu" and "windows 11" disks is GPT
My bios is legacy+uefi

my windows partitions :
```

sudo blkid |grep /dev/sdb
/dev/sdb2: BLOCK_SIZE="512" UUID="76ECEA39ECE9F373" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="65dec1f3-e0a8-4550-b2bb-302075da6631"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="c11d658b-62b7-4710-a923-b38c57d1d123"

```

Thanks for your help

---

### Post by ajgreeny on 2023-12-29
What exactly do you mean by "My bios is legacy+uefi"?
Your Windows must be in UEFI mode but is your Ubuntu also installed in UEFI mode?

If not you will not be able to boot both OSs from grub.

See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2023-12-29
You need to run the boot repair with the Create BootINfo Summary option as the information you posted is too minimal to make reasonable suggestions.  Are  windows and Ubuntu installed on separate disks?  Do you know if they are both installed in UEFI mode?  After installing windows, did you access the BIOS firmware to select the Ubuntu drive as first in boot priority to try to boot it?  If so, what happened?  If not, that would be the first thing to try.  If you are able to boot Ubuntu, run:  sudo update-grub and watch the output for a windows entry.  If you have them on separate hard drives, you should also be able to access either from your BIOS firmware boot options.

---

### Post by rodride on 2023-12-30
This is boot-info result :

```

boot-repair-4ppa2075                                              [20231230_1652]

============================== Boot Info Summary ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Noble Numbat (development branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sdb2 has 
                       1565530111 sectors, but according to the info from 
                       fdisk, it has 5860497407 sectors.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        


================================ 2 OS detected =================================

OS#1:   L'OS actuellement utilisé - Ubuntu Noble Numbat on sda5
OS#2:   Windows 8 or 10 on sdb2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GM204 [GeForce GTX 970] VESA VGA from NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.6.8-060608-generic root=UUID=b489f8cf-e3be-4e67-8f46-f25f9ddccd0c ro quiet loglevel=2 splash rd.driver.blacklist=nouveau nvidia-drm.modeset=0 vt.handoff=7
df -Th / : /dev/sda5        ext4    54G     31G   21G  60% /

===================================== UEFI =====================================

BIOS/UEFI firmware: V3.10(4.6) from American Megatrends Inc.
The firmware is EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).


c152ec201c37b6e97bbc2207e49d1271   sda4/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda4/BOOT/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sda4/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda4/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda4/ubuntu/shimx64.efi
2a3bd52fec672a1f1364ca9b41553f4d   sda4/Microsoft/Boot/bootmgfw.efi
219a45fc0b91c22521a72dffdcbac5d4   sda4/Microsoft/Boot/bootmgr.efi
728124f6ec8e22fbdbe7034812c81b95   sda4/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdf    : notGPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, no-os,    no-wind,    63 sectors * 512 bytes
sdd    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sde    : notGPT,    no-BIOSboot,    has-noESP,     liveusb,    not-mmc, no-os,    no-wind,    32 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ng,    update-grub,    not-far
sdf1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdd1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sde1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdf1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdd1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sde1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdf1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdf
sdd1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdd
sdb2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sde1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sde
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 2.73 TiB, 3000592982016 bytes, 5860533168 sectors
Disk identifier: 46B28EEE-284B-479D-BC3C-FA4D52071719
         Start        End    Sectors  Size Type
sda1       2048    3999743    3997696  1.9G BIOS boot
sda2  121630720  138407935   16777216    8G Linux swap
sda3  138407936 5860532935 5722125000  2.7T Linux filesystem
sda4    3999744    6000639    2000896  977M EFI System
sda5    6000640  121630719  115630080 55.1G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 2.73 TiB, 3000592982016 bytes, 5860533168 sectors
Disk identifier: D37EA1CE-A6DD-4355-9DE6-281280F3B4B7
     Start        End    Sectors  Size Type
sdb1   2048      34815      32768   16M Microsoft reserved
sdb2  34816 5860532223 5860497408  2.7T Microsoft basic data
Disk sdc: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 329589E6-065F-45B1-9951-037F86B691CD
     Start        End    Sectors  Size Type
sdc1   2048 3907026943 3907024896  1.8T Microsoft basic data
Disk sdd: 3.64 TiB, 4000752599040 bytes, 7813969920 sectors
Disk identifier: 3DC8F422-31B2-4E6F-BDFA-5272D40B1C25
     Start        End    Sectors  Size Type
sdd1   2048 7813967871 7813965824  3.6T Linux filesystem
Disk sde: 28.82 GiB, 30943995904 bytes, 60437492 sectors
Disk identifier: 0x62a06c4a
     Boot Start      End  Sectors  Size Id Type
sde1          32 30719775 30719744 14.6G  7 HPFS/NTFS/exFAT
Disk sdf: 57.62 GiB, 61872793600 bytes, 120845300 sectors
Disk identifier: 0x7c5c07c0
     Boot Start       End   Sectors  Size Id Type
sdf1  *       63 120845087 120845025 57.6G  7 HPFS/NTFS/exFAT
Disk zram0: 15.64 GiB, 16791654400 bytes, 4099525 sectors

parted -lm (filtered): _________________________________________________________

sda:3001GB:scsi:512:4096:gpt:ATA WDC WD30EZRX-00D:;
1:1049kB:2048MB:2047MB:::bios_grub;
4:2048MB:3072MB:1024MB:fat32::boot, esp;
5:3072MB:62.3GB:59.2GB:ext4::;
2:62.3GB:70.9GB:8590MB:linux-swap(v1)::swap;
3:70.9GB:3001GB:2930GB:ext4::;
sdb:3001GB:scsi:512:4096:gpt:ATA ST3000DM007-2U91:;
1:1049kB:17.8MB:16.8MB::Microsoft reserved partition:msftres, no_automount;
2:17.8MB:3001GB:3001GB:ntfs::msftdata;
sdc:2000GB:scsi:512:4096:gpt:ATA ST2000DM006-2DM1:;
1:1049kB:2000GB:2000GB:ntfs:Basic data partition:msftdata;
sdd:4001GB:scsi:512:4096:gpt:WD Elements 2620:;
1:1049kB:4001GB:4001GB:ext4:Elements:;
sde:30.9GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:16.4kB:15.7GB:15.7GB:::;
sdf:61.9GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:32.3kB:61.9GB:61.9GB:::boot;

Free space >10MiB: ______________________________________________________________

sde: 15000MiB:29510MiB:14511MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE UUID                                 PARTUUID                             LABEL        PARTLABEL
sda                                                                                                  
&#9500;&#9472;sda1                                             38f0685f-1a39-4d1b-9294-ddbcda6fe650              
&#9500;&#9472;sda2 swap   3fce2b54-c78a-4898-9460-acd88c15ad44 c37b3e25-27cf-4a31-9995-d511e3001831              
&#9500;&#9472;sda3 ext4   e6001b25-54bd-4ac1-8ccb-0c8b9ed7d285 c802fc71-c52a-4cec-9ec1-270a8de51905              
&#9500;&#9472;sda4 vfat   8DD5-0BDE                            67c664f0-7ce2-4474-bd9a-0c9591a25104              
&#9492;&#9472;sda5 ext4   b489f8cf-e3be-4e67-8f46-f25f9ddccd0c 8bb0828a-e375-4fef-94ba-0382d49d4b41              
sdb                                                                                                  
&#9500;&#9472;sdb1                                             c11d658b-62b7-4710-a923-b38c57d1d123              Microsoft reserved partition
&#9492;&#9472;sdb2 ntfs   76ECEA39ECE9F373                     65dec1f3-e0a8-4550-b2bb-302075da6631              Basic data partition
sdc                                                                                                  
&#9492;&#9472;sdc1 ntfs   88F099A3F0999850                     a11d17af-60ec-4f8d-93ce-50f926595f7a Disque local Basic data partition
sdd                                                                                                  
&#9492;&#9472;sdd1 ext4   bf06a4ae-e85f-4a87-9748-27c2250a90dd 7a0f3373-637f-4599-9511-a3519572ca34 WD4To        Elements
sde                                                                                                  
&#9492;&#9472;sde1 exfat  CEDB-B1C8                            62a06c4a-01                          EU2022       
sdf                                                                                                  
&#9492;&#9472;sdf1 exfat  92E8-1F58                            7c5c07c0-01                          KINGSTON64   

Mount points (filtered): _______________________________________________________

                  Avail Use% Mounted on
/dev/sda3          1.7T  28% /home
/dev/sda4        943.1M   3% /mnt/boot-sav/sda4
/dev/sda5         20.6G  57% /
/dev/sda5[/snap]  20.6G  57% /snap
/dev/sdb2          2.7T   3% /mnt/boot-sav/sdb2
/dev/sdc1          1.8T   2% /mnt/boot-sav/sdc1
/dev/sdd1          2.8T  17% /media/filip/WD4To
/dev/sde1          4.3G  70% /media/filip/EU2022
/dev/sdf1         56.2G   3% /media/filip/KINGSTON64

Mount options (filtered): ______________________________________________________

/dev/sda3        ext4            rw,relatime,stripe=32750
/dev/sda4        vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda5        ext4            rw,relatime,errors=remount-ro
/dev/sdb2        fuseblk         ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc1        fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdd1        ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sde1        exfat           rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,iocharset=utf8,errors=remount-ro
/dev/sdf1        exfat           rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,iocharset=utf8,errors=remount-ro

===================== sda4/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid b489f8cf-e3be-4e67-8f46-f25f9ddccd0c root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   b489f8cf-e3be-4e67-8f46-f25f9ddccd0c
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=b489f8cf-e3be-4e67-8f46-f25f9ddccd0c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
# /home was on /dev/sda3 during installation
UUID=e6001b25-54bd-4ac1-8ccb-0c8b9ed7d285 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=3fce2b54-c78a-4898-9460-acd88c15ad44 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=2 splash rd.driver.blacklist=nouveau nvidia-drm.modeset=0"
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX="keep"
GRUB_VIDEO_BACKEND="vbe"
GRUB_BACKGROUND="/boot/grub/linux.png"
GRUB_FONT=/boot/grub/fonts/terminus.pf2 
GRUB_GFXMODE=2560x1440x32
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   4.189407349 = 4.498341888    boot/grub/grub.cfg                             1
  55.490928650 = 59.582930944   boot/grub/i386-pc/core.img                     1
  40.421871185 = 43.402653696   boot/vmlinuz                                   2
  38.429302216 = 41.263149056   boot/vmlinuz-6.6.8-060608-generic              1
  40.421871185 = 43.402653696   boot/vmlinuz-6.6.8-rt18                        2
  38.429302216 = 41.263149056   boot/vmlinuz.old                               1
  49.931636810 = 53.613686784   boot/initrd.img                               40
  20.054447174 = 21.533298688   boot/initrd.img-6.6.8-060608-generic           5
  49.931636810 = 53.613686784   boot/initrd.img-6.6.8-rt18                    40
  20.054447174 = 21.533298688   boot/initrd.img.old                            5

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18228 Nov  9 15:16 10_linux
-rwxr-xr-x 1 root root 43202 Nov  9 15:16 10_linux_zfs
-rwxr-xr-x 1 root root 14459 Nov  9 15:16 20_linux_xen
-rwxr-xr-x 1 root root   786 Nov  9 15:16 25_bli
-rwxr-xr-x 1 root root 13120 Nov  9 15:16 30_os-prober
-rwxr-xr-x 1 root root  1174 Nov  9 15:16 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Nov 14 19:02 35_fwupd.dpkg-dist
-rwxr-xr-x 1 root root   214 Dec 30 16:49 40_custom
-rwxr-xr-x 1 root root   215 Dec  2  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi of
sda5,
using the following options:  sda4/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

WindowsEFI detected. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), after making sure your BIOS is set up to boot USB in EFI mode. 

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the L'OS actuellement utilisé - Ubuntu Noble Numbat entry (sda4/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.

```

---

### Post by tea for one on 2023-12-30
Looks like mixed mode installations.
More info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

```
sda1:     File system:       BIOS Boot partition
```
The presence of this partition indicates that you installed Ubuntu Noble Numbat (development branch) in Legacy mode.
```
The firmware is EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).
```
This line confirms the above.

```
WindowsEFI detected. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware
```
Your ESP partition sda4 contains the necessary boot files for both Ubuntu and Windows.
Therefore, boot Ubuntu in [COLOR="#0000FF"]UEFI[/COLOR] mode, open a terminal and enter:-
```
sudo update-grub
```
Did grub find Windows Boot Manager?

For the future, it is better to have an ESP on each disk to allow independent OS operation.

---

### Post by yancek on 2023-12-30
It is a bit odd that you have your EFI partition on sda4 with both Ubuntu and windows EFI files.  Particularly so since windows is installed on another drive (sdb).  Usually the EFI partition is the first or second partition on the drive.  If you had a Legacy install of Ubuntu on one drive and an EFI partition of windows on another drive, my experience would be that the Ubuntu Grub would boot windows on the other drive.  This is complicated by the EFI file for windows being on the Ubuntu drive and I don't think that will work.  Not sure how you managed this.

---

### Post by MAFoElffen on 2023-12-31
I read Post #6 and that is not exactly what I see. It may be installed as mixed mode... But there are some very odd things going on with that.

Please boot it from the LiveUSB if UEFI mode and do this
```

sudo efibootmgr -v

```
And please answer which version of  Windows is installed, and on which Boot mode if you remember that.
```

sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

```
Windows is installed on /dev/sdb, which has a GPT partition table... Which means it was most likely installed as UEFI boot mode.

It looks like if you just reset your UEFI BIOS to boot as UEFI boot mode, it might just boot fine.

---

### Post by rodride on 2024-01-03
I solved my problem by switching to UEFI and reinstalled grub with boot-repair.
Now I can boot on windows from the grub menu.
Thanks for your help

---

