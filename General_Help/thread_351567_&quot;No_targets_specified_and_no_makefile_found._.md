---
title: "&quot;No targets specified and no makefile found.  Stop.&quot;"
date: 2007-02-02
forum: General Help
---

### Post by wersdaluv on 2007-02-02
I have always had a problem with installing from source whenever running "make."

**What I have tried**
I did exactly what [the screencast from "How to install ANYTHING in Ubuntu."]("http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif")

**What Happened In some installations**
This is what happened when I tried to install the Avant Window Navigator.
After successfully running "./configure" in the directory where I extracted the tar.gz, I entered make and what happened is...
```
user@Laptop:~/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.

```


The same thing happened to me after trying to install other applications like Audacious, Bittyrant, and BasKet 6.1 Beta 3.

What can solve the problem?

:guitar:

---

### Post by wersdaluv on 2007-02-02
Is there an easier way than the "make thing?" Can I just "sudo apt-get install" this?

---

### Post by wersdaluv on 2007-02-02
Bump bump bump... bump

How do I specify the targets for make and where could I target it?

---

### Post by konst88 on 2007-02-02
Are toy sure the configure script ran successfully without errors?
Does it ended with creating config files?

---

### Post by lamego on 2007-02-02
You can't apt install it because its not available on the repositories.
I am sure that configure has reported an error because of missing libraries :)

---

### Post by wersdaluv on 2007-02-02
> **konst88 said:**
> Are toy sure the configure script ran successfully without errors?
Does it ended with creating config files?

Good question. I just ran the configure script for Avant Window Navigator again and at the end of the console, what was written was:
```
checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I tried looking for those packages in Adept but I didn't find them.

So most probably, those dependencies are the problem, right?

Where can I get those packages?

---

### Post by konst88 on 2007-02-02
Search for this packages started with lib and ends with -dev.
For example:libglib2.0-dev

---

### Post by wersdaluv on 2007-02-03
> **konst88 said:**
> Search for this packages started with lib and ends with -dev.
For example:libglib2.0-dev

Thanks for that. I found libglib2.0-dev, but as for the other packages, I didn't find a "lib"+"-dev" counterparts. What do I do with that?

By the way, what does "lib" and "-dev" have to do with installations? What are they? Sorry. I'm very new with this.

:guitar:

---

### Post by wersdaluv on 2007-02-03
I successfully ran "make" (thanks to const88!). 

After that, I ran, make check. What happened was this:
```

vant-window-navigator-0.1.1'
user@Laptop:~/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1$ make check
Making check in src
make[1]: Entering directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/src'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/src'
Making check in data
make[1]: Entering directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data'
Making check in active
make[2]: Entering directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data/active'
make[2]: Nothing to be done for `check'.
make[2]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data/active'
make[2]: Entering directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data'
make[2]: Nothing to be done for `check-am'.
make[2]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data'
make[1]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/data'
Making check in po
make[1]: Entering directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/po'
make[1]: *** No rule to make target `../avant-preferences/avant-preferences.py', needed by `avant-window-navigator.pot'.  Stop.
make[1]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/po'
make: *** [check-recursive] Error 1
user@Laptop:~/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1$    
```

What is "make[1]: *** No rule to make target `../avant-preferences/avant-preferences.py', needed by `avant-window-navigator.pot'.  Stop.
make[1]: Leaving directory `/home/allan/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1/po'
make: *** [check-recursive] Error 1"? How can I fix this?

---

### Post by konst88 on 2007-02-03
Are you sure the configure script finished working?
It should end without eny error.
And you should do the make in the directory you did the configure.

---

### Post by david_2001 on 2007-02-03
> **wersdaluv said:**
> I have always had a problem with installing from source whenever running "make."

**What I have tried**
I did exactly what [the screencast from "How to install ANYTHING in Ubuntu."]("http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif")

**What Happened In some installations**
This is what happened when I tried to install the Avant Window Navigator.
After successfully running "./configure" in the directory where I extracted the tar.gz, I entered make and what happened is...
```
user@Laptop:~/Extracted Files/AvantWindowNavigator/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.

```

A word to the wise - when preparing to install from source always read the included INSTALL and README files first.  In this case, the INSTALL file is standard issue but the README contains the following:
> avant-window-navigator	0.1.1

./autogen.sh --prefix=/usr && make && make install

enjoy!!
Basically, running configure won't work.  Note that the third command should be "sudo make install" for Ubuntu and that it's generally more convenient to use checkinstall (it's in the repositories) rather than make install.

The [Google Code]("http://duggmirror.com/linux_unix/Finally_A_Great_OSX_Like_Dock_For_Linux_Thanks_To_Google/") page for this project isn't terribly helpful about dependencies
> Awn is written in C and uses Gtk & GConf. Avant-preferences is written in python, and needs pygtk and the python bindings to gconf.
Awn needs a composited environment to run in, therefore you should be running either AIGLX or XGL with a compositor (such as Compiz or Beryl). It also depends on libwnck (libwnck-devel), and you will need all the usual development packages on your computer to install it.
but there's enough to get started and the information is at least consistent with the configure errors you're getting.

---

### Post by wersdaluv on 2007-02-03
> **konst88 said:**
> Are you sure the configure script finished working?
It should end without eny error.
And you should do the make in the directory you did the configure.

I ran the configure script again and found some "no" at the end of some checks.

I just read this in FunnyLookinHat's thread:
> NOTE: You will need to be running either XGL or AIGLX along with a composite window manager (usually beryl or compiz). I am running AIGLX and beryl, in case you were wondering.

After reading that, I found out that I can't use the app after all since my laptop videocard can't run XGL or Beryl stuff.

Okay, so I'll try to install another app. 

Here's a question, what if the app doesn't have a configure script?

---

