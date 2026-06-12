---
title: "log4cpp 0.3.0"
date: 2006-10-17
forum: General Help
---

### Post by aljones15 on 2006-10-17
Hey Folks,

Trying to install log4cpp 0.3.0 or higher.
The only problem being the log4cpp in the ubuntu depository is old and the application I want to compile (nano-hive) requires log4cpp 0.3 or higher. I downloaded the source for the new log4cpp, but when I make it, it has a problem: 

Making all in src
make[1]: Entering directory `/home/andrew/Desktop/log4cpp-0.3.5rc3/src'
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -Wall -Wno-unused -pedantic -MT FileAppender.lo -MD -MP -MF ".deps/FileAppender.Tpo" -c -o FileAppender.lo FileAppender.cpp; \
        then mv -f ".deps/FileAppender.Tpo" ".deps/FileAppender.Plo"; else rm -f ".deps/FileAppender.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -Wall -Wno-unused -pedantic -MT FileAppender.lo -MD -MP -MF .deps/FileAppender.Tpo -c FileAppender.cpp  -fPIC -DPIC -o .libs/FileAppender.o
../include/log4cpp/Manipulator.hh:29: error: extra ';'
make[1]: *** [FileAppender.lo] Error 1
make[1]: Leaving directory `/home/andrew/Desktop/log4cpp-0.3.5rc3/src'
make: *** [all-recursive] Error 1

Any idea how I fix FileAppender or compile this or is there a binary for log4cpp that's 0.3 or above? the repository one is like 0.2.8 or something like that.

-
A

---

### Post by po0f on 2006-10-17
aljones15,

The error message tells you what's wrong.  On line 29 in the header file /home/andrew/Desktop/log4cpp-0.3.5rc3/include/log4cpp/Manipulator.hh there is an extra semicolon ";".  Just delete it and re-run make.

---

### Post by aljones15 on 2006-10-18
did that and it worked, but now make check is reporting the following problem:

ERROR   : sub1 error
WARN    : sub1 warn
ERROR   : sub1 error
WARN    : sub1 warn
ERROR   : sub1 error
WARN    : sub1 warn
ERROR   : sub1 error
WARN    : sub1 warn

any idea? do you need more info?

---

