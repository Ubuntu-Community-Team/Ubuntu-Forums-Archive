---
title: "Can anyone successfully build the latest version of f-spot?"
date: 2008-06-07
forum: General Help
---

### Post by jonboy99 on 2008-06-07
I am trying to install the latest (released) version of f-spot - 0.4.4. Gutsy fully updated.

I am installing this rather than the version in the repos as the repo version has a bug which won't let it write photo albums etc on cd.
The author has acknowledged this bug and fixed it in the latest version.

I am having mono problems when trying to ./configure it, when following these instructions.  I think it is because ubuntu needs a later version of mcs to compile or build it.

When I try the ./configure command according to the instructions here:
[http://f-spot.org/How_To_Build_from_Release](http://f-spot.org/How_To_Build_from_Release)

I get this output:

```
admin@q6600:~/Desktop/f-spot-0.4.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
./configure: line 20953: GNOME_COMPILE_WARNINGS: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.16.3)
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... found
checking for System.Web.dll... found
checking for System.Web.Services.dll... found
checking for Mono.Cairo.dll... found
checking for F... yes
checking for GNOME_SHARP... yes
checking for GTKHTML_SHARP... yes
checking for GCONF_SHARP... yes
checking for BEAGLE... no
beagle not found
checking for NDESK_DBUS... yes
checking for MONO_NUNIT... no
checking for NUNIT22... no
checking for NUNIT... no
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for jpeg_start_decompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for LCMS... yes
checking for LIBGPHOTO2... yes
checking for EXIF... yes
checking for LIBEXIF_VERSION_CHECK... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating src/f-spot
config.status: creating Makefile
config.status: creating dbus-sharp/Makefile
config.status: creating dbus-sharp-glib/Makefile
config.status: creating docs/Makefile
config.status: creating gnome-keyring-sharp/Makefile
config.status: creating icons/Makefile
config.status: creating libeog/Makefile
config.status: creating libeog/cursors/Makefile
config.status: creating libjpegtran/Makefile
config.status: creating libfspot/Makefile
config.status: creating libgphoto2-sharp/Makefile
config.status: creating mono-addins/Makefile
config.status: creating mono-addins/Mono.Addins/Makefile
config.status: creating mono-addins/Mono.Addins.Gui/Makefile
config.status: creating mono-addins/Mono.Addins.Setup/Makefile
config.status: creating semweb/Makefile
config.status: creating tools/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Core/Defines.cs
config.status: creating src/AssemblyInfo.cs
config.status: creating src/f-spot.exe.config
config.status: creating src/Cms.dll.config
config.status: creating src/Makefile
config.status: creating glitz-sharp/Makefile
config.status: creating glitz-sharp/src/Makefile
config.status: creating Tao/Makefile
config.status: creating Tao/Tao.OpenGl/Makefile
config.status: creating Tao/Tao.OpenGl.Glu/Makefile
config.status: creating Tao/Tao.GlPostProcess/Makefile
config.status: creating Tao/Tao.OpenGl.ExtensionLoader/Makefile
config.status: creating extensions/Makefile
config.status: creating extensions/CDExport/Makefile
config.status: creating extensions/DefaultExporters/Makefile
config.status: creating extensions/FlickrExport/Makefile
config.status: creating extensions/FlickrExport/FlickrNet/Makefile
config.status: creating extensions/GalleryExport/Makefile
config.status: creating extensions/FolderExport/Makefile
config.status: creating extensions/SmugMugExport/SmugMugNet/Makefile
config.status: creating extensions/SmugMugExport/Makefile
config.status: creating extensions/PicasaWebExport/Makefile
config.status: creating extensions/PicasaWebExport/google-sharp/Makefile
config.status: creating f-spot.pc
config.status: creating f-spot.spec
config.status: creating f-spot.desktop.in
config.status: creating f-spot-view.desktop.in
config.status: creating f-spot-import.desktop.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
=== configuring in gio-sharp (/home/admin/Desktop/f-spot-0.4.4/gio-sharp)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_DEPENDENCY... yes
checking for al... /usr/bin/al
checking for mono... /usr/bin/mono
checking for mcs... no
configure: error: No C# compiler found
configure: error: ./configure failed for gio-sharp
admin@q6600:~/Desktop/f-spot-0.4.4$ 



```

Looking in synaptic, although mono-gmcs and mono-smcs were installed, mono-mcs was not.  So i installed it, and got the following output from the ./configure command, which seemed to indicate the mono-mcs was outdated, and synaptic does indeed describe mcs as being the compiler for CLI 1.1, whereas mono-gmcs and mono-smcs are for 2.1 and 2.0:


```
admin@q6600:~/Desktop/f-spot-0.4.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
./configure: line 20953: GNOME_COMPILE_WARNINGS: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.16.3)
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for mono.pc... found
checking for Mono.Data.SqliteClient.dll... found
checking for Mono.Posix.dll... found
checking for System.Runtime.Remoting.dll... found
checking for System.Web.dll... found
checking for System.Web.Services.dll... found
checking for Mono.Cairo.dll... found
checking for F... yes
checking for GNOME_SHARP... yes
checking for GTKHTML_SHARP... yes
checking for GCONF_SHARP... yes
checking for BEAGLE... no
beagle not found
checking for NDESK_DBUS... yes
checking for MONO_NUNIT... no
checking for NUNIT22... no
checking for NUNIT... no
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for jpeg_start_decompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking for LCMS... yes
checking for LIBGPHOTO2... yes
checking for EXIF... yes
checking for LIBEXIF_VERSION_CHECK... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
configure: creating ./config.status
config.status: creating src/f-spot
config.status: creating Makefile
config.status: creating dbus-sharp/Makefile
config.status: creating dbus-sharp-glib/Makefile
config.status: creating docs/Makefile
config.status: creating gnome-keyring-sharp/Makefile
config.status: creating icons/Makefile
config.status: creating libeog/Makefile
config.status: creating libeog/cursors/Makefile
config.status: creating libjpegtran/Makefile
config.status: creating libfspot/Makefile
config.status: creating libgphoto2-sharp/Makefile
config.status: creating mono-addins/Makefile
config.status: creating mono-addins/Mono.Addins/Makefile
config.status: creating mono-addins/Mono.Addins.Gui/Makefile
config.status: creating mono-addins/Mono.Addins.Setup/Makefile
config.status: creating semweb/Makefile
config.status: creating tools/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Core/Defines.cs
config.status: creating src/AssemblyInfo.cs
config.status: creating src/f-spot.exe.config
config.status: creating src/Cms.dll.config
config.status: creating src/Makefile
config.status: creating glitz-sharp/Makefile
config.status: creating glitz-sharp/src/Makefile
config.status: creating Tao/Makefile
config.status: creating Tao/Tao.OpenGl/Makefile
config.status: creating Tao/Tao.OpenGl.Glu/Makefile
config.status: creating Tao/Tao.GlPostProcess/Makefile
config.status: creating Tao/Tao.OpenGl.ExtensionLoader/Makefile
config.status: creating extensions/Makefile
config.status: creating extensions/CDExport/Makefile
config.status: creating extensions/DefaultExporters/Makefile
config.status: creating extensions/FlickrExport/Makefile
config.status: creating extensions/FlickrExport/FlickrNet/Makefile
config.status: creating extensions/GalleryExport/Makefile
config.status: creating extensions/FolderExport/Makefile
config.status: creating extensions/SmugMugExport/SmugMugNet/Makefile
config.status: creating extensions/SmugMugExport/Makefile
config.status: creating extensions/PicasaWebExport/Makefile
config.status: creating extensions/PicasaWebExport/google-sharp/Makefile
config.status: creating f-spot.pc
config.status: creating f-spot.spec
config.status: creating f-spot.desktop.in
config.status: creating f-spot-view.desktop.in
config.status: creating f-spot-import.desktop.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
=== configuring in gio-sharp (/home/admin/Desktop/f-spot-0.4.4/gio-sharp)
configure: running /bin/bash ./configure '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO_DEPENDENCY... yes
checking for al... /usr/bin/al
checking for mono... /usr/bin/mono
checking for mcs... /usr/bin/mcs
checking for GLIB_SHARP... configure: error: Package requirements (glib-sharp-2.0 >= 2.12.1) were not met:

Requested 'glib-sharp-2.0 >= 2.12.1' but version of GLib is 2.12.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_SHARP_CFLAGS
and GLIB_SHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

configure: error: ./configure failed for gio-sharp
admin@q6600:~/Desktop/f-spot-0.4.4$ 
admin@q6600:~/Desktop/f-spot-0.4.4$ 


```

I am not sure whether the problem is that f-spot should be using mono-gmcs, rahter than mono-mcs, or if my mono-mcs is out of date. (it's the latest version in the repos).
I don't want to go about installing bits like glib-sharp individually as I don't really know what i'm doing and could mess things up!  

Any advice?  I did follow the following advice from the f-spot page and both commands ran without any errors:

> Note: on some systems, like recent debian or ubuntu, installing all this is as simple as running
'apt-get build-dep f-spot'

    * automake/autogen tool chain: automake1.9, libtool, intltool 

'apt-get install automake1.9 build-essential intltool libtool' should do the job on ubuntu or debian


Cheers!

Jon

---

### Post by saffolino on 2008-06-07
Same thing here ;_;

---

### Post by saffolino on 2008-06-09
up

---

### Post by geirha on 2008-06-09
You probably need [mono-gmcs](apt:mono-gmcs) instead of [mono-mcs]("apt:mono-mcs"), but just do ```
sudo apt-get build-dep f-spot
``` and all the necessary libs and programs needed to build f-spot should be installed for you.

---

### Post by emway on 2008-06-09
Same problem here... need latest glib-sharp.. 2.12.1
Anyone tried to install this component seperately?? Is it possible?

>> FIXED 
[https://launchpad.net/~ruben/+archive](https://launchpad.net/~ruben/+archive)

add the lines to /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade will update the components needed for f-spot compilation.

GOOD LUCK!

---

### Post by geodanny on 2008-06-14
> **emway said:**
> Same problem here... need latest glib-sharp.. 2.12.1
Anyone tried to install this component seperately?? Is it possible?

>> FIXED 
[https://launchpad.net/~ruben/+archive](https://launchpad.net/~ruben/+archive)

add the lines to /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade will update the components needed for f-spot compilation.

GOOD LUCK!

Emway: Do you mean to add the launchpad.net url to the sources.list? and then to apt-get update/upgrade? 

```
## to update glib-sharp
deb http://ppa.launchpad.net/ruben/ubuntu hardy main
deb-src http://ppa.launchpad.net/ruben/ubuntu hardy main
```

Note: I updated the packages from [https://launchpad.net/~ruben/+archive](https://launchpad.net/~ruben/+archive). I still have the same issue and get stuck with the same ending point as jonboy99. 

"configure: error: No C# compiler found
configure: error: ./configure failed for gio-sharp"

---

### Post by maxxer on 2008-06-16
> **geodanny said:**
> 
"configure: error: No C# compiler found
configure: error: ./configure failed for gio-sharp"

do you have mono-mcs package installed?

---

### Post by geodanny on 2008-06-16
thx, that did the trick. i installed mono-mcs and ./configure worked. I didn't realize it was not installed.

---

### Post by Tyler Oderkirk on 2008-09-03
Installing glib-sharp 2.12.1 from Ruben's Personal Package Archive (PPA) also solved my ./configure problem.

Be aware that PPA packages are apparently unsigned and you'll have to say "Yes" to the following prompt:

```
WARNING: The following packages cannot be authenticated!
  [...]
Install these packages without verification [y/N]?
```

Here's the good news:

"We're working to fix this and enable you to sign your packages in the near future." - [http://f-spot.org/How_To_Build_from_Release](http://f-spot.org/How_To_Build_from_Release)

---

### Post by kmolnar on 2008-10-06
I'm having this problem too, but for the life of me I can't find a package called glib-sharp in this PPA or anywhere for that matter. What am I doing wrong? =/

---

### Post by srf21c on 2008-10-24
Followed all the steps above in order to compile f-spot 0.4.4 for Hardy Heron 8.04.  The configure script craps out like so:

```
checking for GAPI... configure: error: Package requirements (gapi-2.0 >= 2.12.1) were not met:

No package 'gapi-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAPI_CFLAGS
and GAPI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

configure: error: ./configure failed for gio-sharp

```

---

### Post by directhex on 2008-10-24
apt-get build-dep f-spot

Job jobbed.

---

### Post by jonboy99 on 2008-11-04
Hi srf21c, I had a similar problem after going to Reuben's PPA page (had to make sure I installed the hardy packages not the intrepid ones from his drop down list.)

I then went into the synaptic package manager, searched for gapi, then installed the gtk sharp2 gapi package it came up with.

./configure finally worked!   Woohoo!  Latest version of f-spot without having to upgrade distro from Hardy on this comp.  :D


> **srf21c said:**
> Followed all the steps above in order to compile f-spot 0.4.4 for Hardy Heron 8.04.  The configure scrips craps out like so:

```
checking for GAPI... configure: error: Package requirements (gapi-2.0 >= 2.12.1) were not met:

No package 'gapi-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAPI_CFLAGS
and GAPI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

configure: error: ./configure failed for gio-sharp

```

---

### Post by srf21c on 2008-11-05
> **jonboy99 said:**
> Hi srf21c, I had a similar problem after going to Reuben's PPA page (had to make sure I installed the hardy packages not the intrepid ones from his drop down list.)

I then went into the synaptic package manager, searched for gapi, then installed the gtk sharp2 gapi package it came up with.

./configure finally worked!   Woohoo!  Latest version of f-spot without having to upgrade distro from Hardy on this comp.  :D

Jonboy99, thanks for the suggestion.  

I tried:

```
sudo apt-get build-dep f-spot
sudo apt-get install gtk-sharp2-gapi
```

and then ran the configure script for f-spot-0.4.4, but it died in the same place. 

```
configure: error: No C# compiler found
configure: error: ./configure failed for gio-sharp
```

Environment is Ubuntu Hardy amd64

---

### Post by jonboy99 on 2008-11-05
Bizarre.  At least we can blame your problems on your 64bit version now. :D

Have you got gcc installed?  That is the compiler normally installed as default with ubuntu.

---

### Post by srf21c on 2008-11-05
Yes I do have gcc installed.  At least I'm getting a little further now, but still no success.  

I had forgotten to update glib first via Ruvens repositories, so I did that and also installed mono-mcs  (mono-gmcs was already installed)

Between those two steps, the configure script will now finish without errors.  running "make" also finished without any errors.  "sudo checkinstall" choked.  Ran "sudo make intall"
and that seems  to have finished successfully.  Ran f-spot from the terminal and it chokes.   ](*,)


[Info  13:14:06.254] Initializing DBus
[Info  13:14:06.559] Initializing Mono.Addins
[Info  13:14:06.780] Starting new FSpot server

** (f-spot:8371): WARNING **: The following assembly referenced from /usr/local/lib/f-spot/f-spot.exe could no
t be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=18)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, 
or in the location of the executing assembly (/usr/local/lib/f-spot).


** (f-spot:8371): WARNING **: Could not load file or assembly 'Mono.Data.SqliteClient, Version=2.0.0.0, Cultur
e=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
XXXXX
System.ArgumentNullException: Argument cannot be null.
Parameter name: src
  at System.IO.File.Move (System.String src, System.String dest) [0x00000] 
  at Db.Repair () [0x00000] 
  at FSpot.Core.get_Database () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.913] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.914] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.915] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.916] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.916] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

