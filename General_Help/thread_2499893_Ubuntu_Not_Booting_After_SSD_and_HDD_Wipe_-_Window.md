---
title: "Ubuntu Not Booting After SSD and HDD Wipe - Windows Boot Manager Still Appears in BIO"
date: 2024-08-14
forum: General Help
---

### Post by muckcu on 2024-08-14
As mentioned in the title, Ubuntu is not booting. Even after completely wiping my SSD and HDD, the Windows Boot Manager still appears in the BIOS. I tried setting the SSD as the primary boot device in the BIOS, but I still get the "System Reboot" error. When I manually select the boot device, I see options like "PCIe SSD" and "PCIe SSD (Ubuntu)," but no Windows Boot Manager. I have tried repairing the boot process multiple times with Boot Repair, but I haven't been successful.

I would appreciate any help you can provide.

---

### Post by yancek on 2024-08-14
>   have tried repairing the boot process multiple times with Boot Repai 

Yet you have not posted the output from the Create BootInfo Summary of boot repair as suggested on their page.  Doing that would be useful.

---

### Post by muckcu on 2024-08-14
> **yancek said:**
> Yet you have not posted the output from the Create BootInfo Summary of boot repair as suggested on their page.  Doing that would be useful.

oh sorry for this


[HTML]boot-repair-4ppa2079                                              [20240813_2136]

============================= Boot Repair Summary ==============================





/dev/sda (/dev/sda) has unknown type. Lütfen bu mesaju boot.repair@gmail.com adresine rapor edin
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-45-generic

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p3,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /boot/efi/efi/Microsoft/Boot/bootmgfw.efi /boot/efi/efi/Microsoft/Boot/bootmgfw.efi.grb
rm /boot/efi/efi/Microsoft/Boot/bootx64.efi /boot/efi/efi/Microsoft/Boot/bootx64.efi.grb
rm /boot/efi/efi/Boot/bootx64.efi
mv /boot/efi/efi/Boot/bkpbootx64.efi /boot/efi/efi/Boot/bootx64.efi
/dev/nvme0n1p3/boot/efi not empty

=================== Reinstall the grub-efi of /dev/nvme0n1p3 ===================

grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.5.0-45-generic
modprobe efivars

efibootmgr -v before grub install
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0002,0005,0000,2001,2002,2003
Boot0000* WDC WD5000LPVX-80V0TT0	PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)RC
Boot0001* EFI PXE 0 for IPv4 (B4-A9-FC-47-2E-2A) 	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(b4a9fc472e2a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* PCIe SSD	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-61-6A-D0-17-44)/HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)RC
Boot0003* EFI USB Device (SanDisk)	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0xb3a7b852,0x393e000,0x10000)RC
Boot0005* ubuntu	HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

uname -r
6.5.0-45-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
cp /boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdb2/EFI/ubuntu/grubx64.efi
df /dev/nvme0n1p1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi
df /dev/sdb2
mv /mnt/boot-sav/sdb2/EFI/Boot/bootx64.efi /mnt/boot-sav/sdb2/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/sdb2/EFI/Boot/bootx64.efi
cp: '/mnt/boot-sav/sdb2/EFI/Boot/bootx64.efi' yazarken hata: Ayg&#305;t üzerinde bo&#351; yer yok

grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v after grub install
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0002,0000,2001,2002,2003
Boot0000* WDC WD5000LPVX-80V0TT0	PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)RC
Boot0001* EFI PXE 0 for IPv4 (B4-A9-FC-47-2E-2A) 	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(b4a9fc472e2a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* PCIe SSD	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-61-6A-D0-17-44)/HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)RC
Boot0003* EFI USB Device (SanDisk)	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0xb3a7b852,0x393e000,0x10000)RC
Boot0005* ubuntu	HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Found linux image: /boot/vmlinuz-6.5.0-45-generic
Found initrd image: /boot/initrd.img-6.5.0-45-generic
Found linux image: /boot/vmlinuz-6.5.0-18-generic
Found initrd image: /boot/initrd.img-6.5.0-18-generic
Adding boot menu entry for UEFI Firmware Settings ...

