---
title: "Almost there! Please help to finally compile!"
date: 2008-07-07
forum: General Help
---

### Post by s3a on 2008-07-07
I have build-essential. I have underlined what I think the problem is, I just don't know what to do about it.

[B]deniz@deniz-desktop:~$ cd ~/Desktop/icecat-3-g1
deniz@deniz-desktop:~/Desktop/icecat-3-g1$ ./configure
Adding configure options from ./.mozconfig:
  --disable-ldap
  --disable-calendar
  --disable-mailnews
  --disable-chatzilla
  --enable-extensions=default cookie permissions python/xpcom spellcheck
  --enable-crypto
  --disable-composer
  --enable-single-profile
  --disable-profilesharing
  --disable-shared
  --enable-static
  --disable-debug
  --enable-toolkit-cairo-gtk2
  --enable-default-toolkit=cairo-gtk2
  --enable-xft
  --disable-freetype2
  --disable-tests
  --disable-mochitest
  --disable-debug
  --disable-accessibility
  --enable-strip
  --disable-toolkit-qt
  --prefix=/usr/local
  --disable-pango
  --disable-xprint
  --with-user-appdir=.gnuzilla
  --disable-xinerama
  --with-system-zlib
  --with-system-jpeg
  --enable-svg
  --enable-svg-renderer=cairo
  --enable-application=browser
  --enable-system-cairo
  --disable-negotiateauth
  --disable-installer
  --disable-updater
  --disable-strip
  --disable-strip-libs
  --disable-elf-dynstr-gc
  --with-distribution-id=org.gnu.gnuzilla
  --disable-crashreporter
  --disable-libxul
  --with-branding=browser/branding/unofficial
  --disable-official-branding
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$ ./configure
Adding configure options from ./.mozconfig:
  --disable-ldap
  --disable-calendar
  --disable-mailnews
  --disable-chatzilla
  --enable-extensions=default cookie permissions python/xpcom spellcheck
  --enable-crypto
  --disable-composer
  --enable-single-profile
  --disable-profilesharing
  --disable-shared
  --enable-static
  --disable-debug
  --enable-toolkit-cairo-gtk2
  --enable-default-toolkit=cairo-gtk2
  --enable-xft
  --disable-freetype2
  --disable-tests
  --disable-mochitest
  --disable-debug
  --disable-accessibility
  --enable-strip
  --disable-toolkit-qt
  --prefix=/usr/local
  --disable-pango
  --disable-xprint
  --with-user-appdir=.gnuzilla
  --disable-xinerama
  --with-system-zlib
  --with-system-jpeg
  --enable-svg
  --enable-svg-renderer=cairo
  --enable-application=browser
  --enable-system-cairo
  --disable-negotiateauth
  --disable-installer
  --disable-updater
  --disable-strip
  --disable-strip-libs
  --disable-elf-dynstr-gc
  --with-distribution-id=org.gnu.gnuzilla
  --disable-crashreporter
  --disable-libxul
  --with-branding=browser/branding/unofficial
  --disable-official-branding
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking for as... /usr/bin/as
checking for ar... ar
checking for ld... ld
checking for strip... strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for minimum required perl version >= 5.006... 5.008008
checking for full perl installation... yes
checking for python... /usr/bin/python
PYTHON=/usr/bin/python
checking for nsinstall... no
checking for doxygen... :
checking for whoami... /usr/bin/whoami
checking for autoconf... :
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for makedepend... /usr/bin/makedepend
checking for xargs... /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... no
checking whether ld has archive extraction flags... yes
checking that static assertion macros used in autoconf tests work... yes
checking for 64-bit OS... yes
checking for ANSI C header files... yes
checking for working const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for st_blksize in struct stat... yes
checking for siginfo_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for int64... no
checking for uint... yes
checking for uint_t... no
checking for uint16_t... no
checking for uname.domainname... yes
checking for uname.__domainname... no
checking for usable wchar_t (2 bytes, unsigned)... no
checking for compiler -fshort-wchar option... yes
checking for visibility(hidden) attribute... yes
checking for visibility(default) attribute... yes
checking for visibility pragma support... yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for sys/byteorder.h... no
checking for compat.h... no
checking for getopt.h... yes
checking for sys/bitypes.h... yes
checking for memory.h... yes
checking for unistd.h... yes
checking for gnu/libc-version.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for X11/XKBlib.h... no
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... yes
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking for dladdr... yes
checking for socket in -lsocket... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... no
checking for 8-bit clean memcmp... yes
checking for random... yes
checking for strerror... yes
checking for lchown... yes
checking for fchmod... yes
checking for snprintf... yes
checking for statvfs... yes
checking for memmove... yes
checking for rint... yes
checking for stat64... yes
checking for lstat64... yes
checking for truncate64... yes
checking for statvfs64... yes
checking for flockfile... yes
checking for getpagesize... yes
checking for localtime_r... yes
checking for strtok_r... yes
checking for wcrtomb... yes
checking for mbrtowc... yes
checking for res_ninit()... yes
checking for gnu_get_libc_version()... yes
checking for iconv in -lc... yes
checking for iconv()... yes
checking for iconv() with const input... no
checking for nl_langinfo and CODESET... yes
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... no
checking for C++ exceptions flag... -fno-exceptions
checking for gcc 3.0 ABI... yes
checking for C++ "explicit" keyword... yes
checking for C++ "typename" keyword... yes
checking for modern C++ template specialization syntax support... yes
checking whether partial template specialization works... yes
checking whether operators must be re-defined for templates derived from templates... no
checking whether we need to cast a derived template to pass as its base class... no
checking whether the compiler can resolve const ambiguities for templates... yes
checking whether the C++ "using" keyword can change access... yes
checking whether the C++ "using" keyword resolves ambiguity... yes
checking for "std::" namespace... yes
checking whether standard template operator!=() is ambiguous... unambiguous
checking for C++ reinterpret_cast... yes
checking for C++ dynamic_cast to void*... yes
checking whether C++ requires implementation of unused virtual methods... yes
checking for trouble comparing to zero near std::operator!=()... no
checking for LC_MESSAGES... yes
checking for jpeg_destroy_compress in -ljpeg... no
checking for gzread in -lz... yes
checking if app-specific confvars.sh exists... ./browser/confvars.sh
checking for pkg-config... /usr/bin/pkg-config
[U]checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gtk+-unix-print-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-unix-print-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-unix-print-2.0' found Package gdk-x11-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-x11-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-x11-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$[/B][/U]