---

### Post by jonboy99 on 2008-11-05
Sorry fella, that one's well beyond my novice ability to troubleshoot.  Hope you get it sorted soon.

---

### Post by directhex on 2008-11-06
> **srf21c said:**
> Yes I do have gcc installed.  At least I'm getting a little further now, but still no success.  

I had forgotten to update glib first via Ruvens repositories, so I did that and also installed mono-mcs  (mono-gmcs was already installed)

Between those two steps, the configure script will now finish without errors.  running "make" also finished without any errors.  "sudo checkinstall" choked.  Ran "sudo make intall"
and that seems  to have finished successfully.  Ran f-spot from the terminal and it chokes.   ](*,)


[Info  13:14:06.254] Initializing DBus
[Info  13:14:06.559] Initializing Mono.Addins
[Info  13:14:06.780] Starting new FSpot server

** (f-spot:8371): WARNING **: The following assembly referenced from /usr/local/lib/f-spot/f-spot.exe could no
t be loaded:
     Assembly:   Mono.Data.SqliteClient    (assemblyref_index=18)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, 
or in the location of the executing assembly (/usr/local/lib/f-spot).


** (f-spot:8371): WARNING **: Could not load file or assembly 'Mono.Data.SqliteClient, Version=2.0.0.0, Cultur
e=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
XXXXX
System.ArgumentNullException: Argument cannot be null.
Parameter name: src
  at System.IO.File.Move (System.String src, System.String dest) [0x00000] 
  at Db.Repair () [0x00000] 
  at FSpot.Core.get_Database () [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.913] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.914] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.915] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.916] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