Unhide GRUB boot menu in nvme0n1p3/boot/grub/grub.cfg

Önyükleme ba&#351;ar&#305;yla onar&#305;ld&#305;.

&#350;imdi bilgisayar&#305;n&#305;z&#305; yeniden ba&#351;latabilirsiniz.
Please do not forget to make your UEFI firmware boot on the &#350;u anda kullan&#305;mda olan i&#351;letim sistemi - Ubuntu 22.04.4 LTS entry (nvme0n1p1/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,2)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    offsetio extcmd macho elf file gettext boot bufio verifiers crypto 
    terminal normal datetime date mmap drivemap blocklist archelp newc 
    vga_text relocator video chain ntldr search_label search_fs_file 
    search_fs_uuid search keylayouts at_keyboard pci usb usb_keyboard gcry_md5 
    hashsum gcry_crc gzio xzio lzopio lspci fshelp ext2 xfs acpi reboot 
    iso9660 gcry_sha1 div udf exfat font diskfilter raid6rec zstd btrfs ventoy 
    read halt video_fb vbe linux linux16 test true sleep echo bitmap gfxterm 
    bitmap_scale trig video_colors gfxmenu videotest videoinfo functional_test 
    videotest_checksum video_cirrus video_bochs vga minicmd help configfile tr 
    biosdisk disk ls tar zfs squash4 pbkdf2 gcry_sha512 password_pbkdf2 
    all_video png jpeg part_gpt part_msdos fat ntfs loopback 
    gfxterm_background procfs gfxterm_menu smbios
    ---------------------------------------------------------------------------

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  -
    Boot sector info: 
    Boot file info:      Grub2 (v2.00) in the file 
                       /Fedora-KDE-Live-x86_64-40-1.14.iso looks at sector 0 
                       of the same hard drive for core.img, but core.img can 
                       not be found at this location. Grub2 (v2.00) in the 
                       file /ubuntu-22.04.4-desktop-amd64.iso looks at sector 
                       0 of the same hard drive for core.img, but core.img 
                       can not be found at this location.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 60022784.
    Operating System:  
    Boot files:        /grub/grub.cfg /efi/BOOT/bkpbootx64.efi 
                       /efi/BOOT/bootx64.efi /efi/BOOT/grub.efi 
                       /efi/BOOT/grubia32.efi /efi/BOOT/grubia32_real.efi 
                       /efi/BOOT/grubx64_real.efi /efi/BOOT/mmia32.efi 
                       /efi/BOOT/MokManager.efi /efi/ubuntu/grubx64.efi


================================ 1 OS detected =================================

OS#1:   &#350;u anda kullan&#305;mda olan i&#351;letim sistemi - Ubuntu 22.04.4 LTS on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP107M [GeForce GTX 1050 3 GB Max-Q] CoffeeLake-H GT2 [UHD Graphics 630] from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.5.0-45-generic root=UUID=57101d52-12c1-47b8-b02b-f2a34e319082 ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p3 ext4  234G   11G  211G        5% /

===================================== UEFI =====================================

BIOS/UEFI firmware: CP211(2.11) from Insyde
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0002,0000,2001,2002,2003
Boot0000* WDC WD5000LPVX-80V0TT0	PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)RC
Boot0001* EFI PXE 0 for IPv4 (B4-A9-FC-47-2E-2A) 	PciRoot(0x0)/Pci(0x1d,0x5)/Pci(0x0,0x0)/MAC(b4a9fc472e2a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* PCIe SSD	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-61-6A-D0-17-44)/HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)RC
Boot0003* EFI USB Device (SanDisk)	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,MBR,0xb3a7b852,0x393e000,0x10000)RC
Boot0005* ubuntu	HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