---

### Post by lisati on 2008-07-07
Try ```
sudo aptitude install build-essential
``` and then retry your installation

---

### Post by s3a on 2008-07-07
I specifically mentioned that I did that.

---

### Post by s3a on 2008-07-07
For some reason "sudo aptitude install build-essential" asked me to obtain more packages although I've already done "sudo apt-get install build-essential."

However the following is my second attempt and I still have the problem:

[B]deniz@deniz-desktop:~/Desktop/icecat-3-g1$ sudo aptitude install build-essential
[sudo] password for deniz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  gnash-common 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4092kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 127284 files and directories currently installed.)
Removing gnash-common ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
deniz@deniz-desktop:~/Desktop/icecat-3-g1$ ./configure
Adding configure options from ./.mozconfig:
  --disable-ldap
  --disable-calendar
  --disable-mailnews
  --disable-chatzilla
  --enable-extensions=default cookie permissions python/xpcom spellcheck
  --enable-crypto
  --disable-composer
  --enable-single-profile
  --disable-profilesharing
  --disable-shared
  --enable-static
  --disable-debug
  --enable-toolkit-cairo-gtk2
  --enable-default-toolkit=cairo-gtk2
  --enable-xft
  --disable-freetype2
  --disable-tests
  --disable-mochitest
  --disable-debug
  --disable-accessibility
  --enable-strip
  --disable-toolkit-qt
  --prefix=/usr/local
  --disable-pango
  --disable-xprint
  --with-user-appdir=.gnuzilla
  --disable-xinerama
  --with-system-zlib
  --with-system-jpeg
  --enable-svg
  --enable-svg-renderer=cairo
  --enable-application=browser
  --enable-system-cairo
  --disable-negotiateauth
  --disable-installer
  --disable-updater
  --disable-strip
  --disable-strip-libs
  --disable-elf-dynstr-gc
  --with-distribution-id=org.gnu.gnuzilla
  --disable-crashreporter
  --disable-libxul
  --with-branding=browser/branding/unofficial
  --disable-official-branding
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for c++... c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking for ranlib... ranlib
checking for as... /usr/bin/as
checking for ar... ar
checking for ld... ld
checking for strip... strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... c++ -E
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for minimum required perl version >= 5.006... 5.008008
checking for full perl installation... yes
checking for python... /usr/bin/python
PYTHON=/usr/bin/python
checking for nsinstall... no
checking for doxygen... :
checking for whoami... /usr/bin/whoami
checking for autoconf... :
checking for unzip... /usr/bin/unzip
checking for zip... /usr/bin/zip
checking for makedepend... /usr/bin/makedepend
checking for xargs... /usr/bin/xargs
checking for gmake... no
checking for make... /usr/bin/make
checking for X... no
checking whether ld has archive extraction flags... yes
checking that static assertion macros used in autoconf tests work... yes
checking for 64-bit OS... yes
checking for ANSI C header files... yes
checking for working const... yes
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for st_blksize in struct stat... yes
checking for siginfo_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for int64... no
checking for uint... yes
checking for uint_t... no
checking for uint16_t... no
checking for uname.domainname... yes
checking for uname.__domainname... no
checking for usable wchar_t (2 bytes, unsigned)... no
checking for compiler -fshort-wchar option... yes
checking for visibility(hidden) attribute... yes
checking for visibility(default) attribute... yes
checking for visibility pragma support... yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... no
checking for dirent.h that defines DIR... yes
checking for opendir in -ldir... no
checking for sys/byteorder.h... no
checking for compat.h... no
checking for getopt.h... yes
checking for sys/bitypes.h... yes
checking for memory.h... yes
checking for unistd.h... yes
checking for gnu/libc-version.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for X11/XKBlib.h... no
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... yes
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking for dladdr... yes
checking for socket in -lsocket... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... no
checking for 8-bit clean memcmp... yes
checking for random... yes
checking for strerror... yes
checking for lchown... yes
checking for fchmod... yes
checking for snprintf... yes
checking for statvfs... yes
checking for memmove... yes
checking for rint... yes
checking for stat64... yes
checking for lstat64... yes
checking for truncate64... yes
checking for statvfs64... yes
checking for flockfile... yes
checking for getpagesize... yes
checking for localtime_r... yes
checking for strtok_r... yes
checking for wcrtomb... yes
checking for mbrtowc... yes
checking for res_ninit()... yes
checking for gnu_get_libc_version()... yes
checking for iconv in -lc... yes
checking for iconv()... yes
checking for iconv() with const input... no
checking for nl_langinfo and CODESET... yes
checking for an implementation of va_copy()... yes
checking for an implementation of __va_copy()... yes
checking whether va_lists can be copied by value... no
checking for C++ exceptions flag... -fno-exceptions
checking for gcc 3.0 ABI... yes
checking for C++ "explicit" keyword... yes
checking for C++ "typename" keyword... yes
checking for modern C++ template specialization syntax support... yes
checking whether partial template specialization works... yes
checking whether operators must be re-defined for templates derived from templates... no
checking whether we need to cast a derived template to pass as its base class... no
checking whether the compiler can resolve const ambiguities for templates... yes
checking whether the C++ "using" keyword can change access... yes
checking whether the C++ "using" keyword resolves ambiguity... yes
checking for "std::" namespace... yes
checking whether standard template operator!=() is ambiguous... unambiguous
checking for C++ reinterpret_cast... yes
checking for C++ dynamic_cast to void*... yes
checking whether C++ requires implementation of unused virtual methods... yes
checking for trouble comparing to zero near std::operator!=()... no
checking for LC_MESSAGES... yes
checking for jpeg_destroy_compress in -ljpeg... no
checking for gzread in -lz... yes
checking if app-specific confvars.sh exists... ./browser/confvars.sh
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gtk+-unix-print-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-unix-print-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-unix-print-2.0' found Package gdk-x11-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdk-x11-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gdk-x11-2.0' found Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gobject-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gobject-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gobject-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$[/B]

