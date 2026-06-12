---
title: "Windows 8 not showing up in Grub..."
date: 2014-04-20
forum: General Help
---

### Post by killabee44 on 2014-04-20
Hi all,

I installed Ubuntu 12.04 on a machine that had Windows 8 installed first. But now Windows 8 is not on the Grub list of Operating Systems. 

I know for a fact that Winidows 8 is located in SDD5 and that it works fine. Or at least it used to. 

My Ubuntu 12.04 install is on SDA1 and boots perfectly well. 

Here is the output of boot-repair:

Thanks for your help!

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *         94,208    99,899,391    99,805,184  83 Linux
/dev/sda2          99,899,392   295,194,623   195,295,232  83 Linux
/dev/sda3         295,211,008   315,006,959    19,795,952  82 Linux swap / Solaris
/dev/sda4         315,006,974 4,237,991,935 3,922,984,962   f W95 Extended (LBA)
/dev/sda5         315,006,976 4,237,991,935 3,922,984,960  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 3,907,024,895 3,907,022,848  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   283,273,215   283,273,153   7 NTFS / exFAT / HPFS
/dev/sdd2         283,273,216   488,396,799   205,123,584   5 Extended
/dev/sdd5    *    283,275,264   488,396,799   205,121,536   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63 2,930,272,064 2,930,272,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        e7228883-ef69-4ba4-b55a-88b615dd17fb   ext4       
/dev/sda2        fbef488f-ccd0-4b81-9ca2-5d469bdf16ab   ext4       
/dev/sda3        02c7a2a4-97de-4c3d-b8c2-1288a9b14de2   swap       
/dev/sda5        eba8e2d5-b229-4412-a0b8-b61723c08710   ext4       
/dev/sdb1        1626c7f8-7979-4068-b182-829ef8d42bb9   ext4       2tbCaviar
/dev/sdc1        B420A64C20A61600                       ntfs       250Backup
/dev/sdd1        70B4D348B4D31008                       ntfs       250Newsleecher
/dev/sdd5        6C2CCC532CCC1A4A                       ntfs       
/dev/sde1        2AA91D326971D565                       ntfs       Music and Video

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	linux	/boot/vmlinuz-3.2.0-60-generic-pae root=UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb ro   quiet splash nomodeset $vt_handoff
	initrd	/boot/initrd.img-3.2.0-60-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	echo	'Loading Linux 3.2.0-60-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-60-generic-pae root=UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-60-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb ro   quiet splash nomodeset $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root e7228883-ef69-4ba4-b55a-88b615dd17fb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fbef488f-ccd0-4b81-9ca2-5d469bdf16ab /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=02c7a2a4-97de-4c3d-b8c2-1288a9b14de2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.257919312 = 34.636677120   boot/grub/grub.cfg                             1
  16.215213776 = 17.410953216   boot/grub/core.img                             1
  16.237094879 = 17.434447872   boot/vmlinuz-3.2.0-23-generic-pae              1
   1.471485138 = 1.579995136    boot/vmlinuz-3.2.0-60-generic-pae              2
  16.237094879 = 17.434447872   vmlinuz                                        1
   2.378391266 = 2.553778176    boot/initrd.img-3.2.0-23-generic-pae           1
   2.098655701 = 2.253414400    boot/initrd.img-3.2.0-60-generic-pae           2
   2.378391266 = 2.553778176    initrd.img                                     1
   2.378391266 = 2.553778176    initrd.img.old                                 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  83 f0 7d 76 f7 d5 ff 5f  33 e2 7d 76 f7 d5 ff 5f  |..}v..._3.}v..._|
