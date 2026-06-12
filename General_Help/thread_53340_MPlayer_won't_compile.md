---
title: "MPlayer won't compile"
date: 2005-07-31
forum: General Help
---

### Post by blueturtl on 2005-07-31
I am trying to compile MPlayer according to the instructions in the following link:
[http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt](http://www.oldskoolphreak.com/tfiles/hack/ubuntu.txt)

The only difference is that at the time the version of MPlayer available has changed to 1.0pre7.

I installed the necessary packages through Synaptic and then went on wth the compilation instructions in my /home dir.

make gives me something like this (after a whole few screenfulls of output):

: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1

When issuing sudo make install the same error is outputted.

Along the way there were also a lot of "incompatible pointer errors".

I am trying to compile MPlayer as I cannot find it precompiled in any of the listed repositories because I want to watch movie trailers in my web browser and be able to view Windows Media and Quicktime content locally.

---

### Post by Xian on 2005-07-31
Do you have the libxxf86vm-dev package installed?

---

### Post by blueturtl on 2005-07-31
No infact I don't. It's not mentioned in the howto.
I will install it and retry.

---

### Post by blueturtl on 2005-08-01
It worked! Right after installing the package. Thanks! :)

---

