---
title: "build error on simon listens 0.4.0"
date: 2013-03-08
forum: General Help
---

### Post by r3xu5 on 2013-03-08
Hi everyone/anyone, I've recently migrated from ubuntu to kubuntu  precise. Main reason being that after many fails trying to build simon  listens 
version 0.4.0 on gnome, I thought it would be simpler on kde. :roll: I get the 0.3.0 version working ok but after days of trying I just cant get the new version to build. ](*,)  I've got all the dependencies built (i think), I get this error at 21% of build when running the build_ubuntu.sh:

simon-0.4.0/build/simonlib/simonvision/../../../simonlib/simonvision/imageanalyzer.h:22:16:  fatal error: cv.h: No such file or directory
compilation terminated.
make[2]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/simonvision_automoc.cpp.o] Error 1
make[1]: *** [simonlib/simonvision/CMakeFiles/simonvision.dir/all] Error 2
make: *** [all] Error 2

Cant find any documentation on this problem, any ideas? Please help!!!!
Greatful for any assistance

---

### Post by r3xu5 on 2013-03-08
anyone? im at a complete standstill, please help

---

### Post by GJJ on 2013-03-16
> **r3xu5 said:**
> anyone? im at a complete standstill, please help


Try installing libcv-dev, that fixed the error for me on Xubuntu.

---

