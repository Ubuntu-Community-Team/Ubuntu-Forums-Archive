---
title: "Help solving boot issues"
date: 2015-10-16
forum: General Help
---

### Post by ssnake_br on 2015-10-16
Hi guys.

Well, I need some help (Note, I slept 6 hours in the past three days, so its possible that I forgot some obvious stuff while installing the OS).
I need to simple install 14.04 Server in a 1TB harddisk, 50GB for OS (encrypted), 940GB for data (encrypted).

How I do it: (Ubuntu menu for disc partitioning -> Manual)
250MB For EFI Boot;
500MB ext4 for /boot
50GB Encrypted, with ext4 partition (sda3), mounted on /
950GB Encrypted, with ext4 partition (sda4) mounted on /data
[IMG]http://i.imgur.com/3STR12W.jpg[/IMG]

All went well, instalation occured with no warnings.
At first boot, grub loads, I am prompted for the password, and it says: "unknown fstype, bad password, blah blah blah".
I rebooted and tried to mount both partitions (sda3 and sda4), and after unlocking them, I am noticed that there is no filesystem in the partitions.

This is driving me nuts.

---

### Post by oldfred on 2015-10-16
I do not know LVM nor encryption, but why does it mention RAID. 
Is system also RAID?

You will need Ubuntu live installer or desktop version. Which is good to have to make repairs that you may not be able to do from server type install.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ssnake_br on 2015-10-17
> **oldfred said:**
> I do not know LVM nor encryption, but why does it mention RAID. 
Is system also RAID?

You will need Ubuntu live installer or desktop version. Which is good to have to make repairs that you may not be able to do from server type install.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I will try that and report back, Thank you!

---

### Post by ssnake_br on 2015-10-21
> **oldfred said:**
> I do not know LVM nor encryption, but why does it mention RAID. 
Is system also RAID?

You will need Ubuntu live installer or desktop version. Which is good to have to make repairs that you may not be able to do from server type install.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Hi @oldfred.

I simplified some things:
I have 250MB for EFI, 500MB ext4 for /boot, 60GB encrypted (50GB ext4 for root and 10GB for swap)

My boot info:

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or /mnt/BootInfo/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 2038760. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 already mounted or /mnt/BootInfo/sdb1 busy
mount: /dev/sdb2 already mounted or /mnt/BootInfo/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       487,423       485,376 EFI System partition
/dev/sda2         487,424     1,464,319       976,896 Data partition (Linux)
/dev/sda3       1,464,320   118,650,879   117,186,560 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7862 MB, 7862353920 bytes
255 heads, 63 sectors/track, 955 cylinders, total 15356160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     2,060,287     2,060,288   0 Empty
/dev/sdb2           2,038,760     2,043,303         4,544  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1               0     2,060,231     2,060,232 Data partition (Windows/Linux)
/dev/sdb2       2,038,760     2,043,303         4,544 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0BB0-7678                              vfat       
/dev/sda2        eb64ca30-eb74-4a58-a307-429374d31696   ext4       
/dev/sda3        ce765e56-fda9-4e95-a644-056729b1e870   crypto_LUKS 
/dev/sdb1                                               iso9660    Ubuntu 14.04.3 LTS amd64
/dev/sdb2        B163-D4F2                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 21 21:03 ata-ST1000DM003-1ER162_Z4Y8R8WC -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 21 20:55 ata-ST1000DM003-1ER162_Z4Y8R8WC-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 21 20:55 ata-ST1000DM003-1ER162_Z4Y8R8WC-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 21 20:59 ata-ST1000DM003-1ER162_Z4Y8R8WC-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 21 21:03 dm-name-luks-ce765e56-fda9-4e95-a644-056729b1e870 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Oct 21 21:03 dm-uuid-CRYPT-LUKS1-ce765e56fda94e95a644056729b1e870-luks-ce765e56-fda9-4e95-a644-056729b1e870 -> ../../dm-0
lrwxrwxrwx 1 root root  9 Oct 21 21:03 usb-Sony_Storage_Media_9B3001403200000267-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 21 20:55 usb-Sony_Storage_Media_9B3001403200000267-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 21 20:58 usb-Sony_Storage_Media_9B3001403200000267-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Oct 21 21:03 wwn-0x5000c5007bc5d86d -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 21 20:55 wwn-0x5000c5007bc5d86d-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 21 20:55 wwn-0x5000c5007bc5d86d-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 21 20:59 wwn-0x5000c5007bc5d86d-part3 -> ../../sda3

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
luks-ce765e56-fda9-4e95-a644-056729b1e870

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


