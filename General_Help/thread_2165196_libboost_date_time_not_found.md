---
title: "libboost_date_time not found"
date: 2013-08-03
forum: General Help
---

### Post by 3wais on 2013-08-03
I was trying to install and run some software. when I run it it gives me this error:
```
error while loading shared libraries: libboost_date_time-gcc42-1_38.so.1.38.0: cannot open shared object file: No such file or directory
```

running ```
ls /usr/lib/libboost*
``` gives me this:
```
/usr/lib/libboost_date_time.so.1.49.0/usr/lib/libboost_serialization.a
/usr/lib/libboost_serialization-mt.a
/usr/lib/libboost_serialization-mt.so
/usr/lib/libboost_serialization.so
/usr/lib/libboost_serialization.so.1.49.0
/usr/lib/libboost_wserialization.a
/usr/lib/libboost_wserialization-mt.a
/usr/lib/libboost_wserialization-mt.so
/usr/lib/libboost_wserialization.so
/usr/lib/libboost_wserialization.so.1.49.0
```

I try to install this package. but there is only those packages:
```
libboost-date-time1.49.0    libboost-date-time1.49-dev  libboost-date-time1.53.0    libboost-date-time1.53-dev  libboost-date-time-dev
```
nothing with gcc42 suffix

I tried installing them all but nothing seems to solve the problem. what shall I do ??

[COLOR=#000000][FONT=Verdana]update::[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I also tried creating a symbolic link for libboost_date_time.so.1.49.0 and name it to libboost_date_time-gcc42-1_38.so.1.38.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]that did not work. it gave me this error:
[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]```
[/FONT][/COLOR]error while loading shared libraries: libboost_date_time-gcc42-1_38.so.1.38.0: wrong ELF class: ELFCLASS32[COLOR=#222222][FONT=Verdana]
```[/FONT][/COLOR]

---

