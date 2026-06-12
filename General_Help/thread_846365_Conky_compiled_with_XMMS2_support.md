---
title: "Conky compiled with XMMS2 support"
date: 2008-07-01
forum: General Help
---

### Post by Mechaphoenix25 on 2008-07-01
I have a favor to ask of a generous stranger:

I'm trying to compile Conky (great system monitor) with XMMS2 support, because by the package in the repos does not have it built in, and XMMS2 is awesome.  I've done this 6 ways to sunday, and every time it says I'm missing a header file from XMMS2, either the client or the daemon.  It switches depending on the version of XMMS2 and Conky that I try.  You see, when the default -dev packages didn't work, I tried compiling against just about every -dev package XMMS2 has, even trying old and just released (0.5) versions.  I even tried the new beta version of Conky, to no avail.  I finally resorted to trying to compile the old one, 1.4.9, which finally worked, but when I ran it I got nothing but segfaults.  ](*,)

I have since given up, and I'm posting to ask someone (Thank you nice people!) to configure and compile (./config, make, and package as a .deb file or equivalent) conky 1.5.1 with XMMS2 support (preferably version .5, although I think it'd work with the curent one) and a few other things enabled (see below).  If it makes any difference, I have a Dell Inspiron 1501, running Ubuntu 8.04 x86 (32 bit), with a AMD Sempron 3500+ 1.8GHz CPU (again 32 bit), 1GB RAM, and an ATI Xpress Radeon 1150 graphics card with 256MB shared memory.

All I need is the following config/compile flags enabled, the line is:

./config --enable-xmms2 --enable-portmon --enable-wlan --enable-smapi --enable-rss --enable-x11 --enable-double-buffer --enable-xdamage --enable-xft

After that, then just run make, and package the result as a .deb file or some such.

And yes, I will scan/look through whatever I get, I'm not stupid.  XMMS2 just hates me for some reason. 

THANK YOU!!:KS

---

### Post by Mechaphoenix25 on 2008-07-12
*bump*, Conky is still refusing to compile with XMMS2 support, anybody generous enough to help?

---

### Post by puzzles on 2009-02-10
Have you installed libxmmsclient-dev?

---

### Post by Mechaphoenix25 on 2009-02-10
Yes, I installed all the -dev packages.  Thanks for the help, but I've switched off XMMS2 for other reasons, namely "Banshee rocks harder".  Thanks for the reply though, I still use Conky.

---

### Post by gfulton on 2009-02-10
Conky is cool. Why did you decide do give up on the XMMS2 support?

-gf

---

### Post by Mechaphoenix25 on 2009-02-11
I gave up on xmms2 entirely, after I discovered banshee would do all it did and then some, with a better GUI

---

