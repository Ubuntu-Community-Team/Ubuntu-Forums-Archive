---
title: "Grub detecting the 'wrong' Windows version"
date: 2012-12-10
forum: General Help
---

### Post by Puddingfork on 2012-12-10
Basically I used to have Windows 7 Home
I got an SSD and installed a copy of Win 7 Pro (kept the old windows still there just in case)
I installed Ubuntu 12.10
Grub is only recognising Windows 7 Home

How do I make Grub recognise Windows 7 Pro?

My update-grub results
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sde1
done

```Here's the SSD section of my boot info script results.txt
```

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

```Here's a full copy of my boot info scrip result.txt
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 
    213683712 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 72 for .
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => Windows is installed in the MBR of /dev/sdf.
 => No boot loader is installed in the MBR of /dev/sdg.
 => Windows is installed in the MBR of /dev/sdl.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdl1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   322,766,202   322,766,140   7 NTFS / exFAT / HPFS
/dev/sda2         322,766,848   568,526,847   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda3         568,526,848 2,725,472,255 2,156,945,408   7 NTFS / exFAT / HPFS
/dev/sda4       2,725,472,256 2,729,377,791     3,905,536  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   234,441,647   234,441,647  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       206,847       204,800 EFI System partition
/dev/sdb2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb3         468,992   119,314,431   118,845,440 Data partition (Windows/Linux)
/dev/sdb4     119,314,432   150,034,431    30,720,000 Data partition (Windows/Linux)
/dev/sdb5     179,755,008   234,440,703    54,685,696 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 2,315,259,903 2,315,257,856   7 NTFS / exFAT / HPFS
/dev/sdc2       2,315,259,904 2,520,059,903   204,800,000   7 NTFS / exFAT / HPFS
/dev/sdc3       2,520,059,904 2,724,859,903   204,800,000   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS


Drive: sde _____________________________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *             63   976,767,830   976,767,768   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1               2,048 1,849,595,903 1,849,593,856   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204885504 bytes
199 heads, 63 sectors/track, 155820 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1                  63   829,850,111   829,850,049   7 NTFS / exFAT / HPFS


Drive: sdl _____________________________________________________________________

Disk /dev/sdl: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdl1               2,048 1,953,519,615 1,953,517,568   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5C3CB7253CB6F8DA                       ntfs       Win7_HomeOriginal
/dev/sda2        C668F82A68F81B3F                       ntfs       Win7ProBackup
/dev/sda3        4E92389F92388D89                       ntfs       Games
/dev/sda4        21c9f388-ce72-438d-b39f-2a7a79c6cc23   swap       
/dev/sdb1        0A7F-EF75                              vfat       
/dev/sdb3        3E1685D616858F97                       ntfs       
/dev/sdb4        D82050E12050C7E0                       ntfs       Steam_SSD
/dev/sdb5        07795bf3-dd15-4ab1-a29f-a917753d63f7   ext4       
/dev/sdc1        9CD8164ED8162754                       ntfs       MyDocuments
/dev/sdc2        00FCFCB3FCFCA3D6                       ntfs       Users
/dev/sdc3        72B22E79B22E41C9                       ntfs       Software
/dev/sdd1        025A904A5A903C7B                       ntfs       HDD-2.0.1_Backup2_5200
/dev/sde1        A080F61080F5ED22                       ntfs       HDD-1.1.0_OldBackups_5200
/dev/sdf1        AE5CE52B5CE4EED1                       ntfs       HP Desktop Drive
/dev/sdg1        589217C49217A612                       ntfs       Study
/dev/sdl1        4C44867444866116                       ntfs       Elements

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sdf1        /media/XXXX/HP Desktop Drive fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdg1        /media/XXXX/TAFE fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdl1        /media/XXXX/Elements     fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd1,gpt5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
else
  search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
    else
      search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
    fi
    linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
        else
          search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
    recordfail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
        else
          search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
        else
          search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-07795bf3-dd15-4ab1-a29f-a917753d63f7' {
    recordfail
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
        else
          search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
    else
      search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt5 --hint-efi=hd1,gpt5 --hint-baremetal=ahci1,gpt5  07795bf3-dd15-4ab1-a29f-a917753d63f7
    else
      search --no-floppy --fs-uuid --set=root 07795bf3-dd15-4ab1-a29f-a917753d63f7
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sde1)' --class windows --class os $menuentry_id_option 'osprober-chain-A080F61080F5ED22' {
    insmod part_msdos
    insmod ntfs
    set root='hd4,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd4,msdos1 --hint-efi=hd4,msdos1 --hint-baremetal=ahci4,msdos1  A080F61080F5ED22
    else
      search --no-floppy --fs-uuid --set=root A080F61080F5ED22
    fi
    chainloader +1
}
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=07795bf3-dd15-4ab1-a29f-a917753d63f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=21c9f388-ce72-438d-b39f-2a7a79c6cc23 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               1
               =                boot/initrd.img-3.5.0-19-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-19-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdh sdi sdj sdk 

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

```Thanks <3

