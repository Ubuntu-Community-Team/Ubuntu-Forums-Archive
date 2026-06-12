---
title: "Computeach, Java and Ubuntu"
date: 2007-02-02
forum: General Help
---

### Post by sabrewolf2006 on 2007-02-02
Hi,
I recently installed ubuntu edgy and installed the sun-java5-jre and sun-java5-plugin to allow me to use java applets on the web.
The problem is that when I go to take a mock exam at Computeach, the applet dies and takes firefox with it (I have also tried with epiphany, it dies too)
Luckily, the system provided an error log..
The forum won't let me attach it so I'll have to include it here:

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1aa731e, pid=27284, tid=2973735840
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2d31e]
#

---------------  T H R E A D  ---------------

Current thread (0x083cf468):  JavaThread "AWT-EventQueue-2" [_thread_in_native, id=27309]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0xc1f5ac70

Registers:
EAX=0x08464720, EBX=0xb1ae9d48, ECX=0xb13f826c, EDX=0x0844ebb0
ESP=0xb13f81cc, EBP=0xb13f8224, ESI=0x2e6c3030, EDI=0x00626670
EIP=0xb1aa731e, CR2=0xc1f5ac70, EFLAGS=0x00010202

Top of Stack: (sp=0xb13f81cc)
0xb13f81cc:   b13f841c 00000001 ffffffff 00000001
0xb13f81dc:   000000b7 00000040 0844dacc b1aa8e47
0xb13f81ec:   00000000 8ca50550 00000000 b1ae9d48
0xb13f81fc:   b13f826c 8ca50550 0000014b b1aa4f91
0xb13f820c:   b13f826c 2e6c3030 b1aa72bb b1ae9d48
0xb13f821c:   b13f826c b1aee220 b13f8244 b1aa8f08
0xb13f822c:   b13f826c 083bf4c0 00000106 4041fc00
0xb13f823c:   b13f826c 083b5568 b13f8394 b1aa8501 

Instructions: (pc=0xb1aa731e)
0xb1aa730e:   8b 38 83 e8 04 8b 30 83 e8 04 89 75 ec 8b 52 04
0xb1aa731e:   8b 34 b2 89 75 e8 8b 14 ba 29 f2 89 55 d8 8b 75 