[Info  13:14:06.916] Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

libmono-sqlite2.0-cil

---

### Post by srf21c on 2008-11-06
directhex, thanks for the suggestion to install libmono-sqlite2.0-cil

I tried that, then ran f-spot from the terminal and it still didn't work.

So I unintalled, nuked my f-spot souce dir, then downloaded a fresh tarball of v0.4.4

Ran the configure script, and it choked again.  Ran "apt-get build-dep f-spot" and it installed three missing packages that had somehow uninstalled themselves along the way.

./configure script worked, so did make command.  sudo checkinstall failed once again, so I ran the standard "sudo make install" and that completed without errors.

Lo and behold f-spot runs.   Now it's just a matter of doing battle with the old export extensions which I cannot seem to remove.

---

### Post by srf21c on 2008-11-06
I was finally able to uninstall my old extensions by running f-spot with sudo and then removing the extensions using the GUI menu option.

New extensions were installed as a regular user.

Still getting errors exporting to smugmug though, even with the new updated export extension.  :x

---

### Post by srf21c on 2008-11-07
I gave up on 0.4.4 and downloaded the tarball for the latest 0.5.0.3.  ./configure & make & make install....no problems. checkinstall still croaks.   I can export to SmugMug now w/out indicent.  Huzzah.

---

### Post by RolfH on 2009-01-27
> **kmolnar said:**
> I'm having this problem too, but for the life of me I can't find a package called glib-sharp in this PPA or anywhere for that matter. What am I doing wrong? =/


