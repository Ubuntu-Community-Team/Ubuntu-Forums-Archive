---
title: "error: no such device... grub rescue&gt;"
date: 2015-03-10
forum: General Help
---

### Post by nick176 on 2015-03-10
i have win7, and tried to install dual boot ubuntu.
after install ubuntu, when turning on laptop... "error: no such device:..."
i tried all order posted terminal "boot-repair", win repair "bootrec.exe"... nothing changed...
even i pulled out the hard drive, then turned on the laptop... "error: no such device:..."

how can i fix this?

---

### Post by Bashing-om on 2015-03-11
nick176; Hi !

To start the ball rolling, show us what we are working with.
Boot the liveDVD(USB) - the ubuntu install media - to a terminal.
Post back - Between Code tags -  the results of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and we will know where to install the boot code.

Might be
[INDENT][INDENT]as easy as that
[/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-11
ok... 

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x13c4a646

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1           2048  27934719  27932672  13.3G 27 Hidden NTFS WinRE
/dev/sda2       27934720  28651519    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda3  *    28651520 976769023 948117504 452.1G  7 HPFS/NTFS/exFAT

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9cb32413

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdb1           2048 23519231 23517184 11.2G 84 OS/2 hidden C: drive
/dev/sdb2       23521278 62531583 39010306 18.6G  5 Extended
/dev/sdb5  *    23521280 54345727 30824448 14.7G 83 Linux
/dev/sdb6       54347776 62531583  8183808  3.9G 82 Linux swap / Solaris

Disk /dev/sdc: 15.1 GiB, 16228810752 bytes, 31696896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *    18192 31696895 31678704 15.1G  c W95 FAT32 (LBA)

---

### Post by nick176 on 2015-03-11
and for parted -l

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  14.3GB  14.3GB  primary  ntfs         diag
 2      14.3GB  14.7GB  367MB   primary  ntfs
 3      14.7GB  500GB   485GB   primary  ntfs         boot


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  12.0GB  12.0GB  primary                   irst
 2      12.0GB  32.0GB  20.0GB  extended
 5      12.0GB  27.8GB  15.8GB  logical   ext4            boot
 6      27.8GB  32.0GB  4190MB  logical   linux-swap(v1)


Model: Sony Storage Media (scsi)
Disk /dev/sdc: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      9314kB  16.2GB  16.2GB  primary  fat32        boot, lba

---

### Post by nick176 on 2015-03-11
scary... even no hard drive, no usb... still boot into grub rescue...

Nick

---

### Post by Bashing-om on 2015-03-11
nick176; Humm ...

Are you booting ubuntu by setting in your bios the 1st boot priority to that of the SSD ?
Might be best to explicitly install ubuntu's boot code;
Boot the liveDVD(USB) - the install medium to a terminal:
Re-install the boot code to the MBR:
```

sudo fdisk -lu ##to make sure that the SSD is still seen as 'sdb'
sudo mount /dev/sdb5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

Reboot, and reset in bios to boot from the SSD.
Do you now boot ?
When booting, do you get ubuntu's grub boot menu ?
IF not can you get the grub menu when ->
Booting as soon as the bios screen clears, depress and hold the right shift key -> grub boot menu ?

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-11
did as you said...
still the same...

i wanna cry....

i mean i even tried removed the hard drive and turn on the computer and it still the same...

---

### Post by Bashing-om on 2015-03-11
nick176; Now now,

All problems do have solutions. We just have not poked at it in a responsive way.

Is this a UEFI capable system ? If so the key that grub recognizes is the escape key. There is but a small window of oportunity for the key to be seen. 
With the boot code re-installed to the MBR of the SSD, and we know that the config files reside in the sdb5 partition, should be able to at least get a grub boot menu.
So in bios the SSD is set for 1st boot priority,
rebooting as soon as bios screen clears repeatedly depress and release the escape key, Now do you get the grub boot menu ?

[INDENT][INDENT]it is a process
[INDENT][INDENT][INDENT]follow the trail
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-11
the only thing appears when not with the Live-usb is the

error: no such device: 844c8378-943a-45b8-83b7-295a0f2636a3
Entering rescue mode...
grub rescue>

even i pull out the hard drive...

never seen grub menu appears.

---

### Post by Bashing-om on 2015-03-11
nick176; HoKay ;

That is a bit more info and it is significant, Let's look and see how it " that long string of characters " relates :
Boot the live(USB) to terminal:
We will mount the ubuntu install filesystem and take a look at things:
With both drives connected:
terminal codes:
```

sudo fdisk -lu

```
is the SSD still seen as 'sdb' ?
access the install:
```

sudo mkdir /mnt/look
sudo mount /dev/sdb5 /mnt/look

```

Now we have a looksee:
Post back the outputs:
```

sudo blkid
cat /mnt/look/etc/fstab
cat /mnt/look/boot/grub/grub.cfg

```

OK, we done looking. Whatever one mounts manually one is responsible to UNmount - else file system corruption will result at some level.
UNmount the install:
```

sudo umount /mnt/look

```
Now we compare the numbers, and again see where we go from here,

[INDENT][INDENT]are we having fun now ?
[/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-11
for sudo fdisk -lu

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9cb32413

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdb1           2048 23519231 23517184 11.2G 84 OS/2 hidden C: drive
/dev/sdb2       23521278 62531583 39010306 18.6G  5 Extended
/dev/sdb5  *    23521280 54345727 30824448 14.7G 83 Linux
/dev/sdb6       54347776 62531583  8183808  3.9G 82 Linux swap / Solaris

for sudo blkid

/dev/sda1: LABEL="Recovery" UUID="F01077A110776E0A" TYPE="ntfs" PARTUUID="13c4a646-01" 
/dev/sda2: LABEL="System Reserved" UUID="600EA7910EA75F32" TYPE="ntfs" PARTUUID="13c4a646-02" 
/dev/sda3: UUID="D236A8EC36A8D2B1" TYPE="ntfs" PARTUUID="13c4a646-03" 
/dev/sdb5: UUID="844c6378-943a-45b8-83b7-295a0f2636a3" TYPE="ext4" PARTUUID="9cb32413-05" 
/dev/sdc1: LABEL="UUI" UUID="1D13-2124" TYPE="vfat" PARTUUID="c3072e18-01" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: PARTUUID="9cb32413-01" 
/dev/sdb6: UUID="bba22369-8f67-4110-9a05-797ef3ab8a82" TYPE="swap" PARTUUID="9cb32413-06" 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=844c6378-943a-45b8-83b7-295a0f2636a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bba22369-8f67-4110-9a05-797ef3ab8a82 none            swap    sw              0       0


ubuntu@ubuntu:~$ cat /mnt/look/boot/grub/grub.cfg
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
   set default="menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os  'osprober-chain-D236A8EC36A8D2B1' {"
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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
else
  search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-844c6378-943a-45b8-83b7-295a0f2636a3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
    linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-844c6378-943a-45b8-83b7-295a0f2636a3' {
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-advanced-844c6378-943a-45b8-83b7-295a0f2636a3' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
        else
          search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-recovery-844c6378-943a-45b8-83b7-295a0f2636a3' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
        else
          search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-23-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
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



this is really fun...

---

### Post by Bashing-om on 2015-03-11
nick176; Well !!

This I think is a no no in the config file:
> 
set root=[color=red]'hd0,msdos5[/color]'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-bios=[color=red]hd0,msdos5[/color] --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 844c6378-943a-45b8-83b7-295a0f2636a3

which says it is to look on the 1st hard drive (hd0) in partition 5 for the config files... no no they are on 2nd hard drive !

I must study about best practice to correct this. Presently my eyes are crossing and my brain is fuzzy. We will pick this back up in my AM.

[INDENT][INDENT]1 giant step forward for 'buntu kind
[/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-12
thank you very much for your help 

and have a good sleep.

---

### Post by Bashing-om on 2015-03-12
nick176; I'm Bacckkk ..

So, we know the config files are in error, our options:
a) Spend the time and effort - and we learn in this process - to correct the error(s)
b) We purge grub and it's config files and re-create them, see what results
c) We take the faster approach and (RE-)install the operating system, paying attention to where grub gets installed this time.

[INDENT][INDENT]it is your time, your effort and your system
[INDENT][INDENT][INDENT]your call
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-12
hello Bashing-om,

i would like to go with option a if you can help me.

thanks,

---

### Post by Bashing-om on 2015-03-12
nick176; I like the way you think.

I am all for stepping up on the learning curve,

Will take me a bit of time to flounder out where that field [(hd0,msdos5)] is being parsed from.
I thought I knew, but I was wrong. Welcome to the learning curve.
Anyway, soon as I discover, I will be back and we continue on to get booted.

'nother definition 
[INDENT][INDENT][INDENT]of "something else"
[/INDENT][/INDENT][/INDENT]

---

### Post by nick176 on 2015-03-12
hello Bashing-om,

take your time... let me know where should i start when you are ready.

thank you,

---

### Post by oldfred on 2015-03-12
Is this an UltraBook with Intel SRT or similar?

What brand/model computer?

Newer versions of Ubuntu seem to work if drives are reset to AHCI not Intel SRT so grub then installs correctly. Older versions of Ubuntu often required the RAID meta-data that Linux sees on drive from the Intel SRT to be erased first. But even then it can be recreated after grub is installed.
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

### Post by nick176 on 2015-03-12
sony vaio svt13112fxs

Storage Type: Serial ATA Hybrid 
Storage Capacity: 500GB + 32GB MLC Hybrid

---

### Post by oldfred on 2015-03-13
Do you have AHCI on in BIOS?

The set root= while it should be correct drive, the search by UUID should override it and let you boot correct drive. Either the fixed set root = command or a search by UUID should also work without the other, if correct drive/partition or UUID.

---

### Post by Bashing-om on 2015-03-13
nick176; oldfred; :)

My bash skills are not up to the task to see where/how (hd0,msdos5) gets parsed from. oldfred I sure am glad you joined this thread !
As that field gets overridden it is not a factor, so where now is the problem booting this install ?
I do not know and will gladly follow your lead.
> 
Storage Type: Serial ATA Hybrid 

Are we looking at meta data in the boot sector of the SSD ? And IF we were to remove it, how would that effect Windows ?

[INDENT][INDENT]OH that learning curve
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-03-13
RAID meta-data is not in MBR.

I also am not sure why it is not booting.

Perhaps some more detail, the Summary report from Boot-Repair may show more?
Post link that this gives when you run the summary report.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nick176 on 2015-03-16
```
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 844c6378-943a-45b8-83b7-295a0f2636a3 root hd1,msdos5 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/i386-pc/core.img 
                       /boot/grub/i386-pc/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 61808 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,934,719    27,932,672  27 Hidden NTFS (Recovery Environment)
/dev/sda2          27,934,720    28,651,519       716,800   7 NTFS / exFAT / HPFS
/dev/sda3    *     28,651,520   976,769,023   948,117,504   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    23,519,231    23,517,184  84 OS/2 hidden C: drive
/dev/sdb2          23,521,278    62,531,583    39,010,306   5 Extended
/dev/sdb5    *     23,521,280    54,345,727    30,824,448  83 Linux
/dev/sdb6          54,347,776    62,531,583     8,183,808  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.1 GiB, 16228810752 bytes, 31696896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *         18,192    31,696,895    31,678,704   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:                                                   
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:1 F01077A110776E0A                       ntfs       Recovery
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:2 600EA7910EA75F32                       ntfs       System Reserved
/dev/sda1        F01077A110776E0A                       ntfs       Recovery
/dev/sda2        600EA7910EA75F32                       ntfs       System Reserved
/dev/sda3        D236A8EC36A8D2B1                       ntfs       
/dev/sdb1                                                          
/dev/sdb5        844c6378-943a-45b8-83b7-295a0f2636a3   ext4       
/dev/sdb6        bba22369-8f67-4110-9a05-797ef3ab8a82   swap       
/dev/sdc1        1D13-2124                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Mar 17 02:27 ata-Hitachi_HTS545050A7E380_120417TA9512GZKSVGYX -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 17 02:27 ata-Hitachi_HTS545050A7E380_120417TA9512GZKSVGYX-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 17 02:27 ata-Hitachi_HTS545050A7E380_120417TA9512GZKSVGYX-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar 17 02:27 ata-Hitachi_HTS545050A7E380_120417TA9512GZKSVGYX-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Mar 17 02:27 ata-SAMSUNG_MZMPC032HBCD-00000_S0VSNEAC437633 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 17 02:27 ata-SAMSUNG_MZMPC032HBCD-00000_S0VSNEAC437633-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 17 02:24 ata-SAMSUNG_MZMPC032HBCD-00000_S0VSNEAC437633-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 17 02:24 ata-SAMSUNG_MZMPC032HBCD-00000_S0VSNEAC437633-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 17 02:24 ata-SAMSUNG_MZMPC032HBCD-00000_S0VSNEAC437633-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-name-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8: -> ../../dm-0
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-name-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-name-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:2 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-uuid-DMRAID-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8: -> ../../dm-0
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-uuid-part1-DMRAID-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8: -> ../../dm-1
lrwxrwxrwx 1 root root 10 Mar 17 02:27 dm-uuid-part2-DMRAID-isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8: -> ../../dm-2
lrwxrwxrwx 1 root root 10 Mar 17 02:27 raid-isw_dihbjgbhcj_71AT5921ZGSKGVXY_N8:-part1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Mar 17 02:27 raid-isw_dihbjgbhcj_71AT5921ZGSKGVXY_N8:-part2 -> ../../dm-2
lrwxrwxrwx 1 root root  9 Mar 17 02:24 usb-Sony_Storage_Media_AB4211108233000129-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Mar 16 21:56 usb-Sony_Storage_Media_AB4211108233000129-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Mar 17 02:27 wwn-0x5000cca654f51e75 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 17 02:27 wwn-0x5000cca654f51e75-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 17 02:27 wwn-0x5000cca654f51e75-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar 17 02:27 wwn-0x5000cca654f51e75-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Mar 17 02:27 wwn-0x5002538043584d30 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 17 02:27 wwn-0x5002538043584d30-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 17 02:24 wwn-0x5002538043584d30-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 17 02:24 wwn-0x5002538043584d30-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 17 02:24 wwn-0x5002538043584d30-part6 -> ../../sdb6

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:
isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:1
isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
   set default="menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os  'osprober-chain-D236A8EC36A8D2B1' {"
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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
else
  search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-844c6378-943a-45b8-83b7-295a0f2636a3' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
    linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.16.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-844c6378-943a-45b8-83b7-295a0f2636a3' {
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-advanced-844c6378-943a-45b8-83b7-295a0f2636a3' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
        else
          search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-recovery-844c6378-943a-45b8-83b7-295a0f2636a3' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
        else
          search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /boot/vmlinuz-3.16.0-23-generic root=UUID=844c6378-943a-45b8-83b7-295a0f2636a3 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-23-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-D236A8EC36A8D2B1' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  D236A8EC36A8D2B1
    else
      search --no-floppy --fs-uuid --set=root D236A8EC36A8D2B1
    fi
    parttool ${root} hidden-
    chainloader +1
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=844c6378-943a-45b8-83b7-295a0f2636a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bba22369-8f67-4110-9a05-797ef3ab8a82 none            swap    sw              0       0
--------------------------------------------------------------------------------

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  b7 dd 80 47 1c 0e 3e 02  38 22 00 00 00 00 00 00  |...G..>.8"......|
00000010  00 00 00 00 00 00 00 00  04 7f 00 00 00 00 00 00  |................|
00000020  00 80 00 00 00 00 03 00  00 00 80 56 00 00 00 00  |...........V....|
00000030  00 00 00 00 98 26 5c 0f  55 e0 ff 80 7c 09 7a 57  |.....&\.U...|.zW|
00000040  ed fb ff 3f d0 03 a0 50  70 83 fa 44 e4 a3 df ba  |...?...Pp..D....|
00000050  17 b7 7a 10 ff 4c cf 3c  eb 78 c3 dc 74 e6 de b5  |..z..L.<.x..t...|
00000060  1e 01 47 8e 3c d2 9c d8  3f 45 ed d2 b6 34 6e b6  |..G.<...?E...4n.|
00000070  c4 c3 ff ab fa 57 9c 4b  8d 13 df cf c2 50 f4 7a  |.....W.K.....P.z|
00000080  2d bf 57 05 61 0b d1 8d  da 8f 6f c8 0a 95 0d 9f  |-.W.a.....o.....|
00000090  1e 98 96 4a 53 4e 6c b1  2b 5b bd 6f 4c db c9 bd  |...JSNl.+[.oL...|
000000a0  53 8b ed e6 2c 4a 6a 3b  cd d3 1e 66 a6 5f 5e 76  |S...,Jj;...f._^v|
000000b0  93 9f dd 4c 01 0d c9 ad  e3 ee c7 60 70 7e 66 b5  |...L.......`p~f.|
000000c0  d3 ce 68 d0 e0 5c cd 9a  01 a4 00 10 88 01 01 a1  |..h..\..........|
000000d0  03 20 00 96 53 80 01 90  02 04 00 9a 01 12 01 90  |. ..S...........|
000000e0  01 00 84 98 2b 90 10 90  02 04 04 d0 83 41 00 90  |....+........A..|
000000f0  43 04 44 00 03 60 00 10  03 04 04 80 1a 41 00 90  |C.D..`.......A..|
00000100  41 04 04 80 1a 48 00 90  3f 6f 8f b8 e6 f5 dc d3  |A....H..?o......|
00000110  f3 9d 29 c1 15 00 fe 7a  2b 58 85 5f 24 2a 1e 3c  |..)....z+X._$*.<|
00000120  f5 a3 05 54 b1 8f 17 58  83 c6 25 45 df 6d 1a b3  |...T...X..%E.m..|
00000130  59 47 2f e6 21 8a 8e 62  3d b6 04 44 be b3 29 e7  |YG/.!..b=..D..).|
00000140  1b b3 53 5b 0d 51 b2 65  fb c0 5c 85 be 89 6b be  |..S[.Q.e..\...k.|
00000150  6f 7a 8f c1 dd 3c 29 37  d7 cd 75 39 74 f8 50 6f  |oz...<)7..u9t.Po|
00000160  47 43 7d bf 64 3f ea 12  e6 7f 93 d4 f5 3c f0 6f  |GC}.d?.......<.o|
00000170  7b 2b 1c e6 75 a0 be 8b  97 60 f8 4d f1 88 00 f1  |{+..u....`.M....|
00000180  30 2b 00 20 00 20 80 59  41 00 04 82 91 c0 10 21  |0+. . .YA......!|
00000190  c2 02 44 44 82 d1 01 30  c3 02 44 04 03 89 11 10  |..DD...0..D.....|
000001a0  83 02 04 c0 01 c1 11 01  c3 00 04 e0 01 d4 11 01  |................|
000001b0  c2 02 00 a4 41 4c 01 20  c3 02 40 c0 00 84 10 21  |....AL. ..@....!|
000001c0  c0 00 40 60 18 d0 10 20  81 02 00 24 01 04 00 21  |..@`... ...$...!|
000001d0  42 00 00 40 19 00 00 21  80 00 00 04 11 94 70 21  |B..@...!......p!|
000001e0  03 00 40 04 01 00 00 01  01 02 40 00 09 00 10 00  |..@.......@.....|
000001f0  02 02 40 40 02 20 00 01  00 02 00 00 00 02 00 01  |..@@. ..........|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

{All_DMRaid} 

=============================== StdErr Messages: ===============================

ERROR: opening "/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\87N8:"
cat: write error: Broken pipe
cat: write error: Broken pipe
ERROR: opening "/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\87N8:"
File descriptor 9 (/proc/6400/mounts) leaked on lvs invocation. Parent PID 17662: bash
File descriptor 63 (pipe:[51724]) leaked on lvs invocation. Parent PID 17662: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-03-17__02h24 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in live-session (Ubuntu 14.10, utopic, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash -- BOOT_IMAGE=/casper/vmlinuz.efi
ls: cannot access /home/usr/.config: No such file or directory
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb1 : Error code 12
mount -r /dev/sdb1 /mnt/boot-sav/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb1 : Error code 12

=================== os-prober:


=================== blkid:
/dev/sda1: LABEL="Recovery" UUID="F01077A110776E0A" TYPE="ntfs" PARTUUID="13c4a646-01"
/dev/sda2: LABEL="System Reserved" UUID="600EA7910EA75F32" TYPE="ntfs" PARTUUID="13c4a646-02"
/dev/sda3: UUID="D236A8EC36A8D2B1" TYPE="ntfs" PARTUUID="13c4a646-03"
/dev/sdb5: UUID="844c6378-943a-45b8-83b7-295a0f2636a3" TYPE="ext4" PARTUUID="9cb32413-05"
/dev/sdc1: LABEL="UUI" UUID="1D13-2124" TYPE="vfat" PARTUUID="c3072e18-01"
/dev/loop0: TYPE="squashfs"
/dev/sdb6: UUID="bba22369-8f67-4110-9a05-797ef3ab8a82" TYPE="swap" PARTUUID="9cb32413-06"
/dev/sdb1: PARTUUID="9cb32413-01"

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb1 : Error code 12
mount -r /dev/sdb1 /mnt/boot-sav/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb1 : Error code 12
Windows not detected by os-prober on sda3.
Linux not detected by os-prober on sdb5. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdb5/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct 22 19:12 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Oct 16 09:48 00_header
-rwxr-xr-x 1 root root  6058 Oct 15 12:28 05_debian_theme
-rwxr-xr-x 1 root root 11611 Oct 16 09:48 10_linux
-rwxr-xr-x 1 root root 10418 Oct 16 09:48 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Oct 16 09:48 30_os-prober
-rwxr-xr-x 1 root root  1416 Oct 16 09:48 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 16 09:48 40_custom
-rwxr-xr-x 1 root root   216 Oct 16 09:48 41_custom
-rw-r--r-- 1 root root   483 Oct 16 09:48 README




=================== sdb5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-D236A8EC36A8D2B1' {"
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
This live-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x00000000AAFFD000 000236 (v01 Sony   VAIO     20120430 ACPI 00040000)
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sdb5    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb5.
sdb1    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  14.3GB  14.3GB  primary  ntfs         diag
2      14.3GB  14.7GB  367MB   primary  ntfs
3      14.7GB  500GB   485GB   primary  ntfs         boot


Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type      File system     Flags
1      1049kB  12.0GB  12.0GB  primary                   irst
2      12.0GB  32.0GB  20.0GB  extended
5      12.0GB  27.8GB  15.8GB  logical   ext4            boot
6      27.8GB  32.0GB  4190MB  logical   linux-swap(v1)


Model: Sony Storage Media (scsi)
Disk /dev/sdc: 16.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      9314kB  16.2GB  16.2GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA Hitachi HTS54505:;
1:1049kB:14.3GB:14.3GB:ntfs::diag;
2:14.3GB:14.7GB:367MB:ntfs::;
3:14.7GB:500GB:485GB:ntfs::boot;

BYT;
/dev/sdb:32.0GB:scsi:512:512:msdos:ATA SAMSUNG MZMPC032:;
1:1049kB:12.0GB:12.0GB:::irst;
2:12.0GB:32.0GB:20.0GB:::;
5:12.0GB:27.8GB:15.8GB:ext4::boot;
6:27.8GB:32.0GB:4190MB:linux-swap(v1)::;

BYT;
/dev/sdc:16.2GB:scsi:512:512:msdos:Sony Storage Media:;
1:9314kB:16.2GB:16.2GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE            SIZE LABEL           MODEL            UUID
sda   disk isw_raid_member 465.8G                 Hitachi HTS54505
sda1  part ntfs             13.3G Recovery                         F01077A110776E0A
sda2  part ntfs              350M System Reserved                  600EA7910EA75F32
sda3  part ntfs            452.1G                                  D236A8EC36A8D2B1
sdb   disk isw_raid_member  29.8G                 SAMSUNG MZMPC032
sdb1  part                  11.2G
sdb2  part                     1K
sdb5  part ext4             14.7G                                  844c6378-943a-45b8-83b7-295a0f2636a3
sdb6  part swap              3.9G                                  bba22369-8f67-4110-9a05-797ef3ab8a82
sdc   disk                  15.1G                 Storage Media
sdc1  part vfat             15.1G UUI                              1D13-2124
loop0 loop squashfs            1G

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sdb      0  0  0 running
sdb1     0  0  0
sdb2     0  0  0
sdb5     0  0  0         /mnt/boot-sav/sdb5
sdb6     0  0  0
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,nodev,noexec,nosuid)
sysfs on /sys type sysfs (rw,nodev,noexec,nosuid)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw,uid=0,gid=0,mode=0755,size=1024)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,nodev,noexec,nosuid,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,nodev,noexec,nosuid,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,noexec,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog media0 mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb5 sdb6 sdc sdc1 sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uinput urandom v4l vga_arbiter video0 zero
ls /dev/mapper:  control
ls sda1/efi:
ls sda1: Autorun
Autorun.inf
boot
bootmgr
bootmgr.efi
data
EFI
etfsboot.com
HDD
idf
Recovery
snyhdrcv.ini
Sony
sources
System Volume Information  . Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 37 aa 01 00 00 00 00  |.........7......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  0a 6e 77 10 a1 77 10 f0  |.........nw..w..|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 aa 01  |........?....@..|
00000020  00 00 00 00 80 00 80 00  ff ef 0a 00 00 00 00 00  |................|
00000030  aa 74 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.t..............|
00000040  f6 00 00 00 01 00 00 00  32 5f a7 0e 91 a7 0e 60  |........2_.....`|
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

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 b5 01  |........?....0..|
00000020  00 00 00 00 80 00 80 00  ff 1f 83 38 00 00 00 00  |...........8....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  b1 d2 a8 36 ec a8 36 d2  |...........6..6.|
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

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.9G   68M  1.9G   4% /
udev           devtmpfs   1.9G  4.0K  1.9G   1% /dev
tmpfs          tmpfs      386M  1.1M  385M   1% /run
/dev/sdc1      vfat        16G  1.1G   14G   8% /cdrom
/dev/loop0     squashfs   1.1G  1.1G     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.9G  1.2M  1.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      1.9G  240K  1.9G   1% /run/shm
none           tmpfs      100M   68K  100M   1% /run/user
/dev/sda1      fuseblk     14G   13G  1.1G  92% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    350M   38M  313M  11% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    453G  108G  345G  24% /mnt/boot-sav/sda3
/dev/sdb5      ext4        15G  4.0G  9.7G  30% /mnt/boot-sav/sdb5

=================== fdisk -l:

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x13c4a646

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1           2048  27934719  27932672  13.3G 27 Hidden NTFS WinRE
/dev/sda2       27934720  28651519    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda3  *    28651520 976769023 948117504 452.1G  7 HPFS/NTFS/exFAT

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9cb32413

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdb1           2048 23519231 23517184 11.2G 84 OS/2 hidden C: drive
/dev/sdb2       23521278 62531583 39010306 18.6G  5 Extended
/dev/sdb5  *    23521280 54345727 30824448 14.7G 83 Linux
/dev/sdb6       54347776 62531583  8183808  3.9G 82 Linux swap / Solaris

Disk /dev/sdc: 15.1 GiB, 16228810752 bytes, 31696896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *    18192 31696895 31678704 15.1G  c W95 FAT32 (LBA)



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS).
The boot flag will be placed on sdb5.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems  fix-windows-boot


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.

ntfsfix /dev/sda2
Refusing to operate on read-write mounted device /dev/sda2.

ntfsfix /dev/sda3
Refusing to operate on read-write mounted device /dev/sda3.

fsck -fyM /dev/sdb5
fsck from util-linux 2.25.1

fsck -fyM /dev/sdb1
fsck from util-linux 2.25.1
e2fsck 1.42.10 (18-May-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
or
e2fsck -b 32768 <device>

NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb1 : Error code 12
mount -r /dev/sdb1 /mnt/boot-sav/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb1 : Error code 12
Quantity of real Windows: 1
WinSE in sda3
Copied Win boot files from sda2 to sda3

Reinstall the GRUB of sdb5 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: Sony Corporation Device [104d:90a8]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-15,grub-install (GRUB) 2.

Reinstall the GRUB of sdb5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: Sony Corporation Device [104d:90a8]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-15,grub-install (GRUB) 2.

Reinstall the GRUB of sdb5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

chroot /mnt/boot-sav/sdb5 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-23-generic
Found initrd image: /boot/initrd.img-3.16.0-23-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sdb1 : Error code 12
mount -r /dev/sdb1 /mnt/boot-sav/sdb1
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sdb1 : Error code 12
Unhide GRUB boot menu in sdb5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (32.0GB) disk!
```

