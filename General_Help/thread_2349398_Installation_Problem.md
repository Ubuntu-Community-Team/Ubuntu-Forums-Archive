---
title: "Installation Problem"
date: 2017-01-14
forum: General Help
---

### Post by na2 on 2017-01-14
Hi,
When i'm trying to install the HTK toolkit on my ubuntu 16.04 LTS 32 bits system, it show me the following problem

```
 ./configure
checking whether make sets $(MAKE)... yes
checking for gawk... gawk
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for main in -lX11... yes
checking for main in -lm... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking float.h usability... yes
checking float.h presence... yes
checking for float.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working strtod... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for floor... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for modf... yes
checking for pow... yes
checking for socket... yes
checking for sqrt... yes
checking for strchr... yes
checking for strcspn... yes
checking for strrchr... yes
checking for strspn... yes
checking for strstr... yes
checking for strtol... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating HTKLib/Makefile
config.status: WARNING:  HTKLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKTools/Makefile
config.status: WARNING:  HTKTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMLib/Makefile
config.status: WARNING:  HLMLib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HLMTools/Makefile
config.status: WARNING:  HLMTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating HTKLVRec/Makefile
config.status: WARNING:  HTKLVRec/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting

```
could any one help me solve it please. i was trying everything but i  couldn't find what cause this problem. Thank you in advance.

---

### Post by dragonfly41 on 2017-01-14
I do wish that simple google searches were done first ...

[http://hts.sp.nitech.ac.jp/hts-users/spool/2015/msg00036.html](http://hts.sp.nitech.ac.jp/hts-users/spool/2015/msg00036.html)

and next in thread ..

[http://hts.sp.nitech.ac.jp/hts-users/spool/2015/msg00037.html](http://hts.sp.nitech.ac.jp/hts-users/spool/2015/msg00037.html)

Do you have Fortran 32bits installed?  It seems to be a prerequisite.

---

### Post by na2 on 2017-01-14
Actually, i see this mailing list before [http://hts.sp.nitech.ac.jp/hts-users.../msg00036.html]("http://hts.sp.nitech.ac.jp/hts-users/spool/2015/msg00036.html"), but it didn't help me solve my problem and fortran is installed on my system.

---

### Post by dragonfly41 on 2017-01-14
O.K. my error .. then this thread (another google search on your error pattern)

[http://www.voxforge.org/home/dev/acousticmodels/linux/create/htkjulius/tutorial/download/comments/htk-install](http://www.voxforge.org/home/dev/acousticmodels/linux/create/htkjulius/tutorial/download/comments/htk-install)..

suggests running ...

```
sudo apt-get install g++-multilib
```

Make sure that you are using 32bit libraries.

[P.S.]

Another troubleshooting thread found here ... [http://stackoverflow.com/questions/34465295/htk-3-4-1-installation-error-on-ubuntu-14-04](http://stackoverflow.com/questions/34465295/htk-3-4-1-installation-error-on-ubuntu-14-04)

---

### Post by na2 on 2017-01-15
Thank you for your help, i have installed all the necessary libraries  and tried all the existing solution but my problem still exist.

---

### Post by dragonfly41 on 2017-01-15
In that last thread the user (seeking help) installed these ...

```

[COLOR=#242729][FONT=Arial]sudo apt-get install libx11-dev
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]sudo apt-get install g++-multilib
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]./configure --disable-hslab --disable-hlmtools
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]sudo apt-get install libc6-dev-i386
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]sudo gedit configure.ac then remove "-m32" in the file[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

[/FONT][/COLOR]If you search "HTK ubuntu dependencies" you might find more threads.
Here is one ... [http://htk.eng.cam.ac.uk/docs/inst-nix.shtml](http://htk.eng.cam.ac.uk/docs/inst-nix.shtml)

And in this old thread ... 
[https://lists.ubuntu.com/archives/ubuntu-users/2010-September/228202.html](https://lists.ubuntu.com/archives/ubuntu-users/2010-September/228202.html)
a suggestion is to install HTK using Ubuntu checkinstall package.

But this is all guess work and you will probably get more informed replies from htk mailing list ...
 [http://htk.eng.cam.ac.uk/cgi-bin/search.cgi?q=installation&ps=20&o=0&m=all&ul=%2Fpipermail%2Fhtk-users](http://htk.eng.cam.ac.uk/cgi-bin/search.cgi?q=installation&ps=20&o=0&m=all&ul=%2Fpipermail%2Fhtk-users)

[Later edit]

Look at this thread which seems relevant (32bit installation) ...
[http://askubuntu.com/questions/452208/htk-installation-problem-on-ubuntu-14-04](http://askubuntu.com/questions/452208/htk-installation-problem-on-ubuntu-14-04)

I've searched in Synaptic Package Manager and these are installed .. although I don't use HTK.
libx11-xcb-dev
libx11-dev
x11-utils

You might check these are installed.

---

