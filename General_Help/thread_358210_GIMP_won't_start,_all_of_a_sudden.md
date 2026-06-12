---
title: "GIMP won't start, all of a sudden"
date: 2007-02-10
forum: General Help
---

### Post by anemon on 2007-02-10
Hi everyone!

Well, seems I'm back again with a brand new problem for you all. This time, I've tried to compile a program (Radiance) from source -- without success, I'm afraid, but that's not why I'm here. Trying to start up GIMP, I suddenly get the following error message in terminal:

```
gimp: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
```

Which means? I've already tried to reinstall libgtk-2.0-0 and related packages, but that doesn't seem to help me. So now you'll have to! 

Best / A.

---

### Post by racmar on 2007-02-11
maybe it would help if you reinstalled gimp?  what happens if you execute this:

```
sudo apt-get install --reinstall gimp
```

---

### Post by anemon on 2007-02-11
Sorry, I should have mentioned that I tried that as well -- with no effect. :-(

I was even about to try a "complete removal" of GIMP from Synaptic, because I figured a clean install might fare better than a reinstall -- but then it wanted to remove a packade called "ubuntu-desktop" as well, and even if I don't actually *know* what it's for, it sure *sounds* important... ;-)

---

### Post by jeremy on 2007-02-11
Try renaming or deleting ~/.gimp-2.2 then see if gimp will start.

---

### Post by anemon on 2007-02-11
Thanks, Jeremy -- but I'm afraid that makes no difference. Still the same error message!

---

### Post by anemon on 2007-02-11
Bump bump! :-)

Someone please help me! I really need GIMP to work, and it would sure feel silly to have to reinstall the entire OS to make that happen...

---

### Post by racmar on 2007-02-11
How about reinstalling libgtk? try this:
```
sudo apt-get install --reinstall libgtk2.0-0
```

---

### Post by anemon on 2007-02-11
> **anemon said:**
> I've already tried to reinstall libgtk-2.0-0 and related packages, but that doesn't seem to help me. 

And, as if that wasn't enough, I've also tried to reinstall ALL the Gimp packages (not just "gimp"). With no effect. So you'll have to come up with something else... ;-)

---

### Post by racmar on 2007-02-11
well, do this:
```
ls -al /usr/lib/libgtk-x11-2.0.so.0
```
my system gave me a symbolic link:
> lrwxrwxrwx 1 root root 26 2007-02-02 09:25 /usr/lib/libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.1000.6

---

### Post by anemon on 2007-02-12
Yep, I've got the same one. Just one difference: I have no idea of what it means! ;-) Are you on to something here, racmar?

---

### Post by racmar on 2007-02-12
not really sure if I'm on to anything other than a fishing expedition!  However, let's try a few more commands:

```
ldd /usr/lib/libgtk-x11-2.0.so.0
```
should produce something like this:
```
        linux-gate.so.1 =>  (0xffffe000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7bca000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7b46000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7b3d000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7b03000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7a3a000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7a20000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb79e6000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb79e2000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb79de000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb794b000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb78e9000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb78c3000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb778f000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7760000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7753000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb774a000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7747000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb773f000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb773c000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb7733000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb772e000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7702000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7698000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7684000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7681000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb767c000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7672000)
        /lib/ld-linux.so.2 (0x80000000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb764e000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7630000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb761d000)

```

also, you could try running a strace when running gimp from the cli:
```
strace gimp > strace.txt 2>&1
```
Then look at this file /w your favorite text editor or use ```
tail -n 50 strace.txt
``` and post the results

This will tell us a lot more about what *exactly* is crashing.  The problem is that I'm not *very* experienced /w it.  But I'm willing to try!

---

### Post by anemon on 2007-02-12
OK, here we go: "ldd /usr/lib/libgtk-x11-2.0.so.0" gives me

```
        linux-gate.so.1 =>  (0xffffe000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7c41000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7bbd000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7bb4000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7b7a000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7ab1000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7a97000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7a5d000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7a59000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7a55000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb79c2000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7960000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb793a000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7806000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb77d7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb77ca000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb77c1000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb77be000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb77b6000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb77b3000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb77aa000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb77a5000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb7779000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb770f000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb76fb000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb76f8000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb76f3000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb76e9000)
        /lib/ld-linux.so.2 (0x80000000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb76c5000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb76a7000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7694000)

```

And strace.txt contains -- a h*ll of a lot of text! So much, in fact, that I can't include it all in this post... So here's the last couple of lines (the rest was mostly "no such file or directory" type errors). Hope you can make something out of it:

