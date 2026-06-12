---
title: "Resolving Dependencies (GDAM)"
date: 2005-08-09
forum: General Help
---

### Post by datassette on 2005-08-09
I've been using Linux for about 3 hours now.

I'm trying to install [GDAM](http://gdam.ffem.org/) , a slightly stagnant mp3 mixing program - this is infact the whole reason I'm trying Linux.

When I installed the .deb packages of GDAM, there were a whole bunch of dependency problems, I've managed to get most of these libs from the debian site and install them.

There are 2 things I cannot find though:

xlib6g
mpg123


What are these?  Anyone know where I can find them?

Remember, I am a complete n00b so be gentle!
Thanks for reading.

---

### Post by PeP on 2005-08-09
[QUOTE=datassette]I've been using Linux for about 3 hours now.

I'm trying to install [GDAM](http://gdam.ffem.org/) , a slightly stagnant mp3 mixing program - this is infact the whole reason I'm trying Linux.

When I installed the .deb packages of GDAM, there were a whole bunch of dependency problems, I've managed to get most of these libs from the debian site and install them.

There are 2 things I cannot find though:

xlib6g
mpg123


What are these?  Anyone know where I can find them?

Remember, I am a complete n00b so be gentle!
Thanks for reading.[/QUOTE]

let me guess you didn't use apt nor synaptic nor dselect nor kynaptic ??
launch synaptic search for mpg123 it will install it for you.
xlib6g is not more available ... use  xlibs instead irt replaces it ...(installed with the defaults settings of the installer!)

---

### Post by datassette on 2005-08-09
'xlibs' is already installed, the program I want to use is asking for 'xlib6g'.

I've found mpg123 myself, but it also has dependency problems.

I tried to 'fix' the 'broken packages' in Synaptic, but it's idea of fixing them was to just delete them!  Which isn't much help.

---

### Post by PeP on 2005-08-09
broken means broken dependencies, if you install .deb files from everywhere that is the less annoying thing you can expect.

you will never be able to install correctly xlib6g. It is outdated and replaced by xlibs. It doen't exist anymore. All the stuffs in it are in xlibs and if you manage to install it it might interfere with xlibs, leaving you with a broken system.

it looks like your deb files are outdated,
try the tarball 
downlaod the .tar.gz: in a terminal:
wget [http://prdownloads.sourceforge.net/gdam/gdam-0.942.tar.gz](http://prdownloads.sourceforge.net/gdam/gdam-0.942.tar.gz)
tar -xvzf gdam-0.942.tar.gz
cd gdam-0.942
./configure
make
sudo make install

---

### Post by varunus on 2005-08-09
Make sure to install build-essential before doing the above.

I think some packages you're missing could be found by adding hoary-extras and hoary-backports, and enabling universe.  Follow the guide here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by datassette on 2005-08-10
OK folks, I've got the tarball and un-tarred it, installed build-essential and did the hoary-extras and universe thing (whatever that was!).

When I type "./configure" I get:

loads of other stuff that generally looks OK
.......
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets ${MAKE}... (cached) yes
checking host system type... i686-pc-linux-gnu
checking for dpkg-buildpackage... /usr/bin/dpkg-buildpackage
checking how to run the C preprocessor... gcc -E
checking for ladspa.h... no
checking for termios.h... yes
checking for linux/input.h... yes
checking for semaphore.h... yes
checking for mach/mach.h... no
checking for gtk-config... no
checking for GTK - version >= 1.2.5... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find Gtk - gtk-config missing from path?


Any ideas?

And help would be mucho appreciated. I'm gradually getting there, I can feel it.

---

