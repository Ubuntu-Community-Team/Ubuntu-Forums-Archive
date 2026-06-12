---
title: "libsoundtouch problem with rezound"
date: 2005-07-13
forum: General Help
---

### Post by Karlos on 2005-07-13
I cant seem to get rezound to run

take a look at this

```
karlos@blulamp:~$ rezound
rezound: error while loading shared libraries: libSoundTouch.so.1: cannot open shared object file: No such file or directory
karlos@blulamp:~$ sudo apt-cache search libsoundtouch
libsoundtouch1 - sound stretching library
libsoundtouch1-dev - development files for sound stretching library
karlos@blulamp:~$ sudo apt-get install libsoundtouch1 libsoundtouch1-dev
Reading package lists... Done
Building dependency tree... Done
libsoundtouch1 is already the newest version.
The following NEW packages will be installed:
  libsoundtouch1-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 44.5kB of archives.
After unpacking 188kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libsoundtouch1-dev
Install these packages without verification [y/N]? y
Get:1 http://easynews.dl.sourceforge.net ./ libsoundtouch1-dev 1.3.0-0 [44.5kB]
Fetched 44.5kB in 1s (36.3kB/s)

Preconfiguring packages ...
Selecting previously deselected package libsoundtouch1-dev.
(Reading database ... 155057 files and directories currently installed.)
Unpacking libsoundtouch1-dev (from .../libsoundtouch1-dev_1.3.0-0_i386.deb) ...
Setting up libsoundtouch1-dev (1.3.0-0) ...
Running prelink, please wait...
karlos@blulamp:~$ rezound
rezound: error while loading shared libraries: libSoundTouch.so.1: cannot open shared object file: No such file or directory
karlos@blulamp:~$

```

Any thoughts/ideas would be much appreciated

thanks 

karlos

---

