---
title: "Grub broken after conversion from MBR to GPT!"
date: 2015-12-24
forum: General Help
---

### Post by eshant_engineer on 2015-12-24
I have converted disk partition table from MBR to GPT using disk AOMEI Partition Assistant Professional Edition from Windows in consequence I lost grub and therefore Ubuntu from booting though Windows is booting just fine without grub. Sysinfo is telling that it is booted in UEFI mode rightly so because I have converted to GPT from Windows, therefore it is OK. Here is how my HDD's structure look like now:

[IMG]http://i.stack.imgur.com/oiCPL.png[/IMG]

> How to restore grub and Ubuntu in this scenario?
> sda3 is a new partition created after conversion. Is it at right place or it needs to be at the top?

Boot-repair Log:-
```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/Bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 60436 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    62,923,922    62,921,875 Data partition (Windows/Linux)
/dev/sda2      62,924,800   226,291,588   163,366,789 Data partition (Windows/Linux)
/dev/sda3     226,291,590   226,500,434       208,845 EFI System partition
/dev/sda4     226,504,704   230,506,495     4,001,792 Data partition (Windows/Linux)
/dev/sda5     230,508,544   259,659,775    29,151,232 Data partition (Windows/Linux)
/dev/sda6     259,661,824   280,633,342    20,971,519 Data partition (Windows/Linux)
/dev/sda7     280,635,392   490,350,590   209,715,199 Data partition (Windows/Linux)
/dev/sda8     490,352,640   700,067,838   209,715,199 Data partition (Windows/Linux)
/dev/sda9     700,069,888   804,927,486   104,857,599 Data partition (Windows/Linux)
/dev/sda10    804,929,536   857,358,334    52,428,799 Data partition (Windows/Linux)
/dev/sda11    857,360,384   909,789,182    52,428,799 Data partition (Windows/Linux)
/dev/sda12    909,791,232   976,773,119    66,981,888 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.9 GB, 15854469120 bytes
255 heads, 63 sectors/track, 1927 cylinders, total 30965760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              2    30,965,759    30,965,758   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       c6df7d2b-ff85-ce45-a338-7f926d2e538b   ext2       casper-rw
/dev/sda1        637faed1-16b4-4ce4-8a48-e351e80fd892   btrfs      root
/dev/sda10       3E8B0C3B2C21FB69                       ntfs       W-STORE
/dev/sda11       7FD004415E7E2705                       ntfs       L-STORE
/dev/sda12       9e57f035-351a-4965-9c57-1f76234d7b64   ext4       Backup
/dev/sda2        548B3E37787C1377                       ntfs       Windows7
/dev/sda3        091A-0966                              vfat       
/dev/sda4        5f5c84f4-60b7-49b9-a43b-fb4ed6ba82db   swap       swap
/dev/sda5        08360a3e-b322-42a6-b4fd-b6bde36c7779   xfs        /home
/dev/sda6        1FDFB81E6C7C5C94                       ntfs       EXTRA
/dev/sda7        44A768FA34300A40                       ntfs       MOVIES
/dev/sda8        29E7D61D7C745A57                       ntfs       SONGS
/dev/sda9        3D780A463A2B2C09                       ntfs       VIDEOS
/dev/sdb1        1118-2720                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec 23 19:50 ata-PLDS_DVD+_-RW_DS-8A5SH_1053000700402 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec 23 20:41 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 23 20:21 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Dec 23 19:50 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part12 -> ../../sda12
lrwxrwxrwx 1 root root 10 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 23 19:50 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 23 20:07 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 23 20:07 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Dec 23 20:42 ata-WDC_WD5000BPVT-75HXZT3_WD-WXK1A61C9198-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Dec 23 20:41 usb-SanDisk_SanDisk_Ultra_A20052B68EA7EE58-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Dec 23 19:50 usb-SanDisk_SanDisk_Ultra_A20052B68EA7EE58-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Dec 23 20:41 wwn-0x50014ee60169cb70 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 23 20:21 wwn-0x50014ee60169cb70-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Dec 23 20:42 wwn-0x50014ee60169cb70-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Dec 23 20:42 wwn-0x50014ee60169cb70-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Dec 23 19:50 wwn-0x50014ee60169cb70-part12 -> ../../sda12
lrwxrwxrwx 1 root root 10 Dec 23 20:42 wwn-0x50014ee60169cb70-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 23 19:50 wwn-0x50014ee60169cb70-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 23 20:07 wwn-0x50014ee60169cb70-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 23 20:07 wwn-0x50014ee60169cb70-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 23 20:42 wwn-0x50014ee60169cb70-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 23 20:42 wwn-0x50014ee60169cb70-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Dec 23 20:42 wwn-0x50014ee60169cb70-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Dec 23 20:42 wwn-0x50014ee60169cb70-part9 -> ../../sda9

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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

menuentry "Try elementary OS without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install elementary OS" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5505/mounts) leaked on lvs invocation. Parent PID 17680: bash
File descriptor 63 (pipe:[42983]) leaked on lvs invocation. Parent PID 17680: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-12-23__20h40 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (elementary OS Freya, freya, elementary OS, x86_64)
CPU op-mode(s):        32-bit, 64-bit
boot=casper cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz
ls: cannot access /home/usr/.config: No such file or directory
ls sda1:
@

os-prober
/dev/sda2:Windows 7 (loader):Windows:chain


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="c6df7d2b-ff85-ce45-a338-7f926d2e538b" TYPE="ext2"
/dev/sda1: UUID="637faed1-16b4-4ce4-8a48-e351e80fd892" UUID_SUB="8c14edc0-7450-41c4-9517-da434f6f06fe" TYPE="btrfs" LABEL="root"
/dev/sda2: LABEL="Windows7" UUID="548B3E37787C1377" TYPE="ntfs"
/dev/sda3: UUID="091A-0966" TYPE="vfat"
/dev/sda4: UUID="5f5c84f4-60b7-49b9-a43b-fb4ed6ba82db" TYPE="swap" LABEL="swap"
/dev/sda5: UUID="08360a3e-b322-42a6-b4fd-b6bde36c7779" TYPE="xfs" LABEL="/home"
/dev/sda6: LABEL="EXTRA" UUID="1FDFB81E6C7C5C94" TYPE="ntfs"
/dev/sda7: LABEL="MOVIES" UUID="44A768FA34300A40" TYPE="ntfs"
/dev/sda8: LABEL="SONGS" UUID="29E7D61D7C745A57" TYPE="ntfs"
/dev/sda9: LABEL="VIDEOS" UUID="3D780A463A2B2C09" TYPE="ntfs"
/dev/sda10: LABEL="W-STORE" UUID="3E8B0C3B2C21FB69" TYPE="ntfs"
/dev/sda11: LABEL="L-STORE" UUID="7FD004415E7E2705" TYPE="ntfs"
/dev/sda12: LABEL="Backup" UUID="9e57f035-351a-4965-9c57-1f76234d7b64" TYPE="ext4"
/dev/sdb1: LABEL="UUI" UUID="1118-2720" TYPE="vfat"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/Bootx64.efi

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.
sda5	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sda6	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.
sda7	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda7.
sda8	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda8.
sda9	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda9.
sda10	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda10.
sda11	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda11.
sda12	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda12.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000BPVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  32.2GB  32.2GB  btrfs                 msftdata
2      32.2GB  116GB   83.6GB  ntfs                  msftdata
3      116GB   116GB   107MB   fat32                 boot
4      116GB   118GB   2049MB  linux-swap(v1)        msftdata
5      118GB   133GB   14.9GB  xfs                   msftdata
6      133GB   144GB   10.7GB  ntfs                  msftdata
7      144GB   251GB   107GB   ntfs                  msftdata
8      251GB   358GB   107GB   ntfs                  msftdata
9      358GB   412GB   53.7GB  ntfs                  msftdata
10      412GB   439GB   26.8GB  ntfs                  msftdata
11      439GB   466GB   26.8GB  ntfs                  msftdata
12      466GB   500GB   34.3GB  ext4                  msftdata


Model: SanDisk SanDisk Ultra (scsi)
Disk /dev/sdb: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      1024B  15.9GB  15.9GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA WDC WD5000BPVT-7;
1:1049kB:32.2GB:32.2GB:btrfs::msftdata;
2:32.2GB:116GB:83.6GB:ntfs::msftdata;
3:116GB:116GB:107MB:fat32::boot;
4:116GB:118GB:2049MB:linux-swap(v1)::msftdata;
5:118GB:133GB:14.9GB:xfs::msftdata;
6:133GB:144GB:10.7GB:ntfs::msftdata;
7:144GB:251GB:107GB:ntfs::msftdata;
8:251GB:358GB:107GB:ntfs::msftdata;
9:358GB:412GB:53.7GB:ntfs::msftdata;
10:412GB:439GB:26.8GB:ntfs::msftdata;
11:439GB:466GB:26.8GB:ntfs::msftdata;
12:466GB:500GB:34.3GB:ext4::msftdata;

BYT;
/dev/sdb:15.9GB:scsi:512:512:msdos:SanDisk SanDisk Ultra;
1:1024B:15.9GB:15.9GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          465.8G
sda1  part btrfs       30G root
sda2  part ntfs      77.9G Windows7
sda3  part vfat       102M
sda4  part swap       1.9G swap
sda5  part xfs       13.9G /home
sda6  part ntfs        10G EXTRA
sda7  part ntfs       100G MOVIES
sda8  part ntfs       100G SONGS
sda9  part ntfs        50G VIDEOS
sda10 part ntfs        25G W-STORE
sda11 part ntfs        25G L-STORE
sda12 part ext4        32G Backup
sdb   disk           14.8G
sdb1  part vfat      14.8G UUI
sr0   rom            1024M
loop0 loop squashfs 817.1M
loop1 loop ext2       516M casper-rw

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         /mnt/boot-sav/sda6
sda7     1  0  0         /mnt/boot-sav/sda7
sda8     1  0  0         /mnt/boot-sav/sda8
sda9     1  0  0         /mnt/boot-sav/sda9
sda10    1  0  0         /mnt/boot-sav/sda10
sda11    1  0  0         /mnt/boot-sav/sda11
sda12    1  0  0         /mnt/boot-sav/sda12
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs
loop1    1  0  0


=================== mount:
aufs on / type aufs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=elementary)
/dev/sda1 on /mnt/boot-sav/sda1 type btrfs (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type xfs (rw)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /mnt/boot-sav/sda8 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /mnt/boot-sav/sda9 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda10 on /mnt/boot-sav/sda10 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda11 on /mnt/boot-sav/sda11 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda12 on /mnt/boot-sav/sda12 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda10 sda11 sda12 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fb1 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 input kmsg kvm log mapper mcelog media0 mei0 mem memory_bandwidth net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda10 sda11 sda12 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 c0 03  |........?....(..|
00000020  00 00 00 00 80 00 80 00  85 c7 bc 09 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff 28 04 00 00 00 00 00  |.........(......|
00000040  f6 00 00 00 01 00 00 00  77 13 7c 78 37 3e 8b 54  |........w.|x7>.T|
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
00000000  eb 58 90 50 4b 57 49 4e  34 2e 31 00 02 02 20 00  |.X.PKWIN4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 86 ef 7c 0d  |........?.....|.|
00000020  cd 2f 03 00 2a 03 00 00  00 00 00 00 02 00 00 00  |./..*...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 66 09 1a 09 4e  4f 20 4e 41 4d 45 20 20  |..)f...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 4e 54  |..............NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 7a 0f  |........?.... z.|
00000020  00 00 00 00 80 00 80 00  ff ff 3f 01 00 00 00 00  |..........?.....|
00000030  04 00 00 00 00 00 00 00  ff ff 13 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  94 5c 7c 6c 1e b8 df 1f  |.........|l....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 ba 10  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff ff 7f 0c 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff ff c7 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  40 0a 30 34 fa 68 a7 44  |........@.04.h.D|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda8
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 3a 1d  |........?....0:.|
00000020  00 00 00 00 80 00 80 00  ff ff 7f 0c 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff ff c7 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  57 5a 74 7c 1d d6 e7 29  |........WZt|...)|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda9
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 ba 29  |........?....8.)|
00000020  00 00 00 00 80 00 80 00  ff ff 3f 06 00 00 00 00  |..........?.....|
00000030  04 00 00 00 00 00 00 00  ff ff 63 00 00 00 00 00  |..........c.....|
00000040  f6 00 00 00 01 00 00 00  09 2c 2b 3a 46 0a 78 3d  |.........,+:F.x=|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda10
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 fa 2f  |........?....@./|
00000020  00 00 00 00 80 00 80 00  ff ff 1f 03 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff ff 31 00 00 00 00 00  |..........1.....|
00000040  f6 00 00 00 01 00 00 00  69 fb 21 2c 3b 0c 8b 3e  |........i.!,;..>|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda11
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1a 33  |........?....H.3|
00000020  00 00 00 00 80 00 80 00  ff ff 1f 03 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff ff 31 00 00 00 00 00  |..........1.....|
00000040  f6 00 00 00 01 00 00 00  05 27 7e 5e 41 04 d0 7f  |.........'~^A...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
aufs           aufs      500M  457M   18M  97% /
udev           devtmpfs  5.9G   12K  5.9G   1% /dev
tmpfs          tmpfs     1.2G  1.4M  1.2G   1% /run
/dev/sdb1      vfat       15G  1.4G   14G  10% /cdrom
/dev/loop0     squashfs  818M  818M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G   28K  5.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     5.9G  144K  5.9G   1% /run/shm
none           tmpfs     100M   28K  100M   1% /run/user
/dev/sda1      btrfs      31G   22G  7.7G  74% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    78G   55G   24G  70% /mnt/boot-sav/sda2
/dev/sda3      vfat      102M  5.9M   96M   6% /mnt/boot-sav/sda3
/dev/sda5      xfs        14G  8.5G  5.5G  61% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    10G  2.9G  7.2G  29% /mnt/boot-sav/sda6
/dev/sda7      fuseblk   100G   84G   17G  84% /mnt/boot-sav/sda7
/dev/sda8      fuseblk   100G   74G   27G  74% /mnt/boot-sav/sda8
/dev/sda9      fuseblk    50G   27G   24G  53% /mnt/boot-sav/sda9
/dev/sda10     fuseblk    25G   22G  3.5G  87% /mnt/boot-sav/sda10
/dev/sda11     fuseblk    25G   18G  7.7G  70% /mnt/boot-sav/sda11
/dev/sda12     ext4       32G   27G  3.2G  90% /mnt/boot-sav/sda12

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004ee53

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.9 GB, 15854469120 bytes
255 heads, 63 sectors/track, 1927 cylinders, total 30965760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2    30965759    15482879    c  W95 FAT32 (LBA)


No OS or WinEFI system
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
No OS or WinEFI system
No OS or WinEFI system
No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda1
fsck from util-linux 2.20.1
/sbin/fsck.btrfs: Btrfs file system.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda2
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda3
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda5
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda6
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda7
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda8
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda9
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda10
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda11
fsck from util-linux 2.20.1

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


fsck -fyM /dev/sda12
fsck from util-linux 2.20.1

Boot successfully repaired.

You can now reboot your computer.
```

