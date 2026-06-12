---
title: "Gave up waiting for root device."
date: 2015-02-28
forum: General Help
---

### Post by marc-andr2 on 2015-02-28
Hi everyone! 

I haven't been able to get rid of this boot issue and worked on it for days now. I have succesfully installed distros and ran them fine before, the disk works fine 'cause I've checkdisked the hell out of it.


Here is the message I have : 

-----------------------------------------------------------------------------------------------------------

Gave up waiting on root device. Common problems: 

 - Boot args (cat /proc/cmdline)
      - Check rootdelay= (did the system wait long enough?)
      - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/421f36a9-5b65-4cd3-96af-e5d64e190c65 does not exist.
Dropping to a shell!ààBusybox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs) _

------------------------------------------------------------------------------------------------------------

Then my computer wether stops responding OR gets stuck in a loop where it tries to install whatever is connected to USB (MOUSE) in a loop and always fails and tries again. 

Here are the things I have tried (googling the issue) : 

1. Deleting partition table, rebuilding the table + partitions (tried many configurations and re-installed ubuntu many times) I tried a single ext4 partition with / mount point. Tried a 32Gb for everything and a 400Gb for /home. I even booted into OSX (hackintosh) to format the drive to fat32, then reboot using the live USB key, reinstall... All of this never worked. 

2. Tried fsck

3. From live CD : sudo grub-install /dev/sdd1 : sudo update grub

4. From live CD install grub / update grub as CHROOT 

5. I also tried many other things but since I am frustrated and have tried so many things, I don't think I can recall exactly everything I did.


Here is my hardware specs if it can help : 