============================= sda2/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
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
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  826eb035-dc03-4b03-8d1f-8a9eb0b2e520
else
  search --no-floppy --fs-uuid --set=root 826eb035-dc03-4b03-8d1f-8a9eb0b2e520
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=pt_BR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
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
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-826eb035-dc03-4b03-8d1f-8a9eb0b2e520' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  eb64ca30-eb74-4a58-a307-429374d31696
	else
	  search --no-floppy --fs-uuid --set=root eb64ca30-eb74-4a58-a307-429374d31696
	fi
	linux	/vmlinuz-3.19.0-25-generic.efi.signed root=UUID=826eb035-dc03-4b03-8d1f-8a9eb0b2e520 ro  
	initrd	/initrd.img-3.19.0-25-generic
}
submenu 'Opções avançadas para Ubuntu' $menuentry_id_option 'gnulinux-advanced-826eb035-dc03-4b03-8d1f-8a9eb0b2e520' {
	menuentry 'Ubuntu, com Linux 3.19.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-826eb035-dc03-4b03-8d1f-8a9eb0b2e520' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  eb64ca30-eb74-4a58-a307-429374d31696
		else
		  search --no-floppy --fs-uuid --set=root eb64ca30-eb74-4a58-a307-429374d31696
		fi
		echo	'Carregando Linux 3.19.0-25-generic ...'
		linux	/vmlinuz-3.19.0-25-generic.efi.signed root=UUID=826eb035-dc03-4b03-8d1f-8a9eb0b2e520 ro  
		echo	'Carregando ramdisk inicial ...'
		initrd	/initrd.img-3.19.0-25-generic
	}
	menuentry 'Ubuntu, with Linux 3.19.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-826eb035-dc03-4b03-8d1f-8a9eb0b2e520' {
		recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  eb64ca30-eb74-4a58-a307-429374d31696
		else
		  search --no-floppy --fs-uuid --set=root eb64ca30-eb74-4a58-a307-429374d31696
		fi
		echo	'Carregando Linux 3.19.0-25-generic ...'
		linux	/vmlinuz-3.19.0-25-generic.efi.signed root=UUID=826eb035-dc03-4b03-8d1f-8a9eb0b2e520 ro recovery nomodeset 
		echo	'Carregando ramdisk inicial ...'
		initrd	/initrd.img-3.19.0-25-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  b4 49 1e 00 00 00 00 00  fc 16 62 6a 00 00 80 00  |.I........bj....|
000001c0  01 00 00 3f e0 ed 00 00  00 00 00 70 1f 00 00 fe  |...?.......p....|
000001d0  ff ff ef fe ff ff e8 1b  1f 00 c0 11 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  5a 11 ea d3 c3 8a 85 e1  0a 12 cd 20 5c 08 03 d6  |Z.......... \...|
00000080  cd da b1 b8 40 02 06 3e  02 6f 06 30 0c 98 17 08  |....@..>.o.0....|
00000090  22 68 5f 1d a8 84 5e 46  96 92 82 72 98 2d f5 fe  |"h_...^F...r.-..|
000000a0  52 47 de d5 00 00 fc ee  63 65 37 36 35 65 35 36  |RG......ce765e56|
000000b0  2d 66 64 61 39 2d 34 65  39 35 2d 61 36 34 34 2d  |-fda9-4e95-a644-|
000000c0  30 35 36 37 32 39 62 31  65 38 37 30 00 00 00 00  |056729b1e870....|
000000d0  00 ac 71 f3 00 03 f4 24  94 d9 ad 6c a6 90 a9 c1  |..q....$...l....|
000000e0  5d 42 4f f6 d2 1e 49 e0  a1 59 df d2 7d dc fb 52  |]BO...I..Y..}..R|
000000f0  08 a5 fe d8 fe 46 76 6f  00 00 00 08 00 00 0f a0  |.....Fvo........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  b4 49 1e 00 00 00 00 00  fc 16 62 6a 00 00 80 00  |.I........bj....|
000001c0  01 00 00 3f e0 ed 00 00  00 00 00 70 1f 00 00 fe  |...?.......p....|
000001d0  ff ff ef fe ff ff e8 1b  1f 00 c0 11 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/12962/mounts) leaked on lvs invocation. Parent PID 19267: bash
File descriptor 63 (pipe:[50636]) leaked on lvs invocation. Parent PID 19267: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-10-21__21h03 ===================
boot-info version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
boot-info is executed in live-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda3 : Error code 32
mount -r /dev/sda3 /mnt/boot-sav/sda3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda3 : Error code 32
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="0BB0-7678" TYPE="vfat"
/dev/sda2: UUID="eb64ca30-eb74-4a58-a307-429374d31696" TYPE="ext4"
/dev/sda3: UUID="ce765e56-fda9-4e95-a644-056729b1e870" TYPE="crypto_LUKS"
/dev/sdb1: LABEL="Ubuntu 14.04.3 LTS amd64" TYPE="iso9660"
/dev/sdb2: SEC_TYPE="msdos" UUID="B163-D4F2" TYPE="vfat"

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda3 : Error code 32
mount -r /dev/sda3 /mnt/boot-sav/sda3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda3 : Error code 32
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.

