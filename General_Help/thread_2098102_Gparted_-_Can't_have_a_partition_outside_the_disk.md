---
title: "Gparted - Can't have a partition outside the disk"
date: 2012-12-25
forum: General Help
---

### Post by GameX2 on 2012-12-25
Hi!


I just received a external hard drive today, so I could copy my local backups on this external drive.  I then deleted my backup NTFS partition from Windows XP, and guess what?  Windows deleted my whole logical partition which contained Ubuntu_OS and Ubuntu_Home (EXT4). <<

So I've heard about the software TestDisk; using it, I manage to restore the lost Linux partitions.  I've later tried to restore the MBR of Windows 7, but the restoration wasn't working.  I get the " grub > rescue " message at boot, and I'm only able to boot an operating system from my "Super GRUB 2 Disk".

I booted from a GParted Live CD, and my partition table is illisible. :(  I get the message " *Can't* have a *partition outside* the disk ".

Using: ```
fdisk -l
```; nothing appear in the Terminal.

I know this is not a rare problem, but I'm affraid to do any modification to the disk or use BootRepair - In case that wipe my hard disk completely..

What should I do first?

Thank you very much for the help! :)

---

### Post by drdos2006 on 2012-12-25
Should have done a backup first and then deleted your partition.
Can you use XP to restore the partition ?

regards

---

### Post by GameX2 on 2012-12-25
All the partitions are restored; I used the software "TestDrive" and manage to recover my lost Ubuntu partitions.

The problem is that I can't manage my partitions with GParted, since I get the error message " *Can't* have a *partition outside* the disk ".
To boot into any operating system, I have to insert the "Super GRUB disk", since GRUB got deleted, and I do not wish to restore it yet, while my partition table does not appear in GParted.

I can, however, boot into Windows (Using the GRUB CD), and the partition utility does detect the partition table.

How can I fix the GParted "*Can't* have a *partition outside* the disk " error?

Thanks!

---

### Post by drdos2006 on 2012-12-25
Do a Google on this.

"ubuntu Can't have a partition outside the disk"

Quite a few results turn up, one of those should be helpful.

regards

---

### Post by coffeecat on 2012-12-25
These issues should all be fixable, but first a few comments.

> **GameX2 said:**
> I then deleted my backup NTFS partition from Windows XP, and guess what?  Windows deleted my whole logical partition which contained Ubuntu_OS and Ubuntu_Home (EXT4). <<

An important lesson learnt the hard way. Windows gets very confused when you have Linux filesystems on logical partitions. The Windows installer can also do something very similar if you install Windows in the presence of Linux logical partitions. Use Disk Manager in Windows with great care in this situation.

> **GameX2 said:**
> 
So I've heard about the software TestDisk; using it, I manage to restore the lost Linux partitions.

When restoring a deleted extended partition, testdisk sometimes miscomputes the end of the extended partition to beyond the last physical sector of the disk. This is probably why you are getting the "Can't have a partition outside the disk" message.

> **GameX2 said:**
>   I've later tried to restore the MBR of Windows 7, but the restoration wasn't working.

Hang on - are you running Windows XP or Windows 7 or both?

> **GameX2 said:**
> I get the " grub > rescue " message at boot, and I'm only able to boot an operating system from my "Super GRUB 2 Disk".

With your Linux root partition deleted there is orphan grub code in the mbr which cannot find the partition where the rest of the grub code should be.

We need an overview of your system to see what needs to be done - the boot info script can provide this. Boot up the live Ubuntu CD, choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by GameX2 on 2012-12-25
Thank you very much for the reply and clear explanation; I ran the script from a Ubuntu Live CD, and here's the content of RESULTS.TXT :

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos8)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:      
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /boot.ini /bootmgr /Boot/BCD
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 30659056 of /dev/sdb1 for
                       its second stage. SYSLINUX is installed in the
                       G:\syslinux directory. The integrity check of the ADV
                       area failed. No errors found in the Boot Parameter
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /efi/BOOT/grubx64.efi
                       /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048     7,268,351     4,194,304   7 NTFS / exFAT / HPFS
