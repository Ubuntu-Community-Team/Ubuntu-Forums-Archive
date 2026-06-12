---
title: "Kubuntu LiveCD Integrity???"
date: 2005-04-18
forum: General Help
---

### Post by Tiede on 2005-04-18
I downloaded Kubuntu's i386-iso yesterday. Checked the md5sum, it matches that of the official Kubuntu site. So I burn the CD and try running it.
The Installation stops when copying files from the hard disk and says that I should check the integrity of the CD...
So I skip the copying step and check the integrity of all the files on the CD one by one, and strangely, it does not match... A file from the /pool directory (and maybe some others) don't have the right md5sum size...

Because this is not something that I usually encounter, I thought of posting it here...
I just want to know if I should go ahead and re-download the .iso image or is there something else... Because the md5sum of the .iso file matches the official one. Just some files 'inside' the .iso image are corrupted  :| 

Can anyone help?
I really wanted to try a *blue* Ubuntu for a little while.

#hmm, prehaps it would help to know inform you that the file that seemingly is corrupted (this is the file the installer was coppying  before showing the error message) is casper-udeb...

---

### Post by tread on 2005-04-18
If you used nautilus to burn the iso, that might be the problem. I had similar trouble, then I discovered that nautilus wasn;t burning the cd completely. There is some setting you have to change, but I don;t remember what. 

Alternately, try using gnomebaker .. you should find it at gnomefiles.org

---

### Post by Tiede on 2005-04-18
I tried installing GnomeBaker, but I can't... It seems like Ubuntu like putting me in front of Brick walls...
I ran ./configure, and it failed once asking for GCC, and after GCC it failed asking for G++, and after that it failed asking for gnomelibui, and now it is asking for package vorbisfile... Tried a google search, no vorbisfile around.
In Synaptic, a search for vorbis file give the packets
```

libogg-vorbis-decoder-perl -- Not installed
libvorbisfile3 -- Installed (Version 1.0.1-1)
libvorbisfile-ruby -- Not installed
libvorbisfile-ruby1.6 -- Not Installed
libvorbisfile-ruby1.8 -- Not installled
libvorbisfile-perl -- Not installed

```

Which one is the lucky one to be installed :)

BTW, here is the install log as appeared in the terminal
```

root@Linuxed:/home/marc/gnomebaker-0.3 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0 >= 2.4.0 glib-2.0 >= 2.4.0 libglade-2.0 vorbisfile... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found
root@Linuxed:/home/marc/gnomebaker-0.3 # synaptic
root@Linuxed:/home/marc/gnomebaker-0.3 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 gtk+-2.0 >= 2.4.0 glib-2.0 >= 2.4.0 libglade-2.0 vorbisfile... Package vorbisfile was not found in the pkg-config search path.
Perhaps you should add the directory containing `vorbisfile.pc'
to the PKG_CONFIG_PATH environment variable
No package 'vorbisfile' found
root@Linuxed:

```

Hmmm...

---

### Post by Tiede on 2005-04-18
I just searched "CD Burning" in Syanptic and found some related apps... Do you think Gcombust would be a good guess... Cause all the other one are described as KDE-Frontend, ECLiPT frontend, TCL/Tk frontend... and I don't know if they would work find...

Other optiions that attract me are the packages cdcontrol (A parallel burner that allow you to write to one or more CD-Writer at once) and webmin-burner (CD burning module for webmin) --- that one, of course as a VERY LAST resort.

---

### Post by Tiede on 2005-04-20
Sorry for posting 3 times in a row... One quick question, is there a way to have gnomebaker available in Synaptic so that I do not have to compile it myself?
Or is there a better/cleaner CD Burning App out there that would fit perfectly on my Ubuntu Warty Box?...

---

### Post by siebzehn on 2005-04-20
[QUOTE=Tiede]Sorry for posting 3 times in a row... One quick question, is there a way to have gnomebaker available in Synaptic so that I do not have to compile it myself?
Or is there a better/cleaner CD Burning App out there that would fit perfectly on my Ubuntu Warty Box?...[/QUOTE]
 Yes you can, just add this line to your /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

then   "apt-get update && apt-get install gnomebaker"

---

### Post by Tiede on 2005-04-21
This is quite disturbing...
I have a couple of LiveCDs hanging around my house. So, instead of all those troubles, I decided to use K3B to burn the kubuntu iso image. By default, K3B checks the md5sum of the iso file, which came out perfectly right, it matches that of the original... (The md5 on the .iso file on my computer is the same as the one on the .iso on kubuntu.org)
I decided, as and added bonus, to compare the md5sum of the files in the .iso file with the content of the md5sum list file present on the CD... It does not match.
I only see on output to this: The bug comes not from me, but from Kubuntu.org...
From that, where do I go to report this finding. Should I just report it in Bugzilla?

---

### Post by Tiede on 2005-04-21
Hmm... I think this just *broke* synaptic
each time I try to install a program now, it gives me errors... An example
```

root@Linuxed:/home/marc # apt-get install gnomebaker
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnomebaker: Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
              Depends: libgconf2-4 (>= 2.9) but 2.8.1-0ubuntu1 is to be installed
              Depends: libglade2-0 (>= 1:2.5.1) but 1:2.4.0-1 is to be installed              Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
              Depends: libgnomevfs2-0 (>= 2.9.90) but 2.8.2-0ubuntu1 is to be installed
              Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1.1 is to be installed
              Depends: libogg0 (>= 1.1.2) but 1.1.0-1 is to be installed
              Depends: libpango1.0-0 (>= 1.8.1) but 1.6.0b-0ubuntu1 is to be installed
              Depends: libxml2 (>= 2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
E: Broken packages
root@Linuxed:/home/marc #


```

---

### Post by tread on 2005-04-25
Ok, I remembered the nautilus setting.

Applications->System->Configuration Editor
Click apps, go down to the nautilus cd burning section
then check burnproof.

That worked for me.

---

### Post by Tiede on 2005-04-25
I already did that, but haven't tried it yet.. Will do so tonight.

BTW, I tried burning it using K3B from a LIveCD I had around (Slax), and the same files are corrupted... Is this normal? K3B check for the iso itself, and the other times I burned with it before it never gave me this kind of error.
What do you think?

---