8628f48c5d38765c52418242dbe5c981   sdb2/BOOT/bkpbootx64.efi
8c547ea79251a04753943a968fb6b653   sdb2/BOOT/bootx64.efi
f5787f65638d6e2688bf5c651fcd33d0   sdb2/BOOT/grub.efi
0c7449c90dc9fc090c58b868b747bada   sdb2/BOOT/grubia32.efi
acdc10c40cba8560eb01580ab1981afd   sdb2/BOOT/grubia32_real.efi
654a43635ef7708b84da8cf4926176cb   sdb2/BOOT/grubx64_real.efi
7010d05a34cbf0c3e696df6a62f56015   sdb2/BOOT/mmia32.efi
170cb3c5f2b958e80a4d4d915b0999f4   sdb2/BOOT/MokManager.efi
a1da253696a304dce6b4668b70151c0e   sdb2/ubuntu/grubx64.efi
ce29d74d782d086b923d0f4eaf613508   sdb2/BOOT/BOOTAA64.efi
b6410a7309a1aa9a05df02ea1954c02d   sdb2/BOOT/BOOTIA32.efi
ff3715a29fb2c136d830838ce574a7b6   sdb2/BOOT/BOOTMIPS.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1	: is-GPT,	hasBIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes
sdb	: notGPT,	no-BIOSboot,	has---ESP, 	usb-disk,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes
sda	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p3	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
nvme0n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb2	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sdb1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p3	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb2	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sdb1	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p3	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme0n1
nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
sdb2	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sdb1	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sdb
sda	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 30A271D8-B8F2-4FD1-A4F3-BB37CD6A381E
          Start       End   Sectors   Size Type
nvme0n1p1   2048    194559    192512    94M EFI System
nvme0n1p2 194560    389119    194560    95M BIOS boot
nvme0n1p3 389120 500117503 499728384 238.3G Linux filesystem
Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: FEFCDF91-14DC-4274-BFC1-65074155C98F
Disk sdb: 28.65 GiB, 30765219840 bytes, 60088320 sectors
Disk identifier: 0xb3a7b852
     Boot    Start      End  Sectors  Size Id Type
sdb1  *        2048 60022783 60020736 28.6G  7 HPFS/NTFS/exFAT
sdb2       60022784 60088319    65536   32M ef EFI (FAT-12/16/32)

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:gpt:ATA WDC WD5000LPVX-8:;
sdb:30.8GB:scsi:512:512:msdos:SanDisk Cruzer Force:;
1:1049kB:30.7GB:30.7GB:::boot;
2:30.7GB:30.8GB:33.6MB:fat16::esp;
nvme0n1:256GB:nvme:512:512:gpt:PCIe SSD:;
1:1049kB:99.6MB:98.6MB:fat32::boot, esp;
2:99.6MB:199MB:99.6MB:::bios_grub;
3:199MB:256GB:256GB:ext4::;

Free space >10MiB: ______________________________________________________________

sda: 0.02MiB:476940MiB:476940MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL   PARTLABEL
sda                                                                                                    
sdb                                                                                                    
&#9500;&#9472;sdb1      exfat    4E21-0000                            b3a7b852-01                          Ventoy  
&#9492;&#9472;sdb2      vfat     3F32-27F5                            b3a7b852-02                          VTOYEFI 
nvme0n1                                                                                                
&#9500;&#9472;nvme0n1p1 vfat     6B92-B42F                            d320de0a-623e-407d-8558-9f1e8f5e0949         
&#9500;&#9472;nvme0n1p2                                               3e74751f-ce84-4163-a59b-8471ea2c4688         
&#9492;&#9472;nvme0n1p3 ext4     57101d52-12c1-47b8-b02b-f2a34e319082 034418f3-1b42-4e67-8c34-999cdce34022         

Mount points (filtered): _______________________________________________________

                                     Avail Use% Mounted on
/dev/nvme0n1p3                      210.6G   5% /
/dev/sdb1                             9.3G  67% /media/mustyg3n/Ventoy
/dev/sdb2                               2K 100% /mnt/boot-sav/sdb2
efivarfs                             26.9K  68% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p3                      ext4            rw,relatime,errors=remount-ro
/dev/sdb1                           exfat           rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,iocharset=utf8,errors=remount-ro
/dev/sdb2                           vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 57101d52-12c1-47b8-b02b-f2a34e319082 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p3/boot/grub/grub.cfg (filtered) ====================

