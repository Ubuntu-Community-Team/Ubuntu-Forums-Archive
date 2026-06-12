---
title: "Xscreensaver install problem"
date: 2007-07-22
forum: General Help
---

### Post by Astral Abraxas on 2007-07-22
I get the following errors when doing ./configure

checking for X... no
configure: error: Couldn't find X11 headers/libs.  Try `./configure --help'.

I seen on a website that someone was missing "libxml*-devel-*.rpm" when installing and noticed that I was missing quite a few libxml-dev files. I installed libxml-dev but that didn't do too much >.>;

Anyways, any help would be great.

---

### Post by Astral Abraxas on 2007-07-22
I found this in my config.log:

```

configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #ifndef __cplusplus
| #define inline __inline__
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_UNISTD_H 1
| #define RETSIGTYPE void
| #define TIME_WITH_SYS_TIME 1
| #define HAVE_SYS_WAIT_H 1
| #define HAVE_DIRENT_H 1
| #define HAVE_GETTIMEOFDAY 1
| #define GETTIMEOFDAY_TWO_ARGS 1
| #define HAVE_SELECT 1
| #define HAVE_FCNTL 1
| #define HAVE_UNAME 1
| #define HAVE_NICE 1
| #define HAVE_SETPRIORITY 1
| #define HAVE_GETCWD 1
| #define HAVE_GETWD 1
| #define HAVE_PUTENV 1
| #define HAVE_SBRK 1
| #define HAVE_SIGACTION 1
| #define HAVE_SYSLOG 1
| #define HAVE_REALPATH 1
| #define HAVE_SETRLIMIT 1
| #define HAVE_SETLOCALE 1
| #define HAVE_ICMP 1
| #define HAVE_ICMPHDR 1
| #define HAVE_CRYPT_H 1
| #define HAVE_SYS_SELECT_H 1
| /* end confdefs.h.  */
| #include <X11/Xlib.h>
| int
| main ()
| {
| XrmInitialize ()
|   ;
|   return 0;
| }
configure:6766: result: no
configure:8108: error: Couldn't find X11 headers/libs.  Try `./configure --help'.

```

---

### Post by smirko on 2007-08-27
Hi,

I'm pretty sure you worked it out yourself by now, but it may be a useful hint for others.

Seems that for some reason the x11 libraries' location is not detected correctly by configure. Setting --x-includes and --x-libraries (e.g. --x-includes=/usr/include --x-libraries=/usr/lib) options for configure script to point the location of x header and lib files resolved the issue in my case.
There were still some unresolved dependencies, but that was nothing a simple installation of another required package couldn't handle ;-)

Oh, one more thing. I use FC6, but the behaviour was exactly the same.

Best regards,
Smirk

---

