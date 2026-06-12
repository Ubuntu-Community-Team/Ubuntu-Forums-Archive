---
title: "Recover GRUB2"
date: 2015-04-18
forum: General Help
---

### Post by Filip_Vavera on 2015-04-18
**My problem:**
I'm using Ubuntu 14.04 together with Windows 8.1 and Kali Linux without problems for one year. Ubuntu is on SSD disk under /dev/sda and Windows with Kali on HDD under /dev/sdb. In BIOS I've set UEFI boot with Ubuntu GRUB2. Few days before after selecting Ubuntu in GRUB2 only black screen with some text has shown for a moment and after that just black screen. Other system has started normally and when I start Ubuntu in other way it was working (recovery mode and after that option normal start). So I've been trying fix Ubuntu. I've install something (from official repositories but I didn't remember what was that) and everything seems good. But after restart instead of GRUB2 black screen with prompt *grub>* is shown (something like that [http://img854.imageshack.us/img854/5762/dsc00227edit0.jpg](http://img854.imageshack.us/img854/5762/dsc00227edit0.jpg)) and I can't start Ubuntu with this. If I type *exit* I can choose what I want to start (in BIOS) and when choose Windows it starts properly.

So I decided to repair GRUB2 with LiveCD but it always fails on ```
update-grub
``` with this output:
```
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

```


This is fdisk output which is also messed up:
```
sudo fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    46905263    23452631+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x40d22dca


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 4018 MB, 4018143232 bytes
131 heads, 26 sectors/track, 2304 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73876c0c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048     7847935     3922944    b  W95 FAT32

```

I really don't know how can I fix this. I don't want to reinstall Ubuntu because it looks like its working but I just can't start it (and I don't have backup).


[SIZE=3]**Output form boot_info_script:**[/SIZE]
```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS
    Boot files:        /etc/fstab


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/MokManager.efi /efi/ubuntu/shimx64.efi


sdb3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sdb5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Kali GNU/Linux 1.1.0
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7372160 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1    46,905,263    46,905,263  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624    46,901,247    45,850,624 Data partition (Linux)
/dev/sda3      46,901,248    46,903,295         2,048 Swap partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sdb2         616,448       821,247       204,800 EFI System partition
/dev/sdb3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb4       1,083,392   614,402,047   613,318,656 Data partition (Windows/Linux)
/dev/sdb5     614,402,048 1,809,316,220 1,194,914,173 Data partition (Windows/Linux)
/dev/sdb6   1,809,317,888 1,953,523,711   144,205,824 Data partition (Windows/Linux)


Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 4018 MB, 4018143232 bytes
131 heads, 26 sectors/track, 2304 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1    *          2,048     7,847,935     7,845,888   b W95 FAT32




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        FFF6-B8F7                              vfat       
/dev/sda2        8a104a65-ff1f-4865-8063-2781a43060b9   ext4       
/dev/sda3        ac42eafe-5725-4a38-9b64-e3398faa2f14   swap       
/dev/sdb1        F6C0-42E6                              vfat       
/dev/sdb2        3C26-1D87                              vfat       
/dev/sdb4        F4F24115F240DE0C                       ntfs       Windows
/dev/sdb5        47BD3D9923CA0985                       ntfs       Data
/dev/sdb6        a226513a-fb9a-4528-b005-d7e82de4afb8   ext4       Kali
/dev/sdc1        9AC6-B6AD                              vfat       KALI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                    <mount point>    <type>    <options>                <dump>    <pass>


UUID=8a104a65-ff1f-4865-8063-2781a43060b9    /        ext4    errors=remount-ro            0    1
#UUID=FFF6-B8F7                    /boot/efi    vfat    defaults                0    1
UUID=693a1c18-6ab0-4a50-8733-4341922bd56d     none            swap    sw                          0       0
UUID=F4F24115F240DE0C                /media/Win    ntfs    defaults,noauto                0    0
UUID=a226513a-fb9a-4528-b005-d7e82de4afb8    /media/Kali    ext4    nosuid,nodev,nofail,noauto        0    0
UUID=47BD3D9923CA0985                /media/Data    ntfs    defaults,noauto             0    0
UUID=3C26-1D87                    /boot/efi    vfat    defaults                0    1
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=========================== sdb6/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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


function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}


insmod part_gpt
insmod ext2
set root='(hd1,gpt6)'
search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd1,gpt6)'
  search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_gpt
insmod ext2
set root='(hd1,gpt6)'
search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
insmod png
if background_image /usr/share/images/desktop-base/kali-grub.png; then
  set color_normal=white/black
  set color_highlight=black/white
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Kali GNU/Linux, with Linux 3.18.0-kali3-amd64' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.18.0-kali3-amd64 ...'
    linux    /boot/vmlinuz-3.18.0-kali3-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro initrd=/install/initrd.gz quiet nouveau.modeset=0
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.18.0-kali3-amd64
}
menuentry 'Kali GNU/Linux, with Linux 3.18.0-kali3-amd64 (recovery mode)' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.18.0-kali3-amd64 ...'
    linux    /boot/vmlinuz-3.18.0-kali3-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro single initrd=/install/initrd.gz
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.18.0-kali3-amd64
}
menuentry 'Kali GNU/Linux, with Linux 3.18.0-kali1-amd64' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.18.0-kali1-amd64 ...'
    linux    /boot/vmlinuz-3.18.0-kali1-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro initrd=/install/initrd.gz quiet nouveau.modeset=0
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.18.0-kali1-amd64
}
menuentry 'Kali GNU/Linux, with Linux 3.18.0-kali1-amd64 (recovery mode)' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.18.0-kali1-amd64 ...'
    linux    /boot/vmlinuz-3.18.0-kali1-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro single initrd=/install/initrd.gz
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.18.0-kali1-amd64
}
menuentry 'Kali GNU/Linux, with Linux 3.14-kali1-amd64' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.14-kali1-amd64 ...'
    linux    /boot/vmlinuz-3.14-kali1-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro initrd=/install/initrd.gz quiet nouveau.modeset=0
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.14-kali1-amd64
}
menuentry 'Kali GNU/Linux, with Linux 3.14-kali1-amd64 (recovery mode)' --class kali --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set=root a226513a-fb9a-4528-b005-d7e82de4afb8
    echo    'Loading Linux 3.14-kali1-amd64 ...'
    linux    /boot/vmlinuz-3.14-kali1-amd64 root=UUID=a226513a-fb9a-4528-b005-d7e82de4afb8 ro single initrd=/install/initrd.gz
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.14-kali1-amd64
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
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


=============================== sdb6/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                 <mount point>   <type>  <options>           <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=a226513a-fb9a-4528-b005-d7e82de4afb8    /               ext4    errors=remount-ro    0       1


# swap was on /dev/sdb7 during installation
UUID=6964d68f-dc31-492d-87eb-9f3a85c1a55d     none            swap    sw                  0       0
/dev/sdc1                       /media/usb0     auto    rw,user,noauto      0       0
/dev/sdc2                       /media/usb1     auto    rw,user,noauto      0       0
--------------------------------------------------------------------------------


====================== sdb6/boot/extlinux/extlinux.conf: =======================


--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update




default l0
prompt 1
timeout 50


display boot.txt
include linux.cfg
include memdisk.cfg
--------------------------------------------------------------------------------


=================== sdb6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




================= sdb6: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)




=========================== sdc1/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi


set menu_color_normal=white/black
set menu_color_highlight=black/light-gray


menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------


============================== sdc1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 


label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --


label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --


label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --


label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 


label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 


label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --


label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --


label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --


label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --


--------------------------------------------------------------------------------


=================== sdc1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




================= sdc1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)




============== sdc1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb2


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 87 1d 26 3c 4e  4f 20 4e 41 4d 45 20 20  |..)..&<NO NAME  |
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




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-ZAmc7kGQ/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ZAmc7kGQ/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ZAmc7kGQ/Tmp_Log: No such file or directory
bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-ZAmc7kGQ/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ZAmc7kGQ/Tmp_Log: No such file or directory
  No volume groups found

```



