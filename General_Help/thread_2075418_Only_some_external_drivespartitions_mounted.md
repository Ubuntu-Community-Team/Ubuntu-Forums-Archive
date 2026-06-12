---
title: "Only some external drives/partitions mounted"
date: 2012-10-23
forum: General Help
---

### Post by hwttdz on 2012-10-23
I'm trying to get ubuntu/xfce to mount drives when I plug them in.  In testing I have a drive that has 4 partitions on it.  When I plug the drive in two of the four partitions are mounted, weirdly it's not consistent which two.  

I would like it to mount all 4 partitions.  Any ideas on where to begin?

---

### Post by oldfred on 2012-10-23
Post fstab. Are you automounting or just using Nautilus?

 sudo cat /etc/fstab

And post details:

sudo blkid -c /dev/null -o list

---

### Post by hwttdz on 2012-10-23
```
\grep -Ev "^#"  /etc/fstab

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d /               ext4    relatime,errors=remount-ro 0       1
UUID=9ea31eb6-bf99-4494-8528-1cc30acc9d2d /boot           ext4    noatime         0       2
UUID=c6b467dd-9795-4711-ae0a-c1333b7fe3c0 none            swap    sw              0       0
UUID=a89332c8-8687-44f6-96d1-98194a562dce /home           ext4    relatime,errors=remount-ro,user_xattr,nodev,nosuid 0       2

UUID=27d5474f-3c74-4409-b513-4c162f1ad795 /usr            ext4    relatime,errors=remount-ro 0       2
UUID=49f3dcd9-6ead-4093-b5ce-dd5486097fbf /var            ext4    relatime,errors=remount-ro 0       2
UUID=dad8d46a-bde6-44a0-b6df-b89149a22b5a /plop_build     ext4    relatime,errors=remount-ro,nodev,nosuid 0       2

UUID=244d2c6e-62f2-4a4e-ad64-15387aaf97b3 /media/244d2c6e-62f2-4a   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2
UUID=a9b5e73b-2db2-40ee-91d3-029f0b537a3a /media/a9b5e73b-2db2-40   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2
UUID=a139bbec-0b93-40eb-af66-65104ab15f47 /media/a139bbec-0b93-40   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2
```

I'm automounting using thunar-volman.

So the two partitions that mounted this time are sdh2 and sdh3, and I would like it to have also mounted sdh1 and sdh4.

```
device                                        fs_type         label            mount point                                       UUID
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                     ext4            boot             /boot                                             9ea31eb6-bf99-4494-8528-1cc30acc9d2d
/dev/sda2                                     swap                             <swap>                                            c6b467dd-9795-4711-ae0a-c1333b7fe3c0
/dev/sda3                                     ext4            root             /                                                 f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d
/dev/sdb1                                     ext4            49f3dcd9-6ead-40 /var                                              49f3dcd9-6ead-4093-b5ce-dd5486097fbf
/dev/sdb2                                     ext4            dad8d46a-bde6-44 /plop_build                                       dad8d46a-bde6-44a0-b6df-b89149a22b5a
/dev/sdb3                                     ext4            27d5474f-3c74-44 /usr                                              27d5474f-3c74-4409-b513-4c162f1ad795
/dev/sdb4                                     ext4            a9b5e73b-2db2-40 /media/a9b5e73b-2db2-40                           a9b5e73b-2db2-40ee-91d3-029f0b537a3a
/dev/sdc1                                     ext4            a89332c8-8687-44 /home                                             a89332c8-8687-44f6-96d1-98194a562dce
/dev/sdd1                                     ext4            a139bbec-0b93-40 /media/a139bbec-0b93-40                           a139bbec-0b93-40eb-af66-65104ab15f47
/dev/sde1                                     ext4            244d2c6e-62f2-4a /media/244d2c6e-62f2-4a                           244d2c6e-62f2-4a4e-ad64-15387aaf97b3
/dev/sdh1                                     ext4            88028ed3-3fb9-48 (not mounted)                                     88028ed3-3fb9-4876-9dcf-aafd74cb4c6f
/dev/sdh2                                     ext4            72139b73-8e12-4b /media/jbylund/72139b73-8e12-4b                   72139b73-8e12-4b44-b815-a7876c0cc774
/dev/sdh3                                     ext4            c2b89336-26dc-4a /media/jbylund/c2b89336-26dc-4a                   c2b89336-26dc-4af5-8b33-4b77dcc3e894
/dev/sdh4                                     ext4            08ea9f62-301d-49 (not mounted)                                     08ea9f62-301d-49ba-b377-d76df1e7ce86

```

