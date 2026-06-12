---
title: "Unable to find X11 libraries"
date: 2007-09-08
forum: General Help
---

### Post by NTITech on 2007-09-08
```

nticompass@nticompass-laptop:~/plugger-5.1.3$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for atexit in -ldl... yes
configure: error: Unable to find X11 libraries

```

This is what I get when I try to compile plugger.  Where are the X11 libraries?  I've already instaled libx-dev, x11-dev, and build-essential.  What should I do now?

---

### Post by andion on 2007-09-25
> **NTITech said:**
> ```

nticompass@nticompass-laptop:~/plugger-5.1.3$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for atexit in -ldl... yes
configure: error: Unable to find X11 libraries

```

This is what I get when I try to compile plugger.  Where are the X11 libraries?  I've already instaled libx-dev, x11-dev, and build-essential.  What should I do now?

I've got this information from another Forum:

Plugger has not be maintained since 2001, why don't you try mozplugger instead?

[http://mozplugger.mozdev.org/](http://mozplugger.mozdev.org/)

I've tried it, and it works!

---

### Post by NTITech on 2007-09-25
thanks, that works great for me :P

---

