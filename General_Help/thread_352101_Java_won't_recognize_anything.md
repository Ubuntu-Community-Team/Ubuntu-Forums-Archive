---
title: "Java won't recognize anything"
date: 2007-02-02
forum: General Help
---

### Post by SZF2001 on 2007-02-02
So my brother is trying to play some Java based games, right. They require both the mouse and keyboard inputs, and I'm using Opera (since it won't crash as much as Firefox, even though it would be nice to use Firefox)

Just recently, it's suddenly decided to only accept input from the mouse. He cannot use the keyboard. And then this file called 'hs.err.pid16965.log' showed up in my /home folder suddenly...

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb59f7d19, pid=16965, tid=3070539456
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libnpp.so+0xbd19]  _ZN13pluginWrapperD1Ev+0x51
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x09abf400):  JavaThread "main" [_thread_in_native, id=16965]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x00000028

Registers:
EAX=0x00000010, EBX=0xb5a02170, ECX=0x00000000, EDX=0x0ad72eb0
ESP=0xbfe0ea40, EBP=0xbfe0ea58, ESI=0x09b949a0, EDI=0x096bfb30
EIP=0xb59f7d19, CR2=0x00000028, EFLAGS=0x00210202

Top of Stack: (sp=0xbfe0ea40)
0xbfe0ea40:   0000001f 00000001 bfe0ea58 b5a02170
0xbfe0ea50:   00000010 b5a02170 bfe0ea98 b59f7654
0xbfe0ea60:   096bfb30 0a22d0a0 0000cfb7 00000000
0xbfe0ea70:   09d3abf0 0af6f7f0 00e0ea88 081eb14d
0xbfe0ea80:   096bfb30 096bfb30 bfe0ea98 b5a02170
0xbfe0ea90:   09b949a0 0af6f7f0 bfe0eae8 b59f5369
0xbfe0eaa0:   b5a024d4 0a8981ae 00000000 0a898190
0xbfe0eab0:   09d3abf0 0af6f7f0 bfe0eac8 081eb14d 

Instructions: (pc=0xb59f7d19)
0xb59f7d09:   f8 8b 40 18 89 45 f8 83 7d f8 00 74 0b 8b 45 f8
0xb59f7d19:   8b 40 18 3b 45 08 75 e6 8b 45 f8 3b 45 08 75 0c 

Stack: [0xbfdc0000,0xbfe10000),  sp=0xbfe0ea40,  free space=314k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libnpp.so+0xbd19]  _ZN13pluginWrapperD1Ev+0x51
C  [libnpp.so+0xb654]  _ZN10pluginList16getPluginWrapperEPKc+0x1a8
C  [libnpp.so+0x9369]  _ZN14pluginInstance7NPP_NewEPcP4_NPPtsPS0_S3_P12_NPSavedData+0xd1
C  [opera+0x2227ca]
C  [opera+0x222d76]
C  [opera+0x130c57]
C  [opera+0x12fccd]
C  [opera+0x13007b]
C  [opera+0x131885]
C  [opera+0x5c32d2]
C  [opera+0x5c3466]
C  [opera+0x7c6718]
C  [libqt-mt.so.3+0x307051]  _ZN7QObject15activate_signalEP15QConnectionListP8QUObject+0x12f
C  [libqt-mt.so.3+0x307aec]  _ZN7QObject15activate_signalEi+0x160
C  [libqt-mt.so.3+0x69c536]  _ZN6QTimer7timeoutEv+0x2e
C  [libqt-mt.so.3+0x32c049]  _ZN6QTimer5eventEP6QEvent+0x53
C  [libqt-mt.so.3+0x29cf3e]  _ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0x272
C  [libqt-mt.so.3+0x29d13a]  _ZN12QApplication6notifyEP7QObjectP6QEvent+0x1e2
C  [libqt-mt.so.3+0x22e157]  _ZN12QApplication9sendEventEP7QObjectP6QEvent+0x55
C  [libqt-mt.so.3+0x28e92b]  _ZN10QEventLoop14activateTimersEv+0x207
C  [libqt-mt.so.3+0x241f67]  _ZN10QEventLoop13processEventsEj+0xb8d
C  [libqt-mt.so.3+0x2b5a2f]  _ZN10QEventLoop9enterLoopEv+0x63
C  [libqt-mt.so.3+0x2b5952]  _ZN10QEventLoop4execEv+0x32
C  [libqt-mt.so.3+0x29ba4d]  _ZN12QApplication4execEv+0x25
C  [opera+0x5c30a3]
C  [opera+0x1bb9e]
C  [opera+0x16c24]  _ZN6QFrame10paintEventEP11QPaintEvent+0x180
C  [libc.so.6+0x14ea2]  __libc_start_main+0xd2


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0a114400 JavaThread "Java Sound Event Dispatcher" daemon [_thread_blocked, id=17105]
  0x09e59000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=17077]
  0x0a3b2000 JavaThread "AWT-Shutdown" [_thread_blocked, id=17076]
  0x0a36a800 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=17075]
  0x0a37d400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=17074]
  0x098a8000 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=17072]
  0x098a6800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=17071]
  0x0964ac00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=17070]
  0x0963d400 JavaThread "Finalizer" daemon [_thread_blocked, id=17069]
  0x0a0c4000 JavaThread "Reference Handler" daemon [_thread_blocked, id=17068]
