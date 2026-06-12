---
title: "Dual Boot from 2 different HDDs"
date: 2015-11-22
forum: General Help
---

### Post by veggo94 on 2015-11-22
Hi guys :)

I have an Asus N53SV Notebook, where i removed the optical drive and i've put a second HDD. So this is my configuration:
- SSD Samsung 850 EVO of 250GB: there is located Windows 10, and this is drive C:
- HDD WB Blue of 1TB: there i've stored photos, musics, some programs, etc. and this is the drive D:

So, with Partion Assistant in Windows, i've reduced the HDD by 60GB the principal partition without losing data in D: and in this new free space of 60GB i want to install Ubuntu 15.10. 
I followed this guide ([http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/) ), booted with a Ubuntu 15.10 live pen USB and divided the 60GB free space in:
-536Mb for the EFI Partition
-20Gb for the Root partition (/)
-38Gb for the Home partition (/home)
-3.9Gb for the Swap partition

This is the SSD Samsung 850 EVO (sda):
[IMG]http://s13.postimg.org/6o7vyzudz/Schermata_del_2015_11_22_16_38_08.png[/IMG]

And this is the HDD WB Blue of 1TB (sdb):
[IMG]http://s14.postimg.org/4yur7yfwh/Schermata_del_2015_11_22_16_38_13.png[/IMG]

Then i have set /dev/sdb3 (the EFI Parttion in the 1Tb HDD) as the device for the bootloader and installed correctly the OS. 
In the BIOS settings i've selected the voice "ubuntu" to startup (the other 2 options are: SSD or HDD 1 TB).

The problem is that i can't set the Windows 10 option in the Grub. I've tried
```
sudo apt-update grub
```
but it doesn't see Windows 10. I tried to turn off the hibernate mode in Windows 10 (i'm able to boot it only changing the boot setup in BIOS: i put the SSD as entry and it boots Windows correctly) and update Grub, but nothing happens.

This is a Log made with Bootinfoscript:
```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdb2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb3: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi


sdb4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdb5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 232,9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sda2             718,848   437,893,061   437,174,214   7 NTFS / exFAT / HPFS
/dev/sda3         437,893,120   439,554,047     1,660,928  27 Hidden NTFS (Recovery Environment)




Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 1,953,525,167 1,953,525,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         264,192 1,825,667,234 1,825,403,043 Data partition (Windows/Linux)
/dev/sdb3   1,825,669,120 1,826,713,599     1,044,480 EFI System partition
/dev/sdb4   1,826,713,600 1,865,775,103    39,061,504 Data partition (Linux)
/dev/sdb5   1,865,775,104 1,945,714,687    79,939,584 Data partition (Linux)
/dev/sdb6   1,945,714,688 1,953,523,711     7,809,024 Swap partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        2278AE0B78ADDE33                       ntfs       Riservato per il sistema
/dev/sda2        5EA4AFA2A4AF7B63                       ntfs       
/dev/sda3        0AB49A8CB49A79C1                       ntfs       
/dev/sdb1                                                          
/dev/sdb2        C4AE15E5AE15D0B2                       ntfs       DATI
/dev/sdb3        5031-8E56                              vfat       
/dev/sdb4        807c2781-5ec8-41da-bfda-8d2e09847812   ext4       
/dev/sdb5        5e635041-ffc4-47e2-8439-18ec4dd2a052   ext4       
/dev/sdb6        04da8cdc-1219-4f3b-9857-287fd6a98c6a   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb3        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb4        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb5        /home                    ext4       (rw,relatime,data=ordered)




=========================== sdb4/boot/grub/grub.cfg: ===========================


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
   set default="Ubuntu"
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
set root='hd1,gpt4'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
else
  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=it_IT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=2
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=2
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


### END /etc/grub.d/10_linux_proxy ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10"{
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2278AE0B78ADDE33
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/43_linux_proxy ###
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-807c2781-5ec8-41da-bfda-8d2e09847812' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt4'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
	else
	  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
	fi
	linux	/boot/vmlinuz-4.2.0-19-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.2.0-19-generic
}
submenu "Opzioni avanzate per Ubuntu"{
menuentry "Ubuntu, con Linux 4.2.0-19-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-19-generic-advanced-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-19-generic...'
		linux	/boot/vmlinuz-4.2.0-19-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro  quiet splash $vt_handoff
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-19-generic
}
menuentry "Ubuntu, with Linux 4.2.0-19-generic (upstart)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-19-generic-init-upstart-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-19-generic...'
		linux	/boot/vmlinuz-4.2.0-19-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-19-generic
}
menuentry "Ubuntu, with Linux 4.2.0-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-19-generic-recovery-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-19-generic...'
		linux	/boot/vmlinuz-4.2.0-19-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro recovery nomodeset 
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-19-generic
}
menuentry "Ubuntu, con Linux 4.2.0-18-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-18-generic-advanced-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-18-generic...'
		linux	/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro  quiet splash $vt_handoff
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-18-generic
}
menuentry "Ubuntu, with Linux 4.2.0-18-generic (upstart)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-18-generic-init-upstart-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-18-generic...'
		linux	/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-18-generic
}
menuentry "Ubuntu, with Linux 4.2.0-18-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-18-generic-recovery-807c2781-5ec8-41da-bfda-8d2e09847812' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt4'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt4 --hint-efi=hd1,gpt4 --hint-baremetal=ahci1,gpt4  807c2781-5ec8-41da-bfda-8d2e09847812
		else
		  search --no-floppy --fs-uuid --set=root 807c2781-5ec8-41da-bfda-8d2e09847812
		fi
		echo	'Caricamento Linux 4.2.0-18-generic...'
		linux	/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=807c2781-5ec8-41da-bfda-8d2e09847812 ro recovery nomodeset 
		echo	'Caricamento ramdisk iniziale...'
		initrd	/boot/initrd.img-4.2.0-18-generic
}
}
### END /etc/grub.d/43_linux_proxy ###


### BEGIN /etc/grub.d/44_linux_xen ###


### END /etc/grub.d/44_linux_xen ###


### BEGIN /etc/grub.d/45_memtest86+ ###
### END /etc/grub.d/45_memtest86+ ###


### BEGIN /etc/grub.d/46_os-prober ###
### END /etc/grub.d/46_os-prober ###


### BEGIN /etc/grub.d/47_uefi-firmware ###
### END /etc/grub.d/47_uefi-firmware ###


### BEGIN /etc/grub.d/48_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/48_custom ###
--------------------------------------------------------------------------------


=============================== sdb4/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb4 during installation
UUID=807c2781-5ec8-41da-bfda-8d2e09847812 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb3 during installation
UUID=5031-8E56  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb5 during installation
UUID=5e635041-ffc4-47e2-8439-18ec4dd2a052 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=04da8cdc-1219-4f3b-9857-287fd6a98c6a none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb4: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-5eJJRxkg/Tmp_Log: File o directory non esistente

```

