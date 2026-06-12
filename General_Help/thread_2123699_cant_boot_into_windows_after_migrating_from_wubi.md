---
title: "cant boot into windows after migrating from wubi"
date: 2013-03-08
forum: General Help
---

### Post by geekhush on 2013-03-08
Hi,
I recently migrated from a wubi install to a full install on my windows 8 machine. i referred to this article [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) and adopted the automatic migration. Everything went well until i booted. on booting i couldn't see the option to boot into windows in the grub menu. so how do i fix this so i can boot into windows too. Any help really appreciated.

Thanks in advance! 

hush

---

### Post by geekhush on 2013-03-08
Hi,
I recently migrated from a wubi install to a full install on my windows 8 machine. i referred to this article [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) and adopted the automatic migration. Everything went well until i booted. on booting i couldn't see the option to boot into windows in the grub menu. so how do i fix this so i can boot into windows too. Any help really appreciated.

Thanks in advance! 

hush

---

### Post by Cheesemill on 2013-03-08
Try running this command to add Windows to your grub menu...
```
sudo update-grub
```

---

### Post by geekhush on 2013-03-08
hi thanks for the reply, i tried the above and it didn't help. could you suggest me something else if possible please. :)

---

### Post by ajgreeny on 2013-03-08
Try the command ```
sudo update-grub
``` That should do it.

You can see at any time what your grub menu will include with the command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
```

---

### Post by lisati on 2013-03-08
Threads merged: starting multiple threads for the same question can dilute the community's ability to help.

---

### Post by bcbc on 2013-03-08
Please post the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Thanks

---

### Post by geekhush on 2013-03-09
Hi,
The > sudo update-grub command didn't solve the problem. and here is the result of  [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). 



```
Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Windows is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk


sda1/Wubi: _____________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda3: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1             206,848   123,783,167   123,576,320   7 NTFS / exFAT / HPFS
/dev/sda2         123,783,168   186,697,727    62,914,560  83 Linux
/dev/sda3         186,697,728   976,769,023   790,071,296   5 Extended
/dev/sda5         186,699,776   195,915,775     9,216,000  82 Linux swap / Solaris
/dev/sda6         195,917,824   615,348,223   419,430,400   7 NTFS / exFAT / HPFS
/dev/sda7         615,350,272   976,769,023   361,418,752   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *             64 1,953,520,063 1,953,520,000   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        5CF85A75F85A4E00                       ntfs       Windows
/dev/sda2        a016f810-6a4d-4b2a-8c48-c269cd4a9e5a   ext4       
/dev/sda5        c1d67cb1-e358-4073-9f60-fd4b66e07dd5   swap       
/dev/sda6        6C3A056C6E17A85E                       ntfs       
/dev/sda7        001E0E5376835C01                       ntfs       
/dev/sdb1        0DEE-211E                              vfat       NARUTO


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /media/geekhush/6C3A056C6E17A85E fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7        /media/geekhush/001E0E5376835C01 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/geekhush/NARUTO   vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)




=========================== sda2/boot/grub/grub.cfg: ===========================


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
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
else
  search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    else
      search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    fi
    linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-25-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
    menuentry 'Ubuntu, with Linux 3.5.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-advanced-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        else
          search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        fi
        echo    'Loading Linux 3.5.0-25-generic ...'
        linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-25-generic-recovery-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        else
          search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        fi
        echo    'Loading Linux 3.5.0-25-generic ...'
        linux    /boot/vmlinuz-3.5.0-25-generic root=UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        else
          search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-a016f810-6a4d-4b2a-8c48-c269cd4a9e5a' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        else
          search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    else
      search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    else
      search --no-floppy --fs-uuid --set=root a016f810-6a4d-4b2a-8c48-c269cd4a9e5a
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>




# root was on /dev/sda2 when migrated
UUID=a016f810-6a4d-4b2a-8c48-c269cd4a9e5a    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda5 when migrated
UUID=c1d67cb1-e358-4073-9f60-fd4b66e07dd5    none    swap    sw    0    0
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/grub.cfg                             3
               =                boot/initrd.img-3.5.0-17-generic               1
               =                boot/initrd.img-3.5.0-25-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-25-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda3