```
open("/usr/lib/libexpat.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340 \0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=122016, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb758c000
mmap2(NULL, 120824, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb756e000
mmap2(0xb758a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c) = 0xb758a000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb756d000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb756c000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb756c6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb76e7000, 8192, PROT_READ)   = 0
writev(2, [{"gimp", 4}, {": ", 2}, {"symbol lookup error", 19}, {": ", 2}, {"/usr/lib/libgtk-x11-2.0.so.0", 28}, {": ", 2}, {"undefined symbol: g_hash_table_r"..., 34}, {"", 0}, {"", 0}, {"\n", 1}], 10gimp: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_hash_table_ref
) = 92
exit_group(127)                         = ?
Process 6485 detached

```

I sure can't! ;-)

---

### Post by racmar on 2007-02-12
anemon,

You can upload the file to this forum as an attachment.  I suggest you try that, and I'll have another look in the morning...  Maybe someone else will help out while I'm asleep.

---

### Post by anemon on 2007-02-12
Oh, I see. :-\" Here it is -- although I had to compress it to make the server accept it (too big to attach as a text file, for some silly reason)...

---

### Post by racmar on 2007-02-12
thanks, but I would like to check a couple of more things first.  Please post the output of the following two commands:
```
dpkg -l | grep -i libglib
```
should look like this:
```
ii  libglib-java                               0.3.2-0ubuntu2                           GLIB bindings for Java
ii  libglib-perl                               1.120-1                                  Perl interface to the GLib and GObject libraries
ii  libglib1.2                                 1.2.10-10.1build1                        The GLib library of C routines
ii  libglib2.0-0                               2.12.4-0ubuntu1                          The GLib library of C routines
ii  libglib2.0-cil                             2.10.0-0ubuntu2                          CLI binding for the GLib utility library 2.12
ii  libglib2.0-data                            2.12.4-0ubuntu1                          Common files for GLib library
ii  libglib2.0-dev                             2.12.4-0ubuntu1                          Development files for the GLib library

```

and then:
```
cat /etc/apt/sources.list
```

I'm curious as to what version of libglib2.0-0 you have installed, and if it came from another source than the official repos.





**also, this set of commands will reinstall all packages required by the gimp!**
```
pkgs="" && for pkgname in `apt-cache depends gimp | grep Depends: | cut -d":" -f2 `; do pkgs="$pkgs $pkgname"; done && sudo apt-get install --reinstall $pkgs
```






-Rob

---

### Post by anemon on 2007-02-12
OK, "dpkg" gives me this:

```
ii  libglib-java                               0.3.2-0ubuntu2                       GLIB bindings for Java
ii  libglib-perl                               1.120-1                              Perl interface to the GLib and GObject libraries
ii  libglib1.2                                 1.2.10-10.1build1                    The GLib library of C routines
ii  libglib2.0-0                               2.12.4-0ubuntu1                      The GLib library of C routines
ii  libglib2.0-cil                             2.10.0-0ubuntu2                      CLI binding for the GLib utility library 2.12
ii  libglibmm-2.4-1c2a                         2.12.2-0ubuntu1                      C++ wrapper for the GLib toolkit (shared libraries)

```

... and "cat" this:

```
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb http://se.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://se.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://se.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
deb-src http://wxpython.wxcommunity.com/apt/ubuntu/dapper /

```

So far, all is well. But when I tried to reinstall all of the dependencies, it started out with:

```
0 upgraded, 0 newly installed, 35 reinstalled, 0 to remove and 0 not upgraded.
```

... but then it only got to number 30, and then halted with the following:

```
Get:30 http://se.archive.ubuntu.com edgy/main libxrender1 1:0.9.1-0ubuntu1 [20.1kB]                                                         
Fetched 3893kB in 1m3s (61.1kB/s)                                                                                                           
E: Internal Error, Could not perform immediate configuration (2) on zlib1g

```

... and GIMP still won't start. :-( Does this make any sense to you?

---

### Post by racmar on 2007-02-12
ok, try this instead:```

sudo apt-get install --reinstall wget gimp-data libaa1 libart-2.0-2 libatk1.0-0 libc6 libcairo2 libexif12 libexpat1 libfontconfig1 libfreetype6 libgimp2.0 libglib2.0-0 libgtk2.0-0 libice6 libjpeg62 liblcms1 libmng1 libpango1.0-0 libpng12-0 libsm6 libtiff4 libwmf0.2-7 libx11-6 libxcursor1 libxext6 libxfixes3 libxi6 libxinerama1 libxmu6 libxpm4 libxrandr2 libxrender1 libxt6
```

