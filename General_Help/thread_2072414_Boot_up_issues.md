---
title: "Boot up issues"
date: 2012-10-17
forum: General Help
---

### Post by meduser on 2012-10-17
Hello,

I wanted to try a different desktop environment, so I added Cinnamon to my pc. Now when I try and boot from having the pc turned off, it will not boot. 

The only way to get it to boot, is to boot to recovery mode, and then run fsck, and then dgkg, the I can resume booting and it boots, otherwise it just hangs during booting, and nothing seems to be happening.

Any ideas as to how I can fix this?

Thanks
Med

---

### Post by meduser on 2012-10-17
bump...

any ideas?

Anyone?

---

### Post by 2F4U on 2012-10-18
What error messages do you get? I doubt that it is related to Cinnamon, since that is just a desktop environment. If you have to run fsck to be able to boot, it is likely a problem with the hard disk. Maybe the hdd has errors/bad sectors.

---

### Post by meduser on 2012-10-18
I don't get any errors.

I start up the pc, and I boot to the grub menu.

If I leave it on Ubuntu, it looks like it is going to boot, but the screen just goes black, and the does not continue to boot.

The only way to get it to boot is to go into recovery and run dkpg and fsck.

I have had Ubuntu 12.04 on here since the release day, and this only started happening when I added the Cinnamon environment.

I don't think the issue with the HDD, as it is only a year old, and I have no issue with other programs or Win7, as this is a dual boot.

---

### Post by meduser on 2012-10-18
so how do I fix the boot up? 

Is there some terminal commands I can run that will tell me what is broken?

I love Ubuntu based OS, but I have small issues like this one, and don't know how to fix it.

Can some knowledgeable member help me out?

---

### Post by sienile on 2012-10-18
If it boots after a fsck and dgkg then it should boot properly the next time as well. You may have just had some errors that got fixed.

I doubt it's something that it can fix, but have you tried boot-repair?

---

### Post by meduser on 2012-10-18
> **sienile said:**
> If it boots after a fsck and dgkg then it should boot properly the next time as well. You may have just had some errors that got fixed.

I doubt it's something that it can fix, but have you tried boot-repair?

I have had this issue for a few weeks. If I do not go into recovery, it just won't boot.

How do I use boot repair?

---

### Post by sienile on 2012-10-18
All the info you need is here: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by meduser on 2012-10-18
tried boot repair, and restarted the pc...no change

Now when cinnamon was installed, the grub screen changed, I get a rocket ship, and crappy artwork instead of the clean and crisp grub that Ubuntu starts with.


Debian grub..is that the issue?

---

### Post by meduser on 2012-10-18
BUMP


I can't be the only person using Ubuntu that has had boot issues.

How to troubleshoot this? How to try and find out what is causing this? 

I have had this issue for over 6 weeks now, and have rebooted the pc at least 50 times in that time period.

Same issue every time.

---

### Post by meduser on 2012-10-19
bump

---

### Post by meduser on 2012-10-20
I hate to keep bumping this, but I am almost begging for help here.

---

### Post by meduser on 2012-10-20
Ok, some info off the pc.

When I run fdisk -l I get:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbeb3beb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   443668479   221730816    7  HPFS/NTFS/exFAT
/dev/sda3       443668480  1937276927   746804224   83  Linux
/dev/sda4      1937278974  1953523711     8122369    5  Extended
/dev/sda5      1937278976  1953523711     8122368   82  Linux swap / Solaris


Should the * be next to /dev/sda3? This is a dual boot, that boots to the GRUB, and I have the option of booting into either Windows 7 or Ubuntu. When I run update-grub, I get:
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.2.0-33-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-33-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-31-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-31-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done

