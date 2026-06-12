---
title: "Boot DOS from GRUB 2"
date: 2013-12-07
forum: General Help
---

### Post by GameX2 on 2013-12-07
Hi

I've succesfully installed MS-DOS 7.1 next to Windows 7 on a modern PC, following this guide:

[URL="http://www.thpc.info/dual/7/install_dos710_on_win7.htmlI"]http://www.thpc.info/dual/7/install_dos710_on_win7.html

[/URL]I can boot MS-DOS from a Super GRUB disk without problem; when I select Detect any OS, MS-DOS is found and is bootable.

I ve even installed Windows 3.1 on top of it with a quick patch.Altought I use VMware quite often, I just wanted to see if this was possible at all, since DOS is very basic.

No sound and probably wont ever have, but its actually funny to see it working.
I just cant boot from DOS directly, without booting from a Super GRUB disk.

I booted in Ubuntu, and ran sudo update-grub, but MS-DOS 7.1 is not found.Have not been able to succesfully boot DOS from the Windows 7 bootloader as well.  I feel like booting the OS from GRUB should be possible, since Super GRUB Disk is actually capable of detecting and booting it.

Here's a screenshot of my partition table:

[http://i.imgur.com/HC86nf1.png](http://i.imgur.com/HC86nf1.png)

Can anyone help please?
Thanks for the help, I appreciate it.

---

### Post by heir4c on 2013-12-07
What gives (from out Ubuntu) the command:
```
sudo os-prober
```
Can you see DOS in the list?

---

### Post by GameX2 on 2013-12-07
Unfortunately, no.  Here's the output:

```
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows 7 (loader):Windows1:chain
/dev/sda5:Linux Mint 13 Maya (13):LinuxMint:linux
```

This might help - I've followed the steps of the guide here: [http://www.thpc.info/dual/7/install_dos710_on_win7.html](http://www.thpc.info/dual/7/install_dos710_on_win7.html)
The installation was dead easy actually - but since it's MS-DOS 7.1, it was DOS that came with Windows 98.  The guide recommend, using EasyBCD to add a **Windows 98** boot entry, and not DOS.

Additionnal info: I'm trying to reinstall my GRUB using Boot Repair right now (Reparation don't detect DOS as usual), and the auto-repair encounter a problem.  I broke my Windows 7 bootloader really badly (Had to type tons of commands to delete and reinstall bootloader totally from scratch), and GRUB was erased as well - now I'm trying to reinstall GRUB.
What I mean, is that BootRepair gave this BootInfo script for help:

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 5Sep2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

[SIZE=4][B]sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM[/B][/SIZE]

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 13 Maya 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     1,044,224     1,044,162   7 NTFS / exFAT / HPFS
/dev/sda2           1,044,480     3,125,247     2,080,768   b W95 FAT32
/dev/sda3           3,125,248   420,681,727   417,556,480   7 NTFS / exFAT / HPFS
/dev/sda4         420,681,728   625,142,447   204,460,720   5 Extended
/dev/sda5         452,145,152   466,827,263    14,682,112  83 Linux
/dev/sda6         466,829,312   624,115,711   157,286,400  83 Linux
/dev/sda7         624,117,760   625,141,759     1,024,000  82 Linux swap / Solaris
/dev/sda8         420,683,776   452,143,103    31,459,328  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52B084CCB084B7CD                       ntfs       SYSTEM_DRV
/dev/sda2        A5F7-8321                              vfat       MS-DOS
/dev/sda3        B6E88D0CE88CCC55                       ntfs       Windows7_OS
/dev/sda5        cd48855a-ae7e-45a3-be38-d712a5fadd89   ext4       Mint_OS
/dev/sda6        3b44bdda-dbc7-405a-b4c2-d314939ec30d   ext4       Ubuntu_Home
/dev/sda7        417a922d-e910-48f2-853f-4ba9849edeb5   swap       
/dev/sda8        33f9883d-fede-43bc-90d7-af29c7a1f6fe   ext4       Raring_OS
/dev/sr0                                                iso9660    CDROM
/dev/zram0       fbb3d4ac-bf3e-45af-87c3-9ae69a36f589   swap       
/dev/zram1       36515f64-81f5-4cc6-b152-f5e5ee377ff7   swap       
/dev/zram2       d51a8500-f8e7-4f49-8887-984d03661af6   swap       
/dev/zram3       2451ab5b-14c1-49e4-8096-6ae3423edc20   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/Windows7_OS       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /home                    ext4       (rw)
/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professionnel [x86 Edition]" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINNT="Microsoft Windows 2k Professionnel" /fastdetect--------------------------------------------------------------------------------

