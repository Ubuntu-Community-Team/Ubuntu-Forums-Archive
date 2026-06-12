---
title: "Eclipse Error"
date: 2007-12-29
forum: General Help
---

### Post by scienceandtech on 2007-12-29
The following error is displayed while running eclipse

=====================================[INDENT]     JVM terminated. Exit code=1
    /usr/bin/java
    -Xms256m
    -Xmx512m
    -jar /home/sumiravi/Programs/eclipse/startup.jar
    -os linux
    -ws gtk
    -arch x86
    -launcher /home/sumiravi/Programs/eclipse/eclipse
    -name Eclipse
    -showsplash 600
    -exitdata e8009
    -vm /usr/bin/java
    -vmargs
    -Xms256m
    -Xmx512m
    -jar /home/sumiravi/Programs/eclipse/startup.jar  [/INDENT]========================================
Environment Details

Eclipse: 3.2.1
Java: jdk 1.5.0_13
Exadel: 4.0.0
Tomcat: 5.5.20
Ubuntu: 7.10


Please Help to resolve this issue


######################################################################
This is the error log

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xa52f9f12, pid=10452, tid=3085317808
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_13-b05 mixed mode, sharing)
# Problematic frame:
# C  [libmozjs.so+0x1cf12]
#

---------------  T H R E A D  ---------------

Current thread (0x0805ceb8):  JavaThread "main" [_thread_in_native, id=10452]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x00000002

Registers:
EAX=0x00000002, EBX=0xa5385758, ECX=0xa58f7e30, EDX=0xa58f7f7c
ESP=0xbfc58fbc, EBP=0xbfc58fd4, ESI=0xa5b7dc90, EDI=0xa5512908
EIP=0xa52f9f12, CR2=0x00000002, EFLAGS=0x00210282

Top of Stack: (sp=0xbfc58fbc)
0xbfc58fbc:   a5512908 b2000010 0000017c a5385758
0xbfc58fcc:   a58f7e30 a5512908 bfc59014 a52f9fc0
0xbfc58fdc:   a58f7e30 00000000 0000017c a5804340
0xbfc58fec:   00000000 00000001 00000001 00000000
0xbfc58ffc:   a444ff47 a58f7e30 a52f9f5b a5385758
0xbfc5900c:   8007000e a5bc2230 bfc59034 a52f1a04
0xbfc5901c:   a5512908 00000100 a5bc2230 00000002
0xbfc5902c:   a52f19e0 a4499afc bfc590a4 a4490130 

Instructions: (pc=0xa52f9f12)
0xa52f9f02:   4c 01 00 00 89 81 50 01 00 00 8b 46 04 89 56 04
0xa52f9f12:   89 10 b8 01 00 00 00 8b 5d f4 8b 75 f8 8b 7d fc 

