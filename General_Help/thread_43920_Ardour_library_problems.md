---
title: "Ardour library problems"
date: 2005-06-23
forum: General Help
---

### Post by robojamie on 2005-06-23
I installed Ardour-gtk and it's dependencies from the Ubuntu Professional Audio repository which can be found at [https://wiki.ubuntu.com//MOTUAudio](https://wiki.ubuntu.com//MOTUAudio) . The package installed without problems, but when the program runs I get the following error: 

/usr/bin/ardour: error while loading shared libraries: libSoundTouch.so.1: cannot open shared object file: No such file or directory

I have libSoundTouch installed.. Perhaps Ardour is looking in the wrong place

I tried the Ardour package from the universe repositories and the same error occurs

---

### Post by theToolman on 2005-07-14
worked fine for me with the listed repository; i did have problems with the version that is in the ubuntu universe (i think) repository, one of the files failed MD5 for me repeatedly so no install.  added link to /etc/apt/sources.list and updated fine.

I do have kubuntu installed but not used, otherwise standard hoary box here.

---

### Post by Karlos on 2005-07-14
I have been getting the same thing/error when running rezound AND ardour

I think maybe its something to do with libsoundtouch.so

but i dunno

someone will tho

sooner or later

---

