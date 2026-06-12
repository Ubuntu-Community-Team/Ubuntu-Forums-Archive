---
title: "grub loads in my desktop(64-bi) but does not in my netbook(32-bit)"
date: 2014-07-10
forum: General Help
---

### Post by K.Draziotis on 2014-07-10
[SIZE=2][FONT=arial][COLOR=#333333]I have one desktop(64-bit) and one old netbook (32-bit advent) . Both of them have windows 7 in their internal hds (only). I have a usb hard disk which has ubuntu (64-bit) installed and boots without problems from the desktop pc. Recently I installed also ubuntu 32-bit (in the usb hd) in order to use them with my netbook. 
Now again I get the menu grub in my dekstop pc and I can load both version of ubuntu (32 and 64) but in my netbook, I get the error:[/COLOR]
unknown filesystem
grub rescue>_
[COLOR=#333333]When I give **>ls** I get only (hd0,msdos1),(hd0,msdos2),etc...(which are the partitions in my usb hd). I.e. I assume bios can not see the internal hdd of the netbook. 
Any ideas to boot from my netbook? Also I provide some information which I got from ubuntu live cd (Try it choice) from my netbook.[/COLOR]
              ```
Boot Info Script 0.61      [1 April 2012]
[COLOR=#333333]============================= Boot Info Summary: ===============================[/COLOR]
[COLOR=#333333]=> Windows is installed in the MBR of /dev/sda. => 
Grub2 (v1.99) is installed in the MBR of /dev/sdb 
and looks at sector 1 of the same hard drive for core.img. core.img
 is at this location and looks in partition 112 for .[/COLOR]
[COLOR=#333333]sda1: **______________________________________________________________________**[/COLOR]
File system:       vfat
Boot sector type:  Windows 7: FAT32
Boot sector info:  No errors found in the Boot Parameter Block.
Operating System:  Windows Vista
Boot files:        /Windows/System32/winload.exe
[COLOR=#333333]sda2: **______________________________________________________________________**[/COLOR]
File system:       ntfs
Boot sector type:  Windows Vista/7: NTFS
Boot sector info:  No errors found in the Boot Parameter Block.
Operating System:  Windows 7
Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
[COLOR=#333333]sdb1: **______________________________________________________________________**[/COLOR]
File system:       ext4
Boot sector type:  -
Boot sector info: 
Operating System:  
Boot files:        /grub/grub.cfg
[COLOR=#333333]sdb2: **______________________________________________________________________**[/COLOR]
File system:       Extended Partition
Boot sector type:  Unknown
Boot sector info: 
[COLOR=#333333]sdb5: **______________________________________________________________________**[/COLOR]
File system:       ext4
Boot sector type:  -
Boot sector info: 
Operating System:  Ubuntu 14.04 LTS
Boot files:        /etc/fstab
[COLOR=#333333]sdb6: **______________________________________________________________________**[/COLOR]
File system:       ext4
Boot sector type:  -
Boot sector info: 
Operating System:  
Boot files:        
[COLOR=#333333]sdb7: **______________________________________________________________________**[/COLOR]
File system:       swap
Boot sector type:  -
Boot sector info: 
[COLOR=#333333]sdb3: **______________________________________________________________________**[/COLOR]
File system:       ntfs
Boot sector type:  Windows Vista/7: NTFS
Boot sector info:  No errors found in the Boot Parameter Block.
Operating System:  
Boot files:        
[COLOR=#333333]sdb4: **______________________________________________________________________**[/COLOR]
File system:       ext4
Boot sector type:  -
Boot sector info: 
Operating System:  Ubuntu 14.04 LTS
Boot files:        /boot/grub/grub.cfg /etc/fstab
[COLOR=#333333]============================ Drive/Partition Info: =============================[/COLOR]
[COLOR=#333333]Drive: sda **_________________________________________________________________**[/COLOR]
[COLOR=#333333]Disk /dev/sda: 120.0 GB, 120034123776 bytes 255 heads, 63 sectors/track, 14593 cylinders,
 total 234441648 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#333333]Partition Boot Start Sector End Sector # of Sectors Id System[/COLOR]
[COLOR=#333333]/dev/sda1 2,048 6,146,047 6,144,000 12 Compaq diagnostics /dev/sda2 * 6,146,048 234,438,655 228,292,608 7 NTFS / exFAT / HPFS[/COLOR]
[COLOR=#333333]Drive: sdb **_________________________________________________________________**[/COLOR]
[COLOR=#333333]Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes 255 heads, 63 sectors/track, 121597 cylinders,
 total 1953458176 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#333333]Partition Boot Start Sector End Sector # of Sectors Id System[/COLOR]
[COLOR=#333333]/dev/sdb1 2,048 976,895 974,848 83 Linux 
/dev/sdb2 978,942 272,461,823 271,482,882 5 Extended 
/dev/sdb5 978,944 71,233,535 70,254,592 83 Linux
 /dev/sdb6 71,235,584 264,648,703 193,413,120 83 Linux
 /dev/sdb7 264,650,752 272,461,823 7,811,072 82 Linux swap / Solaris 
/dev/sdb3 * 272,461,824 886,861,823 614,400,000 7 NTFS / exFAT / HPFS

 /dev/sdb4 886,861,824 1,082,174,323 195,312,500 83 Linux
[/COLOR]
[COLOR=#333333]"blkid" output: **____________________________________________________________**[/COLOR]
[COLOR=#333333]Device UUID TYPE LABEL[/COLOR]
[COLOR=#333333]/dev/loop0 squashfs
/dev/sda1 0475-3980 vfat RECOVERY /dev/sda2 C2CC2F46CC2F33D7 ntfs

/dev/sdb1 79b97cb3-a4cc-48a6-afae-f0b5f052eec4 ext4

/dev/sdb3 F25855325854F737 ntfs External-Ntfs /dev/sdb4 13f706a5-bc41-4060-97c3-d83480b2bf32 ext4

/dev/sdb5 d58b8f4c-a995-433b-a117-7dc0e0335ee5 ext4

/dev/sdb6 faf6195b-ba23-4423-9e04-4a027e4da6a8 ext4

/dev/sdb7 f56eab16-08b1-4f42-b849-5844784cc067 swap

/dev/sr0 iso9660 Ubuntu 14.04 LTS i386[/COLOR]
[COLOR=#333333]================================ Mount points: =================================[/COLOR]
[COLOR=#333333]Device Mount_Point Type Options[/COLOR]
[COLOR=#333333]/dev/loop0 /rofs squashfs (ro,noatime)

/dev/sdb1 /media/ubuntu/79b97cb3-a4cc-48a6-afae-f0b5f052eec4 ext4 (rw,nosuid,nodev,uhelper=udisks2) 

/dev/sdb3 /media/ubuntu/External-Ntfs fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) 

/dev/sdb4 /media/ubuntu/13f706a5-bc41-4060-97c3-d83480b2bf32 ext4 (rw,nosuid,nodev,uhelper=udisks2)

/dev/sdb5 /media/ubuntu/d58b8f4c-a995-433b-a117-7dc0e0335ee5 ext4 (rw,nosuid,nodev,uhelper=udisks2) 

/dev/sdb6 /media/ubuntu/faf6195b-ba23-4423-9e04-4a027e4da6a8 ext4 (rw,nosuid,nodev,uhelper=udisks2) 

/dev/sr0 /cdrom iso9660 (ro,noatime)[/COLOR]
[COLOR=#333333]============================= sdb1/grub/grub.cfg: ==============================[/COLOR]

```[/FONT]```
[SIZE=1]DO NOT EDIT THIS FILE[/SIZE]

[COLOR=#333333]#[/COLOR]
[SIZE=1]It is automatically generated by grub-mkconfig using templates

from /etc/grub.d and settings from /etc/default/grub

[COLOR=#333333]#[/COLOR]
BEGIN /etc/grub.d/05_debian_theme
[/SIZE]
[COLOR=#333333]set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30;
 then clear fi[/COLOR]
END /etc/grub.d/05_debian_theme

BEGIN /etc/grub.d/10_linux_proxy

[COLOR=#333333]function gfxmode { set gfxpayload="${1}" if [ "${1}" = "keep" ]; 
then set vt_handoff=vt.handoff=7 else set vt_handoff= fi } 
if [ "${recordfail}" != 1 ]; then if [ -e ${prefix}/gfxblacklist.txt ];
 then if hwmatch ${prefix}/gfxblacklist.txt 3; then if [ ${match} = 0 ]; 
then set linux_gfx_mode=keep else set linux_gfx_mode=text fi
 else set linux_gfx_mode=text fi else set linux_gfx_mode=keep fi else set linux_gfx_mode=text fi
 export linux_gfx_mode[/COLOR]
END /etc/grub.d/10_linux_proxy

BEGIN /etc/grub.d/11_Windows_proxy

END /etc/grub.d/11_Windows_proxy

BEGIN /etc/grub.d/40_custom_proxy

[COLOR=#333333]menuentry "Windows 7"
{ insmod ntfs set root='hd0,2' search --no-floppy --fs-uuid --set 511C-46C3 drivemap -s (hd0) ${root} 
chainloader +1 } 

menuentry "Ubuntu 64-bit"
 --class ubuntu --class gnu-linux --class gnu
 --class os $menuentry_id_option 'gnulinux-simple-d58b8f4c-a995-433b-a117-7dc0e0335ee5' 
{ insmod gzio insmod part_msdos insmod ext2 set root='hd1,msdos1' 
if [ x$feature_platform_search_hint = xy ]; then search --no-floppy --fs-uuid --set=root
 --hint-bios=hd1,msdos1
 --hint-efi=hd1,msdos1 
--hint-baremetal=ahci1,msdos1 79b97cb3-a4cc-48a6-afae-f0b5f052eec4
 else search --no-floppy --fs-uuid --set=root 79b97cb3-a4cc-48a6-afae-f0b5f052eec4 fi 
linux /vmlinuz-3.13.0-24-generic root=UUID=d58b8f4c-a995-433b-a117-7dc0e0335ee5
 ro quiet splash $vt_handoff initrd /initrd.img-3.13.0-24-generic } 

menuentry "ubuntu 32-bit"
{ GRUB_GFXMODE=640x480 insmod gzio insmod part_msdos insmod ext2 set root='hd1,msdos4'
 if [ x$feature_platform_search_hint = xy ]; then search --no-floppy --fs-uuid --set=root 
--hint-bios=hd1,msdos4 
--hint-efi=hd1,msdos4 --hint-baremetal=ahci1,msdos4 13f706a5-bc41-4060-97c3-d83480b2bf32
 else search --no-floppy
 --fs-uuid --set=root 13f706a5-bc41-4060-97c3-d83480b2bf32 fi linux /boot/vmlinuz-3.13.0-24-generic 
root=UUID=13f706a5-bc41-4060-97c3-d83480b2bf32 
ro quiet splash $vt_handoff initrd /boot/initrd.img-3.13.0-24-generic }[/COLOR]
END /etc/grub.d/40_custom_proxy

BEGIN /etc/grub.d/42_linux_xen

END /etc/grub.d/42_linux_xen

BEGIN /etc/grub.d/43_memtest86+_proxy

END /etc/grub.d/43_memtest86+_proxy

BEGIN /etc/grub.d/44_os-prober

[COLOR=#333333]menuentry 'Windows 7 (loader) (on /dev/sda1)'
 --class windows --class os $menuentry_id_option 'osprober-chain-1EF3-52B5' 
{ insmod part_msdos insmod fat set root='hd0,msdos1' if [ x$feature_platform_search_hint = xy ]; 
then search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
 --hint-baremetal=ahci0,msdos1 1EF3-52B5 else search --no-floppy --fs-uuid
 --set=root 1EF3-52B5 fi parttool ${root} hidden- chainloader +1 }

 menuentry 'Windows 7 (loader) (on /dev/sda2)' 
--class windows --class os $menuentry_id_option 'osprober-chain-511C-46C3' 
{ insmod part_msdos insmod fat set root='hd0,msdos2' if [ x$feature_platform_search_hint = xy ];
 then search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2
 --hint-baremetal=ahci0,msdos2 511C-46C3 else search --no-floppy --fs-uuid
 --set=root 511C-46C3 fi parttool ${root} hidden- chainloader +1 } 

[/COLOR][COLOR=#333333]
menuentry 'Ubuntu 14.04 LTS (14.04) (on /dev/sdb4)'
 --class gnu-linux --class gnu 
--class os $menuentry_id_option 'osprober-gnulinux-simple-13f706a5-bc41-4060-97c3-d83480b2bf32'
 {
 insmod part_msdos insmod ext2 
set root='hd1,msdos4'
 if [ x$feature_platform_search_hint = xy ]; 
then search --no-floppy --fs-uuid --set=root 
--hint-bios=hd1,msdos4 --hint-efi=hd1,msdos4
--hint-baremetal=ahci1,msdos4 13f706a5-bc41-4060-97c3-d83480b2bf32 
else search 
--no-floppy --fs-uuid --set=root 13f706a5-bc41-4060-97c3-d83480b2bf32 
fi
linux /boot/vmlinuz-3.13.0-24-generic root=UUID=13f706a5-bc41-4060-97c3-d83480b2bf32
ro quiet splash $vt_handoff initrd /boot/initrd.img-3.13.0-24-generic
 } 

submenu 'Advanced options for Ubuntu 14.04 LTS (14.04) (on /dev/sdb4)' 
$menuentry_id_option 'osprober-gnulinux-advanced-13f706a5-bc41-4060-97c3-d83480b2bf32' 
{ menuentry 'Ubuntu 32-bit (on /dev/sdb4)' 
--class gnu-linux --class gnu 
--class os $menuentry_id_option 
'osprober-gnulinux-/boot/vmlinuz-3.13.0-24-generic--13f706a5-bc41-4060-97c3-d83480b2bf32'
 { insmod part_msdos insmod ext2 set root='hd1,msdos4'
 if [ x$feature_platform_search_hint = xy ]; then search --no-floppy 
--fs-uuid --set=root --hint-bios=hd1,msdos4 --hint-efi=hd1,msdos4
--hint-baremetal=ahci1,msdos4 13f706a5-bc41-4060-97c3-d83480b2bf32
else search 
--no-floppy --fs-uuid
 --set=root 13f706a5-bc41-4060-97c3-d83480b2bf32 
 fi 
linux /boot/vmlinuz-3.13.0-24-generic 
root=UUID=13f706a5-bc41-4060-97c3-d83480b2bf32 
ro quiet splash $vt_handoff initrd /boot/initrd.img-3.13.0-24-generic } }[/COLOR]
[COLOR=#333333]set timeout_style=menu if [ "${timeout}" = 0 ]; then set timeout=10 fi[/COLOR]
END /etc/grub.d/44_os-prober

BEGIN /etc/grub.d/45_uefi-firmware

END /etc/grub.d/45_uefi-firmware

BEGIN /etc/grub.d/46_custom_proxy

This file provides an easy way to add custom menu entries. Simply type the

menu entries you want to add after this comment. Be careful not to change

the 'exec tail' line above.

END /etc/grub.d/46_custom_proxy

BEGIN /etc/grub.d/47_custom

[COLOR=#333333]if [ -f ${config_directory}/custom.cfg ]; 
then source ${config_directory}/custom.cfg elif [ -z "${config_directory}" -a -f $prefix/custom.cfg ];
 then source $prefix/custom.cfg; fi[/COLOR]
END /etc/grub.d/47_custom

[COLOR=#333333]=================== sdb1: Location of files loaded by Grub: ====================[/COLOR]
       GiB - GB             File                                 Fragment(s)
[COLOR=#333333]=============================== sdb5/etc/fstab: ================================[/COLOR]

```[/SIZE]```
[HR][/HR][SIZE=2]/etc/fstab: static file system information.

[COLOR=#333333]#[/COLOR]
Use 'blkid' to print the universally unique identifier for a

device; this may be used with UUID= as a more robust way to name devices

that works even if disks are added and removed. See fstab(5).

[COLOR=#333333]#[/COLOR]
/ was on /dev/sdb5 during installation

[COLOR=#333333]UUID=d58b8f4c-a995-433b-a117-7dc0e0335ee5 / ext4 errors=remount-ro 0 1[/COLOR]
/boot was on /dev/sdb1 during installation

[COLOR=#333333]UUID=79b97cb3-a4cc-48a6-afae-f0b5f052eec4 /boot ext4 defaults 0 2[/COLOR]
/home was on /dev/sdb6 during installation

[COLOR=#333333]UUID=faf6195b-ba23-4423-9e04-4a027e4da6a8 /home ext4 defaults 0 2[/COLOR]
swap was on /dev/sdb7 during installation

UUID=f56eab16-08b1-4f42-b849-5844784cc067 none swap sw 0 0

[COLOR=#333333]=========================== sdb4/boot/grub/grub.cfg: ===========================[/COLOR]

[/SIZE][HR][/HR][SIZE=2][COLOR=#333333]#[/COLOR]
DO NOT EDIT THIS FILE

[COLOR=#333333]#[/COLOR]
It is automatically generated by grub-mkconfig using templates

from /etc/grub.d and settings from /etc/default/grub

[COLOR=#333333]#[/COLOR]
BEGIN /etc/grub.d/00_header

[COLOR=#333333]if [ -s $prefix/grubenv ]; 
then set have_grubenv=true load_env fi if [ "${next_entry}" ] ; 
then set default="${next_entry}"
 set next_entry= save_env next_entry 
set boot_once=true else set default="0"
 fi[/COLOR]
[COLOR=#333333]if [ x"${feature_menuentry_id}" = xy ]; 
then menuentry_id_option="--id" else menuentry_id_option=""
 fi[/COLOR]
[COLOR=#333333]export menuentry_id_option[/COLOR]
[COLOR=#333333]if [ "${prev_saved_entry}" ]; then set saved_entry="${prev_saved_entry}"
 save_env saved_entry set prev_saved_entry= save_env prev_saved_entry 
set boot_once=true 
 fi[/COLOR]
[COLOR=#333333]function savedefault { if [ -z "${boot_once}" ]; 
then saved_entry="${chosen}" save_env saved_entry fi } function recordfail { set recordfail=1
 if [ -n "${have_grubenv}" ]; 
then 
if [ -z "${boot_once}" ]; then save_env recordfail;
 fi; 
 fi }
 function load_video { if [ x$feature_all_video_module = xy ]; 
then insmod all_video 
else 
insmod efi_gop insmod efi_uga 
insmod ieee1275_fb insmod vbe 
insmod vga insmod video_bochs insmod video_cirrus 
 fi }[/COLOR]
[COLOR=#333333]terminal_input console terminal_output console if [ "${recordfail}" = 1 ] ; then set timeout=-1
 else if [ x$feature_timeout_style = xy ] ;
 then 
set timeout_style=menu set timeout=5 # Fallback normal timeout code in case the timeout_style feature is # unavailable. 
else set timeout=5
 fi 
 fi[/COLOR]
**END /etc/grub.d/00_header**

**BEGIN /etc/grub.d/05_debian_theme**

[COLOR=#333333]set menu_color_normal=white/black set menu_color_highlight=black/light-gray
 if background_color 44,0,30; then clear
 fi[/COLOR]
**END /etc/grub.d/05_debian_theme**

**BEGIN /etc/grub.d/20_linux_xen**

**END /etc/grub.d/20_linux_xen**

**BEGIN /etc/grub.d/21_memtest86+_proxy**

**END /etc/grub.d/21_memtest86+_proxy**

**BEGIN /etc/grub.d/30_os-prober_proxy**

[COLOR=#333333]set timeout_style=menu if [ "${timeout}" = 0 ]; then set timeout=10 fi[/COLOR]
**END /etc/grub.d/30_os-prober_proxy**

**BEGIN /etc/grub.d/31_uefi-firmware**

**END /etc/grub.d/31_uefi-firmware**

**BEGIN /etc/grub.d/40_custom_proxy**

**This file provides an easy way to add custom menu entries. Simply type the**

**menu entries you want to add after this comment. Be careful not to change**

**the 'exec tail' line above.**

[COLOR=#333333]menuentry "Windows 7(64-bit)"
{ insmod ntfs set root='hd0,2' search --no-floppy --fs-uuid 
--set 511C-46C3 drivemap -s (hd0) ${root} chainloader +1 } 

menuentry "Ubuntu 64-bit"{[/COLOR]
GRUB_GFXMODE=640x480
insmod gzio
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root
 --hint-bios=hd1,msdos1
 --hint-efi=hd1,msdos1
 --hint-baremetal=ahci1,msdos1  79b97cb3-a4cc-48a6-afae-f0b5f052eec4
else
  search --no-floppy --fs-uuid --set=root 79b97cb3-a4cc-48a6-afae-f0b5f052eec4
fi
linux   /vmlinuz-3.13.0-24-generic root=UUID=d58b8f4c-a995-433b-a117-7dc0e0335ee5
 ro  quiet splash $vt_handoff
initrd  /initrd.img-3.13.0-24-generic
[COLOR=#333333]}[/COLOR]
**END /etc/grub.d/40_custom_proxy**

**BEGIN /etc/grub.d/41_linux_proxy**

[COLOR=#333333]function gfxmode { set gfxpayload="${1}" if [ "${1}" = "keep" ]; 
then set vt_handoff=vt.handoff=7 
else set vt_handoff= fi } if [ "${recordfail}" != 1 ];
 then if [ -e ${prefix}/gfxblacklist.txt ]; 
then if hwmatch ${prefix}/gfxblacklist.txt 3; then if [ ${match} = 0 ]; 
then set linux_gfx_mode=keep else set linux_gfx_mode=text
 fi 
else set linux_gfx_mode=text 
fi
 else set linux_gfx_mode=keep fi else set linux_gfx_mode=text 
fi 
export linux_gfx_mode[/COLOR]
**END /etc/grub.d/41_linux_proxy**

**BEGIN /etc/grub.d/42_custom_proxy**

[COLOR=#333333]menuentry "Ubuntu 32-bit"
 --class ubuntu --class gnu-linux --class gnu
 --class os $menuentry_id_option 'gnulinux-simple-13f706a5-bc41-4060-97c3-d83480b2bf32'
 { GRUB_GFXMODE=640x480 insmod gzio insmod part_msdos insmod ext2 set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then search --no-floppy --fs-uuid --set=root
 --hint-bios=hd1,msdos4
 --hint-efi=hd1,msdos4 
--hint-baremetal=ahci1,msdos4 13f706a5-bc41-4060-97c3-d83480b2bf32 
else search 
--no-floppy --fs-uuid
 --set=root 
13f706a5-bc41-4060-97c3-d83480b2bf32 
fi 
linux /boot/vmlinuz-3.13.0-24-generic 
root=UUID=13f706a5-bc41-4060-97c3-d83480b2bf32
 ro quiet splash $vt_handoff initrd /boot/initrd.img-3.13.0-24-generic }[/COLOR]
**END /etc/grub.d/42_custom_proxy**

**BEGIN /etc/grub.d/43_custom**

[COLOR=#333333]if [ -f ${config_directory}/custom.cfg ]; 
then source ${config_directory}/custom.cfg 
elif [ -z "${config_directory}" -a -f $prefix/custom.cfg ]; then source $prefix/custom.cfg;
 fi[/COLOR]
### END /etc/grub.d/43_custom ###

[COLOR=#333333]=============================== sdb4/etc/fstab: ================================[/COLOR]

[/SIZE][HR][/HR][SIZE=2]/etc/fstab: static file system information.

[COLOR=#333333]#[/COLOR]
Use 'blkid' to print the universally unique identifier for a

device; this may be used with UUID= as a more robust way to name devices

that works even if disks are added and removed. See fstab(5).

[COLOR=#333333]#[/COLOR]
/ was on /dev/sdb4 during installation

[COLOR=#333333]UUID=13f706a5-bc41-4060-97c3-d83480b2bf32 / ext4 errors=remount-ro 0 1[/COLOR]
swap was on /dev/sdb7 during installation

UUID=f56eab16-08b1-4f42-b849-5844784cc067 none swap sw 0 0

[COLOR=#333333]=================== sdb4: Location of files loaded by Grub: ====================[/COLOR]
       GiB - GB             File                                 Fragment(s)
[COLOR=#333333]======================== Unknown MBRs/Boot Sectors/etc: ========================[/COLOR]
[COLOR=#333333]Unknown BootLoader on sdb2[/COLOR]
[COLOR=#333333]00000000 05 75 61 1e 60 f3 18 f2 6e d3 9f 7d 7f 75 f6 cb |.ua....n..}.u..|00000010  5f d5 1f 78 3c 7a 91 f9  6e f7 d9 ac 21 c6 a6 4b  |_..x<z..n...!..K|00000020  f4 53 18 37 f0 92 1f 06  e9 31 8c 77 99 25 99 c2  |.S.7.....1.w.%..|00000030  f4 0b 97 07 d2 13 69 b4  06 63 58 c9 4c 56 10 fa  |......i..cX.LV..|00000040  36 ad d7 a6 ad e5 d9 36  9c 3d 7a db 0c 5e e8 03  |6......6.=z..^..|00000050  b2 61 61 41 92 b2 e7 b7  d1 02 28 a6 b3 10 5c 97  |.aaA......(...\.|00000060  52 58 c4 58 26 90 88 1b  ee d2 9a 4d 52 90 52 21  |RX.X&......MR.R!|00000070  19 ca 90 1a 9a 0f d4 8e  3c 51 89 cd f6 dd b0 2b  |........<Q.....+|00000080  44 e8 ab 8a 95 cf e5 d5  31 73 da 66 9a 3b 8f 07  |D.......1s.f.;..|00000090  e5 de 11 be 76 6a 61 f2  da b9 e4 1f 02 4d e3 a7  |....vja......M..|000000a0  49 51 c0 58 d5 02 fa 5e  ed 74 e8 fd cd 4e c7 ef  |IQ.X...^.t...N..|000000b0  e1 a3 73 18 d2 12 1f 87  21 7d e2 77 43 e9 39 37  |..s.....!}.wC.97|000000c0  fa aa 69 cb 87 38 3c 53  ce 73 5d e2 e7 5e 32 66  |..i..8<S.s]..^2f|000000d0  a7 ac 09 10 ad 08 48 47  13 ac 01 98 09 74 90 34  |......HG.....t.4|000000e0  6b 9e 68 c6 35 36 aa e5  7f 68 41 28 19 40 a5 ed  |k.h.56...hA(.@..|000000f0  0f 14 1a ec c8 58 dd 3d  66 7d ce 98 0e ab 70 8d  |.....X.=f}....p.|00000100  16 cc bf e9 e1 37 22 7c  36 9f 2e 19 84 a0 65 bd  |.....7"|6.....e.|00000110  34 1b ad ca 6a f5 64 65  36 e9 5a 14 98 6f a0 76  |4...j.de6.Z..o.v|00000120  e1 b3 d7 28 ae d4 4f 02  9a c5 53 74 11 93 35 ba  |...(..O...St..5.|00000130  88 f3 0c f1 d3 4c f3 5c  14 ab 2e 73 06 7b c3 f4  |.....L.\...s.{..|00000140  90 61 e6 e9 d4 92 7a 95  0c 50 d1 0a 60 70 52 3d  |.a....z..P..pR=| 00000150 64 81 d0 15 41 61 16 01 75 cc 34 88 b5 73 e9 ac |d...Aa..u.4..s..| 00000160 fd e8 d9 9c b7 cb 1a b8 d8 5d a8 24 8f 5a ff 64 |.........].$.Z.d| 00000170 a8 43 6b 92 65 ed 32 bc 73 77 73 ae fc 7e c8 54 |.Ck.e.2.sws..~.T| 00000180 c4 a8 57 8d 77 3e 65 d2 5b fd 70 dc 06 ef f7 db |..W.w>e.[.p.....| 00000190 ed 13 fd 6e ef 44 97 fc 38 df 04 a2 bd 18 d5 09 |...n.D..8.......| 000001a0 45 bb de a8 81 7a e4 6b f1 f0 1a 7a d7 30 33 8d |E....z.k...z.03.| 000001b0 c1 e4 d1 a6 2e 01 f3 5c 13 6e 2b c2 35 b2 00 ee |........n+.5...| 000001c0 33 3c 83 fe ff ff 02 00 00 00 00 00 30 04 00 fe |3<..........0...| 000001d0 ff ff 05 fe ff ff 02 00 30 04 00 48 87 0b 00 00 |........0..H....| 000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................| 000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.| 00000200[/COLOR]
[COLOR=#333333]========= Devices which don't seem to have a corresponding hard drive: =========[/COLOR]
[COLOR=#333333]sdc[/COLOR]
[COLOR=#333333]=============================== StdErr Messages: ===============================[/COLOR]
[COLOR=#333333]cat: /tmp/BootInfo-F2Q4oQmG/Tmp_Log: No such file or directory cat: /tmp/BootInfo-F2Q4oQmG/Tmp_Log: No such file or directory No volume groups found[/COLOR][/SIZE]
```

---

### Post by oldfred on 2014-07-11
I was hoping code tags might make it more readable, but too much formatting was lost. 
Better to just post link to BootInfo report in pastebin that Boot-Repair gives. 
If posting long text use code tags and standard fonts.

Some BIOS have issues with very large root partitions and booting from a USB device. Others just have issues.
But better to create / (root) of 25GB and use rest of hard drive as /home or data partition(s).
You can test that easily by shinking existing / partition using gparted from live installer.

---

