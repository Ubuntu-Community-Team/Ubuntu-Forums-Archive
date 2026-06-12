---
title: "Fresh install, C compiler won't work"
date: 2008-04-15
forum: General Help
---

### Post by Furbs on 2008-04-15
Or maybe I don't know how to use it? I just converted from WinXP to Xubuntu 7.10 (single boot). My knowledge of Linux is still pretty minimal, barring a bad experience with Redhat back in '00. I'm running a Dell Dimension 2400, 2.4Ghz celeron, ~630mb RAM, and Xubuntu seems to run fine but doesn't have much functionality. First off, I can't figure out how to connect it via ethernet to my gf's computer which is connected to the internet. So, no internet & no update. I'm going to buy a wireless card in a day or two but have been trying to get emulators (zsnes & fceu), mp3s, mplayer, my soundcard (Chaintech AV-710), and networking to work for the past few days by downloading packages & source code on my gf's windows computer and transferring them to mine. One of the .deb packages i installed worked (the one to install mp3 support, even tho I STILL can't play mp3s), but nothing else has worked so far.

When I try to install new software, I often get an error telling me that gcc cannot make an executable file. For instance, this is what I got when I tried to install zsnes (following the instructions in its documentation, of course):

> checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

and here's the config.log that it's referring to:

>    $ ./configure --enable-release

## --------- ##
## Platform. ##
## --------- ##

hostname = mothership
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Sun Oct 14 23:05:12 GMT 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1806: checking build system type
configure:1824: result: i686-pc-linux-gnulibc1
configure:1846: checking host system type
configure:1861: result: i686-pc-linux-gnulibc1
configure:1883: checking target system type
configure:1898: result: i686-pc-linux-gnulibc1
configure:1939: checking for a BSD-compatible install
configure:1995: result: /usr/bin/install -c
configure:2054: checking for gcc
configure:2070: found /usr/bin/gcc
configure:2081: result: gcc
configure:2319: checking for C compiler version
configure:2326: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2329: $? = 0
configure:2336: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2339: $? = 0
configure:2346: gcc -V >&5
gcc: '-V' option must have argument
configure:2349: $? = 1
configure:2372: checking for C compiler default output file name
configure:2399: gcc  -pipe -I. -I/usr/local/include -I/usr/include   -L/usr/local/lib -L/usr/lib conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directorycollect2: ld returned 1 exit status
configure:2402: $? = 1
configure:2440: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2447: error: C compiler cannot create executables
See `config.log' for more details.
## ---------------- ##
## Cache variables. ##
## ---------------- ##
ac_cv_build=i686-pc-linux-gnulibc1
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_XMKMF_set=
ac_cv_env_XMKMF_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_force_arch_set=
ac_cv_env_force_arch_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_target=i686-pc-linux-gnulibc1

I get this error whether I've done sudo to get root powers (something that's still new to me and not 100% clear) or not. I have no knowledge of C and have a very vague knowledge of command-line interfaces way back from when I previously used DOS. I also can't edit my asound.state file in var/lib/alsa, which I think might have something to do with permissions? I've read that I need to edit this to get my soundcard to work. 

While we're at it, anyone want to recommend a good wireless card? ](*,)

---

### Post by oldos2er on 2008-04-15
You need the package build-essential: "sudo aptitude install build-essential"

---

### Post by mali2297 on 2008-04-15
You need the package **build-essential**, it should be available from the Install CD. Install the package with the commands
```

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

```
That will give you the gcc compiler together with the most essential tools. But to compile an emulator, you will probably need more packages.

I suggest that you give priority to the network connection. Once that is fixed, you can install zsnes or whatever directly from the repositories.

---

### Post by Furbs on 2008-04-15
Thanks for the replies! I put in the CD-ROM and entered those three lines of code, and aptitude still seems upset that I don't have a network connection, but it seems like it manages to update to gcc 6.1.10, i think.

However, when I go back to try to install MPlayer, it gives me tons of errors and tells me that my cc is version 4.1.3, among many other things which seem to not be present. Finally, it tells me that inttypes.h and bitypes.h are not present, and that installation is impossible.

I think you are right that I really need to get this computer connected to a network for it to have a chance. I have tried creating a network startup disk under WinXP, and searching on these forums, but I still haven't figured out how to connect via Ethernet to my WinXP box, which is in turn connected to the internet. Is there any way to do this with a (possibly) broken C compiler? Xubuntu runs but isn't functional at all and I've been at a dead end for a day now, and I REALLY don't want to go back to WinXP!

---

### Post by mali2297 on 2008-04-16
There is generally no need to compile from source, hence the fact that gcc is not installed by default. Mplayer et cetera come in deb packages that contain the executable programs. The problem is to sort out the dependencies. If you have an internet connection, then the package manager will do this for you and download all dependent packages.

I suggest that you make a new thread entitled *Internet connection via WinXP* or something similar. Hopefully, you will then get help from people who know these stuff.

---

### Post by The Cog on 2008-04-16
Agreed. Forget everything except getting internet access. 

Can you even ping your gf's PC yet? You can see if you have an IP address with the command **ifconfig**. 

Once you can ping her PC, there are 3 things to set up:
* internet sharing on her PC
* A default route on your PC, pointing to hers
* IP addresses of the DNS name servers to use.

I have no idea how to set up internet sharing on windows. If you are lucky, that might make the other two steps happen automatically though.

---

### Post by Furbs on 2008-04-16
I just created [another thread](http://ubuntuforums.org/showthread.php?t=757449) for my networking issue, but I thought I would bring it up here as well:

> I am trying to get my computer onto the internet. It's a 2.4Ghz celeron 634mb RAM (onboard video) with Xubuntu Gutsy Gibbon installed, and I've found that none of my programs will install because it seems the C compiler is broken. I tried installing the C compiler from CD, which also did not work. I was told in another thread to post this here, so here it goes.

I just got a D-Link Rangebooster-G (model WDA2320), which has the Atheros chipset and is supposedly workable with the Madwifi drivers. This might be a good time to say that I don't know a whole lot about computers, and especially Linux. Anyway, it seems like all the methods for installing Madwifi involve using apt-get, which will not work because I'm not connected to the internet already. Yet, I need apt-get to install the drivers to connect to the internet. This paradox has been killing my brain for the last few days and I'm hoping someone can help! Thanks so much 

---

