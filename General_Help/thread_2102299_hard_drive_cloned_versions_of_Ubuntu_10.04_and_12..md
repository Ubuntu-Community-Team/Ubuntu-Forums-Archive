---
title: "hard drive cloned versions of Ubuntu 10.04 and 12.04 boot error"
date: 2013-01-06
forum: General Help
---

### Post by james2b on 2013-01-06
I used Acronis True Image to make a cloned copy of my hard drive which has 3 Windows and 2 Ubuntu Linux installed on it. And when I do select that new hard drive clone with the boot menu, which I use the Windows boot manager and that EasyBCD configuration tool to add in Linux, it shows an error that says; "invalid partition table". So then I booted to the GParted CD which is the newer version, and used the Test Disk tool to check the partition table of the clone drive, and it was all looking good. On the original hard drive I have the Ubuntu grub 2 installed on 10.04 and 12.04 root partition and no issue to boot those Linux on that drive. So is there some fix ?

---

### Post by james2b on 2013-01-07
Update to this issue. I re-created my Ubuntu 10.04 and 12.04 boot entries in the utility Easy BCD from the original operating system in this computer, Vista. And from the internal hard drive Ubuntu I ran file system checks with that Disk Utility which shows okay. So now when I select the boot device from this store built 2009 desk top system boot menu to be the external esata cloned drive, that error message is gone, and it now boots to grub 2 when selected from the Windows Boot Manager, but then it just re-directs to boot the internal drive Ubuntu. The one sure way to really troubleshoot that cloned SATA drive in my external enclosure is to disconnect my internal hard drive sata cable, then boot up the PC with only the clone drive connected, right ?

---

### Post by ibjsb4 on 2013-01-07
Could it be the clone needs its own uuid?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uuid&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=uuid&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by james2b on 2013-01-07
Okay it is most likely that to boot that external clone drive I do need to change the UUID, so how do I do that ? I can boot to a live Ubuntu CD and fix it with a terminal command or edit a file? I ran that bootinfoscript tool and can post the results text file. So with that detail information I can possibly change the UUID. If I use it to replace the old drive, then all Ubuntus boot as it is, but then only as the second drive if we change it.

---

