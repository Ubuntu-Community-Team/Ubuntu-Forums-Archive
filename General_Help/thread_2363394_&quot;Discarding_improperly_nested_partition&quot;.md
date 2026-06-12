---
title: "&quot;Discarding improperly nested partition&quot; error"
date: 2017-06-09
forum: General Help
---

### Post by boramalper on 2017-06-09
Hello all,

I am dual-booting Ubuntu 16.04 LTS with Windows 10 x64, and I noticed the problem when I couldn't find Windows in the GRUB menu. I tried running **os-prober** to fix the issue but I got the following error (repeated multiple times):

```
grub-probe: warning: Discarding improperly nested partition (hostdisk//dev/sda,gpt3,msdos2).
```

Unfortunately Google didn't return many results either. Here are the outputs of commands in advance that you might ask:

```
$ sudo fdisk -l
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 63564675-38A7-49B6-B654-CDC88B397AAB

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    2050047    2048000  1000M Windows recovery environment
/dev/sda2     2050048    2582527     532480   260M EFI System
/dev/sda3     2582528    4610047    2027520   990M Lenovo boot partition
/dev/sda4     4630528    4892671     262144   128M Microsoft reserved
/dev/sda5     4892672 1771964415 1767071744 842,6G Microsoft basic data
/dev/sda6  1872627712 1925056511   52428800    25G Microsoft basic data
/dev/sda7  1925056512 1953523711   28467200  13,6G Windows recovery environment
/dev/sda8  1771964416 1872627711  100663296    48G Linux filesystem

Partition table entries are not in disk order.

```

```
$ uname -a
Linux coma 4.8.0-54-generic #57~16.04.1-Ubuntu SMP Wed May 24 16:22:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

```
$ blkid
/dev/sda1: LABEL="WINRE_DRV" UUID="8848D9B548D9A1EC" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="1cdcf200-641f-4677-8d8a-ad6403289998"
/dev/sda2: SEC_TYPE="msdos" LABEL="SYSTEM_DRV" UUID="9775-89CB" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="e8d7d661-2e3e-42b9-bc3c-8c7015df64e2"
/dev/sda3: LABEL="LRS_ESP" UUID="84E0-4FD3" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="312251c6-0c3b-4c2d-8304-7406790b00c9"
/dev/sda5: LABEL="Windows8_OS" UUID="C8DEE4B8DEE49FC4" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="5553f8be-5829-4f82-b783-0da6ae7e1702"
/dev/sda6: LABEL="LENOVO" UUID="161EB4761EB4508B" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e4de2f4e-fc33-454e-b7be-869c3e8e838d"
/dev/sda7: LABEL="PBR_DRV" UUID="F602E83802E8000B" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="e42e2099-0cb3-4938-99ab-df58c7b73de5"
/dev/sda8: UUID="2b47a444-51a4-44b1-bdba-526ca744ba0f" TYPE="ext4" PARTUUID="bab1b7e6-f85f-4bd6-9821-84a63acf6692"

```

```
$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=9775-89CB  /boot/efi       vfat    umask=0077      0       1

