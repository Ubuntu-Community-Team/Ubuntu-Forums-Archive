---
title: "ConsoleOne 1.3.6 on Ubuntu"
date: 2006-10-30
forum: General Help
---

### Post by sonician on 2006-10-30
I am working on a project to see if this is a feasible option.
I am building a Groupwise server (version 7), and it requires ConsoleOne.

I downloaded c1_136e-linux.tar.gz from here: [http://download.novell.com/Download?buildid=CVTLiFIagE4~]("http://download.novell.com/Download?buildid=CVTLiFIagE4~")

and ran 
```
tar xf c1_136e-linux.tar.gz
```
I went into the directory and tried running 
```
sudo ./c1-install
```

It starts, and first asks what language. I select English.
It then asks about what snapins to install, I select none.

and it then returns the following errors: 

```
%% NOTE: ConsoleOne will be installed without the provided Java Runtime
%% Environment. Please define the environment variables C1_JRE_HOME or
%% JRE_HOME before running ConsoleOne.
%% Example: C1_JRE_HOME=/path/to/your/JRE

%% Adding package nici ...
error: Failed dependencies:
        /bin/sh is needed by nici-2.6.4-0.05.i386
        ld-linux.so.2 is needed by nici-2.6.4-0.05.i386
        libc.so.6 is needed by nici-2.6.4-0.05.i386
        libpthread.so.0 is needed by nici-2.6.4-0.05.i386
        libc.so.6(GLIBC_2.0) is needed by nici-2.6.4-0.05.i386
        libc.so.6(GLIBC_2.1) is needed by nici-2.6.4-0.05.i386
        libc.so.6(GLIBC_2.1.3) is needed by nici-2.6.4-0.05.i386
        libpthread.so.0(GLIBC_2.0) is needed by nici-2.6.4-0.05.i386
        libpthread.so.0(GLIBC_2.1) is needed by nici-2.6.4-0.05.i386
%% ERROR: Failed to add nici (NICI) package.
%% Installation of packages failed, not all packages were installed.
```

Any help would be appreciated.

Thanks

---

### Post by sonician on 2006-10-31
I should mention that I'm doing this on 6.06 LTS.

Thanks

---

### Post by HighKing on 2006-11-08
Tried this?
[http://www.novell.com/coolsolutions/tip/16609.html](http://www.novell.com/coolsolutions/tip/16609.html)

---

### Post by John Clayton on 2007-08-08
Tried that one, and this as well:
[http://shadowphax.blogspot.com/](http://shadowphax.blogspot.com/)
(Look for Thursday July 5th, Ubuntu 7.0.4)

Your jre/jre error is similar to one I had initially - move the files from the last jre directory into the one above it and ConsoleOne should load.  Mine gets as far as displaying the splash screen and then core dumps.  I'd attach it, but I don't know how to find the contents of the core dump.

Good luck!

---