When I mount my root partition at /mnt then the root directory I find here is @/ and I guess this is the reason it is not repairing properly. Another thing is boot-repair's advanced tabs grub options, MBR options are blank.
[IMG]http://i.imgur.com/eMvHy35.png[/IMG]

Thank You

---

### Post by leunam12 on 2015-12-24
I am no expert but it looks like a big mess to me. Did you want to end up with all those partitions with unallocated space in between or did it just happen? well, I guess it doesn't matter. Why don't you just backup your data and format your hard drive and start from zero creating the partitions that you want just like you want them? Ubuntu was not originally installed to boot in UEFI mode, I don't know if you can change a partition table like you did and still be bootable without re-installing.

---

### Post by eshant_engineer on 2015-12-24
Well it is possible with Ubuntu as well without losing data and here is the [guide]("http://askubuntu.com/questions/84501/how-can-i-change-convert-a-ubuntu-mbr-drive-to-a-gpt-and-make-ubuntu-boot-from")

---

### Post by yancek on 2015-12-24
The boot repair output refers to windows 8, vista and xp.  Do you have all those windows systems installed?  Partition sda3 is a FAT32 partition.  That would be the EFI partition and it only has windows files, none for Ubuntu or elementary.  In addition to that, it shows several Linux partitions with different filesystems but doesn't show any boot files normally shown in the boot repair output.  If you use GPT with windows, you must use UEFI and you must also install other operating systems UEFI and it doesn't look like your Linux was installed UEFI.

