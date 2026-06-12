---
title: "How / where do I set environment variables for gcc?"
date: 2014-10-23
forum: General Help
---

### Post by shahin on 2014-10-23
Hi Guys
I get the following error when I try to compile with gcc:
```
sansari@ubuntu:~/androidkernel$ sudo make ARCH=arm
[sudo] password for sansari: 
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[1]: `include/generated/mach-types.h' is up to date.
  CC      kernel/bounds.s
gcc: error trying to exec 'cc1': execvp: No such file or directory
make[1]: *** [kernel/bounds.s] Error 1
make: *** [prepare0] Error 2

```
After doing a little search online, I suspected the cause to be a discrepency between the default Ubuntu compiler and what gcc tries to use. Here is what I see 
When I issue the following command I get:
```
gcc -print-prog-name=cc1
/usr/lib/gcc/x86_64-linux-gnu/4.6/cc1

```
when I ask for the location of default compiler I get:
```
which cc
/usr/bin/cc

```
I tried this command:
```

export cc1=/usr/lib/gcc/x86_64-linux-gnu/4.6/cc1

```
But I still get the same error. Should I have perhaps issued:
```
export cc=/usr/lib/gcc/x86_64-linux-gnu/4.6/cc1
```
Basically I do not understand shell vs. bash, and which files Ubuntu uses to set environment variables. I did try to review Ubuntu documentation online. But I don't even know where to begin, so pointing me to the right document even is greatly appreciated. I think the problem I am running into is that gcc tries to issue the command 'cc', which points to /usr/bin/cc rather than /usr/lib/gcc/x86_64-linux-gnu/4.6/cc1. Am I right? I also need to understand better how to set environment variables for root vs. user space. I have a lot of my files in the root space ( I know that was an awful thing to do, and I would never do it again. I just do not have a way back now )

---

### Post by TheFu on 2014-10-24
On my system, /usr/bin/cc -> /etc/alternatives/cc
and
/etc/alternatives/cc -> /usr/bin/gcc
and
/usr/bin/gcc -> gcc-4.8

Learn about symbolic links.

Environment variables for compiling are normally set inside the Makefile.
BTW - using sudo is bad for builds almost always.  After doing it once, the entire development tree is polluted and needs to be fixed.  Learn about UNIX/Linux file permissions ... actually learning about the OS sooner than later will save you hours, days, weeks, months of frustration. There is a great, free, book that can be easily skimmed in 1-2 hrs.  Search for "command line linux" to find it.  There are many links to it throughout these forums.  Also, help.ubuntu.com is a good resource, but the book provides an organized introduction which can be learned easier than jumping from topic to topic around the web.

---

### Post by shahin on 2014-10-24
Thanks. I think I'll unzip the source I started with to a new location, and this time I won't use sudo. I searched for the "command line Linux", and found this  [http://www.nixtutor.com/freebsd/understanding-symbolic-links/]("site:") What do you think? Is this the document you mentioned? I think it is pretty useful. I also looked up symbolic links. I'll review permissions; I did not think I would have a permission issue if I am running everything from root logged in as su.

---

### Post by steeldriver on 2014-10-24
Did you install an arm toolchain? if so which one, and how? It seems more likely to me that your issue is related to an incomplete toolchain path (rather than anything to do with environment variables)

When you run 

```

gcc -print-prog-name=cc1

```

you are seeing the prog-name for the regular "system" version of gcc, whereas you presumably should be seeing the version related to your arm version of gcc - for example

```

$ arm-2008q3/bin/arm-none-eabi-gcc -print-prog-name=cc1
/home/steeldriver/arm/arm-2008q3/bin/../libexec/gcc/arm-none-eabi/4.3.2/cc1