dd: invalid number ‘0’
Warning: /var/log/boot-sav/log/2015-10-21__21h03boot-info25/sdb/current_mbr.img could not be created. Please report this message to boot.repair@gmail.com

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== sda2recordfail=1/grub/grubenv :
recordfail=1




=================== efibootmgr -v
BootCurrent: 000A
Timeout: 1 seconds
BootOrder: 0000,0009,000A,0001
Boot0000* ubuntu	HD(1,800,76800,e143b24c-4e91-4e65-87e2-1174afbb79d2)File(EFIUBUNTUSHIMX64.EFI)
Boot0001* Hard Drive 	BIOS(2,0,00)..GO..NO........O.S.T.1.0.0.0.D.M.0.0.3.-.1.E.R.1.6.2.................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .4.Z.8.Y.8.R.C.W........BO..NO........K.S.o.n.y. .S.t.o.r.a.g.e. .M.e.d.i.a.................:..Gd-.;.A..MQ..L.9.B.3.0.0.1.4.0.3.2.0.0.0.0.0.2.6.7........BO
Boot0009* ubuntu	HD(1,800,76800,e143b24c-4e91-4e65-87e2-1174afbb79d2)File(EFIUBUNTUGRUBX64.EFI)..BO
Boot000A* UEFI: (FAT) Sony Storage Media	ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(5,0)HD(1,1f1be8,11c0,6a6216fc)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	is-sepboot,	grubenv-ng	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda3	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda3.
sdb2	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb2.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	0 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
1      1049kB  250MB   249MB   fat32              boot
2      250MB   750MB   500MB   ext4
3      750MB   60.7GB  60.0GB


Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.

Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870: 60.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      17.4kB  50.0GB  50.0GB  ext4
2      50.0GB  60.0GB  9997MB  linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA ST1000DM003-1ER1;
1:1049kB:250MB:249MB:fat32::boot;
2:250MB:750MB:500MB:ext4::;
3:750MB:60.7GB:60.0GB:::;

Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.

BYT;
/dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870:60.0GB:dm:512:4096:gpt:Linux device-mapper (crypt);
1:17.4kB:50.0GB:50.0GB:ext4::;
2:50.0GB:60.0GB:9997MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE  FSTYPE     SIZE LABEL    MODEL    UUID
sda   disk           931.5G          ST1000DM
sda1  part  vfat       237M                   0BB0-7678
sda2  part  ext4       477M                   eb64ca30-eb74-4a58-a307-429374d31696
sda3  part  crypto_L  55.9G                   ce765e56-fda9-4e95-a644-056729b1e870
dm-0  crypt           55.9G
sdb   disk  iso9660    7.3G Ubuntu 14.04.3 LTS amd64
Storage
sdb1  part  iso9660   1006M Ubuntu 14.04.3 LTS amd64

