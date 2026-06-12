---
title: "Korganizer and Kpilot won't sync with Palm"
date: 2006-11-03
forum: General Help
---

### Post by xvila on 2006-11-03
Hi:
After upgrading to kubuntu edgy eft, korganizer fails to sync with my Palm Tungsten T3 Datebook.
New entries in Palm are correctly introduced in Korganizer, but the other way around does not work at all. That is, new entries in Korganizer are not synced to Palm Datebook.
According to Kpilot's HotSync log, things go well and everything looks normal... but the problem remains no matter what I do.
Here is the log of a "typical" sync operation:

15:36:34 Device link ready.
15:37:15 Checking last PC...
15:37:16 KPilot 4.6.0 (blivit) HotSync starting...

15:37:16 Using encoding UTF-8 on the handheld.
15:37:16 [File Installer]
15:37:16 No Files to install
15:37:16 [Internal Editors]
15:37:16 Databases with changed records: 
15:37:16 Databases with changed flags: 
15:37:16 Databases with changed AppBlock: 
15:37:16 [Conduit knotes-conduit]
15:37:16 Could not retrieve list of notes from KNotes. The KNotes conduit will not be run.
15:37:16 The conduit knotes-conduit could not be executed.
15:37:16 [Conduit time_conduit]
15:37:16 Setting the clock on the handheld
15:37:17 [Conduit vcal-conduit]
15:37:17 Using non-local time zone: Europe/Paris
15:37:17 Syncing with file "/home/xvila/.kde/share/apps/korganizer/xavi.ics"
15:37:17 Copying records to PC ...
15:37:17 Copying records to Pilot ...
15:37:17 [Conduit memofile-conduit]
15:37:17  Syncing with /home/xvila/MyMemos.
15:37:17  Doing regular sync...
15:37:18 4 new to Palm. 4 deleted from Palm. 
15:37:19 [Conduit abbrowser_conduit]
15:37:27 [File Installer]
15:37:27 No Files to install
15:37:27 End of HotSync

15:37:27 HotSync Completed.

Any ideas ? Anyone with the same problem ?
The worse thing is that in one of the many attempts the Palm Datebook got completely erased (so, I have now many appointments in Korganizer and none in Palm's Datebook !)

thanks in advance

Xavi

---

### Post by xvila on 2006-11-06
Nobody has a similar problem ??
thanx

---

### Post by TransitMan on 2006-11-06
I am running into a very frustrating problem with Edgy and my Palm m500.
It syncs fine, but will not import to the Palm the calanders from Kontact or Evolution. The address database imports and can be read just fine.
Any suggestions...........................](*,) ](*,)

---

### Post by yurtboy on 2006-11-07
Yep.  No longer works Kpilot --> Palm 3

---

### Post by xvila on 2006-11-07
Well, the problem seems solved to me.
It seems that the issue is in the kpilot version shipped with kubuntu Edgy Eft.
I got the latest kpilot code from svn (this has been my first "subversive" adventure !!), compiled and installed it.
And then, it worked !!
My Palm returned to sanity. Now I can sync both ways my calendar in kontact (Korganizer) with my Palm Datebook.

I guess that this could be considered as something that knowledgeable people calls a "bug", but I am not sure neither know how to tell kubuntu's administrator.

(By the way, I tried out different versions of pilot-link and none worked. So, the problem must be Kpilot indeed)

xavi

---

### Post by TransitMan on 2006-11-07
Any chance of you uploading your compiled KPilot .deb for those of us not smart enough to roll our own?

---

### Post by xvila on 2006-11-07
Sorry ! Do not know how to create .deb packages.

I think, though, that it is really easy to compile from source.
Here is what I did:

1) get the latest development sources 

[INDENT]$ svn co [https://cvs.codeyard.net/svn/kpilot/trunk/](https://cvs.codeyard.net/svn/kpilot/trunk/)[/INDENT]

This will create a new directory named "trunk" and will download the sources into it. 

2) Make sure you have kdepim-dev installed

[INDENT]$ sudo apt-get install kdepim-dev[/INDENT]

3) Get into the newly created directory "trunk"

[INDENT]$ cd trunk[/INDENT]

4) Compile it !

[INDENT]$ make[/INDENT]

5) Install it

[INDENT]$ sudo make install[/INDENT]