Got source files from
[https://launchpad.net/ubuntu/+source/f-spot](https://launchpad.net/ubuntu/+source/f-spot)

Add the lines above to ubuntu sources..
```
echo "deb http://ppa.launchpad.net/ruben/ubuntu hardy main" | sudo tee -a /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/ruben/ubuntu hardy main" | sudo tee -a /etc/apt/sources.list

```

Install missing libs:
```

apt-get install cli-common-dev mono-gmcs libmono-dev libmono-system-runtime2.0-cil libgnome-keyring1.0-cil libusb-dev libgphoto2-2-dev libglitz1-dev libglitz-glx1-dev gtk-sharp2-gapi mono-mcs
apt-get install gtk-sharp2-gapi
apt-get install libglib2.0-cil

```

Clean up the mess and rebuild it..
```
rm -rf f-spot-0.5.0.3
dpkg-source -x f-spot_0.5.0.3-0ubuntu4.dsc
cd f-spot-0.5.0.3
dpkg-buildpackage -rfakeroot -b
```

---

### Post by Rainwolf on 2009-07-29
Well I have a slightly different problem along the same lines.
I got ./configure - make - make install all works fine
but when I try and run f-spot I get this error:

[Info  02:25:43.974] Initializing DBus
[Info  02:25:44.069] Initializing Mono.Addins
WARNING: The add-in 'FSpot.__DefaultExporters,1.6' is trying to extend '/FSpot/Menus/Exports', but there isn't any compatible add-in defining this extension point
[Info  02:25:44.633] Starting new FSpot server

(f-spot:9148): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 317 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I'm unsure which gtk- i need to install or upgrade. any suggestions?

---

### Post by Rainwolf on 2009-07-29
sorry I don't know how to make the code in a box to scroll :/

---

### Post by directhex on 2009-07-29
This looks like a bug I've seen before - can you try changing your window theme under preferences/appearance to something different (e.g. the default)?

---

### Post by Rainwolf on 2009-07-30
I have used the ubuntu studios default as well as a couple others..
 I'll run through them again

---

### Post by Rainwolf on 2009-08-05
I totally reinstalled my system again. without any updates f-spot ran fine.
Updated still fine
upgraded f-spot to 5.0 runs fine
installed my ati video driver...
f-spot will not load
[Info  02:12:34.939] Initializing DBus
[Info  02:12:35.030] Initializing Mono.Addins
[Info  02:12:35.168] Starting new FSpot server
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 332 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I have tried every xwindow theme i have and nothing changes
any help would be greatly appreciated by this poor unbuntu newbie

---

### Post by directhex on 2009-08-05
> **Rainwolf said:**
> I totally reinstalled my system again. without any updates f-spot ran fine.
Updated still fine
upgraded f-spot to 5.0 runs fine
installed my ati video driver...
f-spot will not load
[Info  02:12:34.939] Initializing DBus
[Info  02:12:35.030] Initializing Mono.Addins
[Info  02:12:35.168] Starting new FSpot server
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 332 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I have tried every xwindow theme i have and nothing changes
any help would be greatly appreciated by this poor unbuntu newbie

Those are interesting details. Can you post them into a bug report on the F-Spot bug tracker (i.e. not on the forum or Launchpad) so a developer can work on it?

---

### Post by Rainwolf on 2009-08-05
sure I can post... where?   :)
I'm new to ubuntu and f-spot so forgive my lack of knowledge

---

### Post by directhex on 2009-08-05
> **Rainwolf said:**
> sure I can post... where?   :)
I'm new to ubuntu and f-spot so forgive my lack of knowledge

[http://bugzilla.gnome.org/simple-bug-guide.cgi](http://bugzilla.gnome.org/simple-bug-guide.cgi)

looks like it was reported in Ubuntu as [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/286544](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/286544)

---

