---
title: "libmysqlclient.so.16"
date: 2018-02-16
forum: General Help
---

### Post by aiwendil42 on 2018-02-16
I have a program I'm trying to get running on an Ubuntu machine (I've previously run it only on CentOS), and when executing it I get:

```
error while loading shared libraries: libmysqlclient.so.16: cannot open shared object file: No such file or directory
```

If I do "locate libmysqlclient.so", I get only:

```
/usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
/usr/lib/x86_64-linux-gnu/libmysqlclient.so.18.0.0

```

I've tried:

```
apt-get install libmysqlclient-dev
```

But this did not solve the problem, and I still don't appear to have libmysqlclient.so.16.  

I also found a forum post somewhere where someone apparently solved this by installing the rpm MySQL-shared-compat-5.1.49-1.rhel5.x86_64.rpm, so I tried this but with no change in the result.

I don't know if this is relevant, but the program I'm trying to execute is 32-bit, and I gather my system doesn't have 32-bit support, so initially I was getting "no such file or directory", until I followed the advice on this page: [https://askubuntu.com/questions/133389/no-such-file-or-directory-but-the-file-exists](https://askubuntu.com/questions/133389/no-such-file-or-directory-but-the-file-exists).

Any help would be very much appreciated.  Thanks.

---

### Post by #&amp;thj^% on 2018-02-16
What is the **name and version **of the package you are trying to run or install?

---

### Post by aiwendil42 on 2018-02-16
It's not a package; it's a locally written program.

---

### Post by Impavidus on 2018-02-17
Your program depends on libmysqlclient version 16, but your Ubuntu system comes with libmysqlclient version 18. Which tells me you probably run Ubuntu 14.04, as the other supported releases come with version 20. Version 16 must be pretty old.

In principle you can install version 16 and 18 side by side. You have to find it somewhere and install the dependencies of version 16 too. This is known as dependency hell, which is something you want to avoid. 32 bit vs 64 bit may also be a problem.

As you call it locally written, I assume you have source code. Best to recompile it to make it work for version 18, 64 bit, assuming it's compatible with that version.

I don't really know about mysql. Never did much database work.

---

### Post by spjackson on 2018-02-17
> **aiwendil42 said:**
> 
I also found a forum post somewhere where someone apparently solved this by installing the rpm MySQL-shared-compat-5.1.49-1.rhel5.x86_64.rpm, so I tried this but with no change in the result.

I don't know if this is relevant, but the program I'm trying to execute is 32-bit

That rpm provides a 64-bit library which will be of no use whatsoever to your 32-bit program. You might get somewhere with the equivalent i386 rpm. Which Ubuntu version are you trying to run this on?

---

### Post by aiwendil42 on 2018-02-19
[QUOTE=Impavidus]
As you call it locally written, I assume you have source code. Best to  recompile it to make it work for version 18, 64 bit, assuming it's  compatible with that version.[/QUOTE]

Yes, I have the source code, but finding where libmysqlclient is getting included is not trivial.  I also have no idea how to compile for 64 bit vs 32 bit, though I suppose I could figure that out with a little searching.

[QUOTE=spjackson]That rpm provides a 64-bit library which will be of no use whatsoever to  your 32-bit program. You might get somewhere with the equivalent i386  rpm. Which Ubuntu version are you trying to run this on?[/QUOTE]

Ah, good point.  I can't seem to find an i386 version of this rpm, though...

---

### Post by Impavidus on 2018-02-20
On 32 bit systems the compiler will automatically produce 32 bit executables, on 64 bit systems the compiler will automatically produce 64 bit executables. It's during crosscompiling that things get a little harder. And it should automatically find the header files and libraries on your system, assuming you installed them. When I moved from 32 bit Ubuntu 13.10 to 64 bit Ubuntu 14.04 (or something around that), I had to recompile all my home-made applications by just running make. No tweaks necessary. After other release upgrades I also had to recompile to link to new libraries. As long as function prototypes don't change, that works.

But there is the possibility that your software really depends on being 32 bit or using libmysqlclient 16.

---

### Post by aiwendil42 on 2018-02-20
> **Impavidus said:**
> On 32 bit systems the compiler will automatically produce 32 bit executables, on 64 bit systems the compiler will automatically produce 64 bit executables. It's during crosscompiling that things get a little harder. And it should automatically find the header files and libraries on your system, assuming you installed them. When I moved from 32 bit Ubuntu 13.10 to 64 bit Ubuntu 14.04 (or something around that), I had to recompile all my home-made applications by just running make. No tweaks necessary. After other release upgrades I also had to recompile to link to new libraries. As long as function prototypes don't change, that works.

But there is the possibility that your software really depends on being 32 bit or using libmysqlclient 16.

Ah, OK, maybe I just didn't actually cleanly recompile everything like I thought.  I'll try that.

---

