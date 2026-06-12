---
title: "xword install problems - gcc"
date: 2006-12-25
forum: General Help
---

### Post by bjones01 on 2006-12-25
I'm trying to install xword. The readme file tells me to run ./configure. When I do, i get a lot of missing files, but at the moment, what I'm concentrating on is the fact that gcc can't seem to create executables. Any hints? Thanks.

bjones01@bjones01-laptop:/tmp/xword-0.07$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.

If I drop down to the src directory, and try to run gcc, this is what I get:

bjones01@bjones01-laptop:/tmp/xword-0.07/src$ gcc main.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory

---

### Post by hanzomon4 on 2006-12-26
Run this ```
sudo aptitude install build-essential
```

---

### Post by bjones01 on 2006-12-26
Thanks. That got me past the C++ problem. I'm surprised the default installation didn't install C.

It's now stuck on GTK. The ./configure says:

checking for GTK-- - version >= 1.2.5... no
*** The gtkmm-config script installed by GTK-- could not be found
*** If GTK-- was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTKMM_CONFIG environment variable to the
*** full path to gtkmm-config.
*** The gtkmm-config script was not available in GTK-- versions
*** prior to 0.9.12. Perhaps you need to update your installed
*** version to 0.9.12 or later
configure: error: Cannot find correct Gtk-- version


I went looking for gtk on my installation. I see signs of it in /etc, and /usr/bin/gtk-query-immodules-2.0, but that's as far as I could get. I'm pretty sure there are other gtk application in the install because synaptics shows that things are installed that use it.

 I tried 'aptitude install GTK', also with lower case gtk, with no luck.

Any ideas would  be appreciated.

---

### Post by hanzomon4 on 2006-12-26
You may be missing some dev packages, Try this ```
sudo aptitude install  libgtk2.0-dev libgtk1.2-dev libgtkmm-2.4-dev
```

---

### Post by bjones01 on 2006-12-26
Thanks. It install quite a bunch of stuff, but I'm still getting the same error.

---

### Post by hanzomon4 on 2006-12-26
Can you give me a link to where I can download it so I can try compiling it?

---

### Post by bjones01 on 2006-12-26
Well, I learned not to install things in /tmp!

I also couldn't find the original download site, but I found this one, which has a higher version number, but it's not a package, it needs to be compiled manually I think.

[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/X-word-15446.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/X-word-15446.shtml)

I'm not sure where to start.

I guess you can tell I'm a linux newbie, but I'm determined to find an alternative to Vista before the DRM trap closes.

---

### Post by bjones01 on 2006-12-26
Ah! The text file turns out to be Python, and it runs fine.

Thanks for all the help . . . on to the next issue . . . 

Barry

---

