---
title: "Ubuntu 16.04 won't load without &quot;nomodeset&quot; - will blackscreen with AMDGPU-PRO -help!"
date: 2019-10-22
forum: General Help
---

### Post by tbilisiheat on 2019-10-22
Greetings forums,

I have come across an issue with one of my PCs which is really causing me to rip my hair out - I've lost the past two and a half days trying to self-research this issue and figure it out on my own, but have failed, and therefore I need your help!

I built a rig for BOINC/Folding@Home (Celeron CPU, 12GB RAM, 60GB SSD, 8X AMD RX460 4GB GPUs) and it has been running flawlessly for months on Windows 10 - not a hiccup either when folding or BOINC crunching.

I decided that I wanted to switch this rig to Linux for better performance and simplicity.  This is where the issues began.

Firstly, it has been impossible to get any Live USB installer working (except for Lubuntu 16.04, which is what I currently have loaded) - I tried different flavors of Manjaro, OpenSUSE, Mint, and others.  Every installer except for Lubuntu would hang at a black screen/blinking cursor prior to the DE loading.

Now, with Lubuntu, I couldn't install the OS without using "NOMODESET," and now, it will hang at a blinking cursor (or even an all black screen) if I try to boot with nomodeset removed.  Pressing CTRL-ALT-F3 dumps me to a terminal where I'm able to log in and interact with the OS via CLI, but I require the GUI for my tasks.

This is a huge problem for me since using Ubuntu with nomodeset forces me to use the generic drivers and not AMDGPU/AMDGPU-PRO, which I require for OpenCL compute capabilities (Folding@Home and Boinc won't work at all with nomodeset enabled).

I have confirmed the following:
1) GPUs are in working order and there are no hardware failures, as the PC works flawlessly under Windows 10 and also Lubuntu system profiler recognizes all of my GPUs properly
2) Lubuntu works smoothly and without issues as long as I boot wih NOMODESET
3) OpenCL is disabled with NOMODESET, but when I reboot, get blackscreen/cursored, then get into a terminal after removing NOMODESET, clinfo and *dpkg -l amdgpu-pro *confirm that OpenCL is functional and the AMDGPU-PRO driver is installed;
4) Upgrading Lubuntu 16.04 to 18.0.4 did not resolve the problem and in fact brought several more glitches and issues;
5) Reinstalling the OS from scratch and reinstalling AMDGPU-PRO did not resolve the problem;
6) Adding pci=noaer and/or pci=nomsi to kernel instructions/grub did not resolve;
7) Disabling AHCPI did nothing;
8) Folding@Home recognizes all 8 GPUs under nomodeset but of course, with OpenCL disabled and without AMDGPU/AMDGPU-PRO, can't fold or do tasks;
9) Changing the kernel, to 4.8 and trying 5.0+, did not resolve the issue.

I have concluded and theorized therefore that AMDGPU-PRO (as well as the open source/stock Radeon and AMDGPU drivers) is functional but for some other reason LXDE refuses to load without nomodeset.

Please assist - I think I've tried everything and this keeps failing....and after several days of tinkering I can't figure this out on my own!

```


ragnaros@ragnaros-YANYU:~$ dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  amdgpu-pro     17.40-492261 amd64        Meta package to install amdgpu Pr

ragnaros@ragnaros-YANYU:~$ uname -r
4.15.0-66-generic

ragnaros@ragnaros-YANYU:~$ clinfo
Number of platforms                               0



PC SPECS:
-Computer-
Processor        : 2x Intel(R) Celeron(R) CPU G3930 @ 2.90GHz
Memory        : 12215MB (753MB used)
Operating System        : Ubuntu 16.04.6 LTS
User Name        : ragnaros (ragnaros)
Date/Time        : 2019 &#4332;&#4314;&#4312;&#4321; 22 &#4317;&#4325;&#4322;&#4317;&#4315;&#4305;&#4308;&#4320;&#4312;, 19:57:41 +04
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
Audio Adapter        : HDA-Intel - HDA ATI HDMI
-Input Devices-
 Sleep Button
 Power Button
 Power Button
 Logitech K400 Plus
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA ATI HDMI HDMI/DP,pcm        : 3=
 HDA ATI HDMI HDMI/DP,pcm        : 7=
 HDA ATI HDMI HDMI/DP,pcm        : 8=
 HDA ATI HDMI HDMI/DP,pcm        : 9=
 HDA ATI HDMI HDMI/DP,pcm        : 10=
 HDA Intel PCH HDMI/DP,pcm        : 3=
-Printers-
No printers found
-SCSI Disks-
ATA MT-64

```

---

### Post by tbilisiheat on 2019-10-22
Here is my Boot-Info!

