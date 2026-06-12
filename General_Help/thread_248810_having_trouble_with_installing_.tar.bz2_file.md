---
title: "having trouble with installing .tar.bz2 file"
date: 2006-09-01
forum: General Help
---

### Post by stampit on 2006-09-01
i can't do it.

i did read this section
[https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html](https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html)

and i did read many other posts, but just can't get the hang of installing .tar.bz2 files. actually many other linux files.






this is the installation instruction that came with .tar.bz2 file that i can't follow.

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

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
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

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

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.

---

### Post by mbeierl on 2006-09-05
I think I understand your frustration.  You're trying to install this file, but there doesn't seem to be any documentation on what command to use to install it !?!

The reason is that .tar (which comes originally from Tape ARchive) is actually like a .ZIP file - it is a collection of individual files wrapped up into a single large file.  It must be extracted before it can be used.

Next, the .bz2 extension, also like .ZIP, means that the file has been compressed (to make it smaller) so it needs to be uncompressed before it can be used.

So, nice explanation, but what do you *really* do with this file?

Decompress and extract the contents with this command (from the command line)

tar jxvf filename.tar.bz2

The j means decompress with bzip 2.
The x means extract the files
The v means show the file names as they are being extracted
The f means the next word on the command line is going to be the filename to open.

From there, you can then run the configure, etc, commands that came with the tar.bz2 archive.

Btw, if it is a tar.gz (or .tgz) archive, use

tar zxvf filename.tar.gz

instead.

The z means use gzip to extract the file.

For more information on tar, type man tar.  For a gui version, there is also file-roller.

Hope this helps!

---

### Post by PriceChild on 2006-09-05
once they're extracted, simply run:

./configure
make
checkinstall

I reccoment checkinstall instead of "make install" as it will create a deb package which can really easily be removed using a package manager.

---

### Post by taurus on 2006-09-05
> **PriceChild said:**
> once they're extracted, simply run:

./configure
make
checkinstall

I reccoment checkinstall instead of "make install" as it will create a deb package which can really easily be removed using a package manager.
Better run "sudo checkinstall" since you need to be root to write to your system...

---

### Post by Moonfrost on 2007-12-17
> **mbeierl said:**
> I think I understand your frustration.  You're trying to install this file, but there doesn't seem to be any documentation on what command to use to install it !?!

The reason is that .tar (which comes originally from Tape ARchive) is actually like a .ZIP file - it is a collection of individual files wrapped up into a single large file.  It must be extracted before it can be used.

Next, the .bz2 extension, also like .ZIP, means that the file has been compressed (to make it smaller) so it needs to be uncompressed before it can be used.

So, nice explanation, but what do you *really* do with this file?

Decompress and extract the contents with this command (from the command line)

tar jxvf filename.tar.bz2

The j means decompress with bzip 2.
The x means extract the files
The v means show the file names as they are being extracted
The f means the next word on the command line is going to be the filename to open.

From there, you can then run the configure, etc, commands that came with the tar.bz2 archive.

Btw, if it is a tar.gz (or .tgz) archive, use

tar zxvf filename.tar.gz

instead.

The z means use gzip to extract the file.

For more information on tar, type man tar.  For a gui version, there is also file-roller.

Hope this helps!


Ok I'm kinda of a noob to Linux but I manage very well with everything else (including command line) BUT this is the only thing I can never do...compile...none of those methods work...also, could you be more specific? for example, "make" and the filename don't work at all.../.configure <filename> doesn't do anything for me either...and I can never uncopress it through command line only through GUI since you just double click it like a .zip or .rar...what I'm trying to install is kxmame, a frontend for sdlmame which a multiple arcade emulator...the thing is I can never compile the damn files!! I have a tar.bz2 extension file if you or anybody here could help me it would be very appreciated!

---

### Post by ~LoKe on 2007-12-17
kxmame is in the repositories...

However, to extract a .tar file...open up the terminal and type the following:
(remember to change **filename** to the name of the file)
```
tar jxvf filename.tar.gz2
cd filename
./configure
make
sudo make install
```

---

### Post by Moonfrost on 2007-12-17
> **~LoKe said:**
> kxmame is in the repositories...