---

### Post by oldfred on 2012-12-11
You have a newer system that boots in either UEFI mode or BIOS mode.

Windows & Ubuntu will install in either mode depending on from UEFI how you boot install media. If you boot UEFI mode it installs in UEFI or if you boot in BIOS it installs in BIOS.

Also:
       Windows will only boot from gpt partitioned drives with UEFI.
Windows x64 Installer determines which firmware has been used for booting the ISO/DVD/USB. If BIOS is used, only MBR is supported. If UEFI is used then only GPT is supported. Not vice-versa.

You have UEFI/gpt for sdb and BIOS/MBR for everything else. Only large drives over 2.2TB have to be gpt, but Arch suggests gpt for SSDs. I use gpt with my BIOS but only have Ubuntu on those drives and my Windows is on my MBR drive. I do not now use that Windows as I have to change BIOS from AHCI back to IDE to boot Windows, but cannot have SSD boot in IDE mode without issues with trim.

But you cannot boot a BIOS install from UEFI or vice-versa. So you either need to convert Windows in sda to UEFI or the install in sdb to BIOS/MBR.

Your BIOS Windows install also must have had another drive used as boot drive as it is missing two of the boot files. Windows can only boot from one active partition or the BIOS boot drive with the boot flag. All installs of Windows move boot files to that one active partition. You need a Windows repairCD to fix it. Make it the active partition or boot in BIOS with boot flag and run Windows repairs.

 Pictures here worth 1000+ words for Vista but still applies for all Windows.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Puddingfork on 2012-12-11
I'm pretty sure my Windows 7 Pro does boot in UEFI (I can still boot into it via. the BIOS). I'll go check, try doing a repair and have a read though that link. Thanks for the help :)

---

### Post by dcstar on 2012-12-11
> **Puddingfork said:**
> 
```

.........
sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        **/efi/Boot/bootx64.efi**
.......
```

What the previous post said about UEFI.

---

### Post by Puddingfork on 2012-12-11
All I really care about is having Windows 7 pro show up in Grub. So if I just changed Ubuntu to boot in UEFI would it then be easy to add Windows 7 Pro to Grub?

I haven't done anything yet since last posting (had some other things to attend to).

---

### Post by oldfred on 2012-12-11
If Windows pro is the UEFI install in sdb then you can use Boot-Repair to add a correct chain load entry to boot Windows in UEFI. Grub2's os-prober has a bug and creates the BIOS type entries that do not work with UEFI. But Boot-Repair creates a correct efi entry.

If you want to boot Windows in sda, you have to put boot flag on it and use a Windows repair CD or flash drive to add the missing boot files. Then you could boot it directly from BIOS mode only. I do not think you can boot in UEFI and chain load to a BIOS install as UEFI/BIOS do write parameters into hard drive that systems read. And each does it slightly differently.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by Puddingfork on 2012-12-11
Boot-repair got things working how I wanted them to, when I have time I'll perform the windows repair on sda.

Here's the BootInfo if you're interested
[http://paste.ubuntu.com/1425230/](http://paste.ubuntu.com/1425230/)

Thanks heaps for the help.

---

### Post by oldfred on 2012-12-11
Glad you got it working. :)

---