---

### Post by mc4man on 2008-07-07
You could start by checking/adding libgtk2.0-dev, libglib2.0-dev, libx11-dev
then ck. again. No need to post the complete config. or make , just around where it errors out. Better to put logs, errors, ect. in a code box instead of just pasting into thread (highlight text and use # in toolbar)

---

### Post by s3a on 2008-07-07
This part is giving problems:

checking for gzread in -lz... yes
checking if app-specific confvars.sh exists... ./browser/confvars.sh
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 gdk-x11-2.0 glib-2.0 gobject-2.0... yes
checking MOZ_GTK2_CFLAGS... -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/gtk-unix-print-2.0  
checking MOZ_GTK2_LIBS... -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgmodule-2.0 -ldl -lgobject-2.0 -lglib-2.0  
checking for xft... yes
checking MOZ_XFT_CFLAGS... -I/usr/include/freetype2  
checking MOZ_XFT_LIBS... -lXft -lfontconfig  
checking for pango >= 1.10.0... yes
checking _PANGOCHK_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for pango >= 1.10.0 pangocairo >= 1.10.0 pangoft2 >= 1.10.0... yes
checking MOZ_PANGO_CFLAGS... -DPNG_NO_MMX_CODE -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking MOZ_PANGO_LIBS... -lpangocairo-1.0 -lcairo -lpangoft2-1.0 -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... checking for gconf-2.0 >= 1.2.1... checking for libgnome-2.0 >= 2.0... checking for libgnomeui-2.0 >= 2.2.0... checking for dbus-glib-1 >= 0.60... Package dbus-glib-1 was not found in the pkg-config search path. Perhaps you should add the directory containing `dbus-glib-1.pc' to the PKG_CONFIG_PATH environment variable No package 'dbus-glib-1' found
configure: error: Library requirements (dbus-glib-1 >= 0.60) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$

---

### Post by tamoneya on 2008-07-07
try this:```
sudo apt-get install dbus-glib-1-dev
```Then try tom compile again.

---

### Post by s3a on 2008-07-07
[B]deniz@deniz-desktop:~/Desktop/icecat-3-g1$ sudo apt-get install dbus-glib-1-dev
[sudo] password for deniz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-glib-1-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  libdbus-glib-1-dev
E: Package dbus-glib-1-dev has no installation candidate
deniz@deniz-desktop:~/Desktop/icecat-3-g1$ sudo apt-get install libdbus-glib-1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-qt3support libmysqlclient15off libqt4-core libqt4-gui qt4-qtconfig
  libqt4-sql libpq5 mysql-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdbus-1-dev
The following NEW packages will be installed:
  libdbus-1-dev libdbus-glib-1-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 294kB of archives.
After this operation, 1327kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main libdbus-1-dev 1.1.20-1ubuntu2 [188kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main libdbus-glib-1-dev 0.74-2 [107kB]
Fetched 294kB in 6s (48.1kB/s)                                                 
Selecting previously deselected package libdbus-1-dev.
(Reading database ... 129727 files and directories currently installed.)
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.1.20-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libdbus-glib-1-dev.
Unpacking libdbus-glib-1-dev (from .../libdbus-glib-1-dev_0.74-2_amd64.deb) ...
Setting up moblock (0.9~rc2-11~hardy) ...
 * Starting MoBlock moblock                                              [fail] 
invoke-rc.d: initscript moblock, action "start" failed.
dpkg: error processing moblock (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libdbus-1-dev (1.1.20-1ubuntu2) ...
Setting up libdbus-glib-1-dev (0.74-2) ...
Errors were encountered while processing:
 moblock
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]

_AND_
[B]
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0 glib-2.0 gobject-2.0... checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for libIDL-config... no
checking for libIDL - version >= 0.6.3... no
*** The libIDL-config script installed by libIDL could not be found
*** If libIDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBIDL_CONFIG environment variable to the
*** full path to libIDL-config.
checking for libIDL-2.0 >= 0.8.0... Package libIDL-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libIDL-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libIDL-2.0' found
configure: error: Library requirements (libIDL-2.0 >= 0.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$[/B]

---

### Post by dentaku65 on 2008-07-07
add
```
sudo apt-get install libidl-dev

```
then recompile

Suggestion: in this last case you got this error at the end:
[COLOR="Red"]checking for libIDL-2.0 >= 0.8.0... Package libIDL-2.0 was not found in the pkg-config search path. [/COLOR]

So in case of these errors when compiling try to do a search for the library in the repos in this way:
```
apt-cache search libidl
```
In this case you know the availability of this package with the tail -dev (always you need -dev when compiling something), so you can now install the related package

---

### Post by s3a on 2008-07-07
OMG, lol, it's an ongoing thing where every1 tells me to add some command :(

_Anyway my new problem:_

[B]checking for cairo-xlib-xrender >= 1.6.0... yes
checking CAIRO_XRENDER_CFLAGS... -DPNG_NO_MMX_CODE -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  
checking CAIRO_XRENDER_LIBS... -lXrender -lcairo -lX11  
Building Python extensions using python-2.5 from /usr
configure: error: Could not compile basic X program.
deniz@deniz-desktop:~/Desktop/icecat-3-g1$[/B]

---

### Post by mc4man on 2008-07-08
Just tried building icecat-3-g1, no problems encountered. This is a recent install of hardy but I do have a number of libs and -dev' installed so not exactly sure what your missing. 
What I'd try is running ```
sudo apt-get build-dep firefox
``` You may want to consider for the moment removing moblock, your the second person I've seen recently that had an issue where moblock was involved.
Build info here
[http://developer.mozilla.org/en/docs/Build_Documentation#Build_requirements](http://developer.mozilla.org/en/docs/Build_Documentation#Build_requirements)
[http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options) (not 100% necessary)


are you using this source? (fifth from top, 32M)
[http://gnuzilla.gnu.org/download/](http://gnuzilla.gnu.org/download/)

---