However, to extract a .tar file...open up the terminal and type the following:
(remember to change **filename** to the name of the file)
```
tar jxvf filename.tar.gz2
cd filename
./configure
make
sudo make install
```

Yeah I know it is but it's the beta version of 2.0 and it's slightly outdated...the one I have is the latest version so yeah...thanks a lot for the help!

EDIT: Unfortunately, even though I rectified and I put the name of the file exactly how it is...this is what I get

```
<username>@<username>-desktop:~$ tar jxvf kxmame-2.0-svn-sdlmame-20070603.tar.gz2
tar: kxmame-2.0-svn-sdlmame-20070603.tar.gz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

EDIT #2: It was actually tar.bz2 and gz2...but I still get the same thing regardless...

---

### Post by whit on 2007-12-17
> **~LoKe said:**
> 
```
./configure
make
sudo make install
```There's something else needed, though. What packages does Ubuntu need installed so thet ./configure will work? It's not enough to have automake and autoconf. Where can we find instructions to set up Ubuntu so that it will do what every other base install of a Linux system does - namely, allow the standard steps to do custom builds of packages.

I should know this - I've been a Linux sysadmin for 14 years - but since all other Linuxes come with the basic stuff installed, I've never worried about what the components are. Ubuntu is definitely, by default, missing some.

---

### Post by ~LoKe on 2007-12-17
Generally, it's as easy as **sudo apt-get install build-essential**.

As for the OP...you have to pay attention to where you're downloading your files from.  Download them to your HOME directory (/home/username) for easy access, then, with the terminal open, navigate to your home directory simply by typing **cd**.

---

### Post by whit on 2007-12-17
Ah, looks like in my case the packager of the tar left out the "configure" file but then included the "INSTALL" doc that references running "/.configure" which needs that file. (What I'm trying to build is hnb, since the Debian and Ubuntu version has a serious bug, despite patches being in both systems to fix it.)

**Update:** found a yet more recent hnb tar, which mentions that it uses a different build system. But trying to build it leads to "error: curses.h: No such file or directory". What's the Ubuntu way to find out which .deb contains curses.h? A description of the generic method would be useful. Obviously Ubuntu's official policy is to discourage using anything beyond Ubuntu's own .debs. But in a case like this, where those aren't kept up to date, a serious user does need to build stuff.

Answer?: [http://packages.debian.org/](http://packages.debian.org/) - then searching package contents for curses.h lead to libncurses5-dev, which made the package installable. Is there some Ubuntu/Debian way to just get all the standard development libraries onto the system?

---

### Post by Moonfrost on 2007-12-17
> **~LoKe said:**
> kxmame is in the repositories...

However, to extract a .tar file...open up the terminal and type the following:
(remember to change **filename** to the name of the file)
```
tar jxvf filename.tar.gz2
cd filename
./configure
make
sudo make install
```

The command that worked for me is actually:

```
sudo tar -xvf filename.tar.bz2
```

it extracted everything but after that I didn't know what to do...tried

EDIT: This is everything it extracted...

```
kxmame/
kxmame/.svn/
kxmame/.svn/text-base/
kxmame/.svn/prop-base/
kxmame/.svn/props/
kxmame/.svn/tmp/
kxmame/.svn/tmp/text-base/
kxmame/.svn/tmp/prop-base/
kxmame/.svn/tmp/props/
kxmame/.svn/entries
kxmame/.svn/format
kxmame/.svn/all-wcprops
kxmame/trunk/
kxmame/trunk/.svn/
kxmame/trunk/.svn/text-base/
kxmame/trunk/.svn/text-base/Doxyfile.svn-base
kxmame/trunk/.svn/text-base/kxmame.kdevses.svn-base
kxmame/trunk/.svn/text-base/AUTHORS.svn-base
kxmame/trunk/.svn/text-base/ChangeLog.svn-base
kxmame/trunk/.svn/text-base/kxmame.kdevelop.svn-base
kxmame/trunk/.svn/text-base/configure.in.in.svn-base
kxmame/trunk/.svn/text-base/README.svn-base
kxmame/trunk/.svn/text-base/TODO.svn-base
kxmame/trunk/.svn/text-base/INSTALL.svn-base
kxmame/trunk/.svn/text-base/Makefile.cvs.svn-base
kxmame/trunk/.svn/text-base/COPYING.svn-base
kxmame/trunk/.svn/text-base/Makefile.am.svn-base
kxmame/trunk/.svn/text-base/NEWS.svn-base
kxmame/trunk/.svn/text-base/kxmame.kdevelop.pcs.svn-base
kxmame/trunk/.svn/prop-base/
kxmame/trunk/.svn/prop-base/kxmame.kdevelop.pcs.svn-base
kxmame/trunk/.svn/props/
kxmame/trunk/.svn/tmp/
kxmame/trunk/.svn/tmp/text-base/
kxmame/trunk/.svn/tmp/prop-base/
kxmame/trunk/.svn/tmp/props/
kxmame/trunk/.svn/entries
kxmame/trunk/.svn/format
kxmame/trunk/.svn/all-wcprops
kxmame/trunk/src/
kxmame/trunk/src/.svn/
kxmame/trunk/src/.svn/text-base/
kxmame/trunk/src/.svn/text-base/kxmessagebox.cpp.svn-base
kxmame/trunk/src/.svn/text-base/DirTab.ui.svn-base
kxmame/trunk/src/.svn/text-base/soundpref.ui.svn-base
kxmame/trunk/src/.svn/text-base/properties.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmameui.rc.svn-base
kxmame/trunk/src/.svn/text-base/miscpref.ui.svn-base
kxmame/trunk/src/.svn/text-base/game_list.cpp.svn-base
kxmame/trunk/src/.svn/text-base/dirselectiondialog.cpp.svn-base
kxmame/trunk/src/.svn/text-base/x11render.ui.svn-base
kxmame/trunk/src/.svn/text-base/keyboard.h.svn-base
kxmame/trunk/src/.svn/text-base/DisplayPref.ui.svn-base
kxmame/trunk/src/.svn/text-base/gxmame.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmame.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kbookmarkhandler.h.svn-base
kxmame/trunk/src/.svn/text-base/xmame_options.h.svn-base
kxmame/trunk/src/.svn/text-base/ColorListViewItem.h.svn-base
kxmame/trunk/src/.svn/text-base/auditdialog.h.svn-base
kxmame/trunk/src/.svn/text-base/GLrender.ui.svn-base
kxmame/trunk/src/.svn/text-base/kxmamesnaptab.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmameSplash.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmamesnaplabel.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmessagebox.h.svn-base
kxmame/trunk/src/.svn/text-base/progression_window.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmame_joy.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmame.desktop.svn-base
kxmame/trunk/src/.svn/text-base/dirselectiondialog.h.svn-base
kxmame/trunk/src/.svn/text-base/game_list.h.svn-base
kxmame/trunk/src/.svn/text-base/startuppref.ui.svn-base
kxmame/trunk/src/.svn/text-base/sdlrender.ui.svn-base
kxmame/trunk/src/.svn/text-base/gxmame.h.svn-base
kxmame/trunk/src/.svn/text-base/game_options.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmame.h.svn-base
kxmame/trunk/src/.svn/text-base/gui.h.svn-base
kxmame/trunk/src/.svn/text-base/katefileselector.h.svn-base
kxmame/trunk/src/.svn/text-base/kxmamesnaptab.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmame.lsm.svn-base
kxmame/trunk/src/.svn/text-base/pref.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmameSplash.cpp.svn-base
kxmame/trunk/src/.svn/text-base/progress.ui.svn-base
kxmame/trunk/src/.svn/text-base/kxmame_joy.cpp.svn-base
kxmame/trunk/src/.svn/text-base/screentab.cpp.svn-base
kxmame/trunk/src/.svn/text-base/mameio.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmamelogo.h.svn-base
kxmame/trunk/src/.svn/text-base/xmame_executable.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmamesnaplabel.h.svn-base
kxmame/trunk/src/.svn/text-base/vectorpref.ui.svn-base
kxmame/trunk/src/.svn/text-base/koselectaction.h.svn-base
kxmame/trunk/src/.svn/text-base/ctrlpref.ui.svn-base
kxmame/trunk/src/.svn/text-base/io.h.svn-base
kxmame/trunk/src/.svn/text-base/gameinfo.ui.svn-base
kxmame/trunk/src/.svn/text-base/kxmameview.h.svn-base
kxmame/trunk/src/.svn/text-base/main.cpp.svn-base
kxmame/trunk/src/.svn/text-base/katefileselector.cpp.svn-base
kxmame/trunk/src/.svn/text-base/options_string.h.svn-base
kxmame/trunk/src/.svn/text-base/game_options.h.svn-base
kxmame/trunk/src/.svn/text-base/properties.cpp.svn-base
kxmame/trunk/src/.svn/text-base/keyboard.cpp.svn-base
kxmame/trunk/src/.svn/text-base/pref.h.svn-base
kxmame/trunk/src/.svn/text-base/audit.ui.svn-base
kxmame/trunk/src/.svn/text-base/kxmamelogo.cpp.svn-base
kxmame/trunk/src/.svn/text-base/hi32-app-kxmame.png.svn-base
kxmame/trunk/src/.svn/text-base/unzip.c.svn-base
kxmame/trunk/src/.svn/text-base/koselectaction.cpp.svn-base
kxmame/trunk/src/.svn/text-base/hi16-app-kxmame.png.svn-base
kxmame/trunk/src/.svn/text-base/io.cpp.svn-base
kxmame/trunk/src/.svn/text-base/unzip.h.svn-base
kxmame/trunk/src/.svn/text-base/screentab.h.svn-base
kxmame/trunk/src/.svn/text-base/README.svn-base
kxmame/trunk/src/.svn/text-base/kxmameview.cpp.svn-base
kxmame/trunk/src/.svn/text-base/xmame_executable.h.svn-base
kxmame/trunk/src/.svn/text-base/kbookmarkhandler.cpp.svn-base
kxmame/trunk/src/.svn/text-base/options_string.cpp.svn-base
kxmame/trunk/src/.svn/text-base/xmame_options.cpp.svn-base
kxmame/trunk/src/.svn/text-base/ColorListViewItem.cpp.svn-base
kxmame/trunk/src/.svn/text-base/auditdialog.cpp.svn-base
kxmame/trunk/src/.svn/text-base/Makefile.am.svn-base
kxmame/trunk/src/.svn/text-base/common_kxmame.cpp.svn-base
kxmame/trunk/src/.svn/text-base/kxmame_64.png.svn-base
kxmame/trunk/src/.svn/text-base/common.h.svn-base
kxmame/trunk/src/.svn/prop-base/
kxmame/trunk/src/.svn/prop-base/hi32-app-kxmame.png.svn-base
kxmame/trunk/src/.svn/prop-base/hi16-app-kxmame.png.svn-base
kxmame/trunk/src/.svn/prop-base/kxmame_64.png.svn-base
kxmame/trunk/src/.svn/props/
kxmame/trunk/src/.svn/tmp/
kxmame/trunk/src/.svn/tmp/text-base/
kxmame/trunk/src/.svn/tmp/prop-base/
kxmame/trunk/src/.svn/tmp/props/
kxmame/trunk/src/.svn/entries
kxmame/trunk/src/.svn/format
kxmame/trunk/src/.svn/all-wcprops
kxmame/trunk/src/kxmessagebox.cpp
kxmame/trunk/src/DirTab.ui
kxmame/trunk/src/soundpref.ui
kxmame/trunk/src/properties.h
kxmame/trunk/src/kxmameui.rc
kxmame/trunk/src/miscpref.ui
kxmame/trunk/src/game_list.cpp
kxmame/trunk/src/dirselectiondialog.cpp
kxmame/trunk/src/x11render.ui
kxmame/trunk/src/keyboard.h
kxmame/trunk/src/DisplayPref.ui
kxmame/trunk/src/gxmame.cpp
kxmame/trunk/src/kxmame.cpp
kxmame/trunk/src/kbookmarkhandler.h
kxmame/trunk/src/xmame_options.h
kxmame/trunk/src/ColorListViewItem.h
kxmame/trunk/src/auditdialog.h
kxmame/trunk/src/GLrender.ui
kxmame/trunk/src/kxmamesnaptab.h
kxmame/trunk/src/kxmameSplash.h
kxmame/trunk/src/kxmamesnaplabel.cpp
kxmame/trunk/src/kxmessagebox.h
kxmame/trunk/src/progression_window.h
kxmame/trunk/src/kxmame_joy.h
kxmame/trunk/src/kxmame.desktop
kxmame/trunk/src/dirselectiondialog.h
kxmame/trunk/src/game_list.h
kxmame/trunk/src/startuppref.ui
kxmame/trunk/src/sdlrender.ui
kxmame/trunk/src/gxmame.h
kxmame/trunk/src/game_options.cpp
kxmame/trunk/src/kxmame.h
kxmame/trunk/src/gui.h
kxmame/trunk/src/katefileselector.h
kxmame/trunk/src/kxmamesnaptab.cpp
kxmame/trunk/src/kxmame.lsm
kxmame/trunk/src/pref.cpp
kxmame/trunk/src/kxmameSplash.cpp
kxmame/trunk/src/progress.ui
kxmame/trunk/src/kxmame_joy.cpp
kxmame/trunk/src/screentab.cpp
kxmame/trunk/src/mameio.cpp
kxmame/trunk/src/kxmamelogo.h
kxmame/trunk/src/xmame_executable.cpp
kxmame/trunk/src/kxmamesnaplabel.h
kxmame/trunk/src/vectorpref.ui
kxmame/trunk/src/koselectaction.h
kxmame/trunk/src/ctrlpref.ui
kxmame/trunk/src/io.h
kxmame/trunk/src/gameinfo.ui
kxmame/trunk/src/kxmameview.h
kxmame/trunk/src/main.cpp
kxmame/trunk/src/katefileselector.cpp
kxmame/trunk/src/options_string.h
kxmame/trunk/src/game_options.h
kxmame/trunk/src/properties.cpp
kxmame/trunk/src/keyboard.cpp
kxmame/trunk/src/pref.h
kxmame/trunk/src/audit.ui
kxmame/trunk/src/kxmamelogo.cpp
kxmame/trunk/src/hi32-app-kxmame.png
kxmame/trunk/src/unzip.c
kxmame/trunk/src/koselectaction.cpp
kxmame/trunk/src/hi16-app-kxmame.png
kxmame/trunk/src/io.cpp
kxmame/trunk/src/unzip.h
kxmame/trunk/src/screentab.h
kxmame/trunk/src/README
kxmame/trunk/src/kxmameview.cpp
kxmame/trunk/src/xmame_executable.h
kxmame/trunk/src/kbookmarkhandler.cpp
kxmame/trunk/src/options_string.cpp
kxmame/trunk/src/xmame_options.cpp
kxmame/trunk/src/ColorListViewItem.cpp
kxmame/trunk/src/auditdialog.cpp
kxmame/trunk/src/Makefile.am
kxmame/trunk/src/common_kxmame.cpp
kxmame/trunk/src/kxmame_64.png
kxmame/trunk/src/common.h
kxmame/trunk/admin/
kxmame/trunk/admin/.svn/
kxmame/trunk/admin/.svn/text-base/
kxmame/trunk/admin/.svn/text-base/config.pl.svn-base
kxmame/trunk/admin/.svn/text-base/Doxyfile.am.svn-base
kxmame/trunk/admin/.svn/text-base/mkinstalldirs.svn-base
kxmame/trunk/admin/.svn/text-base/Doxyfile.global.svn-base
kxmame/trunk/admin/.svn/text-base/conf.change.pl.svn-base
kxmame/trunk/admin/.svn/text-base/doxygen.sh.svn-base
kxmame/trunk/admin/.svn/text-base/depcomp.svn-base
kxmame/trunk/admin/.svn/text-base/deps.am.svn-base
kxmame/trunk/admin/.svn/text-base/compile.svn-base
kxmame/trunk/admin/.svn/text-base/libtool.m4.in.svn-base
kxmame/trunk/admin/.svn/text-base/bcheck.pl.svn-base
kxmame/trunk/admin/.svn/text-base/config.guess.svn-base
kxmame/trunk/admin/.svn/text-base/debianrules.svn-base
kxmame/trunk/admin/.svn/text-base/config.sub.svn-base
kxmame/trunk/admin/.svn/text-base/ltmain.sh.svn-base
kxmame/trunk/admin/.svn/text-base/detect-autoconf.pl.svn-base
kxmame/trunk/admin/.svn/text-base/am_edit.svn-base
kxmame/trunk/admin/.svn/text-base/cvs.sh.svn-base
kxmame/trunk/admin/.svn/text-base/Makefile.common.svn-base
kxmame/trunk/admin/.svn/text-base/pkg.m4.in.svn-base
kxmame/trunk/admin/.svn/text-base/oldinclude.m4.in.svn-base
kxmame/trunk/admin/.svn/text-base/configure.in.min.svn-base
kxmame/trunk/admin/.svn/text-base/nmcheck.svn-base
kxmame/trunk/admin/.svn/text-base/missing.svn-base
kxmame/trunk/admin/.svn/text-base/acinclude.m4.in.svn-base
kxmame/trunk/admin/.svn/text-base/configure.in.bot.end.svn-base
kxmame/trunk/admin/.svn/text-base/install-sh.svn-base
kxmame/trunk/admin/.svn/text-base/ylwrap.svn-base
kxmame/trunk/admin/.svn/prop-base/
kxmame/trunk/admin/.svn/prop-base/mkinstalldirs.svn-base
kxmame/trunk/admin/.svn/prop-base/Doxyfile.global.svn-base
kxmame/trunk/admin/.svn/prop-base/depcomp.svn-base
kxmame/trunk/admin/.svn/prop-base/compile.svn-base
kxmame/trunk/admin/.svn/prop-base/config.guess.svn-base
kxmame/trunk/admin/.svn/prop-base/debianrules.svn-base
kxmame/trunk/admin/.svn/prop-base/config.sub.svn-base
kxmame/trunk/admin/.svn/prop-base/detect-autoconf.pl.svn-base
kxmame/trunk/admin/.svn/prop-base/nmcheck.svn-base
kxmame/trunk/admin/.svn/prop-base/missing.svn-base
kxmame/trunk/admin/.svn/prop-base/install-sh.svn-base
kxmame/trunk/admin/.svn/prop-base/ylwrap.svn-base
kxmame/trunk/admin/.svn/props/
kxmame/trunk/admin/.svn/tmp/
kxmame/trunk/admin/.svn/tmp/text-base/
kxmame/trunk/admin/.svn/tmp/prop-base/
kxmame/trunk/admin/.svn/tmp/props/
kxmame/trunk/admin/.svn/entries
kxmame/trunk/admin/.svn/format
kxmame/trunk/admin/.svn/all-wcprops
kxmame/trunk/admin/config.pl
kxmame/trunk/admin/Doxyfile.am
kxmame/trunk/admin/mkinstalldirs
kxmame/trunk/admin/Doxyfile.global
kxmame/trunk/admin/conf.change.pl
kxmame/trunk/admin/doxygen.sh
kxmame/trunk/admin/depcomp
kxmame/trunk/admin/deps.am
kxmame/trunk/admin/compile
kxmame/trunk/admin/libtool.m4.in
kxmame/trunk/admin/bcheck.pl
kxmame/trunk/admin/config.guess
kxmame/trunk/admin/debianrules
kxmame/trunk/admin/config.sub
kxmame/trunk/admin/ltmain.sh
kxmame/trunk/admin/detect-autoconf.pl
kxmame/trunk/admin/am_edit
kxmame/trunk/admin/cvs.sh
kxmame/trunk/admin/Makefile.common
kxmame/trunk/admin/pkg.m4.in
kxmame/trunk/admin/oldinclude.m4.in
kxmame/trunk/admin/configure.in.min
kxmame/trunk/admin/nmcheck
kxmame/trunk/admin/missing
kxmame/trunk/admin/acinclude.m4.in
kxmame/trunk/admin/configure.in.bot.end
kxmame/trunk/admin/install-sh
kxmame/trunk/admin/ylwrap
kxmame/trunk/templates/
kxmame/trunk/templates/.svn/
kxmame/trunk/templates/.svn/text-base/
kxmame/trunk/templates/.svn/text-base/cpp.svn-base
kxmame/trunk/templates/.svn/text-base/h.svn-base
kxmame/trunk/templates/.svn/prop-base/
kxmame/trunk/templates/.svn/props/
kxmame/trunk/templates/.svn/tmp/
kxmame/trunk/templates/.svn/tmp/text-base/
kxmame/trunk/templates/.svn/tmp/prop-base/
kxmame/trunk/templates/.svn/tmp/props/
kxmame/trunk/templates/.svn/entries
kxmame/trunk/templates/.svn/format
kxmame/trunk/templates/.svn/all-wcprops
kxmame/trunk/templates/cpp
kxmame/trunk/templates/h
kxmame/trunk/supportFiles/
kxmame/trunk/supportFiles/.svn/
kxmame/trunk/supportFiles/.svn/text-base/
kxmame/trunk/supportFiles/.svn/text-base/alternative.dat.svn-base
kxmame/trunk/supportFiles/.svn/prop-base/
kxmame/trunk/supportFiles/.svn/props/
kxmame/trunk/supportFiles/.svn/tmp/
kxmame/trunk/supportFiles/.svn/tmp/text-base/
kxmame/trunk/supportFiles/.svn/tmp/prop-base/
kxmame/trunk/supportFiles/.svn/tmp/props/
kxmame/trunk/supportFiles/.svn/entries
kxmame/trunk/supportFiles/.svn/format
kxmame/trunk/supportFiles/.svn/all-wcprops
kxmame/trunk/supportFiles/alternative.dat
kxmame/trunk/doc/
kxmame/trunk/doc/.svn/
kxmame/trunk/doc/.svn/text-base/
kxmame/trunk/doc/.svn/text-base/Makefile.am.svn-base
kxmame/trunk/doc/.svn/prop-base/
kxmame/trunk/doc/.svn/props/
kxmame/trunk/doc/.svn/tmp/
kxmame/trunk/doc/.svn/tmp/text-base/
kxmame/trunk/doc/.svn/tmp/prop-base/
kxmame/trunk/doc/.svn/tmp/props/
kxmame/trunk/doc/.svn/entries
kxmame/trunk/doc/.svn/format
kxmame/trunk/doc/.svn/all-wcprops
kxmame/trunk/doc/en/
kxmame/trunk/doc/en/.svn/
kxmame/trunk/doc/en/.svn/text-base/
kxmame/trunk/doc/en/.svn/text-base/index.docbook.svn-base
kxmame/trunk/doc/en/.svn/text-base/Makefile.am.svn-base
kxmame/trunk/doc/en/.svn/prop-base/
kxmame/trunk/doc/en/.svn/props/
kxmame/trunk/doc/en/.svn/tmp/
kxmame/trunk/doc/en/.svn/tmp/text-base/
kxmame/trunk/doc/en/.svn/tmp/prop-base/
kxmame/trunk/doc/en/.svn/tmp/props/
kxmame/trunk/doc/en/.svn/entries
kxmame/trunk/doc/en/.svn/format
kxmame/trunk/doc/en/.svn/all-wcprops
kxmame/trunk/doc/en/index.docbook
kxmame/trunk/doc/en/Makefile.am
kxmame/trunk/doc/Makefile.am
kxmame/trunk/po/
kxmame/trunk/po/.svn/
kxmame/trunk/po/.svn/text-base/
kxmame/trunk/po/.svn/text-base/kxmame.pot.svn-base
kxmame/trunk/po/.svn/text-base/es.po.svn-base
kxmame/trunk/po/.svn/text-base/fr.po.svn-base
kxmame/trunk/po/.svn/text-base/de.po.svn-base
kxmame/trunk/po/.svn/text-base/sv.po.svn-base
kxmame/trunk/po/.svn/text-base/nl.po.svn-base
kxmame/trunk/po/.svn/text-base/po.sh.svn-base
kxmame/trunk/po/.svn/text-base/pl.po.svn-base
kxmame/trunk/po/.svn/text-base/zh_TW.po.svn-base
kxmame/trunk/po/.svn/text-base/Makefile.am.svn-base
kxmame/trunk/po/.svn/text-base/it.po.svn-base
kxmame/trunk/po/.svn/text-base/el.po.svn-base
kxmame/trunk/po/.svn/text-base/zh_CN.po.svn-base
kxmame/trunk/po/.svn/prop-base/
kxmame/trunk/po/.svn/prop-base/po.sh.svn-base
kxmame/trunk/po/.svn/props/
kxmame/trunk/po/.svn/tmp/
kxmame/trunk/po/.svn/tmp/text-base/
kxmame/trunk/po/.svn/tmp/prop-base/
kxmame/trunk/po/.svn/tmp/props/
kxmame/trunk/po/.svn/entries
kxmame/trunk/po/.svn/format
kxmame/trunk/po/.svn/all-wcprops
kxmame/trunk/po/kxmame.pot
kxmame/trunk/po/es.po
kxmame/trunk/po/fr.po
kxmame/trunk/po/de.po
kxmame/trunk/po/sv.po
kxmame/trunk/po/nl.po
kxmame/trunk/po/po.sh
kxmame/trunk/po/pl.po
kxmame/trunk/po/zh_TW.po
kxmame/trunk/po/Makefile.am
kxmame/trunk/po/it.po
kxmame/trunk/po/el.po
kxmame/trunk/po/zh_CN.po
kxmame/trunk/Doxyfile
kxmame/trunk/kxmame.kdevses
kxmame/trunk/AUTHORS
kxmame/trunk/ChangeLog
kxmame/trunk/kxmame.kdevelop
kxmame/trunk/configure.in.in
kxmame/trunk/README
kxmame/trunk/TODO
kxmame/trunk/INSTALL
kxmame/trunk/Makefile.cvs
kxmame/trunk/COPYING
kxmame/trunk/Makefile.am
kxmame/trunk/NEWS
kxmame/trunk/kxmame.kdevelop.pcs
kxmame/branches/
kxmame/branches/.svn/
kxmame/branches/.svn/text-base/
kxmame/branches/.svn/prop-base/
kxmame/branches/.svn/props/
kxmame/branches/.svn/tmp/
kxmame/branches/.svn/tmp/text-base/
kxmame/branches/.svn/tmp/prop-base/
kxmame/branches/.svn/tmp/props/
kxmame/branches/.svn/entries
kxmame/branches/.svn/format
kxmame/branches/.svn/all-wcprops
kxmame/tags/
kxmame/tags/.svn/
kxmame/tags/.svn/text-base/
kxmame/tags/.svn/prop-base/
kxmame/tags/.svn/props/
kxmame/tags/.svn/tmp/
kxmame/tags/.svn/tmp/text-base/
kxmame/tags/.svn/tmp/prop-base/
kxmame/tags/.svn/tmp/props/
kxmame/tags/.svn/entries
kxmame/tags/.svn/format
kxmame/tags/.svn/all-wcprops
```

```
./configure filename.tar.bz2
```

That didn't work

```
make filename.tar.bz2
```

that also didn't work and...

```
make install filename.tar.bz2
```

didn't work either...

---

### Post by ~LoKe on 2007-12-17
That's not what I said. ;)

```
./configure
make
sudo make install
```

Assuming there is a configure file..

**EDIT**: You downloaded the SVN source, you want this one instead: [http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0](http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0)

---

### Post by Moonfrost on 2007-12-17
> **~LoKe said:**
> That's not what I said. ;)

```
./configure
make
sudo make install
```

Assuming there is a configure file..

**EDIT**: You downloaded the SVN repository, you want this one: [http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0](http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0)

Actually I typed "tried" and then the codes...but for some reason my edit came first...anyway, I tried that because I saw it on another forum and it seemed to work to extract the file but everything else doesn't work...

---

### Post by Moonfrost on 2007-12-17
> **~LoKe said:**
> That's not what I said. ;)

```
./configure
make
sudo make install
```

Assuming there is a configure file..

**EDIT**: You downloaded the SVN source, you want this one instead: [http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0](http://downloads.sourceforge.net/kxmame/kxmame-1.2.tar.bz2?modtime=1136222630&big_mirror=0)

That's 1.2 though...what I have is 2.0...

---

### Post by whit on 2007-12-17
A subversion repository is a whole different animal. See [http://subversion.tigris.org/](http://subversion.tigris.org/). You can definitely build from it, but the command set is different than building from a tar. (I've done it, but don't remember the commands now.)

---