then do this:```

sudo apt-get install --reinstall zlib1g
```

This should reinstall every library that the gimp relies on to run.  If this does not work, I guess the problem would have to be in a library that one of these libraries relies on.
Maybe knowing exactly what was replaced when you tried to compile that other program would be helpful.

---

### Post by anemon on 2007-02-13
Well, this time everything worked just fine, with "zlibg1" as well -- and GIMP still won't work. So it has to be a dependency of a dependency, I guess. As to the program I tried to install (the rendering engine Radiance), here are the scripts that it uses:

"makeall"

```
#!/bin/csh -f
# RCSid $Id: makeall,v 1.21 2005/09/21 17:17:23 greg Exp $
# 
# Make all the Radiance programs
#
if ( $#argv < 1 ) then
	echo "Usage: makeall install [clean] [make options]"
	echo "   or: makeall clean"
	echo "   or: makeall library"
	exit 1
endif
if ( "$1" == library ) then
	source installib
	cp -f src/*/*.{cal,tab,hex} $ldir
	echo ""
	echo "Set the environment variable RAYPATH=.:$ldir"
	echo 'For C-shell users, put the following into ~/.cshrc'
	echo "	setenv RAYPATH .:$ldir"
	echo 'For Bourne shell users, put the following into $HOME/.profile'
	echo "	RAYPATH=.:$ldir"
	echo "	export RAYPATH"
	echo ""
	exit 0
endif
set srcdirs=( common rt meta cv gen ot px hd util cal )
if ( "$1" == install ) then
	cat << _EOF_

		`cat src/rt/VERSION` INSTALLATION

This script rebuilds all of the Radiance programs and installs
them on your system.  You should read the file README before running
this script.  You can type ^C (followed by return) at any time to abort.

You must first answer the following questions.

_EOF_
if ( ! $?EDITOR ) then
	echo -n "What is your preferred editor [vi]? "
	set ans="$<"
	if ( "$ans" != "" ) then
		setenv EDITOR "$ans"
	else
		setenv EDITOR vi
	endif
endif
again1:
echo -n "Where do you want the executables [/usr/local/bin]? "
set idir=$<
(echo $idir) >/dev/null
if ( $status ) then
	goto again1
endif
set idir=$idir
if ( "$idir" == "" ) then
	set idir=/usr/local/bin
else if ( "$idir" !~ /* ) then
	echo "Directory must be relative to root, please reenter"
	goto again1
endif
if ( ! -d $idir ) then
	mkdir $idir
	if ( $status ) then
		echo "Cannot create directory, please reenter"
		goto again1
	endif
endif
if ( ! -d $idir/dev ) then
	mkdir $idir/dev
	if ( $status ) then
		echo "Cannot create subdirectory, please reenter"
		goto again1
	endif
endif
set inpath=0
foreach i ( $path )
	if ( "$i" == "$idir" ) then
		set inpath=1
		break
	endif
end
set rmake=$idir/rmake
if ( "`ls -tL $rmake $0 |& head -1`" == $rmake ) then
	goto gotrmake
endif
set newrmake
more src/common/copyright.h
echo -n "Do you understand and accept the terms of this agreement [n]? "
set ans="$<"
if ( "$ans" !~ [yY]* ) exit
set special=
set arch=
set opt=
set mach=
set compat=
set extras=
set esuffix=
cat << _EOF_

Please select your system type from the following list:

	1)	Sun Solaris
	2)	HP workstation
	3)	Silicon Graphics
	4)	AIX (RS/6000)
	5)	BSDI BSD/386
	6)	Linux
	7)	MacOS X
	8)	FreeBSD
	9)	Cygwin
	10)	Other

_EOF_
echo -n "Choice? "
set arch="$<"
switch ("$arch")
case 1:			# SPARC Station
	set arch=sun
	set mach="-I/usr/openwin/include -L/usr/openwin/lib -DNOSTEREO"
	set opt="-O"
	set compat="strcmp.o"
	breaksw
case 2:			# HP workstation
	set mach=""
	set opt="-O -Aa -D_HPUX_SOURCE"
	set compat="strcmp.o"
	set arch=hpux
	breaksw
case 3:			# Silicon Graphics
	set arch=sgi
	switch (`uname -r`)
	case 3.*:
		set mach="-noprototypes"
		set opt="-O"
		set special="sgi"
		set compat="strcmp.o"
		breaksw
	case 4.*:
		set mach=""
		set opt="-O2"
		set compat="strcmp.o"
		set extras='"MLIB=-lfastm -lm"'
		breaksw
	default:	# 5.x or later
		ln -s `which wish` $idir/wish4.0
		set path=($idir $path)
		set mach="-w"
		set opt="-O2"
		set special="ogl"
		set compat="strcmp.o"
		breaksw
	endsw
	breaksw
case 4:			# AIX
	set opt="-O"
	set compat="erf.o strcmp.o"
	set arch=PowerPC
	breaksw
case 5:			# BSDI BSD/386
	set mach="-DBSD -L/usr/X11/lib -I/usr/X11/include"
	set opt="-O"
	set arch=IBMPC
	set compat="erf.o strcmp.o"
	breaksw
case 6:			# Linux
	set mach="-Dlinux -D_FILE_OFFSET_BITS=64 -Dfseeko=fseek -L/usr/X11R6/lib -I/usr/include/X11 -DNOSTEREO"
	set opt="-O2"
	set arch=IBMPC
	set compat="erf.o"
	set extras=CC=gcc
	breaksw
case 7:			# MacOS X
	set mach="-DBSD -DNOSTEREO -Dfreebsd -I/usr/X11R6/include -L/usr/X11R6/lib"
	set opt="-O2"
	set arch=PowerPC
	set extras="CC=cc CONFIGURE_ARCH=powerpc"
	set special="ogl"
	breaksw
case 8:			# FreeBSD
	set mach="-DBSD -DNOSTEREO -Dfreebsd -I/usr/X11R6/include -L/usr/X11R6/lib"
	set opt="-O"
	set compat="erf.o"
	set extras='CC=cc MLIB="-lcompat -lm"'
	set arch=IBMPC
	breaksw
case 9:			# Cygwin
	set mach="-Dfreebsd -L/usr/lib -L/usr/X11R6/lib -I/usr/include/X11 -I/usr/X11R6/include -DNOSTEREO"
	set opt="-O2"
	set arch=IBMPC
	set compat="erf.o"
	set extras="CC=gcc"
	set special="ogl"
	set esuffix=".exe"
	breaksw
case 10:			# Other
	set opt="-O"
	set compat="erf.o strcmp.o"
	echo -n "Are you using the GNU C compiler [n]? "
	if ( "$<" =~ [yY]* ) then
		set extras="CC=gcc"
	endif
	set arch=other
	breaksw
default:
	echo "Illegal choice\!"
	echo "Installation aborted."
	exit 1
	breaksw
endsw
source installib
sed 's/[ 	]*$//' > $rmake << _EOF_
#!/bin/sh
exec make "SPECIAL=$special" \
	"OPT=$opt" \
	"MACH=$mach" \
	ARCH=$arch "COMPAT=$compat" \
	INSTDIR=$idir \
	LIBDIR=$ldir \
	ESUFFIX=$esuffix \
	$extras "\$@" -f Rmakefile
_EOF_
chmod 755 $rmake
chmod 644 src/*/Rmakefile src/rt/devtable.c
gotrmake:
echo "Current rmake command is:"
cat $rmake
echo -n "Do you want to change it? "
set ans="$<"
if ( "$ans" =~ [yY]* ) then
	cp $rmake /tmp/rmake$$
	$EDITOR $rmake
	if ( `cat $rmake /tmp/rmake$$ | grep OPT= | uniq | wc -l` == 2 ) set newrmake
	rm -f /tmp/rmake$$
endif
if ( ! -d src/lib ) then
	mkdir src/lib
endif
if ( $?newrmake ) then
	echo 'New rmake command -- running "makeall clean"...'
	csh -f $0 clean
endif
cd src
echo "Making programs..."
set errs=0
foreach i ( $srcdirs )
	pushd $i
	echo "In directory $i..."
	$rmake -k $*
	@ errs += $status
	popd
end
if ( $errs ) then
	echo "There were some errors."
else
	echo "Done."
endif
cd ..
if (! $inpath ) then
	echo ""
	echo "Add $idir to the beginning of your execution path:"
	echo 'For C-shell users, put the following into ~/.cshrc'
	echo "	set path=( $idir "'$path )'
	echo 'For Bourne shell users, put the following into $HOME/.profile'
	echo "	PATH=$idir"':$PATH'
	echo "	export PATH"
endif
else
cd src
foreach i ( $srcdirs )
	pushd $i
	echo "In directory $i..."
	make -f Rmakefile $*
	popd
end
cd ..
foreach i ( $* )
	if ( "$i" == clean ) then
		echo "Removing library archives..."
		rm -f src/lib/*.{a,o,la}
	endif
end
echo "Done."
endif
exit 0

```