[SIZE=4]*************************** This boot.ini is not important.  These are older entries now invalid  *************[/SIZE]





=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
  set locale_dir=($root)/boot/grub/locale
  set lang=fr_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 52B084CCB084B7CD
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root B6E88D0CE88CCC55
    chainloader +1
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-33f9883d-fede-43bc-90d7-af29c7a1f6fe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
    linux /boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro quiet splash i915.lvds_downclock=1 $vt_handoff
    initrd /boot/initrd.img-3.8.0-19-generic
}
menuentry "Ubuntu, avec Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
    linux /boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro quiet splash i915.lvds_downclock=1 $vt_handoff
    initrd /boot/initrd.img-3.8.0-19-generic
}
menuentry "Ubuntu, avec Linux 3.8.0-19-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
    linux /boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset
    initrd /boot/initrd.img-3.8.0-19-generic
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=417a922d-e910-48f2-853f-4ba9849edeb5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.433528900 = 234.541215744  boot/grub/grub.cfg                             1
 217.840412140 = 233.904361472  boot/grub/core.img                             1
 221.861801147 = 238.222295040  boot/vmlinuz-3.2.0-23-generic                  1
 221.861801147 = 238.222295040  vmlinuz                                        1
 216.753528595 = 232.737329152  boot/initrd.img-3.2.0-23-generic               5
 216.753528595 = 232.737329152  initrd.img                                     5

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
set root='hd0,msdos8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
else
  search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
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
menuentry 'Kubuntu GNU/Linux' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
    else
      search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
    fi
    linux    /boot/vmlinuz-3.8.0-30-generic root=/dev/sda8 ro   quiet splash $vt_handoff
}
submenu 'Advanced options for Kubuntu GNU/Linux' $menuentry_id_option 'gnulinux-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-30-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=/dev/sda8 ro   quiet splash $vt_handoff
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-30-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=/dev/sda8 ro recovery nomodeset 
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-27-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-27-generic ...'
        linux    /boot/vmlinuz-3.8.0-27-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-27-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-27-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-27-generic ...'
        linux    /boot/vmlinuz-3.8.0-27-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-27-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-26-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-26-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-26-generic ...'
        linux    /boot/vmlinuz-3.8.0-26-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-26-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-26-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-26-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-26-generic ...'
        linux    /boot/vmlinuz-3.8.0-26-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-26-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-25-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-25-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-23-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-23-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-23-generic ...'
        linux    /boot/vmlinuz-3.8.0-23-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-23-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-22-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-22-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-22-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-22-generic ...'
        linux    /boot/vmlinuz-3.8.0-22-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-22-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-21-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-21-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-21-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-21-generic ...'
        linux    /boot/vmlinuz-3.8.0-21-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-21-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-19-generic' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Kubuntu GNU/Linux, with Linux 3.8.0-19-generic (recovery mode)' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-33f9883d-fede-43bc-90d7-af29c7a1f6fe' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  33f9883d-fede-43bc-90d7-af29c7a1f6fe
        else
          search --no-floppy --fs-uuid --set=root 33f9883d-fede-43bc-90d7-af29c7a1f6fe
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-52B084CCB084B7CD' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52B084CCB084B7CD
    else
      search --no-floppy --fs-uuid --set=root 52B084CCB084B7CD
    fi
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-B6E88D0CE88CCC55' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  B6E88D0CE88CCC55
    else
      search --no-floppy --fs-uuid --set=root B6E88D0CE88CCC55
    fi
    chainloader +1
}
menuentry 'Linux Mint 13 Maya (13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-cd48855a-ae7e-45a3-be38-d712a5fadd89' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  cd48855a-ae7e-45a3-be38-d712a5fadd89
    else
      search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
    fi
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
submenu 'Advanced options for Linux Mint 13 Maya (13)' $menuentry_id_option 'osprober-gnulinux-advanced-cd48855a-ae7e-45a3-be38-d712a5fadd89' {
    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic--cd48855a-ae7e-45a3-be38-d712a5fadd89' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  cd48855a-ae7e-45a3-be38-d712a5fadd89
        else
          search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
        fi
        linux /boot/vmlinuz-3.2.0-23-generic root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-23-generic
    }
    menuentry 'Linux Mint 13 Cinnamon 64-bit, 3.2.0-23-generic (/dev/sda5) -- recovery mode (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro recovery nomodeset-cd48855a-ae7e-45a3-be38-d712a5fadd89' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  cd48855a-ae7e-45a3-be38-d712a5fadd89
        else
          search --no-floppy --fs-uuid --set=root cd48855a-ae7e-45a3-be38-d712a5fadd89
        fi
        linux /boot/vmlinuz-3.2.0-23-generic root=UUID=cd48855a-ae7e-45a3-be38-d712a5fadd89 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-23-generic
    }
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda9 :
UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda8 :
UUID=7BCBDD1058C5D153 /media/DATA ntfs-3g defaults,nls=utf8,umask=0000,windows_names 0 0    0    1
#Entry for /dev/sdc1 :
UUID=D2CCB5D2CCB5B159    /media/BERGER-CSTJ    ntfs-3g defaults,noauto,nls=utf8,umask=0000,windows_names 0 0
UUID=D2CCB5D2CCB5B159    /media/BERGER-CSTJ-2    ntfs-3g defaults,noauto,nls=utf8,umask=0000,windows_names 0 0
#Entry for /dev/sda3 :
UUID=B6E88D0CE88CCC55 /media/Windows7_OS ntfs-3g defaults,nls=utf8,umask=0000,windows_names 0 0 
#Entry for /dev/sda6 :
UUID=3b44bdda-dbc7-405a-b4c2-d314939ec30d    /home    ext4    defaults    0    2
#Entry for /dev/sda7 :
UUID=417a922d-e910-48f2-853f-4ba9849edeb5    none    swap    sw    0    0


