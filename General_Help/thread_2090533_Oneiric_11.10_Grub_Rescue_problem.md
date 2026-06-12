---
title: "Oneiric 11.10 Grub Rescue problem"
date: 2012-12-02
forum: General Help
---

### Post by Dr Mac 24 on 2012-12-02
Sovled by followed the info at [http://askubuntu.com/posts/86300/edit](http://askubuntu.com/posts/86300/edit) ie:

Insert your Ubuntu live (desktop) CD or flash drive, reboot your computer from CD/Flash drive into a live, desktop session.

Install and run Boot-Repair

    sudo add-apt-repository ppa:yannubuntu/boot-repair
    sudo apt-get update 
    sudo apt-get install -y boot-repair
    gksu boot-repair

Click "Recommended repair" -> apply.
Cheers.

Hi,

I updated my Ubuntu 11.10 OS and rebooted which resulted in screen with "Error : ELF header smaller than expected, Grub rescue" With the Oneiric Live CD I've found that boot/Grub is full of about 200 empty amiga sound track audio files, so I guess it has become corrupted and needs reinstalling.  Having looked at various forums eg 
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://ubuntuforums.org/showthread.php?t=1865214](http://ubuntuforums.org/showthread.php?t=1865214)

 I'm not sure how to proceed. I would be grateful for anyones help??

I have a number of partitions for Ubuntu 11.10, 10.04, Windows XP, and a few storage partitions. I also have an Oneiric Live CD so can access the partitions.

The bootinfoscript “results” are 

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.0 GB, 499971544064 bytes
255 heads, 63 sectors/track, 60784 cylinders, total 976506922 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 NTFS / exFAT / HPFS
/dev/sda2         104,857,600   230,676,479   125,818,880  83 Linux
/dev/sda3         230,677,335   251,642,159    20,964,825  82 Linux swap / Solaris
/dev/sda4         251,642,221   976,504,831   724,862,611   5 Extended
/dev/sda5         251,642,223   304,078,319    52,436,097  83 Linux
/dev/sda6         304,078,383   461,354,669   157,276,287  83 Linux
/dev/sda7         461,354,733   566,210,924   104,856,192  83 Linux
/dev/sda8         566,212,608   968,646,655   402,434,048  83 Linux
/dev/sda9         968,648,704   976,504,831     7,856,128  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0AB4AB0FB4AAFC77                       ntfs       XPOS
/dev/sda2        fed85577-22b8-4303-96d8-b9ff80b4a476   ext4       Ubuntu11-10
/dev/sda3        7a287806-1b74-4bbf-9900-c820d23e4f38   swap       
/dev/sda5        d94e0a75-817b-477f-815d-c3b1720de54c   ext3       Ububtu-WorkFiles
/dev/sda6        3d02bdd0-26cf-4a8a-82ae-f8e93ca0377b   ext3       UbuntuArchive
/dev/sda7        26f2a6b6-b1ec-46c4-9175-cf0460598e8a   ext3       
/dev/sda8        cf4013d3-7fc7-48d6-a076-c1bb79a6accc   ext4       Store
/dev/sda9        efd89a3e-4b65-4db9-8ca5-bddf3501bacc   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Ubuntu11-10       ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda8        /media/Store             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-28-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-28-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-28-generic ...'
	linux	/boot/vmlinuz-3.0.0-28-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-28-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-26-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-26-generic ...'
	linux	/boot/vmlinuz-3.0.0-26-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-25-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-25-generic ...'
	linux	/boot/vmlinuz-3.0.0-25-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-24-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-24-generic ...'
	linux	/boot/vmlinuz-3.0.0-24-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-23-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-23-generic ...'
	linux	/boot/vmlinuz-3.0.0-23-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-22-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-22-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-22-generic ...'
	linux	/boot/vmlinuz-3.0.0-22-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-22-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-21-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-21-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-21-generic ...'
	linux	/boot/vmlinuz-3.0.0-21-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-21-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-20-generic ...'
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-14-generic ...'
	linux	/boot/vmlinuz-3.0.0-14-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fed85577-22b8-4303-96d8-b9ff80b4a476 ro recovery nomodeset resume=UUID=7a287806-1b74-4bbf-9900-c820d23e4f38
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root fed85577-22b8-4303-96d8-b9ff80b4a476
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0AB4AB0FB4AAFC77
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-45-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-45-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-45-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-45-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-42-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-42-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-42-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-42-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-42-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-42-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-40-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-40-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-40-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-40-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-40-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-38-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-38-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-37-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-37-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-37-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-37-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-36-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-36-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791
	initrd /boot/initrd.img-2.6.32-36-generic
}
menuentry "Ubuntu 10.04.4 LTS, kernel 2.6.32-36-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/vmlinuz-2.6.32-36-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro single
	initrd /boot/initrd.img-2.6.32-36-generic
}
menuentry "Ubuntu 10.04.4 LTS, memtest86+ (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 26f2a6b6-b1ec-46c4-9175-cf0460598e8a
	linux /boot/memtest86+.bin 
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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid          0  0  
# / was on /dev/sda2 during installation
UUID=fed85577-22b8-4303-96d8-b9ff80b4a476  /               ext4  errors=remount-ro            0  1  
# swap was on /dev/sda3 during installation
UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  none            swap  sw                           0  0  
# swap was on /dev/sda9 during installation
UUID=efd89a3e-4b65-4db9-8ca5-bddf3501bacc  none            swap  sw                           0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8     0  0  
/dev/sda8                                  /media/Store    ext4  defaults                     0  0  
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/initrd.img-3.0.0-15-generic               1
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/initrd.img-3.0.0-17-generic               1
               =                boot/initrd.img-3.0.0-19-generic               1
               =                boot/initrd.img-3.0.0-20-generic               2
               =                boot/initrd.img-3.0.0-21-generic               2
               =                boot/initrd.img-3.0.0-22-generic               1
               =                boot/initrd.img-3.0.0-23-generic               2
               =                boot/initrd.img-3.0.0-24-generic               1
               =                boot/initrd.img-3.0.0-25-generic               2
               =                boot/initrd.img-3.0.0-26-generic               2
               =                boot/initrd.img-3.0.0-28-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                boot/vmlinuz-3.0.0-15-generic                  2
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                boot/vmlinuz-3.0.0-17-generic                  2
               =                boot/vmlinuz-3.0.0-19-generic                  2
               =                boot/vmlinuz-3.0.0-20-generic                  1
               =                boot/vmlinuz-3.0.0-21-generic                  1
               =                boot/vmlinuz-3.0.0-22-generic                  1
               =                boot/vmlinuz-3.0.0-23-generic                  1
               =                boot/vmlinuz-3.0.0-24-generic                  1
               =                boot/vmlinuz-3.0.0-25-generic                  2
               =                boot/vmlinuz-3.0.0-26-generic                  2
               =                boot/vmlinuz-3.0.0-28-generic                  2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

