---
title: "Java problem (running JabRef) in Hardy"
date: 2008-02-05
forum: General Help
---

### Post by guano on 2008-02-05
I just upgraded from Gutsy to Hardy, and my JabRef doesn't work anymore (haven't tried other java apps). Anyone experienced something similar?

error msg:

```
guano@eclipse:~$ jabref 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb540a767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb540a8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb51b229d]
#3 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb545c8ce]
#4 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb5439067]
#5 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xb5439318]
#6 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb543961f]
#7 [0xb5c97ecd]
#8 [0xb5c90edd]
#9 [0xb5c90edd]
#10 [0xb5c8e249]
#11 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x6310378]
#13 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c2a0]
#14 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#15 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7ca996d]
#16 [0xb5c97ecd]
#17 [0xb5c90d77]
#18 [0xb5c8e249]
#19 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/client/libjvm.so [0x621c40d]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
Aborted (core dumped)
guano@eclipse:~$ 
```

---

### Post by hugmenot on 2008-02-13
Confirmed. I can start it with the following command:

LIBXCB_ALLOW_SLOPPY_LOCK=true jabref


see here: [https://bugs.launchpad.net/ubuntu/+source/jabref/+bug/86103](https://bugs.launchpad.net/ubuntu/+source/jabref/+bug/86103)

---

### Post by Ares Drake on 2008-02-29
Yeah, thx for your solution. I am running Hardy alpha5 32bit and am affected as well with sun-java-6, but your solution works well for me.

Thx a lot!

---

