---
title: "How To Install Plop Boot Manager and Clonezilla in GRUB2 Boot Menu"
date: 2014-06-19
forum: General Help
---

### Post by randy12 on 2014-06-19
hi guys m totally new to forums and this is my first thread need help i hve dual booted lubuntu and windows xp now my pc cant boot from usb so i need plop boot manager in grub2 boot menu i followed the instruction and i suceed but i also want clonezilla to be installed in the grub menu 2 but both requires to edit 40-custom grub file so i want to ask that is there any way to install both of them in the grub2 menu plzzz help.............i have been googling alot but no hope forum is my last hope plz help me thnx in advance ;)

---

### Post by sudodus on 2014-06-19
Welcome to the Ubuntu Forums :-)

It is much simpler to get a few rather cheap 4 GB pendrives (for example Sandisk Cruzer Blade USB 2.0 4GB). This pendrive is far from fast, but it can boot most computers that boot from USB, and has been reliable for me and it is cheap. See [this link for more details about booting from pendrives]("https://help.ubuntu.com/community/Installation/FromUSBStick").

It might also be a good idea to make a Plop boot CD if your computer can boot from CD.

You can consider a USB pendrive to be a temporary device, where you keep the system(s) that you are using for a period of time. It can be reused many times and in the long run it is both faster and cheaper than to burn CDs.

It is possible to find the commands for the **40-custom** file, but that set of commands might not work for a new version of the iso file (in this case Clonezilla).

If you really like multi-booting, you can check the following links

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by Bucky Ball on 2014-06-19
Welcome. You don't want them in grub. As sudodus suggests, grab some USB dongles and you'll have them on hand and also transportable. What makes you think you need plop to fix a USB that's not booting? Why not try and find out why it's not booting? Cart before the horse and probably complicating things. 

You don't need to install Clonezilla onto a hard drive. There is no reason to. Me thinks you're going slightly the wrong way about this. :-k

Your actual question is 'Why can't I boot from USB?' Presuming you have the machine set to boot from USB? What is the error message (details rather than USB won't boot) or what is happening? Ignoring the USB and booting from the hard drive? What are you trying to boot on the USB?

Unfortunately, we are not psychic, so fill us in with all details and perhaps focus on why you can't boot from USB for starters rather than dive down a slippery slope of complication without knowing whether you actually need to ...

---

### Post by randy12 on 2014-06-19
Guys u both dint understood my question I hve apc tht dnt got boot from usb option so I installed plopon grub2 then I thought tht it would be great tht I could be able to add clonezilla to grub2 in short I wnt a way through which I can put plop and clonezilla both simultaneously in thegrub2 boot menu. And I dnt wnt to use cds or usbs

---

### Post by sudodus on 2014-06-19
I think I understood your question, but it is not the way I would recommend using Clonezilla.

Have a look at these links (but be prepared that the scripts may need modifications for a new version of Clonezilla)
[URL="http://ubuntuforums.org/showthread.php?t=1508896"]
clonezilla grub2 entry[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=1549847"]
ISO Booting with Grub 2

[/URL]

---

### Post by randy12 on 2014-06-20
bro clonezilla entry works fine but i also need a entry for plop boot manager not iso booting with grub2 my pc dont support booting from usb thts why plop is necessary for me make entry for plop in grub2. when i followed clonezilla and plopo tutorials on for grub2 i succeed but the problem is that both requires to edit 40-custom file and if i edit the file with plop entry plop will only work and clonezilla wont coz it also requires to edit 40-custom file so tell me a way through which i can  add 2 entries in grub2 so that both plop and clonezilla comes in my grub2 menu.

---

### Post by sudodus on 2014-06-20
You can have many entries after each other in **40_custom**

This is mine:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Puppy Linux 5.3 frugal in /media/multimed-2/wary5.3frugal" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90
    linux /wary5.3frugal/vmlinuz pmedia=atahd psubdir=wary5.3frugal
    initrd /wary5.3frugal/initrd.gz
}
menuentry "(multimed-2)/CD/knoppix/knoppix.iso" {
set isofile="/CD/knoppix/knoppix.iso"
loopback loop (hd0,2)$isofile
echo "Loading linux"
linux (loop)/boot/isolinux/linux bootfrom=/dev/sda2$isofile noprompt noeject
echo "Loading minirt"
initrd (loop)/boot/isolinux/minirt.gz
}
menuentry "Boot UBUNTU 10+ BASED SYSTEM from /media/multimed-2/CD/candidate.iso" {
 set isofile="/CD/candidate.iso"
 set root='(/dev/sda,msdos2)'
 search --no-floppy --fs-uuid --set=root d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90
 loopback loop ($root)$isofile
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
 initrd (loop)/casper/initrd.lz
}
```

---

### Post by randy12 on 2014-06-20
thnkx bro i edit and see it then ill make this thread as solved :-)

---

### Post by randy12 on 2014-06-20
hi bro m unable to make plop boot custom entry when i do in 40-custom  after updating grub it does not shows up in grub.cfg i restarted my pc  but no plop option came heres my custom-40 entry


```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'Plop Boot Manager'{
        insmod ext2
        set root='hd1,msdos6'
        search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        linux16    /boot/plpbt.bin
}
```



i dont know whts wrong hers my grub.cfg file



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
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
else
  search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class  os $menuentry_id_option  'gnulinux-simple-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu  --class gnu-linux --class gnu --class os $menuentry_id_option  'gnulinux-3.13.0-24-generic-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'  {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)'  --class ubuntu --class gnu-linux --class gnu --class os  $menuentry_id_option  'gnulinux-3.13.0-24-generic-recovery-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'  {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6  --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class  windows --class os $menuentry_id_option  'osprober-chain-4536900336108B5E' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1  --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'   4536900336108B5E
    else
      search --no-floppy --fs-uuid --set=root 4536900336108B5E
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by Bucky Ball on 2014-06-20
PLEASE use [code] tags for terminal output and terminal files. Thanks.

I have given you an example in your last post.

---

### Post by randy12 on 2014-06-20
```
{
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
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'    ca5c8f30-0ad3-4db2-bf6e-940b8874108e
else
  search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class   os $menuentry_id_option   'gnulinux-simple-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'    ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu   --class gnu-linux --class gnu --class os $menuentry_id_option   'gnulinux-3.13.0-24-generic-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'   {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)'   --class ubuntu --class gnu-linux --class gnu --class os   $menuentry_id_option   'gnulinux-3.13.0-24-generic-recovery-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'   {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'    ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6   --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'    ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class   windows --class os $menuentry_id_option   'osprober-chain-4536900336108B5E' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1   --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'    4536900336108B5E
    else
      search --no-floppy --fs-uuid --set=root 4536900336108B5E
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###                                                                                                                                    
}

