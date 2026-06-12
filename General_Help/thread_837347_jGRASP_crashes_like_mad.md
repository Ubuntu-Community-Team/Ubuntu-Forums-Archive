---
title: "jGRASP crashes like mad"
date: 2008-06-22
forum: General Help
---

### Post by lost09 on 2008-06-22
jGRASP (or perhaps the JRE itself) is crashing like mad on hardy. Fortunately the .java and .class files remain intact, but having to restart the IDE every half hour is rather irritating. The error file is posted below. Any help would be most appreciated. 

> #
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb7f2dcec, pid=6314, tid=3033668496
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode, sharing linux-x86)
# Problematic frame:
# C  [libpthread.so.0+0x9cec]  pthread_cond_timedwait+0xc
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0x085ee400):  JavaThread "Thread-3" [_thread_blocked, id=6455, stack(0xb4cd1000,0xb4d22000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0xa8b4d210

Registers:
EAX=0xb4d20c18, EBX=0xb4d20c18, ECX=0x00000000, EDX=0x08500c68
ESP=0xb4d20bc1, EBP=0xa8b4d20c, ESI=0xb4d20be8, EDI=0x085ea880
EIP=0xb7f2dcec, CR2=0xa8b4d210, EFLAGS=0x00010246

Top of Stack: (sp=0xb4d20bc1)
0xb4d20bc1:   b7f38ff4 b4d20be8 085ea880 b4d20be8
0xb4d20bd1:   b7f2e34f b4d20c18 58000000 a8b4d20c
0xb4d20be1:   00085ea8 18085ee4 11b4d20c c0063121
0xb4d20bf1:   a8085ea8 58085ea8 3eb4d20c 2500be53
0xb4d20c01:   4e485e6f c0000616 58085ea8 00b4d20c
0xb4d20c11:   a8085ee4 08085ea8 2fb4d20d 800630f4
0xb4d20c21:   58085ea8 00b4d20c 00000000 b6000000
0xb4d20c31:   63722934 b6000002 63722934 00000002 

Instructions: (pc=0xb7f2dcec)
0xb7f2dcdc:   90 90 90 90 55 57 56 53 8b 5c 24 14 8b 6c 24 1c
0xb7f2dcec:   81 7d 04 00 ca 9a 3b b8 16 00 00 00 0f 83 9e 01 

Stack: [0xb4cd1000,0xb4d22000],  sp=0xb4d20bc1,  free space=318k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libpthread.so.0+0x9cec]  pthread_cond_timedwait+0xc

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J  java.lang.Thread.sleep(J)V
J  x0.a(I)V
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x085ee400 JavaThread "Thread-3" [_thread_blocked, id=6455, stack(0xb4cd1000,0xb4d22000)]
  0x084f7000 JavaThread "TimerQueue" daemon [_thread_blocked, id=6447, stack(0xb5011000,0xb5062000)]
  0x08454000 JavaThread "jGRASPTimer" daemon [_thread_blocked, id=6343, stack(0xb50a9000,0xb50fa000)]
  0x08058c00 JavaThread "DestroyJavaVM" [_thread_blocked, id=6315, stack(0xb7d50000,0xb7da1000)]
  0x082e7000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=6327, stack(0xb528a000,0xb52db000)]
  0x082e5800 JavaThread "AWT-Shutdown" [_thread_blocked, id=6326, stack(0xb530f000,0xb5360000)]
  0x082e1c00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=6325, stack(0xb5360000,0xb53b1000)]
  0x082ad400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=6324, stack(0xb53dd000,0xb542e000)]
  0x08096c00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=6322, stack(0xb592c000,0xb597d000)]
  0x0808c000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=6321, stack(0xb597d000,0xb59fe000)]
  0x0808ac00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=6320, stack(0xb59fe000,0xb5a4f000)]
  0x08081c00 JavaThread "Finalizer" daemon [_thread_blocked, id=6319, stack(0xb5a95000,0xb5ae6000)]
  0x08080800 JavaThread "Reference Handler" daemon [_thread_blocked, id=6318, stack(0xb5ae6000,0xb5b37000)]