00000010  16 e5 d5 73 79 5b df db  21 a9 d5 73 79 5b df db  |...sy[..!..sy[..|
00000020  64 8e d5 73 79 5b df db  c9 ac d5 73 79 5b df db  |d..sy[.....sy[..|
00000030  aa c8 d5 73 79 5b df db  91 9f d5 73 79 5b df db  |...sy[.....sy[..|
00000040  7b 20 ff 7d d7 fd eb 17  a5 5d ff 7d d7 fd eb 17  |{ .}.....].}....|
00000050  ff ff d7 ff f7 9f 1e 6f  e1 21 d7 ff f7 9f 1e 6f  |.......o.!.....o|
00000060  24 f0 bb df 7e 97 9b ff  31 65 bb df 7e 97 9b ff  |$...~...1e..~...|
00000070  f5 92 bb df 7e 97 9b ff  c2 d4 bb df 7e 97 9b ff  |....~.......~...|
00000080  0d b8 ff ff f6 ff ff 37  35 58 ff ff f6 ff ff 37  |.......75X.....7|
00000090  d8 a1 ff 95 f7 ef d5 c1  a3 06 ff 95 f7 ef d5 c1  |................|
000000a0  09 03 ff 95 f7 ef d5 c1  5d ff de 78 dd dd fd 5d  |........]..x...]|
000000b0  ad 86 de 78 dd dd fd 5d  fd f5 9f 9f f7 f7 77 fd  |...x...]......w.|
000000c0  a1 47 9f 9f f7 f7 77 fd  88 af 9f 9f f7 f7 77 fd  |.G....w.......w.|
000000d0  c0 93 9f 9f f7 f7 77 fd  14 7c 9f 9f f7 f7 77 fd  |......w..|....w.|
000000e0  f7 46 9f 9f f7 f7 77 fd  8e d6 9f 9f f7 f7 77 fd  |.F....w.......w.|
000000f0  7e d3 db 5d 7f 7f f7 53  d3 97 d7 dd 57 7f 7d f5  |~..]...S....W.}.|
00000100  15 89 d7 dd 57 7f 7d f5  2f e7 d7 dd 57 7f 7d f5  |....W.}./...W.}.|
00000110  1e 80 d7 dd 57 7f 7d f5  ab 77 d7 dd 57 7f 7d f5  |....W.}..w..W.}.|
00000120  40 fc d7 dd 57 7f 7d f5  a6 8f db 7e 7f ff 5f fd  |@...W.}....~.._.|
00000130  d6 7d fb d5 e7 96 c7 fd  f5 2a fb d5 e7 96 c7 fd  |.}.......*......|
00000140  2b c8 fb d5 e7 96 c7 fd  e6 7d fb d5 e7 96 c7 fd  |+........}......|
00000150  b6 f6 fb d5 e7 96 c7 fd  04 c8 bd e5 f5 d7 6f 7f  |..............o.|
00000160  d6 b1 bd e5 f5 d7 6f 7f  c1 64 e5 9d d7 dc 57 77  |......o..d....Ww|
00000170  f5 b8 e5 9d d7 dc 57 77  a3 24 e5 9d d7 dc 57 77  |......Ww.$....Ww|
00000180  fe 4d 77 f7 ff f4 f5 f7  aa 2b 77 f7 ff f4 f5 f7  |.Mw......+w.....|
00000190  9d 9b 77 f7 ff f4 f5 f7  c7 5e 77 f7 ff f4 f5 f7  |..w......^w.....|
000001a0  55 fd ed b7 f7 dd d5 df  ec 99 ed b7 f7 dd d5 df  |U...............|
000001b0  4d 7f 9d 55 7d fc 1f 8f  d5 ff 75 7f 53 7f 00 fe  |M..U}.....u.S...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 00 d4 e9 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdd2

