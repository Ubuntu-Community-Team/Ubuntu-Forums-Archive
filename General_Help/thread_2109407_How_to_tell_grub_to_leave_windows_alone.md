---
title: "How to tell grub to leave windows alone"
date: 2013-01-27
forum: General Help
---

### Post by magnet18 on 2013-01-27
Hi everybody, first post, hope it's in the right spot.

I'm running Ubuntu 12.04, 64bit, cinnamon desktop, running on an asus G75. 
At first i wasn't a huge fan of it, but it crashed my windows boot sector and i was forced to use it all this week and I've actually come to quite like it to the point I'm planning on putting it on my primary SSD and downgrade windows to the secondary HDD

Unfortunatley I'm required to have a windows boot available. Im in college and some of my classes require windows only programs, so im stuck with it.

**Which brings me to my problem**
Ive been trying for quite some time to get windows and linux to play nice on their own harddrives and not corrupt each other, but to no avail.

I have ubuntu up and running like a charm.
I can remove my ubuntu HDD, install windows on the SSD, and boot windows just fine.
I can then reinstall the ubuntu HDD, and as long as i boot from the windows drive first, windows will keep working
but AS SOON AS I TRY TO BOOT INTO UBUNTU, the windows boot sector gets corrupted, i'm assuming by grub (since it recognizes the windows 7 OS and has it as an option), so the next time i try to boot into windows, there's an error and it said to run windows recovery, which did nothing.

i tried using the testdisk linux terminal command, and now it says device not found

I either want to fix my windows boot section, or reinstall windows and somehow tell grub to just leave it the F alone and ignore it, I'm capable of hitting escape on boot and selecting the drive myself

I would also like to move ubuntu from the 1TB HHD to the 250GB SSD, but that seems to be another beast itself

any help you guys could offer is much appreciated
thanks!

---

### Post by sidzen on 2013-01-27
At any time, have you performed a [PHP]sudo update-grub [/PHP]?
Are you willing to pay for a third-party boot-loader -- what is your preference -- work at it or pay for it?

---

### Post by kc1di on 2013-01-27
Hello magnet18 and Welcome to Ubuntu,

I have one question are you running ubuntu as an install os or via the WuBI install on Windows?

If it's a regualar install alonside windows you should have no problem dual booting 

[Here is a page]("https://help.ubuntu.com/community/WindowsDualBoot") that will help you set that up.

There should be no reason that grub would not boot windows and It should not be corrupting the windows install.
that being said sometimes things do go wrong [here is a tool]("https://help.ubuntu.com/community/Boot-Repair") that can help with boot problems

---

### Post by oldfred on 2013-01-27
Are you hibernating in Windows and then writing files from Ubuntu into the Windows NTFS partition.

You should be sure to install Ubuntu on its own drive and its boot loader into that drive, then set BIOS to boot Ubuntu drive.
All the auto install options will install grub2's boot loader to sda, which usually is the Windows drive.

to see where everything is at:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by magnet18 on 2013-01-27
Thankyou all for the quick replies!

Update, i removed the ubuntu drive and got startup recovery to fix the windows boot partition, so now it's booting ok (writing this in windows as i create an iso and a DVD just in case), though i suspect the problem is not solved and would gander to guess that as soon as i boot ubuntu again it will stop working


> **sidzen said:**
> At any time, have you performed a [PHP]sudo update-grub [/PHP]?
Are you willing to pay for a third-party boot-loader -- what is your preference -- work at it or pay for it?
I have not done a sudo update-grub, and will in a minute.
also, work to fix things, a third party boot loader sounds unnecessary, tons of people have gotten this to work


> **kc1di said:**
> Hello magnet18 and Welcome to Ubuntu,

I have one question are you running ubuntu as an install os or via the WuBI install on Windows?

If it's a regualar install alonside windows you should have no problem dual booting 

[Here is a page]("https://help.ubuntu.com/community/WindowsDualBoot") that will help you set that up.

There should be no reason that grub would not boot windows and It should not be corrupting the windows install.
that being said sometimes things do go wrong [here is a tool]("https://help.ubuntu.com/community/Boot-Repair") that can help with boot problems

