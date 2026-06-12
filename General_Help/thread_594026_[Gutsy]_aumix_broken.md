---
title: "[Gutsy] aumix broken"
date: 2007-10-27
forum: General Help
---

### Post by Bulldog9908 on 2007-10-27
I was depending on aumix to set the line input under Feisty, but with Gutsy, all I get is this:
```
aumix: SOUND_MIXER_READ_DEVMASK
```

I've got it half working with amixer, but I can't get amixer to turn off capture on Line or mute it, so after the recording starts, it's on constantly.

Here's what works:
```
/usr/bin/amixer -c 0 sset Line,0 60% 60% mute cap
```

Here's what should work (according to the man page), but doesn't:
```
/usr/bin/amixer -c 0 sset Line,0 0% 0% mute nocap
```

Any ideas about how to get aumix to work under Gutsy?  Or, what am I doing wrong with amixer that it won't turn off capture or mute the Line input?

Thanks.

---

### Post by jviscosi on 2007-11-05
It seems the aumix package in Gutsy is busted.  I downloaded the source code from the [project page]("http://www.jpj.net/%7Etrevor/aumix.html") and compiled it myself to get it working again.

Assuming you don't want to compile aumix, the Debian package from etch might work.  It's at [http://packages.debian.org/etch/aumix/i386/download](http://packages.debian.org/etch/aumix/i386/download).  You would download it and install it by running **sudo dpkg -i aumix_2.8-17_i386.deb**.  NOTE:  I didn't try this DEB file myself, but it's older than the Ubuntu version so I'd hope it's the working version.  If you install it, Ubuntu is going to immediately want to replace it with its own version 2.8.18 package, which is the busted one, so don't let it.  (I named my compiled version 2.8.19.)

---

### Post by nodog on 2007-11-09
Following jviscosi's post, one can also use ```
sudo dpkg --set-selections
``` and then type "aumix hold", enter, Ctrl-D in order to keep the system from automatically upgrading aumix.  It will also give you a note saying "these packages held back: aumix" when you do an upgrade to remind you that eventually you'll want to get back on the binary package.

---

### Post by jviscosi on 2007-11-09
> **nodog said:**
> Following jviscosi's post, one can also use ```
sudo dpkg --set-selections
``` and then type "aumix hold", enter, Ctrl-D in order to keep the system from automatically upgrading aumix.  It will also give you a note saying "these packages held back: aumix" when you do an upgrade to remind you that eventually you'll want to get back on the binary package.

Hey, cool, I didn't know you could do that -- thanks!

---

### Post by promet on 2007-12-08
A possible alternative:

I ran into this problem, I suppose everyone did. If one doesn't want to package building, etc; there is a package that does work as a mixer, called "gamix". It's not as pretty as aumix, but works very well, for me at least. Check it out.

my $.0.02

---

### Post by dxmosiris on 2008-02-12
I am trying to compile form source but for some reason it is not liking it. Here is the error output.

root@pc:/usr/local/src/aumix-2.8# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for mawk... mawk
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

gcc is a default package. What else could be going wrong?

---

### Post by promet on 2008-02-12
You will need to install each one of those missing packages:

checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing

With apt or Synaptic. These also may be part of another package, such as "build-essential" or some such.

Open up Synaptic (The package manager), or search for these packages from the command line with "sudo apt-cache search [package-name]"

It begins to occur to me how badly I am explaining this. If this seems confusing. Please respond and I will give you a rundown of using apt-get, apt-cache etc. If you've used these before you should be able to make your way.

Cheers...
promet

---

### Post by dxmosiris on 2008-02-13
No that was a great help actually. Before I posted I looked up all the dependencies for aumix;just a few libraries but that did work either.

I did install build-essential and I am getting further through the ./configure.

Now I am failing at with a gtk package.

checking for pkg-config... yes
pkg-config found--compiling with GTK+ 2.0.
checking for pkg-config... /usr/bin/pkg-config
checking for GTK - version >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
no
*** Could not run GTK 2.0 test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK was incorrectly installed
*** or that you have moved GTK since it was installed. In the latter case, you
*** may want to edit the pkg-config script: /usr/bin/pkg-config
configure: error: Test for GTK failed. See the file 'INSTALL' for help.

Going to see if there is a standard package for GTK

---

### Post by dxmosiris on 2008-02-13
The configure successfully finishes now with the installation of libgtk-2.0dev but the make fails. Does anyone have a good list of common developer libraries needed for compiling from source?

error thrown:

interactive.c: In function &#8216;AumixSignalHandler&#8217;:
interactive.c:34: error: &#8216;SIGALRM&#8217; undeclared (first use in this function)
interactive.c:34: error: (Each undeclared identifier is reported only once
interactive.c:34: error: for each function it appears in.)
make[2]: *** [interactive.o] Error 1
make[2]: Leaving directory `/usr/local/src/aumix-2.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/aumix-2.8'
make: *** [all-recursive-am] Error 2

I thought it could be a corrupt download but I downloaded older versions and it fails along the same lines in any version.

---

### Post by dxmosiris on 2008-02-13
Installed from feisty repos... 

Not fully functional but i have volume control in fluxbox now ;D

---

