---
title: "software update error"
date: 2013-07-12
forum: General Help
---

### Post by d73t on 2013-07-12
After an update a few days ago, i have been getting an error as one of the updates couldnt configure and is "half installed".  Any time i try to install or remove anything i get this:     "Running depmod. update-initramfs: deferring update (hook will be called later) Examining /etc/kernel/postinst.d. run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic update-initramfs: Generating /boot/initrd.img-3.8.0-26-generic run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic P: Checking for EXTLINUX directory... found. P: Writing config for /boot/vmlinuz-3.8.0-26-generic... P: Writing config for /boot/vmlinuz-3.8.0-25-generic... P: Writing config for /boot/vmlinuz-3.8.0-23-generic... P: Writing config for /boot/vmlinuz-3.8.0-21-generic... P: Writing config for /boot/vmlinuz-3.7.0-7-generic... P: Installing debian theme... done. run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic /usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-26-generic.postinst line 1010. dpkg: error processing linux-image-3.8.0-26-generic (--configure):  subprocess installed post-installation script returned error exit status 2 dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-26-generic:  linux-image-extra-3.8.0-26-generic depends on linux-image-3.8.0-26-generic; however:   Package linux-image-3.8.0-26-generic is not configured yet.  dpkg: error processing linux-image-extra-3.8.0-26-generic (--configure):  dependency problems - leaving unconfigured No apport report written because the error message indicates its a followup error from a previous failure.                                                                                                           Errors were encountered while processing:  linux-image-3.8.0-26-generic  linux-image-extra-3.8.0-26-generic E: Sub-process /usr/bin/dpkg returned an error code (1)"  not sure what i sould do here...thanks in advance

---

### Post by Cheesehead on 2013-07-13
> **d73t said:**
> [...]P: Installing debian theme... done. run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic [COLOR="#FF0000"]/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected [/COLOR]run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2 Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-26-generic.postinst line 1010. dpkg: error processing linux-image-3.8.0-26-generic (--configure):  [...]

Next time, please use CODE tags. It makes thing much more readable.

Look at line 26 of the highlighted file (/usr/sbin/grub-mkconfig).
If you see the syntax error (unexpected newline), and understand how to fix it, then do so.
If you don't understand, then post the first 50 lines of that file here...in CODE tags, please.

---

