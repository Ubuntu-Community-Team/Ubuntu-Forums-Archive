---
title: "Boot up issues"
date: 2019-04-06
forum: General Help
---

### Post by iamtheeggman2 on 2019-04-06
Hi,
today I put a usb mas storage device into my usb port of my new computer,  then the computer wouldn't respond to anything nor load the bios, i eventually had to use the reset function of the motherboard to get it going again. Then the windows 10 os on the new ssd didnt boot neither did the usb windows 10 installer find it to run any kind of repair, whic is strange. i eventually installed lubunto again to my hdd and then installed boot-repair, however after a few uses of boot repair i am still unable to load windows. windows doesn't load either with it being the only device attached on sata or even when it is connected to lubuntu with grub listing it as a os to boot. i now cant see it i the list for booting having done a clear mbr procedure. can anyone please advise?

---

### Post by Rubi1200 on 2019-04-06
Please use the link in my signature to create a boot info summary to post here for further review.

Thanks.

---

### Post by iamtheeggman2 on 2019-04-06
Hi the dogfish drive is the sdb1 which is the solid state drive with windows 10 on, sda is the normal hdd with linux resting on sda1 - sdc is just a usb drive which had windows 10 installer - which didnt work either because it couldnt see the windows installation.


 ```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid ada6bdbf-c286-4f83-9187-e736251e2ce8 root hd0,msdos1 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    57,116,671    57,114,624  83 Linux
/dev/sda2          57,116,672   976,766,975   919,650,304   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   185,122,815   185,120,768   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 7.5 GiB, 8011120640 bytes, 15646720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    15,646,719    15,644,672   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ada6bdbf-c286-4f83-9187-e736251e2ce8   ext4       
/dev/sda2        1FDA1CEB6049CD2A                       ntfs       Data
/dev/sdb1        A462CD2062CCF856                       ntfs       
/dev/sdc1        288C605F8C602A10                       ntfs       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr  6 23:55 ata-ATAPI_iHAS124_F_3524728_2E7701503291 -> ../../sr0
lrwxrwxrwx 1 root root  9 Apr  7 00:03 ata-DOGFISH_SSD_120GB_AA0000001911403146 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr  7 00:04 ata-DOGFISH_SSD_120GB_AA0000001911403146-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr  7 00:03 ata-WDC_WD5000AVDS-63U7B1_WD-WCAV9F433414 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr  7 00:03 ata-WDC_WD5000AVDS-63U7B1_WD-WCAV9F433414-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr  7 00:04 ata-WDC_WD5000AVDS-63U7B1_WD-WCAV9F433414-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Apr  7 00:03 usb-TDK_LoR_TF10_07074C4388D75F78-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Apr  7 00:03 usb-TDK_LoR_TF10_07074C4388D75F78-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Apr  7 00:03 wwn-0x5000000000000000 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr  7 00:04 wwn-0x5000000000000000-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Apr  7 00:03 wwn-0x50014ee1adfeda6f -> ../../sda
lrwxrwxrwx 1 root root 10 Apr  7 00:03 wwn-0x50014ee1adfeda6f-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr  7 00:04 wwn-0x50014ee1adfeda6f-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdc1        /media/home/288C605F8C602A10 fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)


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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
else
  search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=0
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
        set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
    else
      search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
    fi
        linux    /boot/vmlinuz-4.15.0-47-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-47-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
    menuentry 'Ubuntu, with Linux 4.15.0-47-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-47-generic-advanced-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
        else
          search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
        fi
        echo    'Loading Linux 4.15.0-47-generic ...'
            linux    /boot/vmlinuz-4.15.0-47-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-47-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-47-generic-recovery-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
        else
          search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
        fi
        echo    'Loading Linux 4.15.0-47-generic ...'
            linux    /boot/vmlinuz-4.15.0-47-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-47-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-advanced-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
        else
          search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-recovery-ada6bdbf-c286-4f83-9187-e736251e2ce8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ada6bdbf-c286-4f83-9187-e736251e2ce8
        else
          search --no-floppy --fs-uuid --set=root ada6bdbf-c286-4f83-9187-e736251e2ce8
        fi
        echo    'Loading Linux 4.15.0-20-generic ...'
            linux    /boot/vmlinuz-4.15.0-20-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-20-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.191341400 = 2.352934912    boot/grub/grub.cfg                             2
  12.297576904 = 13.204422656   boot/grub/i386-pc/core.img                     1
  12.343986511 = 13.254254592   boot/vmlinuz-4.15.0-20-generic                 1
  13.894729614 = 14.919352320   boot/vmlinuz-4.15.0-47-generic                 1
  13.894729614 = 14.919352320   vmlinuz                                        1
  12.343986511 = 13.254254592   vmlinuz.old                                    1
  14.221675873 = 15.270408192   boot/initrd.img-4.15.0-20-generic              2
  14.689517975 = 15.772749824   boot/initrd.img-4.15.0-47-generic              1
  14.689517975 = 15.772749824   initrd.img                                     1
  14.221675873 = 15.270408192   initrd.img.old                                 2


ADDITIONAL INFORMATION :
=================== log of boot-repair 20190407_0003 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in installed-session (Ubuntu 18.04.2 LTS, bionic, Ubuntu, i686)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.15.0-47-generic root=UUID=ada6bdbf-c286-4f83-9187-e736251e2ce8 ro quiet splash vt.handoff=1

=================== os-prober:
/dev/sda1:The OS now in use - Ubuntu 18.04.2 LTS CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="ada6bdbf-c286-4f83-9187-e736251e2ce8" TYPE="ext4" PARTUUID="000e7325-01"
/dev/sda2: LABEL="Data" UUID="1FDA1CEB6049CD2A" TYPE="ntfs" PARTUUID="000e7325-02"
/dev/sdb1: UUID="A462CD2062CCF856" TYPE="ntfs" PARTUUID="7a91217b-01"
/dev/sdc1: UUID="288C605F8C602A10" TYPE="ntfs" PARTUUID="5235729f-01"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sdb1.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Apr  6 18:08 grub.d
drwxr-xr-x  2 root root     4096 Apr  6 18:07 grub.d.bak
total 76
-rwxr-xr-x 1 root root 10046 Mar 18 16:11 00_header
-rwxr-xr-x 1 root root  6258 Mar 18 16:11 05_debian_theme
-rwxr-xr-x 1 root root 12693 Mar 18 16:11 10_linux
-rwxr-xr-x 1 root root 11298 Mar 18 16:11 20_linux_xen
-rwxr-xr-x 1 root root 12059 Mar 18 16:11 30_os-prober
-rwxr-xr-x 1 root root  1418 Mar 18 16:11 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mar 18 16:11 40_custom
-rwxr-xr-x 1 root root   216 Mar 18 16:11 41_custom
-rw-r--r-- 1 root root   483 Mar 18 16:11 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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
This installed-session is not EFI-compatible.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    notbiosboot, .
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda2.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sdb1.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /media/home/288C605F8C602A10.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    not-mmc, no-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA WDC WD5000AVDS-6:;
1:1049kB:29.2GB:29.2GB:ext4::boot;
2:29.2GB:500GB:471GB:ntfs::;

BYT;
/dev/sdb:120GB:scsi:512:512:msdos:ATA DOGFISH SSD 120G:;
1:1049kB:94.8GB:94.8GB:ntfs::boot;

BYT;
/dev/sdc:8011MB:scsi:512:512:msdos:TDK LoR TF10:;
1:1049kB:8011MB:8010MB:ntfs::boot;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        465.8G
sda1  part ext4    27.2G
sda2  part ntfs   438.5G Data
sdb   disk        111.8G
sdb1  part ntfs    88.3G
sdc   disk          7.5G
sdc1  part ntfs     7.5G
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /
sda2     1  0  0         /mnt/boot-sav/sda2
sdb      0  0  0 running
sdb1     0  0  0         /mnt/boot-sav/sdb1
sdc      1  0  1 running
sdc1     1  0  1         /media/home/288C605F8C602A10
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=5154280k,nr_inodes=187507,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1034352k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14159)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1034352k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdc1 on /media/home/288C605F8C602A10 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg lightnvm log lp0 mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 67 03  |........?.....g.|
00000020  00 00 00 00 80 00 80 00  ff bf d0 36 00 00 00 00  |...........6....|
00000030  04 00 00 00 00 00 00 00  ff 0b 6d 03 00 00 00 00  |..........m.....|
00000040  f6 00 00 00 01 00 00 00  2a cd 49 60 eb 1c da 1f  |........*.I`....|
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

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff b7 08 0b 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  56 f8 cc 62 20 cd 62 a4  |........V..b .b.|
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

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 00 00  ff b7 ee 00 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  10 2a 60 8c 5f 60 8c 28  |.........*`._`.(|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.0G     0  5.0G   0% /dev
tmpfs          tmpfs    1011M  1.4M 1009M   1% /run
/dev/sda1      ext4       27G  5.0G   21G  20% /
tmpfs          tmpfs     5.0G   28M  5.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.0G     0  5.0G   0% /sys/fs/cgroup
tmpfs          tmpfs    1011M   12K 1011M   1% /run/user/1000
/dev/sdc1      fuseblk   7.5G   65M  7.4G   1% /media/home/288C605F8C602A10
/dev/sda2      fuseblk   439G  172G  267G  40% /mnt/boot-sav/sda2
/dev/sdb1      fuseblk    89G   25G   64G  28% /mnt/boot-sav/sdb1

=================== fdisk -l:
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000e7325

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  57116671  57114624  27.2G 83 Linux
/dev/sda2       57116672 976766975 919650304 438.5G  7 HPFS/NTFS/exFAT




Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7a91217b

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1  *     2048 185122815 185120768 88.3G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 7.5 GiB, 8011120640 bytes, 15646720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5235729f

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 15646719 15644672  7.5G  7 HPFS/NTFS/exFAT




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBRs of all disks (except live-disks and removable disks without OS).
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (ATA WDC WD5000AVDS-6) disk!


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2019-04-06
Please use code tags which you can easily add using # icon in Forum's advanced editor.

With multiple drives, do not run any auto fix in Boot-Repair. It will want to install one boot loader to every drive.
You want Windows boot loader in MBR of Windows drive and grub in MBR of Ubuntu drive and BIOS set to boot from Ubuntu drive.
But note that grub only boots working Windows, so if grub does not boot Windows, you may have to directly boot from MBR of Windows drive or use your Windows repair disk.
From advanced mode in Boot-Repair chose install in sda1 and install grub boot loader to MBR of sda.
If that does not work choose the full reinstall of grub, make sure Internet is working before it erases old grub and downloads a new grub and installs it.

You do now need your Windows repair disk as your Windows install is missing its boot files.
You may have had the Windows boot partition on another drive. But can install those boot files into your main install in sdb1. You are missing bootmgr & BCD.
       Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  
You cannot do those fixes from Linux.

---

### Post by iamtheeggman2 on 2019-04-07
Hi,

I did the reinstall grub procedure using the boot-repair program if that is what you mean.

When I only have the ssd on the computer the windows usb didn't load and said it was unable to locate an os? That's strange too in that the USB should have let me have the choice to reinstall windows.

I believe my brother has Windows ten, can he copy his files to me or can I find these myself on my own?

Hi, I made another usb windows 10 installation disc which started up and it threw up an error message in its command prompt. After some Google search I discovered others had the same issue :

[https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/windows-10-bootrec-fixboot-access-is-denied/747c4180-7ff3-4bc2-b6cc-81e572d546df](https://answers.microsoft.com/en-us/windows/forum/windows_10-performance/windows-10-bootrec-fixboot-access-is-denied/747c4180-7ff3-4bc2-b6cc-81e572d546df)

"I had the same issue with the command Bootrec /Fixboot "Access is denied",

This only happens with Windows 10 1709 install media.

I tried the same command  with Windows 10 1703 install media and do not get the error "Access is denied".

This looks like an error with the install media for Windows 10 1709"


So I found the iso made another usb bootable drive and did the following commands without any errors yet when I turn it on with only the ssd windows installation it still tells me not a valid system disc! 

[https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/)


bootrec /FixMbr
bootrec /FixBoot
bootrec /ScanOs
bootrec /RebuildBcd

Edit: update

After the above failed I then went back into the usb startup disk to run the automated diagnostics and it made it run again! Wow!
Now I need to just get Linux going again, following the above procedures to install to its HDD and not tamper with the SSD windows drive.

Thanks for your help all of you!

---

