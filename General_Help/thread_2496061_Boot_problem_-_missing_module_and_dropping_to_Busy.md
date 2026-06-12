---
title: "Boot problem - missing module and dropping to Busybox (initramfs) after power outage"
date: 2024-03-12
forum: General Help
---

### Post by esalomo on 2024-03-12
Hello all,
Need desperate help before I'll wipe and re-install my server. ubuntu server 22.04 installed few monts ago and was working great until a power outage.
After the power outage - server which was running 24/7 for weeks - will not come-up - fail at boot, getting into Busybox (initramfs) for some reason.
I'm getting the messages "no arrays found" 
I did try to use the process in this thread - [https://ubuntuforums.org/showthread.php?t=1399810](https://ubuntuforums.org/showthread.php?t=1399810) but without any success - same results.
Uisng LiveCD, I did manage to get into the specific disk and to navigate through all files and folders but it will not boot up from this drive any longer - not sure why.
Any help would be very much apericiated 

I did ran the Bootinfoscript using LiveCD - see the output here:

#
                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks in partition 94 for .
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 108 for .

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       VMFS_volume_member
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-UcRLYl0C/sdb1: unknown filesystem type 'VMFS_volume_member'.

sdc1: __________________________________________________________________________

    File system:       VMFS_volume_member
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-UcRLYl0C/sdb1: unknown filesystem type 'VMFS_volume_member'.
mount: /tmp/BootInfo-UcRLYl0C/sdc1: unknown filesystem type 'VMFS_volume_member'.

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi

maindisk-ubuntu-lv': ___________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-UcRLYl0C/sdb1: unknown filesystem type 'VMFS_volume_member'.
mount: /tmp/BootInfo-UcRLYl0C/sdc1: unknown filesystem type 'VMFS_volume_member'.
mount: /tmp/BootInfo-UcRLYl0C/LVM/maindisk-ubuntu-lv': unknown filesystem type ''.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: WDC WD20EARX-32P
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2           4,096     4,198,399     4,194,304 Data partition (Linux)
/dev/sda3       4,198,400 3,907,026,943 3,902,828,544 Data partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5003ABYX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048   976,773,119   976,771,072 -

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5003ABYX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1           2,048   976,773,119   976,771,072 -

Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 28.9 GiB, 31029460992 bytes, 60604416 sectors
Disk model:                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048    60,604,415    60,602,368   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/mapper/maindisk-ubuntu--lv 6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8   ext4       
/dev/sda1                                                          
/dev/sda2        8fffa05f-ff76-4b99-93c0-22dc7217a7c1   ext4       
/dev/sda3        0a1PZK-fQl6-f4vk-mi5g-cmSE-j7eV-j6FDmU LVM2_member 
/dev/sdb1        5b0ee1c8-277c35d2-f1ac-0025902cfc4e    VMFS_volume_member 
/dev/sdc1        5b0ee1da-2a1d7f68-c57c-0025902cfc4e    VMFS_volume_member 
/dev/sdd1        4237-B105                              vfat       UBUNTU 22_0

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
maindisk-ubuntu--lv

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime,errors=continue,threads=single)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
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
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
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
insmod lvm
insmod ext2
set root='lvmid/dSVnF4-aeti-WzXr-DrmB-sdZC-7Gd8-FaPlLk/iyV4YB-ZZOQ-pXfs-3rA8-4kGk-8czB-atYEns'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvmid/dSVnF4-aeti-WzXr-DrmB-sdZC-7Gd8-FaPlLk/iyV4YB-ZZOQ-pXfs-3rA8-4kGk-8czB-atYEns'  6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8
else
  search --no-floppy --fs-uuid --set=root 6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8
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
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
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
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if [ ${grub_platform} != pc ]; then
      set linux_gfx_mode=keep
    elif hwmatch ${prefix}/gfxblacklist.txt 3; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  8fffa05f-ff76-4b99-93c0-22dc7217a7c1
    else
      search --no-floppy --fs-uuid --set=root 8fffa05f-ff76-4b99-93c0-22dc7217a7c1
    fi
    linux    /vmlinuz-5.15.0-91-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  
    initrd    /initrd.img-5.15.0-91-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8' {
    menuentry 'Ubuntu, with Linux 5.15.0-91-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.15.0-91-generic-advanced-6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  8fffa05f-ff76-4b99-93c0-22dc7217a7c1
        else
          search --no-floppy --fs-uuid --set=root 8fffa05f-ff76-4b99-93c0-22dc7217a7c1
        fi
        echo    'Loading Linux 5.15.0-91-generic ...'
        linux    /vmlinuz-5.15.0-91-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro  
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-5.15.0-91-generic
    }
    menuentry 'Ubuntu, with Linux 5.15.0-91-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.15.0-91-generic-recovery-6a8cfbf3-0e3d-42b3-9e35-71bfd71f58e8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_gpt
        insmod ext2
        set root='hd2,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,gpt2 --hint-efi=hd2,gpt2 --hint-baremetal=ahci2,gpt2  8fffa05f-ff76-4b99-93c0-22dc7217a7c1
        else
          search --no-floppy --fs-uuid --set=root 8fffa05f-ff76-4b99-93c0-22dc7217a7c1
        fi
        echo    'Loading Linux 5.15.0-91-generic ...'
        linux    /vmlinuz-5.15.0-91-generic root=/dev/mapper/ubuntu--vg-ubuntu--lv ro recovery nomodeset dis_ucode_ldr 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-5.15.0-91-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/35_fwupd ###
### END /etc/grub.d/35_fwupd ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
set timeout=30

loadfont unicode

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try or Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash --- 
    initrd    /casper/initrd
}
menuentry "Ubuntu (safe graphics)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz nomodeset file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash --- 
    initrd    /casper/initrd
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed only-ubiquity oem-config/enable=true quiet splash --- 
    initrd    /casper/initrd
}
grub_platform
if [ "$grub_platform" = "efi" ]; then
menuentry 'Boot from next volume' {
    exit 1
}
menuentry 'UEFI Firmware Settings' {
    fwsetup
}
else
menuentry 'Test memory' {
    linux16 /boot/memtest86+.bin
}
fi
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
2ae031aa0f40db119590000c2911d1b8
Unknown GPT Partiton Type
2ae031aa0f40db119590000c2911d1b8
Unknown BootLoader on maindisk-ubuntu-lv'



=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-UcRLYl0C/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-UcRLYl0C/Tmp_Log: No such file or directory
  skip_dev_dir: Couldn't split up device name maindisk-ubuntu-lv'.
  Volume group name "maindisk-ubuntu-lv'" has invalid characters.
  Cannot process volume group maindisk-ubuntu-lv'
  skip_dev_dir: Couldn't split up device name maindisk-ubuntu-lv'.
  Volume group name "maindisk-ubuntu-lv'" has invalid characters.
  Cannot process volume group maindisk-ubuntu-lv'
  skip_dev_dir: Couldn't split up device name maindisk-ubuntu-lv'.
  Volume group name "maindisk-ubuntu-lv'" has invalid characters.
  Cannot process volume group maindisk-ubuntu-lv'
hexdump: /dev/mapper/maindisk-ubuntu-lv': No such file or directory
hexdump: stdin: Bad file descriptor
hexdump: /dev/mapper/maindisk-ubuntu-lv': No such file or directory
hexdump: all input file arguments failed
#

---