/dev/sda3           7,270,400   411,164,656   403,894,257   7 NTFS / exFAT / HPFS
/dev/sda4         411,164,712   625,153,409   213,988,698   f W95 Extended (LBA)
/dev/sda5         411,166,720   442,623,984    31,457,265   7 NTFS / exFAT / HPFS
/dev/sda6         442,626,048   483,315,711    40,689,664  83 Linux
/dev/sda7         483,317,760   581,621,759    98,304,000  83 Linux
/dev/sda8         581,625,856   582,649,839     1,023,984  82 Linux swap / Solaris
/dev/sda9         582,651,904   625,141,752    42,489,849   7 NTFS / exFAT / HPFS

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.4 GB, 16358768640 bytes
256 heads, 18 sectors/track, 6933 cylinders, total 31950720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          3,536    31,950,719    31,947,184   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs  
/dev/sda1        52B084CCB084B7CD                       ntfs       SYSTEM_DRV
/dev/sda3        B6E88D0CE88CCC55                       ntfs       Windows7_OS
/dev/sda5        C4CC4184CC4171AA                       ntfs       WindowsXP_OS
/dev/sda6        701c70f1-fb59-453a-ab30-81bce57b7f74   ext4       Ubuntu_OS
/dev/sda7        3b44bdda-dbc7-405a-b4c2-d314939ec30d   ext4       Ubuntu_Home
/dev/sda8        98509b97-f05e-4d1f-bcfe-ad38096f3993   swap      
/dev/sda9        38870F1D28D5E28F                       ntfs       Backups
/dev/sdb1        7ECA-7237                              vfat       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

