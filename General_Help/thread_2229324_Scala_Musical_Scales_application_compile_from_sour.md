---
title: "Scala Musical Scales application compile from source errors"
date: 2014-06-12
forum: General Help
---

### Post by life in color on 2014-06-12
Hi, I'm new to compiling an application from source and I've run into a few problems.

The .tar.bz2 files is too large to post on the forum, so here is the URL for the application's download:[HTML]http://www.huygens-fokker.org/scala/downloads.html[/HTML]

```
./configure
``` produces nothing, so I was trying to work off the INSTALL text file, but the instructions are a little confusing to me.
It suggests that you install "Gtk+ 2.24.0 runtime or higher (present in recent distros)GtkAda 2.24 (libgtkada-2.24.so.0 file is included)
GNAT 4.6 runtime (install from your distro provider). On Ubuntu, you can 
download and install package libgnat-4.6." of which I was able to install gnat, but upon trying to install Gtk+2.24.0 and GtkAda 2.24 I ran into a lot of trouble. Can anyone give me the most efficient method to compile and install this software? I would really appreciate it.

---

### Post by Bucky Ball on 2014-06-12
*Thread moved to **General Help**.*

***Installation & Upgrades*** is for, "... questions about upgrading and installation of your new Ubuntu OS". ;)

---

### Post by steeldriver on 2014-06-12
Are you sure the thing you downloaded is actually a source tarball? the Linux ones I found via your link are pre-compiled binaries, I downloaded the 32-bit one and was able to run it just by cd'ing to the containing directory and typing ./scala

---

### Post by Bucky Ball on 2014-06-12
Have you done this?

 > On Ubuntu Linux, install the following packages:

    aconnectgui (recommended)
    gnuplot (if not installed yet, dependency only if graphic plots are made)
    libgnat-4.6
    playmidi (recommended)
    timidity (recommended) 

For all Linux distros, read the file INSTALL for instructions.

---

### Post by life in color on 2014-06-12
[COLOR=#000000]"Have you done this?[/COLOR]

[COLOR=#000000][I]On Ubuntu Linux, install the following packages:

aconnectgui (recommended)
gnuplot (if not installed yet, dependency only if graphic plots are made)
libgnat-4.6
playmidi (recommended)
timidity (recommended) 

For all Linux distros, read the file INSTALL for instructions.
[/I]
[/COLOR]
"
No, not for playmidi, aconnectgui, gnuplot, or timidity. I couldn't find a simple install for them. Would I need to compile from source? And if they are pre-compiled binaries, I didn't know about it, that sounds a lot easier than what I've been trying to do. I did try ./scala within the folder, but it gave me an assortment of errors, which I can post if you'd like.

---

### Post by life in color on 2014-06-12
Actually I just checked and [COLOR=#000000]playmidi, aconnectgui, gnuplot, and timidity are all installed and up to date. I moved the executable scala file to /usr/bin and then typed ```
./scala
``` only to receive ```
[/COLOR]griffin@griffin-S300CA:/usr/bin$ ./scala[COLOR=#000000]
[/COLOR]
./scala: error while loading shared libraries: libgtkada.so.2.24.1: cannot open shared object file: No such file or directory[COLOR=#000000]
```[/COLOR]

---

### Post by steeldriver on 2014-06-12
As mentioned in the tarball's INSTALL file, you need to install the libgtkada.so.2.24.1 library - the instructions say to copy the file (which is provided in the archive) to /usr/local/lib and manually run ldconfig HOWEVER since libgtkada2.24.1 is in the repository (at least on 12.04) I suggest you just install that instead, either via Software Center / synaptic or from the command line using

```

sudo apt-get install libgtkada2.24.1

```

You may need to also set a SCALA_HOME environment variable in order for the program to find the rest of the files e.g.

```

SCALA_HOME=*/path/where/you/unpacked/*scala-22-pc-linux scala

```

---

### Post by life in color on 2014-06-12
I got it working by actually following the instructions fully; I hadn't added ```
export LC_ALL=en_US.UTF-8export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8
``` to ~/.bashrc and ~/.profile yet and once I did it worked. Thanks for the help!

---

### Post by Bucky Ball on 2014-06-12
A simple install? If they weren't already installed they are all two clicks away in Software Centre or Synaptic Package Manager. ALWAYS look there first before complicating things! ;)

---

