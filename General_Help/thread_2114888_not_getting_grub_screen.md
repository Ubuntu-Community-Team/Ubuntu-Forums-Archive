---
title: "not getting grub screen"
date: 2013-02-11
forum: General Help
---

### Post by nosmokenofire on 2013-02-11
Hi all,

I'm back to humbly ask help for a new problem...

I recently removed windows from a dual boot and copied my ubuntu install from the extended partition onto the space left by windows (not without some booting issues which i managed to sort out with the help of Darko on these forums).

As I was messing about with a live CD some of the time, my boot order in BIOS was set to boot from my external usb dvd drive and I forgot to change it back, which made no difference because I only plug in the drive when I need it (when I'm already booted into ubuntu so no danger of my pc trying to boot from it).

This afternoon my daughter was watching a dvd and the media player got stuck and I ended up rebooting the computer forgetting that the dvd drive was plugged in with her dvd in it...

since then I have changed the boot order in BIOS but to no avail, I am not able to get to grub. the only way I can get into ubuntu is on a live cd. I tried a boot repair but it got stuck in the first stages (os scanner or prober or something like that). Can I try to reinstall grub from a live cd?

Thanks to anyone who can offer any advice.
Nosmokenofire.

---

### Post by Bufeu on 2013-02-11
> **nosmokenofire said:**
> Hi all,

I'm back to humbly ask help for a new problem...

I recently removed windows from a dual boot and copied my ubuntu install from the extended partition onto the space left by windows (not without some booting issues which i managed to sort out with the help of Darko on these forums).

As I was messing about with a live CD some of the time, my boot order in BIOS was set to boot from my external usb dvd drive and I forgot to change it back, which made no difference because I only plug in the drive when I need it (when I'm already booted into ubuntu so no danger of my pc trying to boot from it).

This afternoon my daughter was watching a dvd and the media player got stuck and I ended up rebooting the computer forgetting that the dvd drive was plugged in with her dvd in it...

since then I have changed the boot order in BIOS but to no avail, I am not able to get to grub. the only way I can get into ubuntu is on a live cd. I tried a boot repair but it got stuck in the first stages (os scanner or prober or something like that). **Can I try to reinstall grub from a live cd?**

Thanks to anyone who can offer any advice.
Nosmokenofire.
Yes, as long as Ubuntu finds the disk(s).
Boot from live-CD and run *sudo grub-install /dev/partition-you-want-GRUB-on*, e.g. *sudo grub-install /dev/sdb2* for putting GRUB on /dev/sdb2.

---

### Post by nosmokenofire on 2013-02-11
Bufeu,

Thanks for helping. I ran the command and this is what I got:
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```

Any ideas?

---

### Post by Bufeu on 2013-02-11
Use the flag *--boot-directory*: [http://ubuntuforums.org/showthread.php?t=2076573](http://ubuntuforums.org/showthread.php?t=2076573)

---

### Post by schragge on 2013-02-11
> **Bufeu said:**
> *--boot-directory**--root-directory*?

---

### Post by Bufeu on 2013-02-11
> **schragge said:**
> *--root-directory*?No. My manpage (*man grub-install*) says *--boot-directory*. See here: [http://manpages.ubuntu.com/manpages/precise/man8/grub-install.8.html](http://manpages.ubuntu.com/manpages/precise/man8/grub-install.8.html)

This site says *--root-directory*, though: [http://linux.die.net/man/8/grub-install](http://linux.die.net/man/8/grub-install)

Strange.

---

### Post by nosmokenofire on 2013-02-11
for the moment boot repair seems to be working (but not finished yet). I'll let you know what happens after that. Thanks.

---

### Post by schragge on 2013-02-11
> **Bufeu said:**
> Strange. Aha, I've found out. It was *--root-directory* in lucid, then changed to *--boot-directory*, but the old option name is probably still accepted by grub 1.99.

---

### Post by Bufeu on 2013-02-11
> **schragge said:**
> Aha, I've found out. It was *--root-directory* in lucid, then changed to *--boot-directory*, but the old option name is probably still accepted by grub 1.99.
Ah. Good to know. :)

---

### Post by nosmokenofire on 2013-02-11
ok so boot repair failed it just got stuck at trying to "reinstall grub on sda". I am still only booting into a live cd. I wanted to back up my files from my ubuntu install (as I'm starting to get a bit worried) but I'm not able to mount the partition, I get this message:
```
Error mounting /dev/sda1 at /media/ubuntu/a787b565-5217-4912-8cdf-64832572624d: 
Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "
/dev/sda1" "/media/ubuntu/a787b565-5217-4912-8cdf-64832572624d"' 
exited with non-zero exit status 32: mount: wrong fs type, bad option, 
bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I then tried what you suggested Bufeu and got nowhere
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_ecjaadgfhh_Volume0p1 /mnt
mount: special device /dev/mapper/isw_ecjaadgfhh_Volume0p1 does not exist
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/isw_ecjaadgfhh_Volume0
Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```I'm starting to worry about all my files, emails etc...

---

### Post by Bucky Ball on 2013-02-11
Please show the results of:

sudo blkid

Sounds like something is amiss with sda1 but don't panic yet. Can't see how you would have wiped any of your personal data.

---

### Post by nosmokenofire on 2013-02-11
here is a screenshot from gparted sda1 is my ubuntu partition with all my files and folders and emails in thunderbird etc...
does this mean that it is all gone?

Help!

---

### Post by nosmokenofire on 2013-02-11
> **Bucky Ball said:**
> Please show the results of:

sudo blkid

Sounds like something is amiss with sda1 but don't panic yet. Can't see how you would have wiped any of your personal data.
```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 12.10 i386" TYPE="iso9660" 
/dev/sda1: UUID="a787b565-5217-4912-8cdf-64832572624d" TYPE="ext4" 
/dev/sda5: UUID="173e9a2b-77f5-4b6b-a12d-065fbc84d489" TYPE="ext4" 
/dev/sda6: UUID="135ba135-19c6-4bb8-bc5b-bd81ebd7cd49" TYPE="swap" 
```thanks for the input and the reassurance Buckyball

---

### Post by Bucky Ball on 2013-02-11
From that screen shot sda1 certainly looks empty. What's on sda5?

This is mighty weird because I just don't see how attempting to boot from a non-boot/install disk would wipe anything. The machine should just look for a disk it can boot and when it doesn't find one sit blinking a cursor dumbly, possibly with an error message, and shouldn't write anything to the partition.

---

### Post by Bufeu on 2013-02-11
> **nosmokenofire said:**
> ok so boot repair failed it just got stuck at trying to "reinstall grub on sda". I am still only booting into a live cd. I wanted to back up my files from my ubuntu install (as I'm starting to get a bit worried) but I'm not able to mount the partition, I get this message:
```
Error mounting /dev/sda1 at /media/ubuntu/a787b565-5217-4912-8cdf-64832572624d: 
Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "
/dev/sda1" "/media/ubuntu/a787b565-5217-4912-8cdf-64832572624d"' 
exited with non-zero exit status 32: mount: wrong fs type, bad option, 
bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I then tried what you suggested Bufeu and got nowhere
```
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_ecjaadgfhh_Volume0p1 /mnt
mount: special device /dev/mapper/isw_ecjaadgfhh_Volume0p1 does not exist
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/isw_ecjaadgfhh_Volume0
Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```I'm starting to worry about all my files, emails etc...You can't just copy and paste the command. I linked, so you could get an idea how to use *--boot-directory*. You must replace "/dev/mapper/isw_ecjaadgfhh_Volume0p1" with the name of your partition.
In your case; this should work (replace /dev/sda1 with the partition you want GRUB on):
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda1
```

---

### Post by nosmokenofire on 2013-02-11
A while back I wanted to finish with windows, remove it and use the freed up disk space for ubuntu. I copied my ubuntu install from sda5 to sda1, with a little help (see [http://ubuntuforums.org/showthread.php?t=2107094](http://ubuntuforums.org/showthread.php?t=2107094) )

In the end the operation was succesful. The intention was to reformat sda4 and sda5 and use the extra space. I have not done it yet and what is on sda5 is my old ubuntu install as I copied it onto sda1 a couple of weeks back.

I ran bootinfoscript in case that can give any clues...```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 136230409 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    99,633,151    99,631,104  83 Linux
/dev/sda4          99,635,130   156,301,311    56,666,182   5 Extended
/dev/sda5          99,635,193   154,850,534    55,215,342  83 Linux
/dev/sda6         154,861,568   156,301,311     1,439,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a787b565-5217-4912-8cdf-64832572624d   ext4       
/dev/sda5        173e9a2b-77f5-4b6b-a12d-065fbc84d489   ext4       
/dev/sda6        135ba135-19c6-4bb8-bc5b-bd81ebd7cd49   swap       
/dev/sr0                                                iso9660    Ubuntu 12.10 i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
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
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a787b565-5217-4912-8cdf-64832572624d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
    else
      search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
    fi
    linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-a787b565-5217-4912-8cdf-64832572624d' {
    menuentry 'Ubuntu (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.32-31-generic              2
               =                boot/initrd.img-2.6.38-11-generic-pae          3
               =                boot/initrd.img-3.0.0-17-generic-pae           5
               =                boot/initrd.img-3.2.0-32-generic-pae           3
               =                boot/initrd.img-3.5.0-17-generic               3
               =                boot/initrd.img-3.5.0-18-generic              10
               =                boot/initrd.img-3.5.0-19-generic              17
               =                boot/initrd.img-3.5.0-21-generic              56
               =                boot/initrd.img-3.5.0-22-generic              22
               =                boot/vmlinuz-2.6.32-31-generic                 1
               =                boot/vmlinuz-2.6.38-11-generic-pae             2
               =                boot/vmlinuz-3.0.0-17-generic-pae             46
               =                boot/vmlinuz-3.2.0-32-generic-pae              2
               =                boot/vmlinuz-3.5.0-17-generic                  3
               =                boot/vmlinuz-3.5.0-18-generic                  2
               =                boot/vmlinuz-3.5.0-19-generic                  2
               =                boot/vmlinuz-3.5.0-21-generic                  3
               =                boot/vmlinuz-3.5.0-22-generic                  3
               =                initrd.img                                    22
               =                vmlinuz                                        3
               =                vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ba 18 16 f8 42 e6 ef 5d  11 f9 70 ed b4 9a 9b de  |....B..]..p.....|
00000010  3b 2d ed cd 3c 79 32 53  98 75 79 af 94 76 ec f0  |;-..<y2S.uy..v..|
00000020  9d 8f 56 79 d2 b8 55 20  c5 c2 d7 8b 8a 3e 9f 64  |..Vy..U .....>.d|
00000030  7a d3 e4 96 a1 5a 41 59  d3 67 86 2e 52 62 6b f7  |z....ZAY.g..Rbk.|
00000040  06 a6 8f 0b 19 9c 12 34  78 ef 9e d6 4f 74 9f 8c  |.......4x...Ot..|
00000050  78 dc 3e 8b 36 9b ba a1  17 c0 48 44 73 0b aa e1  |x.>.6.....HDs...|
00000060  2b af e6 31 31 ea ec 84  90 5d c8 bc 1c f4 90 ab  |+..11....]......|
00000070  35 94 3d 3f e3 20 ad b0  13 29 f9 34 f0 f4 38 2d  |5.=?. ...).4..8-|
00000080  c4 8b 63 c2 43 8b 34 46  7d 80 42 33 e3 37 c5 e3  |..c.C.4F}.B3.7..|
00000090  5f 8b 33 9b cc 04 56 81  15 9b c1 21 c2 79 b3 84  |_.3...V....!.y..|
000000a0  17 4c 78 de 54 78 9f 5c  c4 1e a6 58 34 3d ad df  |.Lx.Tx.\...X4=..|
000000b0  35 6f ba 30 7e 29 f7 44  4b e0 25 91 da 5b 0d cb  |5o.0~).DK.%..[..|
000000c0  97 0f 35 8b b9 4a 06 2d  23 24 f6 5e c4 12 cb e4  |..5..J.-#$.^....|
000000d0  38 30 79 be ee a3 67 bb  6f f7 27 4d 2f ca 8e c8  |80y...g.o.'M/...|
000000e0  52 6c 82 b7 92 50 db fb  91 f5 e5 ea d5 12 f8 16  |Rl...P..........|
000000f0  1d 54 9b c7 4e 29 c0 fd  9f 71 45 2b d9 a4 59 c6  |.T..N)...qE+..Y.|
00000100  ba be d8 89 13 0e fe 4a  03 1b a1 6f 7c 83 3c ed  |.......J...o|.<.|
00000110  37 78 b6 d1 f4 49 5b b6  03 56 96 14 2f 22 70 5f  |7x...I[..V../"p_|
00000120  b2 95 25 e7 df e0 3d b3  8a 6b 96 63 f5 07 00 7e  |..%...=..k.c...~|
00000130  d3 26 8c dd 9d 5a 0b 67  9e 84 e9 13 db 47 06 d4  |.&...Z.g.....G..|
00000140  35 35 42 49 27 df df 95  46 cc 35 35 35 c2 99 74  |55BI'...F.555..t|
00000150  6a e7 bc 6d 9d da 9d b6  4f b1 77 59 1e a7 a3 d9  |j..m....O.wY....|
00000160  43 a3 af bf 0e ed 5e 1e  9e ec 0b 23 46 41 fb 39  |C.....^....#FA.9|
00000170  97 1d d9 fb 12 fb bb 6b  d1 c0 8b 0a 8b 70 2d 36  |.......k.....p-6|
00000180  3c 0a f3 5f 6a e5 d1 74  cb 27 b0 d8 10 4f 9d 72  |<.._j..t.'...O.r|
00000190  ef 5b b5 92 7a 91 c3 b3  f6 5e d3 a0 3d b5 c7 f0  |.[..z....^..=...|
000001a0  2e ad 62 bf 13 58 f5 65  12 cd 98 82 4e 0d 1a 14  |..b..X.e....N...|
000001b0  f8 53 cb 9f e8 d5 70 1d  18 26 69 52 7e 91 00 fe  |.S....p..&iR~...|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 ee 84 4a 03 00 fe  |......?.....J...|
000001d0  ff ff 05 fe ff ff 2d 85  4a 03 19 23 16 00 00 00  |......-.J..#....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

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
  /dev/sda1: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found
```

When it tried to boot from my daughters dvd i couldnt think of what else to do but to turn of the pc by keeping the power button pressed. That is when the problems started...

---

### Post by Bucky Ball on 2013-02-11
Ah, the power button could have done something, but still confused. I suggest attempting to boot from sda5 as it looks like that has a bootable grub installed (does that install show up in the kernel list at boot?) and having a closer look from there.

---

### Post by nosmokenofire on 2013-02-11
> **Bufeu said:**
> You can't just copy and paste the command. I linked, so you could get an idea how to use *--boot-directory*. You must replace "/dev/mapper/isw_ecjaadgfhh_Volume0p1" with the name of your partition.
In your case; this should work (replace /dev/sda1 with the partition you want GRUB on):
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda1
```
My mistake. I'm a bit of a cut and paste man who needs explicit instructions when things need changing, thanks for setting me right.
this is what I got for the first command:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
I get the impression that it's not a good thing...

---

### Post by nosmokenofire on 2013-02-11
> **Bucky Ball said:**
> Ah, the power button could have done something, but still confused. I suggest attempting to boot from sda5 as it looks like that has a bootable grub installed (does that install show up in the kernel list at boot?) and having a closer look from there.

How do I do that if I get no grub when things start up?

---

### Post by Bufeu on 2013-02-11
> **nosmokenofire said:**
> My mistake. I'm a bit of a cut and paste man who needs explicit instructions when things need changing, thanks for setting me right.
this is what I got for the first command:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```I get the impression that it's not a good thing...
Please post the output of *dmesg|grep sd*.

---

### Post by nosmokenofire on 2013-02-11
> **Bufeu said:**
> Please post the output of *dmesg|grep sd*.```

[  181.788531] sd 3:0:0:0: >[sda]  
[  181.788535] sd 3:0:0:0: >[sda]  
[  181.788554] sd 3:0:0:0: >[sda]  
[  181.788559] sd 3:0:0:0: >[sda] CDB: 
[  181.788568] end_request: I/O error, dev sda, sector 2062
[  181.788571] Buffer I/O error on device sda1, logical block 1
[  185.836557] sd 3:0:0:0: >[sda] Unhandled sense code
[  185.836560] sd 3:0:0:0: >[sda]  
[  185.836564] sd 3:0:0:0: >[sda]  
[  185.836583] sd 3:0:0:0: >[sda]  
[  185.836588] sd 3:0:0:0: >[sda] CDB: 
[  185.836597] end_request: I/O error, dev sda, sector 2062
[  185.836600] Buffer I/O error on device sda1, logical block 1
[  189.900570] sd 3:0:0:0: >[sda] Unhandled sense code
[  189.900573] sd 3:0:0:0: >[sda]  
[  189.900577] sd 3:0:0:0: >[sda]  
[  189.900597] sd 3:0:0:0: >[sda]  
[  189.900603] sd 3:0:0:0: >[sda] CDB: 
[  189.900612] end_request: I/O error, dev sda, sector 2062
[  189.900615] Buffer I/O error on device sda1, logical block 1
[  193.980579] sd 3:0:0:0: >[sda] Unhandled sense code
[  193.980581] sd 3:0:0:0: >[sda]  
[  193.980585] sd 3:0:0:0: >[sda]  
[  193.980605] sd 3:0:0:0: >[sda]  
[  193.980611] sd 3:0:0:0: >[sda] CDB: 
[  193.980619] end_request: I/O error, dev sda, sector 2062
[  193.980622] Buffer I/O error on device sda1, logical block 1
[  198.036534] sd 3:0:0:0: >[sda] Unhandled sense code
[  198.036536] sd 3:0:0:0: >[sda]  
[  198.036542] sd 3:0:0:0: >[sda]  
[  198.036560] sd 3:0:0:0: >[sda]  
[  198.036566] sd 3:0:0:0: >[sda] CDB: 
[  198.036574] end_request: I/O error, dev sda, sector 2062
[  198.036578] Buffer I/O error on device sda1, logical block 1
[  202.792556] sd 3:0:0:0: >[sda] Unhandled sense code
[  202.792558] sd 3:0:0:0: >[sda]  
[  202.792563] sd 3:0:0:0: >[sda]  
[  202.792582] sd 3:0:0:0: >[sda]  
[  202.792588] sd 3:0:0:0: >[sda] CDB: 
[  202.792597] end_request: I/O error, dev sda, sector 2062
[  202.792602] Buffer I/O error on device sda1, logical block 1
[  206.804572] sd 3:0:0:0: >[sda] Unhandled sense code
[  206.804574] sd 3:0:0:0: >[sda]  
[  206.804579] sd 3:0:0:0: >[sda]  
[  206.804597] sd 3:0:0:0: >[sda]  
[  206.804603] sd 3:0:0:0: >[sda] CDB: 
[  206.804612] end_request: I/O error, dev sda, sector 2062
[  206.804615] Buffer I/O error on device sda1, logical block 1
[  232.236849] Adding 719868k swap on /dev/sda6.  Priority:-1 extents:1 across:719868k 
[  259.345956] sd 3:0:0:0: >[sda] Unhandled sense code
[  259.345959] sd 3:0:0:0: >[sda]  
[  259.345964] sd 3:0:0:0: >[sda]  
[  259.346023] sd 3:0:0:0: >[sda]  
[  259.346029] sd 3:0:0:0: >[sda] CDB: 
[  259.346038] end_request: I/O error, dev sda, sector 2062
[  259.346042] Buffer I/O error on device sda1, logical block 1
[  263.420568] sd 3:0:0:0: >[sda] Unhandled sense code
[  263.420571] sd 3:0:0:0: >[sda]  
[  263.420575] sd 3:0:0:0: >[sda]  
[  263.420595] sd 3:0:0:0: >[sda]  
[  263.420602] sd 3:0:0:0: >[sda] CDB: 
[  263.420610] end_request: I/O error, dev sda, sector 2062
[  263.420614] Buffer I/O error on device sda1, logical block 1
[  267.532580] sd 3:0:0:0: >[sda] Unhandled sense code
[  267.532583] sd 3:0:0:0: >[sda]  
[  267.532587] sd 3:0:0:0: >[sda]  
[  267.532607] sd 3:0:0:0: >[sda]  
[  267.532613] sd 3:0:0:0: >[sda] CDB: 
[  267.532621] end_request: I/O error, dev sda, sector 2062
[  267.532624] Buffer I/O error on device sda1, logical block 1
[  271.600613] sd 3:0:0:0: >[sda] Unhandled sense code
[  271.600616] sd 3:0:0:0: >[sda]  
[  271.600620] sd 3:0:0:0: >[sda]  
[  271.600640] sd 3:0:0:0: >[sda]  
[  271.600646] sd 3:0:0:0: >[sda] CDB: 
[  271.600654] end_request: I/O error, dev sda, sector 2062
[  271.600658] Buffer I/O error on device sda1, logical block 1
[  275.708580] sd 3:0:0:0: >[sda] Unhandled sense code
[  275.708583] sd 3:0:0:0: >[sda]  
[  275.708587] sd 3:0:0:0: >[sda]  
[  275.708607] sd 3:0:0:0: >[sda]  
[  275.708613] sd 3:0:0:0: >[sda] CDB: 
[  275.708621] end_request: I/O error, dev sda, sector 2062
[  275.708625] Buffer I/O error on device sda1, logical block 1
[  279.788574] sd 3:0:0:0: >[sda] Unhandled sense code
[  279.788577] sd 3:0:0:0: >[sda]  
[  279.788582] sd 3:0:0:0: >[sda]  
[  279.788601] sd 3:0:0:0: >[sda]  
[  279.788607] sd 3:0:0:0: >[sda] CDB: 
[  279.788616] end_request: I/O error, dev sda, sector 2062
[  279.788621] Buffer I/O error on device sda1, logical block 1
[  283.832563] sd 3:0:0:0: >[sda] Unhandled sense code
[  283.832566] sd 3:0:0:0: >[sda]  
[  283.832571] sd 3:0:0:0: >[sda]  
[  283.832590] sd 3:0:0:0: >[sda]  
[  283.832597] sd 3:0:0:0: >[sda] CDB: 
[  283.832605] end_request: I/O error, dev sda, sector 2062
[  283.832610] Buffer I/O error on device sda1, logical block 1
[  287.876566] sd 3:0:0:0: >[sda] Unhandled sense code
[  287.876569] sd 3:0:0:0: >[sda]  
[  287.876573] sd 3:0:0:0: >[sda]  
[  287.876594] sd 3:0:0:0: >[sda]  
[  287.876600] sd 3:0:0:0: >[sda] CDB: 
[  287.876608] end_request: I/O error, dev sda, sector 2062
[  287.876612] Buffer I/O error on device sda1, logical block 1
[  291.968564] sd 3:0:0:0: >[sda] Unhandled sense code
[  291.968566] sd 3:0:0:0: >[sda]  
[  291.968571] sd 3:0:0:0: >[sda]  
[  291.968590] sd 3:0:0:0: >[sda]  
[  291.968596] sd 3:0:0:0: >[sda] CDB: 
[  291.968605] end_request: I/O error, dev sda, sector 2062
[  291.968609] Buffer I/O error on device sda1, logical block 1
[  296.044575] sd 3:0:0:0: >[sda] Unhandled sense code
[  296.044577] sd 3:0:0:0: >[sda]  
[  296.044582] sd 3:0:0:0: >[sda]  
[  296.044601] sd 3:0:0:0: >[sda]  
[  296.044607] sd 3:0:0:0: >[sda] CDB: 
[  296.044616] end_request: I/O error, dev sda, sector 2062
[  296.044620] Buffer I/O error on device sda1, logical block 1
[  300.868618] sd 3:0:0:0: >[sda] Unhandled sense code
[  300.868621] sd 3:0:0:0: >[sda]  
[  300.868626] sd 3:0:0:0: >[sda]  
[  300.868646] sd 3:0:0:0: >[sda]  
[  300.868652] sd 3:0:0:0: >[sda] CDB: 
[  300.868661] end_request: I/O error, dev sda, sector 2062
[  300.868665] Buffer I/O error on device sda1, logical block 1
[  304.892589] sd 3:0:0:0: >[sda] Unhandled sense code
[  304.892591] sd 3:0:0:0: >[sda]  
[  304.892596] sd 3:0:0:0: >[sda]  
[  304.892616] sd 3:0:0:0: >[sda]  
[  304.892621] sd 3:0:0:0: >[sda] CDB: 
[  304.892630] end_request: I/O error, dev sda, sector 2062
[  304.892633] Buffer I/O error on device sda1, logical block 1
[  789.836641] sd 3:0:0:0: >[sda] Unhandled sense code
[  789.836643] sd 3:0:0:0: >[sda]  
[  789.836648] sd 3:0:0:0: >[sda]  
[  789.836668] sd 3:0:0:0: >[sda]  
[  789.836674] sd 3:0:0:0: >[sda] CDB: 
[  789.836682] end_request: I/O error, dev sda, sector 2062
[  789.836728] EXT4-fs (sda1): can't read group descriptor 0
[  842.372642] sd 3:0:0:0: >[sda] Unhandled sense code
[  842.372649] sd 3:0:0:0: >[sda]  
[  842.372660] sd 3:0:0:0: >[sda]  
[  842.372707] sd 3:0:0:0: >[sda]  
[  842.372720] sd 3:0:0:0: >[sda] CDB: 
[  842.372742] end_request: I/O error, dev sda, sector 2062
[  842.372811] EXT4-fs (sda1): can't read group descriptor 0
[  861.168595] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
[  861.169231] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  879.032662] sd 3:0:0:0: >[sda] Unhandled sense code
[  879.032669] sd 3:0:0:0: >[sda]  
[  879.032679] sd 3:0:0:0: >[sda]  
[  879.032727] sd 3:0:0:0: >[sda]  
[  879.032740] sd 3:0:0:0: >[sda] CDB: 
[  879.032762] end_request: I/O error, dev sda, sector 2062
[  879.032832] EXT4-fs (sda1): can't read group descriptor 0
[  883.332641] sd 3:0:0:0: >[sda] Unhandled sense code
[  883.332648] sd 3:0:0:0: >[sda]  
[  883.332659] sd 3:0:0:0: >[sda]  
[  883.332706] sd 3:0:0:0: >[sda]  
[  883.332720] sd 3:0:0:0: >[sda] CDB: 
[  883.332740] end_request: I/O error, dev sda, sector 2062
[  883.332810] EXT4-fs (sda1): can't read group descriptor 0
[  921.568643] sd 3:0:0:0: >[sda] Unhandled sense code
[  921.568649] sd 3:0:0:0: >[sda]  
[  921.568661] sd 3:0:0:0: >[sda]  
[  921.568709] sd 3:0:0:0: >[sda]  
[  921.568725] sd 3:0:0:0: >[sda] CDB: 
[  921.568746] end_request: I/O error, dev sda, sector 2062
[  921.568811] EXT4-fs (sda1): can't read group descriptor 0
[ 1598.888674] sd 3:0:0:0: >[sda] Unhandled sense code
[ 1598.888681] sd 3:0:0:0: >[sda]  
[ 1598.888692] sd 3:0:0:0: >[sda]  
[ 1598.888739] sd 3:0:0:0: >[sda]  
[ 1598.888754] sd 3:0:0:0: >[sda] CDB: 
[ 1598.888775] end_request: I/O error, dev sda, sector 2062
[ 1598.888850] EXT4-fs (sda1): can't read group descriptor 0
[ 1906.316639] sd 3:0:0:0: >[sda] Unhandled sense code
[ 1906.316645] sd 3:0:0:0: >[sda]  
[ 1906.316656] sd 3:0:0:0: >[sda]  
[ 1906.316704] sd 3:0:0:0: >[sda]  
[ 1906.316719] sd 3:0:0:0: >[sda] CDB: 
[ 1906.316739] end_request: I/O error, dev sda, sector 2062
[ 1906.316801] EXT4-fs (sda1): can't read group descriptor 0
[ 2243.924641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2243.924648] sd 3:0:0:0: >[sda]  
[ 2243.924659] sd 3:0:0:0: >[sda]  
[ 2243.924707] sd 3:0:0:0: >[sda]  
[ 2243.924722] sd 3:0:0:0: >[sda] CDB: 
[ 2243.924743] end_request: I/O error, dev sda, sector 2062
[ 2243.924752] Buffer I/O error on device sda1, logical block 1
[ 2247.936635] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2247.936642] sd 3:0:0:0: >[sda]  
[ 2247.936653] sd 3:0:0:0: >[sda]  
[ 2247.936699] sd 3:0:0:0: >[sda]  
[ 2247.936713] sd 3:0:0:0: >[sda] CDB: 
[ 2247.936734] end_request: I/O error, dev sda, sector 2062
[ 2247.936742] Buffer I/O error on device sda1, logical block 1
[ 2251.980679] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2251.980685] sd 3:0:0:0: >[sda]  
[ 2251.980696] sd 3:0:0:0: >[sda]  
[ 2251.980744] sd 3:0:0:0: >[sda]  
[ 2251.980758] sd 3:0:0:0: >[sda] CDB: 
[ 2251.980779] end_request: I/O error, dev sda, sector 2062
[ 2251.980791] Buffer I/O error on device sda1, logical block 1
[ 2256.004756] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2256.004763] sd 3:0:0:0: >[sda]  
[ 2256.004774] sd 3:0:0:0: >[sda]  
[ 2256.004820] sd 3:0:0:0: >[sda]  
[ 2256.004834] sd 3:0:0:0: >[sda] CDB: 
[ 2256.004856] end_request: I/O error, dev sda, sector 2062
[ 2256.004864] Buffer I/O error on device sda1, logical block 1
[ 2260.036630] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2260.036637] sd 3:0:0:0: >[sda]  
[ 2260.036648] sd 3:0:0:0: >[sda]  
[ 2260.036695] sd 3:0:0:0: >[sda]  
[ 2260.036709] sd 3:0:0:0: >[sda] CDB: 
[ 2260.036730] end_request: I/O error, dev sda, sector 2062
[ 2260.036738] Buffer I/O error on device sda1, logical block 1
[ 2264.048628] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2264.048635] sd 3:0:0:0: >[sda]  
[ 2264.048647] sd 3:0:0:0: >[sda]  
[ 2264.048695] sd 3:0:0:0: >[sda]  
[ 2264.048711] sd 3:0:0:0: >[sda] CDB: 
[ 2264.048732] end_request: I/O error, dev sda, sector 2062
[ 2264.048742] Buffer I/O error on device sda1, logical block 1
[ 2268.060686] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2268.060693] sd 3:0:0:0: >[sda]  
[ 2268.060705] sd 3:0:0:0: >[sda]  
[ 2268.060753] sd 3:0:0:0: >[sda]  
[ 2268.060769] sd 3:0:0:0: >[sda] CDB: 
[ 2268.060789] end_request: I/O error, dev sda, sector 2062
[ 2268.060800] Buffer I/O error on device sda1, logical block 1
[ 2272.073017] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2272.073024] sd 3:0:0:0: >[sda]  
[ 2272.073038] sd 3:0:0:0: >[sda]  
[ 2272.073089] sd 3:0:0:0: >[sda]  
[ 2272.073106] sd 3:0:0:0: >[sda] CDB: 
[ 2272.073129] end_request: I/O error, dev sda, sector 2062
[ 2272.073143] Buffer I/O error on device sda1, logical block 1
[ 2276.116628] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2276.116635] sd 3:0:0:0: >[sda]  
[ 2276.116646] sd 3:0:0:0: >[sda]  
[ 2276.116694] sd 3:0:0:0: >[sda]  
[ 2276.116708] sd 3:0:0:0: >[sda] CDB: 
[ 2276.116729] end_request: I/O error, dev sda, sector 2062
[ 2276.116739] Buffer I/O error on device sda1, logical block 1
[ 2280.140630] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2280.140636] sd 3:0:0:0: >[sda]  
[ 2280.140648] sd 3:0:0:0: >[sda]  
[ 2280.140695] sd 3:0:0:0: >[sda]  
[ 2280.140709] sd 3:0:0:0: >[sda] CDB: 
[ 2280.140730] end_request: I/O error, dev sda, sector 2062
[ 2280.140738] Buffer I/O error on device sda1, logical block 1
[ 2284.196643] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2284.196650] sd 3:0:0:0: >[sda]  
[ 2284.196661] sd 3:0:0:0: >[sda]  
[ 2284.196709] sd 3:0:0:0: >[sda]  
[ 2284.196722] sd 3:0:0:0: >[sda] CDB: 
[ 2284.196744] end_request: I/O error, dev sda, sector 2062
[ 2284.196754] Buffer I/O error on device sda1, logical block 1
[ 2288.216699] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2288.216706] sd 3:0:0:0: >[sda]  
[ 2288.216717] sd 3:0:0:0: >[sda]  
[ 2288.216766] sd 3:0:0:0: >[sda]  
[ 2288.216780] sd 3:0:0:0: >[sda] CDB: 
[ 2288.216801] end_request: I/O error, dev sda, sector 2062
[ 2288.216812] Buffer I/O error on device sda1, logical block 1
[ 2299.472657] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2299.472664] sd 3:0:0:0: >[sda]  
[ 2299.472675] sd 3:0:0:0: >[sda]  
[ 2299.472723] sd 3:0:0:0: >[sda]  
[ 2299.472738] sd 3:0:0:0: >[sda] CDB: 
[ 2299.472759] end_request: I/O error, dev sda, sector 2062
[ 2303.684640] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2303.684647] sd 3:0:0:0: >[sda]  
[ 2303.684659] sd 3:0:0:0: >[sda]  
[ 2303.684707] sd 3:0:0:0: >[sda]  
[ 2303.684722] sd 3:0:0:0: >[sda] CDB: 
[ 2303.684743] end_request: I/O error, dev sda, sector 2062
[ 2308.084649] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2308.084655] sd 3:0:0:0: >[sda]  
[ 2308.084666] sd 3:0:0:0: >[sda]  
[ 2308.084713] sd 3:0:0:0: >[sda]  
[ 2308.084727] sd 3:0:0:0: >[sda] CDB: 
[ 2308.084748] end_request: I/O error, dev sda, sector 2062
[ 2308.084755] Buffer I/O error on device sda1, logical block 1
[ 2308.084762] Buffer I/O error on device sda1, logical block 2
[ 2308.084768] Buffer I/O error on device sda1, logical block 3
[ 2312.188635] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2312.188638] sd 3:0:0:0: >[sda]  
[ 2312.188644] sd 3:0:0:0: >[sda]  
[ 2312.188663] sd 3:0:0:0: >[sda]  
[ 2312.188669] sd 3:0:0:0: >[sda] CDB: 
[ 2312.188678] end_request: I/O error, dev sda, sector 2062
[ 2312.188682] Buffer I/O error on device sda1, logical block 1
[ 2312.188685] Buffer I/O error on device sda1, logical block 2
[ 2312.188688] Buffer I/O error on device sda1, logical block 3
[ 2317.452772] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2317.452775] sd 3:0:0:0: >[sda]  
[ 2317.452781] sd 3:0:0:0: >[sda]  
[ 2317.452804] sd 3:0:0:0: >[sda]  
[ 2317.452812] sd 3:0:0:0: >[sda] CDB: 
[ 2317.452823] end_request: I/O error, dev sda, sector 2062
[ 2317.452831] Buffer I/O error on device sda1, logical block 1
[ 2321.508696] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2321.508703] sd 3:0:0:0: >[sda]  
[ 2321.508714] sd 3:0:0:0: >[sda]  
[ 2321.508761] sd 3:0:0:0: >[sda]  
[ 2321.508775] sd 3:0:0:0: >[sda] CDB: 
[ 2321.508797] end_request: I/O error, dev sda, sector 2062
[ 2321.508807] Buffer I/O error on device sda1, logical block 1
[ 2325.600589] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2325.600592] sd 3:0:0:0: >[sda]  
[ 2325.600598] sd 3:0:0:0: >[sda]  
[ 2325.600617] sd 3:0:0:0: >[sda]  
[ 2325.600623] sd 3:0:0:0: >[sda] CDB: 
[ 2325.600632] end_request: I/O error, dev sda, sector 2062
[ 2325.600636] Buffer I/O error on device sda1, logical block 1
[ 2329.664696] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2329.664703] sd 3:0:0:0: >[sda]  
[ 2329.664714] sd 3:0:0:0: >[sda]  
[ 2329.664763] sd 3:0:0:0: >[sda]  
[ 2329.664777] sd 3:0:0:0: >[sda] CDB: 
[ 2329.664798] end_request: I/O error, dev sda, sector 2062
[ 2329.664809] Buffer I/O error on device sda1, logical block 1
[ 2333.764661] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2333.764668] sd 3:0:0:0: >[sda]  
[ 2333.764679] sd 3:0:0:0: >[sda]  
[ 2333.764728] sd 3:0:0:0: >[sda]  
[ 2333.764742] sd 3:0:0:0: >[sda] CDB: 
[ 2333.764763] end_request: I/O error, dev sda, sector 2062
[ 2333.764773] Buffer I/O error on device sda1, logical block 1
[ 2337.800641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2337.800648] sd 3:0:0:0: >[sda]  
[ 2337.800659] sd 3:0:0:0: >[sda]  
[ 2337.800708] sd 3:0:0:0: >[sda]  
[ 2337.800722] sd 3:0:0:0: >[sda] CDB: 
[ 2337.800744] end_request: I/O error, dev sda, sector 2062
[ 2337.800753] Buffer I/O error on device sda1, logical block 1
[ 2341.832632] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2341.832639] sd 3:0:0:0: >[sda]  
[ 2341.832649] sd 3:0:0:0: >[sda]  
[ 2341.832697] sd 3:0:0:0: >[sda]  
[ 2341.832710] sd 3:0:0:0: >[sda] CDB: 
[ 2341.832732] end_request: I/O error, dev sda, sector 2062
[ 2341.832740] Buffer I/O error on device sda1, logical block 1
[ 2345.880832] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2345.880840] sd 3:0:0:0: >[sda]  
[ 2345.880852] sd 3:0:0:0: >[sda]  
[ 2345.880904] sd 3:0:0:0: >[sda]  
[ 2345.880920] sd 3:0:0:0: >[sda] CDB: 
[ 2345.880944] end_request: I/O error, dev sda, sector 2062
[ 2345.880957] Buffer I/O error on device sda1, logical block 1
[ 2349.980650] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2349.980656] sd 3:0:0:0: >[sda]  
[ 2349.980668] sd 3:0:0:0: >[sda]  
[ 2349.980715] sd 3:0:0:0: >[sda]  
[ 2349.980729] sd 3:0:0:0: >[sda] CDB: 
[ 2349.980750] end_request: I/O error, dev sda, sector 2062
[ 2349.980759] Buffer I/O error on device sda1, logical block 1
[ 2354.001039] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2354.001046] sd 3:0:0:0: >[sda]  
[ 2354.001057] sd 3:0:0:0: >[sda]  
[ 2354.001104] sd 3:0:0:0: >[sda]  
[ 2354.001118] sd 3:0:0:0: >[sda] CDB: 
[ 2354.001139] end_request: I/O error, dev sda, sector 2062
[ 2354.001149] Buffer I/O error on device sda1, logical block 1
[ 2358.180598] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2358.180600] sd 3:0:0:0: >[sda]  
[ 2358.180605] sd 3:0:0:0: >[sda]  
[ 2358.180625] sd 3:0:0:0: >[sda]  
[ 2358.180630] sd 3:0:0:0: >[sda] CDB: 
[ 2358.180639] end_request: I/O error, dev sda, sector 2062
[ 2358.180643] Buffer I/O error on device sda1, logical block 1
[ 2362.205124] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2362.205131] sd 3:0:0:0: >[sda]  
[ 2362.205142] sd 3:0:0:0: >[sda]  
[ 2362.205189] sd 3:0:0:0: >[sda]  
[ 2362.205203] sd 3:0:0:0: >[sda] CDB: 
[ 2362.205224] end_request: I/O error, dev sda, sector 2062
[ 2362.205233] Buffer I/O error on device sda1, logical block 1
[ 3774.852657] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3774.852664] sd 3:0:0:0: >[sda]  
[ 3774.852677] sd 3:0:0:0: >[sda]  
[ 3774.852724] sd 3:0:0:0: >[sda]  
[ 3774.852740] sd 3:0:0:0: >[sda] CDB: 
[ 3774.852761] end_request: I/O error, dev sda, sector 2062
[ 3774.852769] Buffer I/O error on device sda1, logical block 1
[ 3774.852775] Buffer I/O error on device sda1, logical block 2
[ 3774.852781] Buffer I/O error on device sda1, logical block 3
[ 3778.888634] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3778.888641] sd 3:0:0:0: >[sda]  
[ 3778.888653] sd 3:0:0:0: >[sda]  
[ 3778.888699] sd 3:0:0:0: >[sda]  
[ 3778.888713] sd 3:0:0:0: >[sda] CDB: 
[ 3778.888734] end_request: I/O error, dev sda, sector 2062
[ 3778.888742] Buffer I/O error on device sda1, logical block 1
[ 3783.000832] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3783.000838] sd 3:0:0:0: >[sda]  
[ 3783.000849] sd 3:0:0:0: >[sda]  
[ 3783.000896] sd 3:0:0:0: >[sda]  
[ 3783.000910] sd 3:0:0:0: >[sda] CDB: 
[ 3783.000931] end_request: I/O error, dev sda, sector 2062
[ 3783.001011] EXT4-fs (sda1): can't read group descriptor 0
[ 3783.335650] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[ 3788.832644] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3788.832650] sd 3:0:0:0: >[sda]  
[ 3788.832661] sd 3:0:0:0: >[sda]  
[ 3788.832708] sd 3:0:0:0: >[sda]  
[ 3788.832721] sd 3:0:0:0: >[sda] CDB: 
[ 3788.832742] end_request: I/O error, dev sda, sector 2062
[ 4607.852623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4607.852630] sd 3:0:0:0: >[sda]  
[ 4607.852642] sd 3:0:0:0: >[sda]  
[ 4607.852689] sd 3:0:0:0: >[sda]  
[ 4607.852703] sd 3:0:0:0: >[sda] CDB: 
[ 4607.852724] end_request: I/O error, dev sda, sector 2062
[ 4607.852732] Buffer I/O error on device sda1, logical block 1
[ 4611.872641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4611.872648] sd 3:0:0:0: >[sda]  
[ 4611.872660] sd 3:0:0:0: >[sda]  
[ 4611.872707] sd 3:0:0:0: >[sda]  
[ 4611.872723] sd 3:0:0:0: >[sda] CDB: 
[ 4611.872743] end_request: I/O error, dev sda, sector 2062
[ 4611.872752] Buffer I/O error on device sda1, logical block 1
[ 4615.896649] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4615.896655] sd 3:0:0:0: >[sda]  
[ 4615.896667] sd 3:0:0:0: >[sda]  
[ 4615.896713] sd 3:0:0:0: >[sda]  
[ 4615.896727] sd 3:0:0:0: >[sda] CDB: 
[ 4615.896748] end_request: I/O error, dev sda, sector 2062
[ 4615.896756] Buffer I/O error on device sda1, logical block 1
[ 4619.920623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4619.920630] sd 3:0:0:0: >[sda]  
[ 4619.920640] sd 3:0:0:0: >[sda]  
[ 4619.920688] sd 3:0:0:0: >[sda]  
[ 4619.920701] sd 3:0:0:0: >[sda] CDB: 
[ 4619.920723] end_request: I/O error, dev sda, sector 2062
[ 4619.920734] Buffer I/O error on device sda1, logical block 1
[ 4623.940623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4623.940630] sd 3:0:0:0: >[sda]  
[ 4623.940641] sd 3:0:0:0: >[sda]  
[ 4623.940689] sd 3:0:0:0: >[sda]  
[ 4623.940703] sd 3:0:0:0: >[sda] CDB: 
[ 4623.940724] end_request: I/O error, dev sda, sector 2062
[ 4623.940733] Buffer I/O error on device sda1, logical block 1
[ 4627.976639] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4627.976646] sd 3:0:0:0: >[sda]  
[ 4627.976656] sd 3:0:0:0: >[sda]  
[ 4627.976703] sd 3:0:0:0: >[sda]  
[ 4627.976716] sd 3:0:0:0: >[sda] CDB: 
[ 4627.976738] end_request: I/O error, dev sda, sector 2062
[ 4627.976748] Buffer I/O error on device sda1, logical block 1
[ 4632.008625] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4632.008631] sd 3:0:0:0: >[sda]  
[ 4632.008642] sd 3:0:0:0: >[sda]  
[ 4632.008689] sd 3:0:0:0: >[sda]  
[ 4632.008704] sd 3:0:0:0: >[sda] CDB: 
[ 4632.008724] end_request: I/O error, dev sda, sector 2062
[ 4632.008734] Buffer I/O error on device sda1, logical block 1
[ 4636.032638] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4636.032645] sd 3:0:0:0: >[sda]  
[ 4636.032656] sd 3:0:0:0: >[sda]  
[ 4636.032704] sd 3:0:0:0: >[sda]  
[ 4636.032726] sd 3:0:0:0: >[sda] CDB: 
[ 4636.032746] end_request: I/O error, dev sda, sector 2062
[ 4636.032755] Buffer I/O error on device sda1, logical block 1
[ 4640.076624] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4640.076630] sd 3:0:0:0: >[sda]  
[ 4640.076641] sd 3:0:0:0: >[sda]  
[ 4640.076688] sd 3:0:0:0: >[sda]  
[ 4640.076703] sd 3:0:0:0: >[sda] CDB: 
[ 4640.076723] end_request: I/O error, dev sda, sector 2062
[ 4640.076731] Buffer I/O error on device sda1, logical block 1
[ 4644.112592] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4644.112596] sd 3:0:0:0: >[sda]  
[ 4644.112602] sd 3:0:0:0: >[sda]  
[ 4644.112625] sd 3:0:0:0: >[sda]  
[ 4644.112632] sd 3:0:0:0: >[sda] CDB: 
[ 4644.112643] end_request: I/O error, dev sda, sector 2062
[ 4644.112647] Buffer I/O error on device sda1, logical block 1
[ 4648.144918] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4648.144922] sd 3:0:0:0: >[sda]  
[ 4648.144929] sd 3:0:0:0: >[sda]  
[ 4648.144952] sd 3:0:0:0: >[sda]  
[ 4648.144961] sd 3:0:0:0: >[sda] CDB: 
[ 4648.144971] end_request: I/O error, dev sda, sector 2062
[ 4648.144981] Buffer I/O error on device sda1, logical block 1
[ 4652.168708] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4652.168715] sd 3:0:0:0: >[sda]  
[ 4652.168726] sd 3:0:0:0: >[sda]  
[ 4652.168774] sd 3:0:0:0: >[sda]  
[ 4652.168788] sd 3:0:0:0: >[sda] CDB: 
[ 4652.168809] end_request: I/O error, dev sda, sector 2062
[ 4652.168820] Buffer I/O error on device sda1, logical block 1
[ 4656.188786] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4656.188792] sd 3:0:0:0: >[sda]  
[ 4656.188803] sd 3:0:0:0: >[sda]  
[ 4656.188850] sd 3:0:0:0: >[sda]  
[ 4656.188863] sd 3:0:0:0: >[sda] CDB: 
[ 4656.188885] end_request: I/O error, dev sda, sector 2062
[ 4656.188964] EXT4-fs (sda1): can't read group descriptor 0
[ 5386.778629] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
[ 5386.778939] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)


