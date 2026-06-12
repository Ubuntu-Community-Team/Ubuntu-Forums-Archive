---
title: "bootup in low-res"
date: 2017-07-24
forum: General Help
---

### Post by ray field on 2017-07-24
for no apparent reason, my 16.04 desktop boots into low-resolution graphics. once I log in, my Unity session begins briefly, before I am thrown back out into the password screen. 

thinking I needed to specify a resolution in Grub, I tried to boot to the recovery menu and then drop down to a command prompt -- however, the session is very unstable, with lots of corruption, and I am unable to finish editing using nano.

the card is a GeForce GT 730 fwiw.

I also attempted using a BootRepair DVD without luck.

as a stopgap, from the initial Grub menu, I tried choosing an older kernel -- this works great (I am using that configuration right now). 

part of boot-info report attached.

-rafe t.

```

Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 8ddc873b-786d-4587-b1e2-f64c4a5b0e06 root hd0,msdos6 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 8ddc873b-786d-4587-b1e2-f64c4a5b0e06 root hd0,msdos6 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdd.
 => Grub2 (v2.00) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 8ddc873b-786d-4587-b1e2-f64c4a5b0e06 root hd0,msdos6 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdg and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 8ddc873b-786d-4587-b1e2-f64c4a5b0e06 root hd0,msdos6 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdd2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdd2 has 
                       1177341951 sectors, but according to the info from 
                       fdisk, it has 9767276543 sectors.
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046   283,201,535   283,199,490   5 Extended
/dev/sda5          87,891,968   283,201,535   195,309,568  83 Linux
/dev/sda6               2,048    87,891,967    87,889,920  83 Linux
/dev/sda2    *    283,201,536   468,860,927   185,659,392  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   406,333,439   406,331,392   7 NTFS / exFAT / HPFS
/dev/sdb2         406,333,440   812,414,975   406,081,536   5 Extended
/dev/sdb5         406,337,536   511,918,079   105,580,544  83 Linux
/dev/sdb3    *    812,414,976 3,907,028,991 3,094,614,016  83 Linux


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 1.8 TiB, 2000398933504 bytes, 3907029167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 3,907,029,166 3,907,027,119   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 4.6 TiB, 5000981077504 bytes, 9767541167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdd1                    34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdd2               264,192 9,767,540,735 9,767,276,544 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sde _____________________________________________________________________
Disk /dev/sde: 3.7 TiB, 4000787025920 bytes, 976754645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   976,754,644   976,752,597   7 NTFS / exFAT / HPFS


Drive: sdg _____________________________________________________________________
Disk /dev/sdg: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *          2,048 1,953,521,663 1,953,519,616  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/sda2        85161fdb-b9be-477d-9dcb-5d2b1e75401a   ext4       
/dev/sda5        91642d58-6713-4c18-8d2f-337bb0cd317e   ext4       
/dev/sda6        8ddc873b-786d-4587-b1e2-f64c4a5b0e06   ext4       
/dev/sdb1        27AD28C33FE93BF8                       ntfs       dozer
/dev/sdb3        0ec4fa1a-1e46-46c8-8f63-277cbfaa5cd0   ext4       whouse
/dev/sdb5        1fff218b-4c2f-42fb-9d8f-ae377a95a63a   swap       swap for 16.04
/dev/sdc1        7A2AC7282AC6E06D                       ntfs       Seagate Backup Plus Drive
/dev/sdd1                                                          
/dev/sdd2        0EB0049EB0048E81                       ntfs       Seagate Expansion Drive
/dev/sde1        30525A2F5259FA54                       ntfs       Seagate Expansion Drive
/dev/sdg1        1a003a3c-f1e7-4e5f-bcf8-d3455710098e   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 24 13:43 ata-Crucial_CT240M500SSD1_14010961196B -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-Crucial_CT240M500SSD1_14010961196B-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-Crucial_CT240M500SSD1_14010961196B-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-Crucial_CT240M500SSD1_14010961196B-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-Crucial_CT240M500SSD1_14010961196B-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Jul 23 23:53 ata-HL-DT-ST_BD-RE_WH14NS40_K9LCANH0752 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 24 13:43 ata-ST1000LM024_HN-M101MBB_S2TPJ9BC805623 -> ../../sdg
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST1000LM024_HN-M101MBB_S2TPJ9BC805623-part1 -> ../../sdg1
lrwxrwxrwx 1 root root  9 Jul 24 13:43 ata-ST2000DM006-2DM164_Z4Z834ZP -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST2000DM006-2DM164_Z4Z834ZP-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST2000DM006-2DM164_Z4Z834ZP-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST2000DM006-2DM164_Z4Z834ZP-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST2000DM006-2DM164_Z4Z834ZP-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Jul 24 13:43 ata-ST2000LM003_HN-M201RAD_S362JAFGB11064 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST2000LM003_HN-M201RAD_S362JAFGB11064-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul 24 13:43 ata-ST5000DM003-2FH18L_WCV01PTE -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST5000DM003-2FH18L_WCV01PTE-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 ata-ST5000DM003-2FH18L_WCV01PTE-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  9 Jul 23 23:53 usb-Mass_Storage_Device_125C20100726-0:0 -> ../../sdf
lrwxrwxrwx 1 root root  9 Jul 24 13:43 usb-Seagate_Expansion_Desk_NA4NC0K2-0:0 -> ../../sde
lrwxrwxrwx 1 root root 10 Jul 24 13:43 usb-Seagate_Expansion_Desk_NA4NC0K2-0:0-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Jul 24 13:43 wwn-0x50004cf2081d71dd -> ../../sdg
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x50004cf2081d71dd-part1 -> ../../sdg1
lrwxrwxrwx 1 root root  9 Jul 24 13:43 wwn-0x50004cf2114e69b7 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x50004cf2114e69b7-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul 24 13:43 wwn-0x5000c500a2e1b432 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a2e1b432-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a2e1b432-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a2e1b432-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a2e1b432-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Jul 24 13:43 wwn-0x5000c500a8979f53 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a8979f53-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x5000c500a8979f53-part2 -> ../../sdd2
lrwxrwxrwx 1 root root  9 Jul 24 13:43 wwn-0x500a07510961196b -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x500a07510961196b-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x500a07510961196b-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x500a07510961196b-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul 24 13:43 wwn-0x500a07510961196b-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /usr/local/data          ext4       (rw,relatime,data=ordered)
/dev/sda5        /home                    ext4       (rw,relatime,data=ordered)
/dev/sda6        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb3        /media/whouse            ext4       (rw,relatime,data=ordered)
/dev/sdc1        /media/mext              fuseblk    (rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,allow_other,blksize=4096,user)
/dev/sdd2        /media/ext               fuseblk    (rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,allow_other,blksize=4096,user)
/dev/sde1        /media/sext              fuseblk    (rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,allow_other,blksize=4096,user)
/dev/sdg1        /media/extext            ext4       (rw,nosuid,nodev,noexec,relatime,data=ordered,user)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
else
  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
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
if background_color 44,0,30,0; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
	else
	  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
	fi
        linux	/boot/vmlinuz-4.10.0-27-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.10.0-27-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
	menuentry 'Ubuntu, with Linux 4.10.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-27-generic-advanced-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.10.0-27-generic ...'
	        linux	/boot/vmlinuz-4.10.0-27-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-27-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-27-generic-init-upstart-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.10.0-27-generic ...'
	        linux	/boot/vmlinuz-4.10.0-27-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 4.10.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.10.0-27-generic-recovery-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.10.0-27-generic ...'
	        linux	/boot/vmlinuz-4.10.0-27-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.10.0-27-generic
	}
	menuentry 'Ubuntu, with Linux 4.8.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-58-generic-advanced-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.8.0-58-generic ...'
	        linux	/boot/vmlinuz-4.8.0-58-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.8.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 4.8.0-58-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-58-generic-init-upstart-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.8.0-58-generic ...'
	        linux	/boot/vmlinuz-4.8.0-58-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.8.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 4.8.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-58-generic-recovery-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.8.0-58-generic ...'
	        linux	/boot/vmlinuz-4.8.0-58-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.8.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-87-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-87-generic-advanced-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.4.0-87-generic ...'
	        linux	/boot/vmlinuz-4.4.0-87-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-87-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-87-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-87-generic-init-upstart-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.4.0-87-generic ...'
	        linux	/boot/vmlinuz-4.4.0-87-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-87-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-87-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-87-generic-recovery-8ddc873b-786d-4587-b1e2-f64c4a5b0e06' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		else
		  search --no-floppy --fs-uuid --set=root 8ddc873b-786d-4587-b1e2-f64c4a5b0e06
		fi
		echo	'Loading Linux 4.4.0-87-generic ...'
	        linux	/boot/vmlinuz-4.4.0-87-generic root=UUID=8ddc873b-786d-4587-b1e2-f64c4a5b0e06 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-87-generic
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
```