### Post by d73t on 2013-07-14
Sorry about that, Im kind of new to the forum. I looked at the file and i cant tell whats wrong with it, i kind of understand the issue, but i dont see it.  Here is the first 50 lines of the file    ```
  #! /bin/sh set -e  # Generate grub.cfg by inspecting /boot contents. # Copyright (C) 2006,2007,2008,2009,2010 Free Software Foundation, Inc. # # GRUB is free software: you can redistribute it and/or modify # it under the terms of the GNU General Public License as published by # the Free Software Foundation, either version 3 of the License, or # (at your option) any later version. # # GRUB is distributed in the hope that it will be useful, # but WITHOUT ANY WARRANTY; without even the implied warranty of # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the # GNU General Public License for more details. # # You should have received a copy of the GNU General Public License # along with GRUB.  If not, see .  transform="s,x,x," prefix="/usr" exec_prefix="${prefix}" datarootdir="${prefix}/share"  prefix="/usr" exec_prefix="${prefix}" sbindir="${exec_prefix}/sbin" bindir="${exec_prefix}/bin" sysconfdir="/etc" PACKAGE_NAME=GRUB PACKAGE_VERSION=2.00-13ubuntu3 host_os=linux-gnu datadir="${datarootdir}" if [ "x$pkgdatadir" = x ]; then     pkgdatadir="${datadir}/grub" fi grub_cfg="" grub_mkconfig_dir="${sysconfdir}"/grub.d  self=`basename $0`  grub_probe="${sbindir}/`echo grub-probe | sed "${transform}"`" grub_editenv="${bindir}/`echo grub-editenv | sed "${transform}"`" grub_script_check="${bindir}/`echo grub-script-check | sed "${transform}"`"  export TEXTDOMAIN=grub export TEXTDOMAINDIR="${datarootdir}/locale"  . "${pkgdatadir}/grub-mkconfig_lib"  # Usage: usage # Print the usage. usage () {     gettext_printf "Usage: %s [OPTION]\n" "$self"     gettext "Generate a grub config file"; echo     echo     print_option_help "-o, --output=$(gettext FILE)" "$(gettext "output generated config to FILE [default=stdout]")"     print_option_help "-h, --help" "$(gettext "print this message and exit")"     print_option_help "-v, --version" "$(gettext "print the version information and exit")"     echo     gettext "Report bugs to ."; echo }  argument () {   opt=$1   shift    if test $# -eq 0; then       gettext_printf "%s: option requires an argument -- \`%s'\n" "$0" "$opt" 1>&2       exit 1   fi   echo $1 }  # Check the arguments. while test $# -gt 0 do     option=$1     shift      case "$option" in     -h | --help) 	usage 	exit 0 ;;     -v | --version) 	echo "$self (${PACKAGE_NAME}) ${PACKAGE_VERSION}" 	exit 0 ;;     -o | --output) 	grub_cfg=`argument $option "$@"`; shift;;     --output=*) 	grub_cfg=`echo "$option" | sed 's/--output=//'` 	;;     -*) 	gettext_printf "Unrecognized option \`%s'\n" "$option" 1>&2 	usage 	exit 1 	;;     # Explicitly ignore non-option arguments, for compatibility.     esac done  if fgrep -qs '${GRUB_PREFIX}/video.lst' "${grub_mkconfig_dir}/00_header"; then   echo "GRUB >= 2.00 has been unpacked but not yet configured." >&2   echo "grub-mkconfig will not work until the upgrade is complete." >&2   echo "It should run later as part of configuring the new GRUB packages." >&2   exit 0 fi  if [ "x$EUID" = "x" ] ; then   EUID=`id -u` fi  if [ "$EUID" != 0 ] ; then   root=f   case "`uname 2>/dev/null`" in     CYGWIN*)       # Cygwin: Assume root if member of admin group       for g in `id -G 2>/dev/null` ; do 	case $g in 	  0|544) root=t ;; 	esac       done ;;   esac   if [ $root != t ] ; then     gettext_printf "%s: You must run this as root\n" "$self" >&2     exit 1   fi fi  set $grub_probe dummy if test -f "$1"; then     : else     gettext_print "%s: Not found.\n" "$1" 1>&2     exit 1 fi  # Device containing our userland.  Typically used for root= parameter. GRUB_DEVICE="`${grub_probe} --target=device /`" GRUB_DEVICE_UUID="`${grub_probe} --device ${GRUB_DEVICE} --target=fs_uuid 2> /dev/null`" || true  # Device containing our /boot partition.  Usually the same as GRUB_DEVICE. GRUB_DEVICE_BOOT="`${grub_probe} --target=device /boot`" GRUB_DEVICE_BOOT_UUID="`${grub_probe} --device ${GRUB_DEVICE_BOOT} --target=fs_uuid 2> /dev/null`" || true  # Filesystem for the device containing our userland.  Used for stuff like # choosing Hurd filesystem module. GRUB_FS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2> /dev/null || echo unknown`"  if test -f ${sysconfdir}/default/grub ; then   . ${sysconfdir}/default/grub fi for x in ${sysconfdir}/default/grub.d/*.cfg ; do   if [ -e "${x}" ]; then     . "${x}"   fi done 
 
```

---

### Post by Cheesehead on 2013-07-14
Please don't print everything on one line. Impossible to tell which line is which.

---

### Post by d73t on 2013-07-14
line 26 of the file /usr/sbin/grub-mkconfig is
```

exec_prefix="${prefix}"

```

also line 26 of /etc/default/grub is blank, not sure if that means anything. Im sorry i cant be of more help, im having trouble getting the CODE tags to print on more than one line.

---