independent installer, i used a burned DVD and installed that way,
all hashes checked
I'll look at that tool, thanks

> **oldfred said:**
> Are you hibernating in Windows and then writing files from Ubuntu into the Windows NTFS partition.
nope
anytime I switch, i shut all the way down, and even then i wasn't writing to the NTFS partition

> You should be sure to install Ubuntu on its own drive and its boot loader into that drive, then set BIOS to boot Ubuntu drive.
check check and check
both drives can run independently of the other. When i put them both in, windows runs fine and doesn't hurt linux any. as soon as i boot linux through grub, i have to use recovery to recover the windows boot sector to get windows to boot.
> All the auto install options will install grub2's boot loader to sda, which usually is the Windows drive.

to see where everything is at:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I will as soon as im done creating the windows recovery isos and put my linux drive back in

---

### Post by oldfred on 2013-01-27
I used to use CDs a lot for Linux repair ISO, but now use flash drives. I was able to install the Windows 7 repairCD to a flash drive and use that to run chkdsk on XP.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by magnet18 on 2013-01-27
Im actually going to take this opportunity when everything isn't working, to go ahead and wipe windows off the first harddrive and move linux to that, then see how that works
then ill partition the second hard drive and put windows on that, and then check back in

---

### Post by sidzen on 2013-01-27
Be sure to install windows first

---

### Post by magnet18 on 2013-01-27
why is that?

---

### Post by mcduck on 2013-01-27
> **magnet18 said:**
> why is that?

Windows isn't made to be friendly towards any other operating system installs than other Windows versions. Installing it will overwrite Grub if it's installed on the same drive, leaving only Windows bootable. On the other hand installing Ubuntu after Widnwos on similar situation would result in Grub detecting both operating systems and give you a menu to select which one to use.

Doesn't really make any difference in the setup you've decided to use, though.

To be honest, you'd most likely have much easier time just keeping both drives connected, not mess with BIOS to select which drive is booted, and instead just let Grub handle that for you. :)

---

### Post by magnet18 on 2013-01-27
yea, im planning on separate drives, so i should be able to transfer linux to the current windows drive once i reformat it, then wipe the old linux drive and install windows on it fresh

I've had nothing but bad experiences trying to have linux and windows on the same drive

---

