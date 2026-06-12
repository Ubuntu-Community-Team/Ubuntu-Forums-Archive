---
title: "Changing the resolution of my tty, doesn't fit on the screen now."
date: 2014-02-06
forum: General Help
---

### Post by david-sy6 on 2014-02-06
The previous resolution of my tty (ctrl-alt-f1 etc.) was 640x480. I wanted to change this because the ```
hwinfo --framebuffer
``` said I could have up to 1920x1080.
I changed the line in /etc/default/grub from:
```
GRUB_GFXMODE=640x480
```
to
```
GRUB_GFXMODE=1920x1080
```
and did
```
sudo update-grub
```

I rebooted the computer, and it has made the tty look like this:

[IMG]https://pbs.twimg.com/media/Bf0vfLaIAAAQxdT.jpg:large[/IMG]

Now I have tried changing all sorts of things in the grub file and also in /boot/grub/menu.lst and /etc/grub.d/00_header but nothing is making a single difference to the tty after I update-grub.
Even restoring the file back to what it was originally makes no difference. I'm stuck with this 1920x1080, off the screen, resolution.

Does anybody have any idea why nothing is making a difference anymore? How do I either get back to 640x480, or fix the 1920x1080?

Here is a copy of /etc/default/grub currently:
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash vga=0x037d"
GRUB_CMDLINE_LINUX="vga=0x037d"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=keep


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Here is a copy of /boot/grub/menu.lst currently:
```
# menu.lst - See: grub(8), info grub, update-grub(8)#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0


## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3


## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


# Pretty colours
#color cyan/blue white/blue


## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret


#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#


#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST


### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


## DO NOT UNCOMMENT THEM, Just edit them to your needs


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro


## default grub root device
## e.g. groot=(hd0,0)
# groot=cc422d67-6ee5-49a7-93cf-e6315a38ab1b


## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true


## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false


## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash


## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false


## Xen hypervisor options to use with the default Xen boot option
# xenhopt=


## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0


## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single


## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all


## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect


## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true


## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false


## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false


## ## End Default Options ##


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-35-generic
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-35-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro quiet splash 
initrd        /boot/initrd.img-3.8.0-35-generic


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-35-generic (recovery mode)
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-35-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro  single
initrd        /boot/initrd.img-3.8.0-35-generic


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-34-generic
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-34-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro quiet splash 
initrd        /boot/initrd.img-3.8.0-34-generic


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-34-generic (recovery mode)
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-34-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro  single
initrd        /boot/initrd.img-3.8.0-34-generic


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-29-generic
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-29-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro quiet splash 
initrd        /boot/initrd.img-3.8.0-29-generic


title        Ubuntu 12.04.4 LTS, kernel 3.8.0-29-generic (recovery mode)
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.8.0-29-generic root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro  single
initrd        /boot/initrd.img-3.8.0-29-generic


title        Ubuntu 12.04.4 LTS, kernel 3.2.0-58-generic-pae
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.2.0-58-generic-pae root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro quiet splash 
initrd        /boot/initrd.img-3.2.0-58-generic-pae


title        Ubuntu 12.04.4 LTS, kernel 3.2.0-58-generic-pae (recovery mode)
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.2.0-58-generic-pae root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro  single
initrd        /boot/initrd.img-3.2.0-58-generic-pae


title        Ubuntu 12.04.4 LTS, kernel 3.2.0-57-generic-pae
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.2.0-57-generic-pae root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro quiet splash 
initrd        /boot/initrd.img-3.2.0-57-generic-pae


title        Ubuntu 12.04.4 LTS, kernel 3.2.0-57-generic-pae (recovery mode)
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/vmlinuz-3.2.0-57-generic-pae root=UUID=cc422d67-6ee5-49a7-93cf-e6315a38ab1b ro  single
initrd        /boot/initrd.img-3.2.0-57-generic-pae


title        Chainload into GRUB 2
root        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/grub/core.img


title        Ubuntu 12.04.4 LTS, memtest86+
uuid        cc422d67-6ee5-49a7-93cf-e6315a38ab1b
kernel        /boot/memtest86+.bin


### END DEBIAN AUTOMAGIC KERNELS LIST
```

