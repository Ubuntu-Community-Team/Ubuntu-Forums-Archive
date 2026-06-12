---
title: "Configure help PSPtoolchain"
date: 2006-10-21
forum: General Help
---

### Post by Joaobio on 2006-10-21
Hello, i'm having a problem installing the psptoolchain (the thing that makes possible to create pbp files that run in the PSP) psptoolchain works with gcc... anyway...

I've already installed this in cygwin and it ran perfectly, It takes about 3 hours to run the entire script, but in ubuntu at more or less 20 minutes it appears this :
```
configure.ac:8: error: possibly undefined macro: AC_PSPSDK_VERSION
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:9: error: possibly undefined macro: AC_PSPDEV_PATH
configure.ac:11: error: possibly undefined macro: AM_INIT_AUTOMAKE
configure.ac:14: error: possibly undefined macro: AC_PSPDEV_TOOLCHAIN
configure.ac:19: error: possibly undefined macro: AM_PROG_AS
./configure: line 1312: AC_1.0+beta2: command not found
./configure: line 1313: AC_PSPDEV_PATH: command not found
./configure: line 1315: syntax error near unexpected token `pspsdk,'
./configure: line 1315: `AM_INIT_AUTOMAKE(pspsdk, 1.0+beta2)'
ERROR RUNNING PSPSDK CONFIGURE

```

Does anybody know how can i solve this???

just for the record this is the page where i got the files, and saw the instalation progress. [http://www.psp-programming.com/tutorials/c/lesson01.htm]("http://www.psp-programming.com/tutorials/c/lesson01.htm")

I'm running in root (sudo -s -H) because in normal user i haven't enough permissions... Thank you.

Edit: I solved it, ubuntu installs an older version of automake, the version 1.4 even through apt-get or aptitude, currently the version is 1.9, and some scripts need that one...

I don't where to say this, but it would be better that the repositories are updated no?

Besides i've found a new problem, does somebody know where is the bootstrap of ubuntu, because i have to set there a new path... And i've no idea of where is it or how to change the path...

---

