---
title: "3rd party package install problem"
date: 2007-12-27
forum: General Help
---

### Post by CactusWren on 2007-12-27
Hello,
I am trying to install a package called ttsynth (a text-to-speech synthesizer) onto gutsy gibbon.

The package comes as an rpm package, so I started by going to a terminal window.
then sudo su
then rpm -Uvh ttsynthcore-1.0.-0.i386.rpm

When I do this, I get the following output:
error: Failed dependencies:
	/bin/bash is needed by ttsynthcore-1.0-0.i386
	/bin/sh is needed by ttsynthcore-1.0-0.i386
	/lib/ld-linux.so.2 is needed by ttsynthcore-1.0-0.i386
	/lib/libasound.so.2 is needed by ttsynthcore-1.0-0.i386
	/lib/libc.so.6 is needed by ttsynthcore-1.0-0.i386
	/lib/libdl.so.2 is needed by ttsynthcore-1.0-0.i386
	/lib/libgcc_s.so.1 is needed by ttsynthcore-1.0-0.i386
	/lib/libm.so.6 is needed by ttsynthcore-1.0-0.i386
	/lib/libpthread.so.0 is needed by ttsynthcore-1.0-0.i386
	/usr/lib/libstdc++-libc6.2-2.so.3 is needed by ttsynthcore-1.0-0.i386
	libc.so.6 is needed by ttsynthcore-1.0-0.i386
	libc.so.6(GLIBC_2.0) is needed by ttsynthcore-1.0-0.i386
	libc.so.6(GLIBC_2.1) is needed by ttsynthcore-1.0-0.i386
	libc.so.6(GLIBC_2.1.3) is needed by ttsynthcore-1.0-0.i386
	libc.so.6(GLIBC_2.2) is needed by ttsynthcore-1.0-0.i386
	libdl.so.2 is needed by ttsynthcore-1.0-0.i386
	libdl.so.2(GLIBC_2.0) is needed by ttsynthcore-1.0-0.i386
	libdl.so.2(GLIBC_2.1) is needed by ttsynthcore-1.0-0.i386
	libm.so.6 is needed by ttsynthcore-1.0-0.i386
	libm.so.6(GLIBC_2.0) is needed by ttsynthcore-1.0-0.i386
	libpthread.so.0 is needed by ttsynthcore-1.0-0.i386
	libpthread.so.0(GLIBC_2.0) is needed by ttsynthcore-1.0-0.i386
	libstdc++-libc6.2-2.so.3 is needed by ttsynthcore-1.0-0.i386

I checked and /lib/libc.so.6 exists.

How can I get a clean environment to install this package and/or fix these problems?

---

### Post by jken146 on 2007-12-27
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