```

---

### Post by Bufeu on 2013-02-11
> **nosmokenofire said:**
> ```

[  181.788531] sd 3:0:0:0: >[sda]  
[  181.788535] sd 3:0:0:0: >[sda]  
[  181.788554] sd 3:0:0:0: >[sda]  
[  181.788559] sd 3:0:0:0: >[sda] CDB: 
[  181.788568] end_request: I/O error, dev sda, sector 2062
[  181.788571] Buffer I/O error on device sda1, logical block 1
[  185.836557] sd 3:0:0:0: >[sda] Unhandled sense code
[  185.836560] sd 3:0:0:0: >[sda]  
[  185.836564] sd 3:0:0:0: >[sda]  
[  185.836583] sd 3:0:0:0: >[sda]  
[  185.836588] sd 3:0:0:0: >[sda] CDB: 
[  185.836597] end_request: I/O error, dev sda, sector 2062
[  185.836600] Buffer I/O error on device sda1, logical block 1
[  189.900570] sd 3:0:0:0: >[sda] Unhandled sense code
[  189.900573] sd 3:0:0:0: >[sda]  
[  189.900577] sd 3:0:0:0: >[sda]  
[  189.900597] sd 3:0:0:0: >[sda]  
[  189.900603] sd 3:0:0:0: >[sda] CDB: 
[  189.900612] end_request: I/O error, dev sda, sector 2062
[  189.900615] Buffer I/O error on device sda1, logical block 1
[  193.980579] sd 3:0:0:0: >[sda] Unhandled sense code
[  193.980581] sd 3:0:0:0: >[sda]  
[  193.980585] sd 3:0:0:0: >[sda]  
[  193.980605] sd 3:0:0:0: >[sda]  
[  193.980611] sd 3:0:0:0: >[sda] CDB: 
[  193.980619] end_request: I/O error, dev sda, sector 2062
[  193.980622] Buffer I/O error on device sda1, logical block 1
[  198.036534] sd 3:0:0:0: >[sda] Unhandled sense code
[  198.036536] sd 3:0:0:0: >[sda]  
[  198.036542] sd 3:0:0:0: >[sda]  
[  198.036560] sd 3:0:0:0: >[sda]  
[  198.036566] sd 3:0:0:0: >[sda] CDB: 
[  198.036574] end_request: I/O error, dev sda, sector 2062
[  198.036578] Buffer I/O error on device sda1, logical block 1
[  202.792556] sd 3:0:0:0: >[sda] Unhandled sense code
[  202.792558] sd 3:0:0:0: >[sda]  
[  202.792563] sd 3:0:0:0: >[sda]  
[  202.792582] sd 3:0:0:0: >[sda]  
[  202.792588] sd 3:0:0:0: >[sda] CDB: 
[  202.792597] end_request: I/O error, dev sda, sector 2062
[  202.792602] Buffer I/O error on device sda1, logical block 1
[  206.804572] sd 3:0:0:0: >[sda] Unhandled sense code
[  206.804574] sd 3:0:0:0: >[sda]  
[  206.804579] sd 3:0:0:0: >[sda]  
[  206.804597] sd 3:0:0:0: >[sda]  
[  206.804603] sd 3:0:0:0: >[sda] CDB: 
[  206.804612] end_request: I/O error, dev sda, sector 2062
[  206.804615] Buffer I/O error on device sda1, logical block 1
[  232.236849] Adding 719868k swap on /dev/sda6.  Priority:-1 extents:1 across:719868k 
[  259.345956] sd 3:0:0:0: >[sda] Unhandled sense code
[  259.345959] sd 3:0:0:0: >[sda]  
[  259.345964] sd 3:0:0:0: >[sda]  
[  259.346023] sd 3:0:0:0: >[sda]  
[  259.346029] sd 3:0:0:0: >[sda] CDB: 
[  259.346038] end_request: I/O error, dev sda, sector 2062
[  259.346042] Buffer I/O error on device sda1, logical block 1
[  263.420568] sd 3:0:0:0: >[sda] Unhandled sense code
[  263.420571] sd 3:0:0:0: >[sda]  
[  263.420575] sd 3:0:0:0: >[sda]  
[  263.420595] sd 3:0:0:0: >[sda]  
[  263.420602] sd 3:0:0:0: >[sda] CDB: 
[  263.420610] end_request: I/O error, dev sda, sector 2062
[  263.420614] Buffer I/O error on device sda1, logical block 1
[  267.532580] sd 3:0:0:0: >[sda] Unhandled sense code
[  267.532583] sd 3:0:0:0: >[sda]  
[  267.532587] sd 3:0:0:0: >[sda]  
[  267.532607] sd 3:0:0:0: >[sda]  
[  267.532613] sd 3:0:0:0: >[sda] CDB: 
[  267.532621] end_request: I/O error, dev sda, sector 2062
[  267.532624] Buffer I/O error on device sda1, logical block 1
[  271.600613] sd 3:0:0:0: >[sda] Unhandled sense code
[  271.600616] sd 3:0:0:0: >[sda]  
[  271.600620] sd 3:0:0:0: >[sda]  
[  271.600640] sd 3:0:0:0: >[sda]  
[  271.600646] sd 3:0:0:0: >[sda] CDB: 
[  271.600654] end_request: I/O error, dev sda, sector 2062
[  271.600658] Buffer I/O error on device sda1, logical block 1
[  275.708580] sd 3:0:0:0: >[sda] Unhandled sense code
[  275.708583] sd 3:0:0:0: >[sda]  
[  275.708587] sd 3:0:0:0: >[sda]  
[  275.708607] sd 3:0:0:0: >[sda]  
[  275.708613] sd 3:0:0:0: >[sda] CDB: 
[  275.708621] end_request: I/O error, dev sda, sector 2062
[  275.708625] Buffer I/O error on device sda1, logical block 1
[  279.788574] sd 3:0:0:0: >[sda] Unhandled sense code
[  279.788577] sd 3:0:0:0: >[sda]  
[  279.788582] sd 3:0:0:0: >[sda]  
[  279.788601] sd 3:0:0:0: >[sda]  
[  279.788607] sd 3:0:0:0: >[sda] CDB: 
[  279.788616] end_request: I/O error, dev sda, sector 2062
[  279.788621] Buffer I/O error on device sda1, logical block 1
[  283.832563] sd 3:0:0:0: >[sda] Unhandled sense code
[  283.832566] sd 3:0:0:0: >[sda]  
[  283.832571] sd 3:0:0:0: >[sda]  
[  283.832590] sd 3:0:0:0: >[sda]  
[  283.832597] sd 3:0:0:0: >[sda] CDB: 
[  283.832605] end_request: I/O error, dev sda, sector 2062
[  283.832610] Buffer I/O error on device sda1, logical block 1
[  287.876566] sd 3:0:0:0: >[sda] Unhandled sense code
[  287.876569] sd 3:0:0:0: >[sda]  
[  287.876573] sd 3:0:0:0: >[sda]  
[  287.876594] sd 3:0:0:0: >[sda]  
[  287.876600] sd 3:0:0:0: >[sda] CDB: 
[  287.876608] end_request: I/O error, dev sda, sector 2062
[  287.876612] Buffer I/O error on device sda1, logical block 1
[  291.968564] sd 3:0:0:0: >[sda] Unhandled sense code
[  291.968566] sd 3:0:0:0: >[sda]  
[  291.968571] sd 3:0:0:0: >[sda]  
[  291.968590] sd 3:0:0:0: >[sda]  
[  291.968596] sd 3:0:0:0: >[sda] CDB: 
[  291.968605] end_request: I/O error, dev sda, sector 2062
[  291.968609] Buffer I/O error on device sda1, logical block 1
[  296.044575] sd 3:0:0:0: >[sda] Unhandled sense code
[  296.044577] sd 3:0:0:0: >[sda]  
[  296.044582] sd 3:0:0:0: >[sda]  
[  296.044601] sd 3:0:0:0: >[sda]  
[  296.044607] sd 3:0:0:0: >[sda] CDB: 
[  296.044616] end_request: I/O error, dev sda, sector 2062
[  296.044620] Buffer I/O error on device sda1, logical block 1
[  300.868618] sd 3:0:0:0: >[sda] Unhandled sense code
[  300.868621] sd 3:0:0:0: >[sda]  
[  300.868626] sd 3:0:0:0: >[sda]  
[  300.868646] sd 3:0:0:0: >[sda]  
[  300.868652] sd 3:0:0:0: >[sda] CDB: 
[  300.868661] end_request: I/O error, dev sda, sector 2062
[  300.868665] Buffer I/O error on device sda1, logical block 1
[  304.892589] sd 3:0:0:0: >[sda] Unhandled sense code
[  304.892591] sd 3:0:0:0: >[sda]  
[  304.892596] sd 3:0:0:0: >[sda]  
[  304.892616] sd 3:0:0:0: >[sda]  
[  304.892621] sd 3:0:0:0: >[sda] CDB: 
[  304.892630] end_request: I/O error, dev sda, sector 2062
[  304.892633] Buffer I/O error on device sda1, logical block 1
[  789.836641] sd 3:0:0:0: >[sda] Unhandled sense code
[  789.836643] sd 3:0:0:0: >[sda]  
[  789.836648] sd 3:0:0:0: >[sda]  
[  789.836668] sd 3:0:0:0: >[sda]  
[  789.836674] sd 3:0:0:0: >[sda] CDB: 
[  789.836682] end_request: I/O error, dev sda, sector 2062
[  789.836728] EXT4-fs (sda1): can't read group descriptor 0
[  842.372642] sd 3:0:0:0: >[sda] Unhandled sense code
[  842.372649] sd 3:0:0:0: >[sda]  
[  842.372660] sd 3:0:0:0: >[sda]  
[  842.372707] sd 3:0:0:0: >[sda]  
[  842.372720] sd 3:0:0:0: >[sda] CDB: 
[  842.372742] end_request: I/O error, dev sda, sector 2062
[  842.372811] EXT4-fs (sda1): can't read group descriptor 0
[  861.168595] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
[  861.169231] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[  879.032662] sd 3:0:0:0: >[sda] Unhandled sense code
[  879.032669] sd 3:0:0:0: >[sda]  
[  879.032679] sd 3:0:0:0: >[sda]  
[  879.032727] sd 3:0:0:0: >[sda]  
[  879.032740] sd 3:0:0:0: >[sda] CDB: 
[  879.032762] end_request: I/O error, dev sda, sector 2062
[  879.032832] EXT4-fs (sda1): can't read group descriptor 0
[  883.332641] sd 3:0:0:0: >[sda] Unhandled sense code
[  883.332648] sd 3:0:0:0: >[sda]  
[  883.332659] sd 3:0:0:0: >[sda]  
[  883.332706] sd 3:0:0:0: >[sda]  
[  883.332720] sd 3:0:0:0: >[sda] CDB: 
[  883.332740] end_request: I/O error, dev sda, sector 2062
[  883.332810] EXT4-fs (sda1): can't read group descriptor 0
[  921.568643] sd 3:0:0:0: >[sda] Unhandled sense code
[  921.568649] sd 3:0:0:0: >[sda]  
[  921.568661] sd 3:0:0:0: >[sda]  
[  921.568709] sd 3:0:0:0: >[sda]  
[  921.568725] sd 3:0:0:0: >[sda] CDB: 
[  921.568746] end_request: I/O error, dev sda, sector 2062
[  921.568811] EXT4-fs (sda1): can't read group descriptor 0
[ 1598.888674] sd 3:0:0:0: >[sda] Unhandled sense code
[ 1598.888681] sd 3:0:0:0: >[sda]  
[ 1598.888692] sd 3:0:0:0: >[sda]  
[ 1598.888739] sd 3:0:0:0: >[sda]  
[ 1598.888754] sd 3:0:0:0: >[sda] CDB: 
[ 1598.888775] end_request: I/O error, dev sda, sector 2062
[ 1598.888850] EXT4-fs (sda1): can't read group descriptor 0
[ 1906.316639] sd 3:0:0:0: >[sda] Unhandled sense code
[ 1906.316645] sd 3:0:0:0: >[sda]  
[ 1906.316656] sd 3:0:0:0: >[sda]  
[ 1906.316704] sd 3:0:0:0: >[sda]  
[ 1906.316719] sd 3:0:0:0: >[sda] CDB: 
[ 1906.316739] end_request: I/O error, dev sda, sector 2062
[ 1906.316801] EXT4-fs (sda1): can't read group descriptor 0
[ 2243.924641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2243.924648] sd 3:0:0:0: >[sda]  
[ 2243.924659] sd 3:0:0:0: >[sda]  
[ 2243.924707] sd 3:0:0:0: >[sda]  
[ 2243.924722] sd 3:0:0:0: >[sda] CDB: 
[ 2243.924743] end_request: I/O error, dev sda, sector 2062
[ 2243.924752] Buffer I/O error on device sda1, logical block 1
[ 2247.936635] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2247.936642] sd 3:0:0:0: >[sda]  
[ 2247.936653] sd 3:0:0:0: >[sda]  
[ 2247.936699] sd 3:0:0:0: >[sda]  
[ 2247.936713] sd 3:0:0:0: >[sda] CDB: 
[ 2247.936734] end_request: I/O error, dev sda, sector 2062
[ 2247.936742] Buffer I/O error on device sda1, logical block 1
[ 2251.980679] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2251.980685] sd 3:0:0:0: >[sda]  
[ 2251.980696] sd 3:0:0:0: >[sda]  
[ 2251.980744] sd 3:0:0:0: >[sda]  
[ 2251.980758] sd 3:0:0:0: >[sda] CDB: 
[ 2251.980779] end_request: I/O error, dev sda, sector 2062
[ 2251.980791] Buffer I/O error on device sda1, logical block 1
[ 2256.004756] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2256.004763] sd 3:0:0:0: >[sda]  
[ 2256.004774] sd 3:0:0:0: >[sda]  
[ 2256.004820] sd 3:0:0:0: >[sda]  
[ 2256.004834] sd 3:0:0:0: >[sda] CDB: 
[ 2256.004856] end_request: I/O error, dev sda, sector 2062
[ 2256.004864] Buffer I/O error on device sda1, logical block 1
[ 2260.036630] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2260.036637] sd 3:0:0:0: >[sda]  
[ 2260.036648] sd 3:0:0:0: >[sda]  
[ 2260.036695] sd 3:0:0:0: >[sda]  
[ 2260.036709] sd 3:0:0:0: >[sda] CDB: 
[ 2260.036730] end_request: I/O error, dev sda, sector 2062
[ 2260.036738] Buffer I/O error on device sda1, logical block 1
[ 2264.048628] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2264.048635] sd 3:0:0:0: >[sda]  
[ 2264.048647] sd 3:0:0:0: >[sda]  
[ 2264.048695] sd 3:0:0:0: >[sda]  
[ 2264.048711] sd 3:0:0:0: >[sda] CDB: 
[ 2264.048732] end_request: I/O error, dev sda, sector 2062
[ 2264.048742] Buffer I/O error on device sda1, logical block 1
[ 2268.060686] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2268.060693] sd 3:0:0:0: >[sda]  
[ 2268.060705] sd 3:0:0:0: >[sda]  
[ 2268.060753] sd 3:0:0:0: >[sda]  
[ 2268.060769] sd 3:0:0:0: >[sda] CDB: 
[ 2268.060789] end_request: I/O error, dev sda, sector 2062
[ 2268.060800] Buffer I/O error on device sda1, logical block 1
[ 2272.073017] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2272.073024] sd 3:0:0:0: >[sda]  
[ 2272.073038] sd 3:0:0:0: >[sda]  
[ 2272.073089] sd 3:0:0:0: >[sda]  
[ 2272.073106] sd 3:0:0:0: >[sda] CDB: 
[ 2272.073129] end_request: I/O error, dev sda, sector 2062
[ 2272.073143] Buffer I/O error on device sda1, logical block 1
[ 2276.116628] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2276.116635] sd 3:0:0:0: >[sda]  
[ 2276.116646] sd 3:0:0:0: >[sda]  
[ 2276.116694] sd 3:0:0:0: >[sda]  
[ 2276.116708] sd 3:0:0:0: >[sda] CDB: 
[ 2276.116729] end_request: I/O error, dev sda, sector 2062
[ 2276.116739] Buffer I/O error on device sda1, logical block 1
[ 2280.140630] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2280.140636] sd 3:0:0:0: >[sda]  
[ 2280.140648] sd 3:0:0:0: >[sda]  
[ 2280.140695] sd 3:0:0:0: >[sda]  
[ 2280.140709] sd 3:0:0:0: >[sda] CDB: 
[ 2280.140730] end_request: I/O error, dev sda, sector 2062
[ 2280.140738] Buffer I/O error on device sda1, logical block 1
[ 2284.196643] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2284.196650] sd 3:0:0:0: >[sda]  
[ 2284.196661] sd 3:0:0:0: >[sda]  
[ 2284.196709] sd 3:0:0:0: >[sda]  
[ 2284.196722] sd 3:0:0:0: >[sda] CDB: 
[ 2284.196744] end_request: I/O error, dev sda, sector 2062
[ 2284.196754] Buffer I/O error on device sda1, logical block 1
[ 2288.216699] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2288.216706] sd 3:0:0:0: >[sda]  
[ 2288.216717] sd 3:0:0:0: >[sda]  
[ 2288.216766] sd 3:0:0:0: >[sda]  
[ 2288.216780] sd 3:0:0:0: >[sda] CDB: 
[ 2288.216801] end_request: I/O error, dev sda, sector 2062
[ 2288.216812] Buffer I/O error on device sda1, logical block 1
[ 2299.472657] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2299.472664] sd 3:0:0:0: >[sda]  
[ 2299.472675] sd 3:0:0:0: >[sda]  
[ 2299.472723] sd 3:0:0:0: >[sda]  
[ 2299.472738] sd 3:0:0:0: >[sda] CDB: 
[ 2299.472759] end_request: I/O error, dev sda, sector 2062
[ 2303.684640] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2303.684647] sd 3:0:0:0: >[sda]  
[ 2303.684659] sd 3:0:0:0: >[sda]  
[ 2303.684707] sd 3:0:0:0: >[sda]  
[ 2303.684722] sd 3:0:0:0: >[sda] CDB: 
[ 2303.684743] end_request: I/O error, dev sda, sector 2062
[ 2308.084649] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2308.084655] sd 3:0:0:0: >[sda]  
[ 2308.084666] sd 3:0:0:0: >[sda]  
[ 2308.084713] sd 3:0:0:0: >[sda]  
[ 2308.084727] sd 3:0:0:0: >[sda] CDB: 
[ 2308.084748] end_request: I/O error, dev sda, sector 2062
[ 2308.084755] Buffer I/O error on device sda1, logical block 1
[ 2308.084762] Buffer I/O error on device sda1, logical block 2
[ 2308.084768] Buffer I/O error on device sda1, logical block 3
[ 2312.188635] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2312.188638] sd 3:0:0:0: >[sda]  
[ 2312.188644] sd 3:0:0:0: >[sda]  
[ 2312.188663] sd 3:0:0:0: >[sda]  
[ 2312.188669] sd 3:0:0:0: >[sda] CDB: 
[ 2312.188678] end_request: I/O error, dev sda, sector 2062
[ 2312.188682] Buffer I/O error on device sda1, logical block 1
[ 2312.188685] Buffer I/O error on device sda1, logical block 2
[ 2312.188688] Buffer I/O error on device sda1, logical block 3
[ 2317.452772] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2317.452775] sd 3:0:0:0: >[sda]  
[ 2317.452781] sd 3:0:0:0: >[sda]  
[ 2317.452804] sd 3:0:0:0: >[sda]  
[ 2317.452812] sd 3:0:0:0: >[sda] CDB: 
[ 2317.452823] end_request: I/O error, dev sda, sector 2062
[ 2317.452831] Buffer I/O error on device sda1, logical block 1
[ 2321.508696] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2321.508703] sd 3:0:0:0: >[sda]  
[ 2321.508714] sd 3:0:0:0: >[sda]  
[ 2321.508761] sd 3:0:0:0: >[sda]  
[ 2321.508775] sd 3:0:0:0: >[sda] CDB: 
[ 2321.508797] end_request: I/O error, dev sda, sector 2062
[ 2321.508807] Buffer I/O error on device sda1, logical block 1
[ 2325.600589] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2325.600592] sd 3:0:0:0: >[sda]  
[ 2325.600598] sd 3:0:0:0: >[sda]  
[ 2325.600617] sd 3:0:0:0: >[sda]  
[ 2325.600623] sd 3:0:0:0: >[sda] CDB: 
[ 2325.600632] end_request: I/O error, dev sda, sector 2062
[ 2325.600636] Buffer I/O error on device sda1, logical block 1
[ 2329.664696] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2329.664703] sd 3:0:0:0: >[sda]  
[ 2329.664714] sd 3:0:0:0: >[sda]  
[ 2329.664763] sd 3:0:0:0: >[sda]  
[ 2329.664777] sd 3:0:0:0: >[sda] CDB: 
[ 2329.664798] end_request: I/O error, dev sda, sector 2062
[ 2329.664809] Buffer I/O error on device sda1, logical block 1
[ 2333.764661] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2333.764668] sd 3:0:0:0: >[sda]  
[ 2333.764679] sd 3:0:0:0: >[sda]  
[ 2333.764728] sd 3:0:0:0: >[sda]  
[ 2333.764742] sd 3:0:0:0: >[sda] CDB: 
[ 2333.764763] end_request: I/O error, dev sda, sector 2062
[ 2333.764773] Buffer I/O error on device sda1, logical block 1
[ 2337.800641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2337.800648] sd 3:0:0:0: >[sda]  
[ 2337.800659] sd 3:0:0:0: >[sda]  
[ 2337.800708] sd 3:0:0:0: >[sda]  
[ 2337.800722] sd 3:0:0:0: >[sda] CDB: 
[ 2337.800744] end_request: I/O error, dev sda, sector 2062
[ 2337.800753] Buffer I/O error on device sda1, logical block 1
[ 2341.832632] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2341.832639] sd 3:0:0:0: >[sda]  
[ 2341.832649] sd 3:0:0:0: >[sda]  
[ 2341.832697] sd 3:0:0:0: >[sda]  
[ 2341.832710] sd 3:0:0:0: >[sda] CDB: 
[ 2341.832732] end_request: I/O error, dev sda, sector 2062
[ 2341.832740] Buffer I/O error on device sda1, logical block 1
[ 2345.880832] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2345.880840] sd 3:0:0:0: >[sda]  
[ 2345.880852] sd 3:0:0:0: >[sda]  
[ 2345.880904] sd 3:0:0:0: >[sda]  
[ 2345.880920] sd 3:0:0:0: >[sda] CDB: 
[ 2345.880944] end_request: I/O error, dev sda, sector 2062
[ 2345.880957] Buffer I/O error on device sda1, logical block 1
[ 2349.980650] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2349.980656] sd 3:0:0:0: >[sda]  
[ 2349.980668] sd 3:0:0:0: >[sda]  
[ 2349.980715] sd 3:0:0:0: >[sda]  
[ 2349.980729] sd 3:0:0:0: >[sda] CDB: 
[ 2349.980750] end_request: I/O error, dev sda, sector 2062
[ 2349.980759] Buffer I/O error on device sda1, logical block 1
[ 2354.001039] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2354.001046] sd 3:0:0:0: >[sda]  
[ 2354.001057] sd 3:0:0:0: >[sda]  
[ 2354.001104] sd 3:0:0:0: >[sda]  
[ 2354.001118] sd 3:0:0:0: >[sda] CDB: 
[ 2354.001139] end_request: I/O error, dev sda, sector 2062
[ 2354.001149] Buffer I/O error on device sda1, logical block 1
[ 2358.180598] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2358.180600] sd 3:0:0:0: >[sda]  
[ 2358.180605] sd 3:0:0:0: >[sda]  
[ 2358.180625] sd 3:0:0:0: >[sda]  
[ 2358.180630] sd 3:0:0:0: >[sda] CDB: 
[ 2358.180639] end_request: I/O error, dev sda, sector 2062
[ 2358.180643] Buffer I/O error on device sda1, logical block 1
[ 2362.205124] sd 3:0:0:0: >[sda] Unhandled sense code
[ 2362.205131] sd 3:0:0:0: >[sda]  
[ 2362.205142] sd 3:0:0:0: >[sda]  
[ 2362.205189] sd 3:0:0:0: >[sda]  
[ 2362.205203] sd 3:0:0:0: >[sda] CDB: 
[ 2362.205224] end_request: I/O error, dev sda, sector 2062
[ 2362.205233] Buffer I/O error on device sda1, logical block 1
[ 3774.852657] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3774.852664] sd 3:0:0:0: >[sda]  
[ 3774.852677] sd 3:0:0:0: >[sda]  
[ 3774.852724] sd 3:0:0:0: >[sda]  
[ 3774.852740] sd 3:0:0:0: >[sda] CDB: 
[ 3774.852761] end_request: I/O error, dev sda, sector 2062
[ 3774.852769] Buffer I/O error on device sda1, logical block 1
[ 3774.852775] Buffer I/O error on device sda1, logical block 2
[ 3774.852781] Buffer I/O error on device sda1, logical block 3
[ 3778.888634] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3778.888641] sd 3:0:0:0: >[sda]  
[ 3778.888653] sd 3:0:0:0: >[sda]  
[ 3778.888699] sd 3:0:0:0: >[sda]  
[ 3778.888713] sd 3:0:0:0: >[sda] CDB: 
[ 3778.888734] end_request: I/O error, dev sda, sector 2062
[ 3778.888742] Buffer I/O error on device sda1, logical block 1
[ 3783.000832] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3783.000838] sd 3:0:0:0: >[sda]  
[ 3783.000849] sd 3:0:0:0: >[sda]  
[ 3783.000896] sd 3:0:0:0: >[sda]  
[ 3783.000910] sd 3:0:0:0: >[sda] CDB: 
[ 3783.000931] end_request: I/O error, dev sda, sector 2062
[ 3783.001011] EXT4-fs (sda1): can't read group descriptor 0
[ 3783.335650] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[ 3788.832644] sd 3:0:0:0: >[sda] Unhandled sense code
[ 3788.832650] sd 3:0:0:0: >[sda]  
[ 3788.832661] sd 3:0:0:0: >[sda]  
[ 3788.832708] sd 3:0:0:0: >[sda]  
[ 3788.832721] sd 3:0:0:0: >[sda] CDB: 
[ 3788.832742] end_request: I/O error, dev sda, sector 2062
[ 4607.852623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4607.852630] sd 3:0:0:0: >[sda]  
[ 4607.852642] sd 3:0:0:0: >[sda]  
[ 4607.852689] sd 3:0:0:0: >[sda]  
[ 4607.852703] sd 3:0:0:0: >[sda] CDB: 
[ 4607.852724] end_request: I/O error, dev sda, sector 2062
[ 4607.852732] Buffer I/O error on device sda1, logical block 1
[ 4611.872641] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4611.872648] sd 3:0:0:0: >[sda]  
[ 4611.872660] sd 3:0:0:0: >[sda]  
[ 4611.872707] sd 3:0:0:0: >[sda]  
[ 4611.872723] sd 3:0:0:0: >[sda] CDB: 
[ 4611.872743] end_request: I/O error, dev sda, sector 2062
[ 4611.872752] Buffer I/O error on device sda1, logical block 1
[ 4615.896649] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4615.896655] sd 3:0:0:0: >[sda]  
[ 4615.896667] sd 3:0:0:0: >[sda]  
[ 4615.896713] sd 3:0:0:0: >[sda]  
[ 4615.896727] sd 3:0:0:0: >[sda] CDB: 
[ 4615.896748] end_request: I/O error, dev sda, sector 2062
[ 4615.896756] Buffer I/O error on device sda1, logical block 1
[ 4619.920623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4619.920630] sd 3:0:0:0: >[sda]  
[ 4619.920640] sd 3:0:0:0: >[sda]  
[ 4619.920688] sd 3:0:0:0: >[sda]  
[ 4619.920701] sd 3:0:0:0: >[sda] CDB: 
[ 4619.920723] end_request: I/O error, dev sda, sector 2062
[ 4619.920734] Buffer I/O error on device sda1, logical block 1
[ 4623.940623] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4623.940630] sd 3:0:0:0: >[sda]  
[ 4623.940641] sd 3:0:0:0: >[sda]  
[ 4623.940689] sd 3:0:0:0: >[sda]  
[ 4623.940703] sd 3:0:0:0: >[sda] CDB: 
[ 4623.940724] end_request: I/O error, dev sda, sector 2062
[ 4623.940733] Buffer I/O error on device sda1, logical block 1
[ 4627.976639] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4627.976646] sd 3:0:0:0: >[sda]  
[ 4627.976656] sd 3:0:0:0: >[sda]  
[ 4627.976703] sd 3:0:0:0: >[sda]  
[ 4627.976716] sd 3:0:0:0: >[sda] CDB: 
[ 4627.976738] end_request: I/O error, dev sda, sector 2062
[ 4627.976748] Buffer I/O error on device sda1, logical block 1
[ 4632.008625] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4632.008631] sd 3:0:0:0: >[sda]  
[ 4632.008642] sd 3:0:0:0: >[sda]  
[ 4632.008689] sd 3:0:0:0: >[sda]  
[ 4632.008704] sd 3:0:0:0: >[sda] CDB: 
[ 4632.008724] end_request: I/O error, dev sda, sector 2062
[ 4632.008734] Buffer I/O error on device sda1, logical block 1
[ 4636.032638] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4636.032645] sd 3:0:0:0: >[sda]  
[ 4636.032656] sd 3:0:0:0: >[sda]  
[ 4636.032704] sd 3:0:0:0: >[sda]  
[ 4636.032726] sd 3:0:0:0: >[sda] CDB: 
[ 4636.032746] end_request: I/O error, dev sda, sector 2062
[ 4636.032755] Buffer I/O error on device sda1, logical block 1
[ 4640.076624] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4640.076630] sd 3:0:0:0: >[sda]  
[ 4640.076641] sd 3:0:0:0: >[sda]  
[ 4640.076688] sd 3:0:0:0: >[sda]  
[ 4640.076703] sd 3:0:0:0: >[sda] CDB: 
[ 4640.076723] end_request: I/O error, dev sda, sector 2062
[ 4640.076731] Buffer I/O error on device sda1, logical block 1
[ 4644.112592] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4644.112596] sd 3:0:0:0: >[sda]  
[ 4644.112602] sd 3:0:0:0: >[sda]  
[ 4644.112625] sd 3:0:0:0: >[sda]  
[ 4644.112632] sd 3:0:0:0: >[sda] CDB: 
[ 4644.112643] end_request: I/O error, dev sda, sector 2062
[ 4644.112647] Buffer I/O error on device sda1, logical block 1
[ 4648.144918] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4648.144922] sd 3:0:0:0: >[sda]  
[ 4648.144929] sd 3:0:0:0: >[sda]  
[ 4648.144952] sd 3:0:0:0: >[sda]  
[ 4648.144961] sd 3:0:0:0: >[sda] CDB: 
[ 4648.144971] end_request: I/O error, dev sda, sector 2062
[ 4648.144981] Buffer I/O error on device sda1, logical block 1
[ 4652.168708] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4652.168715] sd 3:0:0:0: >[sda]  
[ 4652.168726] sd 3:0:0:0: >[sda]  
[ 4652.168774] sd 3:0:0:0: >[sda]  
[ 4652.168788] sd 3:0:0:0: >[sda] CDB: 
[ 4652.168809] end_request: I/O error, dev sda, sector 2062
[ 4652.168820] Buffer I/O error on device sda1, logical block 1
[ 4656.188786] sd 3:0:0:0: >[sda] Unhandled sense code
[ 4656.188792] sd 3:0:0:0: >[sda]  
[ 4656.188803] sd 3:0:0:0: >[sda]  
[ 4656.188850] sd 3:0:0:0: >[sda]  
[ 4656.188863] sd 3:0:0:0: >[sda] CDB: 
[ 4656.188885] end_request: I/O error, dev sda, sector 2062
[ 4656.188964] EXT4-fs (sda1): can't read group descriptor 0
[ 5386.778629] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended
[ 5386.778939] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)