---

### Post by hwttdz on 2012-10-23
And from dmesg:
```
[ 4718.286123] usb 2-1: >new high-speed USB device number 12 using ehci_hcd
[ 4718.435286] usb 2-1: >New USB device found, idVendor=152d, idProduct=2329
[ 4718.435291] usb 2-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 4718.435294] usb 2-1: >Product: USB to ATA/ATAPI Bridge
[ 4718.435297] usb 2-1: >Manufacturer: JMicron
[ 4718.435299] usb 2-1: >SerialNumber: 123279040000
[ 4718.436396] usb-storage 2-1:1.0: >Quirks match for vid 152d pid 2329: 8020
[ 4718.436435] scsi16 : usb-storage 2-1:1.0
[ 4719.434149] scsi 16:0:0:0: >Direct-Access     Corsair  Force GT              PQ: 0 ANSI: 2 CCS
[ 4719.435214] sd 16:0:0:0: >Attached scsi generic sg8 type 0
[ 4719.435695] sd 16:0:0:0: >[sdh] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[ 4719.436483] sd 16:0:0:0: >[sdh] Write Protect is off
[ 4719.436490] sd 16:0:0:0: >[sdh] Mode Sense: 34 00 00 00
[ 4719.437512] sd 16:0:0:0: >[sdh] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 4719.442367]  sdh: sdh1 sdh2 sdh3 sdh4
[ 4719.445225] sd 16:0:0:0: >[sdh] Attached SCSI disk
[ 4719.937377] EXT4-fs (sdh3): recovery complete
[ 4719.938018] EXT4-fs (sdh3): mounted filesystem with ordered data mode. Opts: (null)
[ 4720.591871] EXT4-fs (sdh2): recovery complete
[ 4720.592379] EXT4-fs (sdh2): mounted filesystem with ordered data mode. Opts: (null)
```

So weirdly sdh1 and sdh4 don't even show up in dmesg.

---

### Post by oldfred on 2012-10-24
I do not see issue either. If you mount with thunar do they then mount?

Is there any corruption in those partitions?

You could run bootinfoscript. It mounts and reports issues if it cannot mount. Some of the same info I already asked for, but it may show something.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by hwttdz on 2012-10-24
I can mount with thunar, by just opening up thunar and clicking on the semi-transparent drive icon.  I am hoping to eventually use a method like this to automatically import my photos when I plug a camera in, and just plugging a camera in is preferable to me to plugging in camera, mounting, opening photo program, importing.

The partitions are absolutely empty, containing only a lost+found each.

The only interesting bit from the bootinfo script I see is:
```
================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext4       (rw,noatime)
/dev/sda3        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdb1        /var                     ext4       (rw,relatime,errors=remount-ro)
/dev/sdb2        /plop_build              ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdb3        /usr                     ext4       (rw,relatime,errors=remount-ro)
/dev/sdb4        /media/a9b5e73b-2db2-40  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdc1        /home                    ext4       (rw,nosuid,nodev,relatime,errors=remount-ro,user_xattr)
/dev/sdd1        /media/a139bbec-0b93-40  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sde1        /media/244d2c6e-62f2-4a  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdh2        /media/jbylund/72139b73-8e12-4b ext4       (rw,nosuid,nodev,uhelper=udisks2)
```

This time it only mounted one at /media/jbylund/72139b73-8e12-4b.  I would like it to mount the other partitions of this drive in a similar fashion.


Results of bootinfo script:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdh.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /extlinux/extlinux.conf

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdh1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdh2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdh3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdh4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             976,896     5,859,327     4,882,432  82 Linux swap / Solaris
/dev/sda3           5,859,328    62,531,583    56,672,256  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    67,110,911    67,108,864  83 Linux
/dev/sdb2          67,110,912   134,219,775    67,108,864  83 Linux
/dev/sdb3         134,219,776   201,328,639    67,108,864  83 Linux
/dev/sdb4         201,328,640 3,907,028,991 3,705,700,352  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,250,263,039 1,250,260,992  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 3,907,028,991 3,907,026,944  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250261615 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048 1,250,260,991 1,250,258,944  83 Linux


