---
title: "Beep Media Player and gxmms - can it be used without xmms?"
date: 2005-08-25
forum: General Help
---

### Post by Daniel Rehm on 2005-08-25
So! I've decided I prefer beep to xmms, but I'm addicted to the gxmms applet. To my delight, I discover it works with beep... sort of. Hitting play still opens xmms by default. I don't want to have to mess with the application menu every time I want to start my media player! That defeats the whole purpose! Thinking I'm oh so clever, I uninstall xmms. This, of course, renders gxmms unusable. Curses! 

So here is my question:

Is there either a way to make the gxmms applet work without xmms installed OR is there an equivalent applet just for beep?

---

### Post by Perfect Storm on 2005-08-25
[QUOTE=Daniel Rehm]So! I've decided I prefer beep to xmms, but I'm addicted to the gxmms applet. To my delight, I discover it works with beep... sort of. Hitting play still opens xmms by default. I don't want to have to mess with the application menu every time I want to start my media player! That defeats the whole purpose! Thinking I'm oh so clever, I uninstall xmms. This, of course, renders gxmms unusable. Curses! 

So here is my question:

Is there either a way to make the gxmms applet work without xmms installed OR is there an equivalent applet just for beep?[/QUOTE]

gxmms (v.0.2.1) on hoary doesn't support Beep media. The newest one does (v.0.3.0):  [http://linux.softpedia.com/get/Multimedia/Audio/gxmms-3381.shtml](http://linux.softpedia.com/get/Multimedia/Audio/gxmms-3381.shtml)

Some month ago I saw a specific beep media panel player, but I can't remember where an what it's called.



.:=The AI Dude=:.

---

### Post by Daniel Rehm on 2005-08-25
[QUOTE=Artificial Intelligence]gxmms (v.0.2.1) on hoary doesn't support Beep media. The newest one does (v.0.3.0):  [http://linux.softpedia.com/get/Multimedia/Audio/gxmms-3381.shtml](http://linux.softpedia.com/get/Multimedia/Audio/gxmms-3381.shtml)

Some month ago I saw a specific beep media panel player, but I can't remember where an what it's called.



.:=The AI Dude=:.[/QUOTE]
I don't mean to contradict you, but I am using 0.2.1 to listen to music on bmp, this very moment.

---

### Post by Perfect Storm on 2005-08-25
[QUOTE=Daniel Rehm]I don't mean to contradict you, but I am using 0.2.1 to listen to music on bmp, this very moment.[/QUOTE]

No problem. I never used beep, I just read what it says on the page: 

What's New in This Release:

· This release adds support for Beep Media Player, fixes some translation issues and adds new menu options.

---

### Post by Daniel Rehm on 2005-08-25
[QUOTE=Artificial Intelligence]No problem. I never used beep, I just read what it says on the page: 

What's New in This Release:

· This release adds support for Beep Media Player, fixes some translation issues and adds new menu options.[/QUOTE]
 Maybe that means it will support beep w/o xmms installed. I'll have to try it when I get home.

---

### Post by Daniel Rehm on 2005-08-25
[QUOTE=Daniel Rehm]So! I've decided I prefer beep to xmms, but I'm addicted to the gxmms applet. To my delight, I discover it works with beep... sort of. Hitting play still opens xmms by default. I don't want to have to mess with the application menu every time I want to start my media player! That defeats the whole purpose! Thinking I'm oh so clever, I uninstall xmms. This, of course, renders gxmms unusable. Curses! 

So here is my question:

Is there either a way to make the gxmms applet work without xmms installed OR is there an equivalent applet just for beep?[/QUOTE]
Found 0.3.0 but now I'm having difficulty compiling and installing the applet =-/

according to the website the command I use is
```
./configure gxmms-0.3.0.tar.gz --with-bmp --prefix=/usr --libexecdir=/usr/lib/gnome-applets
```

and everything goes fine until the very end...
```
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for gxmms-0.3.0.tar.gz-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gxmms-0.3.0.tar.gz-gcc... gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for gxmms-0.3.0.tar.gz-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME_APPLETS_CFLAGS...
checking for GNOME_APPLETS_LIBS...
Package libpanelapplet-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpanelapplet-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpanelapplet-2.0' found
configure: error: Package requirements (gtk+-2.0 >= 2.0.0
                                 libpanelapplet-2.0 >= 2.0.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

I installed the closest thing synaptic had to "libpanelapplet-2.0" which was "libpanelapplet-2.6.1" which you would *think* would get the job done... sadly, that's not the case!

Where do I go from here?

---