Stack: [0xb1379000,0xb13fa000),  sp=0xb13f81cc,  free space=508k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x2d31e]
C  [libfontmanager.so+0x2ef08]
C  [libfontmanager.so+0x2e501]
C  [libfontmanager.so+0x30d60]
C  [libfontmanager.so+0x2f97b]
C  [libfontmanager.so+0x2f785]
C  [libfontmanager.so+0x1cb44]
C  [libfontmanager.so+0x1d072]
C  [libfontmanager.so+0x3f038]  Java_sun_font_FileFont_getGlyphImage+0x128
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
j  sun.font.FontDesignMetrics.handleCharWidth(I)F+5
j  sun.font.FontDesignMetrics.getLatinCharWidth(C)F+16
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  com.sun.java.swing.SwingUtilities2.stringWidth(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;)I+2
j  javax.swing.SwingUtilities.layoutCompoundLabelImpl(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;IIIILjava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;I)Ljava/lang/String;+197
j  javax.swing.SwingUtilities.layoutCompoundLabel(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;IIIILjava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;I)Ljava/lang/String;+159
j  javax.swing.plaf.basic.BasicLabelUI.layoutCL(Ljavax/swing/JLabel;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;Ljava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;)Ljava/lang/String;+31
j  javax.swing.plaf.basic.BasicLabelUI.getPreferredSize(Ljavax/swing/JComponent;)Ljava/awt/Dimension;+255
j  javax.swing.JComponent.getPreferredSize()Ljava/awt/Dimension;+26
j  se.datadosen.component.RiverLayout.calcTabs(Ljava/awt/Container;)Lse/datadosen/component/Ruler;+100
j  se.datadosen.component.RiverLayout.preferredLayoutSize(Ljava/awt/Container;)Ljava/awt/Dimension;+42
j  java.awt.Container.preferredSize()Ljava/awt/Dimension;+43
j  java.awt.Container.getPreferredSize()Ljava/awt/Dimension;+1
j  javax.swing.JComponent.getPreferredSize()Ljava/awt/Dimension;+39
j  java.awt.BorderLayout.layoutContainer(Ljava/awt/Container;)V+89
j  java.awt.Container.layout()V+11
j  java.awt.Container.doLayout()V+1
j  java.awt.Container.validateTree()V+30
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validate()V+61
j  sun.applet.AppletPanel$2.run()V+4
j  java.awt.event.InvocationEvent.dispatch()V+11
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+26
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x17a75c]
V  [libjvm.so+0x28afd8]
V  [libjvm.so+0x179fb5]
V  [libjvm.so+0x17a04e]
V  [libjvm.so+0x1f1785]
V  [libjvm.so+0x2f43d3]
V  [libjvm.so+0x28bbe8]
C  [libpthread.so.0+0x5504]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
j  sun.font.FontDesignMetrics.handleCharWidth(I)F+5
j  sun.font.FontDesignMetrics.getLatinCharWidth(C)F+16
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  com.sun.java.swing.SwingUtilities2.stringWidth(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;)I+2
j  javax.swing.SwingUtilities.layoutCompoundLabelImpl(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;IIIILjava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;I)Ljava/lang/String;+197
j  javax.swing.SwingUtilities.layoutCompoundLabel(Ljavax/swing/JComponent;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;IIIILjava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;I)Ljava/lang/String;+159
j  javax.swing.plaf.basic.BasicLabelUI.layoutCL(Ljavax/swing/JLabel;Ljava/awt/FontMetrics;Ljava/lang/String;Ljavax/swing/Icon;Ljava/awt/Rectangle;Ljava/awt/Rectangle;Ljava/awt/Rectangle;)Ljava/lang/String;+31
j  javax.swing.plaf.basic.BasicLabelUI.getPreferredSize(Ljavax/swing/JComponent;)Ljava/awt/Dimension;+255
j  javax.swing.JComponent.getPreferredSize()Ljava/awt/Dimension;+26
j  se.datadosen.component.RiverLayout.calcTabs(Ljava/awt/Container;)Lse/datadosen/component/Ruler;+100
j  se.datadosen.component.RiverLayout.preferredLayoutSize(Ljava/awt/Container;)Ljava/awt/Dimension;+42
j  java.awt.Container.preferredSize()Ljava/awt/Dimension;+43
j  java.awt.Container.getPreferredSize()Ljava/awt/Dimension;+1
j  javax.swing.JComponent.getPreferredSize()Ljava/awt/Dimension;+39
j  java.awt.BorderLayout.layoutContainer(Ljava/awt/Container;)V+89
j  java.awt.Container.layout()V+11
j  java.awt.Container.doLayout()V+1
j  java.awt.Container.validateTree()V+30
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validateTree()V+77
j  java.awt.Container.validate()V+61
j  sun.applet.AppletPanel$2.run()V+4
j  java.awt.event.InvocationEvent.dispatch()V+11
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+26
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x083cf468 JavaThread "AWT-EventQueue-2" [_thread_in_native, id=27309]
  0x083d1e48 JavaThread "TimerQueue" daemon [_thread_blocked, id=27308]
  0x083cc7c8 JavaThread "Keep-Alive-Timer" daemon [_thread_blocked, id=27307]
  0x083b6118 JavaThread "Thread-4" [_thread_blocked, id=27305]
  0x083b59c8 JavaThread "thread applet-examengine.client.app.class" [_thread_blocked, id=27304]
  0x083b2ae0 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=27301]
  0x083b1688 JavaThread "AWT-Shutdown" [_thread_blocked, id=27300]
  0x083a6970 JavaThread "Thread-2" [_thread_in_native, id=27299]
  0x08383510 JavaThread "Thread-1" [_thread_blocked, id=27296]
  0x08383020 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=27294]
  0x0836d120 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=27293]
  0x082e52a0 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=27292]
  0x080a1e60 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=27290]
  0x080a08b8 JavaThread "CompilerThread0" daemon [_thread_blocked, id=27289]
  0x0809f988 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=27288]
  0x08097fc0 JavaThread "Finalizer" daemon [_thread_blocked, id=27287]
  0x080972d8 JavaThread "Reference Handler" daemon [_thread_blocked, id=27286]
  0x08050bd0 JavaThread "main" [_thread_in_native, id=27284]

