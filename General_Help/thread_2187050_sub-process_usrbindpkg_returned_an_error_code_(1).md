---
title: "sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-11-10
forum: General Help
---

### Post by chinmay3 on 2013-11-10
Its all started after i tried to update. Now i can't install or remove any package from my system. I have searched on web for solution but nothing useful found. Please help me. Here my output of "sudo apt-get install -f".
```
chinmay@HP-LinuxBox:~$ sudo apt-get install -f
[sudo] password for chinmay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.8.0-33-generic (3.8.0-33.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
/usr/sbin/grub-mkconfig: 27: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-33-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-33-generic:
 linux-image-extra-3.8.0-33-generic depends on linux-image-3.8.0-33-generic; however:
  Package linux-image-3.8.0-33-generic is not configured yet.

dpkg: error processing linux-image-extra-3.8.0-33-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.8.0-33-generic; however:
  Package linux-image-3.8.0-33-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.8.0-33-generic; however:
  Package linux-image-extra-3.8.0-33-generic is not configured yet.

dpkg: error processing linux-image-generic (--confNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                              No apport report written because the error message indicates its a followup error from a previous failure.
                                                                    igure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.33.51); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.8.0-33-generic
 linux-image-extra-3.8.0-33-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
chinmay@HP-LinuxBox:~$ 
```

Thanks in advance.

---

### Post by hamishmb on 2013-11-10
You could try:
sudo dpkg --configure-a

---

### Post by ian-weisser on 2013-11-10
> **chinmay3 said:**
> 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
/usr/sbin/grub-mkconfig: 27: [COLOR=#ff0000]/etc/default/grub: Syntax error: newline unexpected[/COLOR]
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
.

Please post output inside [CODE] tags. It makes the output readable.

Please post the contents of your /etc/default/grub file here (inside [CODE] tags, please).
Please post the contents of your /usr/sbin/grub-mkconfig file here (inside [CODE] tags, please).

---

### Post by chinmay3 on 2013-11-10
sorry for not enclosing output into code , I was unaware of how it is done. Here is output of /etc/default/grub```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1366*768-24<<,mtrr=3,scroll=ywrap"
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1366*768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

& that of usr/sbin/grub-mkconfig is here.....
```
#! /bin/sh
set -e

# Generate grub.cfg by inspecting /boot contents.
# Copyright (C) 2006,2007,2008,2009,2010 Free Software Foundation, Inc.
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

prefix="/usr"
exec_prefix="${prefix}"
sbindir="${exec_prefix}/sbin"
bindir="${exec_prefix}/bin"
sysconfdir="/etc"
PACKAGE_NAME=GRUB
PACKAGE_VERSION=2.00-13ubuntu3
host_os=linux-gnu
datadir="${datarootdir}"
if [ "x$pkgdatadir" = x ]; then
    pkgdatadir="${datadir}/grub"
fi
grub_cfg=""
grub_mkconfig_dir="${sysconfdir}"/grub.d

self=`basename $0`

grub_probe="${sbindir}/`echo grub-probe | sed "${transform}"`"
grub_editenv="${bindir}/`echo grub-editenv | sed "${transform}"`"
grub_script_check="${bindir}/`echo grub-script-check | sed "${transform}"`"

export TEXTDOMAIN=grub
export TEXTDOMAINDIR="${datarootdir}/locale"

. "${pkgdatadir}/grub-mkconfig_lib"

# Usage: usage
# Print the usage.
usage () {
    gettext_printf "Usage: %s [OPTION]\n" "$self"
    gettext "Generate a grub config file"; echo
    echo
    print_option_help "-o, --output=$(gettext FILE)" "$(gettext "output generated config to FILE [default=stdout]")"
    print_option_help "-h, --help" "$(gettext "print this message and exit")"
    print_option_help "-v, --version" "$(gettext "print the version information and exit")"
    echo
    gettext "Report bugs to <bug-grub@gnu.org>."; echo
}

argument () {
  opt=$1
  shift

  if test $# -eq 0; then
      gettext_printf "%s: option requires an argument -- \`%s'\n" "$0" "$opt" 1>&2
      exit 1
  fi
  echo $1
}

# Check the arguments.
while test $# -gt 0
do
    option=$1
    shift

    case "$option" in
    -h | --help)
    usage
    exit 0 ;;
    -v | --version)
    echo "$self (${PACKAGE_NAME}) ${PACKAGE_VERSION}"
    exit 0 ;;
    -o | --output)
    grub_cfg=`argument $option "$@"`; shift;;
    --output=*)
    grub_cfg=`echo "$option" | sed 's/--output=//'`
    ;;
    -*)
    gettext_printf "Unrecognized option \`%s'\n" "$option" 1>&2
    usage
    exit 1
    ;;
    # Explicitly ignore non-option arguments, for compatibility.
    esac
done

if fgrep -qs '${GRUB_PREFIX}/video.lst' "${grub_mkconfig_dir}/00_header"; then
  echo "GRUB >= 2.00 has been unpacked but not yet configured." >&2
  echo "grub-mkconfig will not work until the upgrade is complete." >&2
  echo "It should run later as part of configuring the new GRUB packages." >&2
  exit 0
