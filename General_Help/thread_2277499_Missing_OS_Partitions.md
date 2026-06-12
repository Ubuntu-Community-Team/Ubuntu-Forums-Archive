---
title: "Missing OS Partitions"
date: 2015-05-09
forum: General Help
---

### Post by utkusaridede on 2015-05-09
[FONT=arial]I have tried to install Ubuntu 14.04 LTS alongside of the Windows 7. But ubuntu installation progress could not find partitions, it only shows whole ssd. After using gparted, finally I have reached to partitions and choose "something else" option. Created "/" and "swap area", then installed Ubuntu 14.04 LTS. At the end of the installation, I have encounter with  "error: no such device: ..." at the grub rescue panel. Afterwards I mounted Ubuntu live usb and used boot repair. Firstly, I clicked "restore mbr" and apply, there was no change. Secondly I clicked "Recommended Repair" and did all instructions given by graphical interface. After recommended repair, ubuntu option in grub has returned, but windows option is still missing. Here is my latest boot info: "[/FONT][http://paste.ubuntu.com/11042392](http://paste.ubuntu.com/11042392)[FONT=arial]". Thank you for your helps.

[/FONT]```
[COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015][/COLOR]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 root hd0,msdos2 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   129,378,303   129,376,256   7 NTFS / exFAT / HPFS
/dev/sda2         129,378,304   226,142,207    96,763,904  83 Linux
/dev/sda3         226,142,208   234,440,703     8,298,496  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   976,771,071   976,769,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        90624C6B624C57DC                       ntfs       
/dev/sda2        5ddf6df9-304d-4f61-bdfe-53fcea26b7a7   ext4       
/dev/sda3        78436b56-b757-4c3f-aced-36d4f0c3ed89   swap       
/dev/sdb1        332D7BD17E3B3B4F                       ntfs       Archive

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  9 15:00 ata-Hitachi_HTS545050A7E380_TA95113VGS86RS -> ../../sdb
lrwxrwxrwx 1 root root 10 May  9 14:36 ata-Hitachi_HTS545050A7E380_TA95113VGS86RS-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  9 15:00 ata-KINGSTON_SHFS37A120G_50026B724708040A -> ../../sda
lrwxrwxrwx 1 root root 10 May  9 15:01 ata-KINGSTON_SHFS37A120G_50026B724708040A-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  9 14:36 ata-KINGSTON_SHFS37A120G_50026B724708040A-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  9 14:36 ata-KINGSTON_SHFS37A120G_50026B724708040A-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 May  9 15:00 wwn-0x5000cca6f3ca9361 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  9 14:36 wwn-0x5000cca6f3ca9361-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 May  9 15:00 wwn-0x50026b724708040a -> ../../sda
lrwxrwxrwx 1 root root 10 May  9 15:01 wwn-0x50026b724708040a-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May  9 14:36 wwn-0x50026b724708040a-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 May  9 14:36 wwn-0x50026b724708040a-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/utku/Archive      fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
else
  search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
    else
      search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
    fi
    linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-52-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        else
          search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        else
          search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        else
          search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-5ddf6df9-304d-4f61-bdfe-53fcea26b7a7' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        else
          search --no-floppy --fs-uuid --set=root 5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=78436b56-b757-4c3f-aced-36d4f0c3ed89 none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-05-09__15h00 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in installed-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic root=UUID=5ddf6df9-304d-4f61-bdfe-53fcea26b7a7 ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sda2:The OS now in use - Ubuntu 14.04 LTS CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Windows 7 (loader):Windows1:chain

=================== blkid:
/dev/sda1: UUID="90624C6B624C57DC" TYPE="ntfs"
/dev/sda2: UUID="5ddf6df9-304d-4f61-bdfe-53fcea26b7a7" TYPE="ext4"
/dev/sda3: UUID="78436b56-b757-4c3f-aced-36d4f0c3ed89" TYPE="swap"
/dev/sdb1: LABEL="Archive" UUID="332D7BD17E3B3B4F" TYPE="ntfs"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 May  9 14:30 grub.d
drwxr-xr-x  2 root root     4096 May  9 14:30 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




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
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/utku/Archive.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA KINGSTON SHFS37A (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      1049kB  66.2GB  66.2GB  primary  ntfs            boot
2      66.2GB  116GB   49.5GB  primary  ext4
3      116GB   120GB   4249MB  primary  linux-swap(v1)


Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  500GB  500GB  primary  ntfs         boot

=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA KINGSTON SHFS37A;
1:1049kB:66.2GB:66.2GB:ntfs::boot;
2:66.2GB:116GB:49.5GB:ext4::;
3:116GB:120GB:4249MB:linux-swap(v1)::;

BYT;
/dev/sdb:500GB:scsi:512:4096:msdos:ATA Hitachi HTS54505;
1:1049kB:500GB:500GB:ntfs::boot;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL   MODEL      UUID
sda   disk        111,8G         KINGSTON S
sda1  part ntfs    61,7G                    90624C6B624C57DC
sda2  part ext4    46,1G                    5ddf6df9-304d-4f61-bdfe-53fcea26b7a7
sda3  part swap       4G                    78436b56-b757-4c3f-aced-36d4f0c3ed89
sdb   disk        465,8G         Hitachi HT
sdb1  part ntfs   465,8G Archive            332D7BD17E3B3B4F

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0         /
sda3     0  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /media/utku/Archive


=================== mount:
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=utku)
/dev/sdb1 on /media/utku/Archive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f b6 07 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  dc 57 4c 62 6b 4c 62 90  |.........WLbkLb.|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 38 3a 00 00 00 00  |.........O8:....|
00000030  04 00 00 00 00 00 00 00  ff 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4f 3b 3b 7e d1 7b 2d 33  |........O;;~.{-3|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda2      ext4       46G  4.0G   40G  10% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  1.9G  8.0K  1.9G   1% /dev
tmpfs          tmpfs     384M  1.2M  383M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G  4.8M  1.9G   1% /run/shm
none           tmpfs     100M   72K  100M   1% /run/user
/dev/sdb1      fuseblk   466G  148G  319G  32% /media/utku/Archive
/dev/sda1      fuseblk    62G   47G   15G  77% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df2ec

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   129378303    64688128    7  HPFS/NTFS/exFAT
/dev/sda2       129378304   226142207    48381952   83  Linux
/dev/sda3       226142208   234440703     4149248   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd034e360

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT


User choice: Is sda (120GB) a removable disk? no




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (120GB) disk!

The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)


=================== User settings
The settings chosen by the user will not act on the boot.

 
```[FONT=arial]
[/FONT]