=========================== sda7/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=26f2a6b6-b1ec-46c4-9175-cf0460598e8a

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-45-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-45-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-45-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-45-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-42-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-42-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-42-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-42-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-42-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-42-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-41-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-41-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-41-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-41-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-40-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-40-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-40-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-40-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-40-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-40-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-38-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-38-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-38-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-38-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-38-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-38-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-37-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-37-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-37-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-37-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-36-generic
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-36-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro splash vga=791 
initrd		/boot/initrd.img-2.6.32-36-generic
quiet

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-36-generic (recovery mode)
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/vmlinuz-2.6.32-36-generic root=UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a ro  single
initrd		/boot/initrd.img-2.6.32-36-generic

title		Ubuntu 10.04.4 LTS, memtest86+
uuid		26f2a6b6-b1ec-46c4-9175-cf0460598e8a
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro single 
initrd		/boot/initrd.img-2.6.27-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bef0d311-c229-41fb-bfa0-1c5ca8063f43 ro single 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.10, memtest86+ (on /dev/sda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                 proc         defaults                    0  0  
# / was on /dev/sda7 during installation
UUID=26f2a6b6-b1ec-46c4-9175-cf0460598e8a  /                     ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda3 during installation
UUID=7a287806-1b74-4bbf-9900-c820d23e4f38  none                  swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0         udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0        auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda5                                  /media/sda5           ext3         defaults,relatime           0  0  
/dev/sda6                                  /media/UbuntuArchive  ext3         defaults                    0  0  
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.32-36-generic              6
               =                boot/initrd.img-2.6.32-37-generic              6
               =                boot/initrd.img-2.6.32-38-generic              6
               =                boot/initrd.img-2.6.32-40-generic              6
               =                boot/initrd.img-2.6.32-41-generic             50
               =                boot/initrd.img-2.6.32-42-generic              7
               =                boot/initrd.img-2.6.32-45-generic             11
               =                boot/vmlinuz-2.6.32-36-generic                 3
               =                boot/vmlinuz-2.6.32-37-generic                 2
               =                boot/vmlinuz-2.6.32-38-generic                 2
               =                boot/vmlinuz-2.6.32-40-generic                 2
               =                boot/vmlinuz-2.6.32-41-generic                 5
               =                boot/vmlinuz-2.6.32-42-generic                 3
               =                boot/vmlinuz-2.6.32-45-generic                 3
               =                initrd.img                                    11
               =                initrd.img.old                                 7
               =                vmlinuz                                        3
               =                vmlinuz.old                                    3

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

