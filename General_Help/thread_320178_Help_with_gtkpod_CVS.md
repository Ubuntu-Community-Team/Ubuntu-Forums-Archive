---
title: "Help with gtkpod CVS"
date: 2006-12-16
forum: General Help
---

### Post by damoek on 2006-12-16
ok, installing the CVS of the gtkpod suite is the only way to get the software to include the ability to transfer videos. Which is something that I need if i'm going to make the transition fully from windows. Now when I try to install the cvs of gtkpod the command line output is the following

> 
daniel@daniel-desktop:~/gtkpod$ sudo ./autogen.sh 
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
configure.in:45: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:755: AC_DECL_YYTEXT is expanded from...
aclocal.m4:1371: AM_PROG_LEX is expanded from...
configure.in:45: the top level
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: configure.in: installing `./config.guess'
automake: configure.in: installing `./config.sub'
src/Makefile.am:62: @LIBOBJS@ seen but never set in `configure.in'
automake: src/Makefile.am: not supported: source file `../pixmaps/gtkpod.glade' is in subdirectory
automake: src/Makefile.am: not supported: source file `../pixmaps/gtkpod.gladep' is in subdirectory
automake: configure.in: installing `src/ylwrap'
Running autoconf ...
configure.in:45: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:755: AC_DECL_YYTEXT is expanded from...
aclocal.m4:1371: AM_PROG_LEX is expanded from...
configure.in:45: the top level
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: *** Requested 'libgpod-1.0 >= 0.4.0' but version of libgpod is 0.3.2
See `config.log' for more details.


It seems to tell me that I need the latest version of libgpod, So I downloaded the CVS and  here is the output of that command line install...

> daniel@daniel-desktop:~/gtkpod/libgpod$ sudo ./autogen.sh 

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.7...

  testing automake-1.7... 
not found.
  testing automake-1.8... 
not found.
  testing automake-1.9... 
not found.
***Error***: You must have automake >= 1.7 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/automake/automake-1.7.tar.gz](http://ftp.gnu.org/pub/gnu/automake/automake-1.7.tar.gz)


checking for libtool >= 1.5...

  testing libtoolize... 
not found.
***Error***: You must have libtool >= 1.5 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/libtool/libtool-1.5.tar.gz](http://ftp.gnu.org/pub/gnu/libtool/libtool-1.5.tar.gz)


checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
not found.
***Error***: You must have intltool >= 0.30 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnome.org/pub/GNOME/sources/intltool/](http://ftp.gnome.org/pub/GNOME/sources/intltool/)


checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

checking for gtk-doc >= 1.0...

  testing gtkdocize... 
not found.
***Error***: You must have gtk-doc >= 1.0 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/](http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/)

./gnome-autogen.sh: 347: --print-ac-dir: not found
ACLOCAL=''
AUTOCONF='autoconf'
AUTOCONF_VERSION='2.60'
AUTOHEADER='autoheader'
COLORTERM='gnome-terminal'
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-64yKzEAVoF,guid=54968445d5f96412d9f29f94b654f000'
DESKTOP_SESSION='gnome'
DESKTOP_STARTUP_ID=''
DIE='1'
DISPLAY=':0.0'
DM_CONTROL='/var/run/xdmctl'
ECHO_N=''
FORBIDDEN_M4MACROS=' gnome-cxx-check.m4'
GLIB_GETTEXTIZE='glib-gettextize'
GLIB_GETTEXTIZE_VERSION='2.12.4'
GNOME_DESKTOP_SESSION_ID='Default'
GNOME_KEYRING_SOCKET='/tmp/keyring-pU6tf5/socket'
GTK_RC_FILES='/etc/gtk/gtkrc:/home/daniel/.gtkrc-1.2-gnome2'
HISTCONTROL='ignoredups'
HOME='/home/daniel'
IFS='.'
LANG='en_US.UTF-8'
LANGUAGE='en'
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LOGNAME='root'
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
OLDPWD='/home/daniel/gtkpod'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin'
PKG_CONFIG='pkg-config'
PKG_CONFIG_VERSION='0.20'
PKG_NAME='libgpod'
PPID='7457'
PS1='# '
PS2='> '
PS4='+ '
PWD='/home/daniel/gtkpod/libgpod'
REQUIRED_AUTOCONF_VERSION='2.53'
REQUIRED_AUTOMAKE_VERSION='1.7'
REQUIRED_DOC_COMMON_VERSION='2.3.0'
REQUIRED_GETTEXT_VERSION='0.12'
REQUIRED_GLIB_GETTEXT_VERSION='2.2.0'
REQUIRED_GNOME_DOC_UTILS_VERSION='0.3.2'
REQUIRED_GTK_DOC_VERSION='1.0'
REQUIRED_INTLTOOL_VERSION='0.30'
REQUIRED_LIBTOOL_VERSION='1.5'
REQUIRED_M4MACROS=' libtool.m4 glib-gettext.m4 intltool.m4 pkg.m4 gtk-doc.m4'
REQUIRED_PKG_CONFIG_VERSION='0.14.0'
SESSION_MANAGER='local/daniel-desktop:/tmp/.ICE-unix/4620'
SHELL='/bin/bash'
SHLVL='1'
SSH_AGENT_PID='4678'
SSH_AUTH_SOCK='/tmp/ssh-QJXaov4620/agent.4620'
SUDO_COMMAND='./autogen.sh'
SUDO_GID='1000'
SUDO_UID='1000'
SUDO_USER='daniel'
TERM='xterm'
USER='root'
WANT_AUTOCONF_2_5='1'
WINDOWID='48234590'
XDM_MANAGED='/var/run/xdmctl/xdmctl-:0,maysd,mayfn,sched,rsvd,method=classic'
_='/usr/bin/sudo'
automake_progs='automake-1.7 automake-1.8 automake-1.9'
boldface=''
ch_actual_version=''
ch_cur='20'
ch_min='14'
ch_min_version='1.7'
ch_save_IFS=' 
'
ch_status='0'
cm_macrodirs=''
configure_ac='./configure.ac'
configure_files='./configure.ac'
normal=''
srcdir='.'
vc_actual_version='0.20'
vc_checkprog='gtkdocize'
vc_checkprogs='gtkdocize'
vc_comparator='>='
vc_min_version='1.0'
vc_package='gtk-doc'
vc_source='http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/'
vc_status='1'
vc_variable='GTKDOCIZE'
want_gettext='false'
want_glib_gettext='true'
want_gnome_doc_utils='false'
want_gtk_doc='true'
want_intltool='true'
want_libtool='true'
want_pkg_config='true'
shift: 347: can't shift that many



Please Please Please help me. Where am I going wrong?

---

### Post by pay on 2006-12-16
You need to install automake, libtool, intltoolize and gtkdocize.```
sudo aptitude install build-essential automake1.9 libtool
sudo apt-get build-dep gtkpod
```

---

### Post by damoek on 2006-12-16
intltoolize won't install with apt-get 
any idea of what repository to enable?

---

### Post by pay on 2006-12-16
```
sudo aptitude install build-essential checkinstall
wget http://ftp.gnome.org/pub/GNOME/sources/intltool/0.35/intltool-0.35.1.tar.bz2
tar jxvf intltool-0.35.1.tar.bz2
cd intltool*
./configure
make
sudo checkinstall make install
sudo dpkg -i initool*.deb
```or it might be called intltool ```
sudo aptitude install intltool
```
EDIT: actually it is called intltool in Ubuntu's apt.

---

### Post by damoek on 2006-12-16
Ok. You have no idea how much you rock. Been fighting with this for weeks.

---

### Post by damoek on 2006-12-16
ok now libgpod sudo ./autogen.sh gives me

> daniel@daniel-desktop:~/gtkpod/libgpod$ sudo ./autogen.sh 

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.7...

  testing automake-1.7... 
not found.
  testing automake-1.8... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.1

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

checking for gtk-doc >= 1.0...

  testing gtkdocize... 
not found.
***Error***: You must have gtk-doc >= 1.0 installed
  to build libgpod.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/](http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/)


Checking for required M4 macros...

  intltool.m4 not found
  gtk-doc.m4 not found

Checking for forbidden M4 macros...

***Error***: some autoconf macros required to build libgpod
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


---

### Post by pay on 2006-12-16
You need gtk-doc```
wget http://ftp.gnome.org/pub/GNOME/sources/gtk-doc/1.7/gtk-doc-1.7.tar.bz2
tar jxvf gtk-doc-1.7.tar.bz2
cd gtk-doc*
./configure
make
sudo checkinstall make install
sudo dpkg -i gtk-doc*.deb
```do you have inltool installed? if yes then try compilling it from source because it's missing something.

---

### Post by damoek on 2006-12-17
I don't understand. 
> daniel@daniel-desktop:~/gtkpod/libgpod$ tar jxvf gtk-doc-1.7.tar.bz2
gtk-doc-1.7/
gtk-doc-1.7/gtk-doc.xsl
gtk-doc-1.7/version-greater-or-equal.xsl
gtk-doc-1.7/configure.in
gtk-doc-1.7/gtkdoc-fixxref.in
gtk-doc-1.7/gtkdocize.in
gtk-doc-1.7/configure
gtk-doc-1.7/ChangeLog
gtk-doc-1.7/README
gtk-doc-1.7/missing
gtk-doc-1.7/gtkdoc-scangobj.in
gtk-doc-1.7/gtk-doc.make
gtk-doc-1.7/MAINTAINERS
gtk-doc-1.7/right.png
gtk-doc-1.7/examples/
gtk-doc-1.7/examples/README
gtk-doc-1.7/examples/Makefile.am
gtk-doc-1.7/db2man/
gtk-doc-1.7/db2man/README
gtk-doc-1.7/db2man/docbook-to-man.ts
gtk-doc-1.7/db2man/docbook-to-man
gtk-doc-1.7/gtkdoc-scan.in
gtk-doc-1.7/gtkdoc-mkdb.in
gtk-doc-1.7/acinclude.m4
gtk-doc-1.7/home.png
gtk-doc-1.7/up.png
gtk-doc-1.7/install-sh
gtk-doc-1.7/gtkdoc-mkhtml.in
gtk-doc-1.7/left.png
gtk-doc-1.7/Makefile.in
gtk-doc-1.7/gtk-doc.spec
gtk-doc-1.7/gtk-doc.cat.in
gtk-doc-1.7/style.css
gtk-doc-1.7/COPYING
gtk-doc-1.7/gtkdoc-common.pl.in
gtk-doc-1.7/gtk-doc.dcl
gtk-doc-1.7/gtk-doc.pc.in
gtk-doc-1.7/doc/
gtk-doc-1.7/doc/setting-up.txt
gtk-doc-1.7/doc/README
gtk-doc-1.7/doc/style-guide.txt
gtk-doc-1.7/doc/authors.txt
gtk-doc-1.7/doc/sections-file.txt
gtk-doc-1.7/doc/gnome.txt
gtk-doc-1.7/omf.make
gtk-doc-1.7/NEWS
gtk-doc-1.7/devhelp.xsl
gtk-doc-1.7/devhelp2.xsl
gtk-doc-1.7/aclocal.m4
gtk-doc-1.7/AUTHORS
gtk-doc-1.7/gtk-doc.m4
gtk-doc-1.7/COPYING-DOCS
gtk-doc-1.7/gtkdoc-scanobj.in
gtk-doc-1.7/xmldocs.make
gtk-doc-1.7/gtkdoc-mkman.in
gtk-doc-1.7/Makefile.am
gtk-doc-1.7/gtkdoc-mktmpl.in
gtk-doc-1.7/gtk-doc.spec.in
gtk-doc-1.7/tools/
gtk-doc-1.7/tools/gtk-doc.el
gtk-doc-1.7/tools/docpercentages.pl
gtk-doc-1.7/gtk-doc.dsl.in
gtk-doc-1.7/INSTALL
gtk-doc-1.7/TODO
gtk-doc-1.7/help/
gtk-doc-1.7/help/manual/
gtk-doc-1.7/help/manual/C/
gtk-doc-1.7/help/manual/C/fdl-appendix.xml
gtk-doc-1.7/help/manual/C/ChangeLog
gtk-doc-1.7/help/manual/C/README
gtk-doc-1.7/help/manual/C/gtk-doc-manual.xml
gtk-doc-1.7/help/manual/C/gtk-doc-manual-C.omf
gtk-doc-1.7/help/manual/C/gtk-doc-manual-C.omf.in
gtk-doc-1.7/help/manual/C/Makefile.in
gtk-doc-1.7/help/manual/C/Makefile.am
gtk-doc-1.7/help/manual/Makefile.in
gtk-doc-1.7/help/manual/Makefile.am
gtk-doc-1.7/help/Makefile.in
gtk-doc-1.7/help/Makefile.am
daniel@daniel-desktop:~/gtkpod/libgpod$ cd gtk-doc*
daniel@daniel-desktop:~/gtkpod/libgpod/gtk-doc-1.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.19... yes
checking for perl... /usr/bin/perl
checking if Perl version >= 5.6.0... yes
checking for openjade... no
checking for jade... no
configure: WARNING: Could not find openjade or jade, so SGML is not supported
checking for xsltproc... /usr/bin/xsltproc
checking for XML catalog (/etc/xml/catalog)... found
checking for xmlcatalog... /usr/bin/xmlcatalog
checking for DocBook XML DTD V4.1.2 in XML catalog... found
checking for DocBook XSL Stylesheets in XML catalog... not found
configure: error: could not find DocBook XSL Stylesheets in XML catalog
daniel@daniel-desktop:~/gtkpod/libgpod/gtk-doc-1.7$ make
make: *** No targets specified and no makefile found.  Stop.


---

### Post by pay on 2006-12-17
Here's a howto on how to install docbook [http://tldp.org/HOWTO/DocBook-Install/index.html](http://tldp.org/HOWTO/DocBook-Install/index.html)

---

### Post by damoek on 2006-12-17
```
sudo apt-get install docbook
```

seemed to work just fine.

Why is this so complicated?

---

### Post by damoek on 2006-12-17
even though I installed docbook through the repositories I seem to still be unable to compile gtk-doc

the error i keep running into is 
```
configure: error: could not find DocBook XSL Stylesheets in XML catalog
```

---

### Post by damoek on 2006-12-17
sweet

> sudo apt-get install docbook-xsl 

resolved the first problem

Now, I've been able to compile and install gtk-doc-1.7
which is much further along that I was earlier 
and the output of ./autogen.sh is much cleaner now
> 
checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.7...

  testing automake-1.7... 
not found.
  testing automake-1.8... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.1

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

checking for gtk-doc >= 1.0...

  testing gtkdocize... 
found 1.7

Checking for required M4 macros...

  intltool.m4 not found
  gtk-doc.m4 not found

Checking for forbidden M4 macros...

***Error***: some autoconf macros required to build libgpod
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

So even with intltool installed how come I'm missing a dependency?

any Ideas on this M4 macros or the ALOCAL_FLAGS?

---

### Post by damoek on 2006-12-17
Well. I am coming right along.
I found the missing .m4 files with find -name 'intltool.m4' 
and then ran the command
>  export ACLOCAL_FLAGS="-I /usr/share/aclocal

Which finally resolved that part of the problem. Now I still cant get libgpod to install

when i run the sudo ./autogen.sh

everything looks fine until 
> Running intltoolize...

intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite



when i run intltoolize --force
> intltoolize --force
You should add the contents of '/usr/local/share/aclocal/intltool.m4' to 'aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, '..'.
intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite


I am getting closer. But I have no idea what to do about this. Help?

---

