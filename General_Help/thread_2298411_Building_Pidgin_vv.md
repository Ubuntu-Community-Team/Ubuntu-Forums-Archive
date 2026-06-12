---
title: "Building Pidgin vv"
date: 2015-10-10
forum: General Help
---

### Post by vanili on 2015-10-10
Hello to everyone!

I want to try Pidgin with voice and video support for video calls. However, it seems that there're no Pidgin vv builds for Ubuntu (or I haven't found one), so I've tried to build it by myself, but the make fails wit

```
/usr/bin/ld: gtkmedia.o: undefined reference to symbol 'XSetErrorHandler'
//usr/lib/i386-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line
```

How it is possible to solve this? I'm using Ubuntu 14.04 with pidgin-2.10.11

Thanks in advance

---

### Post by Ubunterrific on 2015-10-11
I think this kind of error can be solved by appending **-lz** to your makefile/LD_FLAGS. 

However, if it's possible to persuade you into trying something else, i recommend qtox ([https://wiki.tox.chat/clients/qtox](https://wiki.tox.chat/clients/qtox)). It's an upcoming (and very well functioning, if i might say so) cross platform, opensource replacement to Skype (still under construction but very stable and resource efficient) that encrypts all transmissions between users, and features audio+video calls + screenshot sender e.t.c. :D

---

### Post by vanili on 2015-10-18
Hi! Thanks for suggestion, but it has not work. The error is the same.

I will try qtox, but it is interesting how to run pidgin-vv

---

### Post by steeldriver on 2015-10-18
The message 

```

//usr/lib/i386-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line

```

would suggest that it is **-lX11** that is missing from the LDFLAGS, rather than **-lz**

Make sure that the configure output doesn't contain any errors related to missing X11 components

---

### Post by anlag on 2016-02-25
I tried to compile Pidgin 2.10.12 today on Ubuntu 15.10, and ran into the same errors as the OP. 

Installing the following packages allowed *./configure* to run without the *--disable-vv* option:

> libgstreamer-plugins-base0.10-dev
libgstreamer-plugins-base1.0-dev
libgstreamer1.0-dev
libfarstream-0.2-dev

But as for the OP, *make* throws errors:

> /usr/bin/ld: gtkmedia.o: undefined reference to symbol 'XSetErrorHandler'
/usr/lib/x86_64-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
Makefile:829: recipe for target 'pidgin' failed

I tried editing the Makefile, changing the **LDFLAGS** parameter as follows:

> LDFLAGS = -lX11 -lz

I tried also with each of the options separately. Unfortunately it does not change the outcome; *make* still fails.

I also verified that *libX11-dev* is installed.

Running ./configure again with *--disable-vv* removes the error and Pidgin compiles fine, but of course without voice and video support.

---