### Post by james2b on 2013-01-13
So then booting with grub 2 is the UUID easy to change since I did run the bootinfoscript tool ? Can I just copy and past what it does show for the Ubuntu 10.04 UUID from the boot info script text file results, into the grub boot lines for UUID= ? Here is that boot file; 
```
ran on 1-7-2013                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /NST/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda6 and looks at sector 367314739 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 404015977 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /NST/menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb6 and looks at sector 367287795 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb7 
                       and looks at sector 416062001 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb10 
                       starts at sector 63.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   136,316,198   136,316,136   7 NTFS / exFAT / HPFS
/dev/sda2         136,316,928   199,235,583    62,918,656   7 NTFS / exFAT / HPFS
/dev/sda3         199,237,632   356,528,127   157,290,496   7 NTFS / exFAT / HPFS
/dev/sda4         356,530,606   976,773,119   620,242,514   5 Extended
/dev/sda5         356,530,608   358,635,059     2,104,452  82 Linux swap / Solaris
/dev/sda6         358,635,123   390,090,329    31,455,207  83 Linux
/dev/sda7         390,090,393   421,545,599    31,455,207  83 Linux
/dev/sda8         421,545,663   455,098,367    33,552,705  83 Linux
/dev/sda9         455,100,416   486,557,695    31,457,280  83 Linux
/dev/sda10        486,559,744   528,502,783    41,943,040   7 NTFS / exFAT / HPFS
/dev/sda11        528,504,832   976,773,119   448,268,288   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   161,356,859   161,356,797   7 NTFS / exFAT / HPFS
/dev/sdb2         161,356,860   235,818,134    74,461,275   7 NTFS / exFAT / HPFS
/dev/sdb3         235,818,135   421,979,354   186,161,220   7 NTFS / exFAT / HPFS
/dev/sdb4         421,979,355   625,153,409   203,174,055   f W95 Extended (LBA)
/dev/sdb5         421,979,418   424,083,869     2,104,452  82 Linux swap / Solaris
/dev/sdb6         424,083,933   461,306,474    37,222,542  83 Linux
/dev/sdb7         461,306,538   498,529,079    37,222,542  83 Linux
/dev/sdb8         498,529,143   538,241,759    39,712,617  83 Linux
/dev/sdb9         538,241,823   575,480,429    37,238,607  83 Linux
/dev/sdb10        575,480,493   625,137,344    49,656,852   7 NTFS / exFAT / HPFS

/dev/sdb4 ends after the last sector of /dev/sdb

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   125,835,263   125,833,216   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FEBCA8E4BCA89923                       ntfs       Vista-64
/dev/sda10       5B81A6E635A82E81                       ntfs       
/dev/sda11       2E0422F630F6BE2A                       ntfs       big-ntfs
/dev/sda2        0C304BFB304BE9F2                       ntfs       XP
/dev/sda3        9CBC1DC4BC1D99BA                       ntfs       Windows 7
/dev/sda5        24960ec2-7042-4ff5-83ed-971ec37d7db1   swap       
/dev/sda6        0d038158-1bce-4602-8d27-55eba42bbd9c   ext4       
/dev/sda7        dbce0e73-9dcc-4924-8d21-a412606ff6bc   ext4       
/dev/sda8        e915031c-9711-4690-9467-90602d3453f5   ext2       
/dev/sda9        8c241979-2e44-4049-9f35-67cd33185ac6   ext2       
/dev/sdb1        CD5CA3F64C5CDEC2                       ntfs       Vista-clone
/dev/sdb10       01FBF2894D18190A                       ntfs       ntfs-clone
/dev/sdb2        E55F3A53A49E7E86                       ntfs       XP-clone
/dev/sdb3        5DFD662B02AF1196                       ntfs       Win7-clone
/dev/sdb5        c757d668-2169-1722-c6cf-4eddfa9df23c   swap       
/dev/sdb6        562ad67b-2bdd-b9b0-b443-05bda0986d0c   ext4       Ubuntu clone
/dev/sdb7        1fd0dd80-3ec2-fc1e-b182-b529cbc174cf   ext4       12.04 clone
/dev/sdb8        940cb0f5-e230-3abd-25e7-c9847aee992d   ext2       
/dev/sdb9        7def511c-f1c4-31b2-3beb-3a43ecab52cc   ext2       
/dev/sdc1        E83AA1DD3AA1A8D0                       ntfs       SSD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


============================== sda1/NST/menu.lst: ==============================

--------------------------------------------------------------------------------
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD/
default 0
timeout 20

title Ubuntu 10.04
root (hd0,5)
chainloader +1
boot

title Ubuntu 12.04 Linux
root (hd0,6)
chainloader +1
boot

--------------------------------------------------------------------------------

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP on N:\" /fastdetect
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             NST/menu.lst                                   0

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-45-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-45-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-45-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-44-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-44-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-44-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-44-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-44-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-42-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-42-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-42-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-42-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-42-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set FEBCA8E4BCA89923
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0C304BFB304BE9F2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-34-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-34-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 12.04 on sda7" {
set root=(hd0,7)
chainloader +1
}

menuentry "external mbr on sdb" {
set root=(hd1)
chainloader +1
}

menuentry "Fedora 15 on sdb1" {
set root=(hd1,1)
chainloader +1
}

menuentry "PCLinux on sdb2" {
set root=(hd1,2)
chainloader +1
}

menuentry "Mint on sdb3" {
set root=(hd1,3)
chainloader +1
}

menuentry "Fedora 14 on sdb5" {
set root=(hd1,5)
chainloader +1
}

menuentry "Kubuntu 10.04 on sdb7" {
set root=(hd1,7)
chainloader +1
}

menuentry "Mandriva on sdb8" {
set root=(hd1,8)
chainloader +1
}
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24960ec2-7042-4ff5-83ed-971ec37d7db1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 175.136495113 = 188.051379712  boot/grub/core.img                             1
 173.541955471 = 186.339255808  boot/grub/grub.cfg                             1
 176.404340267 = 189.412718080  boot/initrd.img-2.6.32-42-generic-pae          1
 176.518830776 = 189.535651328  boot/initrd.img-2.6.32-44-generic-pae          1
 176.653874874 = 189.680653824  boot/initrd.img-2.6.32-45-generic-pae          1
 176.350389004 = 189.354788352  boot/vmlinuz-2.6.32-42-generic-pae             1
 174.973435879 = 187.876296192  boot/vmlinuz-2.6.32-44-generic-pae             2
 172.399220943 = 185.112253952  boot/vmlinuz-2.6.32-45-generic-pae             1
 176.653874874 = 189.680653824  initrd.img                                     1
 176.518830776 = 189.535651328  initrd.img.old                                 1
 172.399220943 = 185.112253952  vmlinuz                                        1
 174.973435879 = 187.876296192  vmlinuz.old                                    2

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-35-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-34-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root FEBCA8E4BCA89923
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0C304BFB304BE9F2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-45-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-45-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-45-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-45-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-44-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-44-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-44-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-44-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-42-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-42-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-42-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-42-generic-pae
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24960ec2-7042-4ff5-83ed-971ec37d7db1 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=90bd4915-b849-4c45-9cfc-34d1378dbe03 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 192.649857044 = 206.856208896  boot/grub/core.img                             1
 198.438980579 = 213.072232960  boot/grub/grub.cfg                             1
 187.514973164 = 201.342669312  boot/initrd.img-3.2.0-29-generic-pae           2
 193.645367146 = 207.925129728  boot/initrd.img-3.2.0-34-generic-pae           2
 193.702480793 = 207.986455040  boot/initrd.img-3.2.0-35-generic-pae           1
 198.310940266 = 212.934750720  boot/vmlinuz-3.2.0-29-generic-pae              1
 186.920517445 = 200.704377344  boot/vmlinuz-3.2.0-34-generic-pae              2
 187.608021259 = 201.442578944  boot/vmlinuz-3.2.0-35-generic-pae              1
 187.514973164 = 201.342669312  initrd.img.old                                 2
 187.608021259 = 201.442578944  vmlinuz                                        1
 198.310940266 = 212.934750720  vmlinuz.old                                    1

============================== sdb1/NST/menu.lst: ==============================

--------------------------------------------------------------------------------
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD/
default 0
timeout 20

title Ubuntu 10.04
root (hd1,5)
chainloader +1
boot

title Ubuntu 12.04 Linux
root (hd1,6)
chainloader +1
boot

--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe
; Use EasyBCD from http://neosmart.net/dl.php?id=1 to manage your bootloader

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP on N:\" /fastdetect
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             NST/menu.lst                                   0

================================ sdb2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-45-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-45-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-45-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-44-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-44-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-44-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-44-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-44-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-42-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux	/boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-42-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-42-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	echo	'Loading Linux 2.6.32-42-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-42-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set FEBCA8E4BCA89923
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0C304BFB304BE9F2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-35-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-34-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-34-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset
	initrd /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu 12.04 on sda7" {
set root=(hd0,7)
chainloader +1
}

menuentry "external mbr on sdb" {
set root=(hd1)
chainloader +1
}

menuentry "Fedora 15 on sdb1" {
set root=(hd1,1)
chainloader +1
}

menuentry "PCLinux on sdb2" {
set root=(hd1,2)
chainloader +1
}

menuentry "Mint on sdb3" {
set root=(hd1,3)
chainloader +1
}

menuentry "Fedora 14 on sdb5" {
set root=(hd1,5)
chainloader +1
}

menuentry "Kubuntu 10.04 on sdb7" {
set root=(hd1,7)
chainloader +1
}

menuentry "Mandriva on sdb8" {
set root=(hd1,8)
chainloader +1
}
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24960ec2-7042-4ff5-83ed-971ec37d7db1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 203.507826328 = 218.514864640  boot/grub/core.img                             1
 202.957224369 = 217.923660288  boot/grub/grub.cfg                             1
 204.024416447 = 219.069549056  boot/initrd.img-2.6.32-42-generic-pae          1
 204.079077244 = 219.128240640  boot/initrd.img-2.6.32-44-generic-pae          1
 204.110369205 = 219.161840128  boot/initrd.img-2.6.32-45-generic-pae          1
 203.988646030 = 219.031140864  boot/vmlinuz-2.6.32-42-generic-pae             1
 203.460161686 = 218.463685120  boot/vmlinuz-2.6.32-44-generic-pae             2
 202.570971012 = 217.508923904  boot/vmlinuz-2.6.32-45-generic-pae             1
 204.110369205 = 219.161840128  initrd.img                                     1
 204.079077244 = 219.128240640  initrd.img.old                                 1
 202.570971012 = 217.508923904  vmlinuz                                        1
 203.460161686 = 218.463685120  vmlinuz.old                                    2

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-35-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-35-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-34-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-34-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root dbce0e73-9dcc-4924-8d21-a412606ff6bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root FEBCA8E4BCA89923
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 0C304BFB304BE9F2
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-45-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-45-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-45-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-45-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-45-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-44-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-44-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-44-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-44-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-44-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-42-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-42-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-42-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-42-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-42-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-41-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-41-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-40-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-40-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-40-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-40-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-40-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-40-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-39-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-39-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-39-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-39-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-39-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-39-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-37-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-37-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-37-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-37-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-37-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-37-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-35-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-35-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-35-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-35-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-35-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-35-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-34-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-34-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 0d038158-1bce-4602-8d27-55eba42bbd9c
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=0d038158-1bce-4602-8d27-55eba42bbd9c ro single
	initrd /boot/initrd.img-2.6.32-25-generic-pae
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=dbce0e73-9dcc-4924-8d21-a412606ff6bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24960ec2-7042-4ff5-83ed-971ec37d7db1 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=90bd4915-b849-4c45-9cfc-34d1378dbe03 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 223.509591103 = 239.991596032  boot/grub/core.img                             1
 222.070870399 = 238.446781440  boot/grub/grub.cfg                             1
 221.091950417 = 237.395674112  boot/initrd.img-3.2.0-29-generic-pae           1
 222.814774513 = 239.245542400  boot/initrd.img-3.2.0-34-generic-pae           2
 222.865204811 = 239.299691520  boot/initrd.img-3.2.0-35-generic-pae           1
 223.457997322 = 239.936197632  boot/vmlinuz-3.2.0-29-generic-pae              1
 220.655434608 = 236.926968832  boot/vmlinuz-3.2.0-34-generic-pae              2
 221.152501106 = 237.460689920  boot/vmlinuz-3.2.0-35-generic-pae              1
 221.091950417 = 237.395674112  initrd.img.old                                 1
 221.152501106 = 237.460689920  vmlinuz                                        1
 223.457997322 = 239.936197632  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

lzma: Decoder error


```

