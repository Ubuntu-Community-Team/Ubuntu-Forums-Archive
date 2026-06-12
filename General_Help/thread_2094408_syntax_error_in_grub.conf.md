---
title: "syntax error in grub.conf"
date: 2012-12-13
forum: General Help
---

### Post by Dopaque on 2012-12-13
edited /etc/default/grub without backing it up first (stupid me I know)

does someone have a working grub.conf for ubuntu 12.10 that I could copy and paste into there?

this is what I have now:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by Dopaque on 2012-12-13
just wanted to include the error message when I try to update the above

```
[sudo] password for jam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.6.9-030609-generic
Found initrd image: /boot/initrd.img-3.6.9-030609-generic
Found linux image: /boot/vmlinuz-3.5.1-030501-generic
Found initrd image: /boot/initrd.img-3.5.1-030501-generic
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda6
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 291
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done

```

---

### Post by Kirk Schnable on 2012-12-13
> **Dopaque said:**
> edited /etc/default/grub without backing it up first (stupid me I know)

does someone have a working grub.conf for ubuntu 12.10 that I could copy and paste into there?

this is what I have now:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

The lines with the # in front of them, are comments and can be completely ignored in your troubleshooting.  So, what you actually have for update-grub to process is this:
```
GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

As a slight disclaimer, I am not running Ubuntu 12.10 as you requested, I am running Ubuntu 12.04.  However, this file has not changed at all since then from what I can see.

The relevant lines of my GRUB file in /etc/default/grub look like this:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Did you choose to add those quotation marks? (around lines like the GRUB_DISTRIBUTOR line)  I wonder if they might be causing problems.

---

### Post by Kirk Schnable on 2012-12-13
> **Dopaque said:**
> just wanted to include the error message when I try to update the above

```
[sudo] password for jam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.6.9-030609-generic
Found initrd image: /boot/initrd.img-3.6.9-030609-generic
Found linux image: /boot/vmlinuz-3.5.1-030501-generic
Found initrd image: /boot/initrd.img-3.5.1-030501-generic
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda6
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 291
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done

```

The syntax error is in the file they're generating, not necessarily in /etc/default/grub but I suppose /etc/default/grub might be the cause of the error on that file.

It might help to see the contents of /boot/grub/grub.cfg.new.. perhaps you'd like to attach that?

---

### Post by Dopaque on 2012-12-13
all right... here it is. Line 291 seems to consist entirely of    }

so idk

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
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
else
  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
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
  set timeout=-1
else
  set timeout=0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-44d88304-38d0-4fa1-8ec5-319858479fe5' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
	else
	  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
	fi
	linux	/boot/vmlinuz-3.6.9-030609-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.6.9-030609-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	menuentry 'Ubuntu, with Linux 3.6.9-030609-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.6.9-030609-generic-advanced-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.6.9-030609-generic ...'
		linux	/boot/vmlinuz-3.6.9-030609-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.6.9-030609-generic
	}
	menuentry 'Ubuntu, with Linux 3.6.9-030609-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.6.9-030609-generic-recovery-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.6.9-030609-generic ...'
		linux	/boot/vmlinuz-3.6.9-030609-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.6.9-030609-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.1-030501-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.1-030501-generic-advanced-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.5.1-030501-generic ...'
		linux	/boot/vmlinuz-3.5.1-030501-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.1-030501-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.1-030501-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.1-030501-generic-recovery-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.5.1-030501-generic ...'
		linux	/boot/vmlinuz-3.5.1-030501-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.1-030501-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.5.0-19-generic ...'
		linux	/boot/vmlinuz-3.5.0-19-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-44d88304-38d0-4fa1-8ec5-319858479fe5' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
		else
		  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
		fi
		echo	'Loading Linux 3.5.0-19-generic ...'
		linux	/boot/vmlinuz-3.5.0-19-generic root=UUID=44d88304-38d0-4fa1-8ec5-319858479fe5 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-19-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
	else
	  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
	fi
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  44d88304-38d0-4fa1-8ec5-319858479fe5
	else
	  search --no-floppy --fs-uuid --set=root 44d88304-38d0-4fa1-8ec5-319858479fe5
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Recovery Environment (loader) (on /dev/sda6)' --class windows --class os $menuentry_id_option 'osprober-chain-7AE6-7588' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  7AE6-7588
	else
	  search --no-floppy --fs-uuid --set=root 7AE6-7588
	fi
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "new"{
	}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

### BEGIN /etc/grub.d/50_uefi-firmware ###
### END /etc/grub.d/50_uefi-firmware ###
```

---

### Post by Dopaque on 2012-12-13
Solution found: reinstall grub 2.

How-to included in this thread: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

using the commands in part 12 !!

thanks for your time guys

---