Other Threads:
  0x0807f400 VMThread [stack: 0xb5b37000,0xb5bb8000] [id=6317]
  0x080aa400 WatcherThread [stack: 0xb58ab000,0xb592c000] [id=6323]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 960K, used 863K [0x8c060000, 0x8c160000, 0x8c540000)
  eden space 896K,  94% used [0x8c060000, 0x8c1332e8, 0x8c140000)
  from space 64K,  28% used [0x8c150000, 0x8c154a10, 0x8c160000)
  to   space 64K,   0% used [0x8c140000, 0x8c140000, 0x8c150000)
 tenured generation   total 11472K, used 7886K [0x8c540000, 0x8d074000, 0x90060000)
   the space 11472K,  68% used [0x8c540000, 0x8ccf39d0, 0x8ccf3a00, 0x8d074000)
 compacting perm gen  total 12288K, used 6825K [0x90060000, 0x90c60000, 0x94060000)
   the space 12288K,  55% used [0x90060000, 0x9070a7e0, 0x9070a800, 0x90c60000)
    ro space 8192K,  73% used [0x94060000, 0x946434a0, 0x94643600, 0x94860000)
    rw space 12288K,  58% used [0x94860000, 0x94f58668, 0x94f58800, 0x95460000)

Dynamic libraries:
06000000-0641b000 r-xp 00000000 08:01 2671184    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
0641b000-06435000 rwxp 0041a000 08:01 2671184    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
06435000-06855000 rwxp 06435000 00:00 0 
08048000-08052000 r-xp 00000000 08:01 2671162    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java
08052000-08053000 rwxp 00009000 08:01 2671162    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/bin/java
08053000-0871d000 rwxp 08053000 00:00 0          [heap]
8c060000-8c160000 rwxp 8c060000 00:00 0 
8c160000-8c540000 rwxp 8c160000 00:00 0 
8c540000-8d074000 rwxp 8c540000 00:00 0 
8d074000-90060000 rwxp 8d074000 00:00 0 
90060000-90c60000 rwxp 90060000 00:00 0 
90c60000-94060000 rwxp 90c60000 00:00 0 
94060000-94644000 r-xs 00001000 08:01 2671371    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/classes.jsa
94644000-94860000 rwxp 94644000 00:00 0 
94860000-94f59000 rwxp 005e5000 08:01 2671371    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/classes.jsa
94f59000-95460000 rwxp 94f59000 00:00 0 
95460000-95539000 rwxp 00cde000 08:01 2671371    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/classes.jsa
95539000-95860000 rwxp 95539000 00:00 0 
95860000-95864000 r-xs 00db7000 08:01 2671371    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/classes.jsa
95864000-95c60000 rwxp 95864000 00:00 0 
b4500000-b4535000 rwxp b4500000 00:00 0 
b4535000-b4600000 ---p b4535000 00:00 0 
b466d000-b4900000 rwxs 00000000 00:09 4128780    /SYSV00000000 (deleted)
b4900000-b49fd000 rwxp b4900000 00:00 0 
b49fd000-b4a00000 ---p b49fd000 00:00 0 
b4a00000-b4af2000 rwxp b4a00000 00:00 0 
b4af2000-b4b00000 ---p b4af2000 00:00 0 
b4b00000-b4bff000 rwxp b4b00000 00:00 0 
b4bff000-b4c00000 ---p b4bff000 00:00 0 
b4cd1000-b4cd4000 ---p b4cd1000 00:00 0 
b4cd4000-b4d22000 rwxp b4cd4000 00:00 0 
b4d6b000-b4d6e000 rwxp b4d6b000 00:00 0 
b4d6e000-b4dbc000 rwxp b4d6e000 00:00 0 
b4dbc000-b4dbf000 rwxp b4dbc000 00:00 0 
b4dbf000-b4e0d000 rwxp b4dbf000 00:00 0 
b4e0d000-b4e10000 rwxp b4e0d000 00:00 0 
b4e10000-b4e5e000 rwxp b4e10000 00:00 0 
b4e5e000-b4e61000 rwxp b4e5e000 00:00 0 
b4e61000-b4eaf000 rwxp b4e61000 00:00 0 
b4eaf000-b4eb2000 rwxp b4eaf000 00:00 0 
b4eb2000-b4ffa000 rwxp b4eb2000 00:00 0 
b4ffa000-b5000000 ---p b4ffa000 00:00 0 
b5011000-b5014000 ---p b5011000 00:00 0 
b5014000-b5062000 rwxp b5014000 00:00 0 
b5062000-b5070000 r-xs 00656000 08:01 2621864    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/charsets.jar
b5084000-b5093000 rwxs 00000000 00:09 2686992    /SYSV00000000 (deleted)
b50a2000-b50a9000 r-xs 00110000 08:01 2621915    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/resources.jar
b50a9000-b50ac000 ---p b50a9000 00:00 0 
b50ac000-b50fa000 rwxp b50ac000 00:00 0 
b50fa000-b5159000 r-xs 00b89000 08:01 2621839    /usr/lib/jvm/java-6-sun-1.6.0.06/lib/tools.jar
b5159000-b51ad000 r-xp 00000000 08:01 2621894    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libcmm.so
b51ad000-b51b0000 rwxp 00054000 08:01 2621894    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libcmm.so
b51b0000-b51b3000 rwxp b51b0000 00:00 0 
b51b3000-b5201000 rwxp b51b3000 00:00 0 
b5206000-b5215000 r-xp 00000000 08:01 2785400    /lib/tls/i686/cmov/libresolv-2.7.so
b5215000-b5217000 rwxp 0000f000 08:01 2785400    /lib/tls/i686/cmov/libresolv-2.7.so
b5217000-b5219000 rwxp b5217000 00:00 0 
b522f000-b5236000 r-xp 00000000 08:01 2621880    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
b5236000-b5237000 rwxp 00006000 08:01 2621880    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
b523c000-b523e000 r-xp 00000000 08:01 2785338    /lib/libnss_mdns4.so.2
b523e000-b523f000 rwxp 00001000 08:01 2785338    /lib/libnss_mdns4.so.2
b523f000-b5243000 r-xp 00000000 08:01 2785366    /lib/tls/i686/cmov/libnss_dns-2.7.so
b5243000-b5245000 rwxp 00003000 08:01 2785366    /lib/tls/i686/cmov/libnss_dns-2.7.so
b5245000-b5252000 rwxs 00000000 00:09 4489230    /SYSV00000000 (deleted)
b5252000-b5254000 r-xp 00000000 08:01 2785466    /lib/libnss_mdns4_minimal.so.2
b5254000-b5255000 rwxp 00001000 08:01 2785466    /lib/libnss_mdns4_minimal.so.2
b5262000-b5277000 r-xp 00000000 08:01 2621888    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libdcpr.so
b5277000-b528a000 rwxp 00014000 08:01 2621888    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libdcpr.so
b528a000-b528d000 ---p b528a000 00:00 0 
b528d000-b52db000 rwxp b528d000 00:00 0 
b52db000-b52e1000 r-xs 00000000 08:01 10979802   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b52e1000-b52e4000 r-xs 00000000 08:01 10979800   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b52e4000-b52e5000 r-xs 00000000 08:01 10979799   /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b52e5000-b52e9000 r-xs 00000000 08:01 10979798   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b52e9000-b52ea000 r-xs 00000000 08:01 10979795   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b52ea000-b52eb000 r-xs 00000000 08:01 10979794   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b52eb000-b52ee000 r-xs 00000000 08:01 10979793   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b52ee000-b52f5000 r-xs 00000000 08:01 10979792   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b52f5000-b52f8000 r-xs 00000000 08:01 10979748   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b52f8000-b5300000 r-xs 00000000 08:01 10979790   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5300000-b5308000 r-xs 00000000 08:01 10979842   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5308000-b5309000 r-xs 00000000 08:01 10979787   /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86.cache-2
b5309000-b530a000 r-xs 00000000 08:01 10979785   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b530a000-b530d000 r-xs 00000000 08:01 10979784   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b530f000-b5312000 ---p b530f000 00:00 0 
b5312000-b5360000 rwxp b5312000 00:00 0 
b5360000-b5363000 ---p b5360000 00:00 0 
b5363000-b53b1000 rwxp b5363000 00:00 0 
b53b1000-b53b5000 r-xp 00000000 08:01 18911090   /usr/lib/libXfixes.so.3.1.0
b53b5000-b53b6000 rwxp 00003000 08:01 18911090   /usr/lib/libXfixes.so.3.1.0
b53b6000-b53bd000 r-xp 00000000 08:01 4866201    /usr/lib/libXrender.so.1.3.0
b53bd000-b53be000 rwxp 00007000 08:01 4866201    /usr/lib/libXrender.so.1.3.0
b53be000-b53c6000 r-xp 00000000 08:01 4866217    /usr/lib/libXcursor.so.1.0.2
b53c6000-b53c7000 rwxp 00007000 08:01 4866217    /usr/lib/libXcursor.so.1.0.2
b53c9000-b53dc000 r-xp 00000000 08:01 2621879    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
b53dc000-b53dd000 rwxp 00013000 08:01 2621879    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
b53dd000-b53e0000 ---p b53dd000 00:00 0 
b53e0000-b542e000 rwxp b53e0000 00:00 0 
b542e000-b54ac000 r-xp 00000000 08:01 2621892    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
b54ac000-b54b6000 rwxp 0007e000 08:01 2621892    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
b54b6000-b54bb000 rwxp b54b6000 00:00 0 
b54bb000-b54bf000 r-xp 00000000 08:01 18911084   /usr/lib/libXdmcp.so.6.0.0
b54bf000-b54c0000 rwxp 00003000 08:01 18911084   /usr/lib/libXdmcp.so.6.0.0
b54c0000-b54d7000 r-xp 00000000 08:01 4866176    /usr/lib/libxcb.so.1.0.0
b54d7000-b54d8000 rwxp 00016000 08:01 4866176    /usr/lib/libxcb.so.1.0.0
b54d8000-b54df000 r-xp 00000000 08:01 4866205    /usr/lib/libXi.so.6.0.0
b54df000-b54e0000 rwxp 00006000 08:01 4866205    /usr/lib/libXi.so.6.0.0
b54e0000-b54e4000 r-xp 00000000 08:01 4866209    /usr/lib/libXtst.so.6.1.0
b54e4000-b54e5000 rwxp 00003000 08:01 4866209    /usr/lib/libXtst.so.6.1.0
b54e5000-b55c9000 r-xp 00000000 08:01 4866180    /usr/lib/libX11.so.6.2.0
b55c9000-b55cc000 rwxp 000e4000 08:01 4866180    /usr/lib/libX11.so.6.2.0
b55cc000-b55d9000 r-xp 00000000 08:01 18911088   /usr/lib/libXext.so.6.4.0
b55d9000-b55da000 rwxp 0000d000 08:01 18911088   /usr/lib/libXext.so.6.4.0
b55dc000-b55e3000 r-xs 00000000 08:01 10979781   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b55e3000-b55e8000 r-xs 00000000 08:01 10978401   /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b55e8000-b55ee000 r-xs 00000000 08:01 10977374   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b55ee000-b55f0000 r-xs 00000000 08:01 10978075   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b55f0000-b5631000 r-xp 00000000 08:01 2671189    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
b5631000-b5634000 rwxp 00040000 08:01 2671189    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
b5634000-b56af000 r-xp 00000000 08:01 2621890    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
b56af000-b56b6000 rwxp 0007b000 08:01 2621890    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
b56b6000-b570c000 rwxp b56b6000 00:00 0 
b570c000-b5897000 r-xs 02df0000 08:01 2621935    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar
b5897000-b58ab000 r-xs 00215000 08:01 17625      /home/rith/Desktop/jgrasp/jgrasp.jar
b58ab000-b58ac000 ---p b58ab000 00:00 0 
b58ac000-b592c000 rwxp b58ac000 00:00 0 
b592c000-b592f000 ---p b592c000 00:00 0 
b592f000-b597d000 rwxp b592f000 00:00 0 
b597d000-b5980000 ---p b597d000 00:00 0 
b5980000-b59fe000 rwxp b5980000 00:00 0 
b59fe000-b5a01000 ---p b59fe000 00:00 0 
b5a01000-b5a4f000 rwxp b5a01000 00:00 0 
b5a4f000-b5a56000 r-xs 00000000 08:01 8913141    /usr/lib/gconv/gconv-modules.cache
b5a56000-b5a95000 r-xp 00000000 08:01 65646      /usr/lib/locale/en_US.utf8/LC_CTYPE
b5a95000-b5a98000 ---p b5a95000 00:00 0 
b5a98000-b5ae6000 rwxp b5a98000 00:00 0 
b5ae6000-b5ae9000 ---p b5ae6000 00:00 0 
b5ae9000-b5b37000 rwxp b5ae9000 00:00 0 
b5b37000-b5b38000 ---p b5b37000 00:00 0 
b5b38000-b5bcb000 rwxp b5b38000 00:00 0 
b5bcb000-b5be5000 rwxp b5bcb000 00:00 0 
b5be5000-b5beb000 rwxp b5be5000 00:00 0 
b5beb000-b5c03000 rwxp b5beb000 00:00 0 
b5c03000-b5c04000 rwxp b5c03000 00:00 0 
b5c04000-b5c05000 rwxp b5c04000 00:00 0 
b5c05000-b5c0c000 rwxp b5c05000 00:00 0 
b5c0c000-b5c23000 rwxp b5c0c000 00:00 0 
b5c23000-b5c29000 rwxp b5c23000 00:00 0 
b5c29000-b5c43000 rwxp b5c29000 00:00 0 
b5c43000-b5c64000 rwxp b5c43000 00:00 0 
b5c64000-b5cce000 rwxp b5c64000 00:00 0 
b5cce000-b6246000 rwxp b5cce000 00:00 0 
b6246000-b7cce000 rwxp b6246000 00:00 0 
b7cce000-b7cdd000 r-xp 00000000 08:01 2621875    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b7cdd000-b7cdf000 rwxp 0000e000 08:01 2621875    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b7cdf000-b7d02000 r-xp 00000000 08:01 2621874    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b7d02000-b7d04000 rwxp 00023000 08:01 2621874    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b7d04000-b7d0d000 r-xp 00000000 08:01 2785368    /lib/tls/i686/cmov/libnss_files-2.7.so
b7d0d000-b7d0f000 rwxp 00008000 08:01 2785368    /lib/tls/i686/cmov/libnss_files-2.7.so
b7d0f000-b7d17000 r-xp 00000000 08:01 2785378    /lib/tls/i686/cmov/libnss_nis-2.7.so
b7d17000-b7d19000 rwxp 00007000 08:01 2785378    /lib/tls/i686/cmov/libnss_nis-2.7.so
b7d19000-b7d2d000 r-xp 00000000 08:01 2785362    /lib/tls/i686/cmov/libnsl-2.7.so
b7d2d000-b7d2f000 rwxp 00013000 08:01 2785362    /lib/tls/i686/cmov/libnsl-2.7.so
b7d2f000-b7d31000 rwxp b7d2f000 00:00 0 
b7d31000-b7d32000 r-xp 00000000 08:01 4866178    /usr/lib/libxcb-xlib.so.0.0.0
b7d32000-b7d33000 rwxp 00000000 08:01 4866178    /usr/lib/libxcb-xlib.so.0.0.0
b7d33000-b7d3e000 r-xp 00000000 08:01 2621873    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b7d3e000-b7d3f000 rwxp 0000b000 08:01 2621873    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b7d3f000-b7d47000 rwxs 00000000 08:01 14467127   /tmp/hsperfdata_rith/6314
b7d47000-b7d4e000 r-xp 00000000 08:01 2785402    /lib/tls/i686/cmov/librt-2.7.so
b7d4e000-b7d50000 rwxp 00006000 08:01 2785402    /lib/tls/i686/cmov/librt-2.7.so
b7d50000-b7d53000 ---p b7d50000 00:00 0 
b7d53000-b7da1000 rwxp b7d53000 00:00 0 
b7da1000-b7dc4000 r-xp 00000000 08:01 2785355    /lib/tls/i686/cmov/libm-2.7.so
b7dc4000-b7dc6000 rwxp 00023000 08:01 2785355    /lib/tls/i686/cmov/libm-2.7.so
b7dc6000-b7dc7000 rwxp b7dc6000 00:00 0 
b7dc7000-b7f10000 r-xp 00000000 08:01 2785320    /lib/tls/i686/cmov/libc-2.7.so
b7f10000-b7f11000 r-xp 00149000 08:01 2785320    /lib/tls/i686/cmov/libc-2.7.so
b7f11000-b7f13000 rwxp 0014a000 08:01 2785320    /lib/tls/i686/cmov/libc-2.7.so
b7f13000-b7f16000 rwxp b7f13000 00:00 0 
b7f16000-b7f18000 r-xp 00000000 08:01 2785339    /lib/tls/i686/cmov/libdl-2.7.so
b7f18000-b7f1a000 rwxp 00001000 08:01 2785339    /lib/tls/i686/cmov/libdl-2.7.so
b7f1a000-b7f21000 r-xp 00000000 08:01 2671187    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli/libjli.so
b7f21000-b7f23000 rwxp 00006000 08:01 2671187    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jli/libjli.so
b7f23000-b7f24000 rwxp b7f23000 00:00 0 
b7f24000-b7f38000 r-xp 00000000 08:01 2785396    /lib/tls/i686/cmov/libpthread-2.7.so
b7f38000-b7f3a000 rwxp 00013000 08:01 2785396    /lib/tls/i686/cmov/libpthread-2.7.so
b7f3a000-b7f3c000 rwxp b7f3a000 00:00 0 
b7f3d000-b7f3f000 r-xp 00000000 08:01 18911073   /usr/lib/libXau.so.6.0.0
b7f3f000-b7f40000 rwxp 00001000 08:01 18911073   /usr/lib/libXau.so.6.0.0
b7f40000-b7f47000 r-xp 00000000 08:01 2785364    /lib/tls/i686/cmov/libnss_compat-2.7.so
b7f47000-b7f49000 rwxp 00006000 08:01 2785364    /lib/tls/i686/cmov/libnss_compat-2.7.so
b7f49000-b7f4f000 r-xp 00000000 08:01 2671179    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b7f4f000-b7f50000 rwxp 00006000 08:01 2671179    /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b7f50000-b7f51000 rwxp b7f50000 00:00 0 
b7f51000-b7f52000 r-xp b7f51000 00:00 0 
b7f52000-b7f54000 rwxp b7f52000 00:00 0 
b7f54000-b7f55000 r-xp b7f54000 00:00 0          [vdso]
b7f55000-b7f6f000 r-xp 00000000 08:01 2785293    /lib/ld-2.7.so
b7f6f000-b7f71000 rwxp 00019000 08:01 2785293    /lib/ld-2.7.so
bfc58000-bfc6d000 rwxp bffeb000 00:00 0          [stack]

VM Arguments:
java_command: Grasp -i
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=rith
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/../lib/i386
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x3be710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x3be710], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x30f810], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x311850], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: SIG_IGN, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGTERM: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
libc:glibc 2.7 NPTL 2.7 
rlimit: STACK 8192k, CORE 0k, NPROC 11765, NOFILE 1024, AS infinity
load average:0.01 0.07 0.12

CPU:total 1 (1 cores per cpu, 1 threads per core) family 6 model 13 stepping 8, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1489280k(860272k free), swap 4361608k(4361608k free)

vm_info: Java HotSpot(TM) Client VM (10.0-b22) for linux-x86 JRE (1.6.0_06-b02), built on Mar 25 2008 00:39:19 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Sun Jun 22 11:26:29 2008
elapsed time: 1815 seconds


---