```

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fallback.efi /efi/fedora/fwupx64.efi 
                       /efi/fedora/gcdx64.efi /efi/fedora/grubx64.efi 
                       /efi/fedora/MokManager.efi /efi/fedora/shim.efi 
                       /efi/fedora/shim-fedora.efi /efi/ubuntu/fbx64.efi 
                       /efi/ubuntu/fwupx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,610,047     2,027,520 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672 1,771,964,415 1,767,071,744 Data partition (Windows/Linux)
/dev/sda6   1,872,627,712 1,925,056,511    52,428,800 Data partition (Windows/Linux)
/dev/sda7   1,925,056,512 1,953,523,711    28,467,200 Windows Recovery Environment (Windows)
/dev/sda8   1,771,964,416 1,872,627,711   100,663,296 Data partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8848D9B548D9A1EC                       ntfs       WINRE_DRV
/dev/sda2        9775-89CB                              vfat       SYSTEM_DRV
/dev/sda3        84E0-4FD3                              vfat       LRS_ESP
/dev/sda4                                                          
/dev/sda5        C8DEE4B8DEE49FC4                       ntfs       Windows8_OS
/dev/sda6        161EB4761EB4508B                       ntfs       LENOVO
/dev/sda7        F602E83802E8000B                       ntfs       PBR_DRV
/dev/sda8        2b47a444-51a4-44b1-bdba-526ca744ba0f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda8        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
else
  search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=tr_TR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
    else
      search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
    fi
    linux    /boot/vmlinuz-4.8.0-54-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.8.0-54-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
    menuentry 'Ubuntu, with Linux 4.8.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-54-generic-advanced-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-54-generic ...'
        linux    /boot/vmlinuz-4.8.0-54-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-54-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-54-generic-init-upstart-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-54-generic ...'
        linux    /boot/vmlinuz-4.8.0-54-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-54-generic-recovery-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-54-generic ...'
        linux    /boot/vmlinuz-4.8.0-54-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-52-generic-advanced-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-52-generic ...'
        linux    /boot/vmlinuz-4.8.0-52-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-52-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-52-generic-init-upstart-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-52-generic ...'
        linux    /boot/vmlinuz-4.8.0-52-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-52-generic-recovery-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-52-generic ...'
        linux    /boot/vmlinuz-4.8.0-52-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-advanced-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-init-upstart-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-recovery-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
        linux    /boot/vmlinuz-4.8.0-36-generic.efi.signed root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-79-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-79-generic-advanced-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.4.0-79-generic ...'
        linux    /boot/vmlinuz-4.4.0-79-generic root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-79-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-79-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-79-generic-init-upstart-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.4.0-79-generic ...'
        linux    /boot/vmlinuz-4.4.0-79-generic root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-79-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-79-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-79-generic-recovery-2b47a444-51a4-44b1-bdba-526ca744ba0f' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt8 --hint-efi=hd0,gpt8 --hint-baremetal=ahci0,gpt8  2b47a444-51a4-44b1-bdba-526ca744ba0f
        else
          search --no-floppy --fs-uuid --set=root 2b47a444-51a4-44b1-bdba-526ca744ba0f
        fi
        echo    'Loading Linux 4.4.0-79-generic ...'
        linux    /boot/vmlinuz-4.4.0-79-generic root=UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-79-generic
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=2b47a444-51a4-44b1-bdba-526ca744ba0f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=9775-89CB  /boot/efi       vfat    umask=0077      0       1
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
e7afbfbf4fa38a449a5b6213eb736c22
Unknown BootLoader on sda3

00000000  78 02 00 4d 53 57 49 4e  34 2e 31 00 02 08 2a 00  |x..MSWIN4.1...*.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 f0 1e 00 bb 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d3 4f e0 84 4e  4f 20 4e 41 4d 45 20 20  |..).O..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 00 00 00 00 00  |  FAT32   ......|
00000060  50 41 00 18 d6 7f 00 00  b0 39 00 18 d6 7f 00 00  |PA.......9......|
00000070  90 22 00 18 d6 7f 00 00  b0 28 00 18 d6 7f 00 00  |.".......(......|
00000080  00 48 1f 00 00 00 00 00  00 20 08 00 00 00 00 00  |.H....... ......|
00000090  ff 67 27 00 00 00 00 00  02 00 00 00 00 00 00 00  |.g'.............|
000000a0  30 a4 68 2f d6 7f 00 00  00 00 00 00 00 00 00 00  |0.h/............|
000000b0  d0 46 00 18 d6 7f 00 00  31 00 00 00 00 00 00 00  |.F......1.......|
000000c0  20 29 00 18 d6 7f 00 00  d0 44 00 18 d6 7f 00 00  | ).......D......|
000000d0  01 00 00 00 00 00 00 00  8f 6d 70 74 00 00 00 00  |.........mpt....|
000000e0  f0 00 00 00 00 00 00 00  74 00 00 00 00 00 00 00  |........t.......|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  20 79 bb 2f d6 7f 00 00  00 00 00 00 00 00 00 00  | y./............|
00000110  d0 65 2a 01 00 00 00 00  c8 00 00 00 00 00 00 00  |.e*.............|
00000120  dc 04 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000150  00 00 00 00 00 00 00 00  b1 00 00 00 00 00 00 00  |................|
00000160  b0 39 00 18 d6 7f 00 00  00 26 00 18 d6 7f 00 00  |.9.......&......|
00000170  20 00 00 00 00 00 00 00  34 00 00 00 00 00 00 00  | .......4.......|
00000180  30 2c 00 18 d6 7f 00 00  d1 00 00 00 00 00 00 00  |0,..............|
00000190  d1 00 00 00 00 00 00 00  69 73 73 69 6e 67 00 00  |........issing..|
000001a0  50 00 00 00 00 00 00 00  64 00 00 00 00 00 00 00  |P.......d.......|
000001b0  40 26 00 18 d6 7f 00 00  c0 39 00 18 d6 7f 00 00  |@&.......9......|
000001c0  90 22 00 18 d6 7f 00 00  b0 28 00 18 d6 7f 00 00  |.".......(......|
000001d0  00 68 70 74 00 00 00 00  8f 05 00 00 00 00 00 00  |.hpt............|
000001e0  8e 6d 70 74 00 00 00 00  ff ff ff ff 04 00 00 00  |.mpt............|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ucZNqbxM/Tmp_Log: No such file or directory

```