### Post by magnet18 on 2013-01-27
the results of the boot info as requested-
[http://paste.ubuntu.com/1578272/](http://paste.ubuntu.com/1578272/)

one other thing i just remembered that might make a difference
my computer is EFI based (no idea what that is but its given me trouble in the past)
and in order to boot from a linux cd i must specify
**noacpi noapic nomodeset**

```
Boot Info Script 5a35e00 + Boot-Repair extra info      [Boot-Info 22Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Testdisk is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sdb4 starts 
                       at sector 1901094912. But according to the info from 
                       fdisk, sdb4 starts at sector 416432128.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,936,830,463 1,936,828,416  83 Linux
/dev/sda2       1,936,832,510 1,953,523,711    16,691,202   5 Extended
/dev/sda5       1,936,832,512 1,953,523,711    16,691,200  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
256 heads, 63 sectors/track, 29071 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       411,647       409,600 EFI System partition
/dev/sdb2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb3         673,792   416,432,127   415,758,336 Data partition (Windows/Linux)
/dev/sdb4     416,432,128   468,860,927    52,428,800 Windows Recovery Environment (Windows)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        32060ca5-8a68-470a-84bc-5e52474bc978   ext4       
/dev/sda5        056711fb-eb5f-4bbe-be6a-1a1488bab424   swap       
/dev/sdb1        0AFE-C7F7                              vfat       SYSTEM
/dev/sdb3        C45E7F375E7F20FA                       ntfs       OS
/dev/sdb4        AC7A43BA7A438056                       ntfs       Recovery

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
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
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	linux	/boot/vmlinuz-3.2.0-36-generic root=UUID=32060ca5-8a68-470a-84bc-5e52474bc978 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	echo	'Loading Linux 3.2.0-36-generic ...'
	linux	/boot/vmlinuz-3.2.0-36-generic root=UUID=32060ca5-8a68-470a-84bc-5e52474bc978 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-36-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=32060ca5-8a68-470a-84bc-5e52474bc978 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=32060ca5-8a68-470a-84bc-5e52474bc978 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 32060ca5-8a68-470a-84bc-5e52474bc978
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" --class windows --class os {
	insmod part_gpt
	insmod ntfs
	set root='(hd1,gpt3)'
	search --no-floppy --fs-uuid --set=root C45E7F375E7F20FA
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb4)" --class windows --class os {
	insmod part_gpt
	insmod ntfs
	set root='(hd1,gpt4)'
	search --no-floppy --fs-uuid --set=root AC7A43BA7A438056
	drivemap -s (hd0) ${root}
	chainloader +1
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=32060ca5-8a68-470a-84bc-5e52474bc978 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=056711fb-eb5f-4bbe-be6a-1a1488bab424 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 228.128166199 = 244.950753280  boot/grub/grub.cfg                             1
 476.145679474 = 511.257530368  boot/grub/core.img                             1
 224.134498596 = 240.662585344  boot/vmlinuz-3.2.0-29-generic                  1
   1.759513855 = 1.889263616    boot/vmlinuz-3.2.0-36-generic                  1
   1.759513855 = 1.889263616    vmlinuz                                        1
 224.134498596 = 240.662585344  vmlinuz.old                                    1
   2.037765503 = 2.188034048    boot/initrd.img-3.2.0-29-generic               2
   2.062259674 = 2.214334464    boot/initrd.img-3.2.0-36-generic               2
   2.062259674 = 2.214334464    initrd.img                                     2
   2.037765503 = 2.188034048    initrd.img.old                                 2


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-01-27__18h17 ===================
boot-repair version : 3.197~ppa29~precise
boot-sav version : 3.197~ppa29~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.197~ppa29~precise
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.2.0-36-generic root=UUID=32060ca5-8a68-470a-84bc-5e52474bc978 ro quiet splash vt.handoff=7

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda1:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sdb3:Windows 7 (loader):Windows:chain
/dev/sdb4:Windows Recovery Environment (loader):Windows1:chain

=================== blkid:
/dev/sda1: UUID="32060ca5-8a68-470a-84bc-5e52474bc978" TYPE="ext4"
/dev/sda5: UUID="056711fb-eb5f-4bbe-be6a-1a1488bab424" TYPE="swap"
/dev/sdb1: LABEL="SYSTEM" UUID="0AFE-C7F7" TYPE="vfat"
/dev/sdb3: LABEL="OS" UUID="C45E7F375E7F20FA" TYPE="ntfs"
/dev/sdb4: LABEL="Recovery" UUID="AC7A43BA7A438056" TYPE="ntfs"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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




=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jan 21 23:14 grub.d
total 60
-rwxr-xr-x 1 root root 6743 Dec 10 07:20 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7780 Dec 10 07:20 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root 1388 Dec 10 07:20 30_uefi-firmware
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README


Presence of EFI/Microsoft file detected: /mnt/boot-sav/sdb1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sdb1/EFI/Boot/bootx64.efi
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, but it is not setup in EFI-mode for this installed-session.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.
sdb3	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb3.
sdb4	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb4.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  992GB   992GB   primary   ext4            boot
2      992GB   1000GB  8546MB  extended
5      992GB   1000GB  8546MB  logical   linux-swap(v1)


Model: ATA OCZ-AGILITY3 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
1      1049kB  211MB  210MB   fat32        EFI system partition          boot
2      211MB   345MB  134MB                Microsoft reserved partition  msftres
3      345MB   213GB  213GB   ntfs         Basic data partition
4      213GB   240GB  26.8GB  ntfs         Basic data partition          hidden, diag

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000LM024 HN-M;
1:1049kB:992GB:992GB:ext4::boot;
2:992GB:1000GB:8546MB:::;
5:992GB:1000GB:8546MB:linux-swap(v1)::;

BYT;
/dev/sdb:240GB:scsi:512:512:gpt:ATA OCZ-AGILITY3;
1:1049kB:211MB:210MB:fat32:EFI system partition:boot;
2:211MB:345MB:134MB::Microsoft reserved partition:msftres;
3:345MB:213GB:213GB:ntfs:Basic data partition:;
4:213GB:240GB:26.8GB:ntfs:Basic data partition:hidden, diag;


=================== mount:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
/dev/sdb1 on /mnt/boot-sav/sdb1 type vfat (rw)
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb4 on /mnt/boot-sav/sdb4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null nvidia0 nvidiactl oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sdb3 sdb4 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 v4l vboxdrv vboxnetctl vboxusb vga_arbiter video0 zero
ls /dev/mapper:  control
Files in /mnt/boot-sav/sdb1/efi: /mnt/boot-sav/sdb1/efi/ASUS/G75VW.BIN /mnt/boot-sav/sdb1/efi/ASUS /mnt/boot-sav/sdb1/efi/Boot/bootx64.efi /mnt/boot-sav/sdb1/efi/Boot /mnt/boot-sav/sdb1/efi/Microsoft/Boot/BCD.LOG2 /mnt/boot-sav/sdb1/efi/Microsoft/Boot/BCD.LOG1 /mnt/boot-sav/sdb1/efi/Microsoft/Boot/BCD.LOG /mnt/boot-sav/sdb1/efi/Microsoft/Boot/BCD /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts/wgl4_boot.ttf /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts/kor_boot.ttf /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts/jpn_boot.ttf /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts/cht_boot.ttf /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts/chs_boot.ttf /mnt/boot-sav/sdb1/efi/Microsoft/Boot/Fonts /mnt/boot-sav/sdb1/efi/Microsoft/Boot/BOOTSTAT.DAT /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-TW/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-TW/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-TW /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-HK/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-HK/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-HK /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-CN/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-CN/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/zh-CN /mnt/boot-sav/sdb1/efi/Microsoft/Boot/tr-TR/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/tr-TR/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/tr-TR /mnt/boot-sav/sdb1/efi/Microsoft/Boot/sv-SE/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/sv-SE/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/sv-SE /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ru-RU/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ru-RU/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ru-RU /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-PT/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-PT/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-PT /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-BR/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-BR/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pt-BR /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pl-PL/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pl-PL/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/pl-PL /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nl-NL/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nl-NL/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nl-NL /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nb-NO/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nb-NO/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/nb-NO /mnt/boot-sav/sdb1/efi/Microsoft/Boot/memtest.efi /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ko-KR/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ko-KR/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ko-KR /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ja-JP/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ja-JP/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/ja-JP /mnt/boot-sav/sdb1/efi/Microsoft/Boot/it-IT/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/it-IT/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/it-IT /mnt/boot-sav/sdb1/efi/Microsoft/Boot/hu-HU/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/hu-HU/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/hu-HU /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fr-FR/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fr-FR/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fr-FR /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fi-FI/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fi-FI/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/fi-FI /mnt/boot-sav/sdb1/efi/Microsoft/Boot/es-ES/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/es-ES/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/es-ES /mnt/boot-sav/sdb1/efi/Microsoft/Boot/en-US/memtest.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/en-US/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/en-US/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/en-US /mnt/boot-sav/sdb1/efi/Microsoft/Boot/el-GR/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/el-GR/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/el-GR /mnt/boot-sav/sdb1/efi/Microsoft/Boot/de-DE/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/de-DE/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/de-DE /mnt/boot-sav/sdb1/efi/Microsoft/Boot/da-DK/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/da-DK/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/da-DK /mnt/boot-sav/sdb1/efi/Microsoft/Boot/cs-CZ/bootmgr.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/cs-CZ/bootmgfw.efi.mui /mnt/boot-sav/sdb1/efi/Microsoft/Boot/cs-CZ /mnt/boot-sav/sdb1/efi/Microsoft/Boot/bootmgr.efi /mnt/boot-sav/sdb1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sdb1/efi/Microsoft/Boot /mnt/boot-sav/sdb1/efi/Microsoft /mnt/boot-sav/sdb1/efi

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 de 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 06 00 11 03 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f7 c7 fe 0a 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

=================== hexdump -n512 -C /dev/sdb3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 0a 00  |........?....H..|
00000020  00 00 00 00 80 00 80 00  ff f7 c7 18 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  fa 20 7f 5e 37 7f 5e c4  |......... .^7.^.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdb4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 50 71  |........?....hPq|
00000020  00 00 00 00 80 00 80 00  ff ff 1f 03 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  ff ff 31 00 00 00 00 00  |..........1.....|
00000040  f6 00 00 00 01 00 00 00  56 80 43 7a ba 43 7a ac  |........V.Cz.Cz.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4      910G   88G  776G  11% /
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     1.6G  916K  1.6G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G  232K  3.9G   1% /run/shm
/dev/sdb1      vfat      196M   24M  173M  13% /mnt/boot-sav/sdb1
/dev/sdb3      fuseblk   199G   51G  148G  26% /mnt/boot-sav/sdb3
/dev/sdb4      fuseblk    25G  8.7G   17G  35% /mnt/boot-sav/sdb4

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001e62a

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936830463   968414208   83  Linux
/dev/sda2      1936832510  1953523711     8345601    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1936832512  1953523711     8345600   82  Linux swap / Solaris

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
256 heads, 63 sectors/track, 29071 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4225e1bd

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


EFI detected. Please check the options.
=================== Advice displayed in case of recommended repair
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb1/efi/.../grub*.efi file!

The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages unsign-grub) and reinstall the grub-efi of sda1, using the following options:        sdb1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
```

---

### Post by oldfred on 2013-01-27
You have mixed modes which will not let you dual boot. It may be easier to install Ubuntu in UEFI mode.

Windows is in UEFI/gpt mode on sdb and Ubuntu is in BIOS/MBR mode in sda.

How you boot install media UEFI or BIOS is how it installs for both Windows & Ubuntu.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

I also prefer to install Ubuntu in smaller system partition of about 25GB and use rest of space for Ubuntu as data partition or /home.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one, so if already existing do not attempt another)
1 MB bios_grub no format (for BIOS boot not required for UEFI)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

    



 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by magnet18 on 2013-01-27
