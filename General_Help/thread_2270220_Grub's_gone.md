---
title: "Grub's gone"
date: 2015-03-21
forum: General Help
---

### Post by Dina_Eaton on 2015-03-21
I messed up. Bad. Im writing to you now from beyond the grave on a mint live USB.
I had Elementary, Mint, Ubuntu, and Sabayon and one [COLOR=#00ff00]Mint for testing[/COLOR] set up in perfect harmony. Today though, i deleted the latest addition to my disto's, the testmint. The testmint install had Shangaied my GRUB and disregarded my previous GRUB-setup. Stupidly I deleted the partition and thought all would be fine. I was wrong.

When i booted up again i got to the grub rescue shell. It seemed there was something wrong with it; basic commands like help, --help, -h, dd and boot were gone.
To rectify this i booted up the mint live usb and did 'attempt datarescue' to find the old [COLOR=#00ff00]testmint[/COLOR], to no avail. I then tried to reinstall mint on a different part of the disk, but the partition i made the first time was too small and the install failed. I made a bigger partition, still not overlapping where the testmint used to be and ran the installer. The installer detects the other OS's. It reports back 'successfull'.

When I boot up again. the GRUB rescue is gone and all Im left with is a 'non-system disk'.
My problem might be I dont understand grub.

Does anyone have any idea on how to get grub back?



This is my lsblk:

```

sda       8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1    8:1    0  1023M  0 part 
&#9500;&#9472;sda3    8:3    0     1K  0 part 
&#9500;&#9472;sda5    8:5    0   4.9G  0 part 
&#9500;&#9472;sda6    8:6    0    99M  0 part [SWAP]
&#9500;&#9472;sda7    8:7    0  19.5G  0 part 
&#9500;&#9472;sda8    8:8    0  39.8G  0 part 
&#9500;&#9472;sda9    8:9    0   9.8G  0 part 
&#9500;&#9472;sda10   8:10   0  19.5G  0 part 
&#9500;&#9472;sda11   8:11   0  11.8G  0 part 
&#9500;&#9472;sda12   8:12   0  18.6G  0 part 
&#9500;&#9472;sda13   8:13   0  20.1G  0 part 
&#9500;&#9472;sda14   8:14   0   4.6G  0 part 
&#9492;&#9472;sda15   8:15   0   9.5G  0 part 
sdb       8:16   1  14.7G  0 disk 
&#9500;&#9472;sdb1    8:17   1   1.5G  0 part 
&#9492;&#9472;sdb2    8:18   1   2.2M  0 part 
loop0     7:0    0   1.4G  1 loop /rofs

```

This is by blkid:
```
[COLOR=#00ff00]
/dev/loop0: TYPE="squashfs"                                                                   Im guessing this is the Live USB[/COLOR]
/dev/sda1: LABEL="Hello" UUID="d0978431-05e6-440a-bc90-6ac579758dcb" TYPE="ext4" 
/dev/sda5: LABEL="blackbook" UUID="34cd7037-85d8-4212-a8d6-e5e7bc0373f5" TYPE="ext4" 
/dev/sda6: UUID="c3a9a1f2-9cea-4211-aa29-dc2b60875646" TYPE="swap" 
/dev/sda7: LABEL="Elementary" UUID="c926aaf0-fccc-42a7-9e54-a5156c355c12" TYPE="ext4" 
[COLOR=#ff8c00]/dev/sda8: LABEL="Nedlastinger" UUID="2E5B49DA222B6E51" TYPE="ntfs"                            Where I keep my data
/dev/sda9: LABEL="Bilder" UUID="27AB008A2BBCB66A" TYPE="ntfs" 
/dev/sda10: LABEL="Filmer" UUID="5F7C6EE663BE4C43" TYPE="ntfs" 
/dev/sda11: LABEL="Skrivebord" UUID="0692210d-ad42-4a02-b1f3-f98c1a5956cf" TYPE="ext4" [/COLOR]
/dev/sda12: LABEL="Mint" UUID="a34ef865-6684-48ff-afb5-a846a61f4c00" TYPE="ext4" 
[COLOR=#800080]/dev/sda13: LABEL="Ubuntu" UUID="f05c536c-ae78-4105-a79f-970479b8483e" TYPE="ext4"             This is my main distro where i had Grub configured correctly.[/COLOR]
/dev/sda14: UUID="e27aaf5c-5d6d-4b6b-b087-a5c7a60a398f" TYPE="ext4" 
[COLOR=#00ff00]/dev/sda15: UUID="98ebd55a-46b5-4515-bb01-3bc35aad6ca8" TYPE="ext4"                            This is my mint i tried installing, but didnt work.[/COLOR]
[COLOR=#ee82ee]/dev/sdb1: LABEL="Linux Mint 17.1 Cinnamon 64-bit" TYPE="iso9660" 
/dev/sdb2: SEC_TYPE="msdos" UUID="0D6C-F933" TYPE="vfat"                                       LiveUSB[/COLOR][COLOR=#ffa500]




[/COLOR]
```

---

### Post by Dina_Eaton on 2015-03-21
Update:
Grub customizer, a personal favorite of mine because Im horrible at GRUB outputs this when I try to apply the settings from Ubuntu (sda13):

```

chroot '/media/grub-customizer_recovery_root_mountpoint' grub-mkconfig couldn't be executed successfully. error message:
 Generating grub configuration file ...
using custom appearance settings
Found background image: /home/dina/Pictures/wp/space/vtgkU.jpg
/etc/grub.d/32_os-prober_proxy: 3: /etc/grub.d/32_os-prober_proxy: /etc/grub.d/bin/grubcfg_proxy: not found
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Found Linux Mint 17.1 Rebecca (17.1) on /dev/sda12
cat: write error: Broken pipe

```

---

### Post by Bucky Ball on 2015-03-21
Have you tried [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? Give that a shot and see what happens. [Bit more]("http://ubuntuforums.org/showthread.php?t=1769482") info on Boot Repair. Don't think Grub Custromizer is going to get you far here. 

Please use [code] tags for terminal output. See last link in my signature for how. ;)

---

### Post by Dina_Eaton on 2015-03-21
Im back :D

At first I ran[COLOR=#0000ff] boot repair[/COLOR] with recommended settings. It said it failed, but it told me to reboot, so thats what I did. Still nothing.
So I opened GParted on the [COLOR=#ff0000]LiveUSB[/COLOR] and set the boot flag active for sda1. And that worked! \\:D/

There is nothing on sda1, except lost+found, so I am slightly mystified as to why this worked, but hey, Im not going to argue with it.


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
GParted > right click the first partition (sd([COLOR=#ff0000]a[/COLOR],b,c,d,)1) > manage flags > check boot

---

### Post by Bucky Ball on 2015-03-21
You can launch boot repair and generate a boot info file for more info on your grub. Post it here if you like. ;)

Good to see you got it working. Well done.

---

### Post by Dina_Eaton on 2015-03-21
Sure thing! Its huge though.

Might be more easily readable here: [http://paste2.org/HMx6jLnb](http://paste2.org/HMx6jLnb)

If the one before setting the flag, but after running boot repair is of any use it's here: [http://paste2.org/dXMLKvbZ](http://paste2.org/dXMLKvbZ)

This is after running boot repair and setting the flag:
```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]
 
 
============================= Boot Info Summary: ===============================
 
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.
 
sda1: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
 
sda3: __________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 
 
sda5: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
 
sda6: __________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info: 
 
sda7: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  elementary OS Luna 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
 
sda8: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sda9: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sda10: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
sda11: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub.cfg
 
sda12: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.1 Rebecca 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
 
sda13: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
 
sda14: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
 
sda15: _________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.1 Rebecca 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1    *          2,048     2,097,151     2,095,104  83 Linux
/dev/sda3           2,099,198   488,396,799   486,297,602   5 Extended
/dev/sda5         478,074,880   488,396,799    10,321,920  83 Linux
/dev/sda6         477,870,080   478,072,831       202,752  82 Linux swap / Solaris
/dev/sda7           2,099,200    43,060,137    40,960,938  83 Linux
/dev/sda8         394,438,656   477,868,031    83,429,376   7 NTFS / exFAT / HPFS
/dev/sda9         373,960,704   394,436,607    20,475,904   7 NTFS / exFAT / HPFS
/dev/sda10        333,002,752   373,958,655    40,955,904   7 NTFS / exFAT / HPFS
/dev/sda11        308,344,832   333,000,703    24,655,872  83 Linux
/dev/sda12         43,061,248    82,122,751    39,061,504  83 Linux
/dev/sda13         82,124,800   124,251,753    42,126,954  83 Linux
/dev/sda14        298,772,480   308,342,792     9,570,313  83 Linux
/dev/sda15        278,876,160   298,770,691    19,894,532  83 Linux
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/sda1        d0978431-05e6-440a-bc90-6ac579758dcb   ext4       *** me pls
/dev/sda10       5F7C6EE663BE4C43                       ntfs       Filmer
/dev/sda11       0692210d-ad42-4a02-b1f3-f98c1a5956cf   ext4       Skrivebord
/dev/sda12       a34ef865-6684-48ff-afb5-a846a61f4c00   ext4       Mint
/dev/sda13       f05c536c-ae78-4105-a79f-970479b8483e   ext4       Ubuntu
/dev/sda14       e27aaf5c-5d6d-4b6b-b087-a5c7a60a398f   ext4       
/dev/sda15       98ebd55a-46b5-4515-bb01-3bc35aad6ca8   ext4       
/dev/sda5        34cd7037-85d8-4212-a8d6-e5e7bc0373f5   ext4       Shiet
/dev/sda6        c3a9a1f2-9cea-4211-aa29-dc2b60875646   swap       
/dev/sda7        c926aaf0-fccc-42a7-9e54-a5156c355c12   ext4       Elementary
/dev/sda8        2E5B49DA222B6E51                       ntfs       Nedlastninger
/dev/sda9        27AB008A2BBCB66A                       ntfs       Bilder
 
========================= "ls -l /dev/disk/by-id" output: ======================
 
total 0
lrwxrwxrwx 1 root root  9 Mar 21 15:35 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part12 -> ../../sda12
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part13 -> ../../sda13
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part14 -> ../../sda14
lrwxrwxrwx 1 root root 11 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part15 -> ../../sda15
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Mar 21 15:15 ata-WDC_WD2500BEKT-60A25T1_WD-WXG1A7062401-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Mar 21 15:35 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part12 -> ../../sda12
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part13 -> ../../sda13
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part14 -> ../../sda14
lrwxrwxrwx 1 root root 11 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part15 -> ../../sda15
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Mar 21 15:15 scsi-SATA_WDC_WD2500BEKT-_WD-WXG1A7062401-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Mar 21 15:35 wwn-0x50014ee25a339911 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part12 -> ../../sda12
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part13 -> ../../sda13
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part14 -> ../../sda14
lrwxrwxrwx 1 root root 11 Mar 21 15:15 wwn-0x50014ee25a339911-part15 -> ../../sda15
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Mar 21 15:15 wwn-0x50014ee25a339911-part9 -> ../../sda9
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/sda10       /home/seb/Videos         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /felles                  ext4       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda8        /home/seb/Downloads      fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9        /home/seb/Pictures       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
 
 
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
search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
 
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
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
menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    linux    /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-77-generic-pae
}
menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (recovery mode)' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    echo    'Loading Linux 3.2.0-77-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-77-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    linux    /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-51-generic-pae
}
menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode)' --class elementary --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    echo    'Loading Linux 3.2.0-51-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-51-generic-pae
}
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) -- recovery mode (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) -- recovery mode (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Linux Mint 17.1 Rebecca (17.1) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e6a43606-8ccc-46ff-a228-e5da106d064d (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda14) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--e6a43606-8ccc-46ff-a228-e5da106d064d (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit,  3.13.0-37-generic (/dev/sda14) -- recovery mode (on /dev/sda14)' --class  gnu-linux --class gnu --class os $menuentry_id_option   'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d  ro recovery nomodeset-e6a43606-8ccc-46ff-a228-e5da106d064d (on  /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda15) (on /dev/sda15)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos15)'
    search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=98ebd55a-46b5-4515-bb01-3bc35aad6ca8 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda15) -- recovery mode (on /dev/sda15)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos15)'
    search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=98ebd55a-46b5-4515-bb01-3bc35aad6ca8 ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Rebecca (17.1) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a34ef865-6684-48ff-afb5-a846a61f4c00 (on /dev/sda15)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos15)'
    search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--a34ef865-6684-48ff-afb5-a846a61f4c00 (on /dev/sda15)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos15)'
    search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit,  3.13.0-37-generic (/dev/sda12) -- recovery mode (on /dev/sda12)' --class  gnu-linux --class gnu --class os $menuentry_id_option   'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00  ro recovery nomodeset-a34ef865-6684-48ff-afb5-a846a61f4c00 (on  /dev/sda15)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos15)'
    search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
    initrd /boot/initrd.img-3.13.0-37-generic
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 /               ext4    errors=remount-ro 0       1
# /felles was on /dev/sda5 during installation
UUID=34cd7037-85d8-4212-a8d6-e5e7bc0373f5 /felles         ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c3a9a1f2-9cea-4211-aa29-dc2b60875646 none            swap    sw              0       0
# /Nedlastninger was on /dev/sda8 during installation
UUID=2E5B49DA222B6E51 /home/seb/Downloads         ntfs    defaults        0       2
# /Bilder was on /dev/sda9 during installation
UUID=27AB008A2BBCB66A /home/seb/Pictures         ntfs    defaults        0       2
# /Filmer was on /dev/sda10 during installation
UUID=5F7C6EE663BE4C43 /home/seb/Videos         ntfs    defaults        0       2
# /Library was on /dev/sda11 during installation
# UUID=40e207e9-4859-40dd-acc9-1ba5d49ad6c4 /usr/lib         ext4    defaults        0       2
 
--------------------------------------------------------------------------------
 
=================== sda7: Location of files loaded by Grub: ====================
 
           GiB - GB             File                                 Fragment(s)
 
  11.140419006 = 11.961933824   boot/grub/grub.cfg                             1
  11.155300140 = 11.977912320   boot/grub/core.img                             1
  11.137626648 = 11.958935552   boot/vmlinuz-3.2.0-51-generic-pae              1
   2.021297455 = 2.170351616    boot/vmlinuz-3.2.0-77-generic-pae              1
  11.137626648 = 11.958935552   vmlinuz                                        1
   2.336914062 = 2.509242368    boot/initrd.img-3.2.0-51-generic-pae           3
  16.399414062 = 17.608736768   boot/initrd.img-3.2.0-77-generic-pae           2
   2.336914062 = 2.509242368    initrd.img                                     3
   2.336914062 = 2.509242368    initrd.img.old                                 3
 
=============================== sda11/grub.cfg: ================================
 
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
set root='hd0,msdos12'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
else
  search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
fi
    font="/usr/share/grub/unicode.pf2"
fi
 
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=nb_NO
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
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
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-37-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    echo    'Loading Linux 3.13.0-37-generic ...'
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-37-generic
}
submenu "Previous Linux versions" {
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    echo    'Loading Linux 3.13.0-24-generic ...'
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-24-generic
}
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a8dbbe34-bf03-4140-b327-3d0397fc0c97' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  a8dbbe34-bf03-4140-b327-3d0397fc0c97
    else
      search --no-floppy --fs-uuid --set=root a8dbbe34-bf03-4140-b327-3d0397fc0c97
    fi
    linux /boot/vmlinuz-3.16.0-30-generic root=UUID=a8dbbe34-bf03-4140-b327-3d0397fc0c97 ro persistent quiet splash $vt_handoff
    initrd /boot/initrd.img-3.16.0-30-generic
}
submenu 'Advanced options for Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' $menuentry_id_option 'osprober-gnulinux-advanced-a8dbbe34-bf03-4140-b327-3d0397fc0c97' {
    menuentry 'Ubuntu (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--a8dbbe34-bf03-4140-b327-3d0397fc0c97' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  a8dbbe34-bf03-4140-b327-3d0397fc0c97
        else
          search --no-floppy --fs-uuid --set=root a8dbbe34-bf03-4140-b327-3d0397fc0c97
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=a8dbbe34-bf03-4140-b327-3d0397fc0c97 ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, med Linux 3.16.0-30-generic (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--a8dbbe34-bf03-4140-b327-3d0397fc0c97' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  a8dbbe34-bf03-4140-b327-3d0397fc0c97
        else
          search --no-floppy --fs-uuid --set=root a8dbbe34-bf03-4140-b327-3d0397fc0c97
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=a8dbbe34-bf03-4140-b327-3d0397fc0c97 ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic-root=UUID=a8dbbe34-bf03-4140-b327-3d0397fc0c97  ro recovery nomodeset persistent-a8dbbe34-bf03-4140-b327-3d0397fc0c97' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  a8dbbe34-bf03-4140-b327-3d0397fc0c97
        else
          search --no-floppy --fs-uuid --set=root a8dbbe34-bf03-4140-b327-3d0397fc0c97
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=a8dbbe34-bf03-4140-b327-3d0397fc0c97 ro recovery nomodeset persistent
        initrd /boot/initrd.img-3.16.0-30-generic
    }
}
 
menuentry 'elementary OS Luna (0.2.1) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
    else
      search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    fi
    linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-77-generic-pae
}
submenu 'Advanced options for elementary OS Luna (0.2.1) (on /dev/sda7)' $menuentry_id_option 'osprober-gnulinux-advanced-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
}
 
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
 
=================== sda11: Location of files loaded by Grub: ===================
 
           GiB - GB             File                                 Fragment(s)
 
 147.158172607 = 158.009884672  grub.cfg                                       1
 
========================== sda12/boot/grub/grub.cfg: ===========================
 
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
set root='hd0,msdos12'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
else
  search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
fi
    font="/usr/share/grub/unicode.pf2"
fi
 
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=nb_NO
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
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-37-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    echo    'Loading Linux 3.13.0-37-generic ...'
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-37-generic
}
submenu "Previous Linux versions" {
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    echo    'Loading Linux 3.13.0-24-generic ...'
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-24-generic
}
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-f05c536c-ae78-4105-a79f-970479b8483e' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
    else
      search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
    fi
    linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
    initrd /boot/initrd.img-3.16.0-30-generic
}
submenu 'Advanced options for Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' $menuentry_id_option 'osprober-gnulinux-advanced-f05c536c-ae78-4105-a79f-970479b8483e' {
    menuentry 'Ubuntu (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic-root=UUID=f05c536c-ae78-4105-a79f-970479b8483e  ro recovery nomodeset persistent-f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro recovery nomodeset persistent
        initrd /boot/initrd.img-3.16.0-30-generic
    }
}
 
menuentry 'Linux Mint 17.1 Rebecca (17.1) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e6a43606-8ccc-46ff-a228-e5da106d064d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos14'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
    else
      search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
    fi
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
submenu 'Advanced options for Linux Mint 17.1 Rebecca (17.1) (on /dev/sda14)' $menuentry_id_option 'osprober-gnulinux-advanced-e6a43606-8ccc-46ff-a228-e5da106d064d' {
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda14) (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--e6a43606-8ccc-46ff-a228-e5da106d064d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos14'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
        else
          search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda14) -- recovery mode (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d  ro recovery nomodeset-e6a43606-8ccc-46ff-a228-e5da106d064d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos14'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
        else
          search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-37-generic
    }
}
 
menuentry 'elementary OS Luna (0.2.1) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
    else
      search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    fi
    linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-77-generic-pae
}
submenu 'Advanced options for elementary OS Luna (0.2.1) (on /dev/sda7)' $menuentry_id_option 'osprober-gnulinux-advanced-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
}
 
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
 
=============================== sda12/etc/fstab: ===============================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda12 during installation
UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c3a9a1f2-9cea-4211-aa29-dc2b60875646 none            swap    sw              0       0
# Nedlastinger
# /Nedlastninger was on /dev/sda8 during installation
# Skrivebord
# /Skrivebord was on /dev/sda11 during installation
# Filmer
# /Filmer was on /dev/sda10 during installation
# Bilder
# /Bilder was on /dev/sda9 during installation
 
UUID=5F7C6EE663BE4C43 /home/seb/Videoklipp ntfs errors=remount-ro,x-gvfs-show 0 1
UUID=27AB008A2BBCB66A /home/seb/Bilder ntfs errors=remount-ro,x-gvfs-show 0 1
UUID=2E5B49DA222B6E51 /home/seb/Nedlastinger ntfs errors=remount-ro,x-gvfs-show 0 1
UUID=0692210d-ad42-4a02-b1f3-f98c1a5956cf /home/seb/Skrivebord ext4 errors=remount-ro 0 1
--------------------------------------------------------------------------------
 
=================== sda12: Location of files loaded by Grub: ===================
 
           GiB - GB             File                                 Fragment(s)
 
  26.721187592 = 28.691656704   boot/grub/grub.cfg                             1
  26.739784241 = 28.711624704   boot/grub/i386-pc/core.img                     1
  38.335460663 = 41.162387456   boot/vmlinuz-3.13.0-24-generic                 1
  26.050334930 = 27.971334144   boot/vmlinuz-3.13.0-37-generic                 1
  26.050334930 = 27.971334144   vmlinuz                                        1
  38.335460663 = 41.162387456   vmlinuz.old                                    1
  27.536613464 = 29.567213568   boot/initrd.img-3.13.0-24-generic              2
  23.427757263 = 25.155362816   boot/initrd.img-3.13.0-37-generic              4
  23.427757263 = 25.155362816   initrd.img                                     4
  27.536613464 = 29.567213568   initrd.img.old                                 2
 
========================== sda13/boot/grub/grub.cfg: ===========================
 
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
   set default="${saved_entry}"
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
set root='hd0,msdos13'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
else
  search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
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
insmod part_msdos
insmod ntfs
set root='hd0,msdos9'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos9 --hint-efi=hd0,msdos9 --hint-baremetal=ahci0,msdos9  27AB008A2BBCB66A
else
  search --no-floppy --fs-uuid --set=root 27AB008A2BBCB66A
fi
insmod jpeg
if background_image /wp/space/vtgkU.jpg; then
  set color_normal=light-gray/black
  set color_highlight=cyan/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30,0; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###
 
### BEGIN /etc/grub.d/10_linux_proxy ###
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
 
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f05c536c-ae78-4105-a79f-970479b8483e' {
    recordfail
    savedefault
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
    else
      search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
    fi
    linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-30-generic
}
### END /etc/grub.d/10_linux_proxy ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/30_os-prober_proxy ###
 
 
 
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
menuentry "elementary OS Luna" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
    else
      search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    fi
    linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-77-generic-pae
}
menuentry "Mint 17.1 Rebecca" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a34ef865-6684-48ff-afb5-a846a61f4c00' {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
### END /etc/grub.d/30_os-prober_proxy ###
 
### BEGIN /etc/grub.d/31_linux_proxy ###
submenu "Annet"{
submenu "Advanced options for Linux Mint 17.1 Rebecca (17.1) (on /dev/sda14)"{
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda14) (on /dev/sda14)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--e6a43606-8ccc-46ff-a228-e5da106d064d' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos14'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
        else
          search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda14) -- recovery mode (on /dev/sda14)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d  ro recovery nomodeset-e6a43606-8ccc-46ff-a228-e5da106d064d' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos14'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
        else
          search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-37-generic
}
}
submenu "Advanced options for Linux Mint 17.1 Rebecca (17.1) (on /dev/sda12)"{
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--a34ef865-6684-48ff-afb5-a846a61f4c00' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) -- recovery mode (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00  ro recovery nomodeset-a34ef865-6684-48ff-afb5-a846a61f4c00' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-37-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-24-generic--a34ef865-6684-48ff-afb5-a846a61f4c00' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) -- recovery mode (on /dev/sda12)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-24-generic-root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00  ro recovery nomodeset-a34ef865-6684-48ff-afb5-a846a61f4c00' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-24-generic
}
}
submenu "Advanced options for elementary OS Luna (0.2.1) (on /dev/sda7)"{
menuentry "elementary OS, with Linux 3.2.0-77-generic-pae (on /dev/sda7)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-77-generic-pae
}
menuentry "elementary OS, with Linux 3.2.0-77-generic-pae (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-77-generic-pae
}
menuentry "elementary OS, with Linux 3.2.0-51-generic-pae (on /dev/sda7)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-51-generic-pae
}
menuentry "elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        savedefault
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-51-generic-pae
}
}
submenu "Advanced options for Ubuntu"{
menuentry "Ubuntu, with Linux 3.16.0-30-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-f05c536c-ae78-4105-a79f-970479b8483e' {
        recordfail
    savedefault
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
}
menuentry "Ubuntu, with Linux 3.16.0-30-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-f05c536c-ae78-4105-a79f-970479b8483e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro recovery nomodeset persistent
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
}
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
    else
      search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
    else
      search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
    fi
    knetbsd    /boot/memtest86+.elf
}
}
### END /etc/grub.d/31_linux_proxy ###
 
### BEGIN /etc/grub.d/32_os-prober_proxy ###
menuentry "testmint" --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-e6a43606-8ccc-46ff-a228-e5da106d064d' {
    savedefault
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos14'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos14 --hint-efi=hd0,msdos14 --hint-baremetal=ahci0,msdos14  e6a43606-8ccc-46ff-a228-e5da106d064d
    else
      search --no-floppy --fs-uuid --set=root e6a43606-8ccc-46ff-a228-e5da106d064d
    fi
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=e6a43606-8ccc-46ff-a228-e5da106d064d ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
### END /etc/grub.d/32_os-prober_proxy ###
 
### BEGIN /etc/grub.d/33_uefi-firmware ###
### END /etc/grub.d/33_uefi-firmware ###
 
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
 
=============================== sda13/etc/fstab: ===============================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda13 during installation
UUID=f05c536c-ae78-4105-a79f-970479b8483e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c3a9a1f2-9cea-4211-aa29-dc2b60875646 none            swap    sw              0       0
LABEL=Nedlastninger /home/seb/Downloads auto nosuid,nodev,nofail 0 0
LABEL=Bilder /home/seb/Pictures auto nosuid,nodev,nofail 0 0
LABEL=Filmer /home/seb/Videos auto nosuid,nodev,nofail 0 0
LABEL=Skrivebord /home/seb/Desktop auto nosuid,nodev,nofail 0 0
--------------------------------------------------------------------------------
 
=================== sda13: Location of files loaded by Grub: ===================
 
           GiB - GB             File                                 Fragment(s)
 
  43.458698273 = 46.663421952   boot/grub/grub.cfg                             1
  44.091983795 = 47.343407104   boot/grub/i386-pc/core.img                     1
  44.086414337 = 47.337426944   boot/vmlinuz-3.16.0-30-generic                 1
  44.086414337 = 47.337426944   vmlinuz                                        1
  40.787273407 = 43.795001344   boot/initrd.img-3.16.0-30-generic              2
  40.787273407 = 43.795001344   initrd.img                                     2
 
========================== sda15/boot/grub/grub.cfg: ===========================
 
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
set root='hd0,msdos15'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  98ebd55a-46b5-4515-bb01-3bc35aad6ca8
else
  search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
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
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda15)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos15'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    else
      search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    fi
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=98ebd55a-46b5-4515-bb01-3bc35aad6ca8 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-37-generic
}
menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda15) -- recovery mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos15'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    else
      search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    fi
    echo    'Loading Linux 3.13.0-37-generic ...'
    linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=98ebd55a-46b5-4515-bb01-3bc35aad6ca8 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.13.0-37-generic
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos15'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    else
      search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos15'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos15 --hint-efi=hd0,msdos15 --hint-baremetal=ahci0,msdos15  98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    else
      search --no-floppy --fs-uuid --set=root 98ebd55a-46b5-4515-bb01-3bc35aad6ca8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Linux Mint 17.1 Rebecca (17.1) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a34ef865-6684-48ff-afb5-a846a61f4c00' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos12'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
    else
      search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
    fi
    linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.13.0-37-generic
}
submenu 'Advanced options for Linux Mint 17.1 Rebecca (17.1) (on /dev/sda12)' $menuentry_id_option 'osprober-gnulinux-advanced-a34ef865-6684-48ff-afb5-a846a61f4c00' {
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic--a34ef865-6684-48ff-afb5-a846a61f4c00' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-37-generic (/dev/sda12) -- recovery mode (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-37-generic-root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00  ro recovery nomodeset-a34ef865-6684-48ff-afb5-a846a61f4c00' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-37-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-24-generic--a34ef865-6684-48ff-afb5-a846a61f4c00' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Linux Mint 17.1 Cinnamon 64-bit, 3.13.0-24-generic (/dev/sda12) -- recovery mode (on /dev/sda12)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.13.0-24-generic-root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00  ro recovery nomodeset-a34ef865-6684-48ff-afb5-a846a61f4c00' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos12'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos12 --hint-efi=hd0,msdos12 --hint-baremetal=ahci0,msdos12  a34ef865-6684-48ff-afb5-a846a61f4c00
        else
          search --no-floppy --fs-uuid --set=root a34ef865-6684-48ff-afb5-a846a61f4c00
        fi
        linux /boot/vmlinuz-3.13.0-24-generic root=UUID=a34ef865-6684-48ff-afb5-a846a61f4c00 ro recovery nomodeset
        initrd /boot/initrd.img-3.13.0-24-generic
    }
}
 
menuentry 'Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-f05c536c-ae78-4105-a79f-970479b8483e' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos13'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
    else
      search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
    fi
    linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
    initrd /boot/initrd.img-3.16.0-30-generic
}
submenu 'Advanced options for Ubuntu 14.04.2 LTS (14.04) (on /dev/sda13)' $menuentry_id_option 'osprober-gnulinux-advanced-f05c536c-ae78-4105-a79f-970479b8483e' {
    menuentry 'Ubuntu (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic--f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro persistent quiet splash $vt_handoff
        initrd /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode) (on /dev/sda13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.16.0-30-generic-root=UUID=f05c536c-ae78-4105-a79f-970479b8483e  ro recovery nomodeset persistent-f05c536c-ae78-4105-a79f-970479b8483e' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos13'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos13 --hint-efi=hd0,msdos13 --hint-baremetal=ahci0,msdos13  f05c536c-ae78-4105-a79f-970479b8483e
        else
          search --no-floppy --fs-uuid --set=root f05c536c-ae78-4105-a79f-970479b8483e
        fi
        linux /boot/vmlinuz-3.16.0-30-generic root=UUID=f05c536c-ae78-4105-a79f-970479b8483e ro recovery nomodeset persistent
        initrd /boot/initrd.img-3.16.0-30-generic
    }
}
 
menuentry 'elementary OS Luna (0.2.1) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
    else
      search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
    fi
    linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-77-generic-pae
}
submenu 'Advanced options for elementary OS Luna (0.2.1) (on /dev/sda7)' $menuentry_id_option 'osprober-gnulinux-advanced-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-77-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-77-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-77-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae--c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
    menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-51-generic-pae-root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12  ro recovery nomodeset-c926aaf0-fccc-42a7-9e54-a5156c355c12' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  c926aaf0-fccc-42a7-9e54-a5156c355c12
        else
          search --no-floppy --fs-uuid --set=root c926aaf0-fccc-42a7-9e54-a5156c355c12
        fi
        linux /boot/vmlinuz-3.2.0-51-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-51-generic-pae
    }
}
 
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
 
=============================== sda15/etc/fstab: ===============================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda15 during installation
UUID=98ebd55a-46b5-4515-bb01-3bc35aad6ca8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda14 during installation
UUID=e27aaf5c-5d6d-4b6b-b087-a5c7a60a398f /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c3a9a1f2-9cea-4211-aa29-dc2b60875646 none            swap    sw              0       0
--------------------------------------------------------------------------------
 
=================== sda15: Location of files loaded by Grub: ===================
 
           GiB - GB             File                                 Fragment(s)
 
 139.384689331 = 149.663170560  boot/grub/grub.cfg                             1
 139.986682892 = 150.309556224  boot/grub/i386-pc/core.img                     1
 139.984329224 = 150.307028992  boot/vmlinuz-3.13.0-37-generic                 1
 139.984329224 = 150.307028992  vmlinuz                                        1
 135.548828125 = 145.544445952  boot/initrd.img-3.13.0-37-generic              3
 135.548828125 = 145.544445952  initrd.img                                     3
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
 
Unknown BootLoader on sda3
 
00000000  37 5d 14 45 84 61 48 ad  5a e1 c0 f2 12 1f fe e0  |7].E.aH.Z.......|
00000010  53 0c 87 23 2e 5d be 52  a0 b0 2e 99 01 00 f4 fa  |S..#.].R........|
00000020  7d 6e ad 6f dc f5 bb 14  87 4d f5 5b 26 fc 39 4c  |}n.o.....M.[&.9L|
00000030  db 5a 43 92 24 1c 3f ba  42 25 0a 48 54 c2 ad db  |.ZC.$.?.B%.HT...|
00000040  eb 08 29 3d 52 8f 2c b2  1f 08 f7 5d 1d 1d bb c3  |..)=R.,....]....|
00000050  6f e4 c2 2f f6 55 34 16  e3 06 df f8 c6 ab ce 52  |o../.U4........R|
00000060  92 81 df f9 cb f3 6e 8d  cb b9 17 05 cd 1a 97 69  |......n........i|
00000070  48 ef 4b 10 06 d4 ea 35  9a cd 06 07 0f 1e a6 d3  |H.K....5........|
00000080  e9 d0 e9 cc 3a 00 8f 08  5c 26 62 22 58 6c b4 ce  |....:...\&b"Xl..|
00000090  13 07 13 bb ff 64 da d5  c5 ac 7c e5 a7 b6 9e 0a  |.....d....|.....|
000000a0  5c 94 4d 31 c8 e8 be 33  06 69 74 f9 3e 99 89 df  |\.M1...3.it.>...|
000000b0  f7 79 dc db 6a c0 f1 50  18 44 a6 b1 d3 89 95 88  |.y..j..P.D......|
000000c0  ac e6 5a 08 e7 43 62 ca  33 24 26 cc a8 49 45 50  |..Z..Cb.3$&..IEP|
000000d0  7e 31 6c 6d 6f 71 ed fa  75 8e ae 1c c9 26 3b 08  |~1lmoq..u....&;.|
000000e0  02 ae 5d bb c2 1b 67 ce  10 04 01 1f fb d8 c7 38  |..]...g........8|
000000f0  7e e2 f8 fe 2c 82 70 3f  a5 f3 fb e8 b2 eb 96 2b  |~...,.p?.......+|
00000100  09 c3 80 28 0a 91 32 20  0a 43 cf 69 2f 41 e6 56  |...(..2 .C.i/A.V|
00000110  4a c6 3f 97 86 8d a7 14  06 b5 da 6d 4e ac ad a2  |J.?........mN...|
00000120  75 c2 8b 2f be c4 a5 4b  97 18 0c 86 24 49 2e 08  |u../...K....$I..|
00000130  81 94 2c 2e 2e f2 ec 07  9f c6 1a eb 94 80 ef f9  |..,.............|
00000140  e7 ae ad 18 6c 32 dc 5e  5f 67 38 2e b7 f7 ba eb  |....l2.^_g8.....|
00000150  b0 b9 c0 a7 b1 0e 97 c2  32 d9 7d 5a 5d 5b 45 c5  |........2.}Z][E.|
00000160  31 dd 7e 0f 15 c7 19 18  87 c0 85 5b b4 cd d5 b5  |1.~........[....|
00000170  9b 86 74 69 e5 c2 9f 22  39 8b f3 7d ec e8 11 5e  |..ti..."9..}...^|
00000180  fc fa d7 39 7a e2 04 bd  61 df 29 57 df b8 54 f8  |...9z...a.)W..T.|
00000190  0d 21 7d 9c ba 84 19 cc  36 6d 17 ee 7f 3b 82 52  |.!}.....6m...;.R|
000001a0  27 d4 52 4a a2 8a c3 63  58 ab a7 b4 f9 2e 6c 1e  |'.RJ...cX.....l.|
000001b0  3a fd db e3 0a 8a eb cc  47 fe f7 29 0f 55 00 fe  |:.......G..).U..|
000001c0  ff ff 83 fe ff ff 02 d0  5e 1c 00 80 9d 00 00 fe  |........^.......|
000001d0  ff ff 05 fe ff ff b4 ad  5b 1c 4e 1a 03 00 00 00  |........[.N.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
 
 
ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-03-21__15h35 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 4ppa33
boot-repair is executed in installed-session (elementary OS Luna, luna, elementary OS, i686)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.2.0-77-generic-pae root=UUID=c926aaf0-fccc-42a7-9e54-a5156c355c12 ro quiet splash vt.handoff=7
 
=================== os-prober:
/dev/sda7:The OS now in use - elementary OS Luna CurrentSession:linux
/dev/sda12:Linux Mint 17.1 Rebecca (17.1):LinuxMint:linux
/dev/sda13:Ubuntu 14.04.2 LTS (14.04):Ubuntu:linux
/dev/sda15:Linux Mint 17.1 Rebecca (17.1):LinuxMint1:linux
 
=================== blkid:
/dev/sda1: LABEL="*** me pls" UUID="d0978431-05e6-440a-bc90-6ac579758dcb" TYPE="ext4"
/dev/sda5: LABEL="Shiet" UUID="34cd7037-85d8-4212-a8d6-e5e7bc0373f5" TYPE="ext4"
/dev/sda6: UUID="c3a9a1f2-9cea-4211-aa29-dc2b60875646" TYPE="swap"
/dev/sda7: LABEL="Elementary" UUID="c926aaf0-fccc-42a7-9e54-a5156c355c12" TYPE="ext4"
/dev/sda8: LABEL="Nedlastninger" UUID="2E5B49DA222B6E51" TYPE="ntfs"
/dev/sda9: LABEL="Bilder" UUID="27AB008A2BBCB66A" TYPE="ntfs"
/dev/sda10: LABEL="Filmer" UUID="5F7C6EE663BE4C43" TYPE="ntfs"
/dev/sda11: LABEL="Skrivebord" UUID="0692210d-ad42-4a02-b1f3-f98c1a5956cf" TYPE="ext4"
/dev/sda12: LABEL="Mint" UUID="a34ef865-6684-48ff-afb5-a846a61f4c00" TYPE="ext4"
/dev/sda13: LABEL="Ubuntu" UUID="f05c536c-ae78-4105-a79f-970479b8483e" TYPE="ext4"
/dev/sda14: UUID="e27aaf5c-5d6d-4b6b-b087-a5c7a60a398f" TYPE="ext4"
/dev/sda15: UUID="98ebd55a-46b5-4515-bb01-3bc35aad6ca8" TYPE="ext4"
 
 
1 disks with OS, 4 OS : 4 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
 
=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Mar  8 12:54 grub.d
total 56
-rwxr-xr-x 1 root root 7806 Sep 17  2014 00_header
-rwxr-xr-x 1 root root 5522 Jul 20  2013 05_debian_theme
-rwxr-xr-x 1 root root 7877 Sep 17  2014 10_linux
-rwxr-xr-x 1 root root 6449 Sep 17  2014 20_linux_xen
-rwxr-xr-x 1 root root 6675 Sep 17  2014 30_os-prober
-rwxr-xr-x 1 root root 1388 Jul 20  2013 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jul 20  2013 40_custom
-rwxr-xr-x 1 root root   95 Jul 20  2013 41_custom
-rw-r--r-- 1 root root  483 Jul 20  2013 README
 
 
 
 
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
 
 
 
 
=================== sda12/etc/grub.d/ :
drwxr-xr-x  3 root root         4096 Mar 21 00:47 grub.d
total 92
-rwxr-xr-x 1 root root  9424 Apr 11  2014 00_header
-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme
-rwxr-xr-x 1 root root  1180 Oct 25 13:17 06_mint_theme
-rwxr-xr-x 1 root root  7500 Mar 21 15:12 10_linux
-rwxr-xr-x 1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x 1 root root 10412 Apr 11  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11  2014 40_custom
-rwxr-xr-x 1 root root   216 Apr 11  2014 41_custom
drwxr-xr-x 4 root root  4096 Mar  8 23:51 backup
-rw-r--r-- 1 root root   483 Apr 11  2014 README
 
 
 
 
=================== sda12/etc/default/grub :
 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
 
GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
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
 
 
 
 
=================== sda13/etc/grub.d/ :
drwxr-xr-x  5 root root        4096 Mar 21 14:00 grub.d
total 88
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rw-r--r-- 1 root root  1077 Mar 21 12:14 10_linux_proxy
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rw-r--r-- 1 root root  2753 Mar 21 12:14 30_os-prober_proxy
-rw-r--r-- 1 root root  3570 Mar 21 12:14 31_linux_proxy
-rwxr-xr-x 1 root root  2706 Mar 21 12:14 32_os-prober_proxy
-rwxr-xr-x 1 root root  1416 May 15  2014 33_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
drwxr-xr-x 4 root root  4096 Mar 18 12:38 backup
drwxr-xr-x 2 root root  4096 Mar 18 12:38 bin
-rwxr-xr-x 1 root root    46 Mar 21 14:00 LS_linux
-rwxr-xr-x 1 root root    51 Mar 21 14:00 LS_memtest86+
-rwxr-xr-x 1 root root    50 Mar 21 14:00 LS_os-prober
drwxr-xr-x 2 root root  4096 Mar 21 12:14 proxifiedScripts
-rw-r--r-- 1 root root   483 May 15  2014 README
 
 
 
 
=================== sda13/etc/default/grub :
 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
 
GRUB_DEFAULT="saved"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="persistent"
 
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
 
export GRUB_MENU_PICTURE="/home/seb/Pictures/wp/space/vtgkU.jpg"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="cyan/black"
GRUB_SAVEDEFAULT="true"
#GRUB_DISABLE_OS_PROBER="false"
 
 
 
=================== sda13saved_entry=osprober-gnulinux-simple-a34ef865-6684-48ff-afb5-a846a61f4c00/grub/grubenv :
saved_entry=osprober-gnulinux-simple-a34ef865-6684-48ff-afb5-a846a61f4c00
 
 
 
 
=================== sda15/etc/grub.d/ :
drwxr-xr-x  2 root root         4096 Nov 26 23:46 grub.d
total 88
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root  1180 Oct 25 13:17 06_mint_theme
-rwxr-xr-x 1 root root  7500 Nov 26 23:44 10_linux
-rwxr-xr-x 1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README
 
 
 
 
=================== sda15/etc/default/grub :
 
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
This installed-session is not EFI-compatible.
SecureBoot disabled.
 
 
=================== PARTITIONS & DISKS:
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,     32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    not-far,    .
sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /felles.
sda8    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /home/seb/Downloads.
sda9    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /home/seb/Pictures.
sda10    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /home/seb/Videos.
sda11    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda11.
sda12    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,     64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda12.
sda13    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,     32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    customized,    not-far,    /mnt/boot-sav/sda13.
sda14    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda14.
sda15    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,     64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda15.
 
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
 
 
=================== parted -l:
 
Model: ATA WDC WD2500BEKT-6 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End     Size    Type      File system     Flags
1      1049kB  1074MB  1073MB  primary   ext4            boot
3      1075MB  250GB   249GB   extended
7      1075MB  22.0GB  21.0GB  logical   ext4
12      22.0GB  42.0GB  20.0GB  logical   ext4
13      42.0GB  63.6GB  21.6GB  logical   ext4
15      143GB   153GB   10.2GB  logical   ext4
14      153GB   158GB   4900MB  logical   ext4
11      158GB   170GB   12.6GB  logical   ext4
10      170GB   191GB   21.0GB  logical   ntfs
9      191GB   202GB   10.5GB  logical   ntfs
8      202GB   245GB   42.7GB  logical   ntfs
6      245GB   245GB   104MB   logical   linux-swap(v1)
5      245GB   250GB   5285MB  logical   ext4
 
=================== parted -lm:
 
BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA WDC WD2500BEKT-6;
1:1049kB:1074MB:1073MB:ext4::boot;
3:1075MB:250GB:249GB:::;
7:1075MB:22.0GB:21.0GB:ext4::;
12:22.0GB:42.0GB:20.0GB:ext4::;
13:42.0GB:63.6GB:21.6GB:ext4::;
15:143GB:153GB:10.2GB:ext4::;
14:153GB:158GB:4900MB:ext4::;
11:158GB:170GB:12.6GB:ext4::;
10:170GB:191GB:21.0GB:ntfs::;
9:191GB:202GB:10.5GB:ntfs::;
8:202GB:245GB:42.7GB:ntfs::;
6:245GB:245GB:104MB:linux-swap(v1)::;
5:245GB:250GB:5285MB:ext4::;
 
=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL     MODEL    UUID
sda   disk        232.9G           WDC WD25
sda1  part ext4    1023M *** me pls
d0978431-05e6-440a-bc90-6ac579758dcb
sda3  part            1K
sda5  part ext4     4.9G Shiet              34cd7037-85d8-4212-a8d6-e5e7bc0373f5
sda6  part swap      99M                    c3a9a1f2-9cea-4211-aa29-dc2b60875646
sda7  part ext4    19.5G Elementary
c926aaf0-fccc-42a7-9e54-a5156c355c12
sda8  part ntfs    39.8G Nedlastninger
2E5B49DA222B6E51
sda9  part ntfs     9.8G Bilder             27AB008A2BBCB66A
sda10 part ntfs    19.5G Filmer             5F7C6EE663BE4C43
sda11 part ext4    11.8G Skrivebord
0692210d-ad42-4a02-b1f3-f98c1a5956cf
sda12 part ext4    18.6G Mint               a34ef865-6684-48ff-afb5-a846a61f4c00
sda13 part ext4    20.1G Ubuntu             f05c536c-ae78-4105-a79f-970479b8483e
sda14 part ext4     4.6G                    e27aaf5c-5d6d-4b6b-b087-a5c7a60a398f
sda15 part ext4     9.5G                    98ebd55a-46b5-4515-bb01-3bc35aad6ca8
 
KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda3     1  0  0
sda5     1  0  0         /felles
sda6     1  0  0         [SWAP]
sda7     1  0  0         /
sda8     1  0  0         /home/seb/Downloads
sda9     1  0  0         /home/seb/Pictures
sda10    1  0  0         /home/seb/Videos
sda11    1  0  0         /mnt/boot-sav/sda11
sda12    1  0  0         /mnt/boot-sav/sda12
sda13    1  0  0         /mnt/boot-sav/sda13
sda14    1  0  0         /mnt/boot-sav/sda14
sda15    1  0  0         /mnt/boot-sav/sda15
 
 
=================== mount:
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda8 on /home/seb/Downloads type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9 on /home/seb/Pictures type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda10 on /home/seb/Videos type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /felles type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/seb/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=seb)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
/dev/sda11 on /mnt/boot-sav/sda11 type ext4 (rw)
/dev/sda12 on /mnt/boot-sav/sda12 type ext4 (rw)
/dev/sda13 on /mnt/boot-sav/sda13 type ext4 (rw)
/dev/sda14 on /mnt/boot-sav/sda14 type ext4 (rw)
/dev/sda15 on /mnt/boot-sav/sda15 type ext4 (rw)
 
 
=================== ls:
/sys/block/sda (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro sda1 sda10 sda11 sda12 sda13 sda14 sda15 sda3 sda5  sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/dev (filtered):   agpgart autofs block bsg btrfs-control bus char console core cpu  cpu_dma_latency disk dri ecryptfs fb0 fd freefall full fuse hpet input  kmsg log mapper mcelog mei mem net network_latency network_throughput  null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1  sda10 sda11 sda12 sda13 sda14 sda15 sda3 sda5 sda6 sda7 sda8 sda9 sg0  shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1  usbmon2 v4l vga_arbiter video0 zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory
 
=================== hexdump -n512 -C /dev/sda8
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 82 17  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 07 f9 04 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  7f 21 14 00 00 00 00 00  |.........!......|
00000040  f6 00 00 00 01 00 00 00  51 6e 2b 22 da 49 5b 2e  |........Qn+".I[.|
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
 
=================== hexdump -n512 -C /dev/sda9
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 4a 16  |........?....0J.|
00000020  00 00 00 00 80 00 80 00  ff 6f 38 01 00 00 00 00  |.........o8.....|
00000030  04 00 00 00 00 00 00 00  ff 86 13 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  6a b6 bc 2b 8a 00 ab 27  |........j..+...'|
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
 
=================== hexdump -n512 -C /dev/sda10
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 38 d9 13  |........?....8..|
00000020  00 00 00 00 80 00 80 00  ff ef 70 02 00 00 00 00  |..........p.....|
00000030  04 00 00 00 00 00 00 00  ff 0e 27 00 00 00 00 00  |..........'.....|
00000040  f6 00 00 00 01 00 00 00  43 4c be 63 e6 6e 7c 5f  |........CL.c.n|_|
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
 
=================== df -Th:
 
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4       20G  7.1G   12G  39% /
udev           devtmpfs  1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs     382M  912K  381M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G  224K  1.9G   1% /run/shm
/dev/sda8      fuseblk    40G   20G   20G  51% /home/seb/Downloads
/dev/sda9      fuseblk   9.8G   77M  9.7G   1% /home/seb/Pictures
/dev/sda10     fuseblk    20G  566M   19G   3% /home/seb/Videos
/dev/sda5      ext4      4.9G  282M  4.4G   6% /felles
/dev/sda1      ext4     1007M   18M  939M   2% /mnt/boot-sav/sda1
/dev/sda11     ext4       12G  2.3G  8.8G  21% /mnt/boot-sav/sda11
/dev/sda12     ext4       19G  7.6G  9.9G  44% /mnt/boot-sav/sda12
/dev/sda13     ext4       20G  4.0G   15G  22% /mnt/boot-sav/sda13
/dev/sda14     ext4      4.5G  149M  4.2G   4% /mnt/boot-sav/sda14
/dev/sda15     ext4      9.4G  4.5G  4.5G  50% /mnt/boot-sav/sda15
 
=================== fdisk -l:
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9cbb2d23
 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2097151     1047552   83  Linux
/dev/sda3         2099198   488396799   243148801    5  Extended
/dev/sda5       478074880   488396799     5160960   83  Linux
/dev/sda6       477870080   478072831      101376   82  Linux swap / Solaris
/dev/sda7         2099200    43060137    20480469   83  Linux
/dev/sda8       394438656   477868031    41714688    7  HPFS/NTFS/exFAT
/dev/sda9       373960704   394436607    10237952    7  HPFS/NTFS/exFAT
/dev/sda10      333002752   373958655    20477952    7  HPFS/NTFS/exFAT
/dev/sda11      308344832   333000703    12327936   83  Linux
/dev/sda12       43061248    82122751    19530752   83  Linux
/dev/sda13       82124800   124251753    21063477   83  Linux
/dev/sda14      298772480   308342792     4785156+  83  Linux
/dev/sda15      278876160   298770691     9947266   83  Linux
 
Partition table entries are not in disk order
 
 
 
 
=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda7 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s
 
 
=================== User settings
The settings chosen by the user will not act on the boot.


```

---

### Post by Keith_Helms on 2015-03-21
The problem I have with grub is that every Linux install seems to  install its own copy of grub and point the master boot record to  itself.  There are 2 pieces to grub - the master boot record (one per hard drive) and the  config file (one per each Linux OS installed).  The grub install changes the master boot record to point  to the partition you just installed a Linux OS in.  In that partition,  there is a file named /boot/grub/grub.cfg that contains the menu of OSes, kernel versions, recovery options, and memory tests that you  see when you start your system.   That grub.cfg file is generated by the  update-grub script.

The problem is that whichever OS you  installed last is the one pointed to by the MBR and its config file is  the one that is used.  If you update one of your other OSes, such as to  install a newer kernel version during maintenance, that partition's  grub.cfg will be updated, but not the one that you're booting off of.   The result would be that you won't be able to boot that new kernel until  you run update-grub under the OS that is pointed to by the MBR.  Clear  as mud?

Anyway, the solution is to figure out which of your OS  installs you want to "own" the boot process.  Each time you install  another OS, go back and boot that "boot owner" OS, open a command line  window, and run the following command:
```
sudo grub-install /dev/sda* [or sdb/c/whichever drive your're booting from]*
```

That will point grub back to the OS partition you want it to and away from the new OS that hijacked it.

Whenever you install or remove a kernel version in one of your other OSes, boot back into the "boot owner" OS and run the following command.
```
sudo update-grub
```

That will update your grub menu to pick up the kernel change(s) to other OSes.

It sounds like you may have your system running again, but if not, you can use the following instructions to get grub installed and pointed to the desired partition:

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by Dina_Eaton on 2015-03-22
Thank you for clearing the mud! I got my grub config back with this :)

---

### Post by oldfred on 2015-03-23
Especially with several Linux installs, best to manage grub.

With at least Debian based version, there is a link to the most current kernel in the / of the install.
Normally you run the grub update in the install you are in, then have to run the grub update in the install used to boot to find new kernel entry in grub or two updates.
But you can change to only boot the link which will always be the most current kernel.
And turn off os-prober so you only have the manual entries using the links.
When installing a new copy, use Something Else and change install of grub to partition. Normally installing grub to partition is not recommended, but there does not seem to be an option not to install, so we install to a partition more as a throw-away.
       
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

And every install may update grub in the MBR on a major grub update. Best to prevent that, so only your main working install updates.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