Drive: sdh _____________________________________________________________________

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1               2,048    51,202,047    51,200,000  83 Linux
/dev/sdh2          51,202,048   102,402,047    51,200,000  83 Linux
/dev/sdh3         102,402,048   153,602,047    51,200,000  83 Linux
/dev/sdh4         153,602,048   234,440,703    80,838,656  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9ea31eb6-bf99-4494-8528-1cc30acc9d2d   ext4       boot
/dev/sda2        c6b467dd-9795-4711-ae0a-c1333b7fe3c0   swap       
/dev/sda3        f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d   ext4       root
/dev/sdb1        49f3dcd9-6ead-4093-b5ce-dd5486097fbf   ext4       49f3dcd9-6ead-40
/dev/sdb2        dad8d46a-bde6-44a0-b6df-b89149a22b5a   ext4       dad8d46a-bde6-44
/dev/sdb3        27d5474f-3c74-4409-b513-4c162f1ad795   ext4       27d5474f-3c74-44
/dev/sdb4        a9b5e73b-2db2-40ee-91d3-029f0b537a3a   ext4       a9b5e73b-2db2-40
/dev/sdc1        a89332c8-8687-44f6-96d1-98194a562dce   ext4       a89332c8-8687-44
/dev/sdd1        a139bbec-0b93-40eb-af66-65104ab15f47   ext4       a139bbec-0b93-40
/dev/sde1        244d2c6e-62f2-4a4e-ad64-15387aaf97b3   ext4       244d2c6e-62f2-4a
/dev/sdh1        88028ed3-3fb9-4876-9dcf-aafd74cb4c6f   ext4       88028ed3-3fb9-48
/dev/sdh2        72139b73-8e12-4b44-b815-a7876c0cc774   ext4       72139b73-8e12-4b
/dev/sdh3        c2b89336-26dc-4af5-8b33-4b77dcc3e894   ext4       c2b89336-26dc-4a
/dev/sdh4        08ea9f62-301d-49ba-b377-d76df1e7ce86   ext4       08ea9f62-301d-49

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext4       (rw,noatime)
/dev/sda3        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdb1        /var                     ext4       (rw,relatime,errors=remount-ro)
/dev/sdb2        /plop_build              ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdb3        /usr                     ext4       (rw,relatime,errors=remount-ro)
/dev/sdb4        /media/a9b5e73b-2db2-40  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdc1        /home                    ext4       (rw,nosuid,nodev,relatime,errors=remount-ro,user_xattr)
/dev/sdd1        /media/a139bbec-0b93-40  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sde1        /media/244d2c6e-62f2-4a  ext4       (rw,nosuid,nodev,relatime,errors=remount-ro)
/dev/sdh2        /media/jbylund/72139b73-8e12-4b ext4       (rw,nosuid,nodev,uhelper=udisks2)


============================= sda1/grub/grub.cfg: ==============================

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
set root='hd1,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  27d5474f-3c74-4409-b513-4c162f1ad795
else
  search --no-floppy --fs-uuid --set=root 27d5474f-3c74-4409-b513-4c162f1ad795
fi
    font="/share/grub/unicode.pf2"
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
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	else
	  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	fi
	linux	/vmlinuz-3.5.0-17-generic root=UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d ro   
	initrd	/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		else
		  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/vmlinuz-3.5.0-17-generic root=UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d ro   
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		else
		  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/vmlinuz-3.5.0-17-generic root=UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-advanced-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		else
		  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		fi
		echo	'Loading Linux 3.2.0-32-generic ...'
		linux	/vmlinuz-3.2.0-32-generic root=UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d ro   
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.2.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-recovery-f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d' {
	recordfail
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		else
		  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
		fi
		echo	'Loading Linux 3.2.0-32-generic ...'
		linux	/vmlinuz-3.2.0-32-generic root=UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.2.0-32-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	else
	  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	fi
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	else
	  search --no-floppy --fs-uuid --set=root 9ea31eb6-bf99-4494-8528-1cc30acc9d2d
	fi
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
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

