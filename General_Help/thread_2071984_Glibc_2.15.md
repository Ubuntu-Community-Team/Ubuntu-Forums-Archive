---
title: "Glibc_2.15"
date: 2012-10-16
forum: General Help
---

### Post by claudiuhks on 2012-10-16
Hey!

I'm trying to compile an extension with CPP and C files for a gaming server.
The problem is that the systems where the game servers are hosted doesn't support GLIBC_2.15.

How should I compile my extension to be able to work without GLIBC_2.15?
Or how should I include that in my extension to not require it from other machine?

I'm compiling it with the next Makefile:

[php]
COMPILER = g++-4.6
OBJECTS = indungi_zombie.o amxxmodule.o GeoIP.o GeoIPCity.o regionName.o timeZone.o
FILENAME = indungi_zombie_amxx_i386.so

$(FILENAME) : $(OBJECTS)
  $(COMPILER) -o $@ $(OBJECTS) libmysqlclient.a -shared -ldl -lm -s

%.o : %.cpp
  $(COMPILER) -O2 -ffast-math -fpermissive -IHeaders -IMySQL -o $@ -c $<
[/php]

I underline that I'm really new in Linux and I just use Linux to compile things for Linux hosted applications.

Thanks in advance!
Have a good day!

- Claudiu

---

