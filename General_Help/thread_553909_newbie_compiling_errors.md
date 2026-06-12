---
title: "newbie compiling errors"
date: 2007-09-18
forum: General Help
---

### Post by Ryanicus on 2007-09-18
I'm trying to "make" this MUD codebase which is available here: [http://www.awakenedworlds.net/index.php?page=5](http://www.awakenedworlds.net/index.php?page=5) and I'm getting dozens of errors in each file such as these:

g++  -Dlinux   -c -o pro_create.o pro_create.cpp
pro_create.cpp: In function 'void do_program(char_data*, char*, int, int)':
pro_create.cpp:314: warning: minimum/maximum operators are deprecated
g++  -Dlinux   -c -o quest.o quest.cpp
g++  -Dlinux   -c -o redit.o redit.cpp
redit.cpp: In function 'void redit_parse(descriptor_data*, char*)':
redit.cpp:883: warning: minimum/maximum operators are deprecated
redit.cpp:883: warning: minimum/maximum operators are deprecated
redit.cpp:888: warning: minimum/maximum operators are deprecated
redit.cpp:888: warning: minimum/maximum operators are deprecated
g++  -Dlinux   -c -o screen.o screen.cpp
g++  -Dlinux   -c -o shop.o shop.cpp
shop.cpp: In function 'void shopping_sell(char*, char_data*, char_data*, int)':
shop.cpp:1074: warning: minimum/maximum operators are deprecated
shop.cpp:1127: warning: minimum/maximum operators are deprecated

This continues with the same errors popping up on most of the files.  I'm new to Ubuntu & bash. I haven't encountered this problem in cygwin and I'm not sure what to do. Any help would be greatly appreciated. Cheers.

-ryanicus

---

### Post by alacheesu on 2007-09-18
Warnings are not the same as errors. It means exactly what the warnings say, namely the source code contains old and deprecated min/max operators. To put it simple, once upon a time a programmer could write doSomethingThisWay, but then someone found out that this was a bad way to do it and you should now write doSomethingThatWay. If you still write doSomethingThisWay you would get the warning that doSomethingThisWay is deprecated, but it would still work. If you used an older compiler you would not get those warnings, but the end result would be the same. Eventually the compiler will drop support for doSomethingThisWay. It's not something you need worry about, unless you want to modify the code yourself.

---

