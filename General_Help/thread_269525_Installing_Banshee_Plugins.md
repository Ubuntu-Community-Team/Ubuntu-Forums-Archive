---
title: "Installing Banshee Plugins"
date: 2006-10-01
forum: General Help
---

### Post by alex-desktop79 on 2006-10-01
I did all the commands to download the plugins I wanted, but when I type
"./autogen.sh" this is the output:
```
alex@alex-desktop:~/banshee-official-plugins$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.59
checking for automake >= 1.9...
  testing automake-1.9... not found.
***Error***: You must have automake >= 1.9 installed
  to build banshee-official-plugins.  Download the appropriate package for
  from your distribution or get the source tarball at
    http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz

checking for libtool >= 1.5...
  testing libtoolize... found 1.5.22
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build banshee-official-plugins.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

checking for intltool >= 0.30...
  testing intltoolize... found 0.35.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.20
/usr/bin/gnome-autogen.sh: line 149: --print-ac-dir: command not found
ACLOCAL=
AUTOCONF=autoconf
AUTOCONF_VERSION=2.59
AUTOHEADER=autoheader
BASH=/bin/sh
BASH_ARGC=([0]="1")
BASH_ARGV=([0]="/usr/bin/gnome-autogen.sh")
BASH_LINENO=([0]="154" [1]="348" [2]="19" [3]="0")
BASH_SOURCE=([0]="/usr/bin/gnome-autogen.sh" [1]="/usr/bin/gnome-autogen.sh" [2]="/usr/bin/gnome-autogen.sh" [3]="./autogen.sh")
BASH_VERSINFO=([0]="3" [1]="1" [2]="17" [3]="1" [4]="release" [5]="i486-pc-linux-gnu")
BASH_VERSION='3.1.17(1)-release'
COLORTERM=gnome-terminal
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-UaA7bFuCn6,guid=9d602045a485d84fad42e7a4e32c0500
DESKTOP_SESSION=gnome
DESKTOP_STARTUP_ID=
DIE=1
DIRSTACK=()
DISPLAY=:0.0
ECHO_N=-n
EUID=1000
FORBIDDEN_M4MACROS=' gnome-cxx-check.m4'
FUNCNAME=([0]="compare_versions" [1]="check_m4macros" [2]="source" [3]="main")
GDMSESSION=gnome
GDM_XSERVER_LOCATION=local
GNOME_DESKTOP_SESSION_ID=Default
GNOME_KEYRING_SOCKET=/tmp/keyring-tONGCh/socket
GROUPS=()
GTK_RC_FILES=/etc/gtk/gtkrc:/home/alex/.gtkrc-1.2-gnome2
HISTCONTROL=ignoredups
HOME=/home/alex
HOSTNAME=alex-desktop
HOSTTYPE=i486
IFS=.
INTLTOOLIZE=intltoolize
INTLTOOLIZE_VERSION=0.35.0
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LIBTOOLIZE=libtoolize
LIBTOOLIZE_VERSION=1.5.22
LOGNAME=alex
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
MACHTYPE=i486-pc-linux-gnu
OPTERR=1
OPTIND=1
OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
PIPESTATUS=([0]="0")
PKG_CONFIG=pkg-config
PKG_CONFIG_VERSION=0.20
PKG_NAME=banshee-official-plugins
POSIXLY_CORRECT=y
PPID=6712
PS4='+ '
PWD=/home/alex/banshee-official-plugins
REQUIRED_AUTOCONF_VERSION=2.53
REQUIRED_AUTOMAKE_VERSION=1.9
REQUIRED_DOC_COMMON_VERSION=2.3.0
REQUIRED_GETTEXT_VERSION=0.12
REQUIRED_GLIB_GETTEXT_VERSION=2.2.0
REQUIRED_GNOME_DOC_UTILS_VERSION=0.4.2
REQUIRED_GTK_DOC_VERSION=1.0
REQUIRED_INTLTOOL_VERSION=0.30
REQUIRED_LIBTOOL_VERSION=1.5
REQUIRED_M4MACROS=' libtool.m4 glib-gettext.m4 intltool.m4 pkg.m4'
REQUIRED_PKG_CONFIG_VERSION=0.14.0
SESSION_MANAGER=local/alex-desktop:/tmp/.ICE-unix/5610
SHELL=/bin/bash
SHELLOPTS=braceexpand:hashall:interactive-comments:posix
SHLVL=2
SSH_AGENT_PID=5658
SSH_AUTH_SOCK=/tmp/ssh-SGpprU5610/agent.5610
TERM=xterm
UID=1000
USER=alex
USERNAME=alex
USE_GNOME2_MACROS=1
WANT_AUTOCONF_2_5=1
WINDOWID=50331753
XAUTHORITY=/home/alex/.Xauthority
_=
automake_progs=automake-1.9
boldface=''
ch_actual_version=
ch_cur=20
ch_min=14
ch_min_version=1.7
ch_save_IFS='
'
ch_status=0
cm_macrodirs=
configure_ac=./configure.ac
configure_files=./configure.ac
normal=''
srcdir=.
vc_actual_version=0.20
vc_checkprog=pkg-config
vc_checkprogs=pkg-config
vc_comparator='>='
vc_min_version=0.14.0
vc_package=pkg-config
vc_source=''\''http://www.freedesktop.org/software/pkgconfig/releases/pkgconfig-0.14.0.tar.gz'
vc_status=0
vc_variable=PKG_CONFIG
want_gettext=false
want_glib_gettext=true
want_gnome_doc_utils=false
want_gtk_doc=false
want_intltool=true
want_libtool=true
want_pkg_config=true
Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee-official-plugins
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
```
Looks like theres a couple of errors in there, how do I get rid of them??

---

### Post by oneferna on 2006-10-30
I installed sudo apt-get install libmono0 libmono-dev and sudo aptitude install automake1.9 to get past some errors. 

But now I'm getting this (so plugins still aren't working for me)

checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... yes
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... not found
configure: error: missing required Mono Assembly: System.Runtime.Remoting.dll

---

### Post by Ferri on 2006-11-25
I've had the same error and found the fix:
```
sudo apt-get install libmono-system-runtime2.0-cil
```

---

### Post by fragos on 2006-11-25
Synaptic does suffer from this confussion.

---