... and "installib"

```
#!/bin/csh -f
# RCSid $Id: installib,v 1.3 2003/10/30 15:41:23 greg Exp $
#
# Install library files
#
again2:
echo -n "Where do you want the library files [/usr/local/lib/ray]? "
set ldir=$<
(echo $ldir) >/dev/null
if ( $status ) goto again2
set ldir=$ldir
if ( "$ldir" == "" ) then
	set ldir=/usr/local/lib/ray
else if ( "$ldir" !~ /* ) then
	echo "Directory must be relative to root, please reenter"
	goto again2
endif
if ( ! -d $ldir ) then
	mkdir $ldir
	if ( $status ) then
		echo "Cannot create directory, please reenter"
		goto again2
	endif
endif
if (! -d lib) then
	echo ">>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>"
	echo "You forgot to install the auxiliary files overlay."
	echo "Download rad3R6supp.tar.gz from http://www.radiance-online.org"
	echo "and run 'installib' later manually, or ^C now."
	echo "<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<"
	exit
endif
set d1=(`ls -Lid lib`)
set d2=(`ls -Lid $ldir`)
if ($d1[1] != $d2[1]) then
	echo -n "Install library files now [n]? "
	if ( "$<" =~ [yY]* ) then
		echo -n "Copying library files to $ldir... "
		(cd lib ; tar -cf - *) | (cd $ldir ; tar -xf -)
		echo "Done."
	endif
endif
unset d1 d2

```

