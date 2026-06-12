---
title: "Suddenly secure boot failing. Am I compromised"
date: 2023-12-01
forum: General Help
---

### Post by xhadesx on 2023-12-01
Hi everyone, sorry if this is a stupid thing to ask but I suddenly found things going haywire last night after I found myself facing the no bootable device found screen. So I got into BIOS and could only get in after I changed it to legacy. There's reason to suspect that someone must have did something on my PC for this to happen. So I reinstalled my OS and then went back to sleep, thinking that the reinstall would actually take care of restoring bios settings and such but it did not and upon waking I checked and it was still legacy but changing it back is again causing the same issue. 

I booted up from the usb and ran boot-repair but it didn't really work, I'm posting the boot- repair summary below. Can anyone please help me find out what's going on and also help restore things to normal? I have just so much of work to do on my poor old potato and this is stressing me out real bad! Appreciate any help

```
boot-repair-4ppa2056                                              [20231201_1050]

============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt3)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg


sda3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb: ___________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg




================================ 1 OS detected =================================


OS#1:   Ubuntu 22.04.3 LTS on sda3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: HD Graphics 5500 GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] from Intel Corporation NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.2.0-37-generic root=UUID=d9aedf79-b930-432e-87e9-051dbe36930e ro quiet splash vt.handoff=7
df -Th / : /dev/sda3      ext4  916G   75G  795G   9% /


===================================== UEFI =====================================


BIOS/UEFI firmware: V1.26(1.26) from Insyde Corp.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,2002,2003
Boot0000* USB HDD: SanDisk    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/USB(3,0)/HD(2,GPT,328732d6-c6b7-49a2-9168-7be57d174978,0x5ab468,0x2754)RC
Boot0001* Unknown Device:     HD(2,GPT,9d8bb3e9-b8fb-4352-82b3-483919322c99,0x1000,0x100800)/File(\EFI\ubuntu\shimx64.efi)RC
Boot0002* Unknown Device:     HD(2,GPT,9d8bb3e9-b8fb-4352-82b3-483919322c99,0x1000,0x100800)/File(\EFI\Boot\grubx64.efi)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


64349b3622c65f495a99dbf6102496e3   sda2/BOOT/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/BOOT/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda2/BOOT/fbx64.efi
a1da253696a304dce6b4668b70151c0e   sda2/BOOT/grubx64.efi
a660182adef313615746a665966d2ccc   sda2/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/ubuntu/shimx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda3    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: B5C87193-DA3E-48AC-BF25-3325320580F2
        Start        End    Sectors  Size Type
sda1     2048       4095       2048    1M BIOS boot
sda2     4096    1054719    1050624  513M EFI System
sda3  1054720 1953523711 1952468992  931G Linux filesystem
Disk sdb: 14.59 GiB, 15669919744 bytes, 30605312 sectors
Disk identifier: 328732D6-C6B7-49A2-916A-7BE57D174978
        Start      End  Sectors  Size Type
sdb1       64  5944423  5944360  2.8G Microsoft basic data
sdb2  5944424  5954491    10068  4.9M EFI System
sdb3  5954492  5955091      600  300K Microsoft basic data
sdb4  5955584 30605248 24649665 11.8G Linux filesystem


parted -lm (filtered): _________________________________________________________


sda:1000GB:scsi:512:4096:gpt:ATA WDC WD10JPVX-22J:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:540MB:538MB:fat32:EFI System Partition:boot, esp;
3:540MB:1000GB:1000GB:ext4::;
sdb:15.7GB:scsi:512:512:gpt:SanDisk Cruzer Blade:;
1:32.8kB:3044MB:3044MB::ISO9660:hidden, msftdata;
2:3044MB:3049MB:5155kB::Appended2:boot, esp;
3:3049MB:3049MB:307kB::Gap1:hidden, msftdata;
4:3049MB:15.7GB:12.6GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                     PARTLABEL
sda                                                                                                                 
&#9500;&#9472;sda1                                               8c98f969-838b-45ae-9270-c2ed3168abf8                           
&#9500;&#9472;sda2 vfat     640D-9DB5                            9d8bb3e9-b8fb-4352-82b3-483919322c99                           EFI System Partition
&#9492;&#9472;sda3 ext4     d9aedf79-b930-432e-87e9-051dbe36930e 0b7429f8-4bfe-4050-aff8-88f6bdb5d397                           
sdb    iso9660  2023-08-07-15-56-48-00                                                    Xubuntu 22.04.3 LTS amd64 


Mount points (filtered): _______________________________________________________


                                Avail Use% Mounted on
/dev/sda2                      502.5M   2% /mnt/boot-sav/sda2
/dev/sda3                      794.7G   8% /


Mount options (filtered): ______________________________________________________




===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid d9aedf79-b930-432e-87e9-051dbe36930e root hd0,gpt3 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda3/boot/grub/grub.cfg (filtered) ======================


Ubuntu   d9aedf79-b930-432e-87e9-051dbe36930e
Ubuntu, with Linux 6.2.0-37-generic   d9aedf79-b930-432e-87e9-051dbe36930e
Ubuntu, with Linux 6.2.0-26-generic   d9aedf79-b930-432e-87e9-051dbe36930e
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###


========================== sda3/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=d9aedf79-b930-432e-87e9-051dbe36930e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=640D-9DB5  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


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
 320.651794434 = 344.297242624  boot/grub/grub.cfg                             1
 638.187652588 = 685.248774144  boot/vmlinuz                                   1
   8.961063385 = 9.621868544    boot/vmlinuz-6.2.0-26-generic                  1
 638.187652588 = 685.248774144  boot/vmlinuz-6.2.0-37-generic                  1
   8.961063385 = 9.621868544    boot/vmlinuz.old                               1
  93.645877838 = 100.551495680  boot/initrd.img                                1
 516.502925873 = 554.590793728  boot/initrd.img-6.2.0-26-generic               4
  93.645877838 = 100.551495680  boot/initrd.img-6.2.0-37-generic               1
 516.502925873 = 554.590793728  boot/initrd.img.old                            4


===================== sda3: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Dec 19  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 19  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 19  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 19  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 19  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 19  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 19  2022 41_custom


====================== sdb/boot/grub/grub.cfg (filtered) =======================


Try or Install Xubuntu
Xubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


==================== sdb: Location of files loaded by Grub =====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !
```

---

### Post by TheFu on 2023-12-03
My first though it that the storage is starting to fail.

a) get your important data off it ASAP.

b) run SMART tests and SMART reports to see if the disk thinks things are starting to fail.

c) If the system has a BIOS battery and it is over 4 yrs old, replace it.  Could be that it has failed, so at every reboot, the BIOS goes back to defaults ... er ... for MS-Windows, not Linux.

d) look through the system patch logs. Did anything change that could remotely have anything to cause the issues seen?

Depending on what you find out, there are other things to research. Other people are much better at this than I am, but that's where I'd start.

I don't see any reason to be too concerned. Probably just a hardware issue.

---

### Post by oldfred on 2023-12-03
It looks like you have installed in both old BIOS boot mode from MBR on gpt drive using MBR & gpt's bios_grub partition and in UEFI boot mode using ESP - efi system partition.
The ESP is mounted in fstab, so default boot mode is UEFI.

But if grub in MBR is valid, it may still boot in old BIOS mode. But if Secure boot on, BIOS mode will not work.

You show "unknown" in UEFI boot entries.
That is typical of Acer where you have to set "trust" on UEFI boot entries.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