why 12.10?
can i use 12.04?

---

### Post by magnet18 on 2013-01-28
ALRIGHT, PROGRESS!

I was trying to get windows to move to the second drive, but it was being a little &!7(# and wouldn't recognize it's own recovery disk, so i just left it and installed ubuntu 12.04 IN UEFI MODE alongside it. Each has roughly 100GB, it went smoothly and if this works, i'm ok with keeping this arrangement and just using my 1TB for data storage.

I then booted into ubuntu and updated grub

i was then able to shut down and boot via the bios into the windows OS as well, no corruption, though it did try to do a disk check

unfortunatley, when i try to use the grub bootloader to select windows 7, it gives me an error something along the lines of invalid EFI path

I don't remember exactly, and can post the exact error message if needed

I'm happy that both OS's work now, but are there any ideas how to fix this new error?
or at the very least remove the windows 7 option from the grub loader?

---

### Post by oldfred on 2013-01-28
I posted above two links with users with two efi bootable drives. I think one is where Yann fixed Boot-Repair to recognize two drives and create a correct efi chain load entry.

Grub has a bug and does not create correct chain entries. Probably best for now to turn off os-prober.
With two drives you change the chain load entry to the Window's drive efi partition not the Ubuntu  drive efi partition.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by magnet18 on 2013-01-28
That worked and the problem is now solved! :D

I first turned off the OS probing as suggested, ran
```
sudo update-grub
```
rebooted, that got rid of the broken windows 7 links

then followed steps 6-8 of post #14 is the thread you posted earlier, which are 
```
sudo blkid
```

look for the vfat partition and in /etc/grub.d/40_custom add-

```
menuentry "Windows 7" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root XXXX-XXXX
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```

replacing XXXX-XXXX with the UUID of the vfat partition

this creates a bootable windows 7 option in the grub bootloader

Thankyou all for all your help!

---

