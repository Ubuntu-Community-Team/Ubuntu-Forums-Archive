---
title: "Xubuntu/Windows Dual Boot Won't Boot to GRUB or to Optical Drive"
date: 2015-09-30
forum: General Help
---

### Post by mlnease on 2015-09-30
Hello,

My wife's HP laptop dual-boots to xubuntu 14.04 and Windows 8.  As of this morning, it won't boot to GRUB or to the optical drive.  I'm able to boot to xubuntu by holding down the escape key while rebooting (from Windows, *not* from xubuntu) and selecting it from Startup Menu > Boot Device Options.  Internal CD/DVD drive is not an option.

She's had enough of Windows now (*thank you*) and we'd be content to replace the Windows partition with a different *ubuntu distro (long story) but I'd like to restore GRUB to its proper function first (I've run ```
sudo update-grub
```, by the way, but to no avail).

First, is restoring GRUB my first priority; second, can anyone tell me how to do that and third, having done that should I expect to be able to install over the Windows partition from a live CD, obliterating it utterly without  any blowback?

Thanks in advance.

---

### Post by yancek on 2015-09-30
If you have windows 8, you are likely using UEFI to boot which adds some complications.  I wouldn't expect a working system to suddenly stop working without any changes having been made other than possibly a hardware failure which doesn't seem likely since you can still boot.  Boot into Xubuntu and go to the site below where you can download the boot repair software.  When you run it, select the option to Create BootInfo Summary rather than trying to repair.  You can then post the output here and some of the members familiar with UEFI should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mlnease on 2015-09-30
> **yancek said:**
> If you have windows 8, you are likely using UEFI to boot which adds some complications.  I wouldn't expect a working system to suddenly stop working without any changes having been made other than possibly a hardware failure which doesn't seem likely since you can still boot.  Boot into Xubuntu and go to the site below where you can download the boot repair software.  When you run it, select the option to Create BootInfo Summary rather than trying to repair.  You can then post the output here and some of the members familiar with UEFI should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for the quick response.  Is this the return you expected?

