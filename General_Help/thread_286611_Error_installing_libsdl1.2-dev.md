---
title: "Error installing libsdl1.2-dev"
date: 2006-10-28
forum: General Help
---

### Post by IYY on 2006-10-28
I am trying to install the SDL libraries for compiling some programs (on Edgy). However,


```

ilya@muddy:~$ sudo apt-get install **libsdl-dev**

Reading package lists... Done
Building dependency tree       
Reading state information... Done

Note, selecting libsdl1.2-dev instead of libsdl-dev

The following NEW packages will be installed:
  libsdl1.2-dev
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/726kB of archives.

After unpacking, 2822kB of additional disk space will be used.
(Reading database ... 142948 files and directories currently installed.)
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.10-3ubuntu2_i386.deb) 

...

dpkg: error processing /var/cache/apt/archives/libsdl1.2-dev_1.2.10-3ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/sdl.m4', which is also in package sdl-devel

dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:

 /var/cache/apt/archives/libsdl1.2-dev_1.2.10-3ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

ilya@muddy:~$ 


```

More specifically, the error is:

```
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.10-3ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsdl1.2-dev_1.2.10-3ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/aclocal/sdl.m4', which is also in package sdl-devel
```

What's happening here?

---