00000000  ce ef 3c 30 ef cd 3d f8  30 f4 bb ee 94 86 f3 4f  |..<0..=.0......O|
00000010  eb 2d 76 e7 4e ab 86 48  4e cf ed 1c 1e 73 65 ab  |.-v.N..HN....se.|
00000020  3e f2 7f 90 1f 3a 56 71  00 10 57 a3 99 68 61 09  |>....:Vq..W..ha.|
00000030  82 90 cd e6 6e fb 72 01  17 7b 95 f8 a7 ca 4a 94  |....n.r..{....J.|
00000040  9a dd 52 03 ec 4b 80 0d  71 2d 19 34 dc 9f bf 3d  |..R..K..q-.4...=|
00000050  c8 a6 c0 22 5f 9c 4d c7  31 8a e9 a1 87 cf 2e 7e  |..."_.M.1......~|
00000060  a7 27 9c 18 50 fd 87 98  d4 bf 4c 04 52 3f 79 7b  |.'..P.....L.R?y{|
00000070  91 fe 8a db e8 b7 aa 9e  f9 ed 5a f1 3a ee d9 6b  |..........Z.:..k|
00000080  09 39 21 a5 09 ba 04 10  42 9b a6 7a fa e4 ae 56  |.9!.....B..z...V|
00000090  87 3b f5 25 e9 df b0 6a  77 07 da 85 3f 9f 17 e0  |.;.%...jw...?...|
000000a0  00 14 a7 ac 2b 1c 81 d1  8d fd 16 b8 bc ac b4 7c  |....+..........||
000000b0  19 01 8a 29 ed 2e db b1  be 42 8c 3b fd 5e 1c bf  |...).....B.;.^..|
000000c0  be 43 b6 0c 5f 3a c6 2c  a9 be 3f 68 bb 35 b3 08  |.C.._:.,..?h.5..|
000000d0  78 08 d1 88 e6 63 ad c2  f0 35 74 fc 3b 59 0e 51  |x....c...5t.;Y.Q|
000000e0  93 be 2b 8e 1e 64 3a ec  db 5f 0c 2a 44 c4 a2 31  |..+..d:.._.*D..1|
000000f0  2c 73 99 c3 70 1d bd 6b  3b f1 13 15 e7 1f 5e 82  |,s..p..k;.....^.|
00000100  7e 48 55 ff 24 7f 6a 8f  82 04 20 07 90 2d 16 7f  |~HU.$.j... ..-..|
00000110  ee c8 22 cd 18 07 16 47  d9 04 5a 32 62 a2 cb 6c  |.."....G..Z2b..l|
00000120  74 3f 5d ea ca 9b 0e 90  12 65 a7 5a cb 6f 3c 5d  |t?]......e.Z.o<]|
00000130  ad 68 32 ab 69 49 83 99  56 43 2e 2b 72 9c 5e bb  |.h2.iI..VC.+r.^.|
00000140  8e 83 ea e6 68 d9 8f 11  bd ae 0b 20 f0 f8 a9 f0  |....h...... ....|
00000150  d0 d2 9c 6a 6b 0f 3c 8b  cf 89 3a 1b 2f f9 a3 4b  |...jk.<...:./..K|
00000160  52 06 12 0f a8 be 3a b9  72 6f 4f 62 45 d9 fe a2  |R.....:.roObE...|
00000170  df 35 75 c2 1f bb 3a 96  76 5c 41 70 10 f1 fb 73  |.5u...:.v\Ap...s|
00000180  f6 94 a8 c7 82 da ac d3  60 f1 e9 36 5d 5c 15 87  |........`..6]\..|
00000190  cc 5b 84 1b 0f 5f f6 76  81 e8 8b fc 5f 70 ec 4b  |.[..._.v...._p.K|
000001a0  85 b2 bd dc a8 6d 78 5f  aa b6 87 ec b7 54 c2 6f  |.....mx_.....T.o|
000001b0  7c 45 0c 11 73 5b 59 60  72 56 8f 7b b4 30 80 fe  ||E..s[Y`rV.{.0..|
000001c0  ff ff 07 fe ff ff 00 08  00 00 00 e8 39 0c 00 00  |............9...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-04-20__00h50 ===================
boot-repair version : 3.199~ppa40~precise
boot-sav version : 3.199~ppa40~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.199~ppa40~precise
boot-repair is executed in installed-session (Ubuntu 12.04.4 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.2.0-60-generic-pae root=UUID=e7228883-ef69-4ba4-b55a-88b615dd17fb ro quiet splash nomodeset
Unmount sde1 from /media/Music and Video to avoid space incompatibilities

=================== os-prober:
/dev/sda1:The OS now in use - Ubuntu 12.04.4 LTS CurrentSession:linux

=================== blkid:
/dev/sda5: UUID="eba8e2d5-b229-4412-a0b8-b61723c08710" TYPE="ext4"
/dev/sdb1: LABEL="2tbCaviar" UUID="1626c7f8-7979-4068-b182-829ef8d42bb9" TYPE="ext4"
/dev/sdc1: LABEL="250Backup" UUID="B420A64C20A61600" TYPE="ntfs"
/dev/sdd1: LABEL="250Newsleecher" UUID="70B4D348B4D31008" TYPE="ntfs"
/dev/sdd5: UUID="6C2CCC532CCC1A4A" TYPE="ntfs"
/dev/sda1: UUID="e7228883-ef69-4ba4-b55a-88b615dd17fb" TYPE="ext4"
/dev/sda2: UUID="fbef488f-ccd0-4b81-9ca2-5d469bdf16ab" TYPE="ext4"
/dev/sda3: UUID="02c7a2a4-97de-4c3d-b8c2-1288a9b14de2" TYPE="swap"
/dev/sde1: LABEL="Music and Video" UUID="2AA91D326971D565" TYPE="ntfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sdd5.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr 19 16:50 grub.d
total 60
-rwxr-xr-x 1 root root 7806 Dec  6 05:07 00_header
-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7877 Dec  6 05:07 10_linux
-rwxr-xr-x 1 root root 6449 Dec  6 05:07 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 6675 Dec  6 05:07 30_os-prober
-rwxr-xr-x 1 root root 1388 Dec  6 05:07 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Apr 17  2012 40_custom
-rwxr-xr-x 1 root root   95 Apr 17  2012 41_custom
-rw-r--r-- 1 root root  483 Apr 17  2012 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
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



=================== UEFI/Legacy mode:
This installed-session is not EFI-compatible.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	.
sda5	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdc1.
sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdd1.
sdd5	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdd5.
sda2	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/home.
sde1	: sde,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sde1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	63 sectors * 512 bytes
sdd	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes
sde	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	no-os,	63 sectors * 512 bytes


=================== parted -l:

Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      48.2MB  51.1GB  51.1GB  primary   ext4            boot
2      51.1GB  151GB   100GB   primary   ext4
3      151GB   161GB   10.1GB  primary   linux-swap(v1)
4      161GB   2170GB  2009GB  extended                  lba
5      161GB   2170GB  2009GB  logical   ext4


Model: ATA WDC WD2001FASS-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2000GB  2000GB  primary  ext4         boot


Model: ATA ST3250823AS (scsi)
Disk /dev/sdc: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ntfs


Model: ATA ST3250823AS (scsi)
Disk /dev/sdd: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
1      32.3kB  145GB  145GB  primary   ntfs
2      145GB   250GB  105GB  extended
5      145GB   250GB  105GB  logical   ntfs         boot


Model: ST315003 41AS (scsi)
Disk /dev/sde: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  1500GB  1500GB  primary  ntfs         boot

=================== parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:4096:msdos:ATA ST3000DM001-9YN1;
1:48.2MB:51.1GB:51.1GB:ext4::boot;
2:51.1GB:151GB:100GB:ext4::;
3:151GB:161GB:10.1GB:linux-swap(v1)::;
4:161GB:2170GB:2009GB:::lba;
5:161GB:2170GB:2009GB:ext4::;

BYT;
/dev/sdb:2000GB:scsi:512:512:msdos:ATA WDC WD2001FASS-0;
1:1049kB:2000GB:2000GB:ext4::boot;

BYT;
/dev/sdc:250GB:scsi:512:512:msdos:ATA ST3250823AS;
1:32.3kB:250GB:250GB:ntfs::;

BYT;
/dev/sdd:250GB:scsi:512:512:msdos:ATA ST3250823AS;
1:32.3kB:145GB:145GB:ntfs::;
2:145GB:250GB:105GB:::;
5:145GB:250GB:105GB:ntfs::boot;

BYT;
/dev/sde:1500GB:scsi:512:512:msdos:ST315003 41AS;
1:32.3kB:1500GB:1500GB:ntfs::boot;


=================== mount:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /mnt/boot-sav/sdd1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd5 on /mnt/boot-sav/sdd5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /mnt/boot-sav/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 sdd2 sdd5 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dmmidi1 dvd dvdrw ecryptfs fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg log mapper mcelog mem midi1 net network_latency network_throughput null nvidia0 nvidiactl oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdc sdc1 sdd sdd1 sdd2 sdd5 sde sde1 sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 vga_arbiter zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  41 45 1c 1d 00 00 00 00  |........AE......|
00000030  00 00 0c 00 00 00 00 00  54 c4 d1 01 00 00 00 00  |........T.......|
00000040  f6 00 00 00 01 00 00 00  00 16 a6 20 4c a6 20 b4  |........... L. .|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdd1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  b8 67 e2 10 00 00 00 00  |.........g......|
00000030  00 00 0c 00 00 00 00 00  54 c4 d1 01 00 00 00 00  |........T.......|
00000040  f6 00 00 00 01 00 00 00  08 10 d3 b4 48 d3 b4 70  |............H..p|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdd5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff e7 39 0c 00 00 00 00  |..........9.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4a 1a cc 2c 53 cc 2c 6c  |........J..,S.,l|
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

=================== hexdump -n512 -C /dev/sde1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  01 67 a8 ae 00 00 00 00  |.........g......|
00000030  04 00 00 00 00 00 00 00  70 86 ea 0a 00 00 00 00  |........p.......|
00000040  f6 00 00 00 01 00 00 00  65 d5 71 69 32 1d a9 2a  |........e.qi2..*|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       47G  3.8G   41G   9% /
udev           devtmpfs  2.5G   12K  2.5G   1% /dev
tmpfs          tmpfs     504M  928K  503M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.5G  3.0M  2.5G   1% /run/shm
/dev/sda2      ext4       92G   69G   19G  79% /home
/dev/sda5      ext4      1.8T  196M  1.8T   1% /mnt/boot-sav/sda5
/dev/sdb1      ext4      1.8T  427G  1.3T  25% /mnt/boot-sav/sdb1
/dev/sdc1      fuseblk   233G   89G  145G  39% /mnt/boot-sav/sdc1
/dev/sdd1      fuseblk   136G  1.9G  134G   2% /mnt/boot-sav/sdd1
/dev/sdd5      fuseblk    98G   25G   74G  25% /mnt/boot-sav/sdd5
/dev/sde1      fuseblk   1.4T   89G  1.3T   7% /mnt/boot-sav/sde1

=================== fdisk -l:

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x93376be2

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       94208    99899391    49902592   83  Linux
/dev/sda2        99899392   295194623    97647616   83  Linux
/dev/sda3       295211008   315006959     9897976   82  Linux swap / Solaris
/dev/sda4       315006974  4237991935  1961492481    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/sda5       315006976  4237991935  1961492480   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a108

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3907024895  1953511424   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c5d0935

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x127589c5

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   283273215   141636576+   7  HPFS/NTFS/exFAT
/dev/sdd2       283273216   488396799   102561792    5  Extended
/dev/sdd5   *   283275264   488396799   102560768    7  HPFS/NTFS/exFAT

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c482

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63  2930272064  1465136001    7  HPFS/NTFS/exFAT



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBRs of all disks (except USB without OS).
The boot flag will be placed on sde1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sdd5
/mnt/boot-sav/sdd5/ may need repair.

Reinstall the GRUB of sda1 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: nvidia
Kernel modules: nvidia_304, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
*******

grub-install (GRUB) 1.99-21ubuntu3.14,grub-install (GRUB) 1.

Reinstall the GRUB of sda1 into the MBR of sdb
grub-install /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: nvidia
Kernel modules: nvidia_304, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
*******

grub-install (GRUB) 1.99-21ubuntu3.14,grub-install (GRUB) 1.

Reinstall the GRUB of sda1 into the MBR of sdc
grub-install /dev/sdc: Installation finished. No error reported.
exit code of grub-install /dev/sdc:0

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: nvidia
Kernel modules: nvidia_304, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
*******

grub-install (GRUB) 1.99-21ubuntu3.14,grub-install (GRUB) 1.

Reinstall the GRUB of sda1 into the MBR of sdd
grub-install /dev/sdd: Installation finished. No error reported.
exit code of grub-install /dev/sdd:0

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: nvidia
Kernel modules: nvidia_304, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
*******

grub-install (GRUB) 1.99-21ubuntu3.14,grub-install (GRUB) 1.

Reinstall the GRUB of sda1 into the MBR of sde
grub-install /dev/sde: Installation finished. No error reported.
exit code of grub-install /dev/sde:0

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: nvidia
Kernel modules: nvidia_304, nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GF116 High Definition Audio Controller [10de:0bee] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:1557]
Kernel driver in use: snd_hda_intel
Kernel modules: snd-hda-intel
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
*******

grub-install (GRUB) 1.99-21ubuntu3.14,grub-install (GRUB) 1.

Reinstall the GRUB of sda1 into the MBR of sda
grub-install /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (3001GB) disk!
```

---

### Post by shadytv on 2014-04-20
Have you tried running "sudo update-grub" in Ubuntu? this reloads the list of what grub sees.

---

### Post by sdowney717 on 2014-04-20
```
sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

```

So that is your windows 8 partition with the os

I notice this though
```
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sdd5
/mnt/boot-sav/sdd5/ may need repair.
```

may need repair. 

If running sudo update-grub does not find the win8 OS properly.
I think I would restore windows booting using the windows install disc
Boot that drop to command prompt and run fixboot and fixmbr.
[http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/](http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/)

Verify the win8 boots ok

Then run the boot-repair disc again.
The repair disc for grub I use is this
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Write the iso to a thumb drive using unetbootin.

---

### Post by killabee44 on 2014-04-20
> **shadytv said:**
> Have you tried running "sudo update-grub" in Ubuntu? this reloads the list of what grub sees.

Yes, I have tried that to no avail.

Here is the output of "sudo update-grub":

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-60-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-60-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
```



> **sdowney717 said:**
> ```
sdd5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sdd5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

```

So that is your windows 8 partition with the os

I notice this though
```
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sdd5
/mnt/boot-sav/sdd5/ may need repair.
```

may need repair. 

If running sudo update-grub does not find the win8 OS properly.
I think I would restore windows booting using the windows install disc
Boot that drop to command prompt and run fixboot and fixmbr.
[http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/](http://www.tweakhound.com/2012/11/13/how-to-fix-the-windows-bootloader/)

Verify the win8 boots ok

Then run the boot-repair disc again.
The repair disc for grub I use is this
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Write the iso to a thumb drive using unetbootin.

I am sure that windows boots ok. I was booting from windows right before I installed Ubuntu. After browsing the windows partition, I did notice that boot.ini is not in the root of the Windows partition. Could that be the cause? 

Boot-repair was the utility I used to try and fix this issue.

---

### Post by oldfred on 2014-04-20
While you may have been booting Windows ok, it was not booting from sdd5. Windows only boots from a primary partition with the boot flag.
And it boots from the drive that is set as boot in BIOS. You which ever drive was the boot drive in BIOS probably had a 100MB boot partition with bootmgr & BCD files.
You do have a copy of bootmgr in your install, but also have to have BCD. And you need a primary NTFS partition with the boot flag to have Windows correctly repair it.
Create a new boot partition sdd2 or change sdd1 to the boot partition (add boot flag or set active in Windows repair) and use your Windows repair CD or flash drive to reinstall bootmgr & create a new BCD. Make sure sdd is set as boot drive in BIOS before making repairs, so Windows will also add its boot loader to the MBR of sdd.

With multiple drives you do not want to use Boot-Repairs auto fix. That reinstalls grub to every drive's MBR. With different installs on different drives you want each install to have its boot loader in the MBR of that install's drive.
But set BIOS to boot grub as it will offer to boot the other installs.

You have also modified your 3TB drive to only be 2TB. It should be partitioned with gpt not MBR.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by killabee44 on 2014-04-20
> **oldfred said:**
> While you may have been booting Windows ok, it was not booting from sdd5. Windows only boots from a primary partition with the boot flag.
And it boots from the drive that is set as boot in BIOS. You which ever drive was the boot drive in BIOS probably had a 100MB boot partition with bootmgr & BCD files.
You do have a copy of bootmgr in your install, but also have to have BCD. And you need a primary NTFS partition with the boot flag to have Windows correctly repair it.
Create a new boot partition sdd2 or change sdd1 to the boot partition (add boot flag or set active in Windows repair) and use your Windows repair CD or flash drive to reinstall bootmgr & create a new BCD. Make sure sdd is set as boot drive in BIOS before making repairs, so Windows will also add its boot loader to the MBR of sdd.

With multiple drives you do not want to use Boot-Repairs auto fix. That reinstalls grub to every drive's MBR. With different installs on different drives you want each install to have its boot loader in the MBR of that install's drive.
But set BIOS to boot grub as it will offer to boot the other installs.

You have also modified your 3TB drive to only be 2TB. It should be partitioned with gpt not MBR.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Oldfred,

Thanks a lot. Thre's a lot I didnt remember about Windows installs since Ive been using Ubuntu for so long. I didn't have the drive with the windows partition set as the primary hard drive in the bios. So I was catching hell while trying to repair the missing boot.ini in my windows partition. 
I ended up re-installing windows as sdd1 but it took me a while because windows wouldnt let me install, as it wasn't the primary hard drive in the bios. As soon as I did that I was able to install without problems. Wish I had seen your message first!e 

I hadnt noticed that my 3tb drive was MBR instead of GPT. Can I change that without losing my data? I expect to have to backup and restore, but just thought I'd ask...

Thanks for telling me about the fact that boot-repair installs grub on every drive. Now I know that I must use Rescatux and super grub disk instead..

Edit: 

If I back up my systm with clonezilla, then format the disk, convert the file sytem to GPT, then restore the image with clonezilla... do you think I will I have any problems?

Also, to be clear, I need to create two partitions. 
     The first, a EFI System Partition (ESP) formatted as fat32; 200MB; Mount point: /boot/efi; needs "boot" flag. 
     The second, a 2mb,"bios_grub" partition with no format. 

Great info.. Thanks again!

---

### Post by oldfred on 2014-04-20
You may be able to convert, but I like to have an efi partition near the beginning of every gpt drive. Then if I want to install a UEFI bootable system in the future I can without totally backing up and redoing it just to get a 300MB partition near front of drive.
Best to still have good backups.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

   Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by killabee44 on 2014-04-21
I see you replied right before I re edited my last reply.. Can you check and see if what I wrote about the partition creation is correct? Thanks.

---

### Post by oldfred on 2014-04-21
I do not think you can use Clonezilla for a backup. It is an image so would be the MBR partition(s).
I use rsync just to copy the files which would be ok.

You cannot copy gpt partitions with low level tools like dd, you can copy an entire gpt drive. There is internal gpt data in partitions and both primary partition table & backup partition table that must be kept in sync.

---

### Post by killabee44 on 2014-04-21
Does the partition structure that I posted above look Ok? 

I think the most simple way to do this will be to:
Format the drive, partition it, copy over the files from the backup of my home partition on to the new home, and do a fresh install of 14.04.
I've been wanting to upgrade anyhow.. 

Also, I'll use rsync like you recommend..

---

### Post by oldfred on 2014-04-21
My current system is BIOS only so I have a bios_grub partition to boot. But all new drives or drives I reformat are now gpt and I leave 300MB for an efi partition or create the FAT32 partition immediately. It is recommended that the efi partition be first, but Windows makes it second or third, but still near beginning of drive.

How you decide to partition is very personal as it depends on how you use system. If recording lots of video you may want a very large partition. If like me, installing various versions for testing you may want a lot of 26GB / (root) partitions and a larger data partition.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by killabee44 on 2014-04-27
Oldfred,

Ok, I copied my home folder over to a backup drive by using rsync, partitioned as you sugested, installed 14.04, but now I am having a new issue. 

I am now getting a login loop at the ubuntu login prompt that is not letting me log in with my root username. I can log in just fine as a guest, but when I try to log in as the main admin account, I get a black screen, and am then taken back to the login scren. 

I did a search for "login loop" and tried some of those fixes, but none have worked so far. 

My question is, could this be because I somehow did not copy the home directory over correctly with rsync?

Edit: When I copied the files back to my home folder using rsync, I used the option to keep permissions. Was that correct? 

When I go to terminal and log in there, I see this:

```
-bash: /home/robert/.profile: Permission denied
```

---

### Post by oldfred on 2014-04-27
I know that with Linux you need to keep permissions, but did you change user name?

I have all this in my notes on resetting things. Not sure if still current.

 Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/$USER/.dmrc
sudo chown $USER:$USER /home/$USER

   Broken sudo
Check permissions - should be
 ls /etc/sudoers -l
-r--r----- 1 root root 723 Jan 31  2012 /etc/sudoers
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
 sudo service lightdm stop
sudo chown username:username ~/.Xauthority
sudo service lightdm start  


 chmod -R a+rwX,o-w /home/$USER
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

   .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.
sudo chown $USER:$USER /home/username/.ICEauthority

   fred@fred-Precise:~$ getent passwd $USER
fred:x:1000:1000:fred,,,:/home/fred:/bin/bash
fred@fred-Precise:~$ ls -n /home/$USER
All should be 1000

---

### Post by newbie2244 on 2014-04-30
Killabee - 

What do you actually see in GRUB? Is it a long list?

---

### Post by killabee44 on 2014-05-01
Oldfred, 

I ended up doing a fresh install. That allowed things to work fine again. Then I copied my home folder files over. The problem was something that I was bringing over. It caused me to not be able to log in. This all was with the same username and password on the backed up home folder as the new install. 

I appreciate all your help though. You really did help me a lot with this. 


Newbie2244, 

My grub got messed up, but I got that sorted early on. Thanks.

---