What can i do? I have to install Grub also in C: and D:?
Thank you in advance :)

---

### Post by oldfred on 2015-11-22
UEFI & BIOS/CSM/Legacy boot modes are not compatible.
Once you start booting in one mode you cannot switch to other mode without reboot, or you cannot use grub to boot system in different boot mode.
You can use UEFI/BIOS to boot or probably a one time boot key like f10 or f12(check your manual on correct key). Some early UEFI required you to also change settings from UEFI to CSM or vice-versa to boot system installed in that mode.

Your Windows are in BIOS boot mode.
Your Ubuntu is in UEFI boot mode.

You can convert Ubuntu to BIOS boot with Boot-Repair, but first have to create a 1 or 2MB unformatted partition with the bios_grub flag if using gparted or code ef02 if using gdisk. Then Boot-Repair has you uninstall grub-efi-amd64(UEFI) and install grub-pc(BIOS)

---

### Post by veggo94 on 2015-11-22
> **oldfred said:**
> UEFI & BIOS/CSM/Legacy boot modes are not compatible.
Once you start booting in one mode you cannot switch to other mode without reboot, or you cannot use grub to boot system in different boot mode.
You can use UEFI/BIOS to boot or probably a one time boot key like f10 or f12(check your manual on correct key). Some early UEFI required you to also change settings from UEFI to CSM or vice-versa to boot system installed in that mode.

Your Windows are in BIOS boot mode.
Your Ubuntu is in UEFI boot mode.

You can convert Ubuntu to BIOS boot with Boot-Repair, but first have to create a 1 or 2MB unformatted partition with the bios_grub flag if using gparted or code ef02 if using gdisk. Then Boot-Repair has you uninstall grub-efi-amd64(UEFI) and install grub-pc(BIOS)

So i can delete the EFI Partition of 536Mb I've created and create another partition of 2Mb with bios_grub flag? Or I should mantain the EFI Partiton? 

Thank you :)

---

### Post by oldfred on 2015-11-22
I had BIOS only system several years ago and started converting all drives to gpt.
I always add both the ESP - efi system partition and the bios_grub to all drives. But only use one or the other normally.

There are some minor advantages of UEFI boot, and some users just dual boot using the one time boot key, not grub. Or if in future you want UEFI on this drive better to keep the ESP. It is not large compared to total space on drive and if drive full of data difficult to add an ESP near beginning of drive where it is preferred.

Or it really is your choice if you want to keep the ESP partition.
But you have to have UEFI/BIOS set to boot in correct mode as default or else it starts looking in the wrong place first, slowing boot slightly.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