--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 214.727577209 = 230.561980416  boot/grub/grub.cfg                             1
 207.344047546 = 222.633975808  boot/grub/i386-pc/core.img                     1
 203.196395874 = 218.180468736  boot/vmlinuz-3.8.0-19-generic                  1
 213.403427124 = 229.140185088  boot/vmlinuz-3.8.0-21-generic                  2
 214.145614624 = 229.937102848  boot/vmlinuz-3.8.0-22-generic                  2
 202.262802124 = 217.178030080  boot/vmlinuz-3.8.0-23-generic                  2
 211.473739624 = 227.068198912  boot/vmlinuz-3.8.0-25-generic                  1
 211.309677124 = 226.892038144  boot/vmlinuz-3.8.0-26-generic                  1
 208.485462189 = 223.859560448  boot/vmlinuz-3.8.0-27-generic                  1
 214.161247253 = 229.953888256  boot/vmlinuz-3.8.0-30-generic                  2
 214.161247253 = 229.953888256  vmlinuz                                        2
 208.485462189 = 223.859560448  vmlinuz.old                                    1
 206.572490692 = 221.805522944  boot/initrd.img-3.8.0-19-generic               1
 215.017807007 = 230.873612288  boot/initrd.img-3.8.0-21-generic               2
 215.392803192 = 231.276261376  boot/initrd.img-3.8.0-22-generic               2
 207.572494507 = 222.879268864  boot/initrd.img-3.8.0-23-generic               2
 202.214843750 = 217.126535168  boot/initrd.img-3.8.0-25-generic               4
 211.978744507 = 227.610443776  boot/initrd.img-3.8.0-26-generic               1
 210.228805542 = 225.731461120  boot/initrd.img-3.8.0-27-generic               2
 210.228805542 = 225.731461120  initrd.img.old                                 2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  69 7a 65 64 2e 71 74 72  22 0a 0a 5b 53 6f 66 74  |ized.qtr"..[Soft|
