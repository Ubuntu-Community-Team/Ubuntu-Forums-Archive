---
title: "google earth"
date: 2014-10-18
forum: General Help
---

### Post by samnang on 2014-10-18
Where and how can I install google-earth?
Thanks.

---

### Post by BlinkinCat on 2014-10-18
> **samnang said:**
> Where and how can I install google-earth?
Thanks.

I believe that google-earth at present has some unfortunate issues. If that is not the case I would be happy to be corrected.

---

### Post by O9aIevckc0 on 2014-10-18
Google Earth is available for Linux from their web site it appears

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

(if this solves your problem please mark this thread as solved)

---

### Post by samnang on 2014-10-18
There is a problem : Dependency is not satisfiable : ia32-libs.

---

### Post by The Cog on 2014-10-18
They can't make a package that even installs on a 64-bit system. It's been broken like that for years. 
Last time I installed it on 32-bit it worked OK though. From the link abpabp gave.

---

### Post by samnang on 2014-10-18
There is a problem : Dependency is not satisfiable : ia32-libs

---

### Post by Impavidus on 2014-10-18
Indeed, that package has been replaced by a different mechanism. That dependency can be removed. See [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304), post #5. On my system that still didn't work, but I managed to install the 32 bit version on my 64 bit system: [http://ubuntuforums.org/showthread.php?t=2183733](http://ubuntuforums.org/showthread.php?t=2183733), post #10. That still leaves the issue of pictures not loading. Even that is supposed to be fixable, but I never bothered. It all comes down to bad packaging.

---

### Post by scouser73 on 2014-10-19
Follow the instructions on Web Upd8

[http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html](http://www.webupd8.org/2014/04/install-google-earth-in-ubuntu-1404.html)

To properly install Google Earth (along with the required 32bit dependencies) in Ubuntu 14.04 (or 13.10) 64bit, use the following commands:

> sudo apt-get install libfontconfig1:i386 libx11-6:i386 libxrender1:i386 libxext6:i386 libgl1-mesa-glx:i386 libglu1-mesa:i386 libglib2.0-0:i386 libsm6:i386

> cd /tmp && wget [http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb](http://dl.google.com/dl/earth/client/current/google-earth-stable_current_i386.deb)

> sudo dpkg -i google-earth-stable_current_i386.deb

> sudo apt-get install -f

Panoramio doesn't work in Google Earth using those instructions, everything else seems fine.  I have installed G.E. using these instructions and can verify they're good.

---

### Post by BlinkinCat on 2014-10-19
Thanks for that scouser73!

I installed and apart from a couple of minor glitches it is looking good.

For example I can't figure out if there is a full screen mode.

Cheers - :p

Edit : Ooops, I found full screen - silly me !

Further Edit : After initially thinking local shots appear to be only a few months old I now see that they are several years old !

---

### Post by vasa1 on 2014-10-19
Bookmarking this thread even though I don't use google earth because the solution seems to apply to installing 32-bit software on a 64-bit system when the particular 32-bit program doesn't support mutli-arch. At least that's what I gather from:> The problem with Google Earth is that the 32bit package doesn't support multiarch so it doesn't install all the 32bit dependencies it needs to run on Ubuntu 64bit.

---

