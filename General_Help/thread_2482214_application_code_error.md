---
title: "application code error"
date: 2022-12-24
forum: General Help
---

### Post by cmcanulty on 2022-12-24
I am trying to get a chess program to work and am getting errors that I don't understand how to fix. I did do one fix already but that didn't help. I did this:



Twitter:@ComDannyda | Facebook | Instagram

Donate 	
Posted on 22 February, 2022
How to Fix “E: You must put some ‘deb-src’ URIs in your sources.list” on Debian/Ubuntu/Kali Linux etc.
The Issue
```

    When trying to execute sudo apt source package_name or sudo apt-get source package_name ( sudo apt source postfix or sudo apt-get source postfix ) or sudo apt build-dep package_name or sudo apt-get build-dep package_name we get an error like following

E: You must put some 'deb-src' URIs in your sources.list
The Fix

Usually this is caused by that deb-src in the /etc/apt/sources.list file are not enabled (Commented out) Refer to: Default contents of sources.list in Ubuntu 20.04.1 LTS Desktop/Server

We can simply create a backup version of /etc/apt/sources.list file then remove “#” from all deb-scr lines to enable them using the below commands

sudo cp /etc/apt/sources.list /etc/apt/sources.list~
sudo sed -Ei 's/^# deb-src /deb-src /' /etc/apt/sources.list
sudo apt update
```


Here is the terminal output with errors I get: 


```

cmcanulty@Dell660s:~$ scidb-beta
26	../sysdeps/unix/sysv/linux/read.c: No such file or directory.
(func) invoke
(file) tcl_base.cpp:741
(what) bad option "fullscreen": must be cget or configure
(type) tcl::Error

=== Backtrace ============================================
 tcl::invoke [tcl_base.cpp:741]
 (anonymous namespace)::Node::performFullscreen [tk_twm.cpp:6704]
 (anonymous namespace)::Node::performFinalizeCreateRecursively [tk_twm.cpp:7331]
 (anonymous namespace)::Node::performDeiconifyFloats [tk_twm.cpp:7616]
 (anonymous namespace)::Node::perform [tk_twm.cpp:7781]
 cmdLoad [tk_twm.cpp:8069]
 execute [tk_twm.cpp:8915]
 cmdTwm [tk_twm.cpp:8993]
 safeCall [tcl_base.cpp:1056]
 main [tkscidb.cpp:110]
==========================================================

Error in startup script: bad option "fullscreen": must be cget or configure
    invoked from within
"::scidb::tk::twm load $twm {*}$args "
    (procedure "::twm::WidgetProc" line 65)
    invoked from within
"::twm::WidgetProc .application.nb.board $command {*}$args"
    (procedure ".application.nb.board" line 1)
    invoked from within
"$twm load $layout"
    (procedure "twm::load" line 12)
    invoked from within
"twm::load $twm"
    (procedure "application::open" line 50)
    invoked from within
"application::open"
    (file "/usr/local/bin/scidb-beta" line 152276)
26	../sysdeps/unix/sysv/linux/read.c: No such file or directory.
(func) mainWindow
(file) tk_base.cpp:146
(what) no main window exists
(type) tcl::Exception

=== Backtrace ============================================
 tk::mainWindow [tk_base.cpp:146]
 tk::exists [tk_base.ipp:118]
 tk::exists [tk_base.ipp:122]
 tk::isAlreadyDead [tk_base.cpp:136]
 (anonymous namespace)::Node::isAlreadyDead [tk_twm.cpp:1610]
 (anonymous namespace)::Node::destroyed [tk_twm.cpp:3813]
 WindowEventProc [tk_twm.cpp:1594]
 main [tkscidb.cpp:110]
==========================================================

terminate called after throwing an instance of 'tcl::Exception'
Aborted (core dumped)
cmcanulty@Dell660s:~$ 

```

---

