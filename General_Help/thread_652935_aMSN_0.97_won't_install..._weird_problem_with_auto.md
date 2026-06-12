---
title: "aMSN 0.97 won't install... weird problem with autopackage"
date: 2007-12-29
forum: General Help
---

### Post by Starlight on 2007-12-29
Hi!

I wanted to try out the new aMSN 0.97 which was released recently, but it's not available in the repositories yet, so I had to use the autopackage installer downloaded from the aMSN website. But it doesn't work... here's the error I get:

> 
# Preparing package: AMSN MSN client
# Checking for required C library versions ... failed
# FAIL:
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
#
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
#
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package AMSN MSN client.


I remember when I tried installing something with autopackage some time ago, I got the same error. The "libc" which I have installed on the computer is the newest version, so I can't upgrade it. Is it possible to force autopackage to install stuff without checking the glibc version? And if not, when will aMSN 0.97 be available in the Ubuntu repositories? The current version is 0.97RC1 which is already quite old, and it's very buggy.... I was hoping to finally use a more stable and working version of aMSN...

---

### Post by patrickfromspain on 2007-12-29
If you want, you could try my packages:

[http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn](http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn)

Hope they help!

---

### Post by Starlight on 2007-12-29
Thank you, I'm downloading them now :)

---

