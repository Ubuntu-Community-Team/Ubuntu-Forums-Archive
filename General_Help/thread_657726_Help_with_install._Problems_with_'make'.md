---
title: "Help with install. Problems with 'make'"
date: 2008-01-03
forum: General Help
---

### Post by whytheam on 2008-01-03
I am trying to install lolifox [[link]("http://linux.softpedia.com/get/Internet/HTTP-WWW-/lolifox-23991.shtml")]. I fallowed the README as it said until it told me to execute './mozilla' which did not exists. I then ran './configure' everything checked out until I entered 'make' It outputted  "make: *** No targets specified and no makefile found.  Stop."  

I can't seem to find a solution, please help.

---

### Post by reckless2k2 on 2008-01-03
once you extracted the tar file there should be some README file in there with install instructions. that should help out. 

make sure that any install is done with "sudo" as well.

---

### Post by logos34 on 2008-01-03
> **whytheam said:**
> I am trying to install lolifox [[link]("http://linux.softpedia.com/get/Internet/HTTP-WWW-/lolifox-23991.shtml")]. I fallowed the README as it said until it told me to execute './mozilla' which did not exists. I then ran './configure' everything checked out until I entered 'make' It outputted  "make: *** No targets specified and no makefile found.  Stop."  

I can't seem to find a solution, please help.

Can you post the README you're going by? (post it as an attachment)

---

### Post by steveneddy on 2008-01-03
You have to cd, or Change Directory and be in the correct directory to get this to work correctly.

For instance:

```

cd /home**/your_user_name**/Desktop/lolifox-0.3.6.source/mozilla

```

if you downloaded it to your desktop.

You must also, before you get started, right click the .tar.gz file and select Extract Here.

Then, cd to the folder path above and

./configure
sudo make
sudo make install

Good Luck.

---

### Post by whytheam on 2008-01-03
I've done all of that and it still wont install. 

> whytheam@whytheam:~$ cd mozilla
whytheam@whytheam:~/mozilla$ cd mozilla
whytheam@whytheam:~/mozilla/mozilla$ sudo ./configure
[sudo] password for whytheam:
Adding configure options from ./.mozconfig:
  --enable-application=browser
  --enable-optimize
  --enable-strip
  --enable-strip-libs
  --disable-debug
  --disable-tests
  --enable-static
  --disable-shared
  --enable-svg
  --enable-canvas
  --enable-update-packaging
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... gawk
checking for nsinstall... no
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
checking for minimum required perl version >= 5.004... 5.008008
checking for full perl installation... yes
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
checking for 64-bit OS... no
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
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... yes
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
checking for X11/XKBlib.h... yes
checking for sys/statvfs.h... yes
checking for sys/statfs.h... yes
checking for sys/vfs.h... yes
checking for sys/mount.h... yes
checking for mmintrin.h... no
checking for new... yes
checking for sys/cdefs.h... yes
checking for gethostbyname_r in -lc_r... no
checking for atan in -lm... yes
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
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
checking whether va_lists can be copied by value... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 1.3.7... yes
checking MOZ_GTK2_CFLAGS... -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  
checking MOZ_GTK2_LIBS...   -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for xft... yes
checking MOZ_XFT_CFLAGS... -I/usr/include/freetype2  
checking MOZ_XFT_LIBS...   -lXft -lfontconfig  
checking for pango >= 1.1.0... yes
checking _PANGOCHK_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS...   -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for XpGetPrinterList in -lXp... no
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... checking for gconf-2.0 >= 1.2.1... checking for libgnome-2.0 >= 2.0... checking for libgnomeui-2.0 >= 2.2.0... configure: warning: Cannot build gnomevfs without required libraries. Removing gnomevfs from MOZ_EXTENSIONS.
checking for valid optimization flags... yes
checking for __builtin_vec_new... no
checking for __builtin_vec_delete... no
checking for __builtin_new... no
checking for __builtin_delete... no
checking for __pure_virtual... no
checking for __cxa_demangle... yes
checking for gcc -pipe support... cat: dummy-hello.s: No such file or directory
yes
checking whether compiler supports -Wno-long-long... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0... checking for glib-config... no
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
whytheam@whytheam:~/mozilla/mozilla$ sudo make
make: *** No targets specified and no makefile found.  Stop.
whytheam@whytheam:~/mozilla/mozilla$ sudo make install
make: *** No rule to make target `install'.  Stop.
whytheam@whytheam:~/mozilla/mozilla$ 



---

### Post by steveneddy on 2008-01-03
Looks like dependency hell.

You need to install every piece of software where it says no in the terminal.

libIDL-2.0
GLIB 1.2.0

The ReadMe file has the dependencies you need to install.

---

### Post by whytheam on 2008-01-03
Ok next newest problem. When I run it as lolifox-0.3.6 It says Error KDesktop Unknown Host lolifox-0.3.6.

---

### Post by geirha on 2008-01-04
> **whytheam said:**
> Ok next newest problem. When I run it as lolifox-0.3.6 It says Error KDesktop Unknown Host lolifox-0.3.6.

run it as lolifox? what do you mean?

And those dependencies the configure-script failed with, running this should install those:
```
sudo aptitude install libidl-dev libglib1.2-dev
```

---

### Post by whytheam on 2008-01-04
> **geirha said:**
> run it as lolifox? what do you mean?

And those dependencies the configure-script failed with, running this should install those:
```
sudo aptitude install libidl-dev libglib1.2-dev
```

Yes run it as lolifox and thoes didn't help it wtill wont work.

---

### Post by geirha on 2008-01-04
Does the configure script give the same errors now, or new ones?

EDIT: I think I understand what you mean by "run it as lolifox" now. You mean to say you run it in the lolifox-something directory. "Run it as" implies that you run the command as a user called lolifox-something.

---

### Post by whytheam on 2008-01-06
I click on run program, I enter  lolifox-0.3.6 and it says, "Unknown host lolifox-0.3.6"

---

