---
title: "Is gcc-4.0.0 bad?"
date: 2005-05-05
forum: General Help
---

### Post by wwwolf on 2005-05-05
I was compiling the MPlayer source and passed the cc flag of gcc-4.0:

CC=gcc-4.0 DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary

and I noticed it was using 3.3 instead. So, I looked more closely and found the following:

Detected operating system: Linux
Detected host architecture: i386
Checking for gcc-4.0. version ... not found
Checking for gcc version ... 4.0.0, bad
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... 3.3.5, ok
Checking for host cc ... gcc-3.3

Does this mean my gcc 4.0.0 is bad or that the mplayer make file just doesn't like it. Is there a way I can test my gcc version now that it is already installed?

Thanx,

wwwolf

---

### Post by XDevHald on 2005-05-05
[QUOTE=wwwolf]I was compiling the MPlayer source and passed the cc flag of gcc-4.0:

CC=gcc-4.0 DEB_BUILD_OPTIONS="--enable-gui" fakeroot debian/rules binary

and I noticed it was using 3.3 instead. So, I looked more closely and found the following:

Detected operating system: Linux
Detected host architecture: i386
Checking for gcc-4.0. version ... not found
Checking for gcc version ... 4.0.0, bad
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... 3.3.5, ok
Checking for host cc ... gcc-3.3

Does this mean my gcc 4.0.0 is bad or that the mplayer make file just doesn't like it. Is there a way I can test my gcc version now that it is already installed?

Thanx,

wwwolf[/QUOTE]
 I am not a huge GCC codeman, but this link might help you out with the compiling of C++

[http://developer.apple.com/releasenotes/DeveloperTools/GCC4.html](http://developer.apple.com/releasenotes/DeveloperTools/GCC4.html)

And to test it with on a simulator, check out

[http://www.mirror5.com/software/gcc/simtest-howto.html](http://www.mirror5.com/software/gcc/simtest-howto.html)

---

### Post by wwwolf on 2005-05-05
OK, thanx, I'll get right on it.  :)

---

