---
title: "PyMOL make error - help please"
date: 2012-10-23
forum: General Help
---

### Post by aravindprasad on 2012-10-23
[Please move to a more appropriate section if needed]

I am trying to compile PyMOL using the more traditional configure-make method. I have my reasons for doing this instead of the Python build method. So I would appreciate it a great deal if people did not digress by suggesting that I do that instead or get into discussions about the merits of each method.

configure runs fine with dependency checks. So I am reasonably sure that I have all the requisite libraries installed. When I run make, I get this error

```
Making all in layer1
make[2]: Entering directory `/home/superuser/Downloads/pymol/layer1'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I../ov/src -I../layer0 -I../layer2 -I../layer3 -I../layer4 -I../layer5 -I../contrib/uiuc/plugins/include  -I/usr/include/python2.7     -I/usr/include/freetype2 -g -O2 -MT CGO.lo -MD -MP -MF .deps/CGO.Tpo -c -o CGO.lo CGO.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I../ov/src -I../layer0 -I../layer2 -I../layer3 -I../layer4 -I../layer5 -I../contrib/uiuc/plugins/include -I/usr/include/python2.7 -I/usr/include/freetype2 -g -O2 -MT CGO.lo -MD -MP -MF .deps/CGO.Tpo -c CGO.c  -fPIC -DPIC -o .libs/CGO.o
CGO.c:150:3: error: ‘CGO_DRAW_CYLINDER_BUFFERS_SZ’ undeclared here (not in a function)
CGO.c: In function ‘CGOArrayAsPyList’:
CGO.c:321:12: error: ‘CGO_DRAW_ARRAYS’ undeclared (first use in this function)
CGO.c:321:12: note: each undeclared identifier is reported only once for each function it appears in
CGO.c: In function ‘CGOArrayFromPyListInPlace’:
CGO.c:390:12: error: ‘CGO_DRAW_ARRAYS’ undeclared (first use in this function)
CGO.c: In function ‘CGOLinewidthSpecial’:
CGO.c:719:3: error: ‘CGO_LINEWIDTH_SPECIAL’ undeclared (first use in this function)
CGO.c:719:3: warning: assignment makes integer from pointer without a cast [enabled by default]
CGO.c: In function ‘CGOOptimizeGLSLCylindersToVBOIndexedImpl’:
CGO.c:3820:12: error: ‘CGO’ has no member named ‘normal’
CGO.c:3820:34: error: ‘CGO’ has no member named ‘normal’
CGO.c:3820:62: error: ‘CGO’ has no member named ‘normal’
CGO.c:3823:12: error: ‘CGO’ has no member named ‘color’
CGO.c:3823:33: error: ‘CGO’ has no member named ‘color’
CGO.c:3823:60: error: ‘CGO’ has no member named ‘color’
CGO.c:3850:5: error: ‘CGO’ has no member named ‘color’
CGO.c:3851:5: error: ‘CGO’ has no member named ‘color’
CGO.c:3852:5: error: ‘CGO’ has no member named ‘color’
CGO.c:3890:24: error: ‘CGO’ has no member named ‘color’
CGO.c:3891:24: error: ‘CGO’ has no member named ‘color’
CGO.c:3892:24: error: ‘CGO’ has no member named ‘color’
CGO.c:3901:22: error: ‘CGO’ has no member named ‘color’
CGO.c:3902:22: error: ‘CGO’ has no member named ‘color’
CGO.c:3903:22: error: ‘CGO’ has no member named ‘color’
CGO.c:3947:29: error: ‘CGO’ has no member named ‘color’
CGO.c:3947:45: error: ‘CGO’ has no member named ‘color’
CGO.c:3947:61: error: ‘CGO’ has no member named ‘color’
CGO.c:4037:10: error: ‘CGO’ has no member named ‘has_draw_buffers’
CGO.c:4038:10: error: ‘CGO’ has no member named ‘has_draw_cylinder_buffers’
CGO.c: In function ‘CGOOptimizeSpheresToVBONonIndexed’:
CGO.c:4050:3: warning: return makes pointer from integer without a cast [enabled by default]
CGO.c: At top level:
CGO.c:4053:6: error: conflicting types for ‘CGOOptimizeSpheresToVBONonIndexedImpl’
CGO.c:4050:11: note: previous implicit declaration of ‘CGOOptimizeSpheresToVBONonIndexedImpl’ was here
CGO.c: In function ‘CGOOptimizeSpheresToVBONonIndexedImpl’:
CGO.c:4112:12: error: ‘CGO’ has no member named ‘normal’
CGO.c:4112:34: error: ‘CGO’ has no member named ‘normal’
CGO.c:4112:62: error: ‘CGO’ has no member named ‘normal’
CGO.c:4115:12: error: ‘CGO’ has no member named ‘color’
CGO.c:4115:33: error: ‘CGO’ has no member named ‘color’
CGO.c:4115:60: error: ‘CGO’ has no member named ‘color’
CGO.c:4143:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4143:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4143:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4144:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4144:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4144:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4145:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4145:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4145:23: error: ‘CGO’ has no member named ‘color’
CGO.c:4149:24: error: ‘CGO’ has no member named ‘color’
CGO.c:4150:24: error: ‘CGO’ has no member named ‘color’
CGO.c:4151:24: error: ‘CGO’ has no member named ‘color’
CGO.c:4197:29: error: ‘CGO’ has no member named ‘color’
CGO.c:4197:45: error: ‘CGO’ has no member named ‘color’
CGO.c:4197:61: error: ‘CGO’ has no member named ‘color’
CGO.c:4282:10: error: ‘CGO’ has no member named ‘has_draw_buffers’
CGO.c:4283:10: error: ‘CGO’ has no member named ‘has_draw_sphere_buffers’
CGO.c: In function ‘CGORenderGL’:
CGO.c:6439:5: error: ‘CGO’ has no member named ‘color’
CGO.c:6439:29: error: ‘CGO’ has no member named ‘color’
CGO.c:6439:53: error: ‘CGO’ has no member named ‘color’
CGO.c:6440:10: error: ‘CGO’ has no member named ‘color’
CGO.c:6440:7: warning: assignment from incompatible pointer type [enabled by default]
make[2]: *** [CGO.lo] Error 1
make[2]: Leaving directory `/home/superuser/Downloads/pymol/layer1'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/superuser/Downloads/pymol'
make: *** [all] Error 2
```


If you need to look at other files, here is the download link to PyMOL source - 
[http://sourceforge.net/projects/pymol/files/latest/download](http://sourceforge.net/projects/pymol/files/latest/download)
I am working with v1.5.0.1 which is the latest as of today (2012-10-23).

Thanks for any help.
Regards.

---

### Post by dino99 on 2012-10-23
looks like a header is missing, or the one used is not the required version (thats what errors says)

---

### Post by aravindprasad on 2012-10-24
> **dino99 said:**
> looks like a header is missing, or the one used is not the required version (thats what errors says)

I sat down and went through all the dependencies of CGO.c and its dependencies and found all of them :-(

Any other possibilities? Any chance this is an issue with using a newer version of the compiler?

---

### Post by aravindprasad on 2012-11-01
ping...

---

### Post by aravindprasad on 2012-11-05
ping... help pls...

At least can someone else who is on Ubuntu 12.04 64-bit try compiling the package from the link provided in my post above.

Thanks,
-Aravind

---

