---
title: "Fluxbuntu - Kazehakase 0.5.2 - &quot;no makefile found&quot;"
date: 2008-02-04
forum: General Help
---

### Post by throwingks on 2008-02-04
I currently have Kazehakase 0.4.3 on Fluxbuntu and I am trying to upgrade to 0.5.2. According to the INSTALL file, all I need to do is:```
1. ./configure
2. make
-optional make check
3. make install
-optional make clean
-optional make distclean
```
I get through step 1 just fine. Step 2 is where I get an error. It reads:> make: *** No targets specified and no makefile found. Stop.
I have build-essential installed, and I have no idea where to go from here.

Thanks in advance for any input.

---

### Post by taurus on 2008-02-04
Can you post the whole output of this command?

```
./configure
```

---

### Post by throwingks on 2008-02-04
> **taurus said:**
> Can you post the whole output of this command?

```
./configure
```
I used sudo to run it and tee to log it.
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
checking for some Win32 platform... no
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
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
checking whether to build static libraries... no
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
checking for pkg-config... /usr/bin/pkg-config
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gawk... (cached) mawk
checking pkg-config is at least version 0.9.0... yes
checking for gecko engine... not found
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.12.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for glib-mkenums... /usr/bin/glib-mkenums
checking for NRCIT... no
checking for GTKIEEMBED... no
checking for libgnutls-config... /usr/bin/libgnutls-config
checking for libgnutls - version >= 1.2.0... yes
checking for X... no
checking for SmcSaveYourselfDone in -lSM... no
checking X11/SM/SMlib.h usability... no
checking X11/SM/SMlib.h presence... no
checking for X11/SM/SMlib.h... no
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking for main in -le... no
checking for main in -links... no
checking winsock2.h usability... no
checking winsock2.h presence... no
checking for winsock2.h... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzread in -lz... yes
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for libintl.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for an ANSI C-conforming const... yes
checking for setlocale... yes
checking for strchr... yes
checking for strtol... yes
checking for uname... yes
checking for memmove... yes
checking for strerror... yes
checking for strptime... yes
checking for ruby... /usr/bin/ruby
checking for ruby.h... no
checking for rgettext... none
checking for EST... no
checking for ANTHY... no
checking for mecab-config... none
This was also on the end but not included in the log for some reason.
> configure: error: conditional "HAVE_NSIBADCERTLISTENER_H" was never defined.
Usually this means the macro was only invoked conditionally.

---

### Post by taurus on 2008-02-04
As you can see from the last line, there is an error from ./configure.

```
checking for mecab-config... none
```
Therefore, there is no Makefiles created so "make" won't work.  Looking at synaptic, I find libmecab1 & libmecab-dev so you may want to install both and run your ./configure again.

---

### Post by throwingks on 2008-02-04
> **taurus said:**
> As you can see from the last line, there is an error from ./configure.

```
checking for mecab-config... none
```
Therefore, there is no Makefiles created so "make" won't work.  Looking at synaptic, I find libmecab1 & libmecab-dev so you may want to install both and run your ./configure again.

I ran mecab-config from the terminal all by itself just to see if any helpful error messages popped up. It told me to apt-get libmecab-dev. So, I Installed from Synaptic, and it also selected libmecab1. :)

That last line has now changed to:> mecab-config... /usr/bin/mecab-config

There is still no make. I am now looking into problems with my GTK+.

Anything else that you see? Thanks for your help so far.

---

### Post by mc4man on 2008-02-04
adding firefox-dev should get you thru configure
I also had gawk and libgtk2.0-dev and some others i tried - let me know and I'll backtrack

edit: got a successful make and checkinstall - whether any options should be added to ./configure don't know - seems to work fine as is

---

### Post by throwingks on 2008-02-04
> **mc4man said:**
> adding firefox-dev should get you thru configure
I also had gawk and libgtk2.0-dev and some others i tried - let me know and I'll backtrack

edit: got a successful make and checkinstall - whether any options should be added to ./configure don't know - seems to work fine as is

