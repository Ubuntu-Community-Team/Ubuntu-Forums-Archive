---
title: "wubi 8.04 md5sum failure"
date: 2008-06-01
forum: General Help
---

### Post by Itasca82 on 2008-06-01
Consistent failure of MD5SUM on downloads of "Wubi-8.04.exe" desktop-i386:
(Running MD5SUM in terminal)
d77b62f8e95f5e1e0e6e18e6993ab1d2 (From Ubuntu)
d77b62f8e95f5e1e0e6e18e6993ab1d2 (From SourceForge)
d77b62f8e95f5e1e0e6e18e6993ab1d2 (Repeat from SourceForge)

This is the one I expected:
a96aa69961f3ed80dd7a88fae1e28196 *wubi.ex

Which was obtained From:
[http://whyamistilltyping.wordpress.com/2008/04/24/ubuntu-804-md5-checksums/](http://whyamistilltyping.wordpress.com/2008/04/24/ubuntu-804-md5-checksums/)
Ubuntu 8.04 MD5 Checksums

And excerpted from the following post:
Posted by whyamistilltyping on April 24, 2008
To save you looking, here are the MD5 sums of the Hardy Heron Ubuntu images:

For Ubuntu:

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
---cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe---(crossed out)
a96aa69961f3ed80dd7a88fae1e28196 *wubi.exe

I also had same situation (twice) with downloads of U-8.04 iso

What am I doing wrong?  These are certainly not random errors?
Thanks.

---

### Post by ago on 2008-06-01
a96aa69961f3ed80dd7a88fae1e28196 is the correct one for [http://releases.ubuntu.com/8.04/wubi.exe](http://releases.ubuntu.com/8.04/wubi.exe)

---

### Post by Itasca82 on 2008-06-02
Thanks for the reply ago,

Several sites have mentioned incorrect published sums. 

I just don't understand why all the "wrong" sums would be identical, when downloaded from two different sites and several days apart, unless they are mirroring the same source file that has a built-in error.

One would think that random download errors would end up with different sums???

I'll keep on keepin' on.

---

### Post by ago on 2008-06-02
The one on [http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS) is correct

The build on wubi-installer.org comes from a different machine and might be slightly different

---