00000000  09 a4 d1 25 8d a8 2a 23  77 74 35 23 a6 1e 0e 91  |...%..*#wt5#....|
00000010  e1 40 3d ba 33 e6 38 5b  97 41 d2 bb 62 e0 40 59  |.@=.3.8[.A..b.@Y|
00000020  b2 ed cd 4c 6e 7e 3b 1f  1f 14 7c 3b 29 55 fd 5c  |...Ln~;...|;)U.\|
00000030  77 c5 05 df 41 17 31 d3  92 60 52 79 6d da 96 bf  |w...A.1..`Rym...|
00000040  39 dd 10 5e 57 da fd a9  e7 e0 31 1c bd 7b 08 6e  |9..^W.....1..{.n|
00000050  91 92 1b 17 5d 4f e8 fc  da 87 18 64 4f ff 27 55  |....]O.....dO.'U|
00000060  bf bc da 26 24 4e 18 ef  33 d9 37 f7 64 5b ac 08  |...&$N..3.7.d[..|
00000070  e3 83 63 7a 0b aa 16 ad  38 1e ca 78 60 be 45 b2  |..cz....8..x`.E.|
00000080  cd f1 4c 9b 0a 8f 8c 69  fa 8c ce 5f 04 be 7e c5  |..L....i..._..~.|
00000090  fc 99 68 0f 64 f7 fb 30  22 eb 62 65 35 9b 6f 16  |..h.d..0".be5.o.|
000000a0  3b b7 76 ad 24 c8 73 22  76 6b c7 89 73 b4 9f 81  |;.v.$.s"vk..s...|
000000b0  ca 5f 92 28 57 22 cb 5c  00 59 36 c6 e5 45 66 bc  |._.(W".\.Y6..Ef.|
000000c0  f6 08 1a 0c 96 8a 9d 85  68 e7 46 28 0a 2f 0a 62  |........h.F(./.b|
000000d0  58 6b 01 3e d8 bf ad 46  76 ac 28 68 3a 77 6b dd  |Xk.>...Fv.(h:wk.|
000000e0  ae 90 cb ad f7 8f 5b 56  96 25 5e d4 91 3b 96 fa  |......[V.%^..;..|
000000f0  79 ad f5 68 5e 46 6b cc  66 37 79 80 10 d2 28 55  |y..h^Fk.f7y...(U|
00000100  e9 24 1f ba b3 dc 8c 85  3a f1 bb 78 f1 3b 05 80  |.$......:..x.;..|
00000110  c5 a6 6c 64 3e 01 7f 49  8f c8 e7 66 53 d3 47 70  |..ld>..I...fS.Gp|
00000120  44 3e 4d c8 af 7f cf 60  be 03 4d 61 6c a5 41 a1  |D>M....`..Mal.A.|
00000130  f5 a2 4c b2 75 4a 9d ef  7f 24 f1 f7 1b bd bb e5  |..L.uJ...$......|
00000140  fa 8c c9 dd d5 1c 6c 47  c7 a4 45 2a 3f 67 95 d3  |......lG..E*?g..|
00000150  f6 d6 57 5e 8e b1 58 e5  36 e3 88 2a 9d 4d 27 8f  |..W^..X.6..*.M'.|
00000160  ff 1d e8 09 98 73 5b f0  58 df 8b 68 50 95 94 22  |.....s[.X..hP.."|
00000170  9b 57 43 49 38 35 e3 27  72 eb 86 fa eb 08 95 4c  |.WCI85.'r......L|
00000180  06 af 97 f3 6d a5 a1 8a  03 4c 6f 33 5a bf a7 21  |....m....Lo3Z..!|
00000190  b4 7a 79 88 14 d2 d4 39  5e 62 fb 86 96 c9 43 a4  |.zy....9^b....C.|
000001a0  55 1e 88 c9 65 da fb 3a  d6 1b 5a 30 4e 6a f9 b5  |U...e..:..Z0Nj..|
000001b0  26 44 8a 03 6b a7 e6 ac  c4 86 b2 62 f9 bd 00 fe  |&D..k......b....|
000001c0  ff ff 82 fe ff ff 00 08  00 00 00 a0 8c 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 00 a8  8c 00 00 08 00 19 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in



```

Thanks.

hush

---

### Post by oldfred on 2013-03-09
You are missing the Windows boot partition. It looks like your main install is still in sda1, but Windows 7/8 normally installs in two partitions. One is a 100MB (hidden in Windows) that has two boot files & the repair console and you do not show that partition.

       Windows Boot files:
Vista/7/8 (with 7/8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Did you have another install of Windows and delete it? It had your boot files.

You need to put the boot flag on sda1 (it was on the partition with the boot files before) and use a Windows repairCD or flash drive to restore the Windows boot files. They can be in the same partition as your main Windows and do not have to be the separate boot partition.

      If you have access to or a friend with Windows 8 make a repair flash drive.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by bcbc on 2013-03-09
Yes two things are apparent. There is no boot flag (windows requires this on the boot partition) and the "bootmgr" file and the "Boot" directory are missing. Is it possible that you 'reused' the boot partition or removed it when you created the ext4 partition? Note that if you had Windows 7 before and added Windows 8 then Windows 8 would have put it's boot files on the existing Windows 7 install. And if you thought you could wipe out Windows 7 then this would have removed those boot files (that's how Windows works because it can only ever have one boot partition at a time).

I would suggest checking your windows backup to find the bootmgr and /Boot directory and then setting the bootflag (I guess this will be on /dev/sda1) and the using a Windows Installation DVD or a Windows Repair CD to try to repair the Windows install.

---

### Post by geekhush on 2013-03-21
hi, so i did as recommended. i got a windows live on a pendrive and used it to boot and repair, now after doing that i lost my ubuntu boot entry too (grub). all is was greeted with was a blank screen saying "no operating system found" and "grub:". so i had to make another ubuntu live usb to repair my ubuntu install and cant log into windows yet. what else option have i got now?

---

### Post by geekhush on 2013-03-21
No i didn't have another install of windows and deleted nothing. I just migrated the wubi install to another partition different from windows ( C: ). Thanks for the help though and the info. :). i tried to repair using a windows live usb but that didnt help instead i lost my grub menu too. what do you suggest i do now?

---

### Post by bcbc on 2013-03-21
Do you have an Ubuntu CD/USB? You can boot it and reinstall grub. 
```
sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

---

### Post by geekhush on 2013-03-24
hi,
bcbc: will the command fix my windows problem too?? like i have got the ubuntu install running now..i mean i repaired it using a ubuntu usb. you see i am planning to stick with ubuntu for now but i will need my windows install for gaming and other stuffs too... so could you suggest me something so i could get my windows running please....

---

### Post by oldfred on 2013-03-24
post #8 should have repaired Windows. But if you just run the auto repairs, it also reinstalls the Windows boot loader to the MBR, overwriting grub. Better to use Windows command line repairs. And you may need chkdsk.

Rerun Bootinfoscript or BootInfo report which includes bootinfoscript just to see if Windows repairs did add the Windows boot files correctly. But It seems you still need Windows repairs.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Kr0nZ on 2013-03-24
Im not sure about windows 8, but in windows 7 I could fix the missing windows boot files by booting the windows install disk/usb then going to a command prompt and running "bootsect /nt60 C:", then running update-grub should get both working.

---

