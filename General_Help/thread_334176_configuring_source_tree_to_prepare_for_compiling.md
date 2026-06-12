---
title: "configuring source tree to prepare for compiling"
date: 2007-01-08
forum: General Help
---

### Post by Ampsonic on 2007-01-08
I am following this guide to compile and install IVTV drivers. :[http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html](http://s91928265.onlinehome.us/hfamily/mythtv/myth_ubuntu.html)

In step 5,  when I execute 'make oldconfig'
this happens:

```
$ sudo make oldconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:105:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:106:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:107:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:108:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:109:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:111:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:112:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:113:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:115:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:129: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:129: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:129: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:129: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:129: error: for each function it appears in.)
scripts/basic/fixdep.c:130: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:130: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:138: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:138: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:141: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:154: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:154: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:156: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:172: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:185: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:185: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:204: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:212: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:218: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:220: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:204: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:223: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:225: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:231: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:242: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:255: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:255: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:266: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:270: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:270: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:272: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:272: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:274: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:278: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:281: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:281: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:281: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:288: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:290: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:266: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:295: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:298: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:300: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:302: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:302: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:304: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:304: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:305: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:307: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:300: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:337: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:341: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:343: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:343: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:345: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:353: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:353: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:360: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:337: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:372: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:372: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:374: warning: incompatible implicit declaration of built-in function ‘exit’
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

```

Not sure what to do now, How do I fix this?

Thanks in advance,
Nick

---

### Post by po0f on 2007-01-08
Ampsonic,

You're missing libc6 headers, install [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) if you haven't already.  This will install libc6-dev (the headers) as well as a compiler if you haven't got one yet.

---

### Post by Ampsonic on 2007-01-09
Thanks! That worked pefectly. Stuck on a new problem though...

At this step:

```
cd utils
wget ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip
wget ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init.mpg /usr/lib/hotplug/firmware
ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw 
```

here is what happens at one of the middle steps:

```
$ sudo cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp: cannot stat `HcwMakoA.ROM': No such file or directory
$ 

```

i looked into it, it seems that there is no hotplug directory in /usr/lib   is this located somewhere else in the current version of ubuntu? or should i simply create these directories?

Thanks,
Nick

---

### Post by po0f on 2007-01-09
Ampsonic,

Actually, the error indicates that the file 'HcwMakoA.ROM' couldn't be found.  Can you confirm that the file is extracted from one of the archives downloaded?

---

### Post by Ampsonic on 2007-01-09
Sorry, what I copied from was after I had been trying a few different things. Here is the actual error, complete with a directory listing.

```
$ ls
ivtv-0.7.3         linux-headers-2.6.17-10          linux-source-2.6.17.tar.bz2
ivtv-0.7.3.tar.gz  linux-headers-2.6.17-10-generic
linux              linux-source-2.6.17
$ cd ivtv-0.7.3
$ cd utils
$ ls
cx25840ctl    HcwMakoA.ROM     ivtv-encoder      ivtv-tune
enc_chann.c   HCWPP2.inf       ivtvfbctl         Makefile
enc_chann.o   hcwPP2.sys       ivtvfbctl.c       mpeg2structs.h
enc_mindex.c  hcwPrxA2.ax      ivtv-functions.h  perl
enc_mindex.o  hcwutl32.dll     ivtvfwextract.pl  pvr_1.18.21.22254_inf.zip
encoder.c     hcwxds.dll       ivtv-mpegindex    pvr_2.0.24.23035.zip
encoder.h     ivtvctl          ivtv-mpegindex.c  README.X11
encoder.o     ivtvctl.c        ivtvplay          ReleaseNotes.txt
hcwCCnv2.ax   ivtvctl.o        ivtvplay.cc       videodev2.h
hcwECP.ax     ivtv-detect      ivtv-radio
HcwFalcn.rom  ivtv-detect.cpp  ivtv-radio.c
$ sudo cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
Password:
cp: cannot create regular file `/usr/lib/hotplug/firmware/v4l-cx25840.fw': No such file or directory
$ 

```


Thanks,
Nick

---

### Post by superm1 on 2007-01-09
> **Ampsonic said:**
> Sorry, what I copied from was after I had been trying a few different things. Here is the actual error, complete with a directory listing.

```
$ ls
ivtv-0.7.3         linux-headers-2.6.17-10          linux-source-2.6.17.tar.bz2
ivtv-0.7.3.tar.gz  linux-headers-2.6.17-10-generic
linux              linux-source-2.6.17
$ cd ivtv-0.7.3
$ cd utils
$ ls
cx25840ctl    HcwMakoA.ROM     ivtv-encoder      ivtv-tune
enc_chann.c   HCWPP2.inf       ivtvfbctl         Makefile
enc_chann.o   hcwPP2.sys       ivtvfbctl.c       mpeg2structs.h
enc_mindex.c  hcwPrxA2.ax      ivtv-functions.h  perl
enc_mindex.o  hcwutl32.dll     ivtvfwextract.pl  pvr_1.18.21.22254_inf.zip
encoder.c     hcwxds.dll       ivtv-mpegindex    pvr_2.0.24.23035.zip
encoder.h     ivtvctl          ivtv-mpegindex.c  README.X11
encoder.o     ivtvctl.c        ivtvplay          ReleaseNotes.txt
hcwCCnv2.ax   ivtvctl.o        ivtvplay.cc       videodev2.h
hcwECP.ax     ivtv-detect      ivtv-radio
HcwFalcn.rom  ivtv-detect.cpp  ivtv-radio.c
$ sudo cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
Password:
cp: cannot create regular file `/usr/lib/hotplug/firmware/v4l-cx25840.fw': No such file or directory
$ 

```
Thanks,
Nick

Hi, if your really working in breezy continue to follow these directions.

From what I see though with 2.6.17 sources sitting in your directory, your more likely on an edgy machine.  You really should follow the guide that keeps the compiling to a minimum (and has updated information for edgy):
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

