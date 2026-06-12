---
title: "Would like access to library source files"
date: 2022-04-18
forum: General Help
---

### Post by the-scourge on 2022-04-18
Is there somewhere to get library source files? In particular, **libc **and all **curses **libs. I would like to look at **printf **especially
and all related "*printf's*" (**fprintf**, **sprintf**, etc). I have a game that uses **curses **and I need to use my own versions of *printf's*. I'm having trouble getting
this particular game going and it appears to be having problems when printing to the screen. I can't use the standard **printf, **or related funcs, because
I need to place strings, with args, to a particular place on the screen.

Does GNU have a repository somewhere that houses the source files for libraries? Or a particular package I can download to get access
to these files? I'm running 20.04 LTS

Thx,
JakeT

---

### Post by #&amp;thj^% on 2022-04-18
Would this suit your needs:
```
dpkg -S [soname]
```
replace <[soname]> with you desired query path.
EG:
```
dpkg -S libc
```
also might find this helpful: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
remember many, many, many source files are used to build one shared library. :)

---

### Post by Bashing-om on 2022-04-18
the-scourge - Hello

> 
Does GNU have a repository somewhere that houses the source files for libraries?


Yes ! All sources are available in the software repo.
Use the command
```
 apt source <package>
```
 (don't use sudo with it) to download the source of a package.

-my bit to try and help-

---

### Post by the-scourge on 2022-04-18
OK, thanx for the help, but... I'm afraid I'm a bit lost.

The **dpkg -S libc **generated over 500 files in various folders on my hard drive. Most of which appear to be binary files. Couldn't find any that
contained library source files. What am I supposed to be looking for?

The **apt source gnulib **generated 5 **.mo** files and I don't know how to open said file. Do these .mo files contain source files for various libraries??

---

### Post by #&amp;thj^% on 2022-04-18
> **the-scourge said:**
>  What am I supposed to be looking for?

Perhaps I'm bit lost myself: "Would like access to library source files"

    The source code for the library is compiled into one or more object modules, which are binary files that can be included in a library and linked to executable clients.
    The object modules are packaged into a single file. For a static library, the standard extension is .a for "archive." For a dynamic library, the extension is .so for "shared object." The two sample libraries, which have the same functionality, are published as the files libprimes.a (static) and libshprimes.so (dynamic). The prefix lib is used for both types of library.
    The library file is copied to a standard directory so that client programs, without fuss, can access the library. A typical location for the library, whether static or dynamic, is /usr/lib or /usr/local/lib; other locations are possible.
Maybe state a clearer support subject, >>with what you intend to do.

---

### Post by norobro on 2022-04-18
> **the-scourge said:**
> Does GNU have a repository somewhere that houses the source files for libraries?
You can browse the source for glibc here: [https://sourceware.org/git/?p=glibc.git;a=tree;f=stdio-common;h=37acb117e74b5130db254203053dbace5f25682f;hb=f9f5c70e7f2ba928fe86801b8d05ffe8f4972d59](https://sourceware.org/git/?p=glibc.git;a=tree;f=stdio-common;h=37acb117e74b5130db254203053dbace5f25682f;hb=f9f5c70e7f2ba928fe86801b8d05ffe8f4972d59)
Seems the code for printf et. al. is in vfprintf-internal.c   

Looks pretty complex. Good luck.

---

### Post by the-scourge on 2022-04-18
I thought when I said "source files" I was clear enough, i.e., meaning the C source code. I didn't say object or binary files of the libraries as "ar -x {lib}" would've got me that.
I suppose I could have said "C source" files to be 100% clear.

---

### Post by Holger_Gehrke on 2022-04-19
'dpkg -S path-and-filename' has nothing to do with source files. It's  for finding out what package a given file belongs to. 'apt source  package-name' is what you want, but you have to configure source  repositories for downloading the source code, either by editing your  /etc/apt/sources.list or by activating one or more of the source  repositories in the software source settings in the GUI.
The name of  the package should be libc6. Alternatively to getting the source package  through apt you can download it from  [https://packages.ubuntu.com/focal/libc6](https://packages.ubuntu.com/focal/libc6)

Holger

---

### Post by SeijiSensei on 2022-04-19
The site packages.ubuntu.com has entries for every piece of software on the system. Here's the page for libc on 20.04.

[https://packages.ubuntu.com/focal/libc++-12-dev](https://packages.ubuntu.com/focal/libc++-12-dev)

AFAIK, all the -dev packages contain source code.

---

### Post by Holger_Gehrke on 2022-04-19
> **SeijiSensei said:**
> The site packages.ubuntu.com has entries for every piece of software on the system. Here's the page for libc on 20.04.

[https://packages.ubuntu.com/focal/libc++-12-dev](https://packages.ubuntu.com/focal/libc++-12-dev)

AFAIK, all the -dev packages contain source code.

Nope, that's libc++, which is for C++. And *-dev packages usually don't hold (complete) source, they have the header files you need to compile and link programs that use the library.

Holger

---

### Post by #&amp;thj^% on 2022-04-19
along with things you have been told about already. **(and Details do matter**)
The source code for every package in the main and universe archives is in Launchpad ([https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)), or you can get it by enabling the Sources in the Software Properties, and then doing apt-get source $packagename in a terminal, *after* refreshing the package information.

Source code for packages in the partner repositories is not generally available, as they are not all not open source applications. You will find this true for some items available in the Software Center.

Or for the whole kit and caboodle you can download the complete source code ISOs from the Ubuntu download servers:
Found Here:[https://cdimage.ubuntu.com/releases/](https://cdimage.ubuntu.com/releases/)

For Focal as an example: [https://cdimage.ubuntu.com/releases/20.04/release/source/](https://cdimage.ubuntu.com/releases/20.04/release/source/)

There is cscope for C codeing/source: [http://cscope.sourceforge.net/](http://cscope.sourceforge.net/)
it's a rather old program last updated 2012-08-04
```
cscope --=help
cscope: option '--=help' is ambiguous; possibilities: '--help' '--version'
Usage: cscope [-bcCdehklLqRTuUvV] [-f file] [-F file] [-i file] [-I dir] [-s dir]
              [-p number] [-P path] [-[0-8] pattern] [source files]


```
basic:
```
Building cross-reference...



Find this C symbol:
Find this global definition:
Find functions called by this function:
Find functions calling this function:
Find this text string:
Change this text string:
Find this egrep pattern:
Find this file:
Find files #including this file:
Find assignments to this symbol:


```

You appear at a glance to be a bit skeptical?

---