[URL="http://paste.ubuntu.com/12627552/"]http://paste.ubuntu.com/12627552/
[/URL]
Well, maybe not.  Here's the full output--I seem to recall there's a way to post something of this size but I don't remember what it is.  Hope this is OK.

 ```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/HP/bootmgr.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA.efi 
                       /EFI/HP/BIOSUpdate/CryptRSA32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt.efi 
                       /EFI/HP/BIOSUpdate/HpBiosMgmt32.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /EFI/HP/BIOSUpdate/HpBiosUpdate32.efi 
                       /EFI/HP/Boot/bootmgfw.efi /EFI/HP/Boot/bootmgr.efi 
                       /EFI/HP/Boot/memtest.efi 
                       /EFI/HP/SystemDiags/CryptRSA.efi 
                       /EFI/HP/SystemDiags/CryptRSA32.efi 
                       /EFI/HP/SystemDiags/HpSysDiags.efi 
                       /EFI/HP/SystemDiags/HpSysDiags32.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/HP/EFI/Boot/bootx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,333,247     1,331,200 Windows Recovery Environment (Windows)
/dev/sda2       1,333,248     1,865,727       532,480 EFI System partition
/dev/sda3       1,865,728     2,127,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,127,872   471,633,919   469,506,048 Data partition (Windows/Linux)
/dev/sda5     930,971,648   976,762,879    45,791,232 Data partition (Windows/Linux)
/dev/sda6     471,633,920   930,971,647   459,337,728 Data partition (Linux)
/dev/sda7     976,762,880   976,771,071         8,192 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        404EACCE4EACBDD2                       ntfs       WINRE
/dev/sda2        D497-F211                              vfat       
/dev/sda4        889C89809C896A10                       ntfs       Windows
/dev/sda5        5CD2F059D2F0393A                       ntfs       RECOVERY
/dev/sda6        fcfab5d8-6302-49a8-8a6a-e466ebe017c7   ext4       
/dev/sda7        68cdc6b5-33d5-48b7-b298-6da5bf6d5336   swap       
/dev/sr0                                                iso9660    Ubuntu 10.04 LTS i386

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Sep 30 15:30 ata-TOSHIBA_MQ01ABF050_84EZC7M9T -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 30 15:30 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 30 15:22 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 30 15:22 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Sep 30 15:22 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Sep 30 15:30 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep 30 15:22 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Sep 30 15:22 ata-TOSHIBA_MQ01ABF050_84EZC7M9T-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Sep 30 15:22 ata-hp_DVDRAM_GU90N_M8DE7I54133 -> ../../sr0
lrwxrwxrwx 1 root root  9 Sep 30 15:30 wwn-0x50000395b44056a1 -> ../../sda
lrwxrwxrwx 1 root root 10 Sep 30 15:30 wwn-0x50000395b44056a1-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 30 15:22 wwn-0x50000395b44056a1-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Sep 30 15:22 wwn-0x50000395b44056a1-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Sep 30 15:22 wwn-0x50000395b44056a1-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Sep 30 15:30 wwn-0x50000395b44056a1-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Sep 30 15:22 wwn-0x50000395b44056a1-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Sep 30 15:22 wwn-0x50000395b44056a1-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Sep 30 15:22 wwn-0x5001480000000000 -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda4        /mnt/boot-sav/sda4       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
else
  search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
    else
      search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
    fi
    linux    /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-65-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-advanced-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-recovery-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-advanced-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-recovery-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-advanced-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-recovery-fcfab5d8-6302-49a8-8a6a-e466ebe017c7' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        else
          search --no-floppy --fs-uuid --set=root fcfab5d8-6302-49a8-8a6a-e466ebe017c7
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-D497-F211' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  D497-F211
    else
      search --no-floppy --fs-uuid --set=root D497-F211
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=D497-F211  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda7 during installation
UUID=68cdc6b5-33d5-48b7-b298-6da5bf6d5336 none            swap    sw              0       0
--------------------------------------------------------------------------------


ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-09-30__15h29 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in installed-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=fcfab5d8-6302-49a8-8a6a-e466ebe017c7 ro quiet splash vt.handoff=7

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda6:The OS now in use - Ubuntu 14.04.3 LTS CurrentSession:linux
/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/sda1: LABEL="WINRE" UUID="404EACCE4EACBDD2" TYPE="ntfs"
/dev/sda2: UUID="D497-F211" TYPE="vfat"
/dev/sda4: LABEL="Windows" UUID="889C89809C896A10" TYPE="ntfs"
/dev/sda5: LABEL="RECOVERY" UUID="5CD2F059D2F0393A" TYPE="ntfs"
/dev/sda6: UUID="fcfab5d8-6302-49a8-8a6a-e466ebe017c7" TYPE="ext4"
/dev/sda7: UUID="68cdc6b5-33d5-48b7-b298-6da5bf6d5336" TYPE="swap"
/dev/sr0: LABEL="Ubuntu 10.04 LTS i386" TYPE="iso9660"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Jul  8 09:47 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Jun 26 04:16 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
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



/boot/efi detected in the fstab of sda6: UUID=D497-F211   (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda5/EFI/Boot/bootx64.efi

=================== efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,0000,0003,2001,2002,2003
Boot0000* Network Adapter (IPv4 UEFI)    ACPI(a0341d0,0)PCI(2,5)PCI(0,0)MAC(3464a97db8a4,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0RC
Boot0001* Windows Boot Manager    HD(2,145800,82000,5aac2f92-9164-47b9-983f-b67e429fa8b2)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...I................
Boot0002* ubuntu    HD(2,145800,82000,5aac2f92-9164-47b9-983f-b67e429fa8b2)File(EFIubuntushimx64.efi)
Boot0003* Network Adapter (IPv6 UEFI)    ACPI(a0341d0,0)PCI(2,5)PCI(0,0)MAC(3464a97db8a4,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  683MB   682MB   ntfs            Basic data partition          hidden, diag
2      683MB   955MB   273MB   fat32           EFI system partition          boot
3      955MB   1089MB  134MB                   Microsoft reserved partition  msftres
4      1089MB  241GB   240GB   ntfs            Basic data partition          msftdata
6      241GB   477GB   235GB   ext4
5      477GB   500GB   23.4GB  ntfs            Basic data partition          hidden, msftdata
7      500GB   500GB   4194kB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA TOSHIBA MQ01ABF0;
1:1049kB:683MB:682MB:ntfs:Basic data partition:hidden, diag;
2:683MB:955MB:273MB:fat32:EFI system partition:boot;
3:955MB:1089MB:134MB::Microsoft reserved partition:msftres;
4:1089MB:241GB:240GB:ntfs:Basic data partition:msftdata;
6:241GB:477GB:235GB:ext4::;
5:477GB:500GB:23.4GB:ntfs:Basic data partition:hidden, msftdata;
7:500GB:500GB:4194kB:linux-swap(v1)::;

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label

=================== lsblk:
KNAME TYPE FSTYPE    SIZE LABEL    MODEL    UUID
sda   disk         465.8G          TOSHIBA
sda1  part ntfs      650M WINRE             404EACCE4EACBDD2
sda2  part vfat      260M                   D497-F211
sda3  part           128M
sda4  part ntfs    223.9G Windows           889C89809C896A10
sda5  part ntfs     21.9G RECOVERY          5CD2F059D2F0393A
sda6  part ext4      219G                   fcfab5d8-6302-49a8-8a6a-e466ebe017c7
sda7  part swap        4M                   68cdc6b5-33d5-48b7-b298-6da5bf6d5336
sr0   rom  iso9660 699.5M Ubuntu 10.04 LTS i386
DVDRAM G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /boot/efi
sda3     1  0  0
sda4     1  0  0         /mnt/boot-sav/sda4
sda5     1  0  0         /mnt/boot-sav/sda5
sda6     1  0  0         /
sda7     1  0  0         [SWAP]
sr0      1  0  1 running


=================== mount:
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda2 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=rose)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 14 00 00 00 00 00  |.........O......|
00000030  aa d8 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d2 bd ac 4e ce ac 4e 40  |...........N..N@|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 14 00  |........?....X..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 11 f2 97 d4 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 78 20 00  |........?....x .|
00000020  00 00 00 00 80 00 80 00  ff 17 fc 1b 00 00 00 00  |................|
00000030  ab e3 9e 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  10 6a 89 9c 80 89 9c 88  |.........j......|
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
ls sda5/efi:
ls sda5: Boot
bootmgr
bootmgr.efi
EFI
preload
Recovery
$RECYCLE.BIN
RP.ini
sources
System Volume Information  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
ls /boot/efi/efi : Boot
HP
Microsoft
ubuntu
Error efitmp. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 80 7d 37  |........?.....}7|
00000020  00 00 00 00 80 00 80 00  ff b7 ba 02 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  3a 39 f0 d2 59 f0 d2 5c  |........:9..Y..|
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

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda6      ext4      216G   15G  190G   8% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  1.7G   12K  1.7G   1% /dev
tmpfs          tmpfs     340M  1.2M  339M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.7G  564K  1.7G   1% /run/shm
none           tmpfs     100M   28K  100M   1% /run/user
/dev/sda2      vfat      256M  108M  149M  43% /boot/efi
/dev/sda1      fuseblk   650M  258M  393M  40% /mnt/boot-sav/sda1
/dev/sda4      fuseblk   224G   47G  178G  21% /mnt/boot-sav/sda4
/dev/sda5      fuseblk    22G   20G  2.5G  89% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xea59fd20

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda6, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


=================== Final advice in case of suggested repair


The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will not act on the boot.


```




