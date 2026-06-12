---
title: "Installing OpenCV 2.2 on Ubuntu 12.04"
date: 2012-11-12
forum: General Help
---

### Post by mirrowwinger on 2012-11-12
Hello Linux-community,

I have some problems to install OpenCV on a Ubuntu 12.04. First why I want to install OpenCV 2.2 instead of the newest (2.4.2?) version? I have a special chip camera (image source dfm 22buc03), which I want to get run. Camera works with mplayer (tested).

In [https://code.ros.org/trac/opencv/ticket/1112](https://code.ros.org/trac/opencv/ticket/1112) there is an guy saying this exactly camera would work in OpenCV 2.2. I tested it with OpenCV 2.4.2 and it fails with the v4l2-driver. If u are intrested i can post the error i got from OpenCV 2.4.2 later.

Ok installing OpenCV 2.2 on Ubuntu 2.2 seems to be a bit tricky. I followed this [http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/](http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/) step by step and got an error when I "make" OpenCV 2.2. At 41 percent I get the following error-message:
```
In file included from /usr/include/tbb/tbb_exception.h:118:0,
                 from /usr/include/tbb/concurrent_vector.h:33,
                 from /usr/include/tbb/enumerable_thread_specific.h:32,
                 from /usr/include/tbb/combinable.h:32,
                 from /usr/include/tbb/tbb.h:46,
                 from /home/theghostwork/Programms/OpenCV-2.2.0/modules/core/include/opencv2/core/internal.hpp:129,
                 from /home/theghostwork/Programms/OpenCV-2.2.0/modules/core/src/precomp.hpp:57,
                 from /home/theghostwork/Programms/OpenCV-2.2.0/modules/core/src/lapack.cpp:43:
/usr/include/c++/4.6/typeinfo:42:37: Fehler: expected »}« before end of line
/usr/include/c++/4.6/typeinfo:42:37: Fehler: expected declaration before end of line
make[2]: *** [modules/core/CMakeFiles/opencv_core.dir/src/lapack.o] Fehler 1
make[1]: *** [modules/core/CMakeFiles/opencv_core.dir/all] Fehler 2
make: *** [all] Fehler 2

```I#m able to program a bit and looked in lapack.cpp and precomp.hpp, but couldn find the place where the "}" is missing.

Hope someone can help me installing OpenCV 2.2 or give me an instruction How to get the Camera working with OpenCV 2.4.2.

Greets

mirrowwinger

---

### Post by HermanAB on 2012-11-12
Howdy,

You need an old Ubuntu version circa 2010 for that.

This may help:
[http://www.aeronetworks.ca/howtos/Fedora-Compile-OpenCV-From-Source.pdf](http://www.aeronetworks.ca/howtos/Fedora-Compile-OpenCV-From-Source.pdf)

---

