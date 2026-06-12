---
title: "Help w/ Installing Various Apps"
date: 2005-05-08
forum: General Help
---

### Post by Monchy on 2005-05-08
Hello Everybody,

I'm going to ask a few big newbie questions here so bare with me. Ubuntu is also my first Linux distro so keep that in mind as well  :) 

Ok here are my questions.

A) When i download a tarball application (assuming that's the right terminology), how can i go about installing the app? I mean i can extract the files inside to desktop, but where do i go from here?

B) .deb files. I just got Opera V8 from there site, the correct version and everything, and when i try to install it, nothing happens.

Here's a portion of my log.

> (Reading database ... 75790 files and directories currently installed.)
Preparing to replace opera 8.0-20050415.5 (using opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
Setting up opera (8.0-20050415.5) ... 

I used the sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb command by the way. Anyway after it finishes doing that, nothing happens, any ideas?

Thank you all in advance and go easy on me :)

---

### Post by Xian on 2005-05-08
[QUOTE=Monchy]I used the sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb command by the way. Anyway after it finishes doing that, nothing happens, any ideas?[/QUOTE]
Open a terminal then type in 'opera' and hit enter. What happens?
Any messages or errors reported?

When you installed opera suing the dpkg command did it finish and present you with a new command prompt in that terminal session?

---

### Post by Xian on 2005-05-08
[QUOTE=Monchy] When i download a tarball application (assuming that's the right terminology), how can i go about installing the app? I mean i can extract the files inside to desktop, but where do i go from here?[/QUOTE]
Read this link on [Compiling and Installing Software in Linux](http://www.tuxfiles.org/linuxhelp/softinstall.html) and post back with further questions.

---

### Post by Monchy on 2005-05-09
> **Xian]Open a terminal then type in 'opera' and hit enter. What happens?
Any messages or errors reported?

When you installed opera suing the dpkg command did it finish and present you with a new command prompt in that terminal session?[/QUOTE]

Hi Xian thank you for your replys :)

Got Opera working finally, didn't know I had to type Opera after installing it, I had kept checking the Applications menu to see it there. I guess i need to stop thinking like a windows user  :-# 

Just reading that link you gave, I'll post back when i have more questions.

Thanks again    said:**
> ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details. 

So now i can't get a Makefile made  ](*,) I went over the steps a few times before starting so pretty sure i didn't mess anything up. Any pointers here?

Thanks again :)

---

### Post by Karlos on 2005-05-09
YOU CAN INSTALL A PROGRAM CALLED MENU WHICH ALLOWS YOU TO RUN "update-menus" IN A TERMINAL .. THAT WOULD SORT OUT YOUR MENUS AFTER ANY CHANGES MADE

---

### Post by Karlos on 2005-05-09
>  			 				./configure
 checking build system type... i686-pc-linux-gnu
 checking host system type... i686-pc-linux-gnu
 checking target system type... i686-pc-linux-gnu
 checking for a BSD-compatible install... /usr/bin/install -c
 checking whether build environment is sane... yes
 checking for gawk... no
 checking for mawk... mawk
 checking whether make sets $(MAKE)... yes
 checking for sed... /bin/sed
 checking for gcc... no
 checking for cc... no
 checking for cc... no
 checking for cl... no
 configure: error: no acceptable C compiler found in $PATH
 See `config.log' for more details. 			 		 

open a terminal and type..

sudo apt-get install build-essential

gaim will install after that

---

### Post by Monchy on 2005-05-09
Aweomse, thank you Karlos, Gaim is installing without a hitch now :)

---

### Post by tread on 2005-05-09
You can install the latest gaim without compiling it too:

1. Add the backports repository to your sources.list

or

2. Use the autopackage installation from the gaim website

---

### Post by Monchy on 2005-05-09
thanks tread, just checked out the autopackage site, that is actually incredibly convienent for new people like me, although i don't mind learning how to compile etc :)

---

### Post by CitricAcid on 2005-05-20
Hello.
I had similar problems with installing. 
I was trying to install KSmoothDock.
I have tried sudo apt-get install build-essential and problem with c went away.
But next error showed up:

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

I typed then locat qt-mt and this is what I have:
/usr/share/qt3/lib/libqt-mt.so.3.3
/usr/share/qt3/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3.3
/usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3

What to do? Help me please.

---

### Post by jobezone on 2005-05-27
Try installing libqt3-mt-dev which is the package for the source(?) and development files of libqt3-mt.

---

### Post by CitricAcid on 2005-05-27
Helped. Thanks :)

---

### Post by CitricAcid on 2005-05-27
I had another error:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

I have installed kdebase-dev and all dependencies and now I can compile :)
Works!!! :D

---

### Post by ivlivs on 2005-06-10
Do you have g++ package installed?
I had a similar problem on a system with g++-3.3 but not g++. Installing g++ too solved it.

---

### Post by CitricAcid on 2005-06-10
As I wrote above it helped after installing kdebase-dev.

But thanks. :)

---