---

### Post by grahammechanical on 2015-05-09
You could try loading Ubuntu and running this command:

```
sudo update-grub
```

Does the printout show a Windows 7 boot loader?

Regards.

---

### Post by yancek on 2015-05-09
The boot repair output clearly shows a windows partition on the first partition of each drive.  There are no menuentries in the grub.cfg file for whatever reason so the first thing I would suggest you do is boot Ubuntu and open a terminal and run:  sudo update-grub
Watch the output for a windows entry.  If you don't see one run this command and after running it, run the update-grub again:  sudo os-prober
If that doesn't meet with success, post back with the results of the commands.

---

### Post by utkusaridede on 2015-05-09
When I entered $sudo update-grub, the result comes with;
```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sdb1
done

```

But I do not have any windows at /dev/sdb1, its my archive disc that just contains private files.

---

### Post by utkusaridede on 2015-05-09
Also, If I choose "Windows 7 (loader) on /dev/sda1; Windows Boot Manager screen welcomes me;
```

"Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your Windows intallation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."
If you do not have this disc, contact your system admin....

Status: 0xc000000e
Info: The boot selection failed because a required device is inaccessible.

```

---

### Post by Bucky Ball on 2015-05-09
Have you tried following those instructions? So you have got an entry in the grub boot options when you restart your machine and this is what happens when you choose it? 

Also, do not edit grub.cfg directly. Edit /etc/default/grub if you want to make any changes, then 'sudo update-grub' to make those changes stick. They are written to grub.cfg then.

---

### Post by Bucky Ball on 2015-05-09
Have you tried following those instructions? So you have got an entry in the grub boot options when you restart your machine and this is what happens when you choose it? You have been advised a couple of times to 'sudo update-grub' in Ubuntu then reboot to see if it picks up your Windows install. Have you done that and, if so, where are you now?

Also, do not edit grub.cfg directly. Edit /etc/default/grub if you want to make any changes, then 'sudo update-grub' to make those changes stick. They are written to grub.cfg then.

---

### Post by utkusaridede on 2015-05-09
I have tried both sudo grub-update and sudo os-prober. The result of sudo os-prober is; 
```

/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Windows 7 (loader):Windows1:chain

```

---

### Post by Bucky Ball on 2015-05-09
Well, it's 'sudo update-grub' so 'sudo grub-update' wouldn't have gotten you far. ;)

---

### Post by utkusaridede on 2015-05-09
I wrote by mistake that "sudo grub-update". The previous post of mine was correct, that is, I used correct one.

---

### Post by oldfred on 2015-05-09
Grub only boots working Windows. And if you have bootmgr & BCD backed up, it finds those as that is how it tells if Windows partition if bootable. Windows uses boot flag to know which partition has boot files.

You may be able to press f8 at the same time you press enter for Windows in grub menu. Most have found it is too quick and you just have to temporarily reinstall Windows boot loader. Or better to have Windows repair CD or flash drive for Windows repairs.
You can use Boot-Repair to reinstall Windows boot loader and then use it to reinstall grub after you fix Windows.

 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