Other Threads:
  0x080946e8 VMThread [id=27285]
  0x080a3348 WatcherThread [id=27291]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 576K, used 162K [0x88a20000, 0x88ac0000, 0x88f00000)
  eden space 512K,  25% used [0x88a20000, 0x88a40608, 0x88aa0000)
  from space 64K,  51% used [0x88aa0000, 0x88aa82e0, 0x88ab0000)
  to   space 64K,   0% used [0x88ab0000, 0x88ab0000, 0x88ac0000)
 tenured generation   total 2364K, used 2038K [0x88f00000, 0x8914f000, 0x8ca20000)
   the space 2364K,  86% used [0x88f00000, 0x890fdb98, 0x890fdc00, 0x8914f000)
 compacting perm gen  total 8192K, used 2408K [0x8ca20000, 0x8d220000, 0x90a20000)
   the space 8192K,  29% used [0x8ca20000, 0x8cc7a1b0, 0x8cc7a200, 0x8d220000)
    ro space 8192K,  68% used [0x90a20000, 0x90f9eaf8, 0x90f9ec00, 0x91220000)
    rw space 12288K,  48% used [0x91220000, 0x917e9d78, 0x917e9e00, 0x91e20000)

Dynamic libraries:
08048000-0804b000 r-xp 00000000 03:03 1224555    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java_vm
0804b000-0804c000 rwxp 00002000 03:03 1224555    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java_vm
0804c000-08481000 rwxp 0804c000 00:00 0          [heap]
88a20000-88ac0000 rwxp 88a20000 00:00 0 
88ac0000-88f00000 rwxp 88ac0000 00:00 0 
88f00000-8914f000 rwxp 88f00000 00:00 0 
8914f000-8ca20000 rwxp 8914f000 00:00 0 
8ca20000-8d220000 rwxp 8ca20000 00:00 0 
8d220000-90a20000 rwxp 8d220000 00:00 0 
90a20000-90f9f000 r-xs 00001000 03:03 1225282    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
90f9f000-91220000 rwxp 90f9f000 00:00 0 
91220000-917ea000 rwxp 00580000 03:03 1225282    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
917ea000-91e20000 rwxp 917ea000 00:00 0 
91e20000-91ef0000 rwxp 00b4a000 03:03 1225282    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
91ef0000-92220000 rwxp 91ef0000 00:00 0 
92220000-92224000 r-xs 00c1a000 03:03 1225282    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
92224000-92620000 rwxp 92224000 00:00 0 
b0f33000-b0f3c000 r-xs 00000000 03:03 180364     /usr/share/fonts/X11/Type1/c0649bt_.pfb
b0f3c000-b0f45000 r-xs 00000000 03:03 180362     /usr/share/fonts/X11/Type1/c0648bt_.pfb
b0f45000-b0f4e000 r-xs 00000000 03:03 180360     /usr/share/fonts/X11/Type1/c0633bt_.pfb
b0f4e000-b0f58000 r-xs 00000000 03:03 180356     /usr/share/fonts/X11/Type1/c0611bt_.pfb
b0f58000-b0f62000 r-xs 00000000 03:03 180354     /usr/share/fonts/X11/Type1/c0583bt_.pfb
b0f62000-b0f6c000 r-xs 00000000 03:03 180352     /usr/share/fonts/X11/Type1/c0582bt_.pfb
b0f6c000-b0f76000 r-xs 00000000 03:03 180350     /usr/share/fonts/X11/Type1/c0419bt_.pfb
b0f76000-b0f82000 r-xs 00000000 03:03 212196     /usr/share/fonts/type1/gsfonts/d050000l.pfb
b0f82000-b0fa3000 r-xs 00000000 03:03 212240     /usr/share/fonts/type1/gsfonts/p052003l.pfb
b0fa3000-b0fc3000 r-xs 00000000 03:03 212244     /usr/share/fonts/type1/gsfonts/p052023l.pfb
b0fc3000-b0fe4000 r-xs 00000000 03:03 212246     /usr/share/fonts/type1/gsfonts/p052024l.pfb
b0fe4000-b1005000 r-xs 00000000 03:03 212242     /usr/share/fonts/type1/gsfonts/p052004l.pfb
b1005000-b1018000 r-xs 00000000 03:03 212173     /usr/share/fonts/type1/gsfonts/a010035l.pfb
b1018000-b102b000 r-xs 00000000 03:03 212167     /usr/share/fonts/type1/gsfonts/a010015l.pfb
b102b000-b103d000 r-xs 00000000 03:03 212170     /usr/share/fonts/type1/gsfonts/a010033l.pfb
b103d000-b104f000 r-xs 00000000 03:03 212164     /usr/share/fonts/type1/gsfonts/a010013l.pfb
b104f000-b106c000 r-xs 00000000 03:03 212250     /usr/share/fonts/type1/gsfonts/z003034l.pfb
b106c000-b108a000 r-xs 00000000 03:03 212182     /usr/share/fonts/type1/gsfonts/b018032l.pfb
b10c1000-b10d3000 r-xs 00000000 03:03 212205     /usr/share/fonts/type1/gsfonts/n019023l.pfb
b10d3000-b10e6000 r-xs 00000000 03:03 212211     /usr/share/fonts/type1/gsfonts/n019043l.pfb
b10e6000-b10f8000 r-xs 00000000 03:03 212199     /usr/share/fonts/type1/gsfonts/n019003l.pfb
b10f8000-b110b000 r-xs 00000000 03:03 212208     /usr/share/fonts/type1/gsfonts/n019024l.pfb
b110b000-b111f000 r-xs 00000000 03:03 212217     /usr/share/fonts/type1/gsfonts/n019064l.pfb
b111f000-b1132000 r-xs 00000000 03:03 212213     /usr/share/fonts/type1/gsfonts/n019044l.pfb
b1132000-b1145000 r-xs 00000000 03:03 212202     /usr/share/fonts/type1/gsfonts/n019004l.pfb
b1145000-b1160000 r-xs 00000000 03:03 212226     /usr/share/fonts/type1/gsfonts/n021023l.pfb
b1160000-b117c000 r-xs 00000000 03:03 212220     /usr/share/fonts/type1/gsfonts/n021003l.pfb
b117c000-b1195000 r-xs 00000000 03:03 212229     /usr/share/fonts/type1/gsfonts/n021024l.pfb
b1195000-b11b1000 r-xs 00000000 03:03 212223     /usr/share/fonts/type1/gsfonts/n021004l.pfb
b11b1000-b11cb000 r-xs 00000000 03:03 212236     /usr/share/fonts/type1/gsfonts/n022023l.pfb
b11cb000-b11e3000 r-xs 00000000 03:03 212232     /usr/share/fonts/type1/gsfonts/n022003l.pfb
b11e3000-b1200000 r-xs 00000000 03:03 212238     /usr/share/fonts/type1/gsfonts/n022024l.pfb
b1200000-b1221000 rwxp b1200000 00:00 0 
b1221000-b1300000 ---p b1221000 00:00 0 
b1304000-b130d000 r-xs 00000000 03:03 180358     /usr/share/fonts/X11/Type1/c0632bt_.pfb
b1326000-b1379000 r-xs 00000000 03:05 3535517    /home/ubutest/.java/deployment/cache/javapi/v1.0/jar/Chart2D.jar-26982375-2d1a98f0.zip
b1379000-b137c000 ---p b1379000 00:00 0 
b137c000-b13fa000 rwxp b137c000 00:00 0 
b13fa000-b13fd000 ---p b13fa000 00:00 0 
b13fd000-b147b000 rwxp b13fd000 00:00 0 
b147b000-b14a7000 r-xs 00000000 03:05 3535515    /home/ubutest/.java/deployment/cache/javapi/v1.0/jar/ExamEngine.jar-625dd04-1f22123e.zip
b14a7000-b14aa000 ---p b14a7000 00:00 0 
b14aa000-b1528000 rwxp b14aa000 00:00 0 
b1528000-b1537000 r-xp 00000000 03:03 1044971    /lib/tls/i686/cmov/libresolv-2.4.so
b1537000-b1539000 rwxp 0000f000 03:03 1044971    /lib/tls/i686/cmov/libresolv-2.4.so
b1539000-b153b000 rwxp b1539000 00:00 0 
b153b000-b153f000 r-xp 00000000 03:03 1044964    /lib/tls/i686/cmov/libnss_dns-2.4.so
b153f000-b1541000 rwxp 00003000 03:03 1044964    /lib/tls/i686/cmov/libnss_dns-2.4.so
b1541000-b1553000 r-xs 00000000 03:03 212215     /usr/share/fonts/type1/gsfonts/n019063l.pfb
b1553000-b1559000 r-xp 00000000 03:03 1224577    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnio.so
b1559000-b155a000 rwxp 00005000 03:03 1224577    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnio.so
b155a000-b155d000 ---p b155a000 00:00 0 
b155d000-b15db000 rwxp b155d000 00:00 0 
b15db000-b15de000 ---p b15db000 00:00 0 
b15de000-b165c000 rwxp b15de000 00:00 0 
b165c000-b165f000 rwxp b165c000 00:00 0 
b165f000-b16dd000 rwxp b165f000 00:00 0 
b16dd000-b16e0000 ---p b16dd000 00:00 0 
b16e0000-b175e000 rwxp b16e0000 00:00 0 
b175e000-b1761000 ---p b175e000 00:00 0 
b1761000-b17df000 rwxp b1761000 00:00 0 
b17df000-b17e2000 ---p b17df000 00:00 0 
b17e2000-b1860000 rwxp b17e2000 00:00 0 
b1860000-b1863000 ---p b1860000 00:00 0 
b1863000-b18e1000 rwxp b1863000 00:00 0 
b18e1000-b18e4000 ---p b18e1000 00:00 0 
b18e4000-b1962000 rwxp b18e4000 00:00 0 
b1962000-b1965000 ---p b1962000 00:00 0 
b1965000-b19e3000 rwxp b1965000 00:00 0 
b19e3000-b19e7000 r-xp 00000000 03:03 1048147    /usr/lib/libXfixes.so.3.1.0
b19e7000-b19e8000 rwxp 00003000 03:03 1048147    /usr/lib/libXfixes.so.3.1.0
b19e8000-b19ef000 r-xp 00000000 03:03 1048179    /usr/lib/libXrender.so.1.3.0
b19ef000-b19f0000 rwxp 00006000 03:03 1048179    /usr/lib/libXrender.so.1.3.0
b19f0000-b19f8000 r-xp 00000000 03:03 1048131    /usr/lib/libXcursor.so.1.0.2
b19f8000-b19f9000 rwxp 00007000 03:03 1048131    /usr/lib/libXcursor.so.1.0.2
b19f9000-b19fc000 ---p b19f9000 00:00 0 
b19fc000-b1a7a000 rwxp b19fc000 00:00 0 
b1a7a000-b1ae1000 r-xp 00000000 03:03 1224593    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libfontmanager.so
b1ae1000-b1aeb000 rwxp 00067000 03:03 1224593    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libfontmanager.so
b1aeb000-b1aef000 rwxp b1aeb000 00:00 0 
b1aef000-b1aff000 r-xp 00000000 03:03 1224605    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_jni.so
b1aff000-b1b00000 rwxp 00010000 03:03 1224605    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_jni.so
b1b00000-b1b14000 rwxp b1b00000 00:00 0 
b1b14000-b1b18000 r-xp 00000000 03:03 1048137    /usr/lib/libXdmcp.so.6.0.0
b1b18000-b1b19000 rwxp 00003000 03:03 1048137    /usr/lib/libXdmcp.so.6.0.0
b1b19000-b1bdf000 r-xp 00000000 03:03 1048112    /usr/lib/libX11.so.6.2.0
b1bdf000-b1be2000 rwxp 000c5000 03:03 1048112    /usr/lib/libX11.so.6.2.0
b1be2000-b1bee000 r-xp 00000000 03:03 1048143    /usr/lib/libXext.so.6.4.0
b1bee000-b1bef000 rwxp 0000c000 03:03 1048143    /usr/lib/libXext.so.6.4.0
b1bef000-b1bf2000 r-xs 00000000 03:05 3535519    /home/ubutest/.java/deployment/cache/javapi/v1.0/jar/ct.jar-60e17914-57e4c0e3.zip
b1bf2000-b1c03000 r-xp 00000000 03:03 1224576    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnet.so
b1c03000-b1c04000 rwxp 00011000 03:03 1224576    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnet.so
b1c04000-b1c07000 r-xp 00000000 03:03 1224608    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libdeploy.so
b1c07000-b1c08000 rwxp 00002000 03:03 1224608    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libdeploy.so
b1c08000-b1c36000 r-xp 00000000 03:03 1224588    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/xawt/libmawt.so
b1c36000-b1c39000 rwxp 0002e000 03:03 1224588    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/xawt/libmawt.so
b1c39000-b1c3a000 rwxp b1c39000 00:00 0 
b1c3a000-b1d00000 r-xp 00000000 03:03 1224583    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libmlib_image.so
b1d00000-b1d01000 rwxp 000c5000 03:03 1224583    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libmlib_image.so
b1d01000-b1d61000 r-xp 00000000 03:03 1224584    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libawt.so
b1d61000-b1d67000 rwxp 0005f000 03:03 1224584    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libawt.so
b1d67000-b1d8b000 rwxp b1d67000 00:00 0 
b1d8b000-b1e4f000 r-xs 00000000 03:03 1225269    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/localedata.jar
b1e4f000-b1e7a000 r-xs 00000000 03:03 1224610    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/sunpkcs11.jar
b1e7a000-b1ea1000 r-xs 00000000 03:03 1225267    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/sunjce_provider.jar
b1ea1000-b1ea2000 ---p b1ea1000 00:00 0 
b1ea2000-b1f22000 rwxp b1ea2000 00:00 0 
b1f22000-b1f25000 ---p b1f22000 00:00 0 
b1f25000-b1fa3000 rwxp b1f25000 00:00 0 
b1fa3000-b1fa6000 ---p b1fa3000 00:00 0 
b1fa6000-b2024000 rwxp b1fa6000 00:00 0 
b2024000-b2027000 ---p b2024000 00:00 0 
b2027000-b20a5000 rwxp b2027000 00:00 0 
b20a5000-b20ac000 r-xs 00000000 03:03 1112372    /usr/lib/gconv/gconv-modules.cache
b20ac000-b20df000 r-xp 00000000 03:03 1145489    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b20df000-b20e2000 ---p b20df000 00:00 0 
b20e2000-b2160000 rwxp b20e2000 00:00 0 
b2160000-b2163000 ---p b2160000 00:00 0 
b2163000-b21e1000 rwxp b2163000 00:00 0 
b21e1000-b21e2000 ---p b21e1000 00:00 0 
b21e2000-b226e000 rwxp b21e2000 00:00 0 
b226e000-b228a000 rwxp b226e000 00:00 0 
b228a000-b228c000 rwxp b228a000 00:00 0 
b228c000-b22a8000 rwxp b228c000 00:00 0 
b22a8000-b22a9000 rwxp b22a8000 00:00 0 
b22a9000-b22aa000 rwxp b22a9000 00:00 0 
b22aa000-b22ac000 rwxp b22aa000 00:00 0 
b22ac000-b22c8000 rwxp b22ac000 00:00 0 
b22c8000-b22cc000 rwxp b22c8000 00:00 0 
b22cc000-b22e8000 rwxp b22cc000 00:00 0 
b22e8000-b22f8000 rwxp b22e8000 00:00 0 
b22f8000-b2373000 rwxp b22f8000 00:00 0 
b2373000-b247b000 rwxp b2373000 00:00 0 
b247b000-b4373000 rwxp b247b000 00:00 0 
b4373000-b4571000 r-xs 00000000 03:03 1224686    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/deploy.jar
b4571000-b4669000 r-xs 00000000 03:03 1224701    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/plugin.jar
b4669000-b4ed9000 r-xs 00000000 03:03 1225275    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/charsets.jar
b4ed9000-b4eee000 r-xs 00000000 03:03 1225270    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/jce.jar
b4eee000-b4f73000 r-xs 00000000 03:03 1225266    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/jsse.jar
b4f73000-b4fdc000 rwxp b4f73000 00:00 0 
b4fdc000-b75f2000 r-xs 00000000 03:03 1224639    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/rt.jar
b75f2000-b7601000 r-xp 00000000 03:03 1224573    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libzip.so
b7601000-b7603000 rwxp 0000e000 03:03 1224573    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libzip.so
b7603000-b7624000 r-xp 00000000 03:03 1224572    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjava.so
b7624000-b7626000 rwxp 00020000 03:03 1224572    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjava.so
b7626000-b762f000 r-xp 00000000 03:03 1044965    /lib/tls/i686/cmov/libnss_files-2.4.so
b762f000-b7631000 rwxp 00008000 03:03 1044965    /lib/tls/i686/cmov/libnss_files-2.4.so
b7631000-b7639000 r-xp 00000000 03:03 1044967    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7639000-b763b000 rwxp 00007000 03:03 1044967    /lib/tls/i686/cmov/libnss_nis-2.4.so
b763b000-b764d000 r-xp 00000000 03:03 1044962    /lib/tls/i686/cmov/libnsl-2.4.so
b764d000-b764f000 rwxp 00011000 03:03 1044962    /lib/tls/i686/cmov/libnsl-2.4.so
b764f000-b7651000 rwxp b764f000 00:00 0 
b7651000-b7652000 r-xp 00000000 03:03 1142545    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7652000-b7653000 rwxp 00000000 03:03 1142545    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7653000-b7655000 r-xp 00000000 03:03 1048120    /usr/lib/libXau.so.6.0.0
b7655000-b7656000 rwxp 00001000 03:03 1048120    /usr/lib/libXau.so.6.0.0
b7656000-b7661000 r-xp 00000000 03:03 1224571    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libverify.so
b7661000-b7662000 rwxp 0000b000 03:03 1224571    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libverify.so
b7662000-b766a000 rwxs 00000000 03:03 539368     /tmp/hsperfdata_ubutest/27284
b766a000-b768e000 r-xp 00000000 03:03 1044960    /lib/tls/i686/cmov/libm-2.4.so
b768e000-b7690000 rwxp 00023000 03:03 1044960    /lib/tls/i686/cmov/libm-2.4.so
b7690000-b79fc000 r-xp 00000000 03:03 1224566    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/libjvm.so
b79fc000-b7a1b000 rwxp 0036b000 03:03 1224566    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/libjvm.so
b7a1b000-b7e32000 rwxp b7a1b000 00:00 0 
b7e32000-b7f5f000 r-xp 00000000 03:03 1044956    /lib/tls/i686/cmov/libc-2.4.so
b7f5f000-b7f61000 r-xp 0012c000 03:03 1044956    /lib/tls/i686/cmov/libc-2.4.so
b7f61000-b7f63000 rwxp 0012e000 03:03 1044956    /lib/tls/i686/cmov/libc-2.4.so
b7f63000-b7f67000 rwxp b7f63000 00:00 0 
b7f67000-b7f69000 r-xp 00000000 03:03 1044959    /lib/tls/i686/cmov/libdl-2.4.so
b7f69000-b7f6b000 rwxp 00001000 03:03 1044959    /lib/tls/i686/cmov/libdl-2.4.so
b7f6b000-b7f7a000 r-xp 00000000 03:03 1044970    /lib/tls/i686/cmov/libpthread-2.4.so
b7f7a000-b7f7c000 rwxp 0000f000 03:03 1044970    /lib/tls/i686/cmov/libpthread-2.4.so
b7f7c000-b7f7e000 rwxp b7f7c000 00:00 0 
b7f7e000-b7f80000 r-xs 00000000 03:03 1225268    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/dnsns.jar
b7f80000-b7f85000 rwxp b7f80000 00:00 0 
b7f85000-b7f8c000 r-xp 00000000 03:03 1044963    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7f8c000-b7f8e000 rwxp 00006000 03:03 1044963    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7f8e000-b7f94000 r-xp 00000000 03:03 1224561    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/native_threads/libhpi.so
b7f94000-b7f95000 rwxp 00006000 03:03 1224561    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/native_threads/libhpi.so
b7f95000-b7f96000 rwxp b7f95000 00:00 0 
b7f96000-b7f97000 r-xp b7f96000 00:00 0 
b7f97000-b7f99000 rwxp b7f97000 00:00 0 
b7f99000-b7fb2000 r-xp 00000000 03:03 1011888    /lib/ld-2.4.so
b7fb2000-b7fb4000 rwxp 00018000 03:03 1011888    /lib/ld-2.4.so
bfb2f000-bfb32000 ---p bfb2f000 00:00 0 
bfb32000-bfd2f000 rwxp bfb32000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -DtrustProxy=true -Xverify:remote -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_08 -Djavaplugin.version=1.5.0_08 -Djavaplugin.vm.options=-DtrustProxy=true -Xverify:remote -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/classes -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/classes -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_08 -Djavaplugin.version=1.5.0_08 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=ubutest
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x325bd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x325bd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x28a010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x28a010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x28a010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x28c460], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
libc:glibc 2.4 NPTL 2.4 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.76 0.57 0.44