================================ sda3/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professionnel x86 Edition" /fastdetect
multi(0)disk(0)rdisk(0)partition(3)\WINNT="Microsoft Windows 2K Professionnel" /fastdetect
--------------------------------------------------------------------------------

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
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
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=701c70f1-fb59-453a-ab30-81bce57b7f74 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
    echo    'Loading Linux 3.2.0-35-generic ...'
    linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=701c70f1-fb59-453a-ab30-81bce57b7f74 ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-35-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=701c70f1-fb59-453a-ab30-81bce57b7f74 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 701c70f1-fb59-453a-ab30-81bce57b7f74
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=701c70f1-fb59-453a-ab30-81bce57b7f74 ro recovery nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 52B084CCB084B7CD
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root B6E88D0CE88CCC55
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda10 during installation
UUID=701c70f1-fb59-453a-ab30-81bce57b7f74  /            ext4  errors=remount-ro        0  1  
# /home was on /dev/sda11 during installation
UUID=3b44bdda-dbc7-405a-b4c2-d314939ec30d  /home        ext4  defaults                 0  2  
# swap was on /dev/sda8 during installation
UUID=98509b97-f05e-4d1f-bcfe-ad38096f3993  none         swap  sw                       0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000  0  0  
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-35-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-35-generic                  1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  c9 75 3f e9 57 87 3e 9f  de 3f bd 83 7a 8e bd 5b  |.u?.W.>..?..z..[|
00000010  f5 75 3f c3 d9 86 3e 82  fa 23 bd df 51 8d bd 84  |.u?...>..#..Q...|
00000020  1d 76 3f eb 5d 86 3e 64  f0 07 bd 14 6c 8c bd 94  |.v?.].>d....l...|
00000030  41 76 3f cd e7 85 3e 8b  ec d7 bc c8 d5 8b bd d9  |Av?...>.........|
00000040  60 76 3f af 7a 85 3e fb  82 a0 bc 0d 9a 8b bd c2  |`v?.z.>.........|
00000050  7a 76 3f a1 19 85 3e 5e  17 54 bc 00 c2 8b bd e2  |zv?...>^.T......|
00000060  8e 76 3f 79 c7 84 3e c8  a5 d3 bb 8a 54 8c bd f0  |.v?y..>.....T...|
00000070  9c 76 3f c3 86 84 3e 41  4b 3c b9 1e 56 8d bd c2  |.v?...>AK<..V...|
00000080  a4 76 3f b8 59 84 3e 36  ca bf 3b 82 c8 8e bd 4f  |.v?.Y.>6..;....O|
00000090  a6 76 3f 35 42 84 3e dd  19 3e 3c ab aa 90 bd a8  |.v?5B.>..><.....|
000000a0  a1 76 3f b4 41 84 3e ec  95 8b 3c a2 f8 92 bd fa  |.v?.A.>...<.....|
000000b0  96 76 3f 47 59 84 3e 0a  58 b5 3c 81 ab 95 bd 87  |.v?GY.>.X.<.....|
000000c0  86 76 3f 97 89 84 3e 6b  29 dc 3c 71 b9 98 bd a4  |.v?...>k).<q....|
000000d0  70 76 3f df d2 84 3e df  eb ff 3c cc 15 9c bd b6  |pv?...>...<.....|
000000e0  55 76 3f f2 34 85 3e 4a  46 10 3d 42 b1 9f bd 34  |Uv?.4.>JF.=B...4|
000000f0  36 76 3f 01 8e f9 03 40  c5 f2 3d 40 a6 08 98 40  |6v?....@..=@...@|
00000100  77 01 00 00 00 00 00 00  80 3f 00 00 00 40 00 00  |w........?...@..|
00000110  40 40 00 00 80 40 00 00  a0 40 00 00 c0 40 00 00  |@@...@...@...@..|
00000120  e0 40 00 00 00 41 00 00  10 41 00 00 20 41 00 00  |.@...A...A.. A..|
00000130  30 41 00 00 50 41 00 00  60 41 00 00 70 41 00 00  |0A..PA..`A..pA..|
00000140  80 41 00 00 88 41 00 00  90 41 00 00 98 41 00 00  |.A...A...A...A..|
00000150  a0 41 00 00 a8 41 00 00  b0 41 00 00 b8 41 00 00  |.A...A...A...A..|
00000160  c0 41 00 00 c8 41 00 00  d0 41 00 00 d8 41 00 00  |.A...A...A...A..|
00000170  e0 41 00 00 e8 41 00 00  f0 41 00 00 f8 41 00 00  |.A...A...A...A..|
00000180  00 42 00 00 04 42 00 00  08 42 00 00 0c 42 00 00  |.B...B...B...B..|
00000190  10 42 00 00 14 42 00 00  18 42 00 00 1c 42 00 00  |.B...B...B...B..|
000001a0  20 42 00 00 24 42 00 00  28 42 00 00 2c 42 00 00  | B..$B..(B..,B..|
000001b0  30 42 00 00 34 42 00 00  38 42 00 00 3c 42 00 fe  |0B..4B..8B..<B..|
000001c0  ff ff 07 fe ff ff d8 07  00 00 f1 ff df 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 87 0f  e0 01 51 e0 6c 02 00 00  |..........Q.l...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```> Hang on - are you running Windows XP or Windows 7 or both?
Sorry for the confusion. Actually, I have many OS installed:

Windows 7 x64: files are stored there, I usually run my Adobe programs - Windows only - there;
Windows XP x86: I use it for gaming. There are games that are only 32bits compatible.
Ubuntu 12.04 LTS;
Windows 2000: Installed it for the challenge (Weird, I know). I was wondering if the system would even install, and after patching the CD, it did. Just cannot find working generic drivers. It's the small 2GB partition.

As for SYSTEM_DRV partition, it's a recovery partition, it came with the laptop.


Thanks again - merry Christmas.

---

### Post by coffeecat on 2012-12-25
It's very late here and I'm going to log off soon. I haven't looked through the boot script output in detail so there may be other things to take into consideration, but I'll point you to two problems that I can see.

Number 1:

> **GameX2 said:**
> ```

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR="Red"]625142448[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048     7,268,351     4,194,304   7 NTFS / exFAT / HPFS
/dev/sda3           7,270,400   411,164,656   403,894,257   7 NTFS / exFAT / HPFS
/dev/sda4         411,164,712   [COLOR="Red"]625,153,409[/COLOR]   213,988,698   f W95 Extended (LBA)
/dev/sda5         411,166,720   442,623,984    31,457,265   7 NTFS / exFAT / HPFS
/dev/sda6         442,626,048   483,315,711    40,689,664  83 Linux
/dev/sda7         483,317,760   581,621,759    98,304,000  83 Linux
/dev/sda8         581,625,856   582,649,839     1,023,984  82 Linux swap / Solaris
/dev/sda9         582,651,904   625,141,752    42,489,849   7 NTFS / exFAT / HPFS

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

The problem bits I've highlighted in red and are what I suggested earlier. In repairing your partition table, testdisk has erroneously put the last sector of your sda4 extended partition beyond the last sector of the disk. Fortunately, easily repaired. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

You can download and run fixparts in the live CD session. It will repair this anomaly easily.
 
The second problem:


> **GameX2 said:**
> :
```

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

```


But...

> **GameX2 said:**
> :
```

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

```


Your Linux root partition used to be sda8 before Windows did whatever it did to your partition table. sda8 is now a swap partition and grub can't find the original partition - which I guess is now sda6 after the testdisk repair. I suggest you have one of two options, either to re-install the Windows MBR or to re-install grub pointing to sda6.

If you wish to re-install grub from the live CD, this link should help:

[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

But I'll look at the whole of your boot script output in the morning (UK time) to see if there is anything else you need to deal with.

---

### Post by GameX2 on 2012-12-25
I managed to fix my partition table using fixparts; it is now visible by GParted!

In GParted, I can read errors on my NTFS partitions:

[http://img211.imageshack.us/img211/1338/capturedu20121225225425.png](http://img211.imageshack.us/img211/1338/capturedu20121225225425.png)

It's basically saying "The package ntfsprogs might be missing", which would explain why the NTFS partitions are illisble (but detected), so I installed it:
```
sudo apt-get install ntfsprogs
```I later found something else in the GParted message - which is now not shown in the screenshot.  It pretty much said "It is too dangerous to continue normally".  Sorry, that's not really helpful - the message is not displayed anymore.  Which probably isn't a bad thing.

I'm not sure where I should go next..  I'm not excellent at fixing broken partitions, and I would not go any further by myself - otherwise, I might screw things up!
Would simply using Boot-Repair fix this, or make things worse?

Note that although I have no more bootloader installed, I can still access all my partitions using my "Super GRUB 2 Disk" and start an OS from here - so nothing is damaged, luckily.

Thank you very much!

---

### Post by oldfred on 2012-12-25
On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)

Do not install ntfsprogs on newer systems as then it installs the old version and uninstalls the new ntfs-3g which is what you really want.

You cannot do much to fix NTFS partitions from Linux. This only does minor fixes and turns on chkdsk flag.

 sudo ntfsfix /dev/sda2

You need to run chkdsk from Windows Repair Console or a Windows repairCD.
But you have to see what "drive" or partition Windows sees sda2 as and run it 

       chkdsk c: /r
    But change c: to your correct drive.

---

### Post by coffeecat on 2012-12-26
I've had a chance to look through your boot info script output in more detail now. A couple of comments:

> **GameX2 said:**
> It's basically saying "The package ntfsprogs might be missing", which would explain why the NTFS partitions are illisble (but detected), so I installed it:
```
sudo apt-get install ntfsprogs
```

Uninstall ntfsprogs. As oldfred says, in Ubuntu 11.10 and later the functionality previously provided by ntfsprogs was found in the ntfs-3g driver. Worse - in 11.10, if you installed ntfsprogs the package manager would uninstall ntfs-3g meaning that you lost the ntfs-3g driver and the system fell back on the read-only kernel ntfs module. I can't remember what happened with 12.04 - this has been resolved in 12.10. I suggest that while you are uninstalling ntfsprogs you check whether you still have ntfs-3g installed and, if it has gone missing, re-install it.

Also +1 to what oldfred said about chkdsk. Whatever ntfsfix does, you would need to use chkdsk. In your situation I wouldn't even bother running ntfsfix, but go straight to chkdsk from the recovery console from a repair disk. Do you have access to a Windows 7 repair CD?

> **GameX2 said:**
> Would simply using Boot-Repair fix this, or make things worse?

Note that although I have no more bootloader installed, I can still access all my partitions using my "Super GRUB 2 Disk" and start an OS from here - so nothing is damaged, luckily.

Boot-repair won't fix your damaged Windows 7 partition is this is what you mean, but it could be used to re-install grub to the mbr of sda. However, since you are able to boot into Ubuntu 12.04 using the supergrub disk, there's an easier solution. Your Ubuntu 12.04 partition was sda8 before you had all these problems, but is now sda6, so all you have to do is to re-install grub from the running 12.04 installation.

Boot into Ubuntu 12.04, open a terminal, and:

```
sudo grub-install /dev/sda
sudo update-grub
``` 

That's it. When you reboot, you should see your grub menu. Whether it has any Windows entries and how many remains to be seen, because the grub menu will have been regenerated with the second command, and you seem to have filesystem damage in sda2 as well as sda3.

---

### Post by GameX2 on 2012-12-26
Thanks!
That solved the problem! :D

I first uninstalled ntfsprogs, and ntfs-3g wasn't uninstalled, after all.
Then I did a CHKDSK from Windows 7 - I can still boot any partition, from Super GRUB Disk.  I booted in Windows 7, and planned a CHKDSK at the next reboot.  Rebooted, did the CheckDisk, and that fixed the problem.

I then reinstalled GRUB the way you've recommended me to, really easy.  The problem I had was that Windows 2000 would later fail to boot.  NTOSKRNL error.  The boot.ini file was incorrect.  I restored a working Windows 2000 image (Without the Update Rollup 1 installed, the OS would corrupt itself and getting BSOD at startup.  Had to do many drivers testing, so I already had a working Windows 2000 image)  and had to mess around with the boot settings.  That took a while (4 operating systems...  That's what annoying with FOUR operating system, that.. a lot.), but I finally got it!

What I have to do now is change the few Windows 7 links I did; I linked the "My Pictures" and "My Music" folders on Windows 7 (previously SDA2), but it's now SDA3, so I have to update a few links.  That shouldn't take too long.

Thanks a bunch!  Solved! :D

---

