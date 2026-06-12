---
title: "Doom3 Sound missing on AMD64"
date: 2014-04-24
forum: General Help
---

### Post by m-dw on 2014-04-24
Previously (to 13.10) had Doom3 working well on 64bit architecture by installing libXext6:i386 for video and ia32-libs to provide an audio compatibility layer (OSS)

I have the video sorted out, but there is no sound because I can't find the 32bit compatibility layer. 

```
david@deskbuntu:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0


E: Package 'ia32-libs' has no installation candidate

```

The three suggested alternatives have nothing to do with sound/audio.  Anyone know what I need to install?

---

### Post by m-dw on 2014-04-24
Solved it with help from here:
[http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760)

---