CPU:total 2 (cores per cpu 2, threads per core 1) family 15 model 6 stepping 4, cmov, cx8, fxsr, mmx, sse, sse2, sse3

Memory: 4k page, physical 1035340k(13764k free), swap 1952960k(1952960k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_08-b03) for linux-x86, built on Jul 11 2006 09:55:52 by java_re with gcc 3.2.1-7a (J2SE release)

Do I just need to provide the sun-java5-fonts package or is there something else going wrong here too..?

---

### Post by phossal on 2007-02-02
I would recommend download Java 6 via the web, and installing it (and the plugin) according to the tutorial in my Sig. At least review the section on installing the plugin to verify that it's been done correctly.  (With a little modification, you can make it work for Java 5)

Cheers!

---

### Post by sabrewolf2006 on 2007-02-04
I have installed Java6 as directed.. according to the Sun Java Test page (Java 5 worked too with the test page) its installed correctly (Duke mascot dancing and the system info above)

But again, when I try to start the Computeach exam the applet dies and takes firefox with it..
The really odd thing is that the exam worked fine in FC6.. I have a partition to spare but I don't wanna install it if I don't have to...
I can provide the error log from Java6 if ya want.?

Thanks for the quick response :)

---

### Post by phossal on 2007-02-04
Can you visit another page with Java Applets? For example, can you play Java-enabled games at [http://games.yahoo.com?](http://games.yahoo.com?)

---

### Post by sabrewolf2006 on 2007-02-05
This is weird, the old chess java applet seems to work fine.
*shrugs*
There must be something in the exam applet that I'm missing.. fonts didn't help, Java6 JDK didn't help
I'm stumped.. :|

---

### Post by lenooh on 2007-02-07
I also had a problem with libfontmanager.so in some java applications.

the problem is in some fonts that are distributed with ubuntu.
you can solve it by removing them:
```
sudo apt-get remove ttf-gujarati-fonts
sudo apt-get remove gsfonts-x11
```

you can read about it here:
[http://intellij.net/forums/thread.jspa?forumID=27&threadID=189420]("http://intellij.net/forums/thread.jspa?forumID=27&threadID=189420")
[http://support.jetbrains.com/kb/entry.jspa?externalID=172&categoryID=4]("http://support.jetbrains.com/kb/entry.jspa?externalID=172&categoryID=4")
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6358041]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6358041")

br

---

### Post by sabrewolf2006 on 2007-02-07
Brilliant, that worked a treat ):P
Thanks for the help phossal and lenooh
Now, to start revising, again. [-o<

---

