---
title: "How do I make grub interactive? (display menu)"
date: 2016-01-02
forum: General Help
---

### Post by dmtparker on 2016-01-02
On my installation of Ubuntu Studio 14.04.3, grub is totally silent and just boots the current (latest) kernal. The most recent update (kernal 3.13.0-74-lowlatency) has a problem (doesn't recognize usb3 devices) and I want to boot into the older kernal until the issue is fixed. I've looked at grub.cfg and there are, in fact, menu entries for older kernals, but I do not know how to get grub to display the menu instead of just booting automatically. Back when grub first replaced lilo, it was pretty easy to edit, but now...... I can't begin to figure out what to change! FWIW I have tried booting with all the usual keys depressed to no avail (shift, cntrl, alt, esc). Hopefully this is a really easy fix and I can get back to the older kernal. Thanks for the help.

---

### Post by Bucky Ball on 2016-01-02
*Thread moved to **General Help**.*

... as the fix applies to any flavour, not just Ubuntu Studio. :)

Leave grub.cfg alone. We don't, under normal circumstances, tweak that. You tweak /etc/default/grub then 'sudo update-grub'. That will write the changes to grub.cfg.

So, there are two ways of going about this. After booting your machine, tap the shift key prior to Ubuntu booting. That should bring up the grub menu where you can choose a kernel. 

If you want it to show the kernels on every boot, open a terminal and:

```
sudo nano /etc/default/grub
```

... and change these lines there to look like these:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=10**

```

Leave everything else as it is. The important line I have made bold. Hope that helps and good luck.

---

### Post by dmtparker on 2016-01-02
Thanks, but my file already has those lines exactly. Here is what mine says:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I've tried the shift key (and esc and alt and cntrl) to no avail. In fact, I just noticed that in the past I got a splash screen that said "Intel NUC" and gave options for entering bios, boot order, etc. and now I don't even see that. On boot there is a single line of text that flashes too quickly to read and then the rotating circle for ubuntu studio and boot proceeds.
I doubt it matters, but I have an Intel NUC i5 and the keyboard is via a dongle (usb2 thankfully)

---

### Post by Dennis N on 2016-01-02
If there is only one OS installed, then you would normally get no menu on startup. Holding the Shift is said to override that behavior and get you the menu. 

Another way that has worked for me is to change the value of **GRUB_TIMEOUT=** to **-1** in /etc/default/grub which stops bootup at the grub menu until you make a selection. As far as I know, this setting still works (I still use it in Xubuntu 14.04 grub in a multiboot setup), even though you can see warnings when saving the file that this is deprecated.

Don't forget to run sudo update-grub after editing /etc/default/grub.
.

---

### Post by grahammechanical on 2016-01-02
Have you edited /etc/default/grub by changing the GRUB_TIMEOUT= line? And then did you run sudo update-grub. We need to do that for the changes to take effect and it is something that we can forget to do. So, it is worth confirming that this has been done.

Regards.

---

### Post by dmtparker on 2016-01-02
> **grahammechanical said:**
> Have you edited /etc/default/grub by changing the GRUB_TIMEOUT= line? And then did you run sudo update-grub. We need to do that for the changes to take effect and it is something that we can forget to do. So, it is worth confirming that this has been done.

Regards.

I did not edit etc/default/grub. What I posted is as it came.
I will try the =-1.

---

### Post by dmtparker on 2016-01-02
> **Dennis N said:**
> If there is only one OS installed, then you would normally get no menu on startup. Holding the Shift is said to override that behavior and get you the menu. 

Another way that has worked for me is to change the value of **GRUB_TIMEOUT=** to **-1** in /etc/default/grub which stops bootup at the grub menu until you make a selection. As far as I know, this setting still works (I still use it in Xubuntu 14.04 grub in a multiboot setup), even though you can see warnings when saving the file that this is deprecated.

Don't forget to run sudo update-grub after editing /etc/default/grub.
.

Just tried the -1 (AND did the update-grub) but it still just immediately boots into current kernal.

Just in case I'm missing something, here is the full text of /etc/default/grub:[INDENT]```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
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