```

---

### Post by TheFu on 2014-10-24
Ah - he's trying to cross-compile for ARM on an amd64 system.  I've never used cross-compilers on Linux (but have for many, many other platforms).

It appears the arm capable compiler isn't there.  Plus doesn't every ARM system have different libs/includes that need to be part of the build?  Picking up **any** x86 versions of those will be bad.  For embedded systems, the exact, correct, specific, libs will be necessary for the OS too.

Knowing which of Android, RaspberryPi or some other system compiles would be helpful too. 
Still - using the Makefile is how we setup cross-compilation, but I don't know how folks normally do it today. That was ... er ... a few years ago when 64-bit was new for everyone, everywhere and 16-bit systems were still running.

---

### Post by shahin on 2014-10-24
> **TheFu said:**
> Ah - he's trying to cross-compile for ARM on an amd64 system.  I've never used cross-compilers on Linux (but have for many, many other platforms).

It appears the arm capable compiler isn't there.  Plus doesn't every ARM system have different libs/includes that need to be part of the build?  Picking up **any** x86 versions of those will be bad.  For embedded systems, the exact, correct, specific, libs will be necessary for the OS too.

Knowing which of Android, RaspberryPi or some other system compiles would be helpful too. 
Still - using the Makefile is how we setup cross-compilation, but I don't know how folks normally do it today. That was ... er ... a few years ago when 64-bit was new for everyone, everywhere and 16-bit systems were still running.

You got it. That is what I am trying to do. I am pretty sure I have the right toolchain. I am following the procedures I got from the vendor; Samsung in this case. I got the toolchain from Android. And the error I am seeing does not have any indications of a compiler mismatch. It just seems like gcc cannot find cc1, which according to my online research, is one of gcc's components which compiles C code to object file and create an executable also. So I have been hitting the sites that was suggested earlier. And I am planning on trying a few things. But any more specific help is greatly appreciated.

---

### Post by shahin on 2014-10-24
> **steeldriver said:**
> Did you install an arm toolchain? if so which one, and how? It seems more likely to me that your issue is related to an incomplete toolchain path (rather than anything to do with environment variables)

When you run 

```

gcc -print-prog-name=cc1

```

you are seeing the prog-name for the regular "system" version of gcc, whereas you presumably should be seeing the version related to your arm version of gcc - for example

```

$ arm-2008q3/bin/arm-none-eabi-gcc -print-prog-name=cc1
/home/steeldriver/arm/arm-2008q3/bin/../libexec/gcc/arm-none-eabi/4.3.2/cc1

```

If my Makefile path was bad, would not gcc just not run? I updated the Makefile and added the path to my toolchain to the CROSSCOMPILE variable in Makefile as stated in the procedures.

---

### Post by TheFu on 2014-10-24
Actually - 
```
export cc=/usr/lib/gcc/x86_64-linux-gnu/4.6/cc1
```   is wrong.
That is the Linux x64 compiler. You need the arm compiler and need to point at it.
[https://stackoverflow.com/questions/20314558/cross-compile-helloworld-c-to-arm-cortex-a5](https://stackoverflow.com/questions/20314558/cross-compile-helloworld-c-to-arm-cortex-a5) might help.

Oh - and if gcc exists on the x64 Linux system, why wouldn't it run unless told differently?  The PATH controls that almost always for native compilers.

---

### Post by shahin on 2014-10-24
> **TheFu said:**
> Actually - 
```
export cc=/usr/lib/gcc/x86_64-linux-gnu/4.6/cc1
```   is wrong.
That is the Linux x64 compiler. You need the arm compiler and need to point at it.

Yes you are right. I'll review the link you sent. I read online that there are two sources for ARM cross compiler toolchains, one was android source and the other is  a site call codesourcery. I tried the later, and ran into some issues with Make stopping when it encounters warnings. So I thought I would give the android version a shot. But it seems like I am running into problems even earlier this time. I will check the path to my toolchain again. 
Thanks

---

### Post by steeldriver on 2014-10-24
(lower case) [FONT=courier new]cc[/FONT] would be the name of the executable - if you are trying to change the location of the compiler used by make, the variable to modify would likely be (upper case) [FONT=courier new]CC[/FONT]

---

