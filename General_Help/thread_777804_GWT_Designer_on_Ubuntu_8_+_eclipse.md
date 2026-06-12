---
title: "GWT Designer on Ubuntu 8 + eclipse"
date: 2008-05-01
forum: General Help
---

### Post by nickmicksoares on 2008-05-01
I am facing the problem on Ubuntu 8.

I have installed jdk 5 (Java HotSpot(TM) Server VM (build 1.5.0_15-b04, mixed mode))

When I try to run the application, i get this from the console window in eclipse.

Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x8c101767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0x8c1018b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x8bb211bd]
#3 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c3bdce]
#4 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c25d77]
#5 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c25ef3]
#6 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x86c26136]
#7 [0xb13802bb]
#8 [0xb1377b6b]
#9 [0xb1377b6b]
#10 [0xb1375236]
#11 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7654eac]
#12 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7824aa8]
#13 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7654cdf]
#14 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76b27ed]
#15 /usr/lib/j2sdk1.5-sun/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb732930d]
#16 [0xb137f7fa]
#17 [0xb1377a94]
#18 [0xb1375236]
#19 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7654eac]
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x8c101767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0x8c10181e]
#2 /usr/lib/libX11.so.6 [0x8bb20518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x8bb170a6]
#4 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c250b9]
#5 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c25303]
#6 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so [0x86c25fa1]
#7 /usr/lib/j2sdk1.5-sun/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x86c26136]
#8 [0xb13802bb]
#9 [0xb1377b6b]
#10 [0xb1377b6b]
#11 [0xb1375236]
#12 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7654eac]
#13 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7824aa8]
#14 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so [0xb7654cdf]
#15 /usr/lib/j2sdk1.5-sun/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76b27ed]
#16 /usr/lib/j2sdk1.5-sun/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb732930d]
#17 [0xb137f7fa]
#18 [0xb1377a94]
#19 [0xb1375236]


Besides, the design tab still crashing my eclispe.

This problem is really killing my time!!!!   ](*,) ](*,)  ](*,)  :cry:


HELP Please!!!!

---

