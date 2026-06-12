---
title: "Grub issue and boot repair do not fixe it (NVram issue ?)"
date: 2023-07-08
forum: General Help
---

### Post by marcussacapuce56 on 2023-07-08
Hello Community,


I really don't understand what's going on with my PC. Let me explain.


I have a Windows 10 Pro / Ubuntu 22.04 dual boot. And often when I restart the PC, it happens that the grub no longer launches and I only have a black screen.
So, I try to run a boot-repair, but surprisingly boot repair doesn't fix the problem either.


It's a mess, so I'm posting here the boot-repair info hoping that a kind and gifted soul can tell me how to solve this.


Thank you :)

Boot repair report : [https://pastebin.ubuntu.com/p/YzbR2tcmGr/](https://pastebin.ubuntu.com/p/YzbR2tcmGr/)
```

boot-repair-4ppa203                                              [20230708_1344]
 
============================= Boot Repair Summary ==============================
 
 
 
 
 
This will modify the mount point of sda1 in order to remove spaces and special characters. Do you want to continue?
This will modify the mount point of sda1 in order to remove spaces and special characters. Do you want to continue?
 
Recommended repair: ____________________________________________________________
 
The default repair of the Boot-Repair utility will reinstall the grub-efi of
sdc5,
using the following options:  sdc1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups
 
 
rm /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sdc1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sdc1/efi/Boot/bootx64.efi
Mount sdc1 on /mnt/boot-sav/sdc5/boot/efi
 
Unhide GRUB boot menu in sdc5/etc/default/grub
 
======================== Reinstall the grub-efi of sdc5 ========================
 
chroot /mnt/boot-sav/sdc5 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.3.0-28-generic
chroot /mnt/boot-sav/sdc5 modprobe efivars
 
chroot /mnt/boot-sav/sdc5 efibootmgr -v before grub install
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0012,000E,0011,000F
Boot000E* Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.T.3.1.5.0.0.3.4.1.A.S....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .V.9.4.S.0.J.5.T........BO..NO........o.C.r.u.c.i.a.l._.C.T.5.1.2.M.X.1.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . .5.1.0.1.E.0.4.E.D.4.1.F........BO
Boot000F* USB    BBS(HD,,0x0)..GO..NO........[.G.-.D.R.I.V.E. .m.o.b.i.l.e. .S.S.D. .0....................A..........................Gd-.;.A..MQ..L.B.1.0.1.8.4.5.0.2.1.2.5........BO..NO........c.J.e.t.F.l.a.s.h.T.r.a.n.s.c.e.n.d. .1.6.G.B. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.2.6.E.I.L.6.8.3.G.L.B.M.Z.2.M.7........BO
Boot0011* UEFI: JetFlashTranscend 16GB 1100, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(2,GPT,8a74ed66-6767-e7e1-8363-570323fdc0dc,0x1e2bfd8,0x10000)..BO
Boot0012* Windows Boot Manager    HD(1,GPT,006814ef-7e2b-4cf8-824c-c7f2c7a10213,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
 
chroot /mnt/boot-sav/sdc5 uname -r
5.3.0-28-generic
 
chroot /mnt/boot-sav/sdc5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sdc1
mv /mnt/boot-sav/sdc5/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sdc5/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sdc5/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdc5/boot/efi/EFI/Boot/bootx64.efi
 
chroot /mnt/boot-sav/sdc5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
 
chroot /mnt/boot-sav/sdc5 efibootmgr -v after grub install
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0012,000E,0011,000F
Boot000E* Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.T.3.1.5.0.0.3.4.1.A.S....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .V.9.4.S.0.J.5.T........BO..NO........o.C.r.u.c.i.a.l._.C.T.5.1.2.M.X.1.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . .5.1.0.1.E.0.4.E.D.4.1.F........BO
Boot000F* USB    BBS(HD,,0x0)..GO..NO........[.G.-.D.R.I.V.E. .m.o.b.i.l.e. .S.S.D. .0....................A..........................Gd-.;.A..MQ..L.B.1.0.1.8.4.5.0.2.1.2.5........BO..NO........c.J.e.t.F.l.a.s.h.T.r.a.n.s.c.e.n.d. .1.6.G.B. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.2.6.E.I.L.6.8.3.G.L.B.M.Z.2.M.7........BO
Boot0011* UEFI: JetFlashTranscend 16GB 1100, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(2,GPT,8a74ed66-6767-e7e1-8363-570323fdc0dc,0x1e2bfd8,0x10000)..BO
Boot0012* Windows Boot Manager    HD(1,GPT,006814ef-7e2b-4cf8-824c-c7f2c7a10213,0x800,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)..BO
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
 
chroot /mnt/boot-sav/sdc5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Found linux image: /boot/vmlinuz-5.19.0-45-generic
Found initrd image: /boot/initrd.img-5.19.0-45-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
grub-probe: error: cannot find a GRUB drive for /dev/sdd2.  Check your device.map.
Found Windows Boot Manager on /dev/sdc1@/EFI/Microsoft/Boot/bootmgfw.efi
This will modify the mount point of sda1 in order to remove spaces and special characters. Do you want to continue?
 
Unhide GRUB boot menu in sdc5/boot/grub/grub.cfg
 
An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
 
Locked-NVram detected.
 
 
============================ Boot Info After Repair ============================
 
 => No known boot loader is installed in the MBR of /dev/sda.
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 34 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,2)/grub. It also embeds following components:
 
    modules
    ---------------------------------------------------------------------------
    offsetio extcmd macho elf file setkey gettext boot bufio verifiers crypto 
    terminal normal datetime date mmap drivemap blocklist regexp archelp newc 
    vga_text relocator video chain ntldr search_label search_fs_file 
    search_fs_uuid search keylayouts at_keyboard pci usb usb_keyboard gcry_md5 
    hashsum gcry_crc gzio xzio lzopio lspci fshelp ext2 xfs acpi iso9660 
    gcry_sha1 div udf exfat font diskfilter raid6rec zstd btrfs ventoy read 
    halt video_fb vbe linux linux16 test true sleep reboot echo bitmap 
    bitmap_scale gfxterm video_colors trig gfxmenu videotest videoinfo 
    functional_test videotest_checksum video_cirrus video_bochs vga minicmd 
    help configfile tr biosdisk disk ls tar squash4 pbkdf2 gcry_sha512 
    password_pbkdf2 all_video png jpeg part_gpt part_msdos fat ntfs loopback 
    gfxterm_background procfs gfxterm_menu
    ---------------------------------------------------------------------------
 
sda1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdb1: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
 
sdc1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi
 
sdc2: __________________________________________________________________________
 
    File system:       
    Boot sector type:  -
    Boot sector info: 
 
sdc3: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe
 
sdc4: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sdc5: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub
 
sdd1: __________________________________________________________________________
 
    File system:       exfat
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   fuse: mount failed: Device or resource busy
 
sdd2: __________________________________________________________________________
 
    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg
 
 
================================ 2 OS detected =================================
 
OS#1:   Ubuntu 22.04.2 LTS on sdc5
OS#2:   Windows 8 or 10 on sdc3
 
================================ Host/Hardware =================================
 
CPU architecture: 64-bit
Video: GM204 [GeForce GTX 970] HD Graphics 530 from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)
 
===================================== UEFI =====================================
 
BIOS/UEFI firmware: 1101 from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0011
Timeout: 1 seconds
BootOrder: 0012,000E,0011,000F
Boot000E* Hard Drive    BBS(HD,,0x0)..GO..NO........o.S.T.3.1.5.0.0.3.4.1.A.S....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .V.9.4.S.0.J.5.T........BO..NO........o.C.r.u.c.i.a.l._.C.T.5.1.2.M.X.1.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . .5.1.0.1.E.0.4.E.D.4.1.F........BO
Boot000F* USB    BBS(HD,,0x0)..GO..NO........[.G.-.D.R.I.V.E. .m.o.b.i.l.e. .S.S.D. .0....................A..........................Gd-.;.A..MQ..L.B.1.0.1.8.4.5.0.2.1.2.5........BO..NO........c.J.e.t.F.l.a.s.h.T.r.a.n.s.c.e.n.d. .1.6.G.B. .1.1.0.0....................A.......................6..Gd-.;.A..MQ..L.2.6.E.I.L.6.8.3.G.L.B.M.Z.2.M.7........BO
Boot0011* UEFI: JetFlashTranscend 16GB 1100, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(2,GPT,8a74ed66-6767-e7e1-8363-570323fdc0dc,0x1e2bfd8,0x10000)..BO
Boot0012* Windows Boot Manager    HD(1,GPT,006814ef-7e2b-4cf8-824c-c7f2c7a10213,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)..BO
 
64349b3622c65f495a99dbf6102496e3   sdc1/Boot/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   sdc1/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sdc1/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   sdc1/Boot/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sdc1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sdc1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sdc1/ubuntu/shimx64.efi
7f2103e085e5b7982c2ebcb6ed2128cd   sdc1/Microsoft/Boot/bootmgfw.efi
33da288b19abd2c259748c9c5764a5a4   sdc1/Microsoft/Boot/bootmgr.efi
 
============================= Drive/Partition Info =============================
 
Disks info: ____________________________________________________________________
 
sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
 
Partitions info (1/3): _________________________________________________________
 
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sdc5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
 
Partitions info (2/3): _________________________________________________________
 
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sdc5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
 
Partitions info (3/3): _________________________________________________________
 
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdc
 
fdisk -l (filtered): ___________________________________________________________
 
Disk sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x3421af51
      Boot Start       End   Sectors   Size Id Type
sda1        2048 976769023 976766976 465.8G  7 HPFS/NTFS/exFAT
Disk sdb: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Disk identifier: 0x0006b1df
      Boot Start        End    Sectors  Size Id Type
sdb1        2048 2930276351 2930274304  1.4T 83 Linux
Disk sdc: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: E4DEB080-262D-45A7-9B74-FFB6AF4BB670
          Start        End   Sectors   Size Type
sdc1       2048     206847    204800   100M EFI System
sdc2     206848     239615     32768    16M Microsoft reserved
sdc3     239616  510913614 510673999 243.5G Microsoft basic data
sdc4  510914560  511999999   1085440   530M Windows recovery environment
sdc5  512000000 1000214527 488214528 232.8G Linux filesystem
Disk sdd: 15.1 GiB, 16231956480 bytes, 31703040 sectors
Disk identifier: 974920FF-E874-4F89-0154-40B5055C3E68
         Start      End  Sectors  Size Type
sdd1      2048 31637463 31635416 15.1G Microsoft basic data
sdd2  31637464 31702999    65536   32M Microsoft basic data
Disk dm-0: 880 MiB, 922746880 bytes, 1802240 sectors
Disk identifier: 0x2c534026
       Boot Start     End Sectors  Size Id Type
dm-0p1 *        0 1802239 1802240  880M  0 Empty
dm-0p2        964    5891    4928  2.4M ef EFI (FAT-12/16/32)
Disk zram0: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram1: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram2: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram3: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram4: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram5: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram6: 993.9 MiB, 1042153472 bytes, 254432 sectors
Disk zram7: 993.9 MiB, 1042153472 bytes, 254432 sectors
 
parted -lm (filtered): _________________________________________________________
 
sda:500GB:scsi:512:512:loop:G-DRIVE mobile SSD:;
1:0.00B:500GB:500GB:fat32::;
sdb:1500GB:scsi:512:512:msdos:ATA ST31500341AS:;
1:1049kB:1500GB:1500GB:ext4::;
sdc:512GB:scsi:512:4096:gpt:ATA Crucial_CT512MX1:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:262GB:261GB:ntfs:Basic data partition:msftdata;
4:262GB:262GB:556MB:ntfs::hidden, diag;
5:262GB:512GB:250GB:ext4::;
sdd:16.2GB:scsi:512:512:gpt:JetFlash Transcend 16GB:;
1:1049kB:16.2GB:16.2GB::Ventoy:msftdata;
2:16.2GB:16.2GB:33.6MB:fat16:VTOYEFI:hidden, msftdata;
 
blkid (filtered): ______________________________________________________________
 
NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9492;&#9472;sda1 ntfs     D4A48352A48335D0                     3421af51-01                          500 G-DRIVE            
sdb                                                                                                              
&#9492;&#9472;sdb1 ext4     916f5b67-c3e9-4a2d-8145-c6fc2e22fc26 0006b1df-01                                                 
sdc                                                                                                              
&#9500;&#9472;sdc1 vfat     5205-4134                            006814ef-7e2b-4cf8-824c-c7f2c7a10213                        EFI system partition
&#9500;&#9472;sdc2                                               a1f97a81-1341-4278-bbad-31fcc740dd68                        Microsoft reserved partition
&#9500;&#9472;sdc3 ntfs     DC5E0EBB5E0E8E88                     3c071f5b-0dc6-4a85-aca1-6eab3c2816af                        Basic data partition
&#9500;&#9472;sdc4 ntfs     92C0DD87C0DD7249                     3aeebc01-7318-4ffc-a128-75e592db7387                        
&#9492;&#9472;sdc5 ext4     0b0be050-31d3-40b5-a61c-509a3eaace58 ed9732a9-bf8b-4407-8299-148b28f8647b                        
sdd                                                                                                              
&#9500;&#9472;sdd1 exfat    3AA1-E09B                            74b4ecd6-3469-e30e-3754-b72d601d6dbe Ventoy                 Ventoy
&#9492;&#9472;sdd2 iso9660  2020-06-13-00-42-55-00                                                    Boot-Repair-Disk 64bit 
 
Mount points (filtered): _______________________________________________________
 
                    Avail Use% Mounted on
/dev/mapper/ventoy      0 100% /cdrom
/dev/sda1          112.8G  76% /media/lubuntu/500 G-DRIVE
/dev/sdb1            552G  55% /mnt/boot-sav/sdb1
/dev/sdc1             64M  33% /mnt/boot-sav/sdc1
/dev/sdc3          167.7G  31% /mnt/boot-sav/sdc3
/dev/sdc4           88.5M  83% /mnt/boot-sav/sdc4
/dev/sdc5          197.8G   8% /mnt/boot-sav/sdc5
/dev/sdd2               0 100% /media/lubuntu/Boot-Repair-Disk 64bit
 
Mount options (filtered): ______________________________________________________
 
 
===================== sdc1/efi/ubuntu/grub.cfg (filtered) ======================
 
search.fs_uuid 0b0be050-31d3-40b5-a61c-509a3eaace58 root hd2,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
 
====================== sdc5/boot/grub/grub.cfg (filtered) ======================
 
Ubuntu   0b0be050-31d3-40b5-a61c-509a3eaace58
Ubuntu, with Linux 5.19.0-46-generic   0b0be050-31d3-40b5-a61c-509a3eaace58
Ubuntu, with Linux 5.19.0-45-generic   0b0be050-31d3-40b5-a61c-509a3eaace58
Windows Boot Manager (on sdc1)   osprober-efi-5205-4134
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###
 
========================== sdc5/etc/fstab (filtered) ===========================
 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=0b0be050-31d3-40b5-a61c-509a3eaace58 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=5205-4134  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
 
======================= sdc5/etc/default/grub (filtered) =======================
 
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
 
==================== sdc5: Location of files loaded by Grub ====================
 
           GiB - GB             File                                 Fragment(s)
 244.140632629 = 262.144008192  boot/grub/grub.cfg                             1
 420.323879242 = 451.319328768  boot/vmlinuz                                   2
 418.515621185 = 449.377726464  boot/vmlinuz-5.19.0-45-generic                 2
 420.323879242 = 451.319328768  boot/vmlinuz-5.19.0-46-generic                 2
 418.515621185 = 449.377726464  boot/vmlinuz.old                               2
 246.015621185 = 264.157261824  boot/initrd.img                                4
 371.656246185 = 399.062855680  boot/initrd.img-5.19.0-45-generic              5
 246.015621185 = 264.157261824  boot/initrd.img-5.19.0-46-generic              4
 371.656246185 = 399.062855680  boot/initrd.img.old                            5
 
===================== sdc5: ls -l /etc/grub.d/ (filtered) ======================
 
-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
 
====================== sdd2/boot/grub/grub.cfg (filtered) ======================
 
 
==================== sdd2: Location of files loaded by Grub ====================
 
           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

```

---

### Post by tea for one on 2023-07-08
The following two lines indicate where the problem may be.
Line 54 - grub-install: warning: EFI variables cannot be set on this system.
Line 55 - grub-install: warning: You will have to complete the GRUB setup manually.

I suggest that you try and re-install grub manually from a "Try Ubuntu" live session.
```
sudo mount /dev/sdc5 /mnt
```
```
sudo mount /dev/sdc1 /mnt/boot/efi
```
```
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
```
```
sudo chroot /mnt
```
```
grub-install /dev/sdc
```
```
grub-install --recheck /dev/sdc
```
```
update-grub  
```
Before running these commands, double check that Ubuntu system partition is still sdc5 and the ESP is still sdc1.
Run the commands separately.

If any error messages appear, please abort the repair and post them here with the respective command (using code tags).

---

### Post by oldfred on 2023-07-08
What brand/model system?
We are seeing more of the locked ESP type issues.
It may be another security setting, separate from UEFI Secure boot in UEFI.
Check UEFI settings, you may need to download & review manual for better descriptions of entries.

---