sdb2  part  vfat       2.2M                   B163-D4F2
loop0 loop  squashfs 962.1M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0
dm-0     1  0  0 running
sdb      1  0  1 running
sdb1     1  0  1
sdb2     1  0  1
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type ext4 (rw)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 input kmsg log lp0 mapper mcelog mei0 mem memory_bandwidth net network_latency network_throughput null parport0 port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control luks-ce765e56-fda9-4e95-a644-056729b1e870

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 01 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 68 07 00 96 0e 00 00  00 00 00 00 02 00 00 00  |.h..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 78 76 b0 0b 4e  4f 20 4e 41 4d 45 20 20  |..)xv..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 3c 90 6d 6b 66 73 2e  66 61 74 00 02 04 01 00  |.<.mkfs.fat.....|
00000010  02 00 02 c0 11 f8 04 00  20 00 40 00 00 00 00 00  |........ .@.....|
00000020  00 00 00 00 80 00 29 f2  d4 63 b1 4e 4f 20 4e 41  |......)..c.NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 32 20 20 20 0e 1f  |ME    FAT12   ..|
00000040  be 5b 7c ac 22 c0 74 0b  56 b4 0e bb 07 00 cd 10  |.[|.".t.V.......|
00000050  5e eb f0 32 e4 cd 16 cd  19 eb fe 54 68 69 73 20  |^..2.......This |
00000060  69 73 20 6e 6f 74 20 61  20 62 6f 6f 74 61 62 6c  |is not a bootabl|
00000070  65 20 64 69 73 6b 2e 20  20 50 6c 65 61 73 65 20  |e disk.  Please |
00000080  69 6e 73 65 72 74 20 61  20 62 6f 6f 74 61 62 6c  |insert a bootabl|
00000090  65 20 66 6c 6f 70 70 79  20 61 6e 64 0d 0a 70 72  |e floppy and..pr|
000000a0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 74  |ess any key to t|
000000b0  72 79 20 61 67 61 69 6e  20 2e 2e 2e 20 0d 0a 00  |ry again ... ...|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   3.9G   84M  3.8G   3% /
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     787M  1.3M  785M   1% /run
/dev/sdb       iso9660  1006M 1006M     0 100% /cdrom
/dev/loop0     squashfs  963M  963M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  1.4M  3.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G   76K  3.9G   1% /run/shm
none           tmpfs     100M   72K  100M   1% /run/user
/dev/sda1      vfat      234M  3.4M  230M   2% /mnt/boot-sav/sda1
/dev/sda2      ext4      454M   54M  374M  13% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 7862 MB, 7862353920 bytes
255 heads, 63 sectors/track, 955 cylinders, total 15356160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6216fc

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0     2060287     1030144    0  Empty
/dev/sdb2         2038760     2043303        2272   ef  EFI (FAT-12/16/32)

Disk /dev/sdb1: 1054 MB, 1054867456 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2060288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a6216fc

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0     2060287     1030144    0  Empty
/dev/sdb1p2         2038760     2043303        2272   ef  EFI (FAT-12/16/32)

Disk /dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870: 60.0 GB, 59997421568 bytes
255 heads, 63 sectors/track, 7294 cylinders, total 117182464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/mapper/luks-ce765e56-fda9-4e95-a644-056729b1e870p1               1   117182463    58591231+  ee  GPT
Partition 1 does not start on physical sector boundary.


No OS or WinEFI system
gui-tab-other.sh: line 94: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```
I tried boot repair with no success, and tried to mount the encrypted volume via live-cd, but gets error with invalid filesystem message (but it unlocks).
I am not using RAID, but I am willing to do.

I am going crazy with this.

Thank you.

---

### Post by oldfred on 2015-10-21
LVM with encryption is pretty advanced. I do not use it as complicated and I do not need encryption on desktop.RAID is even more advanced, usually with servers but a few have it on dual drive desktops.

Some links, you may need to use live installer, mount LVM partitions if possible and run fsck on the ext4 partitions inside the LVM.
see the first sections up to where it discusses resizing. It mentions just before the resize instructions that you at that point can run fsck.

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)


 sudo e2fsck -f /dev/mapper/{your lvm partition}

The UUID shown in the grub boot stanza is not shown, but none of the script shows the LVM mapper. Or is this just an encrypted partition that you encrypted differently?

---

### Post by ssnake_br on 2015-10-21
Thank you for the attention.
I am not using LVM, just trying to simple create and encrypt volumes, but I gave up. I will use guided LVM + Encryption and I bet this will work.
Its sad, since I was planing to create separated volumes (root and data), but I need this server online by tomorrow.

---