Here is a copy of /etc/grub.d/00_header currently:
```
#! /bin/shset -e


# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.


transform="s,x,x,"


prefix="/usr"
exec_prefix="${prefix}"
datarootdir="${prefix}/share"
locale_dir=`echo ${GRUB_PREFIX}/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d . -f 1`


. "${datarootdir}/grub/grub-mkconfig_lib"


# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done


if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=1920x1080 ; fi


if [ "x${GRUB_DEFAULT_BUTTON}" = "x" ] ; then GRUB_DEFAULT_BUTTON="$GRUB_DEFAULT" ; fi
if [ "x${GRUB_DEFAULT_BUTTON}" = "xsaved" ] ; then GRUB_DEFAULT_BUTTON='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT_BUTTON}" = "x" ] ; then GRUB_TIMEOUT_BUTTON="$GRUB_TIMEOUT" ; fi


cat << EOF
if [ -s \$prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
EOF
if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
   set default="${GRUB_DEFAULT_BUTTON}"
else
   set default="${GRUB_DEFAULT}"
fi
EOF
else
    cat <<EOF
set default="${GRUB_DEFAULT}"
EOF
fi
cat <<EOF
if [ "\${prev_saved_entry}" ]; then
  set saved_entry="\${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "\${boot_once}" ]; then
    saved_entry="\${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "\${have_grubenv}" ]; then if [ -z "\${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
EOF
if [ -n "${GRUB_VIDEO_BACKEND}" ]; then
    cat <<EOF
  insmod ${GRUB_VIDEO_BACKEND}
EOF
else
    # Insert all available backends; GRUB will use the most appropriate.
    have_video=0;
    for backend in $(cat "${GRUB_PREFIX}/video.lst"); do
    have_video=1;
    cat <<EOF
  insmod ${backend}
EOF
    done
    if [ x$have_video = x0 ]; then
    echo "true"
    fi
fi
cat <<EOF
}


EOF


serial=0;
gfxterm=0;
for x in ${GRUB_TERMINAL_INPUT} ${GRUB_TERMINAL_OUTPUT}; do
    if [ xserial = "x$x" ]; then
    serial=1;
    fi
    if [ xgfxterm = "x$x" ]; then
    gfxterm=1;
    fi
done


if [ "x$serial" = x1 ]; then
    if ! test -e "${GRUB_PREFIX}/serial.mod" ; then
    echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi


    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
    grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
    GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
fi


if [ "x$gfxterm" = x1 ]; then
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device "${GRUB_FONT_PATH}"`


    cat << EOF
if loadfont `make_system_path_relative_to_its_root "${GRUB_FONT_PATH}"` ; then
  set gfxmode=${GRUB_GFXMODE}
  set gfxpayload=keep
  load_video
  insmod gfxterm
EOF


# Gettext variables and module
if [ "x${LANG}" != "xC" ] && [ -d "${locale_dir}" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir}) | sed -e "s/^/  /"
  cat << EOF
  set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
  set lang=${grub_lang}
  insmod gettext
EOF
fi


cat <<EOF
fi
EOF
fi


case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_input ${GRUB_TERMINAL_INPUT}
EOF
  ;;
esac