---

### Post by eshant_engineer on 2015-12-24
actually Windows 10(Windows 7 label) only Windows that is installed, you are seeing XP because of EFI partition created after conversion which is of FAT32 type and Vista because of partitions of NTFS type. 

Yes Ubuntu root which u can see in gparted was installed long back before the transition of partition table. I heard that we can have legacy boot with UEFI enabled bios.

---

### Post by oldfred on 2015-12-24
I used legacy/BIOS boot with gpt since 10.10 on my old BIOS only system. Back then I still had XP, but it was on a separate MBR(msdos) partitioned drive.

But Windows only boots in UEFI mode from gpt partitioned drives and only in BIOS mode from MBR partitioned drives.
Best to have all systems booting in same boot mode, but Windows requirements pretty much set which you should use. And you can only dual boot from UEFI boot menu or one time boot key if systems not in same boot mode. Or grub only boots systems installed in same boot mode as Ubuntu is installed UEFI or BIOS.

---

### Post by grahammechanical on 2015-12-24
Is Ubuntu installed on sda1, the btrfs partition?

I can tell you this from my experiments with btrfs the other year. Grub in an OS installed on a btrfs partition will recognise Linux kernels on that partition. But Grub will not recognise Linux kernels on other btrfs partitions. And Grub installed in an OS on other partitions (btrfs or Ext4) will not recognise Linux kernels in btrfs partitions.