Gigabyte Z68XP-UD4
Sandy Bridge - i7 2600K 
HyperX 1600Mhz DDR (16Gb)
Main drive Samsung 120Gb SSD (OSX with Chimera bootloader (Unibeast / multibeast installation)
WD 500Gb (Linux install or at least, the drive that I'm trying to use.)
2Tb drive for data and backups, etc.
Airport extreme adapter ripped off an old imac, soldered to a PCI adapter
MSI Geforce GTX 760 twin frozr (2Gb) (2 screens connected / one via HDMI and the other via DVI)

Other stuff connected : Zoom R16 recording interface, HP Deskjet all in one printer/scanner

---

### Post by tgalati4 on 2015-02-28
What is the output of:

```
cat /proc/cmdline
```

Perhaps you don't have the boot flag set on the same partition that you have grub installed to.  You can check with a LiveUSB session and use *gparted* to inspect and change it if necessary under "manage flags".

Also post the output of the disk partitions:

```
sudo fdisk -l
```

Pull out the 120 GB SSD.  I'm sure that is tripping up the drive enumeration.

---

### Post by marc-andr2 on 2015-02-28
```
ubuntu@ubuntu:~$ cat /proc/cmdline
initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern 
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT
/dev/sda2   *           0           0           0    0  Empty

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2  3907029167  1953514583   af  HFS / HFS+
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 32.0 GB, 32008830976 bytes
255 heads, 63 sectors/track, 3891 cylinders, total 62517248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    62517247    31258608    c  W95 FAT32 (LBA)

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df45c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2   976773167   488386583   83  Linux
ubuntu@ubuntu:~$
```

---

### Post by marc-andr2 on 2015-02-28
I'm confused. But I can explain everything there. 

Disk /dev/sda 
        This is my SSD, it has OSX and it boots perfectly fine. 

Disk /dev/sdb
        This is my drive called "Minerva" and it's 2Tb drive used to store my pictures / videos / music, etc.

Disk /dev/sdc
        This is my LIVE USB UBUNTU 14.04 LTS

Disk /dev/sdd
        This is where I'm trying to install UBUNTU as it always worked before, 

I just formatted to switch from ubuntu 12 to Ubuntu Studio, I liked the apps that comes in Ubuntu studio a lot but it does not recognise my ZOOM R16, so I was going to follow some instructions online on how to make it work. I just decided to start from scratch, format,I did not do anything special other than format with Gparted before the installation, installed ubuntu 14.04 as usual and since, I tested the USBkey, rebuilt the USBkey using unetbootin on my laptop (windows 7).... Still nothing.

---

### Post by marc-andr2 on 2015-03-01
additionaly, I checked with parted : 

```
 
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      20.5kB  210MB  210MB  fat32        EFI System Partition  boot
 2      210MB   119GB  119GB  hfs+         HACKINTOSH
 3      119GB   120GB  650MB  hfs+         Recovery HD


Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      1024B  2000GB  2000GB  primary  hfs+         boot


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  32.0GB  32.0GB  primary  fat32        boot, lba


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      1024B  500GB  500GB  primary  ext4         boot


```

I found places where they suggest to add rootdelay=XXX to grub menu.lt, that file doesn't seem to be where they suggest it should be. 

But here's my grub.cfg : 

```

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
set root='hd3,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
else
  search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd3,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    else
      search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    fi
    linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-30-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-advanced-c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
        else
          search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-generic-recovery-c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
        else
          search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
        fi
        echo    'Loading Linux 3.16.0-30-generic ...'
        linux    /boot/vmlinuz-3.16.0-30-generic root=UUID=c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-30-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd3,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    else
      search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd3,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    else
      search --no-floppy --fs-uuid --set=root c95d47fa-e0d3-4a54-b679-1c1d94cf6fa0
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

```

---

### Post by marc-andr2 on 2015-03-01
I'm trying to install once again, this time I'm installing using : install ubuntu alongside... Just to see if the modification it'll make to grub might get me through... and it popped up : Executing grub-install /dev/sda failed. I know linux can't write to my HFS+ partition. Why would it try to do that tho? I asked the installer to install bootloader to sdd... I'm just about to throw my fist through my screens and throw that thing out the window...

---

### Post by marc-andr2 on 2015-03-01
nano /etc/fstab (while chroot) : 

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd1 during installation
UUID=0f3554b3-3704-43fb-9358-9dbc69e8834d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=ac42196f-3674-4fb2-8652-cb44184af99f none            swap    sw              0       0

```

blkid (while chroot) : 

```

/dev/sda1: LABEL="EFI" UUID="67E3-17ED" TYPE="vfat" 
/dev/sda2: UUID="08440460-cf60-3686-af75-b65fa94eef8f" LABEL="HACKINTOSH" TYPE="hfsplus" 
/dev/sda3: UUID="8309a303-f6a7-3ebe-b7b9-b1ecae7647ea" LABEL="Recovery HD" TYPE="hfsplus" 
/dev/sdb1: UUID="60bbb74d-252a-343b-9ae1-55e0d1c73b49" LABEL="Minerva" TYPE="hfsplus" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="Lexar" UUID="93A0-E59E" TYPE="vfat" 
/dev/sdd1: UUID="0f3554b3-3704-43fb-9358-9dbc69e8834d" TYPE="ext4" 
/dev/sdd5: UUID="ac42196f-3674-4fb2-8652-cb44184af99f" TYPE="swap" 

```

---

### Post by marc-andr2 on 2015-03-01
I'm just so lost right now... 

I even booted in OSX, used diskutil to repartition the drive with a GPT table with a HFS+ partition. I copied a bunch of huge files to it and deleted them to see if the drive was working at all... Everything was working perfectly well without a single error. 

Booted once again with my USB LIVE (which works fine, I even rebuilt it and tested it)

Used the automatic installer using the whole disk, it told me it failed installing grub to /dev/sda, but that's my OSX drive and it's hfs+ so obviously linux can't write there. Then I had the option to install bootloader elsewhere, so I picked /dev/sdd, which is my linux 500Gb drive.

- reboot gives me the exact same error message =

  Gave up waiting on root device. Common problems: 

 - Boot args (cat /proc/cmdline)
      - Check rootdelay= (did the system wait long enough?)
      - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/421f36a9-5b65-4cd3-96af-e5d64e190c65 does not exist.
Dropping to a shell!ààBusybox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs) _

---

### Post by marc-andr2 on 2015-03-01
I just had a flash, last week I ordered an Odroid C1 and created a microSD using Disk Destroyer (dd) and I might have made some mistakes cause I had to start over a few times. 

Could Disk Destroyer cause something to the disk identification or something? Is there a way to fix it if it's the case?

---

### Post by marc-andr2 on 2015-03-01
I just did dd if=/dev/zero of=/dev/sdd bs=100M

We'll see if zeroing out everything and start from scratch worked... I'm rebooting in a minute.

---

### Post by marc-andr2 on 2015-03-01
Didn't work. Trying another distro...

---

### Post by marc-andr2 on 2015-03-01
HAHAHAHAHAHAHAHA!!!!!!

I'LL BE DAMNED!!!!!

I WASTED 3 days of my life, I want it back!

All of this time I was trying to install ubuntu 14.04 LTS... I gave up and downloaded the latest stable ubuntu studio and built my usb key... problem solved.

---

### Post by oldfred on 2015-03-01
If sda is a gpt partitioned drive, you have to have a bios_grub partition for it to install. Does not matter what partitions you have on the drive.

Drive numbers often have issues when flash drive is before drive you install into. You may have to manually boot by editing grub. Boot drive is always hd0, then other drives usually are in SATA port order. But I skipped one port and flash drive will be sdb if found, which then always changes all later drivers in order. But search by UUID should override a drive out of order, but does not always seem to work. Manually edit grub boot stanza to correct hd0,Y if booting from same drive or hdX,Y if booting from a different drive. I have had to experiment with the X until I learned how BIOS rported drives.  And edit out search line.

---

