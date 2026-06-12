---
title: "IBM Tivoli TSM Client install in Ubuntu Gusty"
date: 2007-11-05
forum: General Help
---

### Post by peedeeramone on 2007-11-05
I was wondering if anyone out there had any experience installing TSM on Gusty?

I've gotten part of it installed but I think it may be missing some libraries and a few other files.

Not a really big deal since its mostly just for testing purposes, but just wanted to see if I could figure it out.


Thanks

---

### Post by Koning Puber on 2007-11-06
What I have done is cheating, but it seems to work :)
I downloaded a debian package that was created by someone else (Harry Redl) from the website: [http://adsm.org/files/TSM/Clients/Linux/Debian/](http://adsm.org/files/TSM/Clients/Linux/Debian/) (in my case the AMD64 package). It is not supported by IBM, but if you do not need their support, why bother.
Installation went smooth.
I configured dsm.sys and dsm.opt and now my backup it running. I'm happy, hope you're happy too.

---

### Post by peedeeramone on 2007-11-12
thanks for the reply, but I got it working a few days back.  I used a few .deb package that were converted with alien from the  .rpm packages.   the problem was that a few of the libraries were copied to a folder where Ubuntu didn't know they were there.  So basically I just copied them to /usr/lib I believe.  After that I only had to create a startup script for it.

thats basically it aside from a few steps I might have forgotten...

---

