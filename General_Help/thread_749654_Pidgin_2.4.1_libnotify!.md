---
title: "Pidgin 2.4.1 libnotify!"
date: 2008-04-08
forum: General Help
---

### Post by XeiaieX on 2008-04-08
hello again, i have another question.

ive tried just about everything and cannot figure this out.

i have compiled and installed the newest pidgin 2.4.1 and it works perfecty.

however, i have tried multiple times to install the libnotify plugin and while it installs every time without error, it never shows up in the plugins list in pidgin!

it used to work for me on the older pidgin....

anyone know whats up?

thanks.

---

### Post by atomkarinca on 2008-04-08
You can try installing it from the repositories:

```
sudo apt-get install pidgin-libnotify
```

---

### Post by XeiaieX on 2008-04-08
> **atomkarinca said:**
> You can try installing it from the repositories:

```
sudo apt-get install pidgin-libnotify
```

i guess i should have specified. :s

i have done that, and compiled it as well. both install it without error, but it doesnt show up in the pidgin plugins list.

thanks again!

---

### Post by XeiaieX on 2008-04-08
im surprised no one has an answer to this yet. usually these forums are bumpin!

im not complaining, just saying :)

---

### Post by XeiaieX on 2008-04-09
................ bump i guess

---

### Post by XeiaieX on 2008-04-09
i have all the libraries needed installed because i thought that maybe the libnotify windows werent able to draw becuase i was missing something.... so i dont know whats wrong, the only thing that makes sense to me is either its a bug in pidgin 2.4.1 or somethign was missing when i compiled it.... i couldnt find anything on google about my plm...

could it possibly be that somethign was missing, that i didnt have something required by libnotify when i compiled/installed it?

here is my ./configure output:

