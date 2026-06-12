---
title: "Installing Ralink 3062 driver getting compiler errors"
date: 2016-09-28
forum: General Help
---

### Post by Ralph L on 2016-09-28
I am trying to install an Ralink 3062 network card driver following the instructions in [https://ubuntuforums.org/showthread.php?t=1850267](https://ubuntuforums.org/showthread.php?t=1850267) .  However, when I do "make" I get a compiler error that says that the macros __DATE__ and __TIME__ should not be used in naming the version, since it will not be possible to reproduce the same code at a different date and time.  Apparently no one else ran into this problem, so I am guessing that the present compiler flags more errors than the old compiler--or something else.  Attached are the source code and the compiler output.  I would appreciate any input.

---

### Post by Ralph L on 2016-09-30
I substituted "Feb 12 2011" for __DATE__ and "23:59:01" for __TIME__ and the module sta_ioctl.c compiled.  However, now the module rt_linux.c gets and error on the statements: ```
pOSFSInfo->fsuid = current_fsuid();
pOSFSInfo->fsgid = current_fsgid();

```complaining that ```
/rt_linux.c:1233:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kuid_t {aka const struct <anonymous>}&#8217;
   pOSFSInfo->fsuid = current_fsuid();
/rt_linux.c:1234:20: error: incompatible types when assigning to type &#8216;int&#8217; from type &#8216;kgid_t {aka const struct <anonymous>}&#8217;
   pOSFSInfo->fsgid = current_fsgid();  
``` This happens when rt_linux is working on the version number, so I am guessing that my substitution for date and time in sta_ioctl.c was incorrect.  The C code is attached to the first post so anybody can extract it, open a terminal on the main (lowest level) folder and type "make".  The you can see the errors and what I tried to do to fix them.  Since other people got this to compile, I wonder if I am missing a build-essential file, or something like that.

I sure could use some help on this from somebody that knows C.  I don't.

Thanks

---

### Post by Ralph L on 2016-10-01
I managed to fix the compiler errors by dropping back to Ubuntu 12.04 and doing the compilation.  I am guessing that the Ralink 3062 driver requires an older version of linux-headers (or some other package).  Anyway under Ubuntu 12.04 the compiler errors went away (still a bunch of compiler warnings) and I was able to complete the "make" and "make install" for the driver.  The driver I am trying to use is DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.  It is included in this thread as an attachment--above).  Does anybody know how I can find what linux-headers (or other package) is required to do the "make" that would be in my old Ubuntu 12.04 system, but not in my new Xubuntu 16.04 system.??  I would like to be able to do the "make" under my new Xubuntu 16.04 system.

Even with the driver installed my Ralink 3062 card works only intermittently (under my old Ubuntu 12.04 system).  It loses communication whenever, I put a load on it, pauses a while and sometimes reconnects, sometimes not.  I am suspicious that correct firmware is not being used.  Would somebody tell me how I can check what firmware is being actually used by the 3062????  According to this web site [https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/) the correct firmware is rt2860.bin.  I see that file in /lib/firmware but I don't know for sure that it is being used.

I see that sometimes driver installation instructions include and update of initramfs,  Is this something I need to do to make sure the correct firmware is used.

Any help appreciated.

---

### Post by Ralph L on 2016-10-30
See [https://ubuntuforums.org/showthread.php?t=2338890](https://ubuntuforums.org/showthread.php?t=2338890) for how I finally got an 802.11 a/b/g/n wifi card to work on my Dell Latitude D610.

---