Thanks again and in advance.

---

### Post by oldfred on 2015-09-30
HP & UEFI make it a bit more difficult. 
How did you get it to boot before? Boot-Repair used to do a work around where it copied grub into the Windows /EFI/Microsoft/Boot folder & rename grub to be the Windows boot file. Then HP would boot grub as it thought it was booting Windows. But Windows updates overwrite that work around.

Better work around is to copy the files in /EFI/ubuntu into /EFI/Boot and rename shim to bootx64.efi. Back up current bootx64.efi first.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886

      [/URL]
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Also more details on UEFI fixes in link below in my signature.


    [URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

---

### Post by mlnease on 2015-09-30
> **oldfred said:**
> HP & UEFI make it a bit more difficult. 
How did you get it to boot before? Boot-Repair used to do a work around where it copied grub into the Windows /EFI/Microsoft/Boot folder & rename grub to be the Windows boot file. Then HP would boot grub as it thought it was booting Windows. But Windows updates overwrite that work around.

Better work around is to copy the files in /EFI/ubuntu into /EFI/Boot and rename shim to bootx64.efi. Back up current bootx64.efi first.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886

      [/URL]
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Also more details on UEFI fixes in link below in my signature.


    [URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]
Thanks for this.  A bit complicated for me but if necessary I'll try to make it work.  

Might the solution be simpler if I were to remove Windows first?

---

### Post by oldfred on 2015-09-30
Should not matter whether you have Windows or not.

If you want just Ubuntu you can install it in BIOS boot mode on a gpt partitioned drive. In UEFI you have to turn on CSM and have grub installed to gpt drive's protective MBR.         CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
You also have to have a tiny 1 or 2MB unformatted partition with the bios_grub flag(if gparted) for grub to install correctly to MBR. But there are some advantages to UEFI.

       UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by mlnease on 2015-10-01
> **oldfred said:**
> Should not matter whether you have Windows or not.

If you want just Ubuntu you can install it in BIOS boot mode on a gpt partitioned drive. In UEFI you have to turn on CSM and have grub installed to gpt drive's protective MBR.         CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    
You also have to have a tiny 1 or 2MB unformatted partition with the bios_grub flag(if gparted) for grub to install correctly to MBR. But there are some advantages to UEFI.

       UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Thanks again for your time and attention.  Does this mean that, on her HP, she'd have the same problem even if we did a clean, single *ubuntu reinstall, wiping everything on the hard drive?  In other words, I guess I'm beginning to understand that this is an HP firmware problem not related to Windows--correct?

---

### Post by oldfred on 2015-10-01
If you only have Ubuntu on an HP, you can change the UEFI entry to read "Windows" but boot shim or grub's efi boot files. System still thinks it is booting Windows as it just looks for description, but boots grub/ubuntu.

Or you can install in CSM/BIOS boot mode which works. You still can use gpt partitioning with Ubuntu, but then need a tiny 1 or 2MB unformatted partition with the bios_grub flag (if gparted) or ef02 code if gdisk.

I would still fully backup Windows and using HP recovery partition make recovery set of DVDs or flash drive. Many users come back later and have one application they want that only runs in Windows or want to sell system and have to restore Windows. You paid for Windows so best to at least keep a copy.

---

### Post by mlnease on 2015-10-01
> **oldfred said:**
> If you only have Ubuntu on an HP, you can change the UEFI entry to read "Windows" but boot shim or grub's efi boot files. System still thinks it is booting Windows as it just looks for description, but boots grub/ubuntu.

Clever.

> Or you can install in CSM/BIOS boot mode which works. You still can use gpt partitioning with Ubuntu, but then need a tiny 1 or 2MB unformatted partition with the bios_grub flag (if gparted) or ef02 code if gdisk.

I would still fully backup Windows and using HP recovery partition make recovery set of DVDs or flash drive. Many users come back later and have one application they want that only runs in Windows or want to sell system and have to restore Windows. You paid for Windows so best to at least keep a copy.

Sound advice, thanks.  Meanwhile I'll reread and try to digest your references to UEFI, CSM, gpt drive's  protective MBR, etc.  All Greek to me at this point.

Is this the wave of the future?  Are *ubuntu users going to have to jump through all these hoops in future just to get their OS's to boot?  Is it the end of GRUB working with new firmware?

Oh and finally--if you haven't already answered this--why is it presently impossible for me to boot to the CD/DVD drive, even after forcing the boot menu (as I did to boot to xubuntu)?

Thanks again for all your time and attention.

---

### Post by oldfred on 2015-10-01
Some of the new UEFI systems, require you to turn on or allow booting from anything other than the secure boot Windows. You may have a setting somewhere for USB boot.
And often best to have secure boot off. If you want it on, you can only dual boot from UEFI menu, not grub.

Some definitions of terms at end of the link in my signature.

---