fi

if [ "x$EUID" = "x" ] ; then
  EUID=`id -u`
fi

if [ "$EUID" != 0 ] ; then
  root=f
  case "`uname 2>/dev/null`" in
    CYGWIN*)
      # Cygwin: Assume root if member of admin group
      for g in `id -G 2>/dev/null` ; do
    case $g in
      0|544) root=t ;;
    esac
      done ;;
  esac
  if [ $root != t ] ; then
    gettext_printf "%s: You must run this as root\n" "$self" >&2
    exit 1
  fi
fi

set $grub_probe dummy
if test -f "$1"; then
    :
else
    gettext_print "%s: Not found.\n" "$1" 1>&2
    exit 1
fi

# Device containing our userland.  Typically used for root= parameter.
GRUB_DEVICE="`${grub_probe} --target=device /`"
GRUB_DEVICE_UUID="`${grub_probe} --device ${GRUB_DEVICE} --target=fs_uuid 2> /dev/null`" || true

# Device containing our /boot partition.  Usually the same as GRUB_DEVICE.
GRUB_DEVICE_BOOT="`${grub_probe} --target=device /boot`"
GRUB_DEVICE_BOOT_UUID="`${grub_probe} --device ${GRUB_DEVICE_BOOT} --target=fs_uuid 2> /dev/null`" || true

# Filesystem for the device containing our userland.  Used for stuff like
# choosing Hurd filesystem module.
GRUB_FS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2> /dev/null || echo unknown`"

if test -f ${sysconfdir}/default/grub ; then
  . ${sysconfdir}/default/grub
fi
for x in ${sysconfdir}/default/grub.d/*.cfg ; do
  if [ -e "${x}" ]; then
    . "${x}"
  fi
done

# XXX: should this be deprecated at some point?
if [ "x${GRUB_TERMINAL}" != "x" ] ; then
  GRUB_TERMINAL_INPUT="${GRUB_TERMINAL}"
  GRUB_TERMINAL_OUTPUT="${GRUB_TERMINAL}"
fi

termoutdefault=0
if [ "x${GRUB_TERMINAL_OUTPUT}" = "x" ]; then
    GRUB_TERMINAL_OUTPUT=gfxterm;
    termoutdefault=1;
fi

for x in ${GRUB_TERMINAL_OUTPUT}; do
    case "x${x}" in
    xgfxterm) ;;
    xconsole | xserial | xofconsole)
            # make sure all our children behave in conformance with ascii..
        export LANG=C;;
    *) echo "Invalid output terminal \"${GRUB_TERMINAL_OUTPUT}\"" >&2 ; exit 1 ;;
    esac
done

GRUB_ACTUAL_DEFAULT="$GRUB_DEFAULT"

if [ "x${GRUB_ACTUAL_DEFAULT}" = "xsaved" ] ; then GRUB_ACTUAL_DEFAULT="`"${grub_editenv}" - list | sed -n '/^saved_entry=/ s,^saved_entry=,,p'`" ; fi


# These are defined in this script, export them here so that user can
# override them.
export GRUB_DEVICE \
  GRUB_DEVICE_UUID \
  GRUB_DEVICE_BOOT \
  GRUB_DEVICE_BOOT_UUID \
  GRUB_FS \
  GRUB_FONT \
  GRUB_PRELOAD_MODULES \
  GRUB_ACTUAL_DEFAULT

# These are optional, user-defined variables.
export GRUB_DEFAULT \
  GRUB_HIDDEN_TIMEOUT \
  GRUB_HIDDEN_TIMEOUT_QUIET \
  GRUB_TIMEOUT \
  GRUB_DEFAULT_BUTTON \
  GRUB_HIDDEN_TIMEOUT_BUTTON \
  GRUB_TIMEOUT_BUTTON \
  GRUB_BUTTON_CMOS_ADDRESS \
  GRUB_BUTTON_CMOS_CLEAN \
  GRUB_DISTRIBUTOR \
  GRUB_CMDLINE_LINUX \
  GRUB_CMDLINE_LINUX_DEFAULT \
  GRUB_CMDLINE_XEN \
  GRUB_CMDLINE_XEN_DEFAULT \
  GRUB_CMDLINE_LINUX_XEN_REPLACE \
  GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT \
  GRUB_CMDLINE_NETBSD \
  GRUB_CMDLINE_NETBSD_DEFAULT \
  GRUB_CMDLINE_GNUMACH \
  GRUB_TERMINAL_INPUT \
  GRUB_TERMINAL_OUTPUT \
  GRUB_SERIAL_COMMAND \
  GRUB_DISABLE_LINUX_UUID \
  GRUB_DISABLE_RECOVERY \
  GRUB_VIDEO_BACKEND \
  GRUB_GFXMODE \
  GRUB_BACKGROUND \
  GRUB_THEME \
  GRUB_GFXPAYLOAD_LINUX \
  GRUB_DISABLE_OS_PROBER \
  GRUB_INIT_TUNE \
  GRUB_SAVEDEFAULT \
  GRUB_ENABLE_CRYPTODISK \
  GRUB_BADRAM \
  GRUB_RECORDFAIL_TIMEOUT

if test "x${grub_cfg}" != "x"; then
  rm -f "${grub_cfg}.new"
  oldumask=$(umask); umask 077
  exec > "${grub_cfg}.new"
  umask $oldumask
fi
gettext "Generating grub.cfg ..." >&2
echo >&2

cat << EOF
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by $self using templates
# from ${grub_mkconfig_dir} and settings from ${sysconfdir}/default/grub
#
EOF

for i in ${grub_mkconfig_dir}/* ; do
  case "$i" in
    # emacsen backup files. FIXME: support other editors
    *~) ;;
    # emacsen autosave files. FIXME: support other editors
    \#*\#) ;;
    *)
      if grub_file_is_not_garbage "$i" && test -x "$i" ; then
        echo
        echo "### BEGIN $i ###"
        "$i"
        echo "### END $i ###"
      fi
    ;;
  esac
done

if [ "x${grub_cfg}" != "x" ] && ! grep "^password " ${grub_cfg}.new >/dev/null; then
  chmod 444 ${grub_cfg}.new || true
fi

if test "x${grub_cfg}" != "x" ; then
  if ! ${grub_script_check} ${grub_cfg}.new; then
    # TRANSLATORS: %s is replaced by filename
    gettext_printf "Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
%s file attached." "${grub_cfg}.new" >&2
  else
    # none of the children aborted with error, install the new grub.cfg
    mv -f ${grub_cfg}.new ${grub_cfg}
  fi
fi

gettext "done" >&2
echo >&2
```