---

### Post by nick176 on 2015-03-16
sorry for the late reply... i went to some no internet location for the weekend...

Nick.

---

### Post by oldfred on 2015-03-17
Are you booting from sdb?
Can you at grub menu delete the entire search line?

It looks like you left Windows hibernated which locks up all your NTFS partitions. The NTFS driver (fuse?) does not open NTFS partitions with chkdsk or hibernation flags set. So either all your NTFS partitions need chkdsk or you left it hibernated.

But when grub boots it sets the default boot partition with the set root =, but since drives can change it also then uses the search by UUID line to scan the entire system for the correct UUID. I think since it cannot see the NTFS partitions it is hanging up. That really should be a bug since the correct partition by UUID is available.

At grub menu use e for edit and scroll down. leave the set root line but delete all the red. If you boot from sdb directly change hd1 to hd0 also.
     set root='hd1,msdos5'
    [COLOR=#ff0000]if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  844c6378-943a-45b8-83b7-295a0f2636a3
    else
      search --no-floppy --fs-uuid --set=root 844c6378-943a-45b8-83b7-295a0f2636a3
    fi
[/COLOR][COLOR=#000000]
Please use code tags or just post line to summary report.[/COLOR][COLOR=#ff0000]
[/COLOR]

---

### Post by nick176 on 2015-03-17
the thing is... i have never seen grub menu from first installed... only "grub rescue>"

or... how can i get into grub menu from there?

---

### Post by oldfred on 2015-03-18
You may be able to manually boot. 
It may be just easier to use Boot-Repair and its total uninstall/reinstall of grub in advanced.

This depends a lot on which drive you are booting from with BIOS. If the sdb drive, it still is hd0 that you use as boot drive is always hd0. If you have BIOS set to boot any other drive then you may even have to experiment if hd1 or hd2.

# is a comment, do not copy or type.
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
# Do you see (hd0), (hd0,5) ? If not hd0,5 change to correct drive, partition.
ls
configfile (hd0,5)/boot/grub/grub.cfg

# If above does not work then try this:
      
 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

### Post by u2nTu on 2015-04-13
Looks like nick has left the building, a bummer since that leaves this thread like a mystery novel without an ending. What ultimately worked? Unknown.

Having a similar problem myself, with grub switching hd0 (sda) and hd1, which forces manual correction at 'grub rescue>' on each boot, a real PITA. Searching on...

---