Firefox-dev installed a few others along with it, and that did get me through configure. Now, make is giving me problems.> make  all-recursive
make[1]: Entering directory `/home/throwingks/kazehakase-0.5.2'
Making all in po
make[2]: Entering directory `/home/throwingks/kazehakase-0.5.2/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/throwingks/kazehakase-0.5.2/po'
Making all in src
make[2]: Entering directory `/home/throwingks/kazehakase-0.5.2/src'
/usr/bin/glib-genmarshal ../src/kz-marshalers.list --header --body --prefix=_kz_marshal > kz-marshalers.c
/usr/bin/glib-genmarshal ../src/kz-marshalers.list --header --prefix=_kz_marshal > kz-marshalers.h
(cd . && \
	  include_headers="" && \
	  for h in kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h; do \
	    include_headers="${include_headers}#include \"${h}\"\n"; \
	  done && \
	  /usr/bin/glib-mkenums \
	    --fhead "#include \"kz-enum-types.h\"\n${include_headers}" \
	    --fprod "\n/* enumerations from \"@filename@\" */" \
	    --vhead "GType\n@enum_name@_get_type (void)\n{\n  static GType etype = 0;\n  if (etype == 0) {\n    static const G@Type@Value values[] = {" 	\
	    --vprod "      { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
	    --vtail "      { 0, NULL, NULL }\n    };\n    etype = g_@type@_register_static (\"@EnumName@\", values);\n  }\n  return etype;\n}\n" \
	    kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h) > tmp-kz-enum-types.c && \
	(cmp -s tmp-kz-enum-types.c kz-enum-types.c || \
	  cp tmp-kz-enum-types.c kz-enum-types.c ) && \
	rm -f tmp-kz-enum-types.c && \
	echo timestamp > stamp-kz-enum-types-c
(cd . && \
	  mark="__`echo kz-enum-types | sed -e 's/-/_/g' | tr a-z A-Z`_H__" && \
	  /usr/bin/glib-mkenums \
	    --fhead "#ifndef ${mark}\n#define ${mark}\n\n#include <glib-object.h>\n\nG_BEGIN_DECLS\n" \
	    --fprod "/* enumerations from \"@filename@\" */\n" \
	    --vhead "GType @enum_name@_get_type (void);\n#define KZ_TYPE_@ENUMSHORT@ (@enum_name@_get_type())\n" 	\
	    --ftail "G_END_DECLS\n\n#endif /* ${mark} */" \
	    kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h) > tmp-kz-enum-types.h && \
	(cmp -s tmp-kz-enum-types.h kz-enum-types.h || \
	  cp tmp-kz-enum-types.h kz-enum-types.h) && \
	rm -f tmp-kz-enum-types.h && \
	echo timestamp > stamp-kz-enum-types-h
make  all-recursive
make[3]: Entering directory `/home/throwingks/kazehakase-0.5.2/src'
Making all in missing
make[4]: Entering directory `/home/throwingks/kazehakase-0.5.2/src/missing'
make  all-am
make[5]: Entering directory `/home/throwingks/kazehakase-0.5.2/src/missing'
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wcast-align   -o libkzmissing.la    
mkdir .libs
ar cru .libs/libkzmissing.a
ranlib .libs/libkzmissing.a
creating libkzmissing.la
(cd .libs && rm -f libkzmissing.la && ln -s ../libkzmissing.la libkzmissing.la)
make[5]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src/missing'
make[4]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src/missing'
Making all in utils
make[4]: Entering directory `/home/throwingks/kazehakase-0.5.2/src/utils'
make  all-am
make[5]: Entering directory `/home/throwingks/kazehakase-0.5.2/src/utils'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..  -I../../src -I../../src/bookmarks -I../../src/libegg/pixbufthumbnail -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DG_LOG_DOMAIN=\"Kazehakase-Utils\" -DG_DISABLE_DEPRECATED=1   -g -O2 -Wall -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wcast-align -MT glib-utils.lo -MD -MP -MF .deps/glib-utils.Tpo -c -o glib-utils.lo glib-utils.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I../.. -I../../src -I../../src/bookmarks -I../../src/libegg/pixbufthumbnail -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DG_LOG_DOMAIN=\"Kazehakase-Utils\" -DG_DISABLE_DEPRECATED=1 -g -O2 -Wall -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wcast-align -MT glib-utils.lo -MD -MP -MF .deps/glib-utils.Tpo -c glib-utils.c  -fPIC -DPIC -o .libs/glib-utils.o
make[5]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src/utils'
make[4]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src/utils'
make[3]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src'
make[2]: Leaving directory `/home/throwingks/kazehakase-0.5.2/src'
make[1]: Leaving directory `/home/throwingks/kazehakase-0.5.2'