__  __    _       _     __  __
\ \/ /___(_) __ _(_) ___\ \/ /
 \  // _ \ |/ _` | |/ _ \\  / 
 /  \  __/ | (_| | |  __//  \ 
/_/\_\___|_|\__,_|_|\___/_/\_\
                              
xeiaiex@xlubeartu:~$ cd Desktop/pidgin-2.4.1/ && sudo ./configure
[sudo] password for xeiaiex:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
checking the maximum length of command line arguments... 32768
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
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for PANGO... yes
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... no
no
checking for GTKSPELL... yes
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for SQLITE3... no
no
checking for initscr in -lncursesw... no
checking for update_panels in -lpanelw... no
checking for initscr in -lncurses... no
checking for update_panels in -lpanel... no
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... no
no
checking for MEANWHILE... no
checking for AVAHI... no
checking avahi-client/client.h usability... no
checking avahi-client/client.h presence... no
checking for avahi-client/client.h... no
checking avahi-glib/glib-malloc.h usability... no
checking avahi-glib/glib-malloc.h presence... no
checking for avahi-glib/glib-malloc.h... no
checking for avahi_client_new in -lavahi-client... no
checking for SILC... no
checking for SILC... no
checking for SILC... no
checking for GADU... no
no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... /usr/local/bin/pidgin
checking for dbus-binding-tool... yes
checking for DBUS... yes
checking for python... /usr/bin/python
checking location of the D-Bus services directory... /usr/share/dbus-1/services
Building with D-Bus support
checking for python... /usr/bin/python
checking for Python compile flags... Can't find Python.h
checking for perl... /usr/bin/perl
checking for Perl compile flags... ok
checking for libperl... checking for perl_run... no
checking EXTERN.h usability... yes
checking EXTERN.h presence... yes
checking for EXTERN.h... yes
checking for perl.h... yes
checking for GnuTLS includes... ""
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for GnuTLS libraries... yes
checking for Mozilla nspr4 includes in ... ""
checking nspr.h usability... no
checking nspr.h presence... no
checking for nspr.h... no
checking prio.h usability... no
checking prio.h presence... no
checking for prio.h... no
checking for Mozilla nspr4 libraries... no
checking for Mozilla nss3 includes... no
checking for Mozilla nss libraries... no
checking for tclConfig.sh... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for random... yes
checking for strchr... yes
checking for strerror... yes
checking for vprintf... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sgtty.h usability... yes
checking sgtty.h presence... yes
checking for sgtty.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/msgbuf.h usability... no
checking sys/msgbuf.h presence... no
checking for sys/msgbuf.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking for sys/utsname.h... (cached) yes
checking for sys/wait.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for sys/sysctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for struct tm.tm_zone... yes
checking for timezone external... yes
checking for altzone external... no
checking for daylight external... yes
checking for tm_gmtoff in struct tm... yes
checking for CHECK... no
checking for check - version >= 0.8.2... no
*** Could not run check test program, checking why...
*** The test program failed to compile or link. See the file config.log for
*** the exact error that occured.
checking for doxygen... false
configure: WARNING: *** Doxygen not found, docs will not be available
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Doxyfile
config.status: creating doc/Makefile
config.status: creating doc/pidgin.1
config.status: creating doc/finch.1
config.status: creating m4macros/Makefile
config.status: creating pidgin.apspec
config.status: creating pidgin/Makefile
config.status: creating pidgin/pidgin.pc
config.status: creating pidgin/pidgin-uninstalled.pc
config.status: creating pidgin/pixmaps/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/qq/Makefile
config.status: creating pidgin/pixmaps/emotes/default/24/Makefile
config.status: creating pidgin/pixmaps/emotes/none/Makefile
config.status: creating pidgin/plugins/Makefile
config.status: creating pidgin/plugins/cap/Makefile
config.status: creating pidgin/plugins/gestures/Makefile
config.status: creating pidgin/plugins/gevolution/Makefile
config.status: creating pidgin/plugins/musicmessaging/Makefile
config.status: creating pidgin/plugins/perl/Makefile
config.status: creating pidgin/plugins/perl/common/Makefile.PL
config.status: creating pidgin/plugins/ticker/Makefile
config.status: creating libpurple/example/Makefile
config.status: creating libpurple/gconf/Makefile
config.status: creating libpurple/purple.pc
config.status: creating libpurple/purple-uninstalled.pc
config.status: creating libpurple/plugins/Makefile
config.status: creating libpurple/plugins/mono/Makefile
config.status: creating libpurple/plugins/mono/api/Makefile
config.status: creating libpurple/plugins/mono/loader/Makefile
config.status: creating libpurple/plugins/perl/Makefile
config.status: creating libpurple/plugins/perl/common/Makefile.PL
config.status: creating libpurple/plugins/ssl/Makefile
config.status: creating libpurple/plugins/tcl/Makefile
config.status: creating libpurple/Makefile
config.status: creating libpurple/protocols/Makefile
config.status: creating libpurple/protocols/bonjour/Makefile
config.status: creating libpurple/protocols/gg/Makefile
config.status: creating libpurple/protocols/irc/Makefile
config.status: creating libpurple/protocols/jabber/Makefile
config.status: creating libpurple/protocols/msn/Makefile
config.status: creating libpurple/protocols/msnp9/Makefile
config.status: creating libpurple/protocols/myspace/Makefile
config.status: creating libpurple/protocols/novell/Makefile
config.status: creating libpurple/protocols/null/Makefile
config.status: creating libpurple/protocols/oscar/Makefile
config.status: creating libpurple/protocols/qq/Makefile
config.status: creating libpurple/protocols/sametime/Makefile
config.status: creating libpurple/protocols/silc/Makefile
config.status: creating libpurple/protocols/silc10/Makefile
config.status: creating libpurple/protocols/simple/Makefile
config.status: creating libpurple/protocols/toc/Makefile
config.status: creating libpurple/protocols/yahoo/Makefile
config.status: creating libpurple/protocols/zephyr/Makefile
config.status: creating libpurple/tests/Makefile
config.status: creating libpurple/purple.h
config.status: creating libpurple/version.h
config.status: creating share/sounds/Makefile
config.status: creating share/ca-certs/Makefile
config.status: creating finch/finch.pc
config.status: creating finch/Makefile
config.status: creating finch/libgnt/Makefile
config.status: creating finch/libgnt/gnt.pc
config.status: creating finch/libgnt/wms/Makefile
config.status: creating finch/plugins/Makefile
config.status: creating po/Makefile.in
config.status: creating pidgin.spec
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

pidgin 2.4.1

Build GTK+ 2.x UI............. : yes
Build console UI.............. : no
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : gg irc jabber msnp9 myspace novell oscar qq simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : no
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Install pixmaps............... : yes
Install translations.......... : yes
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.
Warning: You have an old copy of Pidgin at /usr/local/bin/pidgin.

configure complete, now type 'make'

xeiaiex@xlubeartu:~/Desktop/pidgin-2.4.1$


---
another weird thing is see at the bottom is says "Warning: You have an old copy of Pidgin at /usr/local/bin/pidgin." .... it is 2.4.1, the newst. i wonder if it didnt completely remove when i removed the version that comes with gutsy? i removed it with --purge tho :s

thanks for any help

---

### Post by XeiaieX on 2008-04-10
i completely removed it again and that file in /bin/ and now not only does libnotify not work, but pidgin is SUPER unstable and keeps crashing.. sigh

---

### Post by XeiaieX on 2008-04-10
im gonna format.

i dont like not knowing my os is 100% perfect and knowing everything thats going on. i cant live with it like this even if i fixed the plm.

i am surprised tho that no one has gotten to this... usually this forum is on bump!

---

### Post by XeiaieX on 2008-04-11
im running 2.2.1 right now and libnotify works. i will try upgrading to 2.41 the day before hardy is released because i dotn wanna chance this not working and makign a mess. there isnt a difference really in the 2 versions anyway.

---

### Post by XeiaieX on 2008-04-13
i wonder why no one ver replied on this.

---

### Post by dasunst3r on 2008-04-13
Sorry that nobody is replying to your messages, but people don't know what they could do to help you, including myself.  How about you execute pidgin in the terminal and paste what kind of messages it spews out.  Maybe that'll give us some insight of what's going on.

---

### Post by XeiaieX on 2008-04-14
> **dasunst3r said:**
> Sorry that nobody is replying to your messages, but people don't know what they could do to help you, including myself.  How about you execute pidgin in the terminal and paste what kind of messages it spews out.  Maybe that'll give us some insight of what's going on.

Hey thanks for the reply. It's nice to see that there is at least life in here! :)

That is a good idea however I am currently running version 2.2.1 with everything working until the Hardy release.

Thanks for the reply and the suggestion!

---

