---
title: "Problems when installing DDD and Insight debuggers"
date: 2013-12-02
forum: General Help
---

### Post by silvercats on 2013-12-02
Insight is the more important one than the DDD. running x64

DDD error

```
mv -f .deps/sigName.Tpo .deps/sigName.Po
g++ -DHAVE_CONFIG_H -I.  -I./..    -O2 -g -Wall -W -Wwrite-strings -trigraphs  -MT strclass.o -MD -MP -MF .deps/strclass.Tpo -c -o strclass.o strclass.C
strclass.C: In function â€˜std::istream& operator>>(std::istream&, string&)â€™:
strclass.C:1546:35: error: â€˜EOFâ€™ was not declared in this scope
strclass.C:1559:15: error: â€˜EOFâ€™ was not declared in this scope
strclass.C: In function â€˜int readline(std::istream&, string&, char, int)â€™:
strclass.C:1589:35: error: â€˜EOFâ€™ was not declared in this scope
strclass.C:1602:15: error: â€˜EOFâ€™ was not declared in this scope
make[2]: *** [strclass.o] Error 1
make[2]: Leaving directory `/home/haritha/Desktop/ddd-3.3.12/ddd'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/haritha/Desktop/ddd-3.3.12/ddd'
make: *** [all-recursive] Error 1

```

Insight error


```

libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.././bfd -I. -I. -I.././bfd -I.././bfd/../include -W -Wall -Wstrict-prototypes -Wmissing-prototypes -Werror -g -O2 -c elf64-x86-64.c -o elf64-x86-64.o
elf64-x86-64.c: In function 'elf64_x86_64_relocate_section':
elf64-x86-64.c:2364:16: error: variable 'warned' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:2807:29: error: variable 'type2' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:3053:29: error: variable 'type2' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:3053:23: error: variable 'type' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:3053:18: error: variable 'val' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:3084:23: error: variable 'type' set but not used [-Werror=unused-but-set-variable]
elf64-x86-64.c:3084:18: error: variable 'val' set but not used [-Werror=unused-but-set-variable]
cc1: all warnings being treated as errors
make[4]: *** [elf64-x86-64.lo] Error 1
make[4]: Leaving directory `/home/haritha/Downloads/insight-6.8-1/bfd'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/haritha/Downloads/insight-6.8-1/bfd'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/haritha/Downloads/insight-6.8-1/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/home/haritha/Downloads/insight-6.8-1'
make: *** [all] Error 2



```


thanks.

---

### Post by silvercats on 2013-12-04
hello....?

---

### Post by silvercats on 2013-12-13
Doesn't anybody having any idea at all?

---

