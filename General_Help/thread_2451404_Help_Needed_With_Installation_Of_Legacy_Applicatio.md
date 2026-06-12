---
title: "Help Needed With Installation Of Legacy Application And Make Commands"
date: 2020-10-03
forum: General Help
---

### Post by vaughanb on 2020-10-03
Hi Everyone,

I am investigating the possibility of migrating a legacy application from Ubuntu 10.04 to Ubuntu 20.04 however I have encountered at least two problems when attempting to do so.

Part of the installation process of the legacy application involves running the command *make; make install* and the first error I encountered was the presence of deprecated method calls and functions in the c files when attempting to compile and build the c files through gcc version 9.  The legacy application was originally intended for gcc version 4.4.3 and I think I was able to solve this issue by installing gcc version 4.4 side by side with version 9.  However this led to another problem namely the errors  

*"cc1: error: unrecognized command line option "-fstack-protector-strong" *and
[I]"cc1: warning: unrecognized command line option "-Wno-unused-but-set-variable"

[/I]Based on what I have researched concerning the above two errors, it would seem that *-fstack-protector-strong *and *-Wno-unused-but-set-variable *are flags which are automatically set for the gcc compiler, but version 4.4 of the compiler doesn't understand them, only later versions of gcc do, but using later versions of gcc mean that parts of the c source code would be marked as deprecated.

I've tried setting environment variables, namely CFLAGS, CC and CXXFLAGS with the values *-fno-stack-protector,* *-Wno-unused-variable *and *-O* in an attempt to disable the above errors produced, and unfortunately I have not been able to solve the *"cc1: error: unrecognized command line option "-fstack-protector-strong" *and [I]"cc1: warning: unrecognized command line option "-Wno-unused-but-set-variable" 
[/I]errors.  The error stack is shown below.

make -C /lib/modules/5.4.0-48-generic/build M=/data/InstallFiles/drivers/Drivers modules
make[1]: Entering directory '/usr/src/linux-headers-5.4.0-48-generic'
  CC [M]  /data/InstallFiles/drivers/Drivers/dtcommon/dtcommon_module.o
cc1: error: unrecognized command line option "-fstack-protector-strong"
cc1: warning: unrecognized command line option "-Wno-unused-but-set-variable"
make[3]: *** [scripts/Makefile.build:275: /data/InstallFiles/drivers/Drivers/dtcommon/dtcommon_module.o] Error 1
make[2]: *** [scripts/Makefile.build:522: /data/InstallFiles/drivers/Drivers/dtcommon] Error 2
make[1]: *** [Makefile:1734: /data/InstallFiles/drivers/Drivers] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.4.0-48-generic'
make: *** [Makefile:4: all] Error 2
mkdir -p /lib/modules/DT/custom
cp */*.ko /lib/modules/DT/custom
cp: cannot stat '*/*.ko': No such file or directory
make: *** [Makefile:10: install] Error 1

I also installed version 4.4 of the g++ compiler side by side with version 9 of g++ in case it was also needed.  If required I can post further details.

Thanks in advance for any assistance to this problem

---

### Post by guiverc on 2020-10-03
I only scanned your issue, but it maybe easier to create a VM/install of 14.04, see if it compiles there, then if it does, package it as a snap.

 Snaps will run in later releases (needed libraries are added to snap), so you should be able to use the created *snap* on a 20.04 system.

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   rmadison gcc
 gcc | 4:4.6.3-1ubuntu5   | precise         | amd64, armel, armhf, i386, powerpc
 gcc | 4:4.8.2-1ubuntu6   | trusty          | amd64, arm64, armhf, i386, powerpc, ppc64el
 gcc | 4:5.3.1-1ubuntu1   | xenial          | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 gcc | 4:7.3.0-3ubuntu2   | bionic          | amd64, arm64, armhf, i386, ppc64el, s390x
 gcc | 4:7.4.0-1ubuntu2.3 | bionic-security | amd64, arm64, armhf, i386, ppc64el, s390x
 gcc | 4:7.4.0-1ubuntu2.3 | bionic-updates  | amd64, arm64, armhf, i386, ppc64el, s390x
 gcc | 4:9.3.0-1ubuntu2   | focal           | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 gcc | 4:10.2.0-1ubuntu1  | groovy          | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x


```

---

### Post by vaughanb on 2020-10-04
Hi guiverc,

Thanks for your advice.  

I see you mention Ubuntu version 14.04 as the version with which I should create the snap, is this the minimum version with which I could create a snap, I'm mentioning this as it would be easier if I could create a snap with version 10.04, as I know the legacy application works on version 10.04.

I did some searching, but couldn't find anything confirming that a snap could be made with version 10.04.

Thanks in advance.

Vaughan

---

### Post by TheFu on 2020-10-04
This is a good example of when a snap could be useful.

You might try using an lxd container with 10.04, assuming it doesn't need networking.  No 10.04 system should be allowed on any network today. Same for 12.04 or 12.10. All of those have well-known remote root exploits where the machines can easily be "popped" and completely pwn'ed in less than 1 minute if on a network.

14.04 still has paid extended support. My guess is that snap support was back-ported to that release.  Open the wallet, pay Canonical their fee and see if you can at least move to that support level. In the meantime, you can hire a C programmer to port the program to 20.04.  I used to make a living doing that for my employer - not so much trying to keep old programs working, but porting to other platforms - so Solaris --> AIX --> HP-UX --> Linux --> Windows --> MacOS.  Last time I did that kind of work was over 20 yrs ago, so I'm not currently qualified.  Pay a C developer 4 hrs to solve the problem (probably about US$500). If she can't solve it - meaning move to a current gcc on 20.04 - in that time, then a report should be included for an estimate to do the work to accomplish that. You can then take that out to a tech "job" bidding sight to see if someone in a low-cost part of the world can port the code. I'd ask for a docker or lxd package as the final deliverable, along with all the code files. The person who did the estimate may be really close to finishing the port, so perhaps they can provide the program.   I don't know how to create a docker or lxd package and I'd personally avoid any snap packages because the code has to be shared with Canonical, which doesn't interest me at all, in order to build a snap package today.

The gcc changes are probably something that can be configured away easily in the gmake Makefiles.  On Linux, make == gmake.  Just need to find the settings and remove them. That would be the "best case."  If there is any code that is truly dependent on those settings, then it could become nasty.  I suspect the *stack-protector-strong* option is just for extra protection, not really mandatory.

If this code is for drivers to manage/access hardware devices, I don't think a snap or any container can be used.

Good luck. I hope this is really easy and cheap.

---

