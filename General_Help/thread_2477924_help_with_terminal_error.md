---
title: "help with terminal error"
date: 2022-08-11
forum: General Help
---

### Post by cmcanulty on 2022-08-11
recently my favorite chess program won't run. I get this error which I can't find a fix for:
```

terminate called after throwing an instance of 'tcl::Exception' Aborted (core dumped)
```

can someone help on this?

---

### Post by TheFu on 2022-08-11
tcl is an interpreted language.  I'd check that the software stack versions for the program as documented are correct for the Tk and TCL versions installed.  If they are, then I'd try reinstalling everything related to the program.

---

### Post by dragonfly41 on 2022-08-11
Change in Python version ... I guess that your chess game is in Python

[https://docs.python.org/3/library/tkinter.html](https://docs.python.org/3/library/tkinter.html)

---

### Post by cmcanulty on 2022-08-24
actually it is in C++

---

### Post by &amp;KyT$0P# on 2022-08-24
What chess program and where are you getting it from?

---

### Post by TheFu on 2022-08-24
> **cmcanulty said:**
> actually it is in C++

And TCL supports C++ bindings, so I'll say again, check the complete stack of all software involved in this program.  Google did find a link that something in tcl:exception had changed.  Perhaps a different tcl library is being used than expected by the program?

---

### Post by cmcanulty on 2022-08-25
I reinstalled all the dependencies and had no effect. It is scidb chess from sourceforge. It worked fine and I guess some Ubuntu update borked it. 
[https://sourceforge.net/projects/scidb/]("https://sourceforge.net/projects/scidb/")
it is the only linux app that can read chessbase game files which are very important to use. Now I am going to completely remove all the dependencies and then reinstall them. Here is the install file that lists all the specific Ubuntu dependencies. Here is the error I get when installing now

```
terminate called after throwing an instance of 'tcl::Exception'
Aborted (core dumped)
```


```

   _/|            __
  // o\         /    )           ,        /    /
  || ._)    ----\---------__----------__-/----/__-
  //__\          \      /   '  /    /   /    /   )
  )___(     _(____/____(___ __/____(___/____(___/_

                       How To Compile

===============================================================================
UNIX
===============================================================================
Probably you have to install some required packages:

1. Tcl/Tk package

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install tcl8.6
      > sudo apt-get install tk8.6

2. Freetype development package
   (normally available, but especially missing under Ubuntu)

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install libfreetype6-dev

3. SM library development package
   (normally available, but especially missing under Ubuntu)

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install libsm-dev

4. Xcursor development package
   (normally available, but especially missing under Ubuntu)

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install libxcursor-dev

5. fontconfig development package
   (normally available, but especially missing under Ubuntu)

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install libfontconfig1-dev

6. libgdbm development package
   (normally available, but especially missing under Ubuntu)

   On Debian/Ubuntu/Mint use:
      > sudo apt-get install libgdbm-dev

A normal unix installation is made in three steps (after you've unpacked
the source archive):

   ./configure
   make
   make install

You probably need to be root when doing the last command. An alternative is
to use the "sudo" command for the installation:

   sudo make install

Get a full listing of all available configure options by invoking it like:

   ./configure --help

If you want to install scidb in a different file hierarchy than /usr/local,
you need to specify that already when running configure:

   ./configure --prefix=/path/to/scidb/tree --exec-prefix=/path/to/scidb/tree

If you happen to have write permission in that directory, you can do "make
install" without being root. An example of this would be to make a local
install in your own home directory:

   ./configure --prefix=$HOME --exec-prefix=$HOME
   make
   make install

The configure script always tries to find a working Tcl/Tk library unless
explicitly told not to. If you have Tcl/Tk installed in the default search
path for your compiler/linker, you don't need to do anything special. If
you have Tcl/Tk somewhere else (for example, $HOME/mytcltk), you can run
configure like:

   PATH=$PATH:$HOME/mytcltk/bin \
   ./configure --tcl-includes$HOME=$HOME/mytcltk/include \
               --tk-includes=$HOME/include \
               --tcl-libraries=$HOME/mytcltk/lib \
               --tk-libraries=$HOME/mytcltk/lib

Note that the PATH variable has to contain the path of the Tcl shell (for
example '$HOME/mytcltk/bin' which contains tclsh8.5), otherwise the Tcl shell
will not be found.

Not every GCC compiler version is properly working. The minimum compiler
version is 3.4, and version 4.6 is excluded because of a compiler bug. It may
be required to install a proper compiler. For example you decided to use
version 4.4: on Debian/Ubuntu/Mint use

   sudo apt-get install gcc-4.4
   sudo apt-get install g++-4.4
   ./configure --gcc-version=4.4

Alternatively the clang compiler may be used. The minimal clang version which
can be used is 3.1. The newer version 3.3 is also working, but it's not yet
sure that this version is linking properly. If you want to use clang tell it
to the configure script in this way:

   ./configure --gcc-version=clang

On Debian/Ubuntu/Mint system the usage of newer compilers is a bit problematic,
because Debian has changed some system paths. It may be neccessary to tell
the configure script the required paths, for example:

   ./configure \
      --gcc-version=4.7 \
      SYS_CFLAGS="-I/usr/include/i386-linux-gnu" \
      SYS_CXXFLAGS="-I/usr/include/i386-linux-gnu" \
      SYS_LDFLAGS="-B/usr/lib/i386-linux-gnu"

Exchange "i386-linux-gnu" with the system specific part of your architecture.
It's of course a bad idea from Debian that the user has to know the system
paths, but the configure script may give you a hint. If you invoke this script
(./configure) look at the output, it shows a line like this:

   Location of X11 library: /usr/lib/i386-linux-gnu

The latter part of the path (in this example "i386-linux-gnu") is your system
specific part.

Ubuntu 14.04 has changed the directory structure of freetype, and this is
definitely a bug, because the new path structure violates the standard. So
you have to create a symlink as a workaround:

    sudo ln -s /usr/include/freetype2/config /usr/include/freetype2/freetype/config

-------------------------------------------------------------------------------
Important notes for the build of packages
-------------------------------------------------------------------------------
For the build of packages in a temporary directory some fine tuning parameters
should be used, for example:

   ./configure \
      --prefix=/usr \
      --exec-prefix=/usr \
      --enginesdir=/usr/bin \
      --destdir=$pkgdir

In this example the installation will be done in $pkgdir/usr, but the
destination directory for the package is determined as /usr. Without
parameter --enginesdir the installation of the engines will be done in
directory $pkgdir/usr/games.

Without the --destdir parameter the configure script would choose the path
/usr/share/fonts/truetype/Scidb for the installation of the truetype fonts,
because in a normal user installation this is the desired directory, but
in the example above $pkgdir/usr/share/fonts/truetype/Scidb will be used
instead.

IMPORTANT NOTE:
With parameter --destdir the setup of the truetype fonts and the
freedesktop.org stuff will be skipped. This means that the packager has to
integrate the scripts postinstall-pak, postremove-pak, and preremove-pak.
But before integration of these scripts the paths used inside the scripts
has to be adjusted.

IMPORTANT NOTE:
Without setup of the truetype fonts Scidb will not run properly.

= vi:set et sw=3 ts=3: =
```

---

### Post by sudodus on 2022-08-26
If there is a conflict with some important part of or tool in your current Ubuntu system, I suggest that you set up a virtual machine with a previous version of Ubuntu and run your chess program there.

---

### Post by cmcanulty on 2022-08-26
OK thanks. Is there no way to just fix the error:  

```
terminate called after throwing an instance of 'tcl::Exception'
Aborted (core dumped)
```

---

### Post by TheFu on 2022-08-26
> **cmcanulty said:**
> OK thanks. Is there no way to just fix the error:  

```
terminate called after throwing an instance of 'tcl::Exception'
Aborted (core dumped)
```

There's always "a way", but you'd need to be a software developer, compile everything from source with debug symbols, then recreate the error in a debugger or force a stack dump (stace could be helpful for this), and finally see, understand and fix the code.  The development team for the program is best able to do that ... or someone with a real itch to use the program who has those specific skills and time.

---

### Post by &amp;KyT$0P# on 2022-08-26
> **cmcanulty said:**
> It is scidb chess from sourceforge. It worked fine and I guess some Ubuntu update borked it. 
[https://sourceforge.net/projects/scidb/]("https://sourceforge.net/projects/scidb/")

:confused:
I got that code to compile on Xubuntu 22.04 and it seems to run fine, running [FONT=Courier New]scidb-beta[/FONT] ran without error and I can play chess moves in the Board tab.

> **sudodus said:**
> If there is a conflict with some important part of or tool in your current Ubuntu system, I suggest that you set up a virtual machine with a previous version of Ubuntu and run your chess program there.

+1, this program is clearly designed for older systems, compiling it on Xubuntu 22.04 required gcc-9/g++-9 (because 11.2 is older than 3.4???) and manually changing an obsolete #include path.

---

### Post by dragonfly41 on 2022-08-26
Can you perhaps try running** ldd **on the binary to list its dependencies?

---

### Post by Impavidus on 2022-08-26
> **halogen2 said:**
> 
compiling it on Xubuntu 22.04 required gcc-9/g++-9 (because 11.2 is older than 3.4???)
I remember this was discussed here before: [https://ubuntuforums.org/showthread.php?t=2474765](https://ubuntuforums.org/showthread.php?t=2474765)

---

### Post by &amp;KyT$0P# on 2022-08-26
> **Impavidus said:**
> I remember this was discussed here before: [https://ubuntuforums.org/showthread.php?t=2474765](https://ubuntuforums.org/showthread.php?t=2474765)

That method of using gcc-9 is needlessly invasive and may break the system.  [FONT=Courier New]./configure --help[/FONT] lists environment variables that can be used to **non-invasively** tell it to compile using gcc-9 and g++-9.

---

### Post by cmcanulty on 2022-08-26
Yes I wrote that  other post and the tutorial on how to install in Ubuntu and it worked for months and now is broken and seems unfixable. I did set up gcc 9 successfully

---