Thanks in advance!

---

### Post by oldfred on 2017-06-09
> hostdisk//dev/sda,gpt3,msdos2

Did you at one time have MBR(msdos) partitioning and now have a hybrid? Which is not normally suggest, but was used my Mac to boot older Windows in BIOS mode on gpt drives. Windows only boots with UEFI from gpt partitioned drive.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
convert hybrid to protective MBR gdisk experts commands  p, x, n, p, w
[http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro](http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro)

You also are not showing the typical UEFI boot files for Windows in the ESP - efi system partition. Not sure if just missing or bootinfoscript does not show them?

---

### Post by boramalper on 2017-06-10
The answer on Ask Ubuntu says:

> 
[LIST=1]
[*]Fortunately, the solution is fairly straightforward, albeit non-intuitive:

[*]Boot to Ubuntu. (You can also do this from OS X, but you'd need to install gdisk and use a different disk device filename.)
[*]Open a Terminal window.
[*]Type sudo gdisk /dev/sda. After you're prompted for your password, **gdisk should launch and tell you, among other things, MBR: hybrid.**
[/LIST]


but when I started gdisk, I got the following output instead:

```
$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 63564675-38A7-49B6-B654-CDC88B397AAB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 23917 sectors (11.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  2700  Basic data partition
   2         2050048         2582527   260.0 MiB   EF00  EFI System Partition
   3         2582528         4610047   990.0 MiB   ED01  Basic data partition
   4         4630528         4892671   128.0 MiB   0C01  Microsoft reserved ...
   5         4892672      1771964415   842.6 GiB   0700  Basic data partition
   6      1872627712      1925056511   25.0 GiB    0700  Basic data partition
   7      1925056512      1953523711   13.6 GiB    2700  Basic data partition
   8      1771964416      1872627711   48.0 GiB    8300  

Command (? for help):
```

So MBR is already protective.

---

### Post by boramalper on 2017-06-10
Using **boot-repair** solved my problem (even though the error message persists, Windows is again on the menu).

---

### Post by oldfred on 2017-06-10
I might back up partition table info.
And just run the gdisk command and save with the w. That should just refresh MBR, gpt & backup gpt partition tables.
It does seem that gdisk thinks it is correct, but some other software is seeing something?

---

