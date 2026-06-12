---
title: "Software Index is broken:"
date: 2018-12-16
forum: General Help
---

### Post by Gizatderebe on 2018-12-16
Hey,
Was trying to install the latest kernel like 4.18.8 or 4.19.8 on ubuntu 18.04.1 LTS. However, it didn't work out for me and tried to remove them. Then tried to update the software, but ends with error saying:

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

on Terminal: sudo apt-get install -f
gives:
```

[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-bin aria2 libapache2-mod-dnssd libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libcaja-extension1 libopenobex2
  libusb-0.1-4 mate-user-share-common obex-data-server python-dbus python-gi
  python-gobject
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-unsigned-4.18.8-041808-generic
  linux-image-unsigned-4.19.8-041908-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 17,2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 260778 files and directories currently installed.)
Removing linux-image-unsigned-4.18.8-041808-generic (4.18.8-041808.201809150431) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.18.8-041808-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-mkconfig: 4: /etc/default/grub: # If you change this file, run update-grub afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n Simple: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-unsigned-4.18.8-041808-generic (--remove):
 installed linux-image-unsigned-4.18.8-041808-generic package post-removal script subprocess returned error exit status 1
Removing linux-image-unsigned-4.19.8-041908-generic (4.19.8-041908.201812080831) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.19.8-041908-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-mkconfig: 4: /etc/default/grub: # If you change this file, run update-grub afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n Simple: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-unsigned-4.19.8-041908-generic (--remove):
 installed linux-image-unsigned-4.19.8-041908-generic package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-unsigned-4.18.8-041808-generic
 linux-image-unsigned-4.19.8-041908-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Any idea please? Thanks!

---

### Post by Frogs Hair on 2018-12-16
Support request moved to *General Help*.

---

### Post by Impavidus on 2018-12-17
There seems to be some error in a post-removal script that's called automatically when removing any kernel. You'll have to fix that script before you can remove any kernel and fix the package manager. The error message is a bit strange, but it could be some sort of syntax error.

Let's have a look at a few files:```
cat -n /etc/kernel/postrm.d/zz-update-grub
cat -n /usr/sbin/grub-mkconfig
cat -n /etc/default/grub
```Maybe we can find the problem.

Did you ever modify one of these files, or use a tool to modify them (grub-customizer, for example)? In that case, do you have backups of the originals?

---

### Post by Gizatderebe on 2018-12-17
Hey Impavidus,

I have never tried to modify those files. I installed ukuu, using [https://linuxhint.com/upgrade-kernel-ubuntu-1804/](https://linuxhint.com/upgrade-kernel-ubuntu-1804/), in order to upgrade the kernels to solve my touchpad problem. Unfortunately, that didn't help me, and in the meantime the error happened. Finally decided to remove the installed kernels and ukuu.

The output of those files:
  
```
cat -n /etc/kernel/postrm.d/zz-update-grub
     1    #! /bin/sh
     2    set -e
     3    
     4    which update-grub >/dev/null 2>&1 || exit 0
     5    
     6    if type systemd-detect-virt >/dev/null 2>&1 &&
     7       systemd-detect-virt --quiet --container; then
     8        exit 0
     9    fi
    10    
    11    set -- $DEB_MAINT_PARAMS
    12    mode="${1#\'}"
    13    mode="${mode%\'}"
    14    case $0:$mode in
    15        # Only run on postinst configure and postrm remove, to avoid wasting
    16        # time by calling update-grub multiple times on upgrade and removal.
    17        # Also run if we have no DEB_MAINT_PARAMS, in order to work with old
    18        # kernel packages.
    19        */postinst.d/*:|*/postinst.d/*:configure|*/postrm.d/*:|*/postrm.d/*:remove)
    20        if [ -e /boot/grub/grub.cfg ]; then
    21            exec update-grub
    22        fi
    23        ;;
    24    esac
    25    
    26    exit 0

```

```

xxx@xxx-lenovo:~$ cat -n /usr/sbin/grub-mkconfig
     1    #! /bin/sh
     2    set -e
     3    
     4    # Generate grub.cfg by inspecting /boot contents.
     5    # Copyright (C) 2006,2007,2008,2009,2010 Free Software Foundation, Inc.
     6    #
     7    # GRUB is free software: you can redistribute it and/or modify
     8    # it under the terms of the GNU General Public License as published by
     9    # the Free Software Foundation, either version 3 of the License, or
    10    # (at your option) any later version.
    11    #
    12    # GRUB is distributed in the hope that it will be useful,
    13    # but WITHOUT ANY WARRANTY; without even the implied warranty of
    14    # MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    15    # GNU General Public License for more details.
    16    #
    17    # You should have received a copy of the GNU General Public License
    18    # along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
    19    
    20    prefix="/usr"
    21    exec_prefix="/usr"
    22    datarootdir="/usr/share"
    23    
    24    prefix="/usr"
    25    exec_prefix="/usr"
    26    sbindir="${exec_prefix}/sbin"
    27    bindir="${exec_prefix}/bin"
    28    sysconfdir="/etc"
    29    PACKAGE_NAME=GRUB
    30    PACKAGE_VERSION=2.02-2ubuntu8.9
    31    host_os=linux-gnu
    32    datadir="${datarootdir}"
    33    if [ "x$pkgdatadir" = x ]; then
    34        pkgdatadir="${datadir}/grub"
    35    fi
    36    # export it for scripts
    37    export pkgdatadir
    38    
    39    grub_cfg=""
    40    grub_mkconfig_dir="${sysconfdir}"/grub.d
    41    
    42    self=`basename $0`
    43    
    44    grub_probe="${sbindir}/grub-probe"
    45    grub_file="${bindir}/grub-file"
    46    grub_editenv="${bindir}/grub-editenv"
    47    grub_script_check="${bindir}/grub-script-check"
    48    
    49    export TEXTDOMAIN=grub
    50    export TEXTDOMAINDIR="${datarootdir}/locale"
    51    
    52    . "${pkgdatadir}/grub-mkconfig_lib"
    53    
    54    # Usage: usage
    55    # Print the usage.
    56    usage () {
    57        gettext_printf "Usage: %s [OPTION]\n" "$self"
    58        gettext "Generate a grub config file"; echo
    59        echo
    60        print_option_help "-o, --output=$(gettext FILE)" "$(gettext "output generated config to FILE [default=stdout]")"
    61        print_option_help "-h, --help" "$(gettext "print this message and exit")"
    62        print_option_help "-v, --version" "$(gettext "print the version information and exit")"
    63        echo
    64        gettext "Report bugs to <bug-grub@gnu.org>."; echo
    65    }
    66    
    67    argument () {
    68      opt=$1
    69      shift
    70    
    71      if test $# -eq 0; then
    72          gettext_printf "%s: option requires an argument -- \`%s'\n" "$self" "$opt" 1>&2
    73          exit 1
    74      fi
    75      echo $1
    76    }
    77    
    78    # Check the arguments.
    79    while test $# -gt 0
    80    do
    81        option=$1
    82        shift
    83    
    84        case "$option" in
    85        -h | --help)
    86        usage
    87        exit 0 ;;
    88        -V | --version)
    89        echo "$self (${PACKAGE_NAME}) ${PACKAGE_VERSION}"
    90        exit 0 ;;
    91        -o | --output)
    92        grub_cfg=`argument $option "$@"`; shift;;
    93        --output=*)
    94        grub_cfg=`echo "$option" | sed 's/--output=//'`
    95        ;;
    96        -*)
    97        gettext_printf "Unrecognized option \`%s'\n" "$option" 1>&2
    98        usage
    99        exit 1
   100        ;;
   101        # Explicitly ignore non-option arguments, for compatibility.
   102        esac
   103    done
   104    
   105    if fgrep -qs '${GRUB_PREFIX}/video.lst' "${grub_mkconfig_dir}/00_header"; then
   106      echo "GRUB >= 2.00 has been unpacked but not yet configured." >&2
   107      echo "grub-mkconfig will not work until the upgrade is complete." >&2
   108      echo "It should run later as part of configuring the new GRUB packages." >&2
   109      exit 0
   110    fi
   111    
   112    if [ "x$EUID" = "x" ] ; then
   113      EUID=`id -u`
   114    fi
   115    
   116    if [ "$EUID" != 0 ] ; then
   117      root=f
   118      case "`uname 2>/dev/null`" in
   119        CYGWIN*)
   120          # Cygwin: Assume root if member of admin group
   121          for g in `id -G 2>/dev/null` ; do
   122        case $g in
   123          0|544) root=t ;;
   124        esac
   125          done ;;
   126      esac
   127      if [ $root != t ] ; then
   128        gettext_printf "%s: You must run this as root\n" "$self" >&2
   129        exit 1
   130      fi
   131    fi
   132    
   133    set $grub_probe dummy
   134    if test -f "$1"; then
   135        :
   136    else
   137        gettext_printf "%s: Not found.\n" "$1" 1>&2
   138        exit 1
   139    fi
   140    
   141    # Device containing our userland.  Typically used for root= parameter.
   142    GRUB_DEVICE="`${grub_probe} --target=device /`"
   143    GRUB_DEVICE_UUID="`${grub_probe} --device ${GRUB_DEVICE} --target=fs_uuid 2> /dev/null`" || true
   144    
   145    # Device containing our /boot partition.  Usually the same as GRUB_DEVICE.
   146    GRUB_DEVICE_BOOT="`${grub_probe} --target=device /boot`"
   147    GRUB_DEVICE_BOOT_UUID="`${grub_probe} --device ${GRUB_DEVICE_BOOT} --target=fs_uuid 2> /dev/null`" || true
   148    
   149    # Filesystem for the device containing our userland.  Used for stuff like
   150    # choosing Hurd filesystem module.
   151    GRUB_FS="`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2> /dev/null || echo unknown`"
   152    
   153    if [ x"$GRUB_FS" = xunknown ]; then
   154        GRUB_FS="$(stat -f --printf=%T / || echo unknown)"
   155    fi
   156    
   157    if test -f ${sysconfdir}/default/grub ; then
   158      . ${sysconfdir}/default/grub
   159    fi
   160    for x in ${sysconfdir}/default/grub.d/*.cfg ; do
   161      if [ -e "${x}" ]; then
   162        . "${x}"
   163      fi
   164    done
   165    
   166    # XXX: should this be deprecated at some point?
   167    if [ "x${GRUB_TERMINAL}" != "x" ] ; then
   168      GRUB_TERMINAL_INPUT="${GRUB_TERMINAL}"
   169      GRUB_TERMINAL_OUTPUT="${GRUB_TERMINAL}"
   170    fi
   171    
   172    termoutdefault=0
   173    if [ "x${GRUB_TERMINAL_OUTPUT}" = "x" ]; then
   174        GRUB_TERMINAL_OUTPUT=gfxterm;
   175        termoutdefault=1;
   176    fi
   177    
   178    for x in ${GRUB_TERMINAL_OUTPUT}; do
   179        case "x${x}" in
   180        xgfxterm) ;;
   181        xconsole | xserial | xofconsole | xvga_text)
   182                # make sure all our children behave in conformance with ascii..
   183            export LANG=C;;
   184        *) echo "Invalid output terminal \"${GRUB_TERMINAL_OUTPUT}\"" >&2 ; exit 1 ;;
   185        esac
   186    done
   187    
   188    GRUB_ACTUAL_DEFAULT="$GRUB_DEFAULT"
   189    
   190    if [ "x${GRUB_ACTUAL_DEFAULT}" = "xsaved" ] ; then GRUB_ACTUAL_DEFAULT="`"${grub_editenv}" - list | sed -n '/^saved_entry=/ s,^saved_entry=,,p'`" ; fi
   191    
   192    if [ "x${GRUB_RECOVERY_TITLE}" = "x" ]; then
   193      GRUB_RECOVERY_TITLE="recovery mode"
   194    fi
   195    
   196    
   197    # These are defined in this script, export them here so that user can
   198    # override them.
   199    export GRUB_DEVICE \
   200      GRUB_DEVICE_UUID \
   201      GRUB_DEVICE_BOOT \
   202      GRUB_DEVICE_BOOT_UUID \
   203      GRUB_FS \
   204      GRUB_FONT \
   205      GRUB_PRELOAD_MODULES \
   206      GRUB_ACTUAL_DEFAULT
   207    
   208    # These are optional, user-defined variables.
   209    export GRUB_DEFAULT \
   210      GRUB_HIDDEN_TIMEOUT \
   211      GRUB_HIDDEN_TIMEOUT_QUIET \
   212      GRUB_TIMEOUT \
   213      GRUB_TIMEOUT_STYLE \
   214      GRUB_DEFAULT_BUTTON \
   215      GRUB_HIDDEN_TIMEOUT_BUTTON \
   216      GRUB_TIMEOUT_BUTTON \
   217      GRUB_TIMEOUT_STYLE_BUTTON \
   218      GRUB_BUTTON_CMOS_ADDRESS \
   219      GRUB_BUTTON_CMOS_CLEAN \
   220      GRUB_DISTRIBUTOR \
   221      GRUB_CMDLINE_LINUX \
   222      GRUB_CMDLINE_LINUX_DEFAULT \
   223      GRUB_CMDLINE_XEN \
   224      GRUB_CMDLINE_XEN_DEFAULT \
   225      GRUB_CMDLINE_LINUX_XEN_REPLACE \
   226      GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT \
   227      GRUB_CMDLINE_NETBSD \
   228      GRUB_CMDLINE_NETBSD_DEFAULT \
   229      GRUB_CMDLINE_GNUMACH \
   230      GRUB_TERMINAL_INPUT \
   231      GRUB_TERMINAL_OUTPUT \
   232      GRUB_SERIAL_COMMAND \
   233      GRUB_DISABLE_LINUX_UUID \
   234      GRUB_DISABLE_RECOVERY \
   235      GRUB_VIDEO_BACKEND \
   236      GRUB_GFXMODE \
   237      GRUB_BACKGROUND \
   238      GRUB_THEME \
   239      GRUB_GFXPAYLOAD_LINUX \
   240      GRUB_DISABLE_OS_PROBER \
   241      GRUB_INIT_TUNE \
   242      GRUB_SAVEDEFAULT \
   243      GRUB_ENABLE_CRYPTODISK \
   244      GRUB_BADRAM \
   245      GRUB_OS_PROBER_SKIP_LIST \
   246      GRUB_DISABLE_SUBMENU \
   247      GRUB_RECORDFAIL_TIMEOUT \
   248      GRUB_RECOVERY_TITLE \
   249      GRUB_FORCE_PARTUUID \
   250      GRUB_DISABLE_INITRD
   251    
   252    if test "x${grub_cfg}" != "x"; then
   253      rm -f "${grub_cfg}.new"
   254      oldumask=$(umask); umask 077
   255      exec > "${grub_cfg}.new"
   256      umask $oldumask
   257    fi
   258    gettext "Generating grub configuration file ..." >&2
   259    echo >&2
   260    
   261    cat << EOF
   262    #
   263    # DO NOT EDIT THIS FILE
   264    #
   265    # It is automatically generated by $self using templates
   266    # from ${grub_mkconfig_dir} and settings from ${sysconfdir}/default/grub
   267    #
   268    EOF
   269    
   270    
   271    for i in "${grub_mkconfig_dir}"/* ; do
   272      case "$i" in
   273        # emacsen backup files. FIXME: support other editors
   274        *~) ;;
   275        # emacsen autosave files. FIXME: support other editors
   276        */\#*\#) ;;
   277        *)
   278          if grub_file_is_not_garbage "$i" && test -x "$i" ; then
   279            echo
   280            echo "### BEGIN $i ###"
   281            "$i"
   282            echo "### END $i ###"
   283          fi
   284        ;;
   285      esac
   286    done
   287    
   288    if [ "x${grub_cfg}" != "x" ] && ! grep "^password" ${grub_cfg}.new >/dev/null; then
   289      chmod 444 ${grub_cfg}.new || true
   290    fi
   291    
   292    if test "x${grub_cfg}" != "x" ; then
   293      if ! ${grub_script_check} ${grub_cfg}.new; then
   294        # TRANSLATORS: %s is replaced by filename
   295        gettext_printf "Syntax errors are detected in generated GRUB config file.
   296    Ensure that there are no errors in /etc/default/grub
   297    and /etc/grub.d/* files or please file a bug report with
   298    %s file attached." "${grub_cfg}.new" >&2
   299        echo >&2
   300        exit 1
   301      else
   302        # none of the children aborted with error, install the new grub.cfg
   303        mv -f ${grub_cfg}.new ${grub_cfg}
   304      fi
   305    fi
   306    
   307    gettext "done" >&2
   308    echo >&2

```
```

xxx@xxx-lenovo:~$ cat -n /etc/default/grub
     1    '# If you change this file, run 'update-grub' afterwards to update
     2    # /boot/grub/grub.cfg.
     3    # For full documentation of the options in this file, see:
     4    #   info -f grub -n 'Simple configuration'
     5    
     6    GRUB_DEFAULT=0
     7    GRUB_TIMEOUT_STYLE=hidden
     8    GRUB_TIMEOUT=10
     9    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    10    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash psmouse.proto=bare"          _***(" this was modified,  but the error still exist with the default ="quiet splash")***_

    11    GRUB_CMDLINE_LINUX=""
    12    
    13    # Uncomment to enable BadRAM filtering, modify to suit your needs
    14    # This works with Linux (no patch required) and with any kernel that obtains
    15    # the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
    16    #GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
    17    
    18    # Uncomment to disable graphical terminal (grub-pc only)
    19    #GRUB_TERMINAL=console
    20    
    21    # The resolution used on graphical terminal
    22    # note that you can use only modes which your graphic card supports via VBE
    23    # you can see them in real GRUB with the command `vbeinfo'
    24    #GRUB_GFXMODE=640x480
    25    
    26    # Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
    27    #GRUB_DISABLE_LINUX_UUID=true
    28    
    29    # Uncomment to disable generation of recovery mode menu entries
    30    #GRUB_DISABLE_RECOVERY="true"
    31    
    32    # Uncomment to get a beep at grub start
    33    #GRUB_INIT_TUNE="480 440 1"
```

---

### Post by coffeecat on 2018-12-17
@Gizatderebe, another member of forum staff had already edited your first post to included code tags. Now I have done the same for your latest post. Without code tags output such as you are posting loses formatting, making it difficult or impossible to read, so please use code tags. If you don't know how to use them, there is a link in my sig.

Thanks.

---

### Post by Gizatderebe on 2018-12-17
Thanks coffeecat-;) Hope will use that next time.

---

### Post by Impavidus on 2018-12-17
There's an apostrophe (single quote mark) at the start of the first line of your /etc/default/grub. That causes the error. Remove the apostrophe with a text editor with root privileges:```
sudo nano /etc/default/grub
```Then let the package manager complete removal of the kernels:```
sudo apt install -f
```

---

### Post by Gizatderebe on 2018-12-17
Thanks [URL="https://ubuntuforums.org/member.php?u=1417721"][COLOR=#000000]Impavidus. I used my big eyeglasses to find out that.
Cheers![/COLOR][/URL]

---