00000010  77 61 72 65 5c 5c 4d 69  63 72 6f 73 6f 66 74 5c  |ware\\Microsoft\|
00000020  5c 57 69 6e 64 6f 77 73  5c 5c 43 75 72 72 65 6e  |\Windows\\Curren|
00000030  74 56 65 72 73 69 6f 6e  5c 5c 49 6e 73 74 61 6c  |tVersion\\Instal|
00000040  6c 65 72 5c 5c 55 73 65  72 44 61 74 61 5c 5c 53  |ler\\UserData\\S|
00000050  2d 31 2d 35 2d 31 38 5c  5c 43 6f 6d 70 6f 6e 65  |-1-5-18\\Compone|
00000060  6e 74 73 5c 5c 32 32 45  43 35 39 31 31 37 30 34  |nts\\22EC5911704|
00000070  35 43 44 44 34 30 43 46  31 38 43 33 42 39 42 31  |5CDD40CF18C3B9B1|
00000080  41 31 45 45 38 5d 20 31  33 36 34 30 37 33 37 34  |A1EE8] 136407374|
00000090  35 0a 22 63 31 63 34 66  30 31 37 38 31 63 63 39  |5."c1c4f01781cc9|
000000a0  34 63 34 63 38 66 62 31  35 34 32 63 30 39 38 31  |4c4c8fb1542c0981|
000000b0  61 32 61 22 3d 22 30 32  3a 5c 5c 53 4f 46 54 57  |a2a"="02:\\SOFTW|
000000c0  41 52 45 5c 5c 4d 69 63  72 6f 73 6f 66 74 5c 5c  |ARE\\Microsoft\\|
000000d0  57 69 6e 64 6f 77 73 5c  5c 43 75 72 72 65 6e 74  |Windows\\Current|
000000e0  56 65 72 73 69 6f 6e 5c  5c 53 69 64 65 42 79 53  |Version\\SideByS|
000000f0  69 64 65 5c 5c 49 6e 73  74 61 6c 6c 61 74 69 6f  |ide\\Installatio|
00000100  6e 73 5c 5c 78 38 36 5f  70 6f 6c 69 63 79 2e 38  |ns\\x86_policy.8|
00000110  2e 30 2e 4d 69 63 72 6f  73 6f 66 74 2e 56 43 38  |.0.Microsoft.VC8|
00000120  30 2e 41 54 4c 5f 31 66  63 38 62 33 62 39 61 31  |0.ATL_1fc8b3b9a1|
00000130  65 31 38 65 33 62 5f 38  2e 30 2e 35 30 37 32 37  |e18e3b_8.0.50727|
00000140  2e 34 30 32 38 5f 78 2d  77 77 5f 38 62 33 37 32  |.4028_x-ww_8b372|
00000150  33 34 63 5c 5c 64 6f 77  6e 6c 65 76 65 6c 5f 6d  |34c\\downlevel_m|
00000160  61 6e 69 66 65 73 74 2e  38 2e 30 2e 35 30 37 32  |anifest.8.0.5072|
00000170  37 2e 34 30 32 38 5c 5c  22 0a 0a 5b 53 6f 66 74  |7.4028\\"..[Soft|
00000180  77 61 72 65 5c 5c 4d 69  63 72 6f 73 6f 66 74 5c  |ware\\Microsoft\|
00000190  5c 57 69 6e 64 6f 77 73  5c 5c 43 75 72 72 65 6e  |\Windows\\Curren|
000001a0  74 56 65 72 73 69 6f 6e  5c 5c 49 6e 73 74 61 6c  |tVersion\\Instal|
000001b0  6c 65 72 5c 5c 55 73 65  72 44 61 74 61 5c 00 fe  |ler\\UserData\..|
000001c0  ff ff 83 fe ff ff 00 18  e0 01 00 08 e0 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 00 20  c0 02 00 08 60 09 00 00  |....... ....`...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-12-07__19h19 ===================
boot-repair version : 3.199~ppa27~raring
boot-sav version : 3.199~ppa27~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa27~raring
boot-repair is executed in installed-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=33f9883d-fede-43bc-90d7-af29c7a1f6fe ro

=================== os-prober:
/dev/sda8:L'OS actuellement utilisé - Ubuntu 13.04 CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Windows 7 (loader):Windows1:chain
/dev/sda5:Linux Mint 13 Maya (13):LinuxMint:linux

=================== blkid:
/dev/sda1: LABEL="SYSTEM_DRV" UUID="52B084CCB084B7CD" TYPE="ntfs"
/dev/sda2: LABEL="MS-DOS" UUID="A5F7-8321" TYPE="vfat"
/dev/sda3: LABEL="Windows7_OS" UUID="B6E88D0CE88CCC55" TYPE="ntfs"
/dev/sda5: LABEL="Mint_OS" UUID="cd48855a-ae7e-45a3-be38-d712a5fadd89" TYPE="ext4"
/dev/sda6: LABEL="Ubuntu_Home" UUID="3b44bdda-dbc7-405a-b4c2-d314939ec30d" TYPE="ext4"
/dev/sda7: UUID="417a922d-e910-48f2-853f-4ba9849edeb5" TYPE="swap"
/dev/sda8: LABEL="Raring_OS" UUID="33f9883d-fede-43bc-90d7-af29c7a1f6fe" TYPE="ext4"
/dev/sr0: LABEL="CDROM" TYPE="iso9660"
/dev/zram0: UUID="fbb3d4ac-bf3e-45af-87c3-9ae69a36f589" TYPE="swap"
/dev/zram1: UUID="36515f64-81f5-4cc6-b152-f5e5ee377ff7" TYPE="swap"
/dev/zram2: UUID="d51a8500-f8e7-4f49-8887-984d03661af6" TYPE="swap"
/dev/zram3: UUID="2451ab5b-14c1-49e4-8096-6ae3423edc20" TYPE="swap"


1 disks with OS, 4 OS : 2 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Avertissement : la partition étendue ne débute pas sur une frontière de
cylindres. DOS et Linux interpréteront les contenus différemment.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 mai  5  2013 grub.d
drwxr-xr-x  4 root root      4096 mai  5  2013 grub.d.bak
total 68
-rwxr-xr-x 1 root root  7541 avr  9  2013 00_header
-rwxr-xr-x 1 root root  5974 avr  9  2013 05_debian_theme
-rwxr-xr-x 1 root root 11381 avr  9  2013 10_linux
-rwxr-xr-x 1 root root 10258 avr  9  2013 20_linux_xen
-rwxr-xr-x 1 root root 10976 avr  9  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 avr  9  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 avr  9  2013 40_custom
-rwxr-xr-x 1 root root   216 avr  9  2013 41_custom
-rw-r--r-- 1 root root   483 avr  9  2013 README




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




=================== sda5/etc/grub.d/ :
drwxr-xr-x 4 root root     4096 nov 27 21:31 grub.d
total 96
-rwxr-xr-x 1 root root 6743 jan 22  2013 00_header
-rwxr-xr-x 1 root root 5522 avr 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 1183 oct 23  2011 10_mint_theme
-rwxr-xr-x 1 root root  331 mai  5  2013 11_linux_proxy
-rwxr-xr-x 1 root root  666 mai  5  2013 12_os-prober_proxy
-rwxr-xr-x 1 root root  458 mai  5  2013 13_linux_proxy
-rwxr-xr-x 1 root root  567 mai  5  2013 14_os-prober_proxy
-rwxr-xr-x 1 root root  359 mai  5  2013 15_memtest86+_proxy
-rwxr-xr-x 1 root root 7780 jan 22  2013 16_linux.dpkg-dist
-rwxr-xr-x 1 root root 6693 jan 18  2012 18_lupin
-rwxr-xr-x 1 root root 6335 avr 17  2012 19_linux_xen
-rwxr-xr-x 1 root root  265 mai  5  2013 20_memtest86+_proxy
-rwxr-xr-x 1 root root  515 mai  5  2013 21_os-prober_proxy
-rwxr-xr-x 1 root root 1388 jan 22  2013 22_uefi-firmware
-rwxr-xr-x 1 root root  214 avr 17  2012 23_custom
-rwxr-xr-x 1 root root   95 avr 17  2012 24_custom
drwxr-xr-x 2 root root 4096 mai  5  2013 bin
drwxr-xr-x 2 root root 4096 mai  5  2013 proxifiedScripts
-rw-r--r-- 1 root root  483 avr 17  2012 README




=================== sda5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="yellow/black"
export GRUB_MENU_PICTURE="/boot/grub/GRUB-Wallpaper.jpg"


=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 00000000bafe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000bafe5000 0003E (v01 LENOVO TP-8H    00000124 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafe4000 0026A (v01 LENOVO TP-8H    00000124 PTL  00000002)
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda8    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/Windows7_OS.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    customized,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA HITACHI HTS72323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  535MB   535MB   primary   ntfs            boot
2      535MB   1600MB  1065MB  primary   fat32
3      1600MB  215GB   214GB   primary   ntfs
4      215GB   320GB   105GB   extended
8      215GB   231GB   16.1GB  logical   ext4
5      231GB   239GB   7517MB  logical   ext4
6      239GB   320GB   80.5GB  logical   ext4
7      320GB   320GB   524MB   logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA HITACHI HTS72323;
1:32.3kB:535MB:535MB:ntfs::boot;
2:535MB:1600MB:1065MB:fat32::;
3:1600MB:215GB:214GB:ntfs::;
4:215GB:320GB:105GB:::;
8:215GB:231GB:16.1GB:ext4::;
5:231GB:239GB:7517MB:ext4::;
6:239GB:320GB:80.5GB:ext4::;
7:320GB:320GB:524MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


                                                                          
Error: /dev/zram2: unrecognised disk label


                                                                          
Error: /dev/zram3: unrecognised disk label


=================== mount:
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda3 on /media/Windows7_OS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/carl/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=carl)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom vboxusb vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  c0 ee 0f 00 00 00 00 00  |................|
00000030  1c 63 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |.c..............|
00000040  f6 00 00 00 01 00 00 00  cd b7 84 b0 cc 84 b0 52  |...............R|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 08 27 00  |.X.MSWIN4.1...'.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 f0 0f 00  |........?.......|
00000020  00 c0 1f 00 ee 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 21 83 f7 a5 4e  4f 20 4e 41 4d 45 20 20  |..)!...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa 33 c9 8e d1 bc  |  FAT32   .3....|
00000060  f8 7b 8e c1 bd 78 00 c5  76 00 1e 56 16 55 bf 22  |.{...x..v..V.U."|
00000070  05 89 7e 00 89 4e 02 b1  0b fc f3 a4 8e d9 bd 00  |..~..N..........|
00000080  7c c6 45 fe 0f 8b 46 18  88 45 f9 38 4e 40 7d 25  ||.E...F..E.8N@}%|
00000090  8b c1 99 bb 00 07 e8 97  00 72 1a 83 eb 3a 66 a1  |.........r...:f.|
000000a0  1c 7c 66 3b 07 8a 57 fc  75 06 80 ca 02 88 56 02  |.|f;..W.u.....V.|
000000b0  80 c3 10 73 ed bf 02 00  83 7e 16 00 75 45 8b 46  |...s.....~..uE.F|
000000c0  1c 8b 56 1e b9 03 00 49  40 75 01 42 bb 00 7e e8  |..V....I@u.B..~.|
000000d0  5f 00 73 26 b0 f8 4f 74  1d 8b 46 32 33 d2 b9 03  |_.s&..Ot..F23...|
000000e0  00 3b c8 77 1e 8b 76 0e  3b ce 73 17 2b f1 03 46  |.;.w..v.;.s.+..F|
000000f0  1c 13 56 1e eb d1 73 0b  eb 27 83 7e 2a 00 77 03  |..V...s..'.~*.w.|
00000100  e9 fd 02 be 7e 7d ac 98  03 f0 ac 84 c0 74 17 3c  |....~}.......t.<|
00000110  ff 74 09 b4 0e bb 07 00  cd 10 eb ee be 81 7d eb  |.t............}.|
00000120  e5 be 7f 7d eb e0 98 cd  16 5e 1f 66 8f 04 cd 19  |...}.....^.f....|
00000130  41 56 66 6a 00 52 50 06  53 6a 01 6a 10 8b f4 60  |AVfj.RP.Sj.j...`|
00000140  80 7e 02 0e 75 04 b4 42  eb 1d 91 92 33 d2 f7 76  |.~..u..B....3..v|
00000150  18 91 f7 76 18 42 87 ca  f7 76 1a 8a f2 8a e8 c0  |...v.B...v......|
00000160  cc 02 0a cc b8 01 02 8a  56 40 cd 13 61 8d 64 10  |........V@..a.d.|
00000170  5e 72 0a 40 75 01 42 03  5e 0b 49 75 b4 c3 03 18  |^r.@u.B.^.Iu....|
00000180  01 27 0d 0a 49 6e 76 61  6c 69 64 20 73 79 73 74  |.'..Invalid syst|
00000190  65 6d 20 64 69 73 6b ff  0d 0a 44 69 73 6b 20 49  |em disk...Disk I|
000001a0  2f 4f 20 65 72 72 6f 72  ff 0d 0a 52 65 70 6c 61  |/O error...Repla|
000001b0  63 65 20 74 68 65 20 64  69 73 6b 2c 20 61 6e 64  |ce the disk, and|
000001c0  20 74 68 65 6e 20 70 72  65 73 73 20 61 6e 79 20  | then press any |
000001d0  6b 65 79 0d 0a 00 00 00  49 4f 20 20 20 20 20 20  |key.....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7e 01  |SYSMSDOS   SYS~.|
000001f0  00 57 49 4e 42 4f 4f 54  20 53 59 53 00 00 55 aa  |.WINBOOT SYS..U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 2f 00  |........?...../.|
00000020  00 00 00 00 80 00 80 00  f8 67 e3 18 00 00 00 00  |.........g......|
00000030  23 a0 0a 00 00 00 00 00  02 00 00 00 00 00 00 00  |#...............|
00000040  f6 00 00 00 01 00 00 00  55 cc 8c e8 0c 8d e8 b6  |........U.......|
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
/dev/sda8      ext4       15G  9.4G  4.6G  68% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     790M  912K  789M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G   96K  3.9G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sda3      fuseblk   200G  125G   75G  63% /media/Windows7_OS
/dev/sda6      ext4       74G   68G  2.4G  97% /home
/dev/sda1      fuseblk   510M  361M  150M  71% /mnt/boot-sav/sda1
/dev/sda2      vfat     1014M  269M  746M  27% /mnt/boot-sav/sda2
/dev/sda5      ext4      6.8G  4.6G  1.9G  71% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc88c59eb

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1044224      522081    7  HPFS/NTFS/exFAT
/dev/sda2         1044480     3125247     1040384    b  W95 FAT32
/dev/sda3         3125248   420681727   208778240    7  HPFS/NTFS/exFAT
/dev/sda4       420681728   625142447   102230360    5  Extended
/dev/sda5       452145152   466827263     7341056   83  Linux
/dev/sda6       466829312   624115711    78643200   83  Linux
/dev/sda7       624117760   625141759      512000   82  Linux swap / Solaris
/dev/sda8       420683776   452143103    15729664   83  Linux

