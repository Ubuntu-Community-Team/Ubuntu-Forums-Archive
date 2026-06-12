---
title: "Access Lost After Bios Upgrade"
date: 2022-04-27
forum: General Help
---

### Post by cryptojim on 2022-04-27
I am a newbie and just upgraded by Bios in Dell Laptop running Ubuntu 20.10

Now I can't boot up.  

I was on legacy mode as I coulldn't get UEFI to boot.  Now neither one works.  

Here is my file from disk-repair but I don't know how to implement the recommended solutions.  

```
boot-repair-4ppa200                                              [20220427_1934]


============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for 
    (lvmid/Kez0Is-R1T3-thL3-ympb-c4gw-UHP4-G5VdSv/zhyRSm-yQT5-NDHt-h9Nh-A1t2-Xk
    7P-27NOZE)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter lvm biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.


nvme0n1p1: _____________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


nvme0n1p2: _____________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


nvme0n1p5: _____________________________________________________________________


    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sda1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys




================================ 1 OS detected =================================


OS#1:   Ubuntu 21.10 on mapper/vgubuntu-root


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.6.0 from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled but mokutil says: SecureBoot enabled - Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL].
Timeout: 0 seconds
BootOrder: 0001,0002
Boot0001  Onboard NIC (IPV4)     PciRoot(0x0)/Pci(0x1,0x6)/Pci(0x0,0x0)/MAC(98e743491a06,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002  Onboard NIC (IPV6)     PciRoot(0x0)/Pci(0x1,0x6)/Pci(0x0,0x0)/MAC(98e743491a06,0)/IPv6([::]:<->[::]:,0,0)RC




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : notGPT,    no-BIOSboot,    has-noESP,     usb-disk,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
nvme0n1    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


mapper/vgubuntu-root    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    not-far
nvme0n1p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


mapper/vgubuntu-root    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


mapper/vgubuntu-root    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1


fdisk -l (filtered): ___________________________________________________________


Disk nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 0xc7a2173a
          Boot   Start        End   Sectors   Size Id Type
nvme0n1p1 *       2048    1050623   1048576   512M  b W95 FAT32
nvme0n1p2      1052670 1000214527 999161858 476.4G  5 Extended
nvme0n1p5      1052672 1000214527 999161856 476.4G 8e Linux LVM
Disk mapper/vgubuntu-root: 475.5 GiB, 510539071488 bytes, 997146624 sectors
Disk mapper/vgubuntu-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Disk sda: 7.6 GiB, 8178892800 bytes, 15974400 sectors
Disk identifier: 0x04be1d0c
      Boot Start      End  Sectors  Size Id Type
sda1  *     2048 15974399 15972352  7.6G  c W95 FAT32 (LBA)
Disk zram0: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram1: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram2: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram3: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram4: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram5: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram6: 368.9 MiB, 386752512 bytes, 94422 sectors
Disk zram7: 368.9 MiB, 386752512 bytes, 94422 sectors


parted -lm (filtered): _________________________________________________________


sda:8179MB:scsi:512:512:msdos:Generic Flash Disk:;
1:1049kB:8179MB:8178MB:fat32::boot, lba;
mapper/vgubuntu-swap_1:1028MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:1028MB:1028MB:linux-swap(v1)::;
mapper/vgubuntu-root:511GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:511GB:511GB:ext4::;
nvme0n1:512GB:nvme:512:512:msdos:PM991 NVMe Samsung 512GB:;
1:1049kB:538MB:537MB:fat32::boot;
2:539MB:512GB:512GB:::;
5:539MB:512GB:512GB:::lvm;


blkid (filtered): ______________________________________________________________


NAME                FSTYPE      UUID                                   PARTUUID                             LABEL       PARTLABEL
sda                                                                                                                     
&#9492;&#9472;sda1              vfat        06F5-8AE5                              04be1d0c-01                          BOOT-REPAIR 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1         vfat        3E1C-F5E8                              c7a2173a-01                                      
&#9500;&#9472;nvme0n1p2                                                            c7a2173a-02                                      
&#9492;&#9472;nvme0n1p5         LVM2_member eWE7Vi-j61i-Zm8M-VHlf-MOjf-1ylb-eDPTAB c7a2173a-05                                      
  &#9500;&#9472;vgubuntu-root   ext4        8effd1d9-af94-4d8b-9b12-a593cfb6090d                                                    
  &#9492;&#9472;vgubuntu-swap_1 swap        de51b6ca-38a8-44a9-86f1-101949b60c8b                                                    


Mount points (filtered): _______________________________________________________


                           Avail Use% Mounted on
/dev/mapper/vgubuntu-root 290.1G  33% /mnt/boot-sav/mapper/vgubuntu-root
/dev/sda1                   6.8G  11% /cdrom


Mount options (filtered): ______________________________________________________


/dev/mapper/vgubuntu-root ext4            rw,relatime
/dev/sda1                 vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


============================== ls -R /dev/mapper/ ==============================


/dev/mapper:
control
vgubuntu-root
vgubuntu-swap_1


====================== sda1/boot/grub/grub.cfg (filtered) ======================


Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)


========================= sda1/syslinux.cfg (filtered) =========================


DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/


==================== sda1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================== sda1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1




==================== blkid (filtered) before lvm activation ====================


/dev/mapper/vgubuntu-root: UUID="8effd1d9-af94-4d8b-9b12-a593cfb6090d" TYPE="ext4"
/dev/nvme0n1p1: UUID="3E1C-F5E8" TYPE="vfat" PARTUUID="c7a2173a-01"
/dev/sda1: LABEL="BOOT-REPAIR" UUID="06F5-8AE5" TYPE="vfat" PARTUUID="04be1d0c-01"
/dev/nvme0n1p5: UUID="eWE7Vi-j61i-Zm8M-VHlf-MOjf-1ylb-eDPTAB" TYPE="LVM2_member" PARTUUID="c7a2173a-05"
/dev/mapper/vgubuntu-swap_1: UUID="de51b6ca-38a8-44a9-86f1-101949b60c8b" TYPE="swap"
/dev/zram0: UUID="c44db8ac-2f12-4b8b-bb69-6e02f46ed905" TYPE="swap"
/dev/zram1: UUID="db71373d-c875-48db-a415-e41445e46527" TYPE="swap"
/dev/zram2: UUID="bff7a7e7-bb52-4492-9790-865a10ccfac8" TYPE="swap"
/dev/zram3: UUID="be548dd5-eb0c-48a3-ad4d-cfe21e321767" TYPE="swap"
/dev/zram4: UUID="92e0bdb5-ebb8-4aa8-be55-36f6717a5fb2" TYPE="swap"
/dev/zram5: UUID="0e9c4140-5931-4ce9-9085-d587c06fafb8" TYPE="swap"
/dev/zram6: UUID="4b959858-d8a1-4e40-915e-cb44f7292e47" TYPE="swap"
/dev/zram7: UUID="360faad8-79f8-49ed-8fce-f5467a3cb638" TYPE="swap"
/dev/nvme0n1: PTUUID="c7a2173a" PTTYPE="dos"




================================ LVM activation ================================


modprobe dm-mod  
vgscan --mknodes
  Reading volume groups from cache.
  Found volume group "vgubuntu" using metadata type lvm2
vgchange -ay
  2 logical volume(s) in volume group "vgubuntu" now active
lvscan
  ACTIVE            '/dev/vgubuntu/root' [<475.48 GiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [980.00 MiB] inherit
blkid -g






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility will purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of
mapper/vgubuntu-root,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file






Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 21.10 entry (nvme0n1p1/efi/****/shim****.efi (**** will be updated in the final message) file) !
```

---

### Post by oldfred on 2022-04-27
It looks like your UEFI/BIOS update reset things to defaults which is common.
You have to go back & reset all the settings you changed originally  to install Ubuntu. I have multiple settings and have to keep a list.

Report shows you booted live installer in UEFI mode, but have BIOS/CSM/Legacy install on a MBR(msdos) partitioned drive.
And now UEFI Secure Boot is on, which locks out BIOS mode. You may also need to change drives to AHCI and some other settings in UEFI.

Better to use UEFI with UEFI systems. Long term you may want to change. But for now only boot in BIOS mode.
When you booted live installer in UEFI mode, it may want to make UEFI repairs, which would complicate things. So always boot in BIOS mode.

---

### Post by cryptojim on 2022-04-27
Thanks for this reply.  
So I put everything back to legacy which is to the best of my knowledge the way it was.  
It is still not seeing the SSD drive.  Is there any recovery that I can do besides fiddling with the Bios settings?

---

### Post by oldfred on 2022-04-27
Did you check the drive settings, should be AHCI, not Intel RST nor RAID.

Please do not post long terminal output. And post terminal output in code tags.
Easy to add code tags with Forum's advanced editor and # icon.

Boot-Repair suggests you just post the link to the pastebin site it can upload to.

---