```Seems to be something wrong with the disk or partition.
[http://askubuntu.com/questions/59064/how-to-run-a-checkdisk](http://askubuntu.com/questions/59064/how-to-run-a-checkdisk)

---

### Post by nosmokenofire on 2013-02-11
> **Bufeu said:**
> Seems to be something wrong with the disk or partition.
[http://askubuntu.com/questions/59064/how-to-run-a-checkdisk](http://askubuntu.com/questions/59064/how-to-run-a-checkdisk)
  
with disk utility the self test failed.

---

### Post by Bufeu on 2013-02-11
> **nosmokenofire said:**
> with disk utility the self test failed.Any errors?

---

### Post by nosmokenofire on 2013-02-11
so as I understand it there is not a lot I can do. For some reason I have wiped my sda1 partition, or at least damaged it in some way.

Does this mean that I can reformat it and start again or does it mean that there is something wrong with the HD and I need to look at getting a replacement?

thanks to anyone who can help...

---

### Post by nosmokenofire on 2013-02-12
> **Bucky Ball said:**
> Ah, the power button could have done something, but still confused. I suggest attempting to boot from sda5 as it looks like that has a bootable grub installed (does that install show up in the kernel list at boot?) and having a closer look from there.

Does anyone out there know how I can do this if I get no grub on boot?

I'm really stuck here... I'm starting to think my hardware may be damaged.

---