### Post by norobro on 2022-12-24
I'm not sure what you are doing with your sources.list file. From where are you getting the source code?

And I don't have a clue about the errors but I built scidb-beta last summer on a Debian system using the following steps and just successfully compiled and ran it on Ubuntu 22.04.

Download the source from here: [https://scidb.sourceforge.net/download.html](https://scidb.sourceforge.net/download.html)
untar the the downloaded file
Make the changes described here: [https://sourceforge.net/p/scidb/bugs/210/](https://sourceforge.net/p/scidb/bugs/210/)  
Download the patch files and the shell script to the untarred root directory and run revise-patch.sh
Then run:```
export CFLAGS="-fcommon" CXXFLAGS="-fcommon"
./configure
make clean
make
sudo make install
```

HTH

---

### Post by stroyan on 2022-12-24
The original question was posted back in Februrary, before 22.04 was released.
The problem may have gone away when upgrading to 22.04, which is listed in cmcanulty's current profile.
It looks like an error from an older version of tcl.tk that did not implement "fullscreen".
That error is listed at  [https://sourceforge.net/p/scidb/bugs/208/](https://sourceforge.net/p/scidb/bugs/208/)  which remains open.

---

### Post by cmcanulty on 2022-12-24
Thanks I did all that and still it starts up the splash screen then crashes with errors below. I am also attaching a file I did as a tutorial for installing scidb on ubuntu 22.04 that works fine for installing scidb on a bunch of computers but fails on my main machine


```

cmcanulty@Dell660s:~$ scidb-beta %F
26	../sysdeps/unix/sysv/linux/read.c: No such file or directory.
(func) invoke
(file) tcl_base.cpp:741
(what) bad option "fullscreen": must be cget or configure
(type) tcl::Error

=== Backtrace ============================================
 tcl::invoke [tcl_base.cpp:741]
 (anonymous namespace)::Node::performFullscreen [tk_twm.cpp:6704]
 (anonymous namespace)::Node::performFinalizeCreateRecursively [tk_twm.cpp:7331]
 (anonymous namespace)::Node::performDeiconifyFloats [tk_twm.cpp:7616]
 (anonymous namespace)::Node::perform [tk_twm.cpp:7781]
 cmdLoad [tk_twm.cpp:8069]
 execute [tk_twm.cpp:8915]
 cmdTwm [tk_twm.cpp:8993]
 safeCall [tcl_base.cpp:1056]
 main [tkscidb.cpp:110]
==========================================================

Error in startup script: bad option "fullscreen": must be cget or configure
    invoked from within
"::scidb::tk::twm load $twm {*}$args "
    (procedure "::twm::WidgetProc" line 65)
    invoked from within
"::twm::WidgetProc .application.nb.board $command {*}$args"
    (procedure ".application.nb.board" line 1)
    invoked from within
"$twm load $layout"
    (procedure "twm::load" line 12)
    invoked from within
"twm::load $twm"
    (procedure "application::open" line 50)
    invoked from within
"application::open"
    (file "/usr/local/bin/scidb-beta" line 152276)
26	../sysdeps/unix/sysv/linux/read.c: No such file or directory.
(func) mainWindow
(file) tk_base.cpp:146
(what) no main window exists
(type) tcl::Exception

=== Backtrace ============================================
 tk::mainWindow [tk_base.cpp:146]
 tk::exists [tk_base.ipp:118]
 tk::exists [tk_base.ipp:122]
 tk::isAlreadyDead [tk_base.cpp:136]
 (anonymous namespace)::Node::isAlreadyDead [tk_twm.cpp:1610]
 (anonymous namespace)::Node::destroyed [tk_twm.cpp:3813]
 WindowEventProc [tk_twm.cpp:1594]
 main [tkscidb.cpp:110]
==========================================================

terminate called after throwing an instance of 'tcl::Exception'
Aborted (core dumped)
cmcanulty@Dell660s:~$ 
```

---

