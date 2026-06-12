---
title: "Amuc help"
date: 2007-10-29
forum: General Help
---

### Post by M0rThden on 2007-10-29
Ive run into a bit of a problem. Im running the new 7.10 version and i love it. But when i go to install amuc and i type in```
./configure
``` it gives me this```
scott@scott-laptop:~/Desktop/amuc-1.5$ sudo ./configure
Testing availability of ALSA ... conftest.cpp:2:28: error: alsa/asoundlib.h: No such file or directory
conftest.cpp: In function ‘int main()’:
conftest.cpp:4: error: ‘SND_LIB_MAJOR’ was not declared in this scope
conftest.cpp:4: error: ‘SND_LIB_MINOR’ was not declared in this scope
scott@scott-laptop:~/Desktop/amuc-1.5$ 

```
i tried to install alsa with apt-get but it said i already had the upgraded version.

any ideas?

---

