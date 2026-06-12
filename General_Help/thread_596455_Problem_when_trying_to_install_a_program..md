---
title: "Problem when trying to install a program."
date: 2007-10-29
forum: General Help
---

### Post by dljesse on 2007-10-29
I get this error every time:

jesse@jesse-desktop:~/mozilla$ ./configure
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
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... no
checking for mawk... mawk
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
checking for pkg-config... /usr/bin/pkg-config
[COLOR="Red"]checking for gtk+-2.0 >= 1.3.7... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.[/COLOR]
jesse@jesse-desktop:~/mozilla$

---

### Post by Maestro23 on 2007-10-29
What exactly are you trying to install?

*And any time you are dealing with source code, you need build-essential installed.

> sudo apt-get install build-essential

---

### Post by dljesse on 2007-10-29
I have build essential already, the program I'm trying to install is a different version of firefox.
If you want to you can take a look at it right here: [http://lolifox.com/download/](http://lolifox.com/download/)

---

### Post by Maestro23 on 2007-10-29
> **dljesse said:**
> I have build essential already, the program I'm trying to install is a different version of firefox.
If you want to you can take a look at it right here: [http://lolifox.com/download/](http://lolifox.com/download/)

Which one are you attempting to install?

Edit: Taurus is on it.

---

### Post by taurus on 2007-10-29
Try installing both** libgtk** and** libgtk-dev** packages using synaptic.  Then, see if ./configure works this time.

---

### Post by dljesse on 2007-10-29
I ran "make" after I did "./configure" and then I get this huge list of errors.

In file included from gtk2xtbin.c:46:
gtk2xtbin.h:78: error: expected specifier-qualifier-list before &#8216;Widget&#8217;
gtk2xtbin.h:104: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;String&#8217;
gtk2xtbin.h:113: error: expected specifier-qualifier-list before &#8216;XtTranslations&#8217;
gtk2xtbin.h:117: warning: struct has no members
gtk2xtbin.h:120: error: expected specifier-qualifier-list before &#8216;Widget&#8217;
gtk2xtbin.h:149: warning: struct has no members
gtk2xtbin.c:61:23: error: X11/Shell.h: No such file or directory
gtk2xtbin.c:63:28: error: X11/StringDefs.h: No such file or directory
gtk2xtbin.c:89: error: expected &#8216;)&#8217; before &#8216;xtplug&#8217;
gtk2xtbin.c:91: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:94: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:97: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:100: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:101: error: expected &#8216;)&#8217; before &#8216;treeroot&#8217;
gtk2xtbin.c:102: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:120: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
gtk2xtbin.c: In function &#8216;xt_event_dispatch&#8217;:
gtk2xtbin.c:163: error: &#8216;XtAppContext&#8217; undeclared (first use in this function)
gtk2xtbin.c:163: error: (Each undeclared identifier is reported only once
gtk2xtbin.c:163: error: for each function it appears in.)
gtk2xtbin.c:163: error: expected &#8216;;&#8217; before &#8216;ac&#8217;
gtk2xtbin.c:164: warning: ISO C90 forbids mixed declarations and code
gtk2xtbin.c:166: error: &#8216;ac&#8217; undeclared (first use in this function)
gtk2xtbin.c:166: warning: implicit declaration of function &#8216;XtDisplayToApplicationContext&#8217;
gtk2xtbin.c:176: warning: implicit declaration of function &#8216;XtAppProcessEvent&#8217;
gtk2xtbin.c:176: error: &#8216;XtIMXEvent&#8217; undeclared (first use in this function)
gtk2xtbin.c: At top level:
gtk2xtbin.c:188: warning: initialization from incompatible pointer type
gtk2xtbin.c: In function &#8216;xt_event_polling_timer_callback&#8217;:
gtk2xtbin.c:197: error: &#8216;XtAppContext&#8217; undeclared (first use in this function)
gtk2xtbin.c:197: error: expected &#8216;;&#8217; before &#8216;ac&#8217;
gtk2xtbin.c:198: warning: ISO C90 forbids mixed declarations and code
gtk2xtbin.c:201: error: &#8216;ac&#8217; undeclared (first use in this function)
gtk2xtbin.c:209: warning: implicit declaration of function &#8216;XtAppPending&#8217;
gtk2xtbin.c:210: error: &#8216;XtIMAll&#8217; undeclared (first use in this function)
gtk2xtbin.c: In function &#8216;gtk_xtbin_realize&#8217;:
gtk2xtbin.c:298: warning: implicit declaration of function &#8216;XtWindow&#8217;
gtk2xtbin.c:298: error: &#8216;XtClient&#8217; has no member named &#8216;child_widget&#8217;
gtk2xtbin.c: At top level:
gtk2xtbin.c:309: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;String&#8217;
gtk2xtbin.c: In function &#8216;gtk_xtbin_new&#8217;:
gtk2xtbin.c:320: error: &#8216;f&#8217; undeclared (first use in this function)
gtk2xtbin.c:321: error: &#8216;fallback&#8217; undeclared (first use in this function)
gtk2xtbin.c: In function &#8216;gtk_xtbin_resize&#8217;:
gtk2xtbin.c:408: error: &#8216;Arg&#8217; undeclared (first use in this function)
gtk2xtbin.c:408: error: expected &#8216;;&#8217; before &#8216;args&#8217;
gtk2xtbin.c:409: warning: ISO C90 forbids mixed declarations and code
gtk2xtbin.c:416: warning: implicit declaration of function &#8216;XtSetArg&#8217;
gtk2xtbin.c:416: error: &#8216;args&#8217; undeclared (first use in this function)
gtk2xtbin.c:416: error: &#8216;XtNheight&#8217; undeclared (first use in this function)
gtk2xtbin.c:417: error: &#8216;XtNwidth&#8217; undeclared (first use in this function)
gtk2xtbin.c:418: warning: implicit declaration of function &#8216;XtSetValues&#8217;
gtk2xtbin.c:418: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c: In function &#8216;xt_client_init&#8217;:
gtk2xtbin.c:504: error: &#8216;XtAppContext&#8217; undeclared (first use in this function)
gtk2xtbin.c:504: error: expected &#8216;;&#8217; before &#8216;app_context&#8217;
gtk2xtbin.c:505: warning: ISO C90 forbids mixed declarations and code
gtk2xtbin.c:511: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:512: error: &#8216;XtClient&#8217; has no member named &#8216;child_widget&#8217;
gtk2xtbin.c:514: error: &#8216;XtClient&#8217; has no member named &#8216;xtvisual&#8217;
gtk2xtbin.c:515: error: &#8216;XtClient&#8217; has no member named &#8216;xtcolormap&#8217;
gtk2xtbin.c:516: error: &#8216;XtClient&#8217; has no member named &#8216;xtdepth&#8217;
gtk2xtbin.c:522: warning: implicit declaration of function &#8216;XtToolkitInitialize&#8217;
gtk2xtbin.c:523: error: &#8216;app_context&#8217; undeclared (first use in this function)
gtk2xtbin.c:523: warning: implicit declaration of function &#8216;XtCreateApplicationContext&#8217;
gtk2xtbin.c:524: error: &#8216;fallback&#8217; undeclared (first use in this function)
gtk2xtbin.c:525: warning: implicit declaration of function &#8216;XtAppSetFallbackResources&#8217;
gtk2xtbin.c:527: warning: implicit declaration of function &#8216;XtOpenDisplay&#8217;
gtk2xtbin.c:528: warning: assignment makes pointer from integer without a cast
gtk2xtbin.c:533: error: &#8216;XtClient&#8217; has no member named &#8216;xtvisual&#8217;
gtk2xtbin.c:534: error: &#8216;XtClient&#8217; has no member named &#8216;xtcolormap&#8217;
gtk2xtbin.c:535: error: &#8216;XtClient&#8217; has no member named &#8216;xtdepth&#8217;
gtk2xtbin.c: In function &#8216;xt_client_create&#8217;:
gtk2xtbin.c:547: error: &#8216;Arg&#8217; undeclared (first use in this function)
gtk2xtbin.c:547: error: expected &#8216;;&#8217; before &#8216;args&#8217;
gtk2xtbin.c:548: error: &#8216;Widget&#8217; undeclared (first use in this function)
gtk2xtbin.c:548: error: expected &#8216;;&#8217; before &#8216;child_widget&#8217;
gtk2xtbin.c:549: error: expected &#8216;;&#8217; before &#8216;top_widget&#8217;
gtk2xtbin.c:554: error: &#8216;top_widget&#8217; undeclared (first use in this function)
gtk2xtbin.c:554: warning: implicit declaration of function &#8216;XtAppCreateShell&#8217;
gtk2xtbin.c:555: error: &#8216;applicationShellWidgetClass&#8217; undeclared (first use in this function)
gtk2xtbin.c:558: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:562: error: &#8216;args&#8217; undeclared (first use in this function)
gtk2xtbin.c:562: error: &#8216;XtNheight&#8217; undeclared (first use in this function)
gtk2xtbin.c:563: error: &#8216;XtNwidth&#8217; undeclared (first use in this function)
gtk2xtbin.c:566: error: &#8216;child_widget&#8217; undeclared (first use in this function)
gtk2xtbin.c:566: warning: implicit declaration of function &#8216;XtVaCreateWidget&#8217;
gtk2xtbin.c:567: error: &#8216;compositeWidgetClass&#8217; undeclared (first use in this function)
gtk2xtbin.c:573: error: &#8216;XtNvisual&#8217; undeclared (first use in this function)
gtk2xtbin.c:573: error: &#8216;XtClient&#8217; has no member named &#8216;xtvisual&#8217;
gtk2xtbin.c:574: error: &#8216;XtNdepth&#8217; undeclared (first use in this function)
gtk2xtbin.c:574: error: &#8216;XtClient&#8217; has no member named &#8216;xtdepth&#8217;
gtk2xtbin.c:575: error: &#8216;XtNcolormap&#8217; undeclared (first use in this function)
gtk2xtbin.c:575: error: &#8216;XtClient&#8217; has no member named &#8216;xtcolormap&#8217;
gtk2xtbin.c:576: error: &#8216;XtNborderWidth&#8217; undeclared (first use in this function)
gtk2xtbin.c:580: error: &#8216;XtClient&#8217; has no member named &#8216;oldwindow&#8217;
gtk2xtbin.c:585: warning: implicit declaration of function &#8216;XtRegisterDrawable&#8217;
gtk2xtbin.c:592: warning: implicit declaration of function &#8216;XtRealizeWidget&#8217;
gtk2xtbin.c:598: warning: implicit declaration of function &#8216;xt_client_set_info&#8217;
gtk2xtbin.c:600: warning: implicit declaration of function &#8216;XtManageChild&#8217;
gtk2xtbin.c:601: error: &#8216;XtClient&#8217; has no member named &#8216;child_widget&#8217;
gtk2xtbin.c:604: warning: implicit declaration of function &#8216;XtAddEventHandler&#8217;
gtk2xtbin.c:607: error: &#8216;XtEventHandler&#8217; undeclared (first use in this function)
gtk2xtbin.c:607: error: expected &#8216;)&#8217; before &#8216;xt_client_event_handler&#8217;
gtk2xtbin.c:611: error: expected &#8216;)&#8217; before &#8216;xt_client_focus_listener&#8217;
gtk2xtbin.c: In function &#8216;xt_client_unrealize&#8217;:
gtk2xtbin.c:620: warning: implicit declaration of function &#8216;XtUnregisterDrawable&#8217;
gtk2xtbin.c:621: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:631: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:631: error: &#8216;XtClient&#8217; has no member named &#8216;oldwindow&#8217;
gtk2xtbin.c:632: warning: implicit declaration of function &#8216;XtUnrealizeWidget&#8217;
gtk2xtbin.c:632: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c: In function &#8216;xt_client_destroy&#8217;:
gtk2xtbin.c:638: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:639: warning: implicit declaration of function &#8216;XtRemoveEventHandler&#8217;
gtk2xtbin.c:639: error: &#8216;XtClient&#8217; has no member named &#8216;child_widget&#8217;
gtk2xtbin.c:640: error: &#8216;XtEventHandler&#8217; undeclared (first use in this function)
gtk2xtbin.c:640: error: expected &#8216;)&#8217; before &#8216;xt_client_event_handler&#8217;
gtk2xtbin.c:641: warning: implicit declaration of function &#8216;XtDestroyWidget&#8217;
gtk2xtbin.c:641: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:642: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c: At top level:
gtk2xtbin.c:647: error: expected &#8216;)&#8217; before &#8216;xtplug&#8217;
gtk2xtbin.c:663: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:724: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c: In function &#8216;send_xembed_message&#8217;:
gtk2xtbin.c:771: error: &#8216;XtClient&#8217; has no member named &#8216;top_widget&#8217;
gtk2xtbin.c:775: warning: implicit declaration of function &#8216;memset&#8217;
gtk2xtbin.c:775: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
gtk2xtbin.c: At top level:
gtk2xtbin.c:824: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:869: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:892: error: expected &#8216;)&#8217; before &#8216;w&#8217;
gtk2xtbin.c:904: error: expected &#8216;)&#8217; before &#8216;treeroot&#8217;
make[2]: *** [gtk2xtbin.o] Error 1
make[2]: Leaving directory `/home/jesse/mozilla/widget/src/gtkxtbin'
make[1]: *** [tier_9] Error 2
make[1]: Leaving directory `/home/jesse/mozilla'
make: *** [default] Error 2

---