```

---

### Post by sudodus on 2014-06-20
The file (including full path) must be ***/etc/grub.d/40_custom*** (with underscore, not minus or hyphen), and it must be executable.

```
ls -l  /etc/grub.d/40_custom
-rwxr-xr-x 1 root root 1511 dec 28  2012 /etc/grub.d/40_custom
```

Then ```
sudo update-grub
``` should give you the entry in ***/boot/grub/grub.cfg***

---

### Post by Bucky Ball on 2014-06-20
One more time: Please use [code] tags. It makes your output much clearer and easier to read as it retains the original formatting.

If you don't know the syntax or how to read them, click 'Edit' on the post of yours I added them to and find out.

---

### Post by randy12 on 2014-06-20
Output:

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
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'     ca5c8f30-0ad3-4db2-bf6e-940b8874108e
else
  search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class    os $menuentry_id_option    'gnulinux-simple-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'     ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu    --class gnu-linux --class gnu --class os $menuentry_id_option    'gnulinux-3.13.0-24-generic-advanced-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'    {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6   --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)'    --class ubuntu --class gnu-linux --class gnu --class os    $menuentry_id_option    'gnulinux-3.13.0-24-generic-recovery-ca5c8f30-0ad3-4db2-bf6e-940b8874108e'    {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6   --hint='hd1,msdos6'   ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        else
          search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=ca5c8f30-0ad3-4db2-bf6e-940b8874108e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'     ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6    --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd1,msdos6'     ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    else
      search --no-floppy --fs-uuid --set=root ca5c8f30-0ad3-4db2-bf6e-940b8874108e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Microsoft Windows XP Professional (on /dev/sda1)' --class    windows --class os $menuentry_id_option    'osprober-chain-4536900336108B5E' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1    --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'     4536900336108B5E
    else
      search --no-floppy --fs-uuid --set=root 4536900336108B5E
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###                                                                                                                                      
}
```

---

### Post by sudodus on 2014-06-20
Try with a space before the curly brace:

Change from
```
menuentry 'Plop Boot Manager'{
```
to
```
menuentry 'Plop Boot Manager' {
```

---

### Post by randy12 on 2014-06-20
i did it but still same result c ustom entry not added in grub.cfg after error plz help

---

### Post by randy12 on 2014-06-20
hi guys i have dual booted xp and lubuntu and got a plop custom entry i want to add clonezilla to my grub boot menu plz tell me how to makeits 40_ cutom menu entry and it will be very helpful if you tell me its output i mean how its gonna look in grub.cfg after updating grub plz help me thnkx in advance:)

---

### Post by yancek on 2014-06-20
The entry below worked for me with the clonezilla iso file extracted and copied to the / of the drive.  I got this info from the clonezilla site but I don't have it bookmarked:

> menuentry "Clonezilla" {
set root=(hd0,1)
linux /live-hd/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" ip=frommedia nosplash live-media-path=/live-hd bootfrom=/dev/sdb1 toram=filesystem.squashfs
initrd /live-hd/initrd.img
}

This was over a year ago so I don't know that it will work on newer versions.  You will need to make the appropriate changes as to drive/partition.

---

### Post by randy12 on 2014-06-20
its not working can u post your grub.cfg file here so tht i will try to manuallyedit my grub.cfg maybe tht will work for me

---

### Post by yancek on 2014-06-20
> its not working can u post your grub.cfg file

What's not working?  My grub.cfg file isn't going to help.  I already posted the menuentry for clonezilla above.  Which partition is your clonezilla on?  You will have to change the entry above to reflect that.  The set root=(hd0,1) would mean it is on sda1.  If it is not, change it.  Also change the line after bootfrom=.  My entry shows /dev/sdb1.  I would suggest you try a few options here.  Are you trying to boot the clonezilla iso directly?   The link below shows an entry which is supposed to work?

[http://cbowman57.deviantart.com/journal/Booting-Clonezilla-iso-with-Grub2-348811954](http://cbowman57.deviantart.com/journal/Booting-Clonezilla-iso-with-Grub2-348811954)
 Did you extract the clonezilla files to the root of the partition

Have you extracted the clonezilla iso?  The menuentry I posted requires that, in the / of the filesystem you are booting from.

---

### Post by sudodus on 2014-06-20
I'm sorry, but I have no more tip than what is in my previous posts, particularly in post #12 and post #15, except that you can add the content of 40_custom ***manually*** at the end of /boot/grub/grub.cfg with an editor.

```
sudo nano /boot/grub/grub.cfg
```

Check carefully that there are no extra or unmatched curly braces '{' or '}'

---

### Post by coffeecat on 2014-06-21
Threads merged. Please stop starting new threads about the same issue.

---

