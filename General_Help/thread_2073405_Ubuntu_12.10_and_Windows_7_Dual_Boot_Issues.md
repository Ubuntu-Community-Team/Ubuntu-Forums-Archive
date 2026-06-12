---
title: "Ubuntu 12.10 and Windows 7 Dual Boot Issues"
date: 2012-10-19
forum: General Help
---

### Post by RedeyeJedi on 2012-10-19
I've been trying to get Ubuntu 12.10 64bit to dual boot with Windows 7 all day. They have both worked at one point but never got dual boot to work. Ubuntu is installed and working fine now, however Windows is not showing up in GRUB.

I am setting up Ubuntu on a 64gb ssd and Windows on an 80gb HDD. I installed Windows first and got everything set up and working. I then installed ubuntu from USB onto my ssd, thinking back there was a small windows partition of about 100mb that was labelled windows recovery but acting like one of my customers I deleted it without thinking.

So basically I have two operating systems on two separate drives that have both worked but GRUB can only see one.

When i run "sudo os-prober" there is nothing returned so I'm guessing it cant see windows.

Here is the output of fdisk -l (from reading other posts similar to mine I figured this would be needed so I'll save some time)
```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91a23594

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39999487    19998720   83  Linux
/dev/sda2        40001534   125044735    42521601    5  Extended
/dev/sda5        40001536   125044735    42521600   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   104859647    52428800    7  HPFS/NTFS/exFAT
/dev/sdb2       104861694   112855039     3996673    5  Extended
/dev/sdb5       104861696   112855039     3996672   82  Linux swap / Solaris
```I have tried "boot repair" using the recommended repair option and this is the link it's given, incase that is any help [http://paste.ubuntu.com/1289971/](http://paste.ubuntu.com/1289971/)

Strangely, if I go into advanced options on boot repair, under the "GRUB location" tab I can select Windows as the OS to boot by default. I have not tried this though because I do not want to end up stuck in Windows 7, would much rather have only Ubuntu working than only Windows.

I have been searching for the answer for the last few hours but can't seem to find the answer I need. I have come to the conclusion I may just need to start again and be careful with my partitioning this time but I am hopeful someone here will be able to help.

If you need any more info from me just ask, I'm not afraid of using the terminal.

Thanks in advance for your help.

Edit: forgot to add, I ran "bootinfoscript" that was suggested in another forum post, thought it might be helpful for anyone helping, here's the output

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    39,999,487    39,997,440  83 Linux
/dev/sda2          40,001,534   125,044,735    85,043,202   5 Extended
/dev/sda5          40,001,536   125,044,735    85,043,200  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   104,859,647   104,857,600   7 NTFS / exFAT / HPFS
/dev/sdb2         104,861,694   112,855,039     7,993,346   5 Extended
/dev/sdb5         104,861,696   112,855,039     7,993,344  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        540096b7-5f8f-40e5-80dc-373d0c7a1e1d   ext4       
/dev/sda5        1e8a4609-812b-4911-99bb-49d09c5e10e7   ext4       
/dev/sdb1        4EB2A77BB2A765E5                       ntfs       
/dev/sdb5        7dde6f6d-8eeb-40cc-86bc-b6fc7f04ff3f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)
/dev/sdb1        /mnt/boot-sav/sdb1       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  540096b7-5f8f-40e5-80dc-373d0c7a1e1d
else
  search --no-floppy --fs-uuid --set=root 540096b7-5f8f-40e5-80dc-373d0c7a1e1d
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
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-540096b7-5f8f-40e5-80dc-373d0c7a1e1d' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  540096b7-5f8f-40e5-80dc-373d0c7a1e1d
    else
      search --no-floppy --fs-uuid --set=root 540096b7-5f8f-40e5-80dc-373d0c7a1e1d
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=540096b7-5f8f-40e5-80dc-373d0c7a1e1d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-540096b7-5f8f-40e5-80dc-373d0c7a1e1d' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-540096b7-5f8f-40e5-80dc-373d0c7a1e1d' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  540096b7-5f8f-40e5-80dc-373d0c7a1e1d
        else
          search --no-floppy --fs-uuid --set=root 540096b7-5f8f-40e5-80dc-373d0c7a1e1d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=540096b7-5f8f-40e5-80dc-373d0c7a1e1d ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-540096b7-5f8f-40e5-80dc-373d0c7a1e1d' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  540096b7-5f8f-40e5-80dc-373d0c7a1e1d
        else
          search --no-floppy --fs-uuid --set=root 540096b7-5f8f-40e5-80dc-373d0c7a1e1d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=540096b7-5f8f-40e5-80dc-373d0c7a1e1d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
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
UUID=540096b7-5f8f-40e5-80dc-373d0c7a1e1d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=1e8a4609-812b-4911-99bb-49d09c5e10e7 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=7dde6f6d-8eeb-40cc-86bc-b6fc7f04ff3f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.126091003 = 15.167774720   boot/grub/grub.cfg                             1
   1.272972107 = 1.366843392    boot/initrd.img-3.5.0-17-generic               1
   4.187011719 = 4.495769600    boot/vmlinuz-3.5.0-17-generic                  1
   1.272972107 = 1.366843392    initrd.img                                     1
   1.272972107 = 1.366843392    initrd.img.old                                 1
   4.187011719 = 4.495769600    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  b2 24 71 39 b3 21 af 15  16 09 20 0c 5c 33 a1 10  |.$q9.!.... .\3..|