And it seems that Boot Repair is also having difficulty finding Linux kernels on sda1 as boot repair says this

> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

One more thing. It used to be that when installing Ubuntu on  btfs partition there had to be at least 1 Mib of free space at the beginning of the disk otherwise Grub will not install

> When installing Ubuntu in one large btrfs-Partition without an extra  boot-partition, take care to keep about 1 Mib space free at the  beginning of the disk. This is possible using the partition manager in  the Ubuntu installer. When there is not this space, the installer fails  at the end when trying to install Grub!

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Regards.

---

### Post by eshant_engineer on 2015-12-24
> **grahammechanical said:**
> Is Ubuntu installed on sda1, the btrfs partition?

I can tell you this from my experiments with btrfs the other year. Grub in an OS installed on a btrfs partition will recognise Linux kernels on that partition. But Grub will not recognise Linux kernels on other btrfs partitions. And Grub installed in an OS on other partitions (btrfs or Ext4) will not recognise Linux kernels in btrfs partitions.

And it seems that Boot Repair is also having difficulty finding Linux kernels on sda1 as boot repair says this



Regards.

Yes, it is the root partition. But I think it is not able to find because when I mount root partition at /mnt then I don't see root FS at /mnt but at  /mnt/@/. I think this is unusual, am I right?

---