---

### Post by mc4man on 2008-02-04
let me look thru my history - can you post last 12 lines or so from make
fresh install 3 days ago  - culled out stuff I don't think matters
Installed the following packages: for this
```
irb1.8 (1.8.6.36-1ubuntu3)
libgettext-ruby-util (1.9.0-1)
libreadline-ruby1.8 (1.8.6.36-1ubuntu3)
gawk (1:3.1.5.dfsg-4ubuntu1)
libatk1-ruby1.8 (0.16.0-3ubuntu1)
libcairo-ruby1.8 (1.5.0-1)
libgdk-pixbuf2-ruby1.8 (0.16.0-3ubuntu1)
libgettext-ruby1.8 (1.9.0-1)
libglib2-ruby1.8 (0.16.0-3ubuntu1)
libgtk2-ruby (0.16.0-3ubuntu1)
libgtk2-ruby1.8 (0.16.0-3ubuntu1)
libmozjs0d (1.8.1.4-2ubuntu5)
libpango1-ruby1.8 (0.16.0-3ubuntu1)
libruby1.8 (1.8.6.36-1ubuntu3)
libxul-common (1.8.1.4-2ubuntu5)
libxul0d (1.8.1.4-2ubuntu5)
ruby (1.8.2-1)
ruby1.8 (1.8.6.36-1ubuntu3)
libatk1.0-dev (1.20.0-0ubuntu1)
libcairo2-dev (1.4.10-1ubuntu4.4)
libgtk2.0-dev (2.12.0-1ubuntu3)
libpango1.0-dev (1.18.3-0ubuntu1)
libxcomposite-dev (1:0.4.0-0ubuntu1)
libxdamage-dev (1:1.1.1-3)
x11proto-composite-dev (1:0.4-0ubuntu1)
x11proto-damage-dev (1:1.1.0-2build1)
```
previous for other stuff
```
build-essential (11.3ubuntu1)
dpkg-dev (1.14.5ubuntu16)
g++ (4:4.1.2-9ubuntu2)
g++-4.1 (4.1.2-16ubuntu2)
libc6-dev (2.6.1-1ubuntu10)
libstdc++6-4.1-dev (4.1.2-16ubuntu2)
linux-libc-dev (2.6.22-14.47)
patch (2.5.9-4)

```

---

### Post by throwingks on 2008-02-04
^ Posted entire make log above. I didn't see your post until after a refresh.

---

### Post by mc4man on 2008-02-04
missed your post also, Look thru my list - I don't know enough unless I see something obvious, your make is failing early (took several minutes)
I'm using ubuntu Gutsy (if that matters - don't think so)

---

