---
title: "Compiling"
date: 2006-12-31
forum: General Help
---

### Post by Ryan H on 2006-12-31
I downloaded Inkscape 0.45 from subversion, but it doesn't have a ./configure file, it has a ./configure.ac file, but that's not what I want. I don't know how to compile without one, is there not one included in Nightly releases?

-Ryan H

---

### Post by taurus on 2006-12-31
Is there a README or INSTALL when you unpack it?

```
ls -la
```

---

### Post by Ryan H on 2006-12-31
Yes but it says it uses the standard ./configure file, which there isn't.

-Ryan H

---

### Post by taurus on 2006-12-31
Then what's the output of that command?

```
ls -la
```

---

### Post by Ryan H on 2006-12-31
> 
total 1128
drwxr-xr-x 11 root root   4096 2006-12-31 16:30 .
drwxr-xr-x  3 root root   4096 2006-12-31 16:30 ..
-rw-r--r--  1 root root   1312 2006-12-31 16:30 AUTHORS
-rwxr-xr-x  1 root root   6273 2006-12-31 16:30 autogen.sh
-rw-r--r--  1 root root  11343 2006-12-31 16:30 build28.xml
-rw-r--r--  1 root root 198456 2006-12-31 16:30 buildtool.cpp
-rw-r--r--  1 root root  15297 2006-12-31 16:30 build.xml
-rw-r--r--  1 root root 399302 2006-12-31 16:30 ChangeLog
-rw-r--r--  1 root root   1238 2006-12-31 16:30 config.h.mingw
-rw-r--r--  1 root root  26834 2006-12-31 16:30 configure.ac
-rw-r--r--  1 root root  18032 2006-12-31 16:30 COPYING
-rw-r--r--  1 root root  26522 2006-12-31 16:30 COPYING.LIB
-rw-r--r--  1 root root    368 2006-12-31 16:30 .cvsignore
drwxr-xr-x  6 root root   4096 2006-12-31 16:30 cxxtest
drwxr-xr-x  3 root root   4096 2006-12-31 16:30 debian
-rwxr-xr-x  1 root root    392 2006-12-31 16:30 delautogen.sh
-rwxr-xr-x  1 root root  10098 2006-12-31 16:30 distro
drwxr-xr-x  4 root root   4096 2006-12-31 16:30 doc
-rwxr-xr-x  1 root root   4416 2006-12-31 16:30 fix-roff-punct
-rw-r--r--  1 root root   3417 2006-12-31 16:30 HACKING.de.txt
-rw-r--r--  1 root root   4126 2006-12-31 16:30 HACKING.fr.txt
-rw-r--r--  1 root root   3652 2006-12-31 16:30 HACKING.it.txt
-rw-r--r--  1 root root   3464 2006-12-31 16:30 HACKING.txt
-rw-r--r--  1 root root   4352 2006-12-31 16:30 Info.plist.in
-rw-r--r--  1 root root    894 2006-12-31 16:30 inkscape16.ico
-rw-r--r--  1 root root    766 2006-12-31 16:30 inkscape32-16.ico
-rw-r--r--  1 root root   3262 2006-12-31 16:30 inkscape32.ico
-rw-r--r--  1 root root    766 2006-12-31 16:30 inkscape32x16col.ico
-rw-r--r--  1 root root  12862 2006-12-31 16:30 inkscape64.ico
-rw-r--r--  1 root root    342 2006-12-31 16:30 inkscape.desktop.in
-rw-r--r--  1 root root  21566 2006-12-31 16:30 inkscape.fr.pod
-rw-r--r--  1 root root  29310 2006-12-31 16:30 inkscape.ico
-rw-r--r--  1 root root     51 2006-12-31 16:30 inkscape.nsi
-rw-r--r--  1 root root   1521 2006-12-31 16:30 inkscape.png
-rw-r--r--  1 root root  19454 2006-12-31 16:30 inkscape.pod
-rw-r--r--  1 root root   3454 2006-12-31 16:30 inkscape.spec.in
-rw-r--r--  1 root root   1625 2006-12-31 16:30 inkview.1.in
-rw-r--r--  1 root root   9378 2006-12-31 16:30 INSTALL
-rw-r--r--  1 root root    299 2006-12-31 16:30 libgc.supp
drwxr-xr-x  3 root root   4096 2006-12-31 16:30 m4
-rw-r--r--  1 root root   6744 2006-12-31 16:30 Makefile.am
-rw-r--r--  1 root root   6827 2006-12-31 16:30 Makefile.mingw
-rw-r--r--  1 root root   5847 2006-12-31 16:30 Makefile.mingw.common
-rw-r--r--  1 root root   5123 2006-12-31 16:30 Makefile.mingw.common.old
-rw-r--r--  1 root root   3102 2006-12-31 16:30 Makefile.mingw.old
-rwxr-xr-x  1 root root    146 2006-12-31 16:30 mingwenv.bat
-rwxr-xr-x  1 root root   1988 2006-12-31 16:30 mkinstalldirs
-rw-r--r--  1 root root  68437 2006-12-31 16:30 NEWS
drwxr-xr-x  6 root root   4096 2006-12-31 16:30 packaging
drwxr-xr-x  3 root root   4096 2006-12-31 16:30 po
-rw-r--r--  1 root root   2846 2006-12-31 16:30 README
-rwxr-xr-x  1 root root   1871 2006-12-31 16:30 README.ca.txt
-rw-r--r--  1 root root   1841 2006-12-31 16:30 README.de.txt
-rw-r--r--  1 root root   3236 2006-12-31 16:30 README.es.txt
-rw-r--r--  1 root root   3319 2006-12-31 16:30 README.fr.txt
-rw-r--r--  1 root root   1736 2006-12-31 16:30 README.it.txt
drwxr-xr-x 17 root root   4096 2006-12-31 16:30 share
drwxr-xr-x 33 root root  12288 2006-12-31 16:30 src
drwxr-xr-x  7 root root   4096 2006-12-31 16:30 .svn
-rwxr-xr-x  1 root root   1336 2006-12-31 16:30 tools-version.sh
-rw-r--r--  1 root root   4684 2006-12-31 16:30 TRANSLATORS
-rwxr-xr-x  1 root root   5936 2006-12-31 16:30 utf8-to-roff