Ubuntu   57101d52-12c1-47b8-b02b-f2a34e319082
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p3/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=57101d52-12c1-47b8-b02b-f2a34e319082 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=6B92-B42F  /boot/efi       vfat    umask=0077      0       1

==================== nvme0n1p3/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p3: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 172,351543427 = 185,061060608  boot/grub/grub.cfg                             1
 171,464450836 = 184,108552192  boot/vmlinuz                                   1
 193,974605560 = 208,278646784  boot/vmlinuz-6.5.0-18-generic                  2
 171,464450836 = 184,108552192  boot/vmlinuz-6.5.0-45-generic                  1
 193,974605560 = 208,278646784  boot/vmlinuz.old                               2
  13,400100708 = 14,388248576   boot/initrd.img                                1
  13,517269135 = 14,514057216   boot/initrd.img-6.5.0-18-generic               1
  13,400100708 = 14,388248576   boot/initrd.img-6.5.0-45-generic               1
  13,517269135 = 14,514057216   boot/initrd.img.old                            1

=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 19  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 19  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 19  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 19  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 19  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 19  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 19  2022 41_custom

======================== sdb2/grub/grub.cfg (filtered) =========================

function iso_common_menuentry {
function miso_common_menuentry {
function common_unsupport_menuentry {
function miso_unsupport_menuentry {
function iso_unsupport_menuentry {
function wim_common_menuentry {
function wim_unsupport_menuentry {
function efi_common_menuentry {
function efi_unsupport_menuentry {
function vhd_common_menuentry {
function vhd_unsupport_menuentry {
function vtoy_common_menuentry {
function vtoy_unsupport_menuentry {
function img_common_menuentry {
function img_unsupport_menuentry {
function mimg_common_menuentry {
$NO_ISO_MENU (Press enter to reboot ...)

==================== sdb2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             grub/grub.cfg                                  1
[/HTML]

---

### Post by muckcu on 2024-08-14
[HTML]============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/sda.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.4 LTS
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /etc/default/grub


================================ 1 OS detected =================================

OS#1:   &#350;u anda kullan&#305;mda olan i&#351;letim sistemi - Ubuntu 22.04.4 LTS on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP107M [GeForce GTX 1050 3 GB Max-Q] CoffeeLake-H GT2 [UHD Graphics 630] from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.5.0-45-generic root=UUID=57101d52-12c1-47b8-b02b-f2a34e319082 ro quiet splash vt.handoff=7
df -Th / : /dev/nvme0n1p3 ext4  234G   12G  211G        6% /

===================================== UEFI =====================================

BIOS/UEFI firmware: CP211(2.11) from Insyde
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0002,0005,2001,2002,2003,0000
Boot0000* WDC WD5000LPVX-80V0TT0	PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)RC
Boot0002* PCIe SSD	PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-61-6A-D0-17-44)/HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)RC
Boot0005* ubuntu	HD(1,GPT,d320de0a-623e-407d-8558-9f1e8f5e0949,0x800,0x2f000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1	: is-GPT,	hasBIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes
sda	: is-GPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, no-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p3	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	end-after-100GB
nvme0n1p1	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda	: no-os,	64, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

nvme0n1p3	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
nvme0n1p1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p3	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	nvme0n1
nvme0n1p1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	nvme0n1
sda	: maybesepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 30A271D8-B8F2-4FD1-A4F3-BB37CD6A381E
          Start       End   Sectors   Size Type
nvme0n1p1   2048    194559    192512    94M EFI System
nvme0n1p2 194560    389119    194560    95M BIOS boot
nvme0n1p3 389120 500117503 499728384 238.3G Linux filesystem
Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: FEFCDF91-14DC-4274-BFC1-65074155C98F

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:gpt:ATA WDC WD5000LPVX-8:;
nvme0n1:256GB:nvme:512:512:gpt:PCIe SSD:;
1:1049kB:99.6MB:98.6MB:fat32::boot, esp;
2:99.6MB:199MB:99.6MB:::bios_grub;
3:199MB:256GB:256GB:ext4::;

Free space >10MiB: ______________________________________________________________

sda: 0.02MiB:476940MiB:476940MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                                  
nvme0n1                                                                                              
&#9500;&#9472;nvme0n1p1 vfat     6B92-B42F                            d320de0a-623e-407d-8558-9f1e8f5e0949       
&#9500;&#9472;nvme0n1p2                                               3e74751f-ce84-4163-a59b-8471ea2c4688       
&#9492;&#9472;nvme0n1p3 ext4     57101d52-12c1-47b8-b02b-f2a34e319082 034418f3-1b42-4e67-8c34-999cdce34022       

Mount points (filtered): _______________________________________________________

                                     Avail Use% Mounted on
/dev/nvme0n1p3                      210.5G   5% /
efivarfs                             34.6K  60% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p3                      ext4            rw,relatime,errors=remount-ro

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 57101d52-12c1-47b8-b02b-f2a34e319082 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== nvme0n1p3/grub/grub.cfg (filtered) ======================

### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

=================== nvme0n1p3/boot/grub/grub.cfg (filtered) ====================

Ubuntu   57101d52-12c1-47b8-b02b-f2a34e319082
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p3/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=57101d52-12c1-47b8-b02b-f2a34e319082 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=6B92-B42F  /boot/efi       vfat    umask=0077      0       1

==================== nvme0n1p3/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p3: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 104,332675934 = 112,026357760  grub/grub.cfg                                  1
 227,818557739 = 244,618313728  boot/grub/grub.cfg                             1
 171,464450836 = 184,108552192  boot/vmlinuz                                   1
 193,974605560 = 208,278646784  boot/vmlinuz-6.5.0-18-generic                  2
 171,464450836 = 184,108552192  boot/vmlinuz-6.5.0-45-generic                  1
 193,974605560 = 208,278646784  boot/vmlinuz.old                               2
  13,400100708 = 14,388248576   boot/initrd.img                                1
  13,517269135 = 14,514057216   boot/initrd.img-6.5.0-18-generic               1
  13,400100708 = 14,388248576   boot/initrd.img-6.5.0-45-generic               1
  13,517269135 = 14,514057216   boot/initrd.img.old                            1

=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 19  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 19  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 19  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 19  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 19  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17  2023 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 19  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 19  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p3,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the &#350;u anda kullan&#305;mda olan i&#351;letim sistemi - Ubuntu 22.04.4 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) ![/HTML]

---

### Post by muckcu on 2024-08-14
I can send you the pastebin link if it will help you more.

---

### Post by oldfred on 2024-08-14
Bit easier to review if you had just posted the link to pastebin that Boot-Repair provides.

Install looks normal.
Looks like Boot-Repair removed some Windows entries.
Wipe of a drive, do not change the UEFI boot entries stored in UEFI.

What brand/model system?
 Some only want to boot Windows or need your to set "trust" to boot Ubuntu.
We can suggest work arounds for those, if required.

Is system set to boot in UEFI boot mode?

---

### Post by muckcu on 2024-08-14
> **oldfred said:**
> Bit easier to review if you had just posted the link to pastebin that Boot-Repair provides.

Install looks normal.
Looks like Boot-Repair removed some Windows entries.
Wipe of a drive, do not change the UEFI boot entries stored in UEFI.

What brand/model system?
 Some only want to boot Windows or need your to set "trust" to boot Ubuntu.
We can suggest work arounds for those, if required.

Is system set to boot in UEFI boot mode?

All screen at my bios
I am unable to make any changes to the UEFI secure boot section in any way. It currently shows as disabled.

---

### Post by tea for one on 2024-08-14
Post 7 Screenshot 2 (IMG_1404.jpg)
Disable "USB BIOS Legacy Support"
Does Ubuntu boot now?

---