=>0x09abf400 JavaThread "main" [_thread_in_native, id=16965]

Other Threads:
  0x0a0c2400 VMThread [id=17067]
  0x098a9800 WatcherThread [id=17073]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 2432K, used 381K [0xa9010000, 0xa92b0000, 0xa94f0000)
  eden space 2176K,   5% used [0xa9010000, 0xa902f758, 0xa9230000)
  from space 256K, 100% used [0xa9230000, 0xa9270000, 0xa9270000)
  to   space 256K,   0% used [0xa9270000, 0xa9270000, 0xa92b0000)
 tenured generation   total 31692K, used 11753K [0xa94f0000, 0xab3e3000, 0xad010000)
   the space 31692K,  37% used [0xa94f0000, 0xaa06a418, 0xaa06a600, 0xab3e3000)
 compacting perm gen  total 14336K, used 12229K [0xad010000, 0xade10000, 0xb1010000)
   the space 14336K,  85% used [0xad010000, 0xadc01580, 0xadc01600, 0xade10000)
No shared spaces configured.

Dynamic libraries:
06000000-06412000 r-xp 00000000 03:01 11681976   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
06412000-0642b000 rw-p 00411000 03:01 11681976   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client/libjvm.so
0642b000-0684a000 rw-p 0642b000 00:00 0 
08048000-089d6000 r-xp 00000000 03:01 11534493   /usr/lib/opera/9.10-20061214.6/opera
089d6000-08a2a000 rw-p 0098e000 03:01 11534493   /usr/lib/opera/9.10-20061214.6/opera
08a2a000-0d785000 rw-p 08a2a000 00:00 0          [heap]
907df000-907e0000 ---p 907df000 00:00 0 
907e0000-90fe0000 rwxp 907e0000 00:00 0 
917e1000-917e2000 ---p 917e1000 00:00 0 
917e2000-91fe2000 rwxp 917e2000 00:00 0 
92fe4000-92fe5000 ---p 92fe4000 00:00 0 
92fe5000-937e5000 rwxp 92fe5000 00:00 0 
937e5000-937e6000 ---p 937e5000 00:00 0 
937e6000-93fe6000 rwxp 937e6000 00:00 0 
93fe6000-93fe7000 ---p 93fe6000 00:00 0 
93fe7000-947e7000 rwxp 93fe7000 00:00 0 
947e7000-947e8000 ---p 947e7000 00:00 0 
947e8000-94fe8000 rwxp 947e8000 00:00 0 
94fe8000-94fe9000 ---p 94fe8000 00:00 0 
94fe9000-957e9000 rwxp 94fe9000 00:00 0 
957e9000-957ea000 ---p 957e9000 00:00 0 
957ea000-95fea000 rwxp 957ea000 00:00 0 
95fea000-95feb000 ---p 95fea000 00:00 0 
95feb000-967eb000 rwxp 95feb000 00:00 0 
967eb000-967ec000 ---p 967eb000 00:00 0 
967ec000-96fec000 rwxp 967ec000 00:00 0 
96fec000-96fed000 ---p 96fec000 00:00 0 
96fed000-977ed000 rwxp 96fed000 00:00 0 
977ed000-977ee000 ---p 977ed000 00:00 0 
977ee000-97fee000 rwxp 977ee000 00:00 0 
97fee000-97fef000 ---p 97fee000 00:00 0 
97fef000-987ef000 rwxp 97fef000 00:00 0 
987ef000-987f0000 ---p 987ef000 00:00 0 
987f0000-98ff0000 rwxp 987f0000 00:00 0 
98ff0000-98ff1000 ---p 98ff0000 00:00 0 
98ff1000-997f1000 rwxp 98ff1000 00:00 0 
997f1000-997f2000 ---p 997f1000 00:00 0 
997f2000-99ff2000 rwxp 997f2000 00:00 0 
99ff2000-99ff3000 ---p 99ff2000 00:00 0 
99ff3000-9a7f3000 rwxp 99ff3000 00:00 0 
9a7f3000-9a7f4000 ---p 9a7f3000 00:00 0 
9a7f4000-9aff4000 rwxp 9a7f4000 00:00 0 
9aff4000-9aff5000 ---p 9aff4000 00:00 0 
9aff5000-9b7f5000 rwxp 9aff5000 00:00 0 
9b7f5000-9b7f6000 ---p 9b7f5000 00:00 0 
9b7f6000-9bff6000 rwxp 9b7f6000 00:00 0 
9bff6000-9bff7000 ---p 9bff6000 00:00 0 
9bff7000-9c7f7000 rwxp 9bff7000 00:00 0 
9c7f7000-9c7f8000 ---p 9c7f7000 00:00 0 
9c7f8000-9cff8000 rwxp 9c7f8000 00:00 0 
9cff8000-9cff9000 ---p 9cff8000 00:00 0 
9cff9000-9d7f9000 rwxp 9cff9000 00:00 0 
9d7f9000-9d7fa000 ---p 9d7f9000 00:00 0 
9d7fa000-9dffa000 rwxp 9d7fa000 00:00 0 
9dffa000-9dffb000 ---p 9dffa000 00:00 0 
9dffb000-9e7fb000 rwxp 9dffb000 00:00 0 
9e7fb000-9e7fc000 ---p 9e7fb000 00:00 0 
9e7fc000-9effc000 rwxp 9e7fc000 00:00 0 
9effc000-9effd000 ---p 9effc000 00:00 0 
9effd000-9f7fd000 rwxp 9effd000 00:00 0 
9f7fd000-9f7fe000 ---p 9f7fd000 00:00 0 
9f7fe000-9fffe000 rwxp 9f7fe000 00:00 0 
9fffe000-9ffff000 ---p 9fffe000 00:00 0 
9ffff000-a07ff000 rwxp 9ffff000 00:00 0 
a07ff000-a0800000 ---p a07ff000 00:00 0 
a0800000-a1000000 rwxp a0800000 00:00 0 
a1000000-a1001000 ---p a1000000 00:00 0 
a1001000-a1801000 rwxp a1001000 00:00 0 
a1801000-a1802000 ---p a1801000 00:00 0 
a1802000-a2002000 rwxp a1802000 00:00 0 
a2002000-a2003000 ---p a2002000 00:00 0 
a2003000-a2803000 rwxp a2003000 00:00 0 
a2803000-a2804000 ---p a2803000 00:00 0 
a2804000-a3004000 rwxp a2804000 00:00 0 
a3004000-a3005000 ---p a3004000 00:00 0 
a3005000-a3805000 rwxp a3005000 00:00 0 
a3805000-a3806000 ---p a3805000 00:00 0 
a3806000-a4006000 rwxp a3806000 00:00 0 
a4006000-a4007000 ---p a4006000 00:00 0 
a4007000-a4807000 rwxp a4007000 00:00 0 
a4807000-a4808000 ---p a4807000 00:00 0 
a4808000-a5008000 rwxp a4808000 00:00 0 
a5008000-a5009000 ---p a5008000 00:00 0 
a5009000-a5809000 rwxp a5009000 00:00 0 
a5809000-a580a000 ---p a5809000 00:00 0 
a580a000-a600a000 rwxp a580a000 00:00 0 
a600a000-a600b000 ---p a600a000 00:00 0 
a600b000-a680b000 rwxp a600b000 00:00 0 
a680b000-a680c000 ---p a680b000 00:00 0 
a680c000-a700c000 rwxp a680c000 00:00 0 
a700c000-a700d000 ---p a700c000 00:00 0 
a700d000-a780d000 rwxp a700d000 00:00 0 
a780d000-a780e000 ---p a780d000 00:00 0 
a780e000-a800e000 rwxp a780e000 00:00 0 
a800e000-a800f000 ---p a800e000 00:00 0 
a800f000-a880f000 rwxp a800f000 00:00 0 
a880f000-a8810000 ---p a880f000 00:00 0 
a8810000-a92b0000 rwxp a8810000 00:00 0 
a92b0000-a94f0000 rwxp a92b0000 00:00 0 
a94f0000-ab3e3000 rwxp a94f0000 00:00 0 
ab3e3000-ad010000 rwxp ab3e3000 00:00 0 
ad010000-ade10000 rwxp ad010000 00:00 0 
ade10000-b1010000 rwxp ade10000 00:00 0 
b1018000-b12e0000 rwxp b1018000 00:00 0 
b12e0000-b3018000 rwxp b12e0000 00:00 0 
b31a3000-b31a4000 ---p b31a3000 00:00 0 
b31a4000-b39a4000 rwxp b31a4000 00:00 0 
b39e8000-b39e9000 ---p b39e8000 00:00 0 
b39e9000-b41e9000 rwxp b39e9000 00:00 0 
b41e9000-b41ea000 ---p b41e9000 00:00 0 
b41ea000-b49ea000 rwxp b41ea000 00:00 0 
b49ea000-b49eb000 ---p b49ea000 00:00 0 
b49eb000-b51eb000 rwxp b49eb000 00:00 0 
b5750000-b577e000 r-xp 00000000 03:01 11682009   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjpeg.so
b577e000-b577f000 rw-p 0002e000 03:01 11682009   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjpeg.so
b57d0000-b57d3000 ---p b57d0000 00:00 0 
b57d3000-b5821000 rwxp b57d3000 00:00 0 
b5821000-b58d1000 r-xp 00000000 03:01 10798886   /usr/lib/libasound.so.2.0.0
b58d1000-b58d6000 rw-p 000af000 03:01 10798886   /usr/lib/libasound.so.2.0.0
b58e2000-b58e3000 rw-p b58e2000 00:00 0 
b58e3000-b58f1000 r-xp 00000000 03:01 11681994   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjsoundalsa.so
b58f1000-b58f2000 rw-p 0000e000 03:01 11681994   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjsoundalsa.so
b58f2000-b5920000 r-xp 00000000 03:01 11681993   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjsound.so
b5920000-b5921000 rw-p 0002e000 03:01 11681993   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjsound.so
b5921000-b5922000 rw-p b5921000 00:00 0 
b59c4000-b59dd000 r-xp 00000000 03:01 11682016   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libunpack.so
b59dd000-b59e1000 rw-p 00018000 03:01 11682016   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libunpack.so
b59e1000-b59e5000 rw-p b59e1000 00:00 0 
b59e5000-b59ec000 r--s 00106000 03:01 11682033   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/resources.jar
b59ec000-b5a01000 r-xp 00000000 03:01 11550724   /usr/lib/opera/plugins/libnpp.so
b5a01000-b5a03000 rw-p 00015000 03:01 11550724   /usr/lib/opera/plugins/libnpp.so
b5aff000-b5b12000 r-xp 00000000 03:01 11681989   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libnet.so
b5b12000-b5b13000 rw-p 00013000 03:01 11681989   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libnet.so
b5b13000-b5b16000 ---p b5b13000 00:00 0 
b5b16000-b5b64000 rwxp b5b16000 00:00 0 
b5b64000-b5b67000 ---p b5b64000 00:00 0 
b5b67000-b5bb5000 rwxp b5b67000 00:00 0 
b5bb5000-b5bb8000 ---p b5bb5000 00:00 0 
b5bb8000-b5c06000 rwxp b5bb8000 00:00 0 
b5c06000-b5c09000 ---p b5c06000 00:00 0 
b5c09000-b5c57000 rwxp b5c09000 00:00 0 
b5c57000-b5cd5000 r-xp 00000000 03:01 11682008   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libfontmanager.so
b5cd5000-b5cdf000 rw-p 0007e000 03:01 11682008   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libfontmanager.so
b5cdf000-b5ce4000 rw-p b5cdf000 00:00 0 
b5ce4000-b5d22000 r-xp 00000000 03:01 11682003   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so
b5d22000-b5d25000 rw-p 0003d000 03:01 11682003   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/xawt/libmawt.so
b5d25000-b5d26000 ---p b5d25000 00:00 0 
b5d26000-b5da6000 rwxp b5d26000 00:00 0 
b5da6000-b5da9000 ---p b5da6000 00:00 0 
b5da9000-b5df7000 rwxp b5da9000 00:00 0 
b5df7000-b5dfa000 ---p b5df7000 00:00 0 
b5dfa000-b5e78000 rwxp b5dfa000 00:00 0 
b5e78000-b5e7b000 ---p b5e78000 00:00 0 
b5e7b000-b5ec9000 rwxp b5e7b000 00:00 0 
b5ec9000-b5ecc000 ---p b5ec9000 00:00 0 
b5ecc000-b5f1a000 rwxp b5ecc000 00:00 0 
b5f1a000-b5f1d000 ---p b5f1a000 00:00 0 
b5f1d000-b5f6b000 rwxp b5f1d000 00:00 0 
b5f6b000-b5f6c000 ---p b5f6b000 00:00 0 
b5f6c000-b5fec000 rwxp b5f6c000 00:00 0 
b5fec000-b6166000 r--s 02c68000 03:01 11682143   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/rt.jar
b6166000-b616e000 rwxp b6166000 00:00 0 
b616e000-b6187000 rwxp b616e000 00:00 0 
b6187000-b6197000 rwxp b6187000 00:00 0 
b6197000-b61a5000 rwxp b6197000 00:00 0 
b61a5000-b61a7000 rwxp b61a5000 00:00 0 
b61a7000-b61b7000 rwxp b61a7000 00:00 0 
b61b7000-b61c5000 rwxp b61b7000 00:00 0 
b61c5000-b61cc000 rwxp b61c5000 00:00 0 
b61cc000-b61e5000 rwxp b61cc000 00:00 0 
b61e5000-b61f2000 rwxp b61e5000 00:00 0 
b61f2000-b6266000 rwxp b61f2000 00:00 0 
b62b1000-b62b5000 r-xp 00000000 03:01 10803429   /usr/lib/libXtst.so.6.1.0
b62b5000-b62b6000 rw-p 00003000 03:01 10803429   /usr/lib/libXtst.so.6.1.0
b62bb000-b62c2000 r-xp 00000000 03:01 11681990   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libnio.so
b62c2000-b62c3000 rw-p 00006000 03:01 11681990   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libnio.so
b62c3000-b62cc000 r--s 000c7000 03:01 11682144   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/plugin.jar
b62cc000-b62db000 r-xp 00000000 03:01 11681985   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libzip.so
b62db000-b62dd000 rw-p 0000e000 03:01 11681985   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libzip.so
b62dd000-b62e5000 rw-s 00000000 03:01 9338901    /tmp/hsperfdata_coleman/16965
b62e5000-b62ec000 r-xp 00000000 03:01 7143463    /lib/tls/i686/cmov/librt-2.3.6.so
b62ec000-b62ed000 rw-p 00006000 03:01 7143463    /lib/tls/i686/cmov/librt-2.3.6.so
b62ef000-b62f0000 rw-p b62ef000 00:00 0 
b62f0000-b62f1000 r--s 00004000 03:01 9338979    /tmp/jar_cache48380.tmp (deleted)
b62f1000-b62f3000 r--s 00010000 03:01 11534432   /usr/share/opera/java/opera.jar
b62f3000-b62f9000 r-xp 00000000 03:01 11681970   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/native_threads/libhpi.so
b62f9000-b62fa000 rw-p 00006000 03:01 11681970   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/native_threads/libhpi.so
b62fa000-b62fb000 rw-p b62fa000 00:00 0 
b62fb000-b6301000 r-xp 00000000 03:01 10806969   /usr/lib/libnss_mdns.so.2
b6301000-b6302000 rw-p 00005000 03:01 10806969   /usr/lib/libnss_mdns.so.2
b6302000-b6312000 r-xp 00000000 03:01 7143462    /lib/tls/i686/cmov/libresolv-2.3.6.so
b6312000-b6313000 rw-p 00010000 03:01 7143462    /lib/tls/i686/cmov/libresolv-2.3.6.so
b6313000-b6315000 rw-p b6313000 00:00 0 
b66e7000-b6739000 r--p 00000000 03:01 9338946    /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf
b67d4000-b67ef000 r--s 00000000 00:07 467501304  /SYSV00000000 (deleted)
b67ef000-b680a000 r--s 00000000 00:07 467468535  /SYSV00000000 (deleted)
b680a000-b6825000 r--s 00000000 00:07 466944237  /SYSV00000000 (deleted)
b6864000-b687f000 r--s 00000000 00:07 466845930  /SYSV00000000 (deleted)
b689a000-b68b5000 r--s 00000000 00:07 466747623  /SYSV00000000 (deleted)
b68b5000-b68d0000 r--s 00000000 00:07 466714854  /SYSV00000000 (deleted)
b68d0000-b68eb000 r--s 00000000 00:07 466682085  /SYSV00000000 (deleted)
b68eb000-b6906000 r--s 00000000 00:07 466616547  /SYSV00000000 (deleted)
b6915000-b6938000 r--p 00000000 03:01 9338951    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf
b6938000-b6957000 r--p 00000000 03:01 9338920    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b6957000-b6979000 rw-s 00000000 00:07 465010757  /SYSV00000000 (deleted)
b6980000-b699b000 r--s 00000000 00:07 466780392  /SYSV00000000 (deleted)
b69a5000-b69c0000 r--s 00000000 00:07 466944237  /SYSV00000000 (deleted)
b69c0000-b69db000 r--s 00000000 00:07 467304688  /SYSV00000000 (deleted)
b69db000-b69f6000 r--s 00000000 00:07 466911468  /SYSV00000000 (deleted)
b69f6000-b6a11000 r--s 00000000 00:07 466878699  /SYSV00000000 (deleted)
b6a11000-b6a2c000 r--s 00000000 00:07 466583778  /SYSV00000000 (deleted)
b6a31000-b6a4c000 r--s 00000000 00:07 467271908  /SYSV00000000 (deleted)
b6a4f000-b6a72000 r--p 00000000 03:01 9338954    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b6a98000-b6ab7000 r--p 00000000 03:01 9338949    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
b6ab7000-b6ad9000 r--p 00000000 03:01 9338922    /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
b6ad9000-b6ada000 rw-p b6ad9000 00:00 0 
b6ae0000-b6ae1000 rw-p b6ae0000 00:00 0 
b6ae6000-b6aec000 rw-p b6ae6000 00:00 0 
b6aed000-b6aee000 rw-p b6aed000 00:00 0 
b6aef000-b6af0000 rw-p b6aef000 00:00 0 
b6af2000-b6af5000 rw-p b6af2000 00:00 0 
b6af9000-b6aff000 rw-p b6af9000 00:00 0 
b6b00000-b6b01000 rw-p b6b00000 00:00 0 
b6b02000-b6b03000 rw-p b6b02000 00:00 0 
b6b05000-b6b06000 rw-p b6b05000 00:00 0 
b6b08000-b6b12000 rw-p b6b08000 00:00 0 
b6b12000-b6b16000 rw-p b6b12000 00:00 0 
b6b16000-b6b1f000 r-xp 00000000 03:01 7143456    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b6b1f000-b6b20000 rw-p 00008000 03:01 7143456    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b6b20000-b6b28000 r-xp 00000000 03:01 7143458    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b6b28000-b6b29000 rw-p 00007000 03:01 7143458    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b6b29000-b6b31000 r-xp 00000000 03:01 7143454    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b6b31000-b6b32000 rw-p 00007000 03:01 7143454    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b6b32000-b6b33000 rwxp b6b32000 00:00 0 
b6b33000-b6b3f000 rw-p b6b33000 00:00 0 
b6b3f000-b6b4a000 r-xp 00000000 03:01 11534402   /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6b4a000-b6b4b000 rw-p 0000a000 03:01 11534402   /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6b4b000-b6b6f000 r-xp 00000000 03:01 11534401   /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6b6f000-b6b70000 rw-p 00024000 03:01 11534401   /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6b70000-b6b79000 r-xp 00000000 03:01 11534399   /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6b79000-b6b7a000 rw-p 00008000 03:01 11534399   /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6b7a000-b6bc0000 r--p 00000000 03:01 9338936    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b6bc0000-b6e32000 rw-p b6bc0000 00:00 0 
b6e32000-b6edf000 r-xp 00000000 03:01 10802763   /usr/lib/libaspell.so.15.1.4
b6edf000-b6ee3000 rw-p 000ad000 03:01 10802763   /usr/lib/libaspell.so.15.1.4
b6ee3000-b6ee8000 rw-p b6ee3000 00:00 0 
b6ee8000-b6eec000 r-xp 00000000 03:01 7143455    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b6eec000-b6eed000 rw-p 00003000 03:01 7143455    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b6eed000-b6ef1000 r-xp 00000000 03:01 11534400   /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6ef1000-b6ef2000 rw-p 00003000 03:01 11534400   /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6ef2000-b6ef4000 rw-p b6ef2000 00:00 0 
b6ef4000-b6ef8000 r-xp 00000000 03:01 11534494   /usr/lib/opera/9.10-20061214.6/spellcheck.so
b6ef8000-b6ef9000 rw-p 00004000 03:01 11534494   /usr/lib/opera/9.10-20061214.6/spellcheck.so
b6ef9000-b6efb000 rw-p b6ef9000 00:00 0 
b6efb000-b6f3f000 r--p 00000000 03:01 9338938    /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b6f3f000-b6f40000 r-xp 00000000 03:01 11534496   /usr/lib/opera/9.10-20061214.6/missingsyms.so
b6f40000-b6f41000 rw-p 00000000 03:01 11534496   /usr/lib/opera/9.10-20061214.6/missingsyms.so
b6f41000-b6f74000 r--p 00000000 03:01 10830816   /usr/lib/locale/en_US.utf8/LC_CTYPE
b6f74000-b704b000 r--p 00000000 03:01 10830819   /usr/lib/locale/en_US.utf8/LC_COLLATE
b704b000-b704d000 rw-p b704b000 00:00 0 
b704d000-b7050000 r-xp 00000000 03:01 10802795   /usr/lib/libXfixes.so.3.0.0
b7050000-b7051000 rw-p 00003000 03:01 10802795   /usr/lib/libXfixes.so.3.0.0
b7051000-b7052000 rw-p b7051000 00:00 0 
b7052000-b706e000 r-xp 00000000 03:01 10802719   /usr/lib/libexpat.so.1.0.0
b706e000-b7071000 rw-p 0001c000 03:01 10802719   /usr/lib/libexpat.so.1.0.0
b7071000-b7083000 r-xp 00000000 03:01 7143453    /lib/tls/i686/cmov/libnsl-2.3.6.so
b7083000-b7084000 rw-p 00012000 03:01 7143453    /lib/tls/i686/cmov/libnsl-2.3.6.so
b7084000-b7086000 rw-p b7084000 00:00 0 
b7086000-b7091000 r-xp 00000000 03:01 11681981   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libverify.so
b7091000-b7092000 rw-p 0000b000 03:01 11681981   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libverify.so
b7092000-b7094000 r-xp 00000000 03:01 10800264   /usr/lib/libXau.so.6.0.0
b7094000-b7095000 rw-p 00001000 03:01 10800264   /usr/lib/libXau.so.6.0.0
b7095000-b709e000 r-xp 00000000 03:01 7143439    /lib/libgcc_s.so.1
b709e000-b709f000 rw-p 00009000 03:01 7143439    /lib/libgcc_s.so.1
b709f000-b70a0000 rw-p b709f000 00:00 0 
b70a0000-b7106000 r-xp 00000000 03:01 10800280   /usr/lib/libfreetype.so.6.3.8
b7106000-b7109000 rw-p 00066000 03:01 10800280   /usr/lib/libfreetype.so.6.3.8
b7109000-b711a000 r-xp 00000000 03:01 10802773   /usr/lib/libXft.so.2.1.2
b711a000-b711b000 rw-p 00010000 03:01 10802773   /usr/lib/libXft.so.2.1.2
b711b000-b711d000 r-xp 00000000 03:01 10802803   /usr/lib/libXinerama.so.1.0.0
b711d000-b711e000 rw-p 00001000 03:01 10802803   /usr/lib/libXinerama.so.1.0.0
b711e000-b7126000 r-xp 00000000 03:01 10802797   /usr/lib/libXcursor.so.1.0.2
b7126000-b7127000 rw-p 00007000 03:01 10802797   /usr/lib/libXcursor.so.1.0.2
b7127000-b7129000 r-xp 00000000 03:01 10802805   /usr/lib/libXrandr.so.2.0.0
b7129000-b712a000 rw-p 00002000 03:01 10802805   /usr/lib/libXrandr.so.2.0.0
b712a000-b7131000 r-xp 00000000 03:01 10802759   /usr/lib/libXrender.so.1.3.0
b7131000-b7132000 rw-p 00006000 03:01 10802759   /usr/lib/libXrender.so.1.3.0
b7132000-b7133000 rw-p b7132000 00:00 0 
b7133000-b713a000 r-xp 00000000 03:01 10802801   /usr/lib/libXi.so.6.0.0
b713a000-b713b000 rw-p 00006000 03:01 10802801   /usr/lib/libXi.so.6.0.0
b713b000-b715d000 r-xp 00000000 03:01 10800290   /usr/lib/libpng12.so.0.1.2.8
b715d000-b715e000 rw-p 00022000 03:01 10800290   /usr/lib/libpng12.so.0.1.2.8
b715e000-b717c000 r-xp 00000000 03:01 10802820   /usr/lib/libjpeg.so.62.0.0
b717c000-b717d000 rw-p 0001d000 03:01 10802820   /usr/lib/libjpeg.so.62.0.0
b717d000-b71c7000 r-xp 00000000 03:01 10802965   /usr/lib/libXt.so.6.0.0
b71c7000-b71cb000 rw-p 00049000 03:01 10802965   /usr/lib/libXt.so.6.0.0
b71cb000-b71de000 r-xp 00000000 03:01 10801106   /usr/lib/libaudio.so.2.3
b71de000-b71df000 rw-p 00013000 03:01 10801106   /usr/lib/libaudio.so.2.3
b71df000-b7207000 r-xp 00000000 03:01 10802755   /usr/lib/libfontconfig.so.1.0.4
b7207000-b720c000 rw-p 00027000 03:01 10802755   /usr/lib/libfontconfig.so.1.0.4
b720c000-b720e000 rw-p b720c000 00:00 0 
b720e000-b7231000 r-xp 00000000 03:01 11681982   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava.so
b7231000-b7233000 rw-p 00023000 03:01 11681982   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libjava.so
b7233000-b72f9000 r-xp 00000000 03:01 11681999   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libmlib_image.so
b72f9000-b72fa000 rw-p 000c5000 03:01 11681999   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libmlib_image.so
b72fa000-b73c5000 r-xp 00000000 03:01 10799199   /usr/lib/libstdc++.so.6.0.7
b73c5000-b73ca000 rw-p 000cb000 03:01 10799199   /usr/lib/libstdc++.so.6.0.7
b73ca000-b73cf000 rw-p b73ca000 00:00 0 
b73cf000-b74f4000 r-xp 00000000 03:01 7143447    /lib/tls/i686/cmov/libc-2.3.6.so
b74f4000-b74fb000 rw-p 00125000 03:01 7143447    /lib/tls/i686/cmov/libc-2.3.6.so
b74fb000-b74fe000 rw-p b74fb000 00:00 0 
b74fe000-b7511000 r-xp 00000000 03:01 10798769   /usr/lib/libz.so.1.2.3
b7511000-b7512000 rw-p 00012000 03:01 10798769   /usr/lib/libz.so.1.2.3
b7512000-b7513000 rw-p b7512000 00:00 0 
b7513000-b7534000 r-xp 00000000 03:01 7143451    /lib/tls/i686/cmov/libm-2.3.6.so
b7534000-b7535000 rw-p 00020000 03:01 7143451    /lib/tls/i686/cmov/libm-2.3.6.so
b7535000-b7537000 r-xp 00000000 03:01 7143450    /lib/tls/i686/cmov/libdl-2.3.6.so
b7537000-b7538000 rw-p 00001000 03:01 7143450    /lib/tls/i686/cmov/libdl-2.3.6.so
b7538000-b7547000 r-xp 00000000 03:01 7143461    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7547000-b7548000 rw-p 0000e000 03:01 7143461    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7548000-b754a000 rw-p b7548000 00:00 0 
b754a000-b755f000 r-xp 00000000 03:01 10802894   /usr/lib/libICE.so.6.3.0
b755f000-b7560000 rw-p 00014000 03:01 10802894   /usr/lib/libICE.so.6.3.0
b7560000-b7562000 rw-p b7560000 00:00 0 
b7562000-b7569000 r-xp 00000000 03:01 10802902   /usr/lib/libSM.so.6.0.0
b7569000-b756a000 rw-p 00007000 03:01 10802902   /usr/lib/libSM.so.6.0.0
b756a000-b7576000 r-xp 00000000 03:01 10802799   /usr/lib/libXext.so.6.4.0
b7576000-b7577000 rw-p 0000c000 03:01 10802799   /usr/lib/libXext.so.6.4.0
b7577000-b7578000 rw-p b7577000 00:00 0 
b7578000-b7659000 r-xp 00000000 03:01 10800266   /usr/lib/libX11.so.6.2.0
b7659000-b765d000 rw-p 000e1000 03:01 10800266   /usr/lib/libX11.so.6.2.0
b765d000-b765e000 rw-p b765d000 00:00 0 
b765e000-b7dfd000 r-xp 00000000 03:01 10801109   /usr/lib/libqt-mt.so.3.3.6
b7dfd000-b7e44000 rw-p 0079e000 03:01 10801109   /usr/lib/libqt-mt.so.3.3.6
b7e44000-b7e47000 rw-p b7e44000 00:00 0 
b7e47000-b7e48000 r--p b7e47000 00:00 0 
b7e48000-b7e4a000 rw-p b7e48000 00:00 0 
b7e4a000-b7e4b000 r--p 00000000 03:01 10830817   /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7e4b000-b7e4c000 r--p 00000000 03:01 10830818   /usr/lib/locale/en_US.utf8/LC_TIME
b7e4c000-b7e4d000 r--p 00000000 03:01 10830820   /usr/lib/locale/en_US.utf8/LC_MONETARY
b7e4d000-b7e4e000 r--p 00000000 03:01 10830822   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7e4e000-b7e4f000 r--p 00000000 03:01 10830823   /usr/lib/locale/en_US.utf8/LC_PAPER
b7e4f000-b7e50000 r--p 00000000 03:01 10830824   /usr/lib/locale/en_US.utf8/LC_NAME
b7e50000-b7e51000 r--p 00000000 03:01 10830825   /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7e51000-b7e52000 r--p 00000000 03:01 10830826   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7e52000-b7e53000 r--p 00000000 03:01 10830827   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7e53000-b7e54000 r--p 00000000 03:01 10830828   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7e54000-b7ecf000 r-xp 00000000 03:01 11682000   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libawt.so
b7ecf000-b7ed6000 rw-p 0007b000 03:01 11682000   /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libawt.so
b7ed6000-b7efd000 rw-p b7ed6000 00:00 0 
b7efd000-b7f12000 r-xp 00000000 03:01 7144837    /lib/ld-2.3.6.so
b7f12000-b7f13000 rw-p 00014000 03:01 7144837    /lib/ld-2.3.6.so
bfdc0000-bfdc3000 ---p bfdc0000 00:00 0 
bfdc3000-bfe10000 rwxp bfdc3000 00:00 0          [stack]
bfe10000-bfe12000 rw-p bfe10000 00:00 0 
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: abort exit -Xbootclasspath/p:/usr/share/opera/java/opera.jar:/usr/share/opera/java/lc.jar:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/plugin.jar -Djava.security.policy=/usr/share/opera/java/opera.policy -Dbrowser.opera.classpath=/usr/share/opera/java/opera.jar:/usr/share/opera/java/lc.jar
java_command: <unknown>
Launcher Type: generic

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=coleman
LD_LIBRARY_PATH=/usr/lib/opera/9.10-20061214.6/:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/native_threads:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/classic
LD_PRELOAD=
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3aea90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3aea90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x304e70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x304e70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x304e70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x306e80], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x3068a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x3068a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x3068a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x3068a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR2: [libjvm.so+0x306e80], sa_mask[0]=0x00000000, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.91 0.30 0.68

CPU:total 1 family 6, cmov, cx8, fxsr, mmx, sse

Memory: 4k page, physical 125412k(1700k free), swap 361420k(40748k free)

vm_info: Java HotSpot(TM) Client VM (1.6.0-b105) for linux-x86, built on Nov 29 2006 01:24:38 by "java_re" with gcc 3.2.1-7a (J2SE release)
```

Using Java 6 and Xubuntu, fyi. I don't know what to do from here...

---

### Post by phossal on 2007-02-02
Are you using beryl?

---

### Post by SZF2001 on 2007-02-03
Nope...

---

### Post by phossal on 2007-02-03
> **SZF2001 said:**
> 
---------------  S Y S T E M  ---------------

**OS:testing/unstable**
uname:Linux 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.91 0.30 0.68
CPU:total 1 family 6, cmov, cx8, fxsr, mmx, sse
Memory: 4k page, physical 125412k(1700k free), swap 361420k(40748k free)
vm_info: Java HotSpot(TM) Client VM (1.6.0-b105) for linux-x86, built on Nov 29 2006 01:24:38 by "java_re" with gcc 3.2.1-7a (J2SE release)[/code]
Using Java 6 and Xubuntu, fyi. I don't know what to do from here...

What's up with that?

---