case x${GRUB_TERMINAL_OUTPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
terminal_output ${GRUB_TERMINAL_OUTPUT}
EOF
  ;;
esac


if [ "x$gfxterm" = x1 ]; then
    if [ "x$GRUB_THEME" != x ] && [ -f "$GRUB_THEME" ] \
    && is_path_readable_by_grub "$GRUB_THEME"; then
    echo "Found theme: $GRUB_THEME" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_THEME"`
    cat << EOF
insmod gfxmenu
EOF
    themedir="`dirname "$GRUB_THEME"`"
    for x in "$themedir"/*.pf2 "$themedir"/f/*.pf2; do
        if [ -f "$x" ]; then
        cat << EOF
loadfont (\$root)`make_system_path_relative_to_its_root $x`
EOF
        fi
    done
    if [ x"`echo "$themedir"/*.jpg`" != x"$themedir/*.jpg" ] || [ x"`echo "$themedir"/*.jpeg`" != x"$themedir/*.jpeg" ]; then
        cat << EOF
insmod jpeg
EOF
    fi
    if [ x"`echo "$themedir"/*.png`" != x"$themedir/*.png" ]; then
        cat << EOF
insmod png
EOF
    fi
    if [ x"`echo "$themedir"/*.tga`" != x"$themedir/*.tga" ]; then
        cat << EOF
insmod tga
EOF
    fi
        
    cat << EOF
set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
EOF
    elif [ "x$GRUB_BACKGROUND" != x ] && [ -f "$GRUB_BACKGROUND" ] \
        && is_path_readable_by_grub "$GRUB_BACKGROUND"; then
    echo "Found background: $GRUB_BACKGROUND" >&2
    case "$GRUB_BACKGROUND" in 
        *.png)         reader=png ;;
        *.tga)         reader=tga ;;
        *.jpg|*.jpeg)  reader=jpeg ;;
        *)             echo "Unsupported image format" >&2; exit 1 ;;
    esac
    prepare_grub_to_access_device `${grub_probe} --target=device "$GRUB_BACKGROUND"`
    cat << EOF
insmod $reader
background_image -m stretch `make_system_path_relative_to_its_root "$GRUB_BACKGROUND"`
EOF
    fi
fi


make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ] ; then
  set timeout=${GRUB_RECORDFAIL_TIMEOUT:--1}
else
EOF
    if [ "x${1}${3}" != "x" ] ; then
    if [ "x${3}" != "x" ] ; then
        timeout="${2}"
        style="${3}"
    else
        # Handle the deprecated GRUB_HIDDEN_TIMEOUT scheme.
        timeout="${1}"
        if [ "x${2}" != "x0" ] ; then
        grub_warn "$(gettext "Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.")"
        fi
        if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
        style="hidden"
        else
        style="countdown"
        fi
    fi
    if [ "x${style}" = "xcountdown" ] ; then
        verbose=" --verbose"
    else
        verbose=
    fi
    cat << EOF
  if [ x\$feature_timeout_style = xy ] ; then
    set timeout_style=${style}
    set timeout=${timeout}
EOF
    if [ "x${style}" != "xmenu" ] ; then
        cat << EOF
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep${verbose} --interruptible ${timeout} ; then
    set timeout=0
EOF
    fi
    cat << EOF
  fi
EOF
    else
    cat << EOF
  set timeout=${2}
EOF
    fi
    cat << EOF
fi
EOF
}


if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
    cat <<EOF
if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
EOF
make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_STYLE_BUTTON}"
echo else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}" "${GRUB_TIMEOUT_STYLE}"
echo fi
else
make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}" "${GRUB_TIMEOUT_STYLE}"
fi


if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ] && [ "x$GRUB_BUTTON_CMOS_CLEAN" = "xyes" ]; then
    cat <<EOF
cmosclean $GRUB_BUTTON_CMOS_ADDRESS
EOF
fi


# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  echo "play ${GRUB_INIT_TUNE}"
fi


if [ "x${GRUB_BADRAM}" != "x" ] ; then
  echo "badram ${GRUB_BADRAM}"
fi
```

I'm running an NVIDIA driver 331.20, and Ubuntu 12.04


Thanks! (sorry for such a long post).

---

### Post by mike233 on 2014-08-22
I have exactly this problem.  Did you find a solution?

---

### Post by Bashing-om on 2014-08-22
david-sy6; Sheeshh,

OK, I am curious. I have not seen a "/boot/grub/menu.lst" file in years !

show us what we are in fact working with:
```

ls -al /etc/grub.d
ls -al /
ls -al /boot
ls -la /boot/grub/grub.cfg

``` and we start scratching out heads and try and 

[INDENT][INDENT]finger this one out
[/INDENT][/INDENT]

---