```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1716040. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 is already mounted or /mnt/BootInfo/sdb1 busy
mount: /dev/sdb2 is already mounted or /mnt/BootInfo/sdb2 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   100,044,799   100,042,752  83 Linux
/dev/sda2         100,046,846   125,044,735    24,997,890   5 Extended
/dev/sda5         100,046,848   125,044,735    24,997,888  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.8 GiB, 4026531840 bytes, 7864320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *              0     1,802,239     1,802,240   0 Empty
/dev/sdb2           1,716,040     1,720,903         4,864  ef EFI (FAT-12/16/32)

/dev/sdb1 overlaps with /dev/sdb2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1   +  R              0     1,802,183     1,802,184 Data partition (Windows/Linux)
/dev/sdb2   +  R      1,716,040     1,720,903         4,864 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4984cd92-ff93-447f-9881-5f9f4a6f3035   ext4       
/dev/sda5        0197cda2-453f-429b-81e3-f294b1595c30   swap       
/dev/sdb1        2017-02-15-20-52-49-00                 iso9660    Lubuntu 16.04.2 LTS amd64
/dev/sdb2        E561-C446                              vfat       
/dev/zram0       9267f930-bad7-4f5e-8e40-780b5ae92110   swap       
/dev/zram1       6b79d594-7590-44f9-b258-de70dd9e8e4e   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 22 16:26 ata-MT-64_978020960010 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 22 16:26 ata-MT-64_978020960010-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 22 16:26 ata-MT-64_978020960010-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 22 16:26 ata-MT-64_978020960010-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Oct 22 16:26 usb-Generic_Flash_Disk_01C08676-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 22 16:26 usb-Generic_Flash_Disk_01C08676-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 22 16:26 usb-Generic_Flash_Disk_01C08676-0:0-part2 -> ../../sdb2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
else
  search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
    else
      search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
    fi
        linux    /boot/vmlinuz-4.15.0-66-generic root=UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 ro nomodeset quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.15.0-66-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
    menuentry 'Ubuntu, with Linux 4.15.0-66-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-66-generic-advanced-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
        else
          search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
        fi
        echo    'Loading Linux 4.15.0-66-generic ...'
            linux    /boot/vmlinuz-4.15.0-66-generic root=UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 ro nomodeset quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 4.15.0-66-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-66-generic-recovery-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
        else
          search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
        fi
        echo    'Loading Linux 4.15.0-66-generic ...'
            linux    /boot/vmlinuz-4.15.0-66-generic root=UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 ro recovery nomodeset nomodeset
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-advanced-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
        else
          search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
            linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 ro nomodeset quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-36-generic-recovery-4984cd92-ff93-447f-9881-5f9f4a6f3035' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
        else
          search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
        fi
        echo    'Loading Linux 4.8.0-36-generic ...'
            linux    /boot/vmlinuz-4.8.0-36-generic root=UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 ro recovery nomodeset nomodeset
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-36-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
    else
      search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  4984cd92-ff93-447f-9881-5f9f4a6f3035
    else
      search --no-floppy --fs-uuid --set=root 4984cd92-ff93-447f-9881-5f9f4a6f3035
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
# / was on /dev/sda1 during installation
UUID=4984cd92-ff93-447f-9881-5f9f4a6f3035 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0197cda2-453f-429b-81e3-f294b1595c30 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  28.384387970 = 30.477504512   boot/grub/grub.cfg                             1
  28.376708984 = 30.469259264   boot/grub/i386-pc/core.img                     1
   7.643192291 = 8.206815232    boot/vmlinuz-4.15.0-66-generic                 1
   0.710895538 = 0.763318272    boot/vmlinuz-4.8.0-36-generic                  1
   7.643192291 = 8.206815232    vmlinuz                                        1
   0.710895538 = 0.763318272    vmlinuz.old                                    1
   7.836910248 = 8.414818304    boot/initrd.img-4.15.0-66-generic              5
   7.368160248 = 7.911501824    boot/initrd.img-4.8.0-36-generic               3
   7.836910248 = 8.414818304    initrd.img                                     5
   7.368160248 = 7.911501824    initrd.img.old                                 3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  3c fa 19 00 00 00 00 00  81 74 c2 34 00 00 80 00  |<........t.4....|
000001c0  01 00 00 3f e0 6f 00 00  00 00 00 80 1b 00 00 fe  |...?.o..........|
000001d0  ff ff ef fe ff ff 48 2f  1a 00 00 13 00 00 00 00  |......H/........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sdb1: unknown GPT attributes
1000000000000001

/dev/sdb2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sdb1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  3c fa 19 00 00 00 00 00  81 74 c2 34 00 00 80 00  |<........t.4....|
000001c0  01 00 00 3f e0 6f 00 00  00 00 00 80 1b 00 00 fe  |...?.o..........|
000001d0  ff ff ef fe ff ff 48 2f  1a 00 00 13 00 00 00 00  |......H/........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/4389/mounts) leaked on lvs invocation. Parent PID 11319: bash
File descriptor 63 (pipe:[37202]) leaked on lvs invocation. Parent PID 11319: bash

ADDITIONAL INFORMATION :
=================== log of boot-info 20191022_1626 ===================
boot-info version : 4ppa66
boot-sav version : 4ppa66
boot-sav-extra version : 4ppa66
glade2script version : 3.2.3~ppa4
grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
boot-info is executed in live-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash ---  nomodeset
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda1:Ubuntu 16.04.6 LTS (16.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="4984cd92-ff93-447f-9881-5f9f4a6f3035" TYPE="ext4" PARTUUID="c9cff9af-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="0197cda2-453f-429b-81e3-f294b1595c30" TYPE="swap" PARTUUID="c9cff9af-05"
/dev/sdb1: UUID="2017-02-15-20-52-49-00" LABEL="Lubuntu 16.04.2 LTS amd64" TYPE="iso9660" PTUUID="34c27481" PTTYPE="dos" PARTUUID="34c27481-01"
/dev/sdb2: SEC_TYPE="msdos" UUID="E561-C446" TYPE="vfat" PARTUUID="34c27481-02"
/dev/zram0: UUID="9267f930-bad7-4f5e-8e40-780b5ae92110" TYPE="swap"
/dev/zram1: UUID="6b79d594-7590-44f9-b258-de70dd9e8e4e" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Oct 22 07:47 grub.d
total 80
-rwxr-xr-x 1 root root  9791 Jan 13  2017 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Apr 29 19:04 10_linux
-rwxr-xr-x 1 root root 11082 Jan 13  2017 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jan 13  2017 30_os-prober
-rwxr-xr-x 1 root root  1418 Jan 13  2017 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 13  2017 40_custom
-rwxr-xr-x 1 root root   216 Jan 13  2017 41_custom
-rw-r--r-- 1 root root   483 Jan 13  2017 README




=================== sda1/etc/default/grub :

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
GRUB_CMDLINE_LINUX="nomodeset"

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
[    0.000000] ACPI: UEFI 0x00000000BCC2BB78 000042 (v01 ALASKA A M I    00000002      01000013)
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:64.0GB:scsi:512:512:msdos:ATA MT-64:;
1:1049kB:51.2GB:51.2GB:ext4::boot;
2:51.2GB:64.0GB:12.8GB:::;
5:51.2GB:64.0GB:12.8GB:linux-swap(v1)::;

BYT;
/dev/sdb:4027MB:scsi:512:512:unknown:Generic Flash Disk:;

BYT;
/dev/zram1:3129MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:3129MB:3129MB:linux-swap(v1)::;

BYT;
/dev/zram0:3129MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:3129MB:3129MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sdb   disk iso9660    3.8G Lubuntu 16.04.2 LTS amd64
sdb2  part vfat       2.4M Lubuntu 16.04.2 LTS amd64
sdb1  part iso9660    880M Lubuntu 16.04.2 LTS amd64
zram1 disk            2.9G
loop0 loop squashfs 830.9M
sda   disk           59.6G
sda2  part              1K
sda5  part swap      11.9G
sda1  part ext4      47.7G
zram0 disk            2.9G

KNAME ROTA RO RM STATE   MOUNTPOINT
sdb      1  0  1 running /cdrom
sdb2     1  0  1
sdb1     1  0  1
zram1    0  0  0         [SWAP]
loop0    1  1  0         /rofs
sda      0  0  0 running
sda2     0  0  0
sda5     0  0  0         [SWAP]
sda1     0  0  0         /mnt/boot-sav/sda1
zram0    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=6095376k,nr_inodes=1523844,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1222196k,mode=755)
/dev/sdb on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=bec2371ea19567fc)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=11633)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1222196k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse gpiochip0 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.9G     0  5.9G   0% /dev
tmpfs          tmpfs     1.2G  9.9M  1.2G   1% /run
/dev/sdb       iso9660   880M  880M     0 100% /cdrom
/dev/loop0     squashfs  831M  831M     0 100% /rofs
aufs           aufs      5.9G  134M  5.7G   3% /
tmpfs          tmpfs     5.9G   25M  5.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G  4.0K  5.9G   1% /tmp
tmpfs          tmpfs     1.2G  4.0K  1.2G   1% /run/user/999
/dev/sda1      ext4       47G  8.8G   36G  20% /mnt/boot-sav/sda1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 830.9 MiB, 871223296 bytes, 1701608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc9cff9af

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 100044799 100042752 47.7G 83 Linux
/dev/sda2       100046846 125044735  24997890 11.9G  5 Extended
/dev/sda5       100046848 125044735  24997888 11.9G 82 Linux swap / Solaris


Disk /dev/sdb: 3.8 GiB, 4026531840 bytes, 7864320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x34c27481

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 1802239 1802240  880M  0 Empty
/dev/sdb2       1716040 1720903    4864  2.4M ef EFI (FAT-12/16/32)


Disk /dev/zram0: 2.9 GiB, 3128815616 bytes, 763871 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 2.9 GiB, 3128815616 bytes, 763871 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.


```

---