Thank you for your help :)

---

### Post by oldfred on 2015-04-18
You have two drives with two efi partitions. But script did not show the /EFI/Microsoft folder? Your Windows must be in UEFI boot mode as it is on a gpt drive, and if it works script must not have shown it correctly?

You show your install in sda2 originally was using the efi partition on sda, which to me would be more correct, but Boot-Repair or you commented it out and changed to the efi partition on sdb.

Your install in sdb6 Kali, does not have a reference to an efi partition in its fstab, so it must be in BIOS mode? And if you try to reinstall grub from it, it will use grub-pc  (i386 platform) not grub-efi-amd64. But to have a BIOS boot on a gpt partitioned drive, you must have a 1 or 2MB unformatted partition with the bios_grub flag if using gparted or the code ef02 if using gdisk. That assigns the correct GUID.

But I think you want to keep UEFI boot. And you need to select UEFI boot from UEFI boot menu. 

Booting Ubuntu in UEFI mode, were you able to boot kali from grub menu? It may not have to be a UEFI install to work since most of the difference is grub version and an fstab entry. But I thought grub2's os-prober only found other installs in same boot mode either UEFI or BIOS?

Better to make sure all installs are UEFI boot.

Post this from Ubuntu  or live installer booted in UEFI mode.

sudo efibootmgr -v

---

### Post by Filip_Vavera on 2015-04-19
There are some pictures of my notebook :)

On PC start:
[ATTACH=CONFIG]261402[/ATTACH]

After type *exit*:
[ATTACH=CONFIG]261403[/ATTACH]

My BIOS boot menu:
[ATTACH=CONFIG]261404[/ATTACH]

When I choose something else then "Windows Boot Manager" or "EFI USB Device" (Live CD) I end up in the first screen (black grub).

```
sudo efibootmgr -v
```
Command not found.

The unknown program which I installed and use was Boot-Repair and after that black GRUB screen is shown.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2015-04-19
You have to be consistent on how you boot. And you may be in CSM mode and then the exit takes you to UEFI?

You have both UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And if you boot in BIOS mode then you do not have efibootmgr. Boot in UEFI mode to see UEFI entries.
But you should be able to boot ubuntu entry directly from UEFI menu?

---

