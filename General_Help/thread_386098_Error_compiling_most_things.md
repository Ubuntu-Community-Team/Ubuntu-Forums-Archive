---
title: "Error compiling most things"
date: 2007-03-16
forum: General Help
---

### Post by NeuroticKiss on 2007-03-16
I get this same error when trying to compile almost anything. I've searched and cannot find a solution. Whenever I try compiling I get a list of "error: expected ‘)’ before ‘*’ token" errors and the final error is "error: old-style parameter declarations in prototyped function definition"

Does anyone have any idea how to fix this? I'm running Edgy.

---

### Post by NeuroticKiss on 2007-03-17
I'm trying to install affinity-0.1.

Here is the output of autogen.sh. Here is a link to the whole output of make as it is too big to attach or paste: [LINK]("http://www.systemcafe.net/makeerror.txt")
Any help would be greatly appreciated.
```
~/affinity-0.1$ sh autogen.sh 
/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.9...

  testing automake-1.9... 
found 1.9.6

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.6.6

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.0

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`autogen.sh' command line.


Processing ./configure.ac


Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running aclocal-1.9...


Running autoconf...


Running autoheader...


Running automake-1.9...


Running ./configure --enable-maintainer-mode ...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking for intltool >= 0.34... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for TRACKER... checking for BEAGLE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating affinity-preferences/Makefile
config.status: creating data/Makefile
config.status: creating data/actions/Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

affinity-0.1:

        prefix:                 /usr/local
        source code location:   .
        compiler:               gcc
        tracker support:        no
        beagle support:         yes

Now type `make' to compile affinity
sasha@slevin:~/affinity-0.1$ 

```

---