========================= sda1/extlinux/extlinux.conf: =========================

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

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.145556450 = 0.156290048    grub/grub.cfg                                  1
   0.088664055 = 0.095202304    initrd.img-3.2.0-32-generic                    2
   0.144238472 = 0.154874880    initrd.img-3.5.0-17-generic                    4
   0.062244415 = 0.066834432    vmlinuz-3.2.0-32-generic                       1
   0.099504471 = 0.106842112    vmlinuz-3.5.0-17-generic                       1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

   0.067220688 = 0.072177664    extlinux/chain.c32                             1
   0.142259598 = 0.152750080    extlinux/extlinux.conf                         1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 extlinux/chain.c32                 :  COM32R module (v4.xx)

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
#!/bin/bash
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d /               ext4    relatime,errors=remount-ro 0       1
UUID=9ea31eb6-bf99-4494-8528-1cc30acc9d2d /boot           ext4    noatime         0       2
UUID=c6b467dd-9795-4711-ae0a-c1333b7fe3c0 none            swap    sw              0       0
UUID=a89332c8-8687-44f6-96d1-98194a562dce /home           ext4    relatime,errors=remount-ro,user_xattr,nodev,nosuid 0       2

# small extra partitions 32 gb each
UUID=27d5474f-3c74-4409-b513-4c162f1ad795 /usr            ext4    relatime,errors=remount-ro 0       2
UUID=49f3dcd9-6ead-4093-b5ce-dd5486097fbf /var            ext4    relatime,errors=remount-ro 0       2
UUID=dad8d46a-bde6-44a0-b6df-b89149a22b5a /plop_build     ext4    relatime,errors=remount-ro,nodev,nosuid 0       2

#media1
UUID=244d2c6e-62f2-4a4e-ad64-15387aaf97b3 /media/244d2c6e-62f2-4a   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2
UUID=a9b5e73b-2db2-40ee-91d3-029f0b537a3a /media/a9b5e73b-2db2-40   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2
UUID=a139bbec-0b93-40eb-af66-65104ab15f47 /media/a139bbec-0b93-40   ext4    relatime,errors=remount-ro,nodev,nosuid 0       2

#/dev/sdg1: LABEL="" UUID="" TYPE="ext4" 

#/dev/sdc1: LABEL="boot" UUID="9ea31eb6-bf99-4494-8528-1cc30acc9d2d" TYPE="ext4" 
#/dev/sdc2: UUID="c6b467dd-9795-4711-ae0a-c1333b7fe3c0" TYPE="swap" 
#/dev/sdc3: LABEL="root" UUID="f3f67ac8-3c3f-4ff6-87ac-2a161d0ee40d" TYPE="ext4" 
#/dev/sdd1: LABEL="ec5e0297-2471-41" UUID="ec5e0297-2471-41fd-b47e-447debf59782" TYPE="ext4" 
#/dev/sde1: LABEL="a89332c8-8687-44" UUID="a89332c8-8687-44f6-96d1-98194a562dce" TYPE="ext4" 
#/dev/sdf1: LABEL="a139bbec-0b93-40" UUID="a139bbec-0b93-40eb-af66-65104ab15f47" TYPE="ext4" 
#/dev/sdg1: LABEL="244d2c6e-62f2-4a" UUID="244d2c6e-62f2-4a4e-ad64-15387aaf97b3" TYPE="ext4" 

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.937207222 = 3.153802240    initrd.img                                     4
   2.937207222 = 3.153802240    initrd.img.old                                 4
   2.892473221 = 3.105769472    vmlinuz                                        1
   2.892473221 = 3.105769472    vmlinuz.old                                    1

============== sda3: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdf sdg
```

---

### Post by oldfred on 2012-10-24
Had you clicked on sdh2 before running script and not on other partitions. Have you tried copying a small file to those partitions?

Even with XP, I always remove camera card from camera and insert into a multi-card USB device. Then it auto mounts and I manually copy my photo as I want to organize in a different fashion than most photo apps.

---

### Post by hwttdz on 2012-10-24
> **oldfred said:**
> Had you clicked on sdh2 before running script and not on other partitions. Have you tried copying a small file to those partitions?

I had not.

> **oldfred said:**
> Even with XP, I always remove camera card from camera and insert into a multi-card USB device. Then it auto mounts and I manually copy my photo as I want to organize in a different fashion than most photo apps.

I think honeycrisp apples are superior to all other sorts of apples, they're deliciously crispy and sweet.  Really the only downside is that they're only available for a month or two in the fall, luckily that time is right now, so get em while they're hot.

---

