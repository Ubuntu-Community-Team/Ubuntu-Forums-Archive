---
title: "Compile Errors--what packages do I need?"
date: 2006-10-21
forum: General Help
---

### Post by LodeRunner on 2006-10-21
So, I'm trying to get this not-exactly-commonplace [program]("http://www.trading-shim.org/") to work and it just isn't happening.  make is throwing all kinds of errors at me.   I've installed linux-kernel-headers and libmysqlclient15-dev (the program uses MySQL) to no avail.  Ubuntu doesn't even come with make installed, so I'm wondering if there are some other commonly-needed packages I could be missing.

Running Xubuntu 6.06 with extra repositories enabled and all updates installed.  Am 100% positive I'm making from the correct directory.  Makefile specifies g++, which I've already installed.  Cleaned error list:

make shim 2>&1 | bin/filter | head -16
make[1]: Entering directory [snip]
g++ -Wall -g -I/usr/include/mysql  -c -o once.o src/once.c
src/../lib/interfaces.h:13: error: 'void* operator new(nat)' may not be declared within a namespace
src/../lib/interfaces.h:14: error: 'void* operator new(nat, void*)' may not be declared within a namespace
src/../lib/interfaces.h:15: error: 'void* operator new(nat, const Pool&)' may not be declared within a namespace
src/../lib/interfaces.h:16: error: 'void* operator new(nat, const PermPool&)' may not be declared within a namespace
src/../lib/interfaces.h:17: error: 'void* operator new(nat, const Factories&)' may not be declared within a namespace
src/../lib/interfaces.h:18: error: 'void* operator new(nat, const Products&)' may not be declared within a namespace
src/../lib/interfaces.h:20: error: 'void* operator new [](nat)' may not be declared within a namespace
src/../lib/interfaces.h:21: error: 'void* operator new [](nat, const Pool&)' may not be declared within a namespace
src/../lib/interfaces.h:22: error: 'void* operator new [](nat, const PermPool&)' may not be declared within a namespace
src/../lib/interfaces.h:23: error: 'void* operator new [](nat, const Factories&)' may not be declared within a namespace
src/../lib/interfaces.h:24: error: 'void* operator new [](nat, const Products&)' may not be declared within a namespace
src/term.h:14: warning: 'class obj::Term' has virtual functions but non-virtual destructor
src/term.h:30: warning: 'class obj::Empty' has virtual functions but non-virtual destructor
src/term.h:39: warning: 'class obj::String' has virtual functions but non-virtual destructor

---

### Post by raul_ on 2006-10-21
It seems that it uses some kind of script that u don't have installed (maybe python based for example) Check for the dependencies in the programs website and see if u've installed them

---

### Post by moore.bryan on 2006-10-21
*a quick check on the trading shim website suggested reading the INSTALL file... is there a text file by that name in the untar'd dir?*

---

### Post by LodeRunner on 2006-10-21
> **raul_ said:**
> It seems that it uses some kind of script that u don't have installed (maybe python based for example) Check for the dependencies in the programs website and see if u've installed them

Actually, I just noticed one of the devs sent me a quick list of packages I should have, but unfortunately they're yum (they use CentOS--a fine distro to be sure, but it's no Ubuntu)...  

> yum -y install mysql-devel mysqlclient10-devel gcc-c++ \
               make

is probably enough to pull in a sufficient minimal build
environment, by the time it is done grabbing the dependencies

Not sure if that helps at all or not.  The only relevant-sounding mysql dev package I could find was libmysqlclient15-dev (which I've already installed), and I can't find a gcc package that mentions c++ in the description, let alone has it in the name.

---

### Post by LodeRunner on 2006-10-21
> **moore.bryan said:**
> *a quick check on the trading shim website suggested reading the INSTALL file... is there a text file by that name in the untar'd dir?*

Yes.  I'm lazy, but not THAT lazy.  Wouldn't waste everyone's time without having thoroughly gone over the documentation myself. I emailed the devs, too, who're helpful but (perhaps understandably) not so eager to hold my hand through my dependency issues on a distro they don't use or support.

---

### Post by moore.bryan on 2006-10-22
[I]i wasn't trying to insult you, lode... i've had packages not include readme's the website says should be there; i was just checking.
;-)
[/I]

---

### Post by LodeRunner on 2006-10-22
> **moore.bryan said:**
> [I]i wasn't trying to insult you, lode... i've had packages not include readme's the website says should be there; i was just checking.
;-)
[/I]

And I didn't take offense.  Was merely trying to clarify that while I'm not any sort of expert, I'm not utterly clueless/helpless/lazy. I'm sure there are plenty of queries from people who haven't attempted to read any documentation.


EDIT: The dev finally got back to me.  The gcc package he referenced is actually an earlier version, and when he used the version I'm using he was able to duplicate the exact error list I was received.  So the problem apparently is on their end, and while they work on fixing it I can probably work around by using an earlier version of gcc.

---