You can find a more "terse" explanation at

[INDENT][http://cvs.codeyard.net/kpilot/develop.php](http://cvs.codeyard.net/kpilot/develop.php)[/INDENT]

Hope it works for you !

xavi

---

### Post by TransitMan on 2006-11-07
Thank you, thank you.
It worked, after an initial failure.

This should be put up as a "How To" for those who are having problems with their Palm Pilots.

---

### Post by xvila on 2006-11-08
Well, I don't think it's worth a "How To" (also, I do not know how to use the Wiki system in Ubuntu !). It is probably more important to let the developers know so that they can fix it.

I was going to file a bug, but I found that it has already been reported. 

[https://launchpad.net/distros/ubuntu/+source/kdepim/+bug/66313](https://launchpad.net/distros/ubuntu/+source/kdepim/+bug/66313)

So, I guess that sooner or later the development team will pay attention to it and produce new packages.

xavi

---

### Post by fgosse on 2006-11-14
Hi,

Do you know where and when can i find a package for edgy ?

Thanks a lot

F.G

---

### Post by ym4546 on 2006-11-23
You might also need the package libpisock-dev and cmake (especially if you're using a svn revision in the 600s).

---

### Post by chikko on 2006-11-25
hey!

i've been trying to follow your steps, but got into this problem:
```

:~/trunk$ sudo make
test -d "build-Linux2_6_17_10_generic" || mkdir -p "build-Linux2_6_17_10_generic"
test -d "build-Linux2_6_17_10_generic"
SRC_DIR=`pwd` ; cd "build-Linux2_6_17_10_generic" && cmake $SRC_DIR 
/bin/sh: cmake: not found
make: *** [build-check] error 127
```
any idea..? :(

i'm using Edgy (ubuntu 6.10), and already installed kdepim-dev.
what's more - when i simply tried to run "make" it didn't do anything, so i figured i should run "./configure" first, but all it did was to say something like "hello, there - please use make" - so i did, and the answer is up there, in the code box..

please help...?  :)
thanks.

---

### Post by fatejudger on 2006-11-26
chikko, you need to apt-get cmake.

---

### Post by chikko on 2006-11-26
thanks fatejudger - i've installed it :)

but now i got another issue here:

i'm trying to sudo make and getting this message:

```
-- Found KDE3 include dir: /usr/include/kde
-- Found KDE3 library dir: /usr/lib
-- Found KDE3 dcopidl preprocessor: /usr/bin/dcopidl
-- Found KDE3 dcopidl2cpp preprocessor: /usr/bin/dcopidl2cpp
-- Found KDE3 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Could not find pi-dlp.h
-- Could not find libpisock
-- KPilot requires pilot-link 0.12.1 or later. Pilot-link is available from pilot-link.org and is packaged by most distributions. Remember to install the development package with the compilation headers as well.
CMake Error: Error in cmake code at
/home/chikko/trunk/cmake/modules/FindPilotlink.cmake:34:
MESSAGE Could not find pilot-link.
Current CMake stack: /home/chikko/trunk/CMakeLists.txt;/usr/share/CMake/Modules/CMakeCInformation.cmake;/usr/share/CMake/Modules/CMakeCXXInformation.cmake;/home/chikko/trunk/cmake/modules/FindPilotlink.cmake
-- Configuring done
make: *** [build-check] 255 &#1492;&#1500;&#1511;&#1514;

```

so the first thing i did was to sudo apt-get install pilot-link, but that didn't seem to make any difference..
what's next..?  :(

thanks!!!

---

### Post by fatejudger on 2006-11-26
Chikko, you have to install kdepim-dev per the instructions on the first page of this thread.

On another note, I personally can't seem to install kpilot properly as the included kpilot package seems to overwrite the new one. If I remove the kpilot package that I got from the Edgy repos, I end up with a slightly crippled version of kpilot that lacks config dialogs and hotsync options, and works no better than the one in the Edgy repos. I'm not sure whether this is because the folks at kpilot are still working on a fix, but any advice would help.

---

### Post by MagnusL on 2007-01-12
Just a mistake- can I erase this post?

---

### Post by bouncingmolar on 2008-01-02
> **xvila said:**
> 

Hope it works for you !

xavi

So do your Knotes sync properly?

---