Stack: [0xbfa5d000,0xbfc5d000),  sp=0xbfc58fbc,  free space=2031k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libmozjs.so+0x1cf12]
C  [libmozjs.so+0x1cfc0]
C  [libmozjs.so+0x14a04]  JS_NewContext+0x24
C  [libxpconnect.so+0x44130]
C  [libxpconnect.so+0x4598f]
C  [libxpconnect.so+0x460fe]
C  [libxpconnect.so+0x465dd]
C  [libxpconnect.so+0x43318]
C  [libxpcom_core.so+0x6773a]
C  [libxpcom_core.so+0x67b62]
C  [libxpcom_core.so+0x67ca6]
C  [libxpcom_core.so+0x2d1f2]  NS_InitXPCOM3_P+0x5c2
C  [libxpcom_core.so+0x2d5fb]  NS_InitXPCOM2_P+0x3b
C  [libxpcom.so+0x1eeb]  NS_InitXPCOM2+0x2b
C  [libswt-mozilla-gtk-3235.so+0x997b]
C  [libswt-mozilla-gtk-3235.so+0x4a58]  Java_org_eclipse_swt_internal_mozilla_XPCOM_NS_1InitEmbedding+0x1e
j  org.eclipse.swt.internal.mozilla.XPCOM.NS_InitEmbedding(II)I+0
j  org.eclipse.swt.browser.Browser.<init>(Lorg/eclipse/swt/widgets/Composite; I)V+392
j  org.eclipse.jdt.internal.ui.text.java.hover.BrowserInformationControl.isAvailable(Lorg/eclipse/swt/widgets/Composite; )Z+29
j  org.eclipse.jdt.internal.ui.text.java.hover.JavadocHover$2.doCreateInformationControl(Lorg/eclipse/swt/widgets/Shell; )Lorg/eclipse/jface/text/IInformationControl;+1
j  org.eclipse.jdt.internal.ui.text.java.hover.AbstractReusableInformationControlCreator.createInformationControl(Lorg/eclipse/swt/widgets/Shell; )Lorg/eclipse/jface/text/IInformationControl;+20
j  org.eclipse.jface.text.AbstractInformationControlManager.getInformationControl()Lorg/eclipse/jface/text/IInformationControl;+146
j  org.eclipse.jface.text.AbstractInformationControlManager.internalShowInformationControl(Lorg/eclipse/swt/graphics/Rectangle;Ljava/lang/Object; )V+1
j  org.eclipse.jface.text.AbstractInformationControlManager.presentInformation()V+70
j  org.eclipse.jface.text.AbstractHoverInformationControlManager.presentInformation()V+64
j  org.eclipse.jface.text.TextViewerHoverManager.doPresentInformation()V+1
j  org.eclipse.jface.text.TextViewerHoverManager$5.run()V+4
J  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
J  org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display; )V
v  ~OSRAdapter
j  org.eclipse.ui.internal.Workbench.runUI()I+225
j  org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor; )I+11
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor; )I+2
j  org.eclipse.ui.internal.ide.IDEApplication.run(Ljava/lang/Object; )Ljava/lang/Object;+76
j  org.eclipse.core.internal.runtime.PlatformActivator$1.run(Ljava/lang/Object; )Ljava/lang/Object;+219
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object; )Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object; )Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object; )Ljava/lang/Object;+135
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable; )Ljava/lang/Object;+60
v  ~StubRoutines::call_stub
V  [libjvm.so+0x17b1ac]
V  [libjvm.so+0x28fc18]
V  [libjvm.so+0x17afdf]
V  [libjvm.so+0x2ba08c]
V  [libjvm.so+0x2bcd9a]
V  [libjvm.so+0x1ef452]
C  [libjava.so+0x137b4]  Java_sun_reflect_NativeMethodAccessorImpl_invoke0+0x34
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+111
j  org.eclipse.core.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL;)V+181
j  org.eclipse.core.launcher.Main.basicRun([Ljava/lang/String; )V+107
j  org.eclipse.core.launcher.Main.run([Ljava/lang/String; )I+4
j  org.eclipse.core.launcher.Main.main([Ljava/lang/String; )V+10
v  ~StubRoutines::call_stub
V  [libjvm.so+0x17b1ac]
V  [libjvm.so+0x28fc18]
V  [libjvm.so+0x17afdf]
V  [libjvm.so+0x1a5bb2]
V  [libjvm.so+0x196dc2]
C  [java+0x1873]
C  [libc.so.6+0x16050]  __libc_start_main+0xe0

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  org.eclipse.swt.internal.mozilla.XPCOM.NS_InitEmbedding(II)I+0
j  org.eclipse.swt.browser.Browser.<init>(Lorg/eclipse/swt/widgets/Composite;I)V+392
j  org.eclipse.jdt.internal.ui.text.java.hover.BrowserInformationControl.isAvailable(Lorg/eclipse/swt/widgets/Composite; )Z+29
j  org.eclipse.jdt.internal.ui.text.java.hover.JavadocHover$2.doCreateInformationControl(Lorg/eclipse/swt/widgets/Shell; )Lorg/eclipse/jface/text/IInformationControl;+1
j  org.eclipse.jdt.internal.ui.text.java.hover.AbstractReusableInformationControlCreator.createInformationControl(Lorg/eclipse/swt/widgets/Shell; )Lorg/eclipse/jface/text/IInformationControl;+20
j  org.eclipse.jface.text.AbstractInformationControlManager.getInformationControl()Lorg/eclipse/jface/text/IInformationControl;+146
j  org.eclipse.jface.text.AbstractInformationControlManager.internalShowInformationControl(Lorg/eclipse/swt/graphics/Rectangle;Ljava/lang/Object; )V+1
j  org.eclipse.jface.text.AbstractInformationControlManager.presentInformation()V+70
j  org.eclipse.jface.text.AbstractHoverInformationControlManager.presentInformation()V+64
j  org.eclipse.jface.text.TextViewerHoverManager.doPresentInformation()V+1
j  org.eclipse.jface.text.TextViewerHoverManager$5.run()V+4
J  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z
J  org.eclipse.swt.widgets.Display.readAndDispatch()Z
J  org.eclipse.ui.internal.Workbench.runEventLoop(Lorg/eclipse/jface/window/Window$IExceptionHandler;Lorg/eclipse/swt/widgets/Display; )V
v  ~OSRAdapter
j  org.eclipse.ui.internal.Workbench.runUI()I+225
j  org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor; )I+11
j  org.eclipse.ui.PlatformUI.createAndRunWorkbench(Lorg/eclipse/swt/widgets/Display;Lorg/eclipse/ui/application/WorkbenchAdvisor; )I+2
j  org.eclipse.ui.internal.ide.IDEApplication.run(Ljava/lang/Object; )Ljava/lang/Object;+76
j  org.eclipse.core.internal.runtime.PlatformActivator$1.run(Ljava/lang/Object; )Ljava/lang/Object;+219
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Ljava/lang/Object; )Ljava/lang/Object;+103
j  org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Ljava/lang/Object; )Ljava/lang/Object;+29
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run(Ljava/lang/Object; )Ljava/lang/Object;+135
j  org.eclipse.core.runtime.adaptor.EclipseStarter.run([Ljava/lang/String;Ljava/lang/Runnable; )Ljava/lang/Object;+60
v  ~StubRoutines::call_stub
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+87
j  sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+6
j  java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object; )Ljava/lang/Object;+111
j  org.eclipse.core.launcher.Main.invokeFramework([Ljava/lang/String;[Ljava/net/URL; )V+181
j  org.eclipse.core.launcher.Main.basicRun([Ljava/lang/String; )V+107
j  org.eclipse.core.launcher.Main.run([Ljava/lang/String; )I+4
j  org.eclipse.core.launcher.Main.main([Ljava/lang/String; )V+10
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x084ac200 JavaThread "Worker-23" [_thread_blocked, id=11204]
  0x0848c3d8 JavaThread "Process monitor" daemon [_thread_blocked, id=11160]
  0x0848b778 JavaThread "Input Stream Monitor" daemon [_thread_blocked, id=11159]
  0x0848abb8 JavaThread "Output Stream Monitor" daemon [_thread_in_native, id=11158]
  0x0848a088 JavaThread "Output Stream Monitor" daemon [_thread_in_native, id=11157]
  0x08489340 JavaThread "process reaper" daemon [_thread_in_native, id=11155]
  0xae89bb78 JavaThread "Worker-20" [_thread_blocked, id=11150]
  0xa5b3b0b8 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=11101]
  0x08405440 JavaThread "Worker-13" [_thread_blocked, id=11071]
  0xa91c1ba0 JavaThread "org.eclipse.jdt.internal.ui.text.JavaReconciler" daemon [_thread_blocked, id=11059]
  0xa9122880 JavaThread "org.eclipse.jdt.internal.ui.text.JavaReconciler" daemon [_thread_blocked, id=11040]
  0xaac10850 JavaThread "Update Run Page Action" [_thread_blocked, id=10528]
  0xace74b78 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=10527]
  0xb20378d0 JavaThread "Timer-0" daemon [_thread_blocked, id=10526]
  0xb1a95780 JavaThread "Java indexing" daemon [_thread_blocked, id=10468]
  0xb191e130 JavaThread "Start Level Event Dispatcher" daemon [_thread_blocked, id=10464]
  0xb191f3b0 JavaThread "Framework Event Dispatcher" daemon [_thread_blocked, id=10463]
  0xb191f798 JavaThread "State Data Manager" daemon [_thread_blocked, id=10462]
  0x080a6c90 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=10458]
  0x080a5858 JavaThread "CompilerThread0" daemon [_thread_blocked, id=10457]
  0x080a48f8 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=10456]
  0x0809ea10 JavaThread "Finalizer" daemon [_thread_blocked, id=10455]
  0x0809cbb0 JavaThread "Reference Handler" daemon [_thread_blocked, id=10454]
=>0x0805ceb8 JavaThread "main" [_thread_in_native, id=10452]

Other Threads:
  0x0809b728 VMThread [id=10453]
  0xb2000da8 WatcherThread [id=10459]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 36288K, used 12130K [0x6c9d0000, 0x6f130000, 0x6f130000)
  eden space 32256K,  33% used [0x6c9d0000, 0x6d449fa0, 0x6e950000)
  from space 4032K,  34% used [0x6ed40000, 0x6ee9ec38, 0x6f130000)
  to   space 4032K,   0% used [0x6e950000, 0x6e950000, 0x6ed40000)
 tenured generation   total 483968K, used 42024K [0x6f130000, 0x8c9d0000, 0x8c9d0000)
   the space 483968K,   8% used [0x6f130000, 0x71a3a2a8, 0x71a3a400, 0x8c9d0000)
 compacting perm gen  total 50176K, used 49921K [0x8c9d0000, 0x8fad0000, 0x909d0000)
   the space 50176K,  99% used [0x8c9d0000, 0x8fa90420, 0x8fa90600, 0x8fad0000)
    ro space 8192K,  68% used [0x909d0000, 0x90f525e0, 0x90f52600, 0x911d0000)
    rw space 12288K,  48% used [0x911d0000, 0x917a06e0, 0x917a0800, 0x91dd0000)

Dynamic libraries:
08048000-08057000 r-xp 00000000 08:08 1457853    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/bin/java
08057000-08059000 rwxp 0000e000 08:08 1457853    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/bin/java
08059000-08852000 rwxp 08059000 00:00 0          [heap]
6c9d0000-8fad0000 rwxp 6c9d0000 00:00 0 
8fad0000-909d0000 rwxp 8fad0000 00:00 0 
909d0000-90f53000 r-xs 00001000 08:08 1474185    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/classes.jsa
90f53000-911d0000 rwxp 90f53000 00:00 0 
911d0000-917a1000 rwxp 00584000 08:08 1474185    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/classes.jsa
917a1000-91dd0000 rwxp 917a1000 00:00 0 
91dd0000-91ea0000 rwxp 00b55000 08:08 1474185    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/classes.jsa
91ea0000-921d0000 rwxp 91ea0000 00:00 0 
921d0000-921d4000 r-xs 00c25000 08:08 1474185    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/classes.jsa
921d4000-925d0000 rwxp 921d4000 00:00 0 
a4444000-a444b000 r-xp 00000000 08:08 1341543    /usr/lib/firefox/components/libimgicon.so
a444b000-a444c000 rwxp 00007000 08:08 1341543    /usr/lib/firefox/components/libimgicon.so
a444c000-a4497000 r-xp 00000000 08:08 1341578    /usr/lib/firefox/components/libxpconnect.so
a4497000-a449b000 rwxp 0004b000 08:08 1341578    /usr/lib/firefox/components/libxpconnect.so
a449b000-a44d1000 r-xp 00000000 08:08 1341542    /usr/lib/firefox/components/libi18n.so
a44d1000-a44d4000 rwxp 00035000 08:08 1341542    /usr/lib/firefox/components/libi18n.so
a44d4000-a4507000 r-xp 00000000 08:08 1341579    /usr/lib/firefox/components/libxpinstall.so
a4507000-a450a000 rwxp 00033000 08:08 1341579    /usr/lib/firefox/components/libxpinstall.so
a450a000-a450f000 r-xp 00000000 08:08 1341577    /usr/lib/firefox/components/libxpcom_compat_c.so
a450f000-a4510000 rwxp 00005000 08:08 1341577    /usr/lib/firefox/components/libxpcom_compat_c.so
a4510000-a4514000 r-xp 00000000 08:08 1341530    /usr/lib/firefox/components/libcommandlines.so
a4514000-a4515000 rwxp 00004000 08:08 1341530    /usr/lib/firefox/components/libcommandlines.so
a4515000-a4518000 r-xp 00000000 08:08 1341556    /usr/lib/firefox/components/libpermissions.so
a4518000-a4519000 rwxp 00002000 08:08 1341556    /usr/lib/firefox/components/libpermissions.so
a4519000-a452b000 r-xp 00000000 08:08 1341531    /usr/lib/firefox/components/libcomposer.so
a452b000-a452d000 rwxp 00011000 08:08 1341531    /usr/lib/firefox/components/libcomposer.so
a452d000-a4551000 r-xp 00000000 08:08 1341544    /usr/lib/firefox/components/libimglib2.so
a4551000-a4553000 rwxp 00023000 08:08 1341544    /usr/lib/firefox/components/libimglib2.so
a4553000-a45ec000 r-xp 00000000 08:08 1341534    /usr/lib/firefox/components/libeditor.so
a45ec000-a45f0000 rwxp 00099000 08:08 1341534    /usr/lib/firefox/components/libeditor.so
a45f0000-a461a000 r-xp 00000000 08:08 1341535    /usr/lib/firefox/components/libembedcomponents.so
a461a000-a461c000 rwxp 0002a000 08:08 1341535    /usr/lib/firefox/components/libembedcomponents.so
a461c000-a462b000 r-xp 00000000 08:08 1341529    /usr/lib/firefox/components/libchrome.so
a462b000-a462c000 rwxp 0000f000 08:08 1341529    /usr/lib/firefox/components/libchrome.so
a462c000-a4634000 r-xp 00000000 08:08 1341571    /usr/lib/firefox/components/libucvmath.so
a4634000-a4635000 rwxp 00008000 08:08 1341571    /usr/lib/firefox/components/libucvmath.so
a4635000-a464b000 r-xp 00000000 08:08 1309525    /usr/lib/firefox/libjsj.so
a464b000-a464c000 rwxp 00016000 08:08 1309525    /usr/lib/firefox/libjsj.so
a464c000-a4660000 r-xp 00000000 08:08 1341555    /usr/lib/firefox/components/liboji.so
a4660000-a4661000 rwxp 00014000 08:08 1341555    /usr/lib/firefox/components/liboji.so
a4661000-a468a000 r-xp 00000000 08:08 1341540    /usr/lib/firefox/components/libgkplugin.so
a468a000-a468c000 rwxp 00028000 08:08 1341540    /usr/lib/firefox/components/libgkplugin.so
a468c000-a46af000 r-xp 00000000 08:08 1341563    /usr/lib/firefox/components/libsearchservice.so
a46af000-a46b0000 rwxp 00022000 08:08 1341563    /usr/lib/firefox/components/libsearchservice.so
a46b0000-a4707000 r-xp 00000000 08:08 1341565    /usr/lib/firefox/components/libstoragecomps.so
a4707000-a4709000 rwxp 00057000 08:08 1341565    /usr/lib/firefox/components/libstoragecomps.so
a4709000-a4762000 r-xp 00000000 08:08 1341541    /usr/lib/firefox/components/libhtmlpars.so
a4762000-a476a000 rwxp 00058000 08:08 1341541    /usr/lib/firefox/components/libhtmlpars.so
a476a000-a47bb000 r-xp 00000000 08:08 1341568    /usr/lib/firefox/components/libtransformiix.so
a47bb000-a47bf000 rwxp 00050000 08:08 1341568    /usr/lib/firefox/components/libtransformiix.so
a47bf000-a47d8000 r-xp 00000000 08:08 1309536    /usr/lib/firefox/libxpcom_compat.so
a47d8000-a47d9000 rwxp 00018000 08:08 1309536    /usr/lib/firefox/libxpcom_compat.so
a47d9000-a47da000 rwxp a47d9000 00:00 0 
a47da000-a4813000 r-xp 00000000 08:08 1341526    /usr/lib/firefox/components/libbrowsercomps.so
a4813000-a4816000 rwxp 00038000 08:08 1341526    /usr/lib/firefox/components/libbrowsercomps.so
a4816000-a482a000 r-xp 00000000 08:08 1341523    /usr/lib/firefox/components/libappcomps.so
a482a000-a482b000 rwxp 00014000 08:08 1341523    /usr/lib/firefox/components/libappcomps.so
a482b000-a48e7000 r-xp 00000000 08:08 1341570    /usr/lib/firefox/components/libuconv.so
a48e7000-a48ed000 rwxp 000bc000 08:08 1341570    /usr/lib/firefox/components/libuconv.so
a48ed000-a48f7000 rwxp a48ed000 00:00 0 
a48f7000-a48fd000 r-xp 00000000 08:08 1308961    /usr/lib/libpangoxft-1.0.so.0.1800.2
a48fd000-a48fe000 rwxp 00005000 08:08 1308961    /usr/lib/libpangoxft-1.0.so.0.1800.2
a48fe000-a4902000 r-xp 00000000 08:08 1341549    /usr/lib/firefox/components/libmozgnome.so
a4902000-a4903000 rwxp 00003000 08:08 1341549    /usr/lib/firefox/components/libmozgnome.so
a4903000-a4908000 r-xp 00000000 08:08 1341576    /usr/lib/firefox/components/libxmlextras.so
a4908000-a4909000 rwxp 00004000 08:08 1341576    /usr/lib/firefox/components/libxmlextras.so
a4909000-a4941000 r-xp 00000000 08:08 1341537    /usr/lib/firefox/components/libgfx_gtk.so
a4941000-a4944000 rwxp 00038000 08:08 1341537    /usr/lib/firefox/components/libgfx_gtk.so
a4944000-a49b8000 r-xp 00000000 08:08 1341574    /usr/lib/firefox/components/libwebsrvcs.so
a49b8000-a49be000 rwxp 00074000 08:08 1341574    /usr/lib/firefox/components/libwebsrvcs.so
a49be000-a49c8000 r-xp 00000000 08:08 1341552    /usr/lib/firefox/components/libnecko2.so
a49c8000-a49c9000 rwxp 0000a000 08:08 1341552    /usr/lib/firefox/components/libnecko2.so
a49c9000-a4a0e000 r-xp 00000000 08:08 1341567    /usr/lib/firefox/components/libtoolkitcomps.so
a4a0e000-a4a11000 rwxp 00045000 08:08 1341567    /usr/lib/firefox/components/libtoolkitcomps.so
a4a11000-a4a14000 r-xp 00000000 08:08 1341527    /usr/lib/firefox/components/libbrowserdirprovider.so
a4a14000-a4a15000 rwxp 00002000 08:08 1341527    /usr/lib/firefox/components/libbrowserdirprovider.so
a4a15000-a4a26000 r-xp 00000000 08:08 1308377    /usr/lib/libXft.so.2.1.2
a4a26000-a4a27000 rwxp 00010000 08:08 1308377    /usr/lib/libXft.so.2.1.2
a4a2a000-a4a31000 r-xp 00000000 08:08 1341559    /usr/lib/firefox/components/libpippki.so
a4a31000-a4a32000 rwxp 00006000 08:08 1341559    /usr/lib/firefox/components/libpippki.so
a4a32000-a4a72000 r-xp 00000000 08:08 1341538    /usr/lib/firefox/components/libgfxps.so
a4a72000-a4a74000 rwxp 00040000 08:08 1341538    /usr/lib/firefox/components/libgfxps.so
a4a74000-a4ac0000 r-xp 00000000 08:08 1341533    /usr/lib/firefox/components/libdocshell.so
a4ac0000-a4ac4000 rwxp 0004c000 08:08 1341533    /usr/lib/firefox/components/libdocshell.so
a4ac4000-a4ac9000 r-xp 00000000 08:08 1341524    /usr/lib/firefox/components/libauth.so
a4ac9000-a4aca000 rwxp 00004000 08:08 1341524    /usr/lib/firefox/components/libauth.so
a4aca000-a4ae0000 r-xp 00000000 08:08 1341554    /usr/lib/firefox/components/libnsappshell.so
a4ae0000-a4ae2000 rwxp 00015000 08:08 1341554    /usr/lib/firefox/components/libnsappshell.so
a4ae2000-a4ae9000 r-xp 00000000 08:08 1341557    /usr/lib/firefox/components/libpipboot.so
a4ae9000-a4aea000 rwxp 00006000 08:08 1341557    /usr/lib/firefox/components/libpipboot.so
a4aea000-a4b54000 r-xp 00000000 08:08 1341522    /usr/lib/firefox/components/libaccessibility.so
a4b54000-a4b66000 rwxp 00069000 08:08 1341522    /usr/lib/firefox/components/libaccessibility.so
a4b66000-a4b8d000 r-xp 00000000 08:08 1341561    /usr/lib/firefox/components/librdf.so
a4b8d000-a4b8f000 rwxp 00026000 08:08 1341561    /usr/lib/firefox/components/librdf.so
a4b8f000-a4ba0000 r-xp 00000000 08:08 1341573    /usr/lib/firefox/components/libwebbrwsr.so
a4ba0000-a4ba2000 rwxp 00010000 08:08 1341573    /usr/lib/firefox/components/libwebbrwsr.so
a4ba2000-a4baa000 r-xp 00000000 08:08 1341532    /usr/lib/firefox/components/libcookie.so
a4baa000-a4bab000 rwxp 00007000 08:08 1341532    /usr/lib/firefox/components/libcookie.so
a4bab000-a4bb0000 r-xp 00000000 08:08 1341569    /usr/lib/firefox/components/libtxmgr.so
a4bb0000-a4bb1000 rwxp 00004000 08:08 1341569    /usr/lib/firefox/components/libtxmgr.so
a4bb1000-a4bc0000 r-xp 00000000 08:08 1341564    /usr/lib/firefox/components/libspellchecker.so
a4bc0000-a4bc1000 rwxp 0000f000 08:08 1341564    /usr/lib/firefox/components/libspellchecker.so
a4bc1000-a4bd4000 r-xp 00000000 08:08 1341528    /usr/lib/firefox/components/libcaps.so
a4bd4000-a4bd5000 rwxp 00013000 08:08 1341528    /usr/lib/firefox/components/libcaps.so
a4bd5000-a4c08000 r-xp 00000000 08:08 1341547    /usr/lib/firefox/components/libmork.so
a4c08000-a4c0b000 rwxp 00032000 08:08 1341547    /usr/lib/firefox/components/libmork.so
a4c0b000-a4c19000 r-xp 00000000 08:08 1341560    /usr/lib/firefox/components/libpref.so
a4c19000-a4c1a000 rwxp 0000e000 08:08 1341560    /usr/lib/firefox/components/libpref.so
a4c1a000-a4c1f000 r-xp 00000000 08:08 1341566    /usr/lib/firefox/components/libsystem-pref.so
a4c1f000-a4c20000 rwxp 00004000 08:08 1341566    /usr/lib/firefox/components/libsystem-pref.so
a4c20000-a4c32000 r-xp 00000000 08:08 1341572    /usr/lib/firefox/components/libuniversalchardet.so
a4c32000-a4c3c000 rwxp 00012000 08:08 1341572    /usr/lib/firefox/components/libuniversalchardet.so
a4c3c000-a4c72000 r-xp 00000000 08:08 1308813    /usr/lib/libhunspell-1.1.so.0.0.0
a4c72000-a4c76000 rwxp 00036000 08:08 1308813    /usr/lib/libhunspell-1.1.so.0.0.0
a4c76000-a5196000 r-xp 00000000 08:08 1341539    /usr/lib/firefox/components/libgklayout.so
a5196000-a51f4000 rwxp 00520000 08:08 1341539    /usr/lib/firefox/components/libgklayout.so
a51f4000-a51fc000 rwxp a51f4000 00:00 0 
a51fc000-a5245000 r-xp 00000000 08:08 1309050    /usr/lib/libsoftokn3.so.0d
a5245000-a5249000 rwxp 00048000 08:08 1309050    /usr/lib/libsoftokn3.so.0d
a5249000-a52b5000 r-xp 00000000 08:08 1308927    /usr/lib/libnss3.so.0d
a52b5000-a52ba000 rwxp 0006c000 08:08 1308927    /usr/lib/libnss3.so.0d
a52ba000-a52db000 r-xp 00000000 08:08 1309044    /usr/lib/libsmime3.so.0d
a52db000-a52dd000 rwxp 00021000 08:08 1309044    /usr/lib/libsmime3.so.0d
a52dd000-a5384000 r-xp 00000000 08:08 1309526    /usr/lib/firefox/libmozjs.so
a5384000-a5389000 rwxp 000a7000 08:08 1309526    /usr/lib/firefox/libmozjs.so
a5389000-a53e3000 r-xp 00000000 08:08 1341558    /usr/lib/firefox/components/libpipnss.so
a53e3000-a53e7000 rwxp 0005a000 08:08 1341558    /usr/lib/firefox/components/libpipnss.so
a53e7000-a5434000 r-xp 00000000 08:08 1308397    /usr/lib/libXt.so.6.0.0
a5434000-a5438000 rwxp 0004c000 08:08 1308397    /usr/lib/libXt.so.6.0.0
a5438000-a54f8000 r-xp 00000000 08:08 1341551    /usr/lib/firefox/components/libnecko.so
a54f8000-a5500000 rwxp 000c0000 08:08 1341551    /usr/lib/firefox/components/libnecko.so
a5500000-a5572000 rwxp a5500000 00:00 0 
a5572000-a5600000 ---p a5572000 00:00 0 
a5603000-a560a000 r-xp 00000000 08:08 1341525    /usr/lib/firefox/components/libautoconfig.so
a560a000-a560b000 rwxp 00006000 08:08 1341525    /usr/lib/firefox/components/libautoconfig.so
a560b000-a561c000 r-xp 00000000 08:08 1341545    /usr/lib/firefox/components/libjar50.so
a561c000-a561d000 rwxp 00011000 08:08 1341545    /usr/lib/firefox/components/libjar50.so
a561d000-a5642000 r-xp 00000000 08:08 1309060    /usr/lib/libssl3.so.0d
a5642000-a5644000 rwxp 00024000 08:08 1309060    /usr/lib/libssl3.so.0d
a5644000-a5661000 r-xp 00000000 08:08 1309522    /usr/lib/firefox/libgkgfx.so
a5661000-a5663000 rwxp 0001c000 08:08 1309522    /usr/lib/firefox/libgkgfx.so
a5663000-a5705000 r-xp 00000000 08:08 1309537    /usr/lib/firefox/libxpcom_core.so
a5705000-a570d000 rwxp 000a1000 08:08 1309537    /usr/lib/firefox/libxpcom_core.so
a570d000-a57f5000 r-xp 00000000 08:08 1309064    /usr/lib/libstdc++.so.6.0.9
a57f5000-a57f8000 r-xp 000e8000 08:08 1309064    /usr/lib/libstdc++.so.6.0.9
a57f8000-a57fa000 rwxp 000eb000 08:08 1309064    /usr/lib/libstdc++.so.6.0.9
a57fa000-a5900000 rwxp a57fa000 00:00 0 
a5903000-a5916000 r-xp 00000000 08:08 1341546    /usr/lib/firefox/components/libjsd.so
a5916000-a5917000 rwxp 00012000 08:08 1341546    /usr/lib/firefox/components/libjsd.so
a5917000-a591c000 r-xp 00000000 08:08 1341553    /usr/lib/firefox/components/libnkgnomevfs.so
a591c000-a591d000 rwxp 00004000 08:08 1341553    /usr/lib/firefox/components/libnkgnomevfs.so
a591d000-a5948000 r-xp 00000000 08:08 1341575    /usr/lib/firefox/components/libwidget_gtk2.so
a5948000-a594c000 rwxp 0002b000 08:08 1341575    /usr/lib/firefox/components/libwidget_gtk2.so
a594c000-a597a000 r-xp 00000000 08:08 1308926    /usr/lib/libnspr4.so.0d
a597a000-a597b000 rwxp 0002e000 08:08 1308926    /usr/lib/libnspr4.so.0d
a597b000-a597d000 rwxp a597b000 00:00 0 
a597d000-a5980000 rwxp a597d000 00:00 0 
a5980000-a59fe000 rwxp a5980000 00:00 0 
a59fe000-a5a01000 rwxp a59fe000 00:00 0 
a5a01000-a5a7f000 rwxp a5a01000 00:00 0 
a5a7f000-a5a82000 ---p a5a7f000 00:00 0 
a5a82000-a5c00000 rwxp a5a82000 00:00 0 
a5c00000-a5c04000 r-xp 00000000 08:08 1341550    /usr/lib/firefox/components/libmyspell.so
a5c04000-a5c05000 rwxp 00004000 08:08 1341550    /usr/lib/firefox/components/libmyspell.so
a5c05000-a5c0b000 r-xp 00000000 08:08 1341536    /usr/lib/firefox/components/libfileview.so
a5c0b000-a5c0c000 rwxp 00005000 08:08 1341536    /usr/lib/firefox/components/libfileview.so
a5c0c000-a5c16000 r-xp 00000000 08:01 439843     /lib/libgcc_s.so.1
a5c16000-a5c17000 rwxp 0000a000 08:01 439843     /lib/libgcc_s.so.1
a5c17000-a5c19000 r-xp 00000000 08:08 1309521    /usr/lib/firefox/libgfxpsshar.so
a5c19000-a5c1a000 rwxp 00001000 08:08 1309521    /usr/lib/firefox/libgfxpsshar.so
a5c1a000-a5c1d000 r-xp 00000000 08:08 1309524    /usr/lib/firefox/libgtkxtbin.so
a5c1d000-a5c1e000 rwxp 00003000 08:08 1309524    /usr/lib/firefox/libgtkxtbin.so
a5c1e000-a5c21000 r-xp 00000000 08:08 1341562    /usr/lib/firefox/components/libremoteservice.so
a5c21000-a5c22000 rwxp 00002000 08:08 1341562    /usr/lib/firefox/components/libremoteservice.so
a5c22000-a5c35000 r-xp 00000000 08:07 213204     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-mozilla-gtk-3235.so
a5c35000-a5c36000 rwxp 00012000 08:07 213204     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-mozilla-gtk-3235.so
a5c36000-a5c37000 ---p a5c36000 00:00 0 
a5c37000-a6437000 rwxp a5c37000 00:00 0 
a6437000-a6438000 ---p a6437000 00:00 0 
a6438000-a6c38000 rwxp a6438000 00:00 0 
a6c38000-a6c39000 ---p a6c38000 00:00 0 
a6c39000-a7439000 rwxp a6c39000 00:00 0 
a7439000-a743a000 ---p a7439000 00:00 0 
a743a000-a7c3a000 rwxp a743a000 00:00 0 
a7c3a000-a7e31000 r-xp 00000000 08:08 1685385    /usr/share/icons/hicolor/icon-theme.cache
a7e31000-a8590000 r-xp 00000000 08:08 1687639    /usr/share/icons/gnome/icon-theme.cache
a8590000-a863b000 r-xp 00000000 08:08 1687636    /usr/share/icons/Tangerine/icon-theme.cache
a863b000-a87a1000 r-xp 00000000 08:08 1687180    /usr/share/icons/Human/icon-theme.cache
a87a1000-a8f00000 r-xp 00000000 08:08 1687639    /usr/share/icons/gnome/icon-theme.cache
a8f00000-a9000000 rwxp a8f00000 00:00 0 
a9000000-a9002000 r-xp 00000000 08:08 1309774    /usr/lib/gconv/UTF-16.so
a9002000-a9004000 rwxp 00001000 08:08 1309774    /usr/lib/gconv/UTF-16.so
a9004000-a9008000 r-xp 00000000 08:07 213209     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-mozilla18-profile-gtk-3235.so
a9008000-a9009000 rwxp 00003000 08:07 213209     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-mozilla18-profile-gtk-3235.so
a9009000-a9015000 r-xs 00000000 08:07 98790      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.prompting.knowledgebase_8.0.0/lib/dtdparser121.jar
a9015000-a9074000 r-xs 00000000 08:07 1841221    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.dtd.core_1.1.0.v200606141450.jar
a9074000-a907b000 r-xp 00000000 08:08 1309082    /usr/lib/libtrackerclient.so.0.0.0
a907b000-a907c000 rwxp 00006000 08:08 1309082    /usr/lib/libtrackerclient.so.0.0.0
a907e000-a9087000 r-xs 00000000 08:07 1841204    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.internet.cache_1.0.101.v200606130645.jar
a9087000-a9096000 r-xp 00000000 08:01 439815     /lib/libbz2.so.1.0.4
a9096000-a9097000 rwxp 0000f000 08:01 439815     /lib/libbz2.so.1.0.4
a9097000-a90c9000 r-xp 00000000 08:08 1308478    /usr/lib/libcroco-0.6.so.3.0.1
a90c9000-a90cc000 rwxp 00031000 08:08 1308478    /usr/lib/libcroco-0.6.so.3.0.1
a90cc000-a90fc000 r-xp 00000000 08:08 1308720    /usr/lib/libgsf-1.so.114.0.7
a90fc000-a90ff000 rwxp 0002f000 08:08 1308720    /usr/lib/libgsf-1.so.114.0.7
a90ff000-a91ff000 rwxp a90ff000 00:00 0 
a91ff000-a9200000 ---p a91ff000 00:00 0 
a9200000-a9204000 r-xp 00000000 08:08 1308979    /usr/lib/libplc4.so.0d
a9204000-a9205000 rwxp 00003000 08:08 1308979    /usr/lib/libplc4.so.0d
a9205000-a9207000 r-xp 00000000 08:08 1308980    /usr/lib/libplds4.so.0d
a9207000-a9208000 rwxp 00001000 08:08 1308980    /usr/lib/libplds4.so.0d
a9208000-a9238000 r-xp 00000000 08:08 1309018    /usr/lib/librsvg-2.so.2.18.2
a9238000-a9239000 rwxp 00030000 08:08 1309018    /usr/lib/librsvg-2.so.2.18.2
a9239000-a9243000 r-xp 00000000 08:08 1357631    /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
a9243000-a9244000 rwxp 00009000 08:08 1357631    /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
a9244000-a92c6000 r-xs 00000000 08:07 167016     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.team.cvs.core_3.2.1.M200608161750.jar
a92c6000-a9300000 r-xs 00000000 08:07 167017     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.forms_3.2.0.v20060602.jar
a9300000-a9400000 rwxp a9300000 00:00 0 
a9402000-a9404000 r-xp 00000000 08:08 1309535    /usr/lib/firefox/libxpcom.so
a9404000-a9405000 rwxp 00002000 08:08 1309535    /usr/lib/firefox/libxpcom.so
a9405000-a9424000 r-xs 00000000 08:07 98926      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.ui_3.0.0/exadel_ui.jar
a9424000-a961b000 r-xp 00000000 08:08 1685385    /usr/share/icons/hicolor/icon-theme.cache
a961b000-a96c6000 r-xp 00000000 08:08 1687636    /usr/share/icons/Tangerine/icon-theme.cache
a96c6000-a982c000 r-xp 00000000 08:08 1687180    /usr/share/icons/Human/icon-theme.cache
a982c000-a982f000 ---p a982c000 00:00 0 
a982f000-a98ad000 rwxp a982f000 00:00 0 
a98ad000-a98b0000 ---p a98ad000 00:00 0 
a98b0000-a992e000 rwxp a98b0000 00:00 0 
a992e000-a9931000 ---p a992e000 00:00 0 
a9931000-a99af000 rwxp a9931000 00:00 0 
a99af000-a99b2000 rwxp a99af000 00:00 0 
a99b2000-a9a30000 rwxp a99b2000 00:00 0 
a9a30000-a9a33000 rwxp a9a30000 00:00 0 
a9a33000-a9ab1000 rwxp a9a33000 00:00 0 
a9ab1000-a9ab4000 rwxp a9ab1000 00:00 0 
a9ab4000-a9b32000 rwxp a9ab4000 00:00 0 
a9b32000-a9b35000 ---p a9b32000 00:00 0 
a9b35000-a9bb3000 rwxp a9b35000 00:00 0 
a9bb3000-a9bb6000 ---p a9bb3000 00:00 0 
a9bb6000-a9c34000 rwxp a9bb6000 00:00 0 
a9c34000-a9c46000 r-xs 00000000 08:07 1840924    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.server.core_1.0.102.v200606130315.jar
a9c46000-a9c6f000 r-xs 00000000 08:07 1841184    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.server.tomcat.core_1.0.102.v200606130315.jar
a9c6f000-a9c72000 ---p a9c6f000 00:00 0 
a9c72000-a9cf0000 rwxp a9c72000 00:00 0 
a9cf0000-a9d4c000 r-xs 00000000 08:07 212116     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.junit_3.2.1.r321_v20060810/junitsupport.jar
a9d4c000-a9d4f000 rwxp a9d4c000 00:00 0 
a9d4f000-a9dcd000 rwxp a9d4f000 00:00 0 
a9dcd000-a9e82000 r-xs 00000000 08:07 212121     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.debug_3.2.1.r321_v20060731/jdimodel.jar
a9e82000-a9eea000 r-xs 00000000 08:07 167006     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ltk.ui.refactoring_3.2.1.r321_v20060726.jar
a9eea000-a9f25000 r-xs 00000000 08:07 167002     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ltk.core.refactoring_3.2.1.r321_v20060823.jar
a9f25000-a9f28000 ---p a9f25000 00:00 0 
a9f28000-a9fa6000 rwxp a9f28000 00:00 0 
a9fa6000-a9fc4000 r-xs 00000000 08:07 1841100    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.ui_1.1.0.v200606142122.jar
a9fc4000-a9fd0000 r-xs 00000000 08:07 1841102    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.web_1.1.0.v200606222043.jar
a9fd0000-aa00c000 r-xs 00000000 08:07 1841255    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee.webservice_1.1.0.v200606130315.jar
aa00c000-aa02a000 r-xs 00000000 08:07 1841142    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.emfworkbench.integration_1.1.0.v200606130645.jar
aa02a000-aa068000 r-xs 00000000 08:07 1841238    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.modulecore_1.1.0.v200606222043.jar
aa068000-aa087000 r-xs 00000000 08:07 1841085    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.frameworks.ui_1.1.0.v200606130645.jar
aa087000-aa0b1000 r-xs 00000000 08:07 1841267    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.emf.ecore.xmi_2.2.0.v200606271057.jar
aa0b1000-aa0de000 r-xs 00000000 08:07 1841151    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.emf_1.1.0.v200606130645.jar
aa0de000-aa289000 r-xs 00000000 08:07 1841097    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee.core_1.1.0.v200606130315.jar
aa289000-aa3d9000 r-xs 00000000 08:07 1841160    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee_1.1.0.v200606222043.jar
aa3d9000-aa3ed000 r-xs 00000000 08:07 1841203    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.equinox.servlet.api_1.0.0.v20060601.jar
aa3ed000-aa43a000 r-xs 00000000 08:07 166978     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.apt.core_3.2.1.R32x_v20060822-2100.jar
aa43a000-aa453000 r-xs 00000000 08:07 97873      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.beans.core_1.3.2/beans-core.jar
aa453000-aa579000 r-xs 00000000 08:07 81608      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/xercesImpl.jar
aa579000-aa5a9000 r-xs 00000000 08:07 81612      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/xml-apis.jar
aa5a9000-aa5e2000 r-xs 00000000 08:07 81613      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/spring-beans.jar
aa5e2000-aa600000 r-xs 00000000 08:07 81607      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/spring-core.jar
aa600000-aa700000 rwxp aa600000 00:00 0 
aa700000-aa70d000 r-xs 00000000 08:07 212125     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.debug_3.2.1.r321_v20060731/jdi.jar
aa70d000-aa71c000 r-xs 00000000 08:07 1841194    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.server.ui_1.0.102.v200606130315.jar
aa71c000-aa724000 r-xs 00000000 08:07 81610      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/core.jar
aa724000-aa749000 r-xs 00000000 08:07 97830      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.beans.ui_1.3.1/beans-ui.jar
aa749000-aa763000 r-xs 00000000 08:07 1841056    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.frameworks_1.1.0.v200606130645.jar
aa763000-aa791000 r-xs 00000000 08:07 1841131    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.validation_1.1.0.v200606130645.jar
aa791000-aa81d000 r-xs 00000000 08:07 167030     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.update.core_3.2.1.v20092006.jar
aa81d000-aa820000 ---p aa81d000 00:00 0 
aa820000-aa89e000 rwxp aa820000 00:00 0 
aa89e000-aa8c6000 r-xs 00000000 08:07 1841146    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.project.facet.core_1.1.0.v200606130645.jar
aa8c6000-aac00000 r-xs 00000000 08:07 167048     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.pde.ui_3.2.1.v20060816-0800.jar
aac00000-aad00000 rwxp aac00000 00:00 0 
aad00000-aad07000 r-xs 00000000 08:07 166967     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.variables_3.1.100.v20060605.jar
aad07000-aad11000 r-xs 00000000 08:07 81611      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.core_1.2.8/commons-logging.jar
aad11000-aad14000 ---p aad11000 00:00 0 
aad14000-aad92000 rwxp aad14000 00:00 0 
aad92000-aadf7000 r-xs 00000000 08:07 81796      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse.console_3.1.0.beta5/org.hibernate.eclipse.console.jar
aadf7000-aadfe000 r-xp 00000000 08:08 1308562    /usr/lib/libfam.so.0.0.0
aadfe000-aadff000 rwxp 00006000 08:08 1308562    /usr/lib/libfam.so.0.0.0
aadff000-aae05000 r-xp 00000000 08:01 439802     /lib/libacl.so.1.1.0
aae05000-aae06000 rwxp 00005000 08:01 439802     /lib/libacl.so.1.1.0
aae06000-aae09000 r-xp 00000000 08:01 439808     /lib/libattr.so.1.1.0
aae09000-aae0a000 rwxp 00002000 08:01 439808     /lib/libattr.so.1.1.0
aae0a000-aae16000 r-xp 00000000 08:08 1357575    /usr/lib/gnome-vfs-2.0/modules/libfile.so
aae16000-aae17000 rwxp 0000b000 08:08 1357575    /usr/lib/gnome-vfs-2.0/modules/libfile.so
aae17000-aae1e000 r-xp 00000000 08:08 1308580    /usr/lib/libgailutil.so.18.0.1
aae1e000-aae1f000 rwxp 00006000 08:08 1308580    /usr/lib/libgailutil.so.18.0.1
aae1f000-aaee0000 r-xp 00000000 08:08 1308423    /usr/lib/libasound.so.2.0.0
aaee0000-aaee5000 rwxp 000c0000 08:08 1308423    /usr/lib/libasound.so.2.0.0
aaee5000-aaee9000 r-xp 00000000 08:08 1308342    /usr/lib/libORBitCosNaming-2.so.0.1.0
aaee9000-aaeea000 rwxp 00003000 08:08 1308342    /usr/lib/libORBitCosNaming-2.so.0.1.0
aaeea000-aaf20000 r-xp 00000000 08:01 439901     /lib/libsepol.so.1
aaf20000-aaf21000 rwxp 00035000 08:01 439901     /lib/libsepol.so.1
aaf21000-aaf2b000 rwxp aaf21000 00:00 0 
aaf2b000-aaf7a000 r-xp 00000000 08:08 1308595    /usr/lib/libgcrypt.so.11.2.3
aaf7a000-aaf7c000 rwxp 0004e000 08:08 1308595    /usr/lib/libgcrypt.so.11.2.3
aaf7c000-aaf7f000 r-xp 00000000 08:08 1308702    /usr/lib/libgpg-error.so.0.3.0
aaf7f000-aaf80000 rwxp 00002000 08:08 1308702    /usr/lib/libgpg-error.so.0.3.0
aaf80000-aaf8f000 r-xp 00000000 08:08 1309070    /usr/lib/libtasn1.so.3.0.9
aaf8f000-aaf90000 rwxp 0000e000 08:08 1309070    /usr/lib/libtasn1.so.3.0.9
aaf90000-aafa5000 r-xp 00000000 08:08 1308328    /usr/lib/libICE.so.6.3.0
aafa5000-aafa7000 rwxp 00014000 08:08 1308328    /usr/lib/libICE.so.6.3.0
aafa7000-aafa8000 rwxp aafa7000 00:00 0 
aafa8000-aafaf000 r-xp 00000000 08:08 1308346    /usr/lib/libSM.so.6.0.0
aafaf000-aafb0000 rwxp 00006000 08:08 1308346    /usr/lib/libSM.so.6.0.0
aafb0000-aafcf000 r-xp 00000000 08:08 1308844    /usr/lib/libjpeg.so.62.0.0
aafcf000-aafd0000 rwxp 0001e000 08:08 1308844    /usr/lib/libjpeg.so.62.0.0
aafd0000-aafdd000 r-xp 00000000 08:08 1308666    /usr/lib/libgnome-keyring.so.0.1.1
aafdd000-aafde000 rwxp 0000d000 08:08 1308666    /usr/lib/libgnome-keyring.so.0.1.1
aafde000-aaff3000 r-xp 00000000 08:08 1308421    /usr/lib/libart_lgpl_2.so.2.3.19
aaff3000-aaff4000 rwxp 00014000 08:08 1308421    /usr/lib/libart_lgpl_2.so.2.3.19
aaff4000-ab023000 r-xp 00000000 08:08 1308676    /usr/lib/libgnomecanvas-2.so.0.2000.0
ab023000-ab024000 rwxp 0002f000 08:08 1308676    /usr/lib/libgnomecanvas-2.so.0.2000.0
ab024000-ab07f000 r-xp 00000000 08:08 1308456    /usr/lib/libbonoboui-2.so.0.0.0
ab07f000-ab082000 rwxp 0005a000 08:08 1308456    /usr/lib/libbonoboui-2.so.0.0.0
ab082000-ab089000 r-xp 00000000 08:01 439890     /lib/libpopt.so.0.0.0
ab089000-ab08a000 rwxp 00006000 08:01 439890     /lib/libpopt.so.0.0.0
ab08a000-ab0aa000 r-xp 00000000 08:08 1308433    /usr/lib/libaudiofile.so.0.0.2
ab0aa000-ab0ac000 rwxp 00020000 08:08 1308433    /usr/lib/libaudiofile.so.0.0.2
ab0ac000-ab0b5000 r-xp 00000000 08:08 1308549    /usr/lib/libesd.so.0.2.38
ab0b5000-ab0b6000 rwxp 00009000 08:08 1308549    /usr/lib/libesd.so.0.2.38
ab0b6000-ab0c9000 r-xp 00000000 08:08 1308454    /usr/lib/libbonobo-activation.so.4.0.0
ab0c9000-ab0cb000 rwxp 00013000 08:08 1308454    /usr/lib/libbonobo-activation.so.4.0.0
ab0cb000-ab11d000 r-xp 00000000 08:08 1308452    /usr/lib/libbonobo-2.so.0.0.0
ab11d000-ab127000 rwxp 00051000 08:08 1308452    /usr/lib/libbonobo-2.so.0.0.0
ab127000-ab13b000 r-xp 00000000 08:01 439900     /lib/libselinux.so.1
ab13b000-ab13d000 rwxp 00013000 08:01 439900     /lib/libselinux.so.1
ab13d000-ab14b000 r-xp 00000000 08:08 1308435    /usr/lib/libavahi-client.so.3.2.2
ab14b000-ab14c000 rwxp 0000e000 08:08 1308435    /usr/lib/libavahi-client.so.3.2.2
ab14c000-ab156000 r-xp 00000000 08:08 1308437    /usr/lib/libavahi-common.so.3.4.4
ab156000-ab157000 rwxp 00009000 08:08 1308437    /usr/lib/libavahi-common.so.3.4.4
ab157000-ab1c1000 r-xp 00000000 08:08 1308698    /usr/lib/libgnutls.so.13.3.0
ab1c1000-ab1c7000 rwxp 0006a000 08:08 1308698    /usr/lib/libgnutls.so.13.3.0
ab1c7000-ab1fb000 r-xp 00000000 08:08 1308498    /usr/lib/libdbus-1.so.3.3.0
ab1fb000-ab1fc000 rwxp 00033000 08:08 1308498    /usr/lib/libdbus-1.so.3.3.0
ab1fc000-ab216000 r-xp 00000000 08:08 1308500    /usr/lib/libdbus-glib-1.so.2.1.0
ab216000-ab217000 rwxp 0001a000 08:08 1308500    /usr/lib/libdbus-glib-1.so.2.1.0
ab217000-ab32f000 r-xp 00000000 08:08 1309128    /usr/lib/libxml2.so.2.6.30
ab32f000-ab334000 rwxp 00118000 08:08 1309128    /usr/lib/libxml2.so.2.6.30
ab334000-ab335000 rwxp ab334000 00:00 0 
ab335000-ab37e000 r-xp 00000000 08:08 1308338    /usr/lib/libORBit-2.so.0.1.0
ab37e000-ab387000 rwxp 00049000 08:08 1308338    /usr/lib/libORBit-2.so.0.1.0
ab387000-ab388000 rwxp ab387000 00:00 0 
ab388000-ab3b7000 r-xp 00000000 08:08 1308593    /usr/lib/libgconf-2.so.4.1.2
ab3b7000-ab3ba000 rwxp 0002e000 08:08 1308593    /usr/lib/libgconf-2.so.4.1.2
ab3ba000-ab442000 r-xp 00000000 08:08 1308690    /usr/lib/libgnomeui-2.so.0.2000.0
ab442000-ab446000 rwxp 00087000 08:08 1308690    /usr/lib/libgnomeui-2.so.0.2000.0
ab446000-ab45a000 r-xp 00000000 08:08 1308662    /usr/lib/libgnome-2.so.0.2000.0
ab45a000-ab45b000 rwxp 00014000 08:08 1308662    /usr/lib/libgnome-2.so.0.2000.0
ab45b000-ab4b1000 r-xp 00000000 08:08 1308692    /usr/lib/libgnomevfs-2.so.0.2000.0
ab4b1000-ab4b4000 rwxp 00055000 08:08 1308692    /usr/lib/libgnomevfs-2.so.0.2000.0
ab4b6000-ab4bf000 r-xs 00000000 08:07 1841235    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.internet.proxy_1.0.100.v200606130645.jar
ab4bf000-ab4c2000 r-xp 00000000 08:07 213201     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-gnome-gtk-3235.so
ab4c2000-ab4c3000 rwxp 00002000 08:07 213201     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-gnome-gtk-3235.so
ab4c3000-ab4cf000 r-xs 00000000 08:07 1841091    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.web.ui_1.1.0.v200606161959.jar
ab4cf000-ab4f1000 r-xs 00000000 08:07 167024     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.console_3.1.100.v20060605.jar
ab4f1000-ab522000 r-xp 00000000 08:07 98312      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libnspr4.so
ab522000-ab524000 rwxp 00031000 08:07 98312      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libnspr4.so
ab524000-ab525000 rwxp ab524000 00:00 0 
ab525000-ab526000 r-xp 00000000 08:08 1341548    /usr/lib/firefox/components/libmozfind.so
ab526000-ab527000 rwxp 00001000 08:08 1341548    /usr/lib/firefox/components/libmozfind.so
ab527000-ab528000 r-xp 00000000 08:08 1357664    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
ab528000-ab529000 rwxp 00000000 08:08 1357664    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
ab529000-ab54b000 r-xs 00000000 08:07 1841154    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee.navigator.ui_1.1.0.v200606130315.jar
ab54b000-ab55f000 r-xs 00000000 08:07 1841088    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.server.tomcat.ui_1.0.102.v200606130315.jar
ab55f000-ab562000 ---p ab55f000 00:00 0 
ab562000-ab5e0000 rwxp ab562000 00:00 0 
ab5e0000-ab65a000 r-xp 00000000 08:08 1457896    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libfontmanager.so
ab65a000-ab664000 rwxp 00079000 08:08 1457896    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libfontmanager.so
ab664000-ab668000 rwxp ab664000 00:00 0 
ab668000-ab697000 r-xp 00000000 08:08 1471685    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/xawt/libmawt.so
ab697000-ab69a000 rwxp 0002e000 08:08 1471685    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/xawt/libmawt.so
ab69a000-ab69b000 rwxp ab69a000 00:00 0 
ab69b000-ab761000 r-xp 00000000 08:08 1457892    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libmlib_image.so
ab761000-ab762000 rwxp 000c5000 08:08 1457892    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libmlib_image.so
ab762000-ab7c2000 r-xp 00000000 08:08 1457893    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libawt.so
ab7c2000-ab7c8000 rwxp 0005f000 08:08 1457893    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libawt.so
ab7c8000-ab7ec000 rwxp ab7c8000 00:00 0 
ab7ec000-ab833000 r-xp 00000000 08:08 1586273    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
ab833000-ab87e000 r-xp 00000000 08:08 1586274    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
ab87e000-ab900000 r-xs 00000000 08:07 1841207    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.javascript.ui_1.0.0.v200606141450.jar
ab900000-aba00000 rwxp ab900000 00:00 0 
aba00000-aba02000 r-xs 00000000 08:07 167000     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.update.core.linux_3.2.0.v20060605.jar
aba02000-aba04000 r-xp 00000000 08:01 473842     /lib/tls/i686/cmov/libutil-2.6.1.so
aba04000-aba06000 rwxp 00001000 08:01 473842     /lib/tls/i686/cmov/libutil-2.6.1.so
aba06000-aba08000 r-xp 00000000 08:08 1308441    /usr/lib/libavahi-glib.so.1.0.1
aba08000-aba09000 rwxp 00001000 08:08 1308441    /usr/lib/libavahi-glib.so.1.0.1
aba0a000-aba11000 r-xs 00000000 08:07 166987     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.update.scheduler_3.2.1.v20092006.jar
aba11000-aba1b000 r-xs 00000000 08:07 1841269    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.server.generic.ui_1.0.100.v200606130315.jar
aba1b000-aba4c000 r-xs 00000000 08:07 100357     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.texteditors.extensions_2.0.0/texteditorextensions.jar
aba4c000-abad0000 r-xp 00000000 08:08 1586271    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
abad0000-abae5000 r-xs 00000000 08:07 1841049    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.springframework.ide.eclipse.beans.ui.editor_1.0.3/beans-editor.jar
abae5000-abc6f000 r-xs 00000000 08:07 81539      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jgroups-2.2.8.jar
abc6f000-abcb4000 r-xs 00000000 08:07 81520      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/cglib-2.1.3.jar
abcb4000-abd21000 r-xs 00000000 08:07 81536      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/antlr-2.7.6rc1.jar
abd21000-abd71000 r-xs 00000000 08:07 81544      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/annotations/lucene-1.4.3.jar
abd71000-abdbb000 r-xs 00000000 08:07 81543      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/annotations/hibernate-annotations.jar
abdbb000-abdc8000 r-xs 00000000 08:07 81542      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/annotations/ejb3-persistence.jar
abdc8000-abdec000 r-xs 00000000 08:07 81515      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/bsh-core-2.0b4.jar
abdec000-abead000 r-xs 00000000 08:07 81512      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/tools/freemarker.jar
abead000-abeea000 r-xs 00000000 08:07 81514      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/tools/jtidy-r8-21122004.jar
abeea000-abf29000 r-xs 00000000 08:07 81513      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/tools/hibernate-tools.jar
abf29000-abf31000 r-xs 00000000 08:07 81535      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/swarmcache-1.0rc2.jar
abf31000-abfa6000 r-xs 00000000 08:07 81522      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/proxool-0.8.3.jar
abfa6000-abfc2000 r-xs 00000000 08:07 81521      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/oscache-2.1.jar
abfc2000-ac018000 r-xs 00000000 08:07 81532      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/log4j-1.2.11.jar
ac018000-ac032000 r-xs 00000000 08:07 81525      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jaas.jar
ac032000-ac035000 r-xs 00000000 08:07 81517      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jta.jar
ac035000-ac037000 r-xs 00000000 08:07 81518      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jdbc2_0-stdext.jar
ac037000-ac06e000 r-xs 00000000 08:07 81537      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jboss-system.jar
ac06e000-ac0ff000 r-xs 00000000 08:07 81538      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jboss-jmx.jar
ac0ff000-ac18e000 r-xs 00000000 08:07 81524      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jboss-common.jar
ac18e000-ac20d000 r-xs 00000000 08:07 81527      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/jboss-cache.jar
ac20d000-ac40a000 r-xs 00000000 08:07 81530      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/hibernate3.jar
ac40a000-ac416000 r-xs 00000000 08:07 81529      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/ehcache-1.1.jar
ac416000-ac463000 r-xs 00000000 08:07 81523      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/dom4j-1.6.1.jar
ac463000-ac48d000 r-xs 00000000 08:07 81526      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/concurrent-1.3.2.jar
ac48d000-ac4b8000 r-xs 00000000 08:07 81531      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/commons-collections-2.1.1.jar
ac4b8000-ac52f000 r-xs 00000000 08:07 81540      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/c3p0-0.9.0.jar
ac52f000-ac543000 r-xs 00000000 08:07 81545      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/org.hibernate.eclipse.jar
ac543000-ac56a000 r-xs 00000000 08:07 81498      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse.mapper_3.1.0.beta5/org.hibernate.eclipse.mapper.jar
ac56a000-ac732000 r-xs 00000000 08:07 1841246    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.sun.enterprise.jst.server.sunappsrv_1.0.0.jar
ac732000-ac7dd000 r-xs 00000000 08:07 1841212    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.xsd_2.2.0.v200606271057.jar
ac7dd000-ac8be000 r-xs 00000000 08:07 1841101    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.xsd.ui_1.1.0.v200606142122.jar
ac8be000-ac934000 r-xs 00000000 08:07 1841112    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.css.core_1.1.0.v200606141450.jar
ac934000-ac943000 r-xs 00000000 08:07 166989     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.pde_3.2.1.v20060810-0800.jar
ac943000-aca00000 r-xs 00000000 08:07 167051     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.pde.core_3.2.1.v20060915-0800.jar
aca00000-acaff000 rwxp aca00000 00:00 0 
acaff000-acb00000 ---p acaff000 00:00 0 
acb00000-acbfe000 rwxp acb00000 00:00 0 
acbfe000-acc00000 ---p acbfe000 00:00 0 
acc00000-acd00000 rwxp acc00000 00:00 0 
acd01000-acd05000 r-xp 00000000 08:07 98694      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libplc4.so
acd05000-acd06000 rwxp 00003000 08:07 98694      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libplc4.so
acd06000-acd13000 r-xs 00000000 08:07 1841208    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.javascript.core_1.0.0.v200606141450.jar
acd13000-acd18000 r-xs 00000000 08:07 81528      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/connector.jar
acd18000-acd22000 r-xs 00000000 08:07 81519      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/commons-logging-1.0.4.jar
acd22000-acd3d000 r-xs 00000000 08:07 1841265    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.html.standard.dtds_1.0.0.jar
acd3d000-acd78000 r-xs 00000000 08:07 166998     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.debug.core_3.2.1.v20060823.jar
acd78000-ace00000 r-xs 00000000 08:07 1841195    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.html.core_1.1.0.v200606141450.jar
ace00000-acf00000 rwxp ace00000 00:00 0 
acf00000-acf02000 r-xp 00000000 08:07 98523      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libplds4.so
acf02000-acf03000 rwxp 00002000 08:07 98523      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla.gtk_2.0.0/os/linux/x86/libplds4.so
acf03000-acf0a000 r-xs 00000000 08:07 81533      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/asm.jar
acf0a000-acf19000 r-xp 00000000 08:01 473836     /lib/tls/i686/cmov/libresolv-2.6.1.so
acf19000-acf1b000 rwxp 0000f000 08:01 473836     /lib/tls/i686/cmov/libresolv-2.6.1.so
acf1b000-acf1d000 rwxp acf1b000 00:00 0 
acf1d000-acf21000 r-xp 00000000 08:01 473823     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
acf21000-acf23000 rwxp 00003000 08:01 473823     /lib/tls/i686/cmov/libnss_dns-2.6.1.so
acf23000-acf5c000 r-xs 00000000 08:07 166984     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.launching_3.2.1.r321_v20060731.jar
acf5c000-acff0000 r-xs 00000000 08:07 1841081    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.xml.core_1.1.0.v200606142000.jar
acff0000-ad060000 r-xs 00000000 08:07 1841104    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.jsp.core_1.1.0.v200606191945.jar
ad060000-ad0d2000 r-xs 00000000 08:07 166972     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.compare_3.2.1.M20060711.jar
ad0d2000-ad114000 r-xs 00000000 08:07 100373     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe.mozilla_2.0.0/mozilla-vpe.jar
ad114000-ad145000 r-xs 00000000 08:07 1841183    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.css.ui_1.0.100.v200606141450.jar
ad145000-ad15f000 r-xs 00000000 08:07 98886      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model.ui.views_8.0.0/modeluiviews.jar
ad15f000-ad1aa000 r-xs 00000000 08:07 1841107    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.jsp.ui_1.1.0.v200606191945.jar
ad1aa000-ad248000 r-xs 00000000 08:07 1841153    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.xml.ui_1.0.100.v200606141450.jar
ad248000-ad300000 r-xs 00000000 08:07 1841106    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.emf.ecore_2.2.0.v200606271057.jar
ad300000-ad400000 rwxp ad300000 00:00 0 
ad400000-ad405000 r-xs 00000000 08:07 81534      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.hibernate.eclipse_3.1.0.beta5/lib/hibernate/asm-attrs.jar
ad405000-ad40d000 r-xs 00000000 08:07 1841196    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.uriresolver_1.1.0.v200606130645.jar
ad40d000-ad43c000 r-xs 00000000 08:07 1841168    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.html.ui_1.0.100.v200606191945.jar
ad43c000-ad43e000 r-xs 00000000 08:07 1841197    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.generic.jdbc_1.0.101.v200605040131.jar
ad43e000-ad440000 r-xs 00000000 08:07 1840922    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.mysql_1.0.0.v200605040131.jar
ad440000-ad445000 r-xs 00000000 08:07 1841145    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.oracle_1.0.101.v200605040131.jar
ad445000-ad44b000 r-xs 00000000 08:07 1841164    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.informix_1.0.102.v200605082300.jar
ad44b000-ad44e000 r-xs 00000000 08:07 1841178    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.derby_1.0.102.v200606221744.jar
ad44e000-ad450000 r-xs 00000000 08:07 1841109    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.iseries_1.0.102.v200606221744.jar
ad450000-ad455000 r-xs 00000000 08:07 1841201    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.luw_1.0.103.v200606221744.jar
ad455000-ad45a000 r-xs 00000000 08:07 1841054    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.db2.zseries_1.0.102.v200606221744.jar
ad45a000-ad45e000 r-xs 00000000 08:07 1841228    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.sqlserver_1.0.102.v200605040131.jar
ad45e000-ad461000 r-xs 00000000 08:07 1841213    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.dbdefinition.sybase_1.0.103.v200606221744.jar
ad461000-ad487000 r-xs 00000000 08:07 1841227    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.emf.common_2.2.0.v200606271057.jar
ad487000-ad49e000 r-xs 00000000 08:07 1841258    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jem.util_1.2.0.v20060530_RC2.jar
ad49e000-ad4e1000 r-xs 00000000 08:07 1841133    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jem_1.2.0.v20060530_RC2.jar
ad4e1000-ad4ff000 r-xs 00000000 08:07 98841      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.prompting.knowledgebase_8.0.0/knowledgebase.jar
ad4ff000-ad516000 r-xs 00000000 08:07 167023     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.filebuffers_3.2.1.r321_v20060721.jar
ad516000-ad570000 r-xs 00000000 08:07 1841171    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.sse.core_1.1.0.v200606141450.jar
ad570000-ad614000 r-xs 00000000 08:07 1841245    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.sse.ui_1.0.101.v200606191900.jar
ad614000-ad620000 r-xs 00000000 08:07 98101      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.texteditors.xml_8.0.0/xmleditor.jar
ad620000-ad64f000 r-xs 00000000 08:07 98972      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model.ui.editors_8.0.0/modeluieditors.jar
ad64f000-ad65f000 r-xs 00000000 08:07 98960      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model.ui.editors_8.0.0/lib/jakarta-oro.jar
ad65f000-ad71c000 r-xs 00000000 08:07 166983     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jface.text_3.2.1.r321_v20060810.jar
ad71c000-ad71f000 r-xs 00000000 08:07 98036      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.web.verification_2.0.0/web-verification.jar
ad71f000-ad724000 r-xs 00000000 08:07 97941      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.struts.verification_8.0.0/struts-verification.jar
ad724000-ad735000 r-xs 00000000 08:07 167042     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.views_3.2.1.M20060906-0800.jar
ad735000-ad737000 r-xs 00000000 08:07 98021      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.struts.pro.ui_8.0.0/strutsproui.jar
ad737000-ad746000 r-xs 00000000 08:07 99199      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.verification.ui_8.0.0/verificationui.jar
ad746000-ad7d7000 r-xs 00000000 08:07 100323     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.struts.ui_8.0.0/strutsui.jar
ad7d7000-ad85a000 r-xs 00000000 08:07 98915      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.jsf.ui_3.0.0/jsfui.jar
ad85a000-ad8cc000 r-xs 00000000 08:07 97979      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.web.ui_8.0.0/webui.jar
ad8cc000-ad9c3000 r-xs 00000000 08:07 100246     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.common_8.0.0/lib/xercesImpl.jar
ad9c3000-ada40000 r-xs 00000000 08:07 100247     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.common_8.0.0/lib/velocity-dep-1.3.1.jar
ada40000-ada96000 r-xs 00000000 08:07 100244     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.common_8.0.0/lib/velocity-1.3.1.jar
ada96000-adac7000 r-xs 00000000 08:07 81632      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/xml-apis.jar
adac7000-adbed000 r-xs 00000000 08:07 81628      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/xercesImpl.jar
adbed000-adbfc000 r-xs 00000000 08:07 81626      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.apache.xerces_2.8.0.v200606131651/resolver.jar
adbfc000-adbff000 ---p adbfc000 00:00 0 
adbff000-adc7d000 rwxp adbff000 00:00 0 
adc7d000-adc8f000 r-xs 00000000 08:07 100396     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.verification_8.0.0/verification.jar
adc8f000-adce3000 r-xs 00000000 08:07 100236     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.jsf_7.0.0/jsf.jar
adce3000-add70000 r-xs 00000000 08:07 100183     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.vpe_2.0.0/vpe.jar
add70000-add74000 r-xs 00000000 08:07 100426     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.jsf.verification_8.0.0/jsf-verification.jar
add74000-add8b000 r-xs 00000000 08:07 98930      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.shale_2.0.0/shale.jar
add8b000-add9f000 r-xs 00000000 08:07 100201     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.struts.debug_3.0.0/strutsdebug.jar
add9f000-addad000 r-xs 00000000 08:07 98047      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.web.tiles_8.0.0/web-tiles.jar
addad000-ade3a000 r-xs 00000000 08:07 98872      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.struts_8.0.0/struts.jar
ade3a000-adeb4000 r-xs 00000000 08:07 98054      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.web_8.0.0/web.jar
adeb4000-adeb7000 ---p adeb4000 00:00 0 
adeb7000-adf35000 rwxp adeb7000 00:00 0 
adf35000-ae2f0000 r-xs 00000000 08:07 167020     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.core_3.2.1.v_677_R32x.jar
ae2f0000-ae426000 r-xs 00000000 08:07 98939      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model_8.0.0/model.jar
ae426000-ae500000 r-xs 00000000 08:07 99110      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model.ui_8.0.0/modelui.jar
ae500000-ae5fa000 rwxp ae500000 00:00 0 
ae5fa000-ae600000 ---p ae5fa000 00:00 0 
ae600000-ae6f5000 rwxp ae600000 00:00 0 
ae6f5000-ae700000 ---p ae6f5000 00:00 0 
ae701000-ae736000 r-xs 00000000 08:07 167043     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.text_3.2.0.v20060605-1400.jar
ae736000-ae775000 r-xs 00000000 08:07 98975      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.texteditors.jsp_8.0.0/jspeditor.jar
ae775000-ae800000 r-xp 00000000 08:08 1586272    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ae800000-ae900000 rwxp ae800000 00:00 0 
ae901000-ae93d000 r-xs 00000000 08:07 1841200    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.server.core_1.0.102.v200606130645.jar
ae93d000-ae948000 r-xs 00000000 08:07 100320     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.common_8.0.0/common.jar
ae948000-ae950000 r-xs 00000000 08:07 100248     /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.common_8.0.0/lib/commons-logging.jar
ae950000-ae959000 r-xp 00000000 08:07 213193     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-cairo-gtk-3235.so
ae959000-ae95a000 rwxp 00009000 08:07 213193     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-cairo-gtk-3235.so
ae95a000-ae960000 r-xp 00000000 08:07 213192     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-atk-gtk-3235.so
ae960000-ae961000 rwxp 00005000 08:07 213192     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-atk-gtk-3235.so
ae961000-ae963000 r-xp 00000000 08:08 1422723    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
ae963000-ae964000 rwxp 00001000 08:08 1422723    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
ae964000-ae9c4000 rwxs 00000000 00:09 1638419    /SYSV00000000 (deleted)
ae9c4000-aecdf000 r-xs 00000000 08:07 167003     /home/sumiravi/Programs/eclipse/plugins/com.ibm.icu_3.4.5.jar
aecdf000-aecfc000 r-xs 00000000 08:07 167034     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.help_3.2.1.R321_v20060920.jar
aecfc000-aed37000 r-xs 00000000 08:07 1841087    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.common.snippets_1.1.0.v200606141450.jar
aed37000-aed5f000 r-xs 00000000 08:07 1841157    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.server.ui_1.0.101.v200606130645.jar
aed5f000-aed6f000 r-xs 00000000 08:07 1841069    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.wsi.ui_1.0.0.v200606130645.jar
aed6f000-aed77000 r-xs 00000000 08:07 1841185    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.sqlscrapbook_1.0.101.v200606130645.jar
aed77000-aed8f000 r-xs 00000000 08:07 1841230    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.internet.monitor.ui_1.0.102.v200606130645.jar
aed8f000-aed99000 r-xs 00000000 08:07 1841210    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.emf.mapping.ecore2ecore.editor_2.2.0.v200606271057.jar
aed99000-aee40000 r-xs 00000000 08:07 1841162    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.wsdl.ui_1.1.0.v200606142122.jar
aee40000-aee47000 r-xs 00000000 08:07 1841126    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.emf.mapping.xsd2ecore.editor_2.1.0.v200606271057.jar
aee47000-af5fd000 r-xs 00000000 08:07 167049     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.ui_3.2.1.r321_v20060907.jar
af5fd000-af7c3000 r-xs 00000000 08:07 167007     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.debug.ui_3.2.1.v20060823.jar
af7c3000-af8d6000 r-xs 00000000 08:07 166988     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jdt.debug.ui_3.2.1.r321_v20060918.jar
af8d6000-afa42000 r-xs 00000000 08:07 167045     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.team.cvs.ui_3.2.1.M20060831.jar
afa42000-afaab000 r-xs 00000000 08:07 166977     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.workbench.texteditor_3.2.0.v20060605-1400.jar
afaab000-afb17000 r-xs 00000000 08:07 167019     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.search_3.2.1.r321_v20060726.jar
afb17000-afb86000 r-xs 00000000 08:07 167022     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.editors_3.2.1.r321_v20060721.jar
afb86000-afc8a000 r-xs 00000000 08:07 166980     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.team.ui_3.2.1.M200608151725.jar
afc8a000-afd8d000 r-xs 00000000 08:07 167026     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ant.ui_3.2.1.r321_v20060828.jar
afd8d000-afdad000 r-xs 00000000 08:07 167005     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.externaltools_3.1.101.r321_v20060802.jar
afdad000-afde6000 r-xs 00000000 08:07 1841243    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.ejb.ui_1.1.0.v200606130315.jar
afde6000-afe7c000 r-xs 00000000 08:07 1841192    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.server.ui_1.0.102.v200606130645.jar
afe7c000-aff35000 r-xs 00000000 08:07 1841224    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee.ui_1.1.0.v200606130315.jar
aff35000-affdf000 r-xs 00000000 08:07 1841262    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.ws.consumption.ui_1.0.101.v200606130315.jar
affdf000-b0000000 r-xs 00000000 08:07 1841205    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jem.ui_1.2.0.v20060518_RC1.jar
b0000000-b0100000 rwxp b0000000 00:00 0 
b0100000-b0101000 r-xs 00000000 08:07 98936      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.model_8.0.0/lib/Bundles.jar
b0101000-b0102000 r-xs 00000000 08:07 99316      /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/com.exadel.project.templates_8.0.0/projtempl.jar
b0102000-b0105000 rwxs 00000000 00:09 1605649    /SYSV00000000 (deleted)
b0105000-b0107000 r-xs 00000000 08:07 1840965    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.wst.rdb.fe.ui.actions_1.0.101.v200606130645.jar
b0107000-b011f000 r-xs 00000000 08:07 1841103    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.servlet.ui_1.1.0.v200606130315.jar
b011f000-b0125000 r-xs 00000000 08:07 1841215    /home/sumiravi/Programs/ExadelStudio/eclipse/plugins/org.eclipse.jst.j2ee.jca.ui_1.1.0.v200606130315.jar
b0125000-b0128000 ---p b0125000 00:00 0 
b0128000-b01a6000 rwxp b0128000 00:00 0 
b01a6000-b01ac000 r-xs 00000000 08:06 1433415    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b01ac000-b01af000 r-xs 00000000 08:06 1433578    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b01af000-b01b3000 r-xs 00000000 08:06 1433577    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b01b3000-b01b4000 r-xs 00000000 08:06 1433576    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b01b4000-b01b5000 r-xs 00000000 08:06 1433575    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b01b5000-b01b8000 r-xs 00000000 08:06 1433574    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b01b8000-b01b9000 r-xs 00000000 08:06 1433573    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b01b9000-b01bc000 r-xs 00000000 08:06 1433572    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b01bc000-b01be000 r-xs 00000000 08:06 1433571    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b01be000-b01c6000 r-xs 00000000 08:06 1433570    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b01c6000-b01cc000 r-xs 00000000 08:06 1433569    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b01cc000-b01cd000 r-xs 00000000 08:06 1433568    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b01cd000-b01cf000 r-xs 00000000 08:06 1433567    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b01cf000-b01d5000 r-xs 00000000 08:06 1433566    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b01d5000-b01d9000 r-xs 00000000 08:06 1433400    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b01d9000-b01db000 r-xs 00000000 08:06 1433451    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b01db000-b01dc000 r-xs 00000000 08:06 1433601    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b01dc000-b01dd000 r-xs 00000000 08:06 1433600    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b01dd000-b01de000 r-xs 00000000 08:06 1433599    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b01de000-b01e1000 r-xs 00000000 08:06 1433598    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b01e1000-b01e4000 r-xs 00000000 08:06 1433597    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b01e4000-b01e6000 r-xs 00000000 08:06 1433596    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b01e6000-b01e7000 r-xs 00000000 08:06 1433595    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b01e7000-b01e8000 r-xs 00000000 08:06 1433594    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b01e8000-b01e9000 r-xs 00000000 08:06 1433593    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b01e9000-b01ee000 r-xs 00000000 08:06 1433592    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b01ee000-b01f3000 r-xs 00000000 08:06 1433591    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b01f3000-b01f5000 r-xs 00000000 08:06 1433590    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b01f5000-b01f8000 r-xs 00000000 08:06 1433589    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b01f8000-b01f9000 r-xs 00000000 08:06 1433588    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b01f9000-b01fc000 r-xs 00000000 08:06 1433586    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b01fc000-b0202000 r-xs 00000000 08:06 1433585    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b0202000-b0206000 r-xs 00000000 08:06 1433583    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b0206000-b0208000 r-xs 00000000 08:06 1433582    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b0208000-b020c000 r-xs 00000000 08:06 1433581    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b020c000-b0237000 r-xs 00000000 08:07 166994     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.browser_3.2.0.v20060602.jar
b0237000-b027e000 r-xs 00000000 08:07 166976     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.cheatsheets_3.2.1.R321_v20060720.jar
b027e000-b0281000 ---p b027e000 00:00 0 
b0281000-b02ff000 rwxp b0281000 00:00 0 
b02ff000-b0356000 r-xs 00000000 08:07 167011     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.team.core_3.2.1.M20060711.jar
b0356000-b0367000 r-xs 00000000 08:07 167050     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.expressions_3.2.1.r321_v20060721.jar
b0367000-b036a000 rwxp b0367000 00:00 0 
b036a000-b03e8000 rwxp b036a000 00:00 0 
b03e8000-b03fb000 r-xs 00000000 08:07 166966     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.contenttype_3.2.0.v20060603.jar
b03fb000-b03fd000 r-xp 00000000 08:07 213191     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/338/1/.cp/os/linux/x86/liblocalfile_1_0_0.so
b03fd000-b03fe000 rwxp 00001000 08:07 213191     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/338/1/.cp/os/linux/x86/liblocalfile_1_0_0.so
b03fe000-b0402000 r-xs 00000000 08:07 166986     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.filesystem.linux.x86_1.0.0.v20060603.jar
b0402000-b04a0000 r-xs 00000000 08:07 166975     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.resources_3.2.1.R32x_v20060914.jar
b04a0000-b0500000 rwxs 00000000 00:09 1572880    /SYSV00000000 (deleted)
b0500000-b0600000 rwxp b0500000 00:00 0 
b0600000-b0601000 r-xs 00000000 08:06 1433587    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b0601000-b0602000 r-xs 00000000 08:06 1433584    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b0602000-b060b000 r-xs 00000000 08:07 167008     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.filesystem_1.0.0.v20060603.jar
b060b000-b0627000 r-xs 00000000 08:07 167047     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.resources.compatibility_3.2.0.v20060603.jar
b0627000-b0639000 r-xp 00000000 08:08 1357630    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b0639000-b063a000 rwxp 00011000 08:08 1357630    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b063a000-b0660000 r-xp 00000000 08:07 213179     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-gtk-3235.so
b0660000-b0662000 rwxp 00025000 08:07 213179     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-gtk-3235.so
b0662000-b0663000 rwxp b0662000 00:00 0 
b0663000-b0664000 r-xp 00000000 08:08 1309726    /usr/lib/gconv/ISO8859-1.so
b0664000-b0666000 rwxp 00000000 08:08 1309726    /usr/lib/gconv/ISO8859-1.so
b0666000-b066d000 r-xs 00000000 08:08 1309779    /usr/lib/gconv/gconv-modules.cache
b066d000-b074d000 r-xp 00000000 08:08 1358380    /usr/lib/locale/en_IN/LC_COLLATE
b074d000-b076b000 r-xp 00000000 08:08 1308558    /usr/lib/libexpat.so.1.0.0
b076b000-b076d000 rwxp 0001e000 08:08 1308558    /usr/lib/libexpat.so.1.0.0
b076d000-b078f000 r-xp 00000000 08:08 1308982    /usr/lib/libpng12.so.0.15.0
b078f000-b0790000 rwxp 00021000 08:08 1308982    /usr/lib/libpng12.so.0.15.0
b0790000-b0794000 r-xp 00000000 08:08 1308367    /usr/lib/libXdmcp.so.6.0.0
b0794000-b0795000 rwxp 00003000 08:08 1308367    /usr/lib/libXdmcp.so.6.0.0
b0795000-b0797000 r-xp 00000000 08:08 1308356    /usr/lib/libXau.so.6.0.0
b0797000-b0798000 rwxp 00001000 08:08 1308356    /usr/lib/libXau.so.6.0.0
b0798000-b07ac000 r-xp 00000000 08:08 1309134    /usr/lib/libz.so.1.2.3.3
b07ac000-b07ad000 rwxp 00013000 08:08 1309134    /usr/lib/libz.so.1.2.3.3
b07ad000-b0819000 r-xp 00000000 08:08 1308572    /usr/lib/libfreetype.so.6.3.16
b0819000-b081d000 rwxp 0006b000 08:08 1308572    /usr/lib/libfreetype.so.6.3.16
b081d000-b084a000 r-xp 00000000 08:08 1308955    /usr/lib/libpangoft2-1.0.so.0.1800.2
b084a000-b084b000 rwxp 0002c000 08:08 1308955    /usr/lib/libpangoft2-1.0.so.0.1800.2
b084b000-b0853000 r-xp 00000000 08:08 1308363    /usr/lib/libXcursor.so.1.0.2
b0853000-b0854000 rwxp 00007000 08:08 1308363    /usr/lib/libXcursor.so.1.0.2
b0854000-b0859000 r-xp 00000000 08:08 1308391    /usr/lib/libXrandr.so.2.1.0
b0859000-b085a000 rwxp 00005000 08:08 1308391    /usr/lib/libXrandr.so.2.1.0
b085a000-b0861000 r-xp 00000000 08:08 1308379    /usr/lib/libXi.so.6.0.0
b0861000-b0862000 rwxp 00006000 08:08 1308379    /usr/lib/libXi.so.6.0.0
b0862000-b0864000 r-xp 00000000 08:08 1308381    /usr/lib/libXinerama.so.1.0.0
b0864000-b0865000 rwxp 00001000 08:08 1308381    /usr/lib/libXinerama.so.1.0.0
b0865000-b086c000 r-xp 00000000 08:08 1308393    /usr/lib/libXrender.so.1.3.0
b086c000-b086d000 rwxp 00006000 08:08 1308393    /usr/lib/libXrender.so.1.3.0
b086d000-b0890000 r-xp 00000000 08:08 1308564    /usr/lib/libfontconfig.so.1.2.0
b0890000-b0898000 rwxp 00023000 08:08 1308564    /usr/lib/libfontconfig.so.1.2.0
b0898000-b08a5000 r-xp 00000000 08:08 1308371    /usr/lib/libXext.so.6.4.0
b08a5000-b08a6000 rwxp 0000d000 08:08 1308371    /usr/lib/libXext.so.6.4.0
b08a6000-b08ad000 r-xp 00000000 08:01 473838     /lib/tls/i686/cmov/librt-2.6.1.so
b08ad000-b08af000 rwxp 00006000 08:01 473838     /lib/tls/i686/cmov/librt-2.6.1.so
b08af000-b0924000 r-xp 00000000 08:08 1308460    /usr/lib/libcairo.so.2.11.5
b0924000-b0926000 rwxp 00074000 08:08 1308460    /usr/lib/libcairo.so.2.11.5
b0926000-b09e2000 r-xp 00000000 08:08 1308650    /usr/lib/libglib-2.0.so.0.1400.1
b09e2000-b09e3000 rwxp 000bc000 08:08 1308650    /usr/lib/libglib-2.0.so.0.1400.1
b09e3000-b09e6000 r-xp 00000000 08:08 1308660    /usr/lib/libgmodule-2.0.so.0.1400.1
b09e6000-b09e7000 rwxp 00002000 08:08 1308660    /usr/lib/libgmodule-2.0.so.0.1400.1
b09e7000-b0a21000 r-xp 00000000 08:08 1308700    /usr/lib/libgobject-2.0.so.0.1400.1
b0a21000-b0a22000 rwxp 0003a000 08:08 1308700    /usr/lib/libgobject-2.0.so.0.1400.1
b0a22000-b0a3b000 r-xp 00000000 08:08 1308429    /usr/lib/libatk-1.0.so.0.2009.1
b0a3b000-b0a3d000 rwxp 00018000 08:08 1308429    /usr/lib/libatk-1.0.so.0.2009.1
b0a3d000-b0a41000 r-xp 00000000 08:08 1308373    /usr/lib/libXfixes.so.3.1.0
b0a41000-b0a42000 rwxp 00003000 08:08 1308373    /usr/lib/libXfixes.so.3.1.0
b0a42000-b0a44000 r-xp 00000000 08:08 1308365    /usr/lib/libXdamage.so.1.1.0
b0a44000-b0a45000 rwxp 00001000 08:08 1308365    /usr/lib/libXdamage.so.1.1.0
b0a45000-b0a47000 r-xp 00000000 08:08 1308361    /usr/lib/libXcomposite.so.1.0.0
b0a47000-b0a48000 rwxp 00001000 08:08 1308361    /usr/lib/libXcomposite.so.1.0.0
b0a48000-b0b35000 r-xp 00000000 08:08 1308350    /usr/lib/libX11.so.6.2.0
b0b35000-b0b39000 rwxp 000ed000 08:08 1308350    /usr/lib/libX11.so.6.2.0
b0b39000-b0b74000 r-xp 00000000 08:08 1308951    /usr/lib/libpango-1.0.so.0.1800.2
b0b74000-b0b76000 rwxp 0003b000 08:08 1308951    /usr/lib/libpango-1.0.so.0.1800.2
b0b76000-b0b7e000 r-xp 00000000 08:08 1308953    /usr/lib/libpangocairo-1.0.so.0.1800.2
b0b7e000-b0b7f000 rwxp 00007000 08:08 1308953    /usr/lib/libpangocairo-1.0.so.0.1800.2
b0b7f000-b0c03000 r-xp 00000000 08:08 1308610    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b0c03000-b0c06000 rwxp 00084000 08:08 1308610    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b0c06000-b0c1d000 r-xp 00000000 08:08 1308612    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b0c1d000-b0c1e000 rwxp 00016000 08:08 1308612    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b0c1e000-b0f9b000 r-xp 00000000 08:08 1308765    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b0f9b000-b0fa2000 rwxp 0037c000 08:08 1308765    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b0fa2000-b0fa3000 rwxp b0fa2000 00:00 0 
b0fa3000-b0fa6000 r-xs 00000000 08:06 1433423    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b0fa6000-b0fa7000 r-xp 00000000 08:08 1358386    /usr/lib/locale/en_IN/LC_NUMERIC
b0fa7000-b0fa8000 r-xp 00000000 08:08 1358389    /usr/lib/locale/en_IN/LC_TIME
b0fa8000-b0fa9000 r-xp 00000000 08:08 1358384    /usr/lib/locale/en_IN/LC_MONETARY
b0fa9000-b0faa000 r-xp 00000000 08:08 1373598    /usr/lib/locale/en_IN/LC_MESSAGES/SYS_LC_MESSAGES
b0faa000-b0fab000 r-xp 00000000 08:08 1358387    /usr/lib/locale/en_IN/LC_PAPER
b0fab000-b0fac000 r-xp 00000000 08:08 1358385    /usr/lib/locale/en_IN/LC_NAME
b0fac000-b0fad000 r-xp 00000000 08:08 1358379    /usr/lib/locale/en_IN/LC_ADDRESS
b0fad000-b0fae000 r-xp 00000000 08:08 1358388    /usr/lib/locale/en_IN/LC_TELEPHONE
b0fae000-b0ff8000 r-xp 00000000 08:07 213178     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-pi-gtk-3235.so
b0ff8000-b0ffa000 rwxp 0004a000 08:07 213178     /home/sumiravi/Programs/eclipse/configuration/org.eclipse.osgi/bundles/327/1/.cp/libswt-pi-gtk-3235.so
b0ffa000-b1010000 r-xs 00000000 08:07 167038     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.commands_3.2.0.I20060605-1400.jar
b1010000-b102f000 r-xs 00000000 08:07 166985     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui_3.2.1.M20060913-0800.jar
b102f000-b11e4000 r-xs 00000000 08:07 167035     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.1.v3235.jar
b11e4000-b11e7000 r-xs 00000000 08:07 166992     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.swt_3.2.1.v3235e.jar
b11e7000-b12ae000 r-xs 00000000 08:07 167037     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.jface_3.2.1.M20060908-1000.jar
b12ae000-b159d000 r-xs 00000000 08:07 166982     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.workbench_3.2.1.M20060906-0800.jar
b159d000-b1731000 r-xs 00000000 08:07 166981     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.ide_3.2.1.M20060915-1030.jar
b1731000-b1746000 r-xs 00000000 08:07 166996     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar
b1746000-b1759000 r-xs 00000000 08:07 166991     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.jobs_3.2.0.v20060603.jar
b1759000-b177d000 r-xs 00000000 08:07 166970     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar
b177d000-b1780000 ---p b177d000 00:00 0 
b1780000-b17fe000 rwxp b1780000 00:00 0 
b17fe000-b1801000 ---p b17fe000 00:00 0 
b1801000-b187f000 rwxp b1801000 00:00 0 
b187f000-b1882000 ---p b187f000 00:00 0 
b1882000-b1a00000 rwxp b1882000 00:00 0 
b1a00000-b1afd000 rwxp b1a00000 00:00 0 
b1afd000-b1b00000 ---p b1afd000 00:00 0 
b1b00000-b1b01000 r-xp 00000000 08:08 1358383    /usr/lib/locale/en_IN/LC_MEASUREMENT
b1b01000-b1b05000 r-xp 00000000 08:08 1308399    /usr/lib/libXtst.so.6.1.0
b1b05000-b1b06000 rwxp 00004000 08:08 1308399    /usr/lib/libXtst.so.6.1.0
b1b06000-b1b1d000 r-xs 00000000 08:07 167009     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.equinox.preferences_3.2.1.R32x_v20060717.jar
b1b1d000-b1b30000 r-xs 00000000 08:07 167040     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar
b1b30000-b1c00000 r-xs 00000000 08:07 167012     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.osgi_3.2.1.R32x_v20060919.jar
b1c00000-b1d00000 rwxp b1c00000 00:00 0 
b1d00000-b1d04000 r-xp 00000000 08:08 1308762    /usr/lib/libgthread-2.0.so.0.1400.1
b1d04000-b1d05000 rwxp 00003000 08:08 1308762    /usr/lib/libgthread-2.0.so.0.1400.1
b1d05000-b1d1b000 r-xs 00000000 08:07 166965     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.update.configurator_3.2.1.v20092006.jar
b1d1b000-b1d2f000 r-xs 00000000 08:07 167039     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar
b1d2f000-b1d36000 r-xp 00000000 08:08 1457886    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libnio.so
b1d36000-b1d37000 rwxp 00006000 08:08 1457886    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libnio.so
b1d37000-b1d3a000 rwxp b1d37000 00:00 0 
b1d3a000-b1db8000 rwxp b1d3a000 00:00 0 
b1db8000-b1e7d000 r-xs 00000000 08:08 1472285    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext/localedata.jar
b1e7d000-b1e7e000 ---p b1e7d000 00:00 0 
b1e7e000-b1efe000 rwxp b1e7e000 00:00 0 
b1efe000-b1f01000 ---p b1efe000 00:00 0 
b1f01000-b1f7f000 rwxp b1f01000 00:00 0 
b1f7f000-b1f82000 ---p b1f7f000 00:00 0 
b1f82000-b2100000 rwxp b1f82000 00:00 0 
b2100000-b2101000 r-xp 00000000 08:08 1358382    /usr/lib/locale/en_IN/LC_IDENTIFICATION
b2101000-b2106000 r-xs 00000000 08:07 166968     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.runtime.compatibility.auth_3.2.0.v20060601.jar
b2106000-b2117000 r-xp 00000000 08:08 1457885    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libnet.so
b2117000-b2118000 rwxp 00011000 08:08 1457885    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libnet.so
b2118000-b2143000 r-xs 00000000 08:08 1471691    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext/sunpkcs11.jar
b2143000-b216a000 r-xs 00000000 08:08 1472283    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext/sunjce_provider.jar
b216a000-b2173000 r-xs 00000000 08:07 167060     /home/sumiravi/Programs/eclipse/startup.jar
b2173000-b2176000 ---p b2173000 00:00 0 
b2176000-b21f4000 rwxp b2176000 00:00 0 
b21f4000-b2233000 r-xp 00000000 08:08 1358381    /usr/lib/locale/en_IN/LC_CTYPE
b2233000-b2236000 ---p b2233000 00:00 0 
b2236000-b22b4000 rwxp b2236000 00:00 0 
b22b4000-b22b7000 ---p b22b4000 00:00 0 
b22b7000-b2335000 rwxp b22b7000 00:00 0 
b2335000-b2336000 ---p b2335000 00:00 0 
b2336000-b23db000 rwxp b2336000 00:00 0 
b23db000-b23e3000 rwxp b23db000 00:00 0 
b23e3000-b25e9000 rwxp b23e3000 00:00 0 
b25e9000-b25f0000 rwxp b25e9000 00:00 0 
b25f0000-b2621000 rwxp b25f0000 00:00 0 
b2621000-b267b000 rwxp b2621000 00:00 0 
b267b000-b2feb000 rwxp b267b000 00:00 0 
b2feb000-b467b000 rwxp b2feb000 00:00 0 
b467b000-b4eea000 r-xs 00000000 08:08 1457986    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/charsets.jar
b4eea000-b4eff000 r-xs 00000000 08:08 1457985    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/jce.jar
b4eff000-b4f84000 r-xs 00000000 08:08 1457984    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/jsse.jar
b4f84000-b4fed000 rwxp b4f84000 00:00 0 
b4fed000-b7616000 r-xs 00000000 08:08 1457937    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/rt.jar
b7616000-b7625000 r-xp 00000000 08:08 1457882    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libzip.so
b7625000-b7627000 rwxp 0000e000 08:08 1457882    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libzip.so
b7627000-b7648000 r-xp 00000000 08:08 1457881    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libjava.so
b7648000-b764a000 rwxp 00020000 08:08 1457881    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libjava.so
b764a000-b7655000 r-xp 00000000 08:08 1457880    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libverify.so
b7655000-b7656000 rwxp 0000b000 08:08 1457880    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/libverify.so
b7656000-b765f000 r-xp 00000000 08:01 473825     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b765f000-b7661000 rwxp 00008000 08:01 473825     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7661000-b7669000 r-xp 00000000 08:01 473829     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7669000-b766b000 rwxp 00007000 08:01 473829     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b766b000-b7672000 r-xp 00000000 08:01 473821     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7672000-b7674000 rwxp 00006000 08:01 473821     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7674000-b7688000 r-xp 00000000 08:01 473819     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7688000-b768a000 rwxp 00013000 08:01 473819     /lib/tls/i686/cmov/libnsl-2.6.1.so
b768a000-b768c000 rwxp b768a000 00:00 0 
b768c000-b768d000 r-xs 00000000 08:07 212980     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.ui.workbench.compatibility_3.2.0.I20060605-1400/compatibility.jar
b768d000-b768f000 r-xs 00000000 08:07 212428     /home/sumiravi/Programs/eclipse/plugins/org.eclipse.core.runtime.compatibility.registry_3.2.1.R32x_v20060907/runtime_registry_compatibility.jar
b768f000-b7697000 rwxs 00000000 08:01 1400817    /tmp/hsperfdata_sumiravi/10452
b7697000-b76ba000 r-xp 00000000 08:01 473816     /lib/tls/i686/cmov/libm-2.6.1.so
b76ba000-b76bc000 rwxp 00023000 08:01 473816     /lib/tls/i686/cmov/libm-2.6.1.so
b76bc000-b7a2e000 r-xp 00000000 08:08 1471682    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/libjvm.so
b7a2e000-b7a4d000 rwxp 00371000 08:08 1471682    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client/libjvm.so
b7a4d000-b7e64000 rwxp b7a4d000 00:00 0 
b7e64000-b7fa8000 r-xp 00000000 08:01 473808     /lib/tls/i686/cmov/libc-2.6.1.so
b7fa8000-b7fa9000 r-xp 00143000 08:01 473808     /lib/tls/i686/cmov/libc-2.6.1.so
b7fa9000-b7fab000 rwxp 00144000 08:01 473808     /lib/tls/i686/cmov/libc-2.6.1.so
b7fab000-b7faf000 rwxp b7fab000 00:00 0 
b7faf000-b7fb1000 r-xp 00000000 08:01 473814     /lib/tls/i686/cmov/libdl-2.6.1.so
b7fb1000-b7fb3000 rwxp 00001000 08:01 473814     /lib/tls/i686/cmov/libdl-2.6.1.so
b7fb3000-b7fc7000 r-xp 00000000 08:01 473834     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7fc7000-b7fc9000 rwxp 00013000 08:01 473834     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7fc9000-b7fcb000 rwxp b7fc9000 00:00 0 
b7fcb000-b7fcd000 r-xs 00000000 08:08 1472284    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/ext/dnsns.jar
b7fcd000-b7fd3000 r-xp 00000000 08:08 1457873    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/native_threads/libhpi.so
b7fd3000-b7fd4000 rwxp 00006000 08:08 1457873    /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/native_threads/libhpi.so
b7fd4000-b7fd5000 rwxp b7fd4000 00:00 0 
b7fd5000-b7fd6000 r-xp b7fd5000 00:00 0 
b7fd6000-b7fd8000 rwxp b7fd6000 00:00 0 
b7fd8000-b7ff2000 r-xp 00000000 08:01 439796     /lib/ld-2.6.1.so
b7ff2000-b7ff4000 rwxp 00019000 08:01 439796     /lib/ld-2.6.1.so
bfa5d000-bfa60000 ---p bfa5d000 00:00 0 
bfa60000-bfc5d000 rwxp bfa60000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -Xms512m -Xmx512m
java_command: /home/sumiravi/Programs/eclipse/startup.jar -os linux -ws gtk -arch x86 -launcher /home/sumiravi/Programs/eclipse/eclipse -name Eclipse -showsplash 600 -exitdata 17000d -vm /usr/bin/java -vmargs -Xms512m -Xmx512m -jar /home/sumiravi/Programs/eclipse/startup.jar
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=sumiravi
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/lib/i386:/usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/../lib/i386:/usr/lib/firefox/
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x32b400], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x32b400], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x28ec50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGILL: [libjvm.so+0x28ec50], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x2910a0], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x290ad0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x290ad0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x290ad0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x290ad0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 5618, NOFILE 1024, AS infinity
load average:0.18 0.13 0.14

CPU:total 2 (cores per cpu 1, threads per core 2) family 15 model 6 stepping 5, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ht

Memory: 4k page, physical 708744k(21488k free), swap 2048248k(2013460k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_13-b05) for linux-x86, built on Sep 25 2007 19:49:16 by java_re with gcc 3.2.1-7a (J2SE release)

---

### Post by prince_niceguy on 2007-12-29
seems eclipse process is running out of memory... note the permanent memory is 99% used. try creating an eclipse.sh like the one attached and see if it works for you. I have increased mine to 1GB or so, you can increase further if it is crashing seems you are using some heavy plugins in eclipse...

---

### Post by scienceandtech on 2008-01-07
Installing Java 6 eliminated the problem. But I would like to know why it happened

---

