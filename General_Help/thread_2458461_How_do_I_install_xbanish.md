---
title: "How do I install xbanish?"
date: 2021-02-24
forum: General Help
---

### Post by robert99999 on 2021-02-24
Trying to make the mouse pointer disappear when I start typing, I discovered that this feature is not inherent in the window manager, and so I need to install xbanish.
[https://github.com/jcs/xbanish](https://github.com/jcs/xbanish)
However, the github repository doesn't have any prebuilt versions. So, I downloaded the project and tried to run the makefile. I found that "make" is not on my system, so I installed it. I ran make but it failed because cc is not on my system, so I installed it. Ran make again, but it failed because X11/X.h couldn't be found. At this point, I gave up. Is there an easier way to install xbanish?

---

### Post by HermanAB on 2021-02-25
Are you running an Xorg based system or a Wayland based system?

People who don’t understand UNIX are doomed to reinvent it.  That is what happens with Linux over and over again.  For example Init, Alsa, X etc.  New guys don’t understand something, rewrite it from scratch and sometimes it is better, sometimes not.  

Wayland is one of the latter.

---

### Post by robert99999 on 2021-02-25
Sorry, I should have mentioned that I'm running Xorg, I think. It's whatever the the 20.04 LTS installation defaults to. I thought Xorg and X were the same thing.
Are you suggesting that xbanish may not be necessary?

---

### Post by Holger_Gehrke on 2021-02-26
No, he's telling you that it probably will not work if you're using Wayland.

If you want to compile from source, you need additional packages with header files (c source files which tell the compiler what functions are in which libraries).
After a short look at the source I'd say you should run
```

sudo apt install build-essential x11proto-dev libx11-dev libxfixes-dev libxi-dev

```
'build-essential' installs make, the c compiler, the c++ compiler, the headers for libc and tools for building .deb-files. The others are developers packages containing headers for X11 and various extensions to X11. On my XUbuntu 18.04 system (which already had these and many other sets of headers) it compiled without any problems and seems to work as advertised.

If you don't want to compile the program yourself, there's a [PPA]("https://launchpad.net/~minos-archive/+archive/ubuntu/main") that seems to have it.

Holger

---

### Post by TheFu on 2021-02-26
Always prefer using a trusted PPA over compiling yourself.  Of course, an unknown PPA shouldn't be trusted so do a little research about the team/person who setup the PPA. If it is created by the team that creates the software, there is very little risk. After all, you've already agreed to run that code.

---

### Post by robert99999 on 2021-02-26
> **Holger_Gehrke said:**
> No, he's telling you that it probably will not work if you're using Wayland.

After a short look at the source I'd say you should run
```

sudo apt install build-essential x11proto-dev libx11-dev libxfixes-dev libxi-dev

```

Thanks, but it didn't help. It tells me that all of those are already installed, and after it's done and I try 'make' again, I still get this:
```

cc -O2 -Wall -Wunused -Wmissing-prototypes -Wstrict-prototypes -Wunused -I/usr/X11R6/include -c xbanish.c -o xbanish.o
xbanish.c:37:10: fatal error: X11/Intrinsic.h: No such file or directory
   37 | #include <X11/Intrinsic.h>
      |          ^~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [Makefile:28: xbanish.o] Error 1

```

I'd rather compile this myself, if possible, rather than deal with an untrusted repository. The source code and the make file look simple enough that I don't mind trying it as long I don't get stuck in an infinite loop chasing after missing files.

---

### Post by Holger_Gehrke on 2021-02-26
Looks like I missed one. '/usr/include/X11/Intrinsic.h' is in the package 'libxt-dev'. By the way, you can look up files in packages on packages.ubuntu.com (the first form looks for packages that have the search term in its name or description, the second form searches for files in packages).

Holger

---

### Post by TheFu on 2021-02-26
Be sure that libXt is included in the makefile if the link step fails.  That would be a -lXt

I looked at the project source. This is clearly a personal hobby for someone.  If you open some bugs on the documentation, they might consider it helpful.

---

### Post by robert99999 on 2021-02-26
> **Holger_Gehrke said:**
> Looks like I missed one. '/usr/include/X11/Intrinsic.h' is in the package 'libxt-dev'. By the way, you can look up files in packages on packages.ubuntu.com (the first form looks for packages that have the search term in its name or description, the second form searches for files in packages).

Holger

Thanks. I installed that, and the make file now runs and compiles properly.
Next problem: I realized that I didn't know what to to to make it run when the system boots up, but I found the following at [https://github.com/jcs/xbanish/issues/47](https://github.com/jcs/xbanish/issues/47)
```

cd xbanish
echo "~/xbanish/xbanish" >> ~/.xinitrc

```
It's now working as I wanted, but it occurs to me that before installing xbanish, the pointer had been hiding automatically in some applications such as the text editor, but not in others such as Firefox. With xbanish installed, it's now hiding in Firefox.
Hopefully, I haven't accidentally done something that will eventually destroy my system.
Thanks all.

EDIT:
BTW, it was good to actually build and install an application for my first time ever. I've done a lot of automated installs, but I don't learn anything from doing that. It's nice to find out where all of these things are getting installed.

---

### Post by robert99999 on 2021-02-27
I'd marked this thread as Solved last night, but I've now changed it  back to Unsolved, because xbanish doesn't appear to be running at boot  time. Or, if it is, it must be quitting at some point. If I open a  terminal session and run it, the mouse pointer hiding works. But as soon  as I end the terminal session, I'm back to the non-hiding pointer. As mentioned in my previous post, I ran the following:
```

cd xbanish
echo "~/xbanish/xbanish" >> ~/.xinitrc

```
and it created the file .xinitrc in the home directory. I confirmed that the contents of the file are:
```

~/xbanish/xbanish

```
But apparently I'm still missing a step somewhere.

---

### Post by Holger_Gehrke on 2021-02-28
> **robert99999 said:**
> If I open a  terminal session and run it, the mouse pointer hiding works. But as soon  as I end the terminal session, I'm back to the non-hiding pointer.


Which is as expected. xbanish doesn't just make some settings, it keeps running and waits for input events and hides or shows the mouse pointer depending on whether the last event was a mouse or keyboard event. If you exit a program the program tells any other programs it started to shut down. So you close the terminal, the terminal closes the shell and the shell closes xbanish.

AFAIK ~/.xinitrc only gets called if you're starting the GUI through xinit, for example by logging in in text mode and then running startx. If you're logging in graphically using some display manager it doesn't get called. Depending on the Desktop Environment you're using there should be a tool to set up programs to start with your session (in XFCE - which is what I'm using - it's called 'Session and Startup' and can be found in the 'Settings'-part of the whisker menu; there should be something similar in any other DE). Another way to do it is to create a [.desktop-file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/") for xbanish and put it in ~/.config/autostart.

Holger

---

### Post by robert99999 on 2021-03-01
That helps explain something that had confused me. The documentation on github mentioned xinit, but I couldn't find either an xinit directory or file on my system. I'll put together a .desktop file and try the autostart method as soon as I have a spare moment.

Meanwhile, I've noticed that applications, which I assume use the GTK3 library, will automatically hide the pointer. It seems to be those such as LibreOffice and the Mozilla applications, that use a their own graphics library, that don't play nicely. Unfortunately, those happen to be the applications that I use about 95% of the time. I also develop cross-platform (Mac/Win/Linux) GUI applications using Xojo, which uses GTK3 for Linux, and these also correctly hide the pointer. So, maybe we need to give the LibreOffice and Mozilla people a little prod to clean up their user interface.

---

### Post by Holger_Gehrke on 2021-03-02
I think hiding the mouse pointer after a period of inactivity is something you have to put in your program yourself - searching for 'GTK hide mousepointer' brought up lots of pages describing how to do it but none describing any kind of automatism. According to 'apt show firefox' Firefox depends on gtk-3 (>= 3.4), so I think Firefox actually uses GTK. Hiding the mouse pointer is also possible in QT, since the reader component of calibre (using python-pyqt5) also does it.

While looking for information on this (I had hopes that it might be user-configurable ...) I came across unclutter, which serves the same purpose as xbanish and actually is in the repositories under that name.

Meanwhile I actually have the opposite problem usually: not seeing the pointer hiding somewhere in all the stuff on screen. Thankfully there's a tool for that in XFCE (my DE of choice) named xfce-find-pointer, which can be assigned to a keyboard shortcut to make the position of the pointer really obvious: concentric red circles spreading from the mouse pointer are kind of hard to overlook ... There probably is something like that in other DEs, too.

Holger

---

### Post by robert99999 on 2021-03-02
Unclutter was the first thing I looked at, but everything I read about it indicated that it had quickly become broken with a new system update, or that it had never worked correctly in the first place. So, I didn't bother to try it.

BTW, I'm not trying to hide the mouse pointer after a period of inactivity. I want to hide the pointer as soon as I start typing, so that the pointer isn't obscuring what I'm trying to type.

---

