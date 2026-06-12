---
title: "problem with 'make'"
date: 2006-10-27
forum: General Help
---

### Post by martbab on 2006-10-27
I have tried to install Gnome commander from sources, but I have encountered a problem.

when I run

martbab@hal:~/gnome-commander-1.2.1$ ./configure

everything seems to be fine. But when I try to run

martbab@hal:~/gnome-commander-1.2.1$ make

I get this message

make: *** No targets specified and no makefile found.  Stop.

I have installed the build-essentials and stuff, but I don't know where the problem is :(

---

### Post by jpkotta on 2006-10-27
The problem is that there appears to be no Makefile.  To make sure, ```
ls Makefile
```  The Makefile is generally created by configure, so either it didn't complete successfully or it has a bug.

---

### Post by martbab on 2006-10-28
Well, there really isn't a Makefile.. I have tried to run ./configure again and it displayed some errors....

checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

I have no idea what's going on..could you help please?

---

### Post by jpkotta on 2006-10-30
You need that package: XML::Parser.  Search for "xml parser" in synaptic and install the one for Perl.  Usually, the packages have a -dev at the end, but Perl is kind of an exception.  Then run configure again, and if it fails again, it will tell you what to search for.

---

### Post by martbab on 2006-10-31
oh, thank you for your help, i'm quite new to Linux so there will be probably some more silly questions on these forums :D

---