### Post by mc4man on 2008-02-04
hope your good to go , here's 1st 60 lines if you need cross comparison  - will delete if not needed/ useful  
```
doug@doug-desktop:~/Desktop/kazehakase-0.5.2$ make
make  all-recursive
make[1]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2'
Making all in po
make[2]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/po'
file=`echo cs | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file cs.po
file=`echo fr | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file fr.po
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ja.po
file=`echo ru | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ru.po
make[2]: Leaving directory `/home/doug/Desktop/kazehakase-0.5.2/po'
Making all in src
make[2]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src'
/usr/bin/glib-genmarshal ../src/kz-marshalers.list --header --body --prefix=_kz_marshal > kz-marshalers.c
/usr/bin/glib-genmarshal ../src/kz-marshalers.list --header --prefix=_kz_marshal > kz-marshalers.h
(cd . && \
          include_headers="" && \
          for h in kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h; do \
            include_headers="${include_headers}#include \"${h}\"\n"; \
          done && \
          /usr/bin/glib-mkenums \
            --fhead "#include \"kz-enum-types.h\"\n${include_headers}" \
            --fprod "\n/* enumerations from \"@filename@\" */" \
            --vhead "GType\n@enum_name@_get_type (void)\n{\n  static GType etype = 0;\n  if (etype == 0) {\n    static const G@Type@Value values[] = {"        \
            --vprod "      { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
            --vtail "      { 0, NULL, NULL }\n    };\n    etype = g_@type@_register_static (\"@EnumName@\", values);\n  }\n  return etype;\n}\n" \
            kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h) > tmp-kz-enum-types.c && \
        (cmp -s tmp-kz-enum-types.c kz-enum-types.c || \
          cp tmp-kz-enum-types.c kz-enum-types.c ) && \
        rm -f tmp-kz-enum-types.c && \
        echo timestamp > stamp-kz-enum-types-c
(cd . && \
          mark="__`echo kz-enum-types | sed -e 's/-/_/g' | tr a-z A-Z`_H__" && \
          /usr/bin/glib-mkenums \
            --fhead "#ifndef ${mark}\n#define ${mark}\n\n#include <glib-object.h>\n\nG_BEGIN_DECLS\n" \
            --fprod "/* enumerations from \"@filename@\" */\n" \
            --vhead "GType @enum_name@_get_type (void);\n#define KZ_TYPE_@ENUMSHORT@ (@enum_name@_get_type())\n"        \
            --ftail "G_END_DECLS\n\n#endif /* ${mark} */" \
            kazehakase.h kz-app.h kz-module.h kz-module-impl.h kz-embed.h kz-embed-event.h kz-embed-prefs.h kz-gesture.h kz-tab-label.h kz-icons.h kz-prefs-win.h kz-sidebar.h kz-window.h kz-profile.h kz-xml.h kz-downloader.h kz-downloader-group.h kz-download-box.h kz-feed-info.h kz-navi.h kz-notebook.h kz-proxy-menu.h kz-proxy-item.h kz-favicon.h kz-langinfo.h kz-thumbnails-view.h kz-autoscroller.h kz-popup-preview.h kz-popup-tablist.h kz-search.h kz-statusbar.h kz-migemo.h kz-ext.h) > tmp-kz-enum-types.h && \
        (cmp -s tmp-kz-enum-types.h kz-enum-types.h || \
          cp tmp-kz-enum-types.h kz-enum-types.h) && \
        rm -f tmp-kz-enum-types.h && \
        echo timestamp > stamp-kz-enum-types-h
make  all-recursive
make[3]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src'
Making all in missing
make[4]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src/missing'
make  all-am
make[5]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src/missing'
/bin/bash ../../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wcast-align   -o libkzmissing.la    
mkdir .libs
ar cru .libs/libkzmissing.a
ranlib .libs/libkzmissing.a
creating libkzmissing.la
(cd .libs && rm -f libkzmissing.la && ln -s ../libkzmissing.la libkzmissing.la)
make[5]: Leaving directory `/home/doug/Desktop/kazehakase-0.5.2/src/missing'
make[4]: Leaving directory `/home/doug/Desktop/kazehakase-0.5.2/src/missing'
Making all in utils
make[4]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src/utils'
make  all-am
make[5]: Entering directory `/home/doug/Desktop/kazehakase-0.5.2/src/utils'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -I../../src -I../../src/bookmarks -I../../src/libegg/pixbufthumbnail -DGTK_DISABLE_DEPRECATED=1 -DGDK_DISABLE_DEPRECATED=1 -DG_LOG_DOMAIN=\"Kazehakase-Utils\" -DG_DISABLE_DEPRECATED=1   -g -O2 -Wall -Wmissing-declarations -Wmissing-prototypes -Wpointer-arith -Wcast-align -MT glib-utils.lo -MD -MP -MF .deps/glib-utils.Tpo -c -o glib-utils.lo glib-utils.c

```

---

### Post by throwingks on 2008-02-06
That helps a little, but I do not understand the errors I am receiving from my log. As far as I can tell it just quits. Am I missing anything obvious?

---

### Post by mc4man on 2008-02-06
Your definitely missing some build dependencies - did you look thru what I posted. All I had previously on this install was build depends for k9copy and f4linux. I added a number of packages based on what i saw in the configure. (I also installed/uninstalled  the repo version prior to doing anything)
I'll do a search for build depends and post back

edit:ck. here also [https://launchpad.net/ubuntu/gutsy/+source/kazehakase](https://launchpad.net/ubuntu/gutsy/+source/kazehakase)
if still no go try
```
sudo aptitude install libdvdread-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev libavcodec-dev libavformat-dev
```
k9 depends - won't hurt to have

---

### Post by zarathustra on 2008-02-07
I don't think the configure error is anything to do with mecab but something to do with xulrunner 1.9, which this version of Kazehakase detects. When I first try running the configure command, it went fine but only detected the stable 1.8 xulrunner, and I realised I hadn't installed the development packages for 1.9 and I then got the same error as you after running configure again once I had done installed the,

---

