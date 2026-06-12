---
title: "Some program install issues.."
date: 2007-12-31
forum: General Help
---

### Post by fr33zypop on 2007-12-31
I have been trying to install a program called Avant Window Navigator. I guess I don’t need it, I just want to be able to get it working, and learning the steps to install it. I go to [**https://launchpad.net/awn **]("**https://launchpad.net/awn**")and download the [**https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar**]("**https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar**"). I extract it to the desktop. Then I open Terminal and do cd to the extracted folder from desktop dropped into terminal line, ENTER>./configure I start to get errors. .  

USER@USER-desktop:/home/freezy/Desktop/avant-window-navigator-0.2.1# ./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for a Python interpreter with version >= 2.3.5... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
checking for PYCAIRO... yes
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.36.2 found
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
checking for catalogs to be installed...  ar bg ca cs da de de_DE el en_AU en_GB es eu fa fi fi_FI fr fr_FR gl he hr hu it it_IT ja ka ko nb nl nn no_NO pl pt_BR pt ro ru ru_RU sk sr sv tr zh_CN zh_HK zh_TW
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.14.1)

checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11
xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found

[B]Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

I have installed all of the follwing from the **README **file in the install folder that’s avalible in Package Manager.

libwnck-1.0
gnome-desktop-2.0
libgnome-2.0
gnome-vfs-2.0
gconf-2.0
x11 – I don’t know if I found the right package cause there was a lot of returns for search.
xproto
dbus-glib-1
libglade-2.0
xdamage
xcomposite
xrender

You will also need the following python packages (these are debian-specific naming, but should also be easy to find on other systems):

python2.5-dev
python-gnome2-dev
python-gnome2-desktop-dev
python-gnome2-extras-dev

Now some of these packages I didn’t see when I searched them. I am new so I don’t know if it matters what distro I have.

---

### Post by cdenley on 2007-12-31
I would just wait for ubuntu hardy to be released. AWN is already in the hardy repository. Installing from source is difficult because you have to resolve all the dependencies yourself. You usually need the -dev packages for all the dependencies as well.

---

### Post by fr33zypop on 2007-12-31
Though I get the same kinds of errors when I try install some other programs like cairo dock.

---

### Post by dlegend on 2007-12-31
Do you have all the repos enabled? 

To do this go to your Synaptic Package Manager, click on "Settings" > "Repositories" and make sure under the Ubuntu Software tab that the first four boxes are checked (main, universe, restricted, and multiverse).

Now go to the Updates tab and make sure gutsy-security, gutsy-updates, and gutsy-backports are checked.

Reload the repository and try to update / install those packages.

If you are still missing packages, let me know.

---

### Post by ~LoKe on 2007-12-31
I'm pretty sure you need the -dev versions of those packages.

---

### Post by fr33zypop on 2007-12-31
> **~LoKe said:**
> I'm pretty sure you need the -dev versions of those packages.

Can you explain a little more about "which" dev versions I need. I have downloaded  and of the required packages that was a -dev.

---

### Post by PeterJS on 2007-12-31
Getdeb.net is your friend. They've got the best collection of third party deb's I've seen. Like an [AWN](http://www.getdeb.net/app.php?name=Avant+Window+Navigator) Deb.

---

### Post by fr33zypop on 2008-01-01
> **dlegend said:**
> Do you have all the repos enabled? 

To do this go to your Synaptic Package Manager, click on "Settings" > "Repositories" and make sure under the Ubuntu Software tab that the first four boxes are checked (main, universe, restricted, and multiverse).

Now go to the Updates tab and make sure gutsy-security, gutsy-updates, and gutsy-backports are checked.

Reload the repository and try to update / install those packages.

If you are still missing packages, let me know.

So I had to check gutsy-backports and I found only one more package that I didnt have from python packages. I did updates and it still gives the same errors.

---

### Post by dlegend on 2008-01-09
As suggested, I'd download the latest deb from this link: [http://www.getdeb.net/app.php?name=Avant+Window+Navigator](http://www.getdeb.net/app.php?name=Avant+Window+Navigator)

After download it, just run it and install. It should install the dependencies with it and you shouldn't run into the problem in the future. Might not be a direct solution to why you can't find those packages, but it will solve your AWN installation problem.

---