Partition table entries are not in disk order


Partition outside the disk détecté.

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda8 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
démontage : /media/Windows7_OS : périphérique occupé.
(Dans certains cas, des infos sur les processus l'utilisant
sont récupérables par lsof(8) ou fuser(1))
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.

Reinstall the GRUB of sda8 into the MBR of sda
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
FlexNet détecté. Veuillez sauvegarder vos données avant cette opération. Voulez-vous continuer ? no

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda3
Found Linux Mint 13 Maya (13) on /dev/sda5
Unhide GRUB boot menu in sda8/boot/grub/grub.cfg

Une erreur est survenue pendant la réparation.

Vous pouvez maintenant redémarrer votre ordinateur.


```   


I will try to restore GRUB first.  But notice that MS-DOS ( 7.1 ) is listed as Windows 98 OS.
Although that when I boot from a Super GRUB Disk and select "Detect any OS", it's listed as MS-DOS:

[https://dl.dropboxusercontent.com/u/67605655/IMG188.jpg](https://dl.dropboxusercontent.com/u/67605655/IMG188.jpg)



Thanks!

---

### Post by heir4c on 2013-12-07
To repair grub (point 6) or the MBR look at this site. I hope you find a lot of helpful information here:
[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

---

### Post by heir4c on 2013-12-07
And maybe you can edit a boot entry in the grub files. I don't now what you must write into and how you must do that, but I hope you find somewhere on internet the answer. Or maybe there is someone of the members who know what to do.
Success!!!

Greetings
Gerolf

---

### Post by jeanjd63 on 2013-12-08
Hello,
You can edit file 40_custom :
**sudo  gedit  /etc/grub.d/40_custom**
and **add** this :
> [COLOR=#000000][FONT=Ubuntu Mono]menuentry "Msdos 7 (on /dev/sda2)" {[/FONT][/COLOR] 
   set root='(hd0,msdos2)'
    chainloader +1
}


You save this, do a :
**sudo  update-grub**
then try this entry at next boot.

Bye

---

### Post by GameX2 on 2013-12-08
It worked! :D

Thanks!

---

