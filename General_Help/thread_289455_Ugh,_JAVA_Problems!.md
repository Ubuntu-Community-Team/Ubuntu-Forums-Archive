---
title: "Ugh, JAVA Problems!"
date: 2006-10-31
forum: General Help
---

### Post by NewWaves on 2006-10-31
Hi all,
I'm having problems with java and a any pjirc chat applet... Here's a debug log:


```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1b10cfd, pid=1287, tid=2971839408
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ecfd]
#

---------------  T H R E A D  ---------------

Current thread (0x082751d0):  JavaThread "AWT-EventQueue-2" [_thread_in_native, id=1324]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x0b6089c4

Registers:
EAX=0x081881c4, EBX=0xb1b5e5a8, ECX=0x081870dc, EDX=0x03480800
ESP=0xb12293ec, EBP=0xb1229414, ESI=0x081881c4, EDI=0x00e2030e
EIP=0xb1b10cfd, CR2=0x0b6089c4, EFLAGS=0x00010212

Top of Stack: (sp=0xb12293ec)
0xb12293ec:   b122945c b122962c b1229494 b783f028
0xb12293fc:   03880c38 00d20200 00000004 b1b5e5a8
0xb122940c:   08184668 0818469c b1229434 b1b16ec6
0xb122941c:   b122945c 00000000 0000000a b2415690
0xb122942c:   b1b62ac0 b7a4538c b1229594 b1b1724e
0xb122943c:   b122945c 0842fec0 0842ff08 0833c73c
0xb122944c:   082751d0 082d89f8 913e9420 b122945c
0xb122945c:   081870dc 081870dc 081870dc 00004000 

Instructions: (pc=0xb1b10cfd)
0xb1b10ced:   8b 4a 08 8b 45 ec 8d 14 85 00 00 00 00 8b 41 04
0xb1b10cfd:   8b 14 10 8b 4d e8 8b 04 0e 29 d0 89 44 24 04 8b 

Stack: [0xb11aa000,0xb122b000),  sp=0xb12293ec,  free space=508k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x2ecfd]
C  [libfontmanager.so+0x34ec6]
C  [libfontmanager.so+0x3524e]
C  [libfontmanager.so+0x3768a]
C  [libfontmanager.so+0x35a92]
C  [libfontmanager.so+0x35faa]
C  [libfontmanager.so+0x225c6]
C  [libfontmanager.so+0x24326]
C  [libfontmanager.so+0x463c6]  Java_sun_font_FileFont_getGlyphImage+0x120
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
J  sun.font.FontDesignMetrics.getLatinCharWidth(C)F
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  irc.gui.pixx.PixxMenuBar.drawItem(Ljava/awt/Graphics;IIZLjava/lang/String;)V+133
j  irc.gui.pixx.PixxMenuBar.drawDisconnectItem(Ljava/awt/Graphics;IIZ)V+12
j  irc.gui.pixx.PixxMenuBar.update(Ljava/awt/Graphics;)V+210
j  sun.awt.RepaintArea.updateComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+6
j  sun.awt.X11.XRepaintArea.updateComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+23
j  sun.awt.RepaintArea.paint(Ljava/lang/Object;Z)V+263
j  sun.awt.X11.XComponentPeer.handleEvent(Ljava/awt/AWTEvent;)V+188
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEvent;)V+765
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEvent;)V+42
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEvent;)V+2
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+46
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x174fec]
V  [libjvm.so+0x2821f8]
V  [libjvm.so+0x174845]
V  [libjvm.so+0x1748de]
V  [libjvm.so+0x1ebee5]
V  [libjvm.so+0x2ea563]
V  [libjvm.so+0x282d08]
C  [libpthread.so.0+0x5341]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
J  sun.font.FontDesignMetrics.getLatinCharWidth(C)F
v  ~RuntimeStub::alignment_frame_return Runtime1 stub
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  irc.gui.pixx.PixxMenuBar.drawItem(Ljava/awt/Graphics;IIZLjava/lang/String;)V+133
j  irc.gui.pixx.PixxMenuBar.drawDisconnectItem(Ljava/awt/Graphics;IIZ)V+12
j  irc.gui.pixx.PixxMenuBar.update(Ljava/awt/Graphics;)V+210
j  sun.awt.RepaintArea.updateComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+6
j  sun.awt.X11.XRepaintArea.updateComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+23
j  sun.awt.RepaintArea.paint(Ljava/lang/Object;Z)V+263
j  sun.awt.X11.XComponentPeer.handleEvent(Ljava/awt/AWTEvent;)V+188
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEvent;)V+765
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEvent;)V+42
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEvent;)V+2
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+46
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0808fd58 JavaThread "Image Fetcher 0" daemon [_thread_blocked, id=1328]
  0x08274240 JavaThread "Read thread" [_thread_in_native, id=1325]
=>0x082751d0 JavaThread "AWT-EventQueue-2" [_thread_in_native, id=1324]
  0x0808e730 JavaThread "Event dispatch thread" daemon [_thread_blocked, id=1323]
  0x08116c38 JavaThread "AWT-EventQueue-1" [_thread_blocked, id=1321]
  0x08090d40 JavaThread "thread applet-IRCApplet.class" [_thread_blocked, id=1309]
  0x0808dbf8 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=1306]
  0x0808c918 JavaThread "AWT-Shutdown" [_thread_blocked, id=1305]
  0x083b7af8 JavaThread "Thread-2" [_thread_in_native, id=1304]
  0x0839add0 JavaThread "Thread-1" [_thread_blocked, id=1301]
  0x083946e8 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=1299]
  0x0837fc58 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=1298]
  0x082f7888 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=1295]
  0x080b5088 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=1293]
  0x080b3b28 JavaThread "CompilerThread0" daemon [_thread_blocked, id=1292]
  0x080b2c08 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=1291]
  0x08096e48 JavaThread "Finalizer" daemon [_thread_blocked, id=1290]
  0x08096148 JavaThread "Reference Handler" daemon [_thread_blocked, id=1289]
  0x08051c80 JavaThread "main" [_thread_in_native, id=1287]

Other Threads:
  0x080935e8 VMThread [id=1288]
  0x080b6528 WatcherThread [id=1294]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 576K, used 199K [0x88aa0000, 0x88b40000, 0x88f80000)
  eden space 512K,  32% used [0x88aa0000, 0x88ac9960, 0x88b20000)
  from space 64K,  51% used [0x88b20000, 0x88b28330, 0x88b30000)
  to   space 64K,   0% used [0x88b30000, 0x88b30000, 0x88b40000)
 tenured generation   total 3692K, used 3604K [0x88f80000, 0x8931b000, 0x8caa0000)
   the space 3692K,  97% used [0x88f80000, 0x893052d0, 0x89305400, 0x8931b000)
 compacting perm gen  total 8192K, used 3555K [0x8caa0000, 0x8d2a0000, 0x90aa0000)
   the space 8192K,  43% used [0x8caa0000, 0x8ce18c48, 0x8ce18e00, 0x8d2a0000)
    ro space 8192K,  68% used [0x90aa0000, 0x9101c408, 0x9101c600, 0x912a0000)
    rw space 12288K,  48% used [0x912a0000, 0x91863a30, 0x91863c00, 0x91ea0000)

Dynamic libraries:
08048000-0804c000 r-xp 00000000 03:01 771780     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java_vm
0804c000-0804d000 rwxp 00003000 03:01 771780     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java_vm
0804d000-08457000 rwxp 0804d000 00:00 0          [heap]
88aa0000-88b40000 rwxp 88aa0000 00:00 0 
88b40000-88f80000 rwxp 88b40000 00:00 0 
88f80000-8931b000 rwxp 88f80000 00:00 0 
8931b000-8caa0000 rwxp 8931b000 00:00 0 
8caa0000-8d2a0000 rwxp 8caa0000 00:00 0 
8d2a0000-90aa0000 rwxp 8d2a0000 00:00 0 
90aa0000-9101d000 r-xs 00001000 03:01 951769     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
9101d000-912a0000 rwxp 9101d000 00:00 0 
912a0000-91864000 rwxp 0057e000 03:01 951769     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
91864000-91ea0000 rwxp 91864000 00:00 0 
91ea0000-91f6f000 rwxp 00b42000 03:01 951769     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
91f6f000-922a0000 rwxp 91f6f000 00:00 0 
922a0000-922a4000 r-xs 00c11000 03:01 951769     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
922a4000-926a0000 rwxp 922a4000 00:00 0 
b0f85000-b0f93000 r-xs 00000000 03:01 786335     /usr/share/X11/fonts/Type1/cursor.pfa
b0f93000-b0f9c000 r-xs 00000000 03:01 786334     /usr/share/X11/fonts/Type1/c0649bt_.pfb
b0f9c000-b0fa5000 r-xs 00000000 03:01 786332     /usr/share/X11/fonts/Type1/c0648bt_.pfb
b0fa5000-b0fae000 r-xs 00000000 03:01 786330     /usr/share/X11/fonts/Type1/c0633bt_.pfb
b0fae000-b0fb7000 r-xs 00000000 03:01 786328     /usr/share/X11/fonts/Type1/c0632bt_.pfb
b0fb7000-b0fc1000 r-xs 00000000 03:01 786326     /usr/share/X11/fonts/Type1/c0611bt_.pfb
b0fdf000-b1002000 r-xs 00000000 03:01 1144709    /home/josh/.java/deployment/cache/javapi/v1.0/jar/pixx.jar-6e51db4b-2eaf5529.zip
b1002000-b10a4000 rwxs 00000000 00:07 37257268   /SYSV00000000 (deleted)
b10a4000-b10a8000 rwxs 00000000 00:07 37224501   /SYSV00000000 (deleted)
b10a8000-b10ab000 ---p b10a8000 00:00 0 
b10ab000-b1129000 rwxp b10ab000 00:00 0 
b1129000-b112c000 ---p b1129000 00:00 0 
b112c000-b11aa000 rwxp b112c000 00:00 0 
b11aa000-b11ad000 ---p b11aa000 00:00 0 
b11ad000-b122b000 rwxp b11ad000 00:00 0 
b122b000-b1325000 rwxs 00000000 00:07 37158963   /SYSV00000000 (deleted)
b1325000-b133d000 r-xp 00000000 03:01 771809     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdcpr.so
b133d000-b1350000 rwxp 00018000 03:01 771809     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdcpr.so
b1350000-b144a000 rwxs 00000000 00:07 37126194   /SYSV00000000 (deleted)
b144a000-b144d000 rwxp b144a000 00:00 0 
b144d000-b14cb000 rwxp b144d000 00:00 0 
b14cb000-b14ce000 ---p b14cb000 00:00 0 
b14ce000-b154c000 rwxp b14ce000 00:00 0 
b154c000-b1590000 r-xs 00000000 03:01 1144707    /home/josh/.java/deployment/cache/javapi/v1.0/jar/irc.jar-4a30142e-2988c96d.zip
b1590000-b15a0000 r-xp 00000000 03:01 3336867    /lib/tls/i686/cmov/libresolv-2.3.6.so
b15a0000-b15a1000 rwxp 00010000 03:01 3336867    /lib/tls/i686/cmov/libresolv-2.3.6.so
b15a1000-b15a3000 rwxp b15a1000 00:00 0 
b15a7000-b15ad000 r-xp 00000000 03:01 771804     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnio.so
b15ad000-b15ae000 rwxp 00005000 03:01 771804     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnio.so
b15ae000-b15c2000 r-xp 00000000 03:01 771803     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnet.so
b15c2000-b15c3000 rwxp 00013000 03:01 771803     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnet.so
b15c3000-b15c6000 ---p b15c3000 00:00 0 
b15c6000-b1644000 rwxp b15c6000 00:00 0 
b1644000-b1647000 rwxp b1644000 00:00 0 
b1647000-b16c5000 rwxp b1647000 00:00 0 
b16c5000-b16c8000 ---p b16c5000 00:00 0 
b16c8000-b1746000 rwxp b16c8000 00:00 0 
b1746000-b1749000 ---p b1746000 00:00 0 
b1749000-b17c7000 rwxp b1749000 00:00 0 
b17c7000-b17ca000 ---p b17c7000 00:00 0 
b17ca000-b1848000 rwxp b17ca000 00:00 0 
b1848000-b184b000 ---p b1848000 00:00 0 
b184b000-b18c9000 rwxp b184b000 00:00 0 
b18c9000-b18cc000 ---p b18c9000 00:00 0 
b18cc000-b194a000 rwxp b18cc000 00:00 0 
b194a000-b194d000 ---p b194a000 00:00 0 
b194d000-b19cb000 rwxp b194d000 00:00 0 
b19cb000-b19ce000 ---p b19cb000 00:00 0 
b19ce000-b1a4c000 rwxp b19ce000 00:00 0 
b1a4c000-b1a4f000 r-xp 00000000 03:01 655333     /usr/lib/libXfixes.so.3.0.0
b1a4f000-b1a50000 rwxp 00003000 03:01 655333     /usr/lib/libXfixes.so.3.0.0
b1a50000-b1a57000 r-xp 00000000 03:01 655353     /usr/lib/libXrender.so.1.3.0
b1a57000-b1a58000 rwxp 00006000 03:01 655353     /usr/lib/libXrender.so.1.3.0
b1a58000-b1a60000 r-xp 00000000 03:01 655325     /usr/lib/libXcursor.so.1.0.2
b1a60000-b1a61000 rwxp 00007000 03:01 655325     /usr/lib/libXcursor.so.1.0.2
b1a61000-b1a64000 ---p b1a61000 00:00 0 
b1a64000-b1ae2000 rwxp b1a64000 00:00 0 
b1ae2000-b1b55000 r-xp 00000000 03:01 771814     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libfontmanager.so
b1b55000-b1b5f000 rwxp 00073000 03:01 771814     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libfontmanager.so
b1b5f000-b1b63000 rwxp b1b5f000 00:00 0 
b1b63000-b1b76000 r-xp 00000000 03:01 771826     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so
b1b76000-b1b77000 rwxp 00012000 03:01 771826     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so
b1b77000-b1b8b000 rwxp b1b77000 00:00 0 
b1b8b000-b1c6c000 r-xp 00000000 03:01 655314     /usr/lib/libX11.so.6.2.0
b1c6c000-b1c70000 rwxp 000e1000 03:01 655314     /usr/lib/libX11.so.6.2.0
b1c70000-b1c71000 rwxp b1c70000 00:00 0 
b1c71000-b1c7d000 r-xp 00000000 03:01 655331     /usr/lib/libXext.so.6.4.0
b1c7d000-b1c7e000 rwxp 0000c000 03:01 655331     /usr/lib/libXext.so.6.4.0
b1c80000-b1c84000 r-xp 00000000 03:01 3336854    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b1c84000-b1c85000 rwxp 00003000 03:01 3336854    /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b1c85000-b1c88000 r-xp 00000000 03:01 771829     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdeploy.so
b1c88000-b1c89000 rwxp 00002000 03:01 771829     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdeploy.so
b1c89000-b1cbf000 r-xp 00000000 03:01 950075     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/xawt/libmawt.so
b1cbf000-b1cc2000 rwxp 00035000 03:01 950075     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/xawt/libmawt.so
b1cc2000-b1cc3000 rwxp b1cc2000 00:00 0 
b1cc3000-b1d89000 r-xp 00000000 03:01 771810     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libmlib_image.so
b1d89000-b1d8a000 rwxp 000c5000 03:01 771810     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libmlib_image.so
b1d8a000-b1dff000 r-xp 00000000 03:01 771811     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libawt.so
b1dff000-b1e05000 rwxp 00074000 03:01 771811     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libawt.so
b1e05000-b1e29000 rwxp b1e05000 00:00 0 
b1e29000-b1eed000 r-xs 00000000 03:01 951763     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/localedata.jar
b1eed000-b1f18000 r-xs 00000000 03:01 950081     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/sunpkcs11.jar
b1f18000-b1f3e000 r-xs 00000000 03:01 951761     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/sunjce_provider.jar
b1f3e000-b1f3f000 ---p b1f3e000 00:00 0 
b1f3f000-b1fbf000 rwxp b1f3f000 00:00 0 
b1fbf000-b1fc2000 ---p b1fbf000 00:00 0 
b1fc2000-b2040000 rwxp b1fc2000 00:00 0 
b2040000-b2043000 ---p b2040000 00:00 0 
b2043000-b20c1000 rwxp b2043000 00:00 0 
b20c1000-b20c4000 ---p b20c1000 00:00 0 
b20c4000-b2142000 rwxp b20c4000 00:00 0 
b2142000-b2175000 r-xp 00000000 03:01 703935     /usr/lib/locale/en_US.utf8/LC_CTYPE
b2175000-b2178000 ---p b2175000 00:00 0 
b2178000-b21f6000 rwxp b2178000 00:00 0 
b21f6000-b21f9000 ---p b21f6000 00:00 0 
b21f9000-b2277000 rwxp b21f9000 00:00 0 
b2277000-b2278000 ---p b2277000 00:00 0 
b2278000-b2309000 rwxp b2278000 00:00 0 
b2309000-b2325000 rwxp b2309000 00:00 0 
b2325000-b2327000 rwxp b2325000 00:00 0 
b2327000-b2343000 rwxp b2327000 00:00 0 
b2343000-b2344000 rwxp b2343000 00:00 0 
b2344000-b2345000 rwxp b2344000 00:00 0 
b2345000-b2348000 rwxp b2345000 00:00 0 
b2348000-b2363000 rwxp b2348000 00:00 0 
b2363000-b2367000 rwxp b2363000 00:00 0 
b2367000-b2383000 rwxp b2367000 00:00 0 
b2383000-b2394000 rwxp b2383000 00:00 0 
b2394000-b240e000 rwxp b2394000 00:00 0 
b240e000-b258e000 rwxp b240e000 00:00 0 
b258e000-b440e000 rwxp b258e000 00:00 0 
b440e000-b460b000 r-xs 00000000 03:01 771856     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar
b460b000-b4703000 r-xs 00000000 03:01 771857     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar
b4703000-b4f3e000 r-xs 00000000 03:01 771902     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/charsets.jar
b4f3e000-b4f52000 r-xs 00000000 03:01 771901     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/jce.jar
b4f52000-b4fd7000 r-xs 00000000 03:01 771900     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/jsse.jar
b4fd7000-b5040000 rwxp b4fd7000 00:00 0 
b5040000-b7628000 r-xs 00000000 03:01 771855     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/rt.jar
b7628000-b763b000 r-xp 00000000 03:01 771800     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libzip.so
b763b000-b763d000 rwxp 00012000 03:01 771800     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libzip.so
b763d000-b765e000 r-xp 00000000 03:01 771799     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjava.so
b765e000-b7660000 rwxp 00020000 03:01 771799     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjava.so
b7660000-b766b000 r-xp 00000000 03:01 771798     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libverify.so
b766b000-b766c000 rwxp 0000b000 03:01 771798     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libverify.so
b766c000-b7675000 r-xp 00000000 03:01 3336856    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b7675000-b7676000 rwxp 00008000 03:01 3336856    /lib/tls/i686/cmov/libnss_files-2.3.6.so
b7676000-b767e000 r-xp 00000000 03:01 3336860    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b767e000-b767f000 rwxp 00007000 03:01 3336860    /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b767f000-b7687000 r-xp 00000000 03:01 3336852    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b7687000-b7688000 rwxp 00007000 03:01 3336852    /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b7688000-b769a000 r-xp 00000000 03:01 3336850    /lib/tls/i686/cmov/libnsl-2.3.6.so
b769a000-b769b000 rwxp 00012000 03:01 3336850    /lib/tls/i686/cmov/libnsl-2.3.6.so
b769b000-b769d000 rwxp b769b000 00:00 0 
b769d000-b769f000 r-xp 00000000 03:01 655320     /usr/lib/libXau.so.6.0.0
b769f000-b76a0000 rwxp 00001000 03:01 655320     /usr/lib/libXau.so.6.0.0
b76a0000-b76a8000 rwxs 00000000 03:01 1520831    /tmp/hsperfdata_josh/1287
b76a8000-b76c9000 r-xp 00000000 03:01 3336847    /lib/tls/i686/cmov/libm-2.3.6.so
b76c9000-b76ca000 rwxp 00020000 03:01 3336847    /lib/tls/i686/cmov/libm-2.3.6.so
b76ca000-b7a2a000 r-xp 00000000 03:01 950072     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/libjvm.so
b7a2a000-b7a48000 rwxp 0035f000 03:01 950072     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/libjvm.so
b7a48000-b7e5f000 rwxp b7a48000 00:00 0 
b7e5f000-b7f84000 r-xp 00000000 03:01 3336839    /lib/tls/i686/cmov/libc-2.3.6.so
b7f84000-b7f8b000 rwxp 00125000 03:01 3336839    /lib/tls/i686/cmov/libc-2.3.6.so
b7f8b000-b7f8e000 rwxp b7f8b000 00:00 0 
b7f8e000-b7f90000 r-xp 00000000 03:01 3336845    /lib/tls/i686/cmov/libdl-2.3.6.so
b7f90000-b7f91000 rwxp 00001000 03:01 3336845    /lib/tls/i686/cmov/libdl-2.3.6.so
b7f91000-b7fa0000 r-xp 00000000 03:01 3336865    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7fa0000-b7fa1000 rwxp 0000e000 03:01 3336865    /lib/tls/i686/cmov/libpthread-2.3.6.so
b7fa1000-b7fa3000 rwxp b7fa1000 00:00 0 
b7fa3000-b7fa5000 r-xs 00000000 03:01 951762     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/dnsns.jar
b7fa5000-b7fab000 r-xp 00000000 03:01 771786     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/native_threads/libhpi.so
b7fab000-b7fac000 rwxp 00006000 03:01 771786     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/native_threads/libhpi.so
b7fac000-b7fad000 rwxp b7fac000 00:00 0 
b7fad000-b7fae000 r-xp b7fad000 00:00 0 
b7fae000-b7fb1000 rwxp b7fae000 00:00 0 
b7fb1000-b7fc6000 r-xp 00000000 03:01 3303126    /lib/ld-2.3.6.so
b7fc6000-b7fc7000 rwxp 00014000 03:01 3303126    /lib/ld-2.3.6.so
bf8c6000-bf8c9000 ---p bf8c6000 00:00 0 
bf8c9000-bfac6000 rwxp bf8c9000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -DtrustProxy=true -Xverify:remote -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_06 -Djavaplugin.version=1.5.0_06 -Djavaplugin.vm.options=-DtrustProxy=true -Xverify:remote -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/classes -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/classes -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_06 -Djavaplugin.version=1.5.0_06 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=josh
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x31b990], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x31b990], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x283580], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:3.10 2.01 1.75

CPU:total 1 family 6, cmov, cx8, fxsr, mmx, sse

Memory: 4k page, physical 385256k(3936k free), swap 1124508k(1012508k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_06-b05) for linux-x86, built on Dec 17 2005 01:54:22 by java_re with gcc 3.2.1-7a (J2SE release)


```


I'm pretty lost and can't figure it out!  Any help is apreciated!

---