```[/INDENT]

Here is the resultant grub.cfg:[INDENT]```
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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
else
  search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
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

### BEGIN /etc/grub.d/09_lowlatency ###
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
menuentry 'Ubuntu (lowlatency)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
    else
      search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
    fi
    linux    /boot/vmlinuz-3.13.0-74-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-74-lowlatency
}

### END /etc/grub.d/09_lowlatency ###

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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
    else
      search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
    fi
    linux    /boot/vmlinuz-3.13.0-74-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-74-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
    menuentry 'Ubuntu, with Linux 3.13.0-74-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-74-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-74-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-74-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-74-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-74-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-74-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-74-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-74-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-73-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-73-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-73-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-73-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-73-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-73-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-73-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-73-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-73-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-73-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-71-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-71-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-71-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-71-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-71-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-71-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-71-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-70-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-70-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-70-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-70-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-70-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-70-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-70-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-68-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-68-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-68-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-68-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-68-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-68-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-68-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-68-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-68-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-68-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-67-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-67-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-67-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-67-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-67-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-67-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-67-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-67-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-67-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-67-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-66-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-lowlatency-advanced-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-66-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-66-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.13.0-66-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-lowlatency-recovery-2d449a68-a4c6-4cdf-b32b-d869bebdb634' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
        else
          search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
        fi
        echo    'Loading Linux 3.13.0-66-lowlatency ...'
        linux    /boot/vmlinuz-3.13.0-66-lowlatency root=UUID=2d449a68-a4c6-4cdf-b32b-d869bebdb634 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-lowlatency
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
    else
      search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  2d449a68-a4c6-4cdf-b32b-d869bebdb634
    else
      search --no-floppy --fs-uuid --set=root 2d449a68-a4c6-4cdf-b32b-d869bebdb634
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
[/INDENT]
Thanks for the continuing help.

---

### Post by Bucky Ball on 2016-01-02
They're not the same exactly. Look closely. You have:

```
GRUB_HIDDEN_TIMEOUT=0
```

I have:

```
#GRUB_HIDDEN_TIMEOUT=0
```

:)

Please use code tags (and add them to your last post, please) for all code/terminal output. See last link in my signature. Thanks.

---

### Post by Dennis N on 2016-01-02
What you show is what I have on that 14.04 system I refered to (using grub-efi-amd64 2.02~beta2). I have no explanation at the moment.

Looks like you have a custom file **/etc/grub.d/09_lowlatency** that would generate the default top menu entry. You should have two top level entries from looking at your grub.cfg, so the grub menu should be appearing with these titles: 

Ubuntu (lowlatency)
Ubuntu

Leaving that mystery unexplained, I suggest editing **/etc/grub.d/09_lowlatency** and changing 3.13.0-74 to 3.13.0-73 in all occurences and then save. Then run sudo update-grub and reboot. Should boot the -73 kernel whether the menu shows or not, I would think.

---

### Post by Dennis N on 2016-01-02
> What you show is what I have on that 14.04 system I refered to (using grub-efi-amd64 2.02~beta2). I have no explanation at the moment.

Yes, didn't notice your missing #: I also have #GRUB_HIDDEN_TIMEOUT=0

---

### Post by dmtparker on 2016-01-02
YES, commenting out that line gives me the option of choosing from a menu.
Thanks
Unfortunately, my reason for wanting to boot from an older kernel was that the most recent update (which included the -74 kernel) caused me to lose usb 3.0 functionality and I assumed it was the new kernel. That appears NOT to be the case as even dropping back to -70 (where I KNOW it was  working), I still cannot get usb 3.0 devices to work. I started another thread for that issue so I guess I should consider this issue SOLVED and I will pursue the other thread.

---

### Post by Bucky Ball on 2016-01-02
> **dmtparker said:**
> I still cannot get usb 3.0 devices to work. I started another thread for that issue so I guess I should consider this issue SOLVED and I will pursue the other thread.

Glad you got the menu working, sad it didn't solve the issue. Good luck on the other thread. Posting one was the way to go. Thanks. :)

---