When I run bash ~/Desktop/boot_info_script*.sh, the results file that gets created looks like:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

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
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   443,668,479   443,461,632   7 NTFS / exFAT / HPFS
/dev/sda3         443,668,480 1,937,276,927 1,493,608,448  83 Linux
/dev/sda4       1,937,278,974 1,953,523,711    16,244,738   5 Extended
/dev/sda5       1,937,278,976 1,953,523,711    16,244,736  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2C8AC9438AC909F2                       ntfs       System Reserved
/dev/sda2        D486D82986D80E3C                       ntfs       
/dev/sda3        a6cbbcf7-787a-4191-9855-dfe0848e8a54   ext4       
/dev/sda5        68d1c604-ef05-48b8-b402-1f96cfe6be0a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,0,0; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-33-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-33-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-33-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-33-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-32-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-32-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-32-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-31-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-31-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-31-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-30-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-30-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-30-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-29-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	echo	'Loading Linux 3.2.0-23-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-23-generic-pae root=UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root a6cbbcf7-787a-4191-9855-dfe0848e8a54
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 2C8AC9438AC909F2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root D486D82986D80E3C
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a6cbbcf7-787a-4191-9855-dfe0848e8a54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=68d1c604-ef05-48b8-b402-1f96cfe6be0a none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda3/boot/extlinux/extlinux.conf: =======================

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

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 365.712192535 = 392.680476672  boot/grub/core.img                             1
 428.444355011 = 460.038623232  boot/grub/grub.cfg                             1
 212.935520172 = 228.637773824  boot/initrd.img-3.2.0-23-generic-pae           2
 215.612697601 = 231.512371200  boot/initrd.img-3.2.0-29-generic-pae           3
 221.102546692 = 237.407051776  boot/initrd.img-3.2.0-30-generic-pae           2
 222.899108887 = 239.336095744  boot/initrd.img-3.2.0-31-generic-pae           2
 220.547557831 = 236.811137024  boot/initrd.img-3.2.0-32-generic-pae           1
 223.524116516 = 240.007192576  boot/initrd.img-3.2.0-33-generic-pae           1
 483.690670013 = 519.358902272  boot/vmlinuz-3.2.0-23-generic-pae              1
 212.726348877 = 228.413177856  boot/vmlinuz-3.2.0-29-generic-pae              1
 217.788848877 = 233.848995840  boot/vmlinuz-3.2.0-30-generic-pae              1
 219.152130127 = 235.312807936  boot/vmlinuz-3.2.0-31-generic-pae              2
 222.398227692 = 238.798278656  boot/vmlinuz-3.2.0-32-generic-pae              1
 223.147460938 = 239.602761728  boot/vmlinuz-3.2.0-33-generic-pae              2
 223.524116516 = 240.007192576  initrd.img                                     1
 220.547557831 = 236.811137024  initrd.img.old                                 1
 223.147460938 = 239.602761728  vmlinuz                                        2
 222.398227692 = 238.798278656  vmlinuz.old                                    1

================= sda3: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 693.720802307 = 744.877039616  boot/extlinux/chain.c32                        1
 485.683376312 = 521.498554368  boot/extlinux/extlinux.conf                    1

============== sda3: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
```

I see errors there, any ideas how to fix this?

Cheers.

---

### Post by meduser on 2012-10-20
So, digging deeper, 

I get the following error:
Superblock last mount is in the future (by less than a day).

Ran the following commands:
sudo apt-get install ntp
then:
sudo service ntp start

Just rebooted all the way thru.

Going to try again.

---

### Post by offgridguy on 2012-10-20
Boot up issues seem to be one of the most common of all in this forum,  I can't be of much help but I do share your frustration.

---

### Post by meduser on 2012-10-20
Nope, locked up again upon reboot.

After running recovery, and enabling networking, running dkpg,
resume boot. I get a line flash at the top of the page that something, but it flashes too fast. 

The last part of it says already in use, but it is on the screen for less than a second.

---

### Post by meduser on 2012-10-20
Seems to be a kernel issue.

A google search on the error gives me results that this is an ongoing Debian kernel issue. Kernel points to a slot that has already been assigned to a ram slot, which blocks any further load

---

### Post by meduser on 2012-10-20
When running Boot repair, I get:

The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by meduser on 2012-10-20
I also get a link to here:

[http://paste.ubuntu.com/1292889/](http://paste.ubuntu.com/1292889/)

---

### Post by meduser on 2012-10-20
So, I have booted into the pc 4x in a row now.

The only hangup is that it does not show the login window unless I press the enter button.

But it appears to be temp. fixed.

---

### Post by meduser on 2012-10-21
upgraded to 12.10 and it is fixed for sure now.

Not sure what went wrong. If any knowledgeable member out there can take a look and try to figure it out that would be awesome.

Anyhow, it's fixed.

---

