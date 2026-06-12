---
title: "installing ng-spice-rework-15 Error"
date: 2008-06-15
forum: General Help
---

### Post by a.dehqan on 2008-06-15
In the name of god .
hello;

I will be thankfull if you GUIDE me .
When i want to install ng-spice-rework-15 on Debian etch in MAKE stage it gives me these errors :


[left]```
maths/sparse/libsparse.a(spalloc.o): In function `spDestroy':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:663: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:664: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:665: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:666: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:667: undefined reference to `txfree'
maths/sparse/libsparse.a(spalloc.o):/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:668: more undefined references to `txfree' follow
maths/sparse/libsparse.a(spalloc.o): In function `AllocateBlockOfAllocationList':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:600: undefined reference to `tmalloc'
maths/sparse/libsparse.a(spalloc.o): In function `RecordAllocation':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:556: undefined reference to `txfree'
maths/sparse/libsparse.a(spalloc.o): In function `spcGetElement':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:317: undefined reference to `tmalloc'
maths/sparse/libsparse.a(spalloc.o): In function `spCreate':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:152: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:227: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:231: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:243: undefined reference to `tmalloc'
maths/sparse/libsparse.a(spalloc.o):/root/Desktop/ng-spice-rework-15/src/maths/sparse/spalloc.c:247: more undefined references to `tmalloc' follow
maths/sparse/libsparse.a(spbuild.o): In function `EnlargeMatrix':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:980: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:985: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:990: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:995: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1000: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1008: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1009: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1010: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1011: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1012: undefined reference to `txfree'
maths/sparse/libsparse.a(spbuild.o):/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1013: more undefined references to `txfree' follow
maths/sparse/libsparse.a(spbuild.o): In function `ExpandTranslationArrays':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1070: undefined reference to `trealloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spbuild.c:1075: undefined reference to `trealloc'
maths/sparse/libsparse.a(spfactor.o): In function `spcCreateInternalVectors':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:752: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:757: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:762: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:768: undefined reference to `tmalloc'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:772: undefined reference to `tmalloc'
maths/sparse/libsparse.a(spfactor.o):/root/Desktop/ng-spice-rework-15/src/maths/sparse/spfactor.c:778: more undefined references to `tmalloc' follow
maths/sparse/libsparse.a(spoutput.o): In function `spPrint':
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spoutput.c:380: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spoutput.c:177: undefined reference to `txfree'
/root/Desktop/ng-spice-rework-15/src/maths/sparse/spoutput.c:178: undefined reference to `txfree'
collect2: ld returned 1 exit status
make[3]: *** [ngspice] Error 1
make[3]: Leaving directory `/root/Desktop/ng-spice-rework-15/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/Desktop/ng-spice-rework-15/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/Desktop/ng-spice-rework-15'
make: *** [all] Error 2

```[/left]


THANKS

---