---

### Post by sudodus on 2013-01-13
> **james2b said:**
> Okay it is most likely that to boot that external clone drive I do need to change the UUID, so how do I do that ? I can boot to a live Ubuntu CD and fix it with a terminal command or edit a file? I ran that bootinfoscript tool and can post the results text file. So with that detail information I can possibly change the UUID. If I use it to replace the old drive, then all Ubuntus boot as it is, but then only as the second drive if we change it.
You can test that the clone is working by removing the original drive. Then the clone should behave like the original drive.

If you want both mounted at the same time, you can use tune2fs to edit the UUID of each partition /dev/sdx where x is a, b, c ...

```
**tune2fs -U **_UUID_ /dev/sdx
```

From ```
man tune2fs
```
```

      -U UUID
             Set the universally unique identifier (UUID) of the  filesystem  to
             UUID.   The  format of the UUID is a series of hex digits separated
             by hyphens, like this: "c1b9d5a2-f162-11cf-9ece-0020afc76f16".  The
             UUID parameter may also be one of the following:

             clear  clear the filesystem UUID
 
             random generate a new randomly-generated UUID

             time   generate a new time-based UUID

             The  UUID  may be used by mount(8), fsck(8), and /etc/fstab(5) (and
             possibly others) by specifying UUID=uuid instead of a block special
             device name like /dev/hda1.

             See uuidgen(8) for more information.  If the system does not have a
             good random number generator such as /dev/random  or  /dev/urandom,
             tune2fs  will automatically use a time-based UUID instead of a ran&#8208;
             domly-generated UUID.

```

---

### Post by sudodus on 2013-01-13
You need also to edit /etc/fstab to use the new UUID for the drives to be mounted and for the swap file.

If you forget this for the system drive(s) it will not boot.

---

