---
title: "Interesting error when compiling xine"
date: 2005-10-26
forum: General Help
---

### Post by anton123 on 2005-10-26
Hello,

I say interesting because I did not get this error in Ubuntu 5.04 when compiling xine 1.0.1/1.0.2

Right now, I try to compile either xine 1.0.3 or 1.1.0, however towards the end of the configuration step (running ./configure) I get this error:

****************************************************************
WARNING! No X11 output plugins will be built.

For some reason, the requirements for building the X11 video
output plugins are not met. That means, that you will NOT be
able to use the resulting xine-lib to watch videos in a window
on any X11-based display (e.g. your desktop).

If this is not what you want, provide the necessary X11 build
dependencies (usually done by installing a package called
XFree86-devel or similar) and run configure again.
****************************************************************

How come I did not see this in Ubuntu 5.04? If a xorg package exists somewhere in the repository, what is its name?

Thank you

---

### Post by RAOF on 2005-10-26
You probably want to search for xorg dev packages in synaptic.  Failing that, find out the dependencies of xine, and install the -dev versions of those packages.

---

### Post by anton123 on 2005-10-26
Ok, since I am very new to Linux, what exactly are the names of those xorg development packages? I tried to look for xorg and dev combined but I have seen xorg-server-core and never seen something like xorg-server-dev or xorg-server-core-dev, etc

---

### Post by anton123 on 2005-10-26
Is it maybe libx11-dev?

Just tried to install it and rerun the configuration script for xine but I still get the same error

---

### Post by RAOF on 2005-10-26
That would be one.  Searching in synaptic for "xorg dev", searching package names and descriptions brought up a big list of libx(something)-dev packages.

But even better would be:  earlier in the output of ./configure, there should have been something like
```
Searching for X (whatever libs)... failed
```
If you search for that specific library, and install the -dev version, it should work.  Or, at least fail for a **different** library, and then you can install that one... repeat until it configures correctly :)

---

### Post by anton123 on 2005-10-26
Now trying x-windows-system-dev

---

### Post by anton123 on 2005-10-26
I would like to report to NASA that the mission has succeeded. Thank you.

---

