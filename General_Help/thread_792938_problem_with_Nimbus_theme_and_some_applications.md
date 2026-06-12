---
title: "problem with Nimbus theme and some applications"
date: 2008-05-13
forum: General Help
---

### Post by laptoplinux on 2008-05-13
I have installed the Nimbus theme on Ubuntu Hardy, and so far it is by far the best Gnome theme I've come across.  I only have one issue with it.  On at least a couple of applications, the window decorator part will phase out or get corrupted when you mouse over and around the minimize, maximize, and close buttons.  Specfically, this happens with OpenOffice and Thunderbird.  It also happens when the Thunderbird compose window title changes as you type in the subject line.  This is also with Compiz-Fusion running.  I haven't tried it without Compiz, but I'll change themes before I drop Compiz.

Has anyone else run into this?  Any known solutions?  If not, can anyone recommend a good window decorator theme that still matches with the rest of the Nimbus theme?

---

### Post by peddy on 2008-06-12
I installed the latest version of Nimbus (0.0.16) found [here](http://dlc.sun.com/osol/jds/downloads/extras/). Let me know if you have any problems compiling. 

It includes a nice new menu-bar, as well as fixed Openoffice fonts. 

Cheers

---

### Post by ethoms on 2008-08-18
> **peddy said:**
> I installed the latest version of Nimbus (0.0.16) found [here](http://dlc.sun.com/osol/jds/downloads/extras/). Let me know if you have any problems compiling. 

It includes a nice new menu-bar, as well as fixed Openoffice fonts. 

Cheers

I'm having problems compiling on Ubuntu 8.04 (hardy). I extracted the zip to /source, cd into nimbus-0.0.16 and typed ./configure Below is the error I get.

# ./configure CONFIG_SHELL=/bin/bash
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


I'm guessing this is a common error, I'm new to compiling on linux, please help! :)

---

### Post by ethoms on 2008-08-18
I found out that I just needed to install gcc, I also had to install some other dependencies, the configure script let's you know what they are.

Useful note: I had to copy intltool files to the root of the source code folder (where the configure script and make file resides). Also, once  built successfully, you need to make some links (in Solaris /usr/share = /usr/local/share) Other than that it was pretty straight forward.

Links:
```

ln -s /usr/local/lib/gtk-2.0/2.10.0/engines/libnimbus.so /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.so
ln -s /usr/local/lib/gtk-2.0/2.10.0/engines/libnimbus.a /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.a
ln -s /usr/local/lib/gtk-2.0/2.10.0/engines/libnimbus.la /usr/lib/gtk-2.0/2.10.0/engines/libnimbus.la
ln -s /usr/local/share/icons/nimbus /usr/share/icons/nimbus
ln -s /usr/local/share/themes/nimbus /usr/share/themes/nimbus

```

I also replaced the opensolaris launch icon with ubuntu one. They can be found at /usr/local/share/icons/nimbus/32x32/places/start-here.png and /usr/local/share/icons/nimbus/24x24/places/start-here.png. Ubuntu logo is also called start-here.png and should be in /usr/share/icons/...

Results so far: Window borders and icons are working but controls are not installed properly, noticably the scroll bar is not that of Nimbus but a basic one instead. Shame because the Nimbus scrollbar is the best thing about the theme. This theme is top notch IMHO.

If anybody has compiled/installed 0.0.16 completely (with all controls working) please can you post any additional steps.

---

### Post by ethoms on 2008-08-18
Theme is now fully working, yee-ha! All I did since last post is clean, re-configure, re-make, re-install.

```

# cd /source/nimbus*
# make clean
# ./configure
# make
# make install

```

---

### Post by Ashinberry on 2009-01-16
Heya,

   I stumbled upon this thread while googling to discover why the pretty scroll bar wasn't working. Kudos to ethoms for figuring it out. FYI, an easier and cleaner method of installing this (without having to use links) would be:

```

$ make clean
$ ./configure --prefix=/usr/
$ make
# make install

```

---

