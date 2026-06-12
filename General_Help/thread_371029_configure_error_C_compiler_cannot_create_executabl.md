---
title: "configure: error: C compiler cannot create executables"
date: 2007-02-26
forum: General Help
---

### Post by iBuck on 2007-02-26
Hi, thanks for help in advance. 

I just installed Ubuntu yesterday for the first time ever. I've never used linux before this, but it seems to be going smoothly. The only trouble i'm having is installing new programs that aren't all ready in the package manager. 

Right now I'm trying to install gift since it seems to be the best p2p file sharing program out for the Linux environment. I ran the ./configure and it shows me that all the dependencies are there except when it checks the C compiler. It then gives me this error code: 

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```

I've tried searching the forums, but being so new to Linux, it's been somewhat difficult to understand some of the terminology and instructions. After running it, it says to check the config.log file, allthough, that isn't helping either since I have no idea what to even look for. Here's the log file:

>   $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = pat-desktop
uname -m = i686
uname -r = 2.6.17-10-generic
uname -s = Linux
uname -v = #2 SMP Fri Oct 13 18:45:35 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/bin/X11
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1613: checking for a BSD-compatible install
configure:1668: result: /usr/bin/install -c
configure:1679: checking whether build environment is sane
configure:1722: result: yes
configure:1755: checking for gawk
configure:1771: found /usr/bin/gawk
configure:1781: result: gawk
configure:1791: checking whether make sets $(MAKE)
configure:1811: result: yes
configure:1977: checking whether to enable maintainer-specific portions of Makefiles
configure:1986: result: no
configure:2070: checking for gcc
configure:2086: found /usr/bin/gcc
configure:2096: result: gcc
configure:2340: checking for C compiler version
configure:2343: gcc --version </dev/null >&5
gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2346: $? = 0
configure:2348: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
configure:2351: $? = 0
configure:2353: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2356: $? = 1
configure:2379: checking for C compiler default output file name
configure:2382: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2385: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "giFT"
| #define PACKAGE_TARNAME "gift"
| #define PACKAGE_VERSION "0.11.8.1"
| #define PACKAGE_STRING "giFT 0.11.8.1"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "gift"
| #define VERSION "0.11.8.1"
| #define BUILD_DATE "Mon Feb 26 13:05:47 EST 2007"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2424: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/pat/Desktop/gift/missing --run aclocal-1.7'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/pat/Desktop/gift/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/pat/Desktop/gift/missing --run autoconf'
AUTOHEADER='${SHELL} /home/pat/Desktop/gift/missing --run autoheader'
AUTOMAKE='${SHELL} /home/pat/Desktop/gift/missing --run automake-1.7'
AWK='gawk'
BUILD_DOCS_FALSE=''
BUILD_DOCS_TRUE=''
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
DL_CFLAGS=''
DL_LDFLAGS=''
DL_LIBS=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
F77=''
FFLAGS=''
GIFTD_MAJOR='0'
GIFTD_MICRO='8'
GIFTD_MINOR='11'
GIFTD_VERSION='0.11.8'
GIFTD_VERSIONSTR='"0.11.8"'
GIFT_CFLAGS=''
GIFT_LDFLAGS=''
GIFT_LIBS=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBGIFTPROTO_MAJOR='0'
LIBGIFTPROTO_MICRO='8'
LIBGIFTPROTO_MINOR='11'
LIBGIFTPROTO_VERSION='0.11.8'
LIBGIFTPROTO_VERSIONSTR='"0.11.8"'
LIBGIFT_MAJOR='0'
LIBGIFT_MICRO='8'
LIBGIFT_MINOR='11'
LIBGIFT_VERSION='0.11.8'
LIBGIFT_VERSIONSTR='"0.11.8"'
LIBMAGIC_FALSE=''
LIBMAGIC_TRUE=''
LIBOBJS=''
LIBOGG_FALSE=''
LIBOGG_TRUE=''
LIBS=''
LIBTOOL=''
LIBVORBIS_FALSE=''
LIBVORBIS_TRUE=''
LN_S=''
LTDL_FALSE=''
LTDL_TRUE=''
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/pat/Desktop/gift/missing --run makeinfo'
OBJEXT=''
OGG_CFLAGS=''
OGG_LIBS=''
PACKAGE='gift'
PACKAGE_BUGREPORT=''
PACKAGE_NAME='giFT'
PACKAGE_STRING='giFT 0.11.8.1'
PACKAGE_TARNAME='gift'
PACKAGE_VERSION='0.11.8.1'
PATH_SEPARATOR=':'
PERL=''
PERL_CFLAGS=''
PERL_FALSE=''
PERL_LIBS=''
PERL_TRUE=''
RANLIB=''
SED=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
USE_LTDL=''
VERSION='0.11.8.1'
VORBISENC_LIBS=''
VORBISFILE_LIBS=''
VORBIS_CFLAGS=''
VORBIS_LIBS=''
XSLTPROC=''
ac_ct_AR=''
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
ac_ct_RANLIB=''
ac_ct_STRIP=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${prefix}/share'
exec_prefix='NONE'
giftdatadir=''
giftperldir=''
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/pat/Desktop/gift/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
libgiftincdir=''
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
perlpath=''
plugindir=''
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ------------- ##
## Output files. ##
## ------------- ##

GIFT_FEATURES=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define BUILD_DATE "Mon Feb 26 13:05:47 EST 2007"
#define PACKAGE "gift"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME "giFT"
#define PACKAGE_STRING "giFT 0.11.8.1"
#define PACKAGE_TARNAME "gift"
#define PACKAGE_VERSION "0.11.8.1"
#define VERSION "0.11.8.1"

configure: exit 77



All help is greatly appreciated.

---

### Post by nereid on 2007-02-26
You do have gcc installed? It isn't installed by default.

---

### Post by taurus on 2007-02-26
```
sudo aptitude update
sudo aptitude install build-essential
```

---

