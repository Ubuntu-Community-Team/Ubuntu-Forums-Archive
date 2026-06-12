---
title: "Can never get ./configure to work... this time with airsnort"
date: 2005-10-11
forum: General Help
---

### Post by otakuj462 on 2005-10-11
Hi all, I've been using Ubuntu Linux for the last six months and absolutely love it. One of the major problems I have, though, is building applications from source. At the moment, I'm trying to build AirSnort from source, and I can't get past running ./configure. The output is as follows:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Failed to open '/usr/lib/pkgconfig/gtk+-2.0.pc': Too many open files
Package 'gtk+-2.0', required by 'libgtk 2.0', not found

configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

This is the output after a few attempts to fix it. At first, it couldn't find gtk+-2.0.pc. Then I added it to /usr/lib/pkgconfig and tried to write the file myself. Then it started returning this error message.
Does it make sense to write the metadata file myself? Or is there a tool to take care of it automatically? Or am I totally off-base? 
If anyone has any insight into this, please let me know. Thanks.

-Jake

---

### Post by Pablo_Escobar on 2005-10-11
Do you install the dev packages of the libraries ./configure requests ?

If not then, you need them for compilation process. Just type in synaptic "gtk dev" and install these libraries.

---

### Post by otakuj462 on 2005-10-12
Are dev libraries different than normal libraries? I have libgtk on there, as well as all of its associated packages, and I reinstalled them just to be sure.
I searched for gtk dev and came up with nothing different than the libgtk stuff. Could this be because I haven't done apt-get update? I haven't done that because I haven't had internet access...
Let me know what you think. Thanks.

-Jake

---

### Post by mlomker on 2005-10-12
It is looking for **libgtk2.0-dev**.  I'm not sure what the error about 'too many open files' is...that's new.

---

### Post by otakuj462 on 2005-10-17
I'm still having trouble. When I try to apt-get install libgtk2.0-dev, I get the following output:
```

Reading package lists...
Building dependency tree...
Package libgtk2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgtk2.0-bin
E: Package libgtk2.0-dev has no installation candidate

```

When I then try to apt-get install libgtk2.0-bin, it tells me I have the most recent version. 
What should I do? Maybe try and build libgtk2.0-dev from source?
If anyone has any recommendations, I'd really appreciate hearing them. Thanks.

---