00000010  92 1e fc 02 7a 06 44 07  65 0b 53 0e c0 02 ce 84  |....z.D.e.S.....|
00000020  f1 06 42 1f f5 17 4f 19  32 2f ad 08 f4 23 d3 01  |..B...O.2/...#..|
00000030  c3 18 0d 10 5e 11 34 0e  b9 11 cb 06 7d 01 c9 23  |....^.4.....}..#|
00000040  5c 08 da 3d 46 0d df 33  f9 05 ca 1e f4 3b d9 00  |\..=F..3.....;..|
00000050  d3 11 a6 0b f3 12 1f 0d  f0 16 03 04 14 06 d7 18  |................|
00000060  5d 07 1e 2b 82 06 2a 04  87 00 8a 02 ef d8 d9 0e  |]..+..*.........|
00000070  d8 4b d3 15 65 3e 8a 03  c6 08 c2 02 31 1e 00 00  |.K..e>......1...|
00000080  0f 1c 90 13 b7 1a 3a 2b  23 10 a2 09 c8 03 5b 11  |......:+#.....[.|
00000090  70 01 4a 20 34 0f 6f 1e  3d 1e 70 05 d2 09 6e 2f  |p.J 4.o.=.p...n/|
000000a0  7c 40 36 25 d1 18 7d 47  18 1c 9c 03 4f 19 a7 0e  ||@6%..}G....O...|
000000b0  15 05 25 17 98 05 53 08  57 00 e0 04 77 29 2a 45  |..%...S.W...w)*E|
000000c0  bb 22 ea 00 52 03 75 1f  b4 02 b3 0a 25 06 09 52  |."..R.u.....%..R|
000000d0  1e 20 6d 2d 27 02 f0 00  e1 0b 98 07 a9 12 22 04  |. m-'.........".|
000000e0  8f 0d 53 13 d1 06 cb 04  0a 1f 22 10 e8 26 ec 0f  |..S......."..&..|
000000f0  5b 10 7c 16 fe 12 7e 01  20 24 e9 0d 00 00 c8 20  |[.|...~. $..... |
00000100  8d 0a 32 37 89 17 85 0d  41 05 c3 03 63 02 16 61  |..27....A...c..a|
00000110  76 0c bc 10 30 13 21 43  5a 0a bd 19 73 0e 37 1e  |v...0.!CZ...s.7.|
00000120  e7 07 e0 07 cf 17 84 27  6e 19 c7 22 69 09 07 1f  |.......'n.."i...|
00000130  b9 0d e9 27 db 03 2b 16  4b 02 8e 2d 0b 6f 84 5c  |...'..+.K..-.o.\|
00000140  97 0b 83 18 ee 3c a5 05  13 14 ac 4f 3e 60 9e 16  |.....<.....O>`..|
00000150  58 0d 25 00 24 3c 75 18  9d 12 79 20 d6 04 eb 14  |X.%.$<u...y ....|
00000160  28 04 93 0b c7 05 8b 0f  8c 18 17 0f 07 06 6a 15  |(.............j.|
00000170  aa 14 34 07 de 18 48 8d  3e 13 5a 05 5e 1a e7 13  |..4...H.>.Z.^...|
00000180  f9 1a ef 0a ff 0e 04 02  50 25 7f 14 a6 00 56 02  |........P%....V.|
00000190  ba 01 4b 1f b1 12 37 0a  e7 1c 98 19 8d 06 e4 01  |..K...7.........|
000001a0  d9 01 85 04 01 04 38 24  38 1f dc 69 eb 08 98 02  |......8$8..i....|
000001b0  36 00 59 1f 8d 63 a2 0f  1d 12 c3 0b 18 09 00 fe  |6.Y..c..........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f8 79 00 00 00  |............y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2012-10-20
You are missing Windows boot files. Windows 7 normally installs to two partitions, one a 100MB boot/repair partition that is hidden in Windows. And on dual drive systems if BIOS is set to boot from other drive it installs its boot partition to the drive that BIOS boots and the main c: drive partition on the other drive.

If you have a Windows repairCD or USB you can repair the current install just by adding bootmgr & /boot/BCD. One user did not even run the Windows repairs but copied the bootmgr & BCD & manually edited the BCD to correct partition.

Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

If you do not have a Windows repairCD you can make one if you have access to a friend with the same 32 or 64 bit version. There is a link to download the repairCD but it costs $10.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by YannBuntu on 2012-10-23
**@oldfred:** you can add this to your links: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
( why promoting commercial links when there are free disks..)

---

### Post by RedeyeJedi on 2012-11-09
Sorry bout the late reply, completely forgot I asked about this.

That was a great answer, just what I was looking for, thanks.

In the end however I just decided to run only Ubuntu 12.10 from just my SSD and I have to say it's brilliantly fast. I've been using Ubuntu too long now to start going back to Windows anyway. 

Thanks Again :)

---

