---
title: "[SOLVED] Java problems after upgrade"
date: 2008-06-02
forum: General Help
---

### Post by otree013 on 2008-06-02
Hi,
I upgraded from Ubuntu 7.10 to 8.04 tonight, but now I can't run Matlab or Photran (Eclipse) which is a pretty big issue for me. I think it is a Java issue, here is the output trying to run Matlab:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5aad767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb5aad8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb5e191bd]
#3 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d9576e]
#4 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d3b6e6]
#5 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d3b92d]
#6 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1d3bb38]
#7 [0xae27eb8b]
#8 [0xae278a7b]
#9 [0xae278a7b]
#10 [0xae276157]
#11 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f308ec]
#12 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb301f378]
#13 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f3071f]
#14 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb2f88ebb]
#15 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb35232cd]
#16 [0xae27e43b]
#17 [0xae2789a4]
#18 [0xae276157]
#19 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f308ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5aad767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb5aad81e]
#2 /usr/lib/libX11.so.6 [0xb5e18518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb5e0f0a6]
#4 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d3a573]
#5 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d3a804]
#6 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d3ba74]
#7 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1d3bb38]
#8 [0xae27eb8b]
#9 [0xae278a7b]
#10 [0xae278a7b]
#11 [0xae276157]
#12 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f308ec]
#13 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb301f378]
#14 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f3071f]
#15 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb2f88ebb]
#16 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb35232cd]
#17 [0xae27e43b]
#18 [0xae2789a4]
#19 [0xae276157]
Killed

Photran/Eclipse starts to work, then crashes. Trying to switch to Java 1.5 it worked once but has crashed continously since.

Any help would be much appreciated.

Thanks

---

### Post by jamesstansell on 2008-06-02
There have been a number of sun-java bug reports [https://bugs.launchpad.net/ubuntu/+source/sun-java6](https://bugs.launchpad.net/ubuntu/+source/sun-java6) talking about eclipse.  Some of the entries are from people who say they've found a work-around.

(It's too bad that the eclipse devs are mostly on either Windows or Mac., and that the Sun devs mostly don't use Eclipse.)

---

### Post by scouser73 on 2008-06-02
Hi,

When I installed Ubuntu 8.4, I came across an issue with Java, the Java that is included in 8.4 is called 'Open Java'.  What I did was to remove 'Open Java' and install the Sun Microsystems version of Java.

In the Synaptic Package Manager, type Java in the search box, scroll through the results and select 'Sun-Java6-Jre', this should correct the problem with Java.

Alternatively, you can just install 'Sun-Java6-Jre' without removing 'Open Java'.

---

### Post by jamesstansell on 2008-06-03
> **scouser73 said:**
> ... the Java that is included in 8.4 is called 'Open Java'.  What I did was to remove 'Open Java' and install the Sun Microsystems version of Java.


I'm glad you were able to get Java working for you.  I know that the 'Open Java' works for many people, so it's too bad that there are also many for whom it doesn't work.

If you review the output posted by otree013 you can see that he already has Sun's java, so the problem here is something else.

---

### Post by jamesstansell on 2008-06-03
> **otree013 said:**
> Hi,
I upgraded from Ubuntu 7.10 to 8.04 tonight, but now I can't run Matlab or Photran (Eclipse) which is a pretty big issue for me. I think it is a Java issue, here is the output trying to run Matlab:

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5aad767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb5aad8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb5e191bd]
#3 /home/oliver/MatLab/sys/java/jre/glnx86/jre1.5.0/lib/i386/motif21/libmawt.so [0xa1d9576e]

In general, Java on Linux shouldn't be calling the motif libs anymore.  Does MatLab include Motif?  Do you know if you have it installed?

The error message reported appears to point to the xcb locking bug.  I thought the xcb libs shipped by 8.04 were reverted (from the beta) back to the 7.10 behavior, though, so the assertion shouldn't be fatal.  That's why I would check out the motif angle first.

---

### Post by otree013 on 2008-06-04
Hi all, thanks for your replies. After googling around last night I came across [https://answers.launchpad.net/ubuntu/+question/26562](https://answers.launchpad.net/ubuntu/+question/26562) and after playing around with the suggested fixes I managed to get it working.The same or similar issue is also covered here: [http://ubuntuforums.org/showthread.php?t=467133](http://ubuntuforums.org/showthread.php?t=467133). The basic idea is adding something like:

export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/ 

in $matlab_root/bin/matlab (the links above give some variations in approach).

Thanks again :)

---

### Post by Executor89 on 2008-08-12
> **jamesstansell said:**
> There have been a number of sun-java bug reports [https://bugs.launchpad.net/ubuntu/+source/sun-java6](https://bugs.launchpad.net/ubuntu/+source/sun-java6) talking about eclipse.  Some of the entries are from people who say they've found a work-around.

(It's too bad that the eclipse devs are mostly on either Windows or Mac., and that the Sun devs mostly don't use Eclipse.)

It is a shame indeed. There are two "hacks" ( sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so OR export LIBXCB_ALLOW_SLOPPY_LOCK=1 [[source]("https://bugs.launchpad.net/xorg-server/+bug/185311")]), but these don't solve... anything :(.

But here is the REAL question - in the Backtrace log it spits an error message similar to: "/usr/java/jdk1.6.0_03/...", but I have "/usr/java/jdk1.6.0.6/" or something... Does anybody think this is another problem?

---

