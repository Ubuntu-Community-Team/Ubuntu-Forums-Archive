---
title: "Installing a program, make errors..."
date: 2007-07-06
forum: General Help
---

### Post by NT4usB on 2007-07-06
So, I'm trying to install this Dominoes game:
[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/DMN-20434.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Arcade/DMN-20434.shtml)
./configure then make gives these errors. I don't have a clue how to fix them. Google doesn't help much. A couple hits...
Any suggestions how to make it work or, maybe another plain old domino game that will install?
```
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../.. -DCONFIG_DIR=\"/usr/local/etc\" -DPLUGIN_DIR=\"/usr/local/lib/dmn\" -DPLUGIN_EXT=\".so\" -I/usr/include/libxml++-1.0 -I/usr/lib/libxml++-1.0/include -I/usr/include/libxml2 -g -O2 -MT default_la-configfile.lo -MD -MP -MF .deps/default_la-configfile.Tpo -c configfile.cpp  -fPIC -DPIC -o .libs/default_la-configfile.o
configfile.h:54: error: expected ',' or '...' before '&' token
configfile.h:54: error: ISO C++ forbids declaration of 'AttributeMap' with no type
configfile.cpp:39: error: expected ',' or '...' before '&' token
configfile.cpp:39: error: ISO C++ forbids declaration of 'AttributeMap' with no type
configfile.cpp: In member function 'void dmn::ConfigFile::on_start_element(const std::string&, int)':
configfile.cpp:46: error: 'attributes' was not declared in this scope
configfile.cpp:53: error: 'AttributeMap' is not a class or namespace
configfile.cpp:53: error: expected `;' before 'iter'
configfile.cpp:54: error: 'iter' was not declared in this scope
configfile.cpp:54: error: 'attributes' was not declared in this scope
configfile.cpp:56: error: 'iter' was not declared in this scope
configfile.cpp:57: error: 'attributes' was not declared in this scope
configfile.cpp:64: error: 'attributes' was not declared in this scope
configfile.cpp:67: error: 'AttributeMap' is not a class or namespace
configfile.cpp:67: error: expected `;' before 'iter'
configfile.cpp:68: error: 'iter' was not declared in this scope
configfile.cpp:68: error: 'attributes' was not declared in this scope
configfile.cpp:72: error: 'iter' was not declared in this scope
configfile.cpp:74: error: 'iter' was not declared in this scope
configfile.cpp:76: error: 'iter' was not declared in this scope
configfile.cpp:78: error: 'iter' was not declared in this scope
configfile.cpp:80: error: 'iter' was not declared in this scope
configfile.cpp:82: error: 'iter' was not declared in this scope
configfile.cpp:84: error: 'iter' was not declared in this scope
configfile.cpp:86: error: 'iter' was not declared in this scope
make[3]: *** [default_la-configfile.lo] Error 1
make[3]: Leaving directory `/home/ct/dmn-0.4/src/Config'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ct/dmn-0.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ct/dmn-0.4'
make: *** [all] Error 2

```

---

### Post by CautionaryX on 2007-07-06
Did you install build-essential?

try running "sudo apt-get install build-essential" in a terminal then try to compile the game again.

---

### Post by NT4usB on 2007-07-07
build-essential was installed.
Good thought though. I probably have the wrong version of something that's causing it.
It requires libxml++ and I installed the wrong version of that and it wouldn't build at all...

---