---

### Post by BenginM on 2017-07-24
Salutations! Ray.. did this occurred after an upgrade ! is this machine with hybrid/dual graphics !  is the /root partition full !

you might want to check , when you're forced back to the login manager/screen , switch to a virtual console by pressin' Ctrl+Alt+F4 , login nd run df -h , if root/ is full you might need to remove few older kernels .. and keep at least one or two old ones.

if that's not the case , then it's probable a miss configuration with the nvidia driver ..

I see your 16.04 LTS is still using kernel base 4.4.0- , you should be at least fylin' the LTS Stack 4.8.0 , install that and try bootin' with it, see if that gets you to Unity desktop without issues! #See

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by oldfred on 2017-07-24
The recovery mode should be using nomodeset.
But have you tried nomodeset in grub when booting?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters
[/URL]

     Have you installed more than one nVidia driver or the incorrect one? If more than one you must totally purge the old nVidia driver before installing the correct one.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
            

    What does this show if you can get to terminal?
 ubuntu-drivers devices 
      
 dkms status 
    
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by ray field on 2017-07-25
dear old Fred, thanks much -- indeed it was the Nvidia drivers, I should have realized my installation had somehow become corrupted (otherwise why would the old kernel have booted up fine?) -- maybe from an incomplete software/kernel upgrade? I chose the recommended driver, and all is well again. tip of the hat to you and BenginM.

ray

---

