---
title: "Installing Qt Designer/Creator causes Maya 2013 crash(Ubuntu 12.04)"
date: 2012-11-24
forum: General Help
---

### Post by raul1st2002 on 2012-11-24
Hi guys, I am new to Qt and want to use it with Maya. But my Maya 2013 always crash during launch after installing Qt Designer/Creator.

I’m using Ubuntu 12.04 and installed Qt Designer/Creator from Ubuntu software center. After installation, the QT version is 4.8.1.

Running Maya 2013 from terminal generate a crash report like this:
//crash log file name     = /usr/tmp/ding.20121124.0833
//cut            = 201209210317 /builds/Maya_2013_Linux_Build/build
//host name      = ding-System-Product-Name
//release name   = 3.2.0-23-generic
//version        = #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012
//machine name   = x86_64
//current scene   =
//directory      = /home/ding
//====================================================
//last tool: renderWindowSelectContextItem
//====================================================
//panel with focus: modelPanel4
//visible panels:
// modelPanel4
//====================================================
  /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7fcc06ef84a0]
  /usr/lib/nvidia-current/libGL.so.1(+0x81b65) [0x7fcc09a9bb65]
 
 
//====================================================
//Memory usage:
// 2147.484 Mb    Free Memory
// 2147.484 Mb    Free Swap
//  126.445 Mb    Heap
//   60.156 Mb    MEL
//    0.135 Mb    arguments
//    0.332 Mb    Data Blocks
//    0.195 Mb    Object Arrays
//    0.125 Mb    Transforms
//    0.062 Mb    Arrays
//====================================================
It seems the problem is related to libc.so.6 and libGL.so.1. But I double checked those two files are not changed during Qt installation.
Maya 2013 relies on Qt 4.7.1. I wonder if there is a version conflict? I’ve tried compile and install Qt library 4.7.1 from source file and that works fine. But installing Qt Designer/Creator always update it to 4.8.1.

Is it possible install an older version Qt Designer without using Ubuntu software center?

Any info would be appreciated! Thank you!

---