Not sure if you can make anything out of this, but it's worth a try, right? If not, I'll do what I can to supply you with any other info that you might need... Thanks for taking all this time!

---

### Post by racmar on 2007-02-13
No problem!  In a twisted sorta way, this is fun!

now, looking over the two scripts you posted, I see some mention of manipulating your path.
For example, from the first script:
```

	echo ""
	echo "Set the environment variable RAYPATH=.:$ldir"
	echo 'For C-shell users, put the following into ~/.cshrc'
	echo "	setenv RAYPATH .:$ldir"
	echo 'For Bourne shell users, put the following into $HOME/.profile'
	echo "	RAYPATH=.:$ldir"
	echo "	export RAYPATH"

and

	echo "Add $idir to the beginning of your execution path:"
	echo 'For C-shell users, put the following into ~/.cshrc'
	echo "	set path=( $idir "'$path )'
	echo 'For Bourne shell users, put the following into $HOME/.profile'
	echo "	PATH=$idir"':$PATH'
	echo "	export PATH"

```
Did you do add the path to .cshrc or .profile?

Also, just for kicks, post your path variable:
```
echo $PATH
```

when you ran installib, did you keep the default answers to where to install the libraries?  Maybe you could list /usr/local/lib/ray
```
ls -al /usr/local/lib/ray
```

I'm off for some sleep.  If I have to, I'll even try to install this radiance stuff myself ( let's hope it doesn't come to that! )

---

### Post by anemon on 2007-02-13
I guess you'll be awake by now? I'm just back from work and movies, myself, and will be going to sleep soon... :-) Anyhow, "echo" gave me:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

... and "ls" this:

```
ls: /usr/local/lib/ray: No such file or directory
```

... which, of course, isn't very helpful: when the compilation failed, I just deleted the files that had been installed. Probably a *very stupid* thing to do. Well, I'm a n00b. Sue me. ;-)

But I did keep all the defaults when I ran "installib" -- maybe we can still get somewhere with that lead?

---

### Post by anemon on 2007-02-21
Ok, people! I finally figured out to solve the problem! I still don't know what the problem *was*, exactly, but once it's solved, it's solved -- right?

Fiddling around with the Gimp and GTK packages, I suddenly realized that I had the Gimpshop hack installed. So I started up Synaptic and removed *that* package, and voilà! Everything is back to normal...

It remains to be seen if reinstalling Gimpshop will generate the same problem. In that case, I guess I'll just have to settle for the good ol' standard Gimp interface.

Anyhow, a million thanks to Racmar for all the trouble you went through! This is what Open Source is all about, right? :-)

---

### Post by risingfree on 2008-02-20
Woo Hoo!
Thanks for this. I've been trying to put words on a banner all night and this solved my problem.
 :lolflag:

Cheers
Mike

---

