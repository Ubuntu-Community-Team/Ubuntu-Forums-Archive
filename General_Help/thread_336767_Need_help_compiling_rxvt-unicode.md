---
title: "Need help compiling rxvt-unicode"
date: 2007-01-12
forum: General Help
---

### Post by hanzomon4 on 2007-01-12
I'm having trouble compiling rxvt-unicode, it will ./autogen.sh ./configure just fine but it dies with an error during make.. 
[list][*]Here's the ./configure output```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu

configuring for rxvt 8.1

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for working libsupc++... ok
checking for setlocale... yes
checking for gethostbyname... yes
checking for socket... yes
checking for mv... /bin/mv
checking for cp... /bin/cp
checking for ln... /bin/ln
checking for sed... /bin/sed
checking for echo... /bin/echo
checking for cmp... /usr/bin/cmp
checking for tic... /usr/bin/tic
checking how to run the C++ preprocessor... g++ -E
checking for X... libraries , headers 
checking for gethostbyname... (cached) yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for libXpm... -I, -L/usr/lib
checking for sys/wait.h that is POSIX.1 compatible... yes
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
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for unistd.h... (cached) yes
checking sys/byteorder.h usability... no
checking sys/byteorder.h presence... no
checking for sys/byteorder.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking sys/strredir.h usability... no
checking sys/strredir.h presence... no
checking for sys/strredir.h... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for stdint.h... (cached) yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking cwchar usability... yes
checking cwchar presence... yes
checking for cwchar... yes
checking clocale usability... yes
checking clocale presence... yes
checking for clocale... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether termios.h and sys/ioctl.h may both be included... yes
checking for -rpath dynamic library path recording... no
checking for -R dynamic library path recording... no
checking for XPointer... yes
checking for XLIB_ILLEGAL_ACCESS... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for mode_t... yes
checking for pid_t... yes
checking for uid_t in sys/types.h... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long long... yes
checking size of long long... 8
checking for int *... yes
checking size of int *... 4
checking for int16_t... yes
checking for uint16_t... yes
checking for int32_t... yes
checking for uint32_t... yes
checking return type of signal handlers... void
checking for unsetenv... yes
checking for setutent... yes
checking for on_exit... yes
checking for ttyslot... yes
checking for updwtmp... yes
checking for updwtmpx... yes
checking utmp.h usability... yes
checking utmp.h presence... yes
checking for utmp.h... yes
checking utmpx.h usability... yes
checking utmpx.h presence... yes
checking for utmpx.h... yes
checking lastlog.h usability... yes
checking lastlog.h presence... yes
checking for lastlog.h... yes
checking for utmp.h... (cached) yes
checking for struct utmp... yes
checking for ut_host in utmp struct... yes
checking for ut_pid in utmp struct... yes
checking for utmpx.h... (cached) yes
checking for struct utmpx... yes
checking for host in utmpx struct... yes
checking for session in utmpx struct... yes
checking for struct lastlog... yes
checking for struct lastlogx... no
checking where utmp is located... 
checking where utmpx is located... 
checking where wtmp is located... 
checking where wtmpx is located... 
checking where lastlog is located... 
checking where lastlogx is located... 
checking where ttys/ttytab is located... 
checking for working Xlocale... no
checking for working X setlocale... no
checking for working plain setlocale... yes
checking for working nl_langinfo... yes
checking for unix-compliant filehandle passing ability... yes
checking for broken XIM callback... no
checking pty.h usability... yes
checking pty.h presence... yes
checking for pty.h... yes
checking util.h usability... no
checking util.h presence... no
checking for util.h... no
checking libutil.h usability... no
checking libutil.h presence... no
checking for libutil.h... no
checking for sys/ioctl.h... (cached) yes
checking sys/stropts.h usability... yes
checking sys/stropts.h presence... yes
checking for sys/stropts.h... yes
checking for revoke... no
checking for _getpty... no
checking for getpt... yes
checking for posix_openpt... yes
checking for isastream... yes
checking for setuid... yes
checking for seteuid... yes
checking for setreuid... yes
checking for setresuid... yes
checking for /dev/ptym/clone... no
checking for /dev/ptc... no
checking for /dev/ptmx... yes
checking for UNIX98 ptys... yes
checking for tty group... no
checking for pkg-config... /usr/bin/pkg-config
checking X11/Xft/Xft.h usability... yes
checking X11/Xft/Xft.h presence... yes
checking for X11/Xft/Xft.h... yes
checking for XftDrawString32 in -lXft... yes
checking for perl5... no
checking for perl... /usr/bin/perl
checking for /usr/bin/perl suitability... ok
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: creating src/rxvtlib.h
config.status: creating config.h
config.status: config.h is unchanged
Configuration:

  Rxvt version:               8.1 : 2006-12-07
  Source code location:       .
  Install path:               /usr//bin
  Compiler:                   g++
  Compiler flags:             -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs
  Linker:                     gcc
  Xpm library:                -L/usr/lib -lXpm
  default resource name:      urxvt
  resource class:             URxvt
  resource class fallback:    Rxvt

  embedded perl:              yes

.----------------------------------------------------------------.
. WARNING: --enable-xim was specified however the locale support .
.          functions could not be found.                         .
.          XIM is now being DISABLED!                            .
.----------------------------------------------------------------.
*** Optionally check src/feature.h for further, rarely used options ***


```[*]And this is the output from make```
~/Desktop/rxvt-unicode-8.1$ make
make[1]: Entering directory `/home/hanzomon4/Desktop/rxvt-unicode-8.1/src'
g++ -DHAVE_CONFIG_H  -I/usr/include/freetype2    -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c rxvt.C
g++ -DHAVE_CONFIG_H  -I/usr/include/freetype2    -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c command.C
g++ -DHAVE_CONFIG_H  -I/usr/include/freetype2    -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c rxvtfont.C
g++ -DHAVE_CONFIG_H  -I/usr/include/freetype2    -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c init.C
g++ -DHAVE_CONFIG_H  -I/usr/include/freetype2    -g -O3 -fno-threadsafe-statics -fno-enforce-eh-specs  -DDEBUG_STRICT   -I.. -I. -I. -c logging.C
In file included from logging.C:40:
ptytty.h:36:4: error: #error cannot build with utmp support - no utmp or utmpx struct found
logging.C: In member function ‘virtual void ptytty_unix::login(int, bool, const char*)’:
logging.C:96: error: ‘ut_id’ was not declared in this scope
logging.C:98: error: ‘ut_id’ was not declared in this scope
make[1]: *** [logging.o] Error 1
make[1]: Leaving directory `/home/hanzomon4/Desktop/rxvt-unicode-8.1/src'
make: *** [all] Error 1

```[/list]

I'm lost, so any ideas?

---

### Post by hanzomon4 on 2007-01-13
BuMP!

---

### Post by tom-g on 2007-01-13
I don't have the sources for the package . But from the error you posted, I can see that the compiler does not know the definition of utmp and utmpx. From the run of the configure script I can see that those structs are supported. Sorry I just found that the standard includes are not installed on my system - fresh install. It could be that include directive or flag is missing. Where is the file utmp.h and utmpx.h ?

---

### Post by sh0x on 2007-02-01
Hi Folks,

i've got exactly the same problem. Do you already know how to solve the problem? Maybe it's needed to install additional header files? But which ones?

Best regards,
Peter

---