---

### Post by ian-weisser on 2013-11-10
> **chinmay3 said:**
> Here is output of /etc/default/grub```

[...]
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR=#ff0000]GRUB_GFXMODE=>>1366*768-24<<[/COLOR]

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
[...]

```

Did you change that line?
The syntax doesn't look right to me, and it's in the right place to cause your error.
Normally the line would be commented out (for autodetection), or more like: **GRUB_GFXMODE=1366x768** or whatever best resolution your video card supports.

---

### Post by chinmay3 on 2013-11-10
Yes. I have changed that. In attempt to change some of my boot parameters using 'super boot manager' I entered those values when it prompted me to do so. I have multiple os installed & each one of them put multiple entries in my boot sequence & my boot menu became mess so i tried to remove those entries using options in SBM.

---

### Post by chinmay3 on 2013-11-10
I edited /etc/default/grub. I commented the line as you said it. then I ran command 'sudo dpkg --reconfigure -a' it give me some error at first e.g.```
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 132
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done
Setting up linux-image-generic (3.8.0.33.51) ...
Setting up linux-generic (3.8.0.33.51) ...
chinmay@HP-LinuxBox:~$ 

```
I checked /etc/default/grub for line 132 but there are no more than 36 lines. But at end everything looks like going right. It doesn't giving previous error code. Let me check if i can install other packages. I will post result soon. 
Thank u very much for your help.

---

### Post by ian-weisser on 2013-11-10
> **chinmay3 said:**
> 
Syntax error at line 132
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done

The error message means line 132 of /boot/grub/grub.cfg
The grub.cfg file is automatically generated from several sources, including /etc/default/grub. The error simply means that the syntax error is somewhere in one of those several sources. Looking at grub.cfg will give you a clue which source.

---

### Post by chinmay3 on 2013-11-11
I edited /boot/grub/grub.cfg , at first i didn't understand what was wrong on line 132 but after reading other code i guessed that , hypen(-) was missing in root=UUID=f0f0432_6-e_cb8-4b19-81a6-1dc02c151ce7. so i added it. now there is no error. 
But i have installed linux kernel image 3.8.0-33 two days ago and still command "uname -a" gives me output```
Linux HP-LinuxBox 3.8.0-32-generic #47-Ubuntu SMP Tue Oct 1 22:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```
even in synaptic package manager it shows linux-image 3.8.0-33 installed. what am i missing?

---

### Post by ian-weisser on 2013-11-11
Have you rebooted since installing the new kernel?
I reboot about once a month, sometimes less. More than once I jumped two kernel versions upon reboot.

---

### Post by chinmay3 on 2013-11-11
yes i rebooted so many times after that.

---

### Post by ian-weisser on 2013-11-11
Well, your system seems to be running, so any further investigation is not critical.

See the /boot/grub/grub.cfg file - is the latest kernel in there?

If so, hit ESC at boot to get into the grub menu, and select the kernel.

If not, you have two options.
1) You can manually run the **update-grub** command to add the new kernel to grub.
2) You can wait for the next kernel update, which will run **update-grub** for you.

Since I'm not familiar with your grub customizations, and since we already know that you have at least one unresolved syntax error among those customizations, there is a (low but non-zero) risk that updating grub will result in a hard-to-boot situation.

---

### Post by chinmay3 on 2013-11-11
i reinstalled linux-image-3.8.0-33 its shows in uname -a output so i am going to mark thread solved.
I appreciate your help. **Thank You very Much.**:P

---