-Ryan H

---

### Post by taurus on 2006-12-31
What does the content of INSTALL say?  Probably have to use one of those Makefile.* to build it...

---

### Post by Ryan H on 2006-12-31
> Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002 Free Software
Foundation, Inc. 

   This file is free documentation; the Free Software Foundation gives
unlimited permission to copy, distribute and modify it.

Basic Installation
==================

   If you have problems compiling Inkscape, then see
[http://wiki.inkscape.org/wiki/index.php/CompilingInkscape](http://wiki.inkscape.org/wiki/index.php/CompilingInkscape) .

   The remainder of this file gives generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').

   It can also use an optional file (typically called `config.cache'
and enabled with `--cache-file=config.cache' or simply `-C') that saves
the results of its tests to speed up reconfiguring.  (Caching is
disabled by default to prevent problems with accidental use of stale
cache files.)

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If you are using the cache, and at
some point `config.cache' contains results you don't want to keep, you
may remove or edit it.

   The file `configure.ac' (or `configure.in') is used to create
`configure' by a program called `autoconf'.  You only need
`configure.ac' if you want to change it or regenerate `configure' using
a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  Run `./configure --help'
for details on some of the pertinent environment variables.

   You can give `configure' initial values for configuration parameters
by setting variables in the command line or in the environment.  Here
is an example:

     ./configure CC=c89 CFLAGS=-O2 LIBS=-lposix

   *Note Defining Variables::, for more details.

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not support the `VPATH'
variable, you have to compile the package for one architecture at a
time in the source code directory.  After you have installed the
package for one architecture, use `make distclean' before reconfiguring
for another architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' cannot figure out
automatically, but needs to determine by the type of machine the package
will run on.  Usually, assuming the package is built to be run on the
_same_ architectures, `configure' can figure that out, but if it prints
a message saying it cannot guess the machine type, give it the
`--build=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name which has the form:

     CPU-COMPANY-SYSTEM

where SYSTEM can have one of these forms:

     OS KERNEL-OS

   See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the machine type.

   If you are _building_ compiler tools for cross-compiling, you should
use the `--target=TYPE' option to select the type of system they will
produce code for.

   If you want to _use_ a cross compiler, that generates code for a
platform different from the build platform, you should specify the
"host" platform (i.e., that on which the generated programs will
eventually be run) with `--host=TYPE'.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Defining Variables
==================

   Variables not defined in a site shell script can be set in the
environment passed to `configure'.  However, some packages may run
configure again during the build, and the customized values of these
variables may be lost.  In order to avoid this problem, you should set
them in the `configure' command line, using `VAR=value'.  For example:

     ./configure CC=/usr/local2/bin/gcc

will cause the specified gcc to be used as the C compiler (unless it is
overridden in the site shell script).

`configure' Invocation
======================

   `configure' recognizes the following options to control how it
operates.

`--help'
`-h'
     Print a summary of the options to `configure', and exit.

`--version'
`-V'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`--cache-file=FILE'
     Enable the cache: use and save the results of the tests in FILE,
     traditionally `config.cache'.  FILE defaults to `/dev/null' to
     disable caching.

`--config-cache'
`-C'
     Alias for `--cache-file=config.cache'.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`configure' also accepts some other, not widely useful, options.  Run
`configure --help' for more details.


Apparently I have to use a program called autoconf to make the configure file.

-Ryan H

Edit: When I tried autoconf it game me this:
> configure.ac:12: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:22: error: possibly undefined macro: AM_CONFIG_HEADER
configure.ac:24: error: possibly undefined macro: AC_PROG_INTLTOOL
configure.ac:28: error: possibly undefined macro: AM_PROG_CC_C_O
configure.ac:44: error: possibly undefined macro: AM_PROG_CC_STDC
configure.ac:45: error: possibly undefined macro: AM_PROG_AS
configure.ac:84: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:206: error: possibly undefined macro: AM_CONDITIONAL


I don't know what to do.

---

### Post by Ryan H on 2007-01-01
What am I doing wrong?

-Ryan H

---

### Post by moma on 2007-01-01
You have pulled down a CVS (or SVN) version of the source.  It will not have ./configure script because it's not prepared for direct installation.

First run autogen.sh and then ./configure && make && sudo make install.

$ [COLOR="Green"]./autogen.sh[/COLOR]

Notice that ./autogen.sh and ./configure will check and report any missing dependencies (packages). Eg. It will need  "automake1.8".  The Ubuntu's dafault automake v1.9.6 will not work with that version of inkscape.
$ [COLOR="SeaGreen"]sudo apt-get install automake1.8  libgc-dev  liblcms1-dev  libxslt1-dev  [/COLOR]

etc.

Check also what extra options the ./configure can take.
$ [COLOR="SeaGreen"]./configure --help [/COLOR]

If you must repeat the ./configure && make several times, run "make clean" first. It wipes out all compiled object files and libraries (from the local directory) so you can safely re-compile it.

---

### Post by Ryan H on 2007-01-02
Thank you! That worked like a charm. :)

-Ryan H

---

