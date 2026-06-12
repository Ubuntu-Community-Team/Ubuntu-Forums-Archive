---
title: "17 IcedTea errors in home folder???"
date: 2008-02-26
forum: General Help
---

### Post by aliencam on 2008-02-26
I went into my home folder today and saw that I have 17 nearly identical error files.  They were made by IcedTea, the java plugin, which i am using for swiftweasel x64  

I am using ubuntu gutsy x64 and swiftweasel (not firefox) for the x64 chip. 

here is the text of the error file.  I don't know what caused all of these, and I can't think of any websites that use java offhand to test it out... 


```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b823c55ce11, pid=6183, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609400):  JavaThread "main" [_thread_in_vm, id=6185, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609400, RBX=0x0000000000609400, RCX=0x0000000000609400, RDX=0x00002b823b101280
RSP=0x00000000400fe260, RBP=0x00000000400fe290, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd84783, R11=0x00002b823c4cc2f0
R12=0xec01e02000002ab3, R13=0x0000000000609400, R14=0x00000000400fe330, R15=0x00002b823c9626c0
RIP=0x00002b823c55ce11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe260)
0x00000000400fe260:   00000000400fe380 00002aaaaef44fd0
0x00000000400fe270:   0000000000000101 00002aaaaef44fd0
0x00000000400fe280:   00000000400fe330 0000000000609400
0x00000000400fe290:   00000000400fe300 00002aaaabd847b0
0x00000000400fe2a0:   0000000000c405b0 0000000000c405d0
0x00000000400fe2b0:   0000000000c405d8 0000000000c405d8
0x00000000400fe2c0:   00000000400fe2c0 0000000000000000
0x00000000400fe2d0:   00000000400fe330 00002aaaaef48a48
0x00000000400fe2e0:   0000000000000000 00002aaaaef44fd0
0x00000000400fe2f0:   0000000000000000 00000000400fe320
0x00000000400fe300:   00000000400fe380 00002aaaabd78342
0x00000000400fe310:   0000000000000000 00002aaaabd80cee
0x00000000400fe320:   ec01e02000002ab3 0000000000c405b8
0x00000000400fe330:   00002aaad8ba90c0 00000000000000ff
0x00000000400fe340:   00000000400fe340 00002aaaaf507c97
0x00000000400fe350:   00000000400fe398 00002aaaaf50b160
0x00000000400fe360:   0000000000000000 00002aaaaf507cb0
0x00000000400fe370:   00000000400fe320 00000000400fe390
0x00000000400fe380:   00000000400fe3e0 00002aaaabd782b8
0x00000000400fe390:   ec01e02000002ab3 00002aaaabd781e9
0x00000000400fe3a0:   00000000400fe3a0 00002aaaaf507d6c
0x00000000400fe3b0:   00000000400fe400 00002aaaaf50b160
0x00000000400fe3c0:   0000000000000000 00002aaaaf507d90
0x00000000400fe3d0:   00000000400fe390 00000000400fe3f0
0x00000000400fe3e0:   00000000400fe448 00002aaaabd782b8
0x00000000400fe3f0:   0000000000000009 ec01e02000002aaa
0x00000000400fe400:   0000000000000000 00000000400fe408
0x00000000400fe410:   00002aaaaf4dad21 00000000400fe4d8
0x00000000400fe420:   00002aaaaf4e1f38 0000000000000000
0x00000000400fe430:   00002aaaaf4dafb0 00000000400fe3f0
0x00000000400fe440:   00000000400fe4e0 00000000400fe520
0x00000000400fe450:   00002aaaabd7811a 0000000000000000 

Instructions: (pc=0x00002b823c55ce11)
0x00002b823c55ce01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002b823c55ce11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

Stack: [0x0000000040000000,0x0000000040101000],  sp=0x00000000400fe260,  free space=1016k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x5c9e11]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x30ec06]
V  [libjvm.so+0x30fe0d]
V  [libjvm.so+0x3102f1]
V  [libjvm.so+0x389aaa]
V  [libjvm.so+0x3943fa]
C  [libjava.so+0x1242d]  Java_java_lang_Class_forName0+0x15d
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x39b888]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x33b231]
V  [libjvm.so+0x3583d5]
C  [libjli.so+0x3abd]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00000000007ac000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=6207, stack(0x0000000040b0b000,0x0000000040c0c000)]
  0x00000000006ab400 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=6203, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00000000006a8400 JavaThread "CompilerThread1" daemon [_thread_blocked, id=6200, stack(0x0000000040808000,0x0000000040909000)]
  0x00000000006a4800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=6197, stack(0x0000000040707000,0x0000000040808000)]
  0x00000000006a2c00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=6196, stack(0x0000000040606000,0x0000000040707000)]
  0x000000000067bc00 JavaThread "Finalizer" daemon [_thread_blocked, id=6194, stack(0x0000000040505000,0x0000000040606000)]
  0x000000000067a000 JavaThread "Reference Handler" daemon [_thread_blocked, id=6192, stack(0x0000000040404000,0x0000000040505000)]
=>0x0000000000609400 JavaThread "main" [_thread_in_vm, id=6185, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000674800 VMThread [stack: 0x0000000040303000,0x0000000040404000] [id=6190]
  0x00000000006ad400 WatcherThread [stack: 0x0000000040a0a000,0x0000000040b0b000] [id=6205]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 14016K, used 4101K [0x00002aaad8ba0000, 0x00002aaad9b40000, 0x00002aaae8640000)
  eden space 12032K, 34% used [0x00002aaad8ba0000,0x00002aaad8fa1520,0x00002aaad9760000)
  from space 1984K, 0% used [0x00002aaad9950000,0x00002aaad9950000,0x00002aaad9b40000)
  to   space 1984K, 0% used [0x00002aaad9760000,0x00002aaad9760000,0x00002aaad9950000)
 PSOldGen        total 32064K, used 0K [0x00002aaab9640000, 0x00002aaabb590000, 0x00002aaad8ba0000)
  object space 32064K, 0% used [0x00002aaab9640000,0x00002aaab9640000,0x00002aaabb590000)
 PSPermGen       total 21248K, used 6959K [0x00002aaaaee40000, 0x00002aaab0300000, 0x00002aaab9640000)
  object space 21248K, 32% used [0x00002aaaaee40000,0x00002aaaaf50be70,0x00002aaab0300000)

Dynamic libraries:
00400000-00401000 r-xp 00000000 08:01 10422822                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00600000-00601000 rw-p 00000000 08:01 10422822                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00601000-00dd3000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40203000 ---p 40202000 00:00 0 
40203000-40303000 rwxp 40203000 00:00 0 
40303000-40304000 ---p 40303000 00:00 0 
40304000-40404000 rwxp 40304000 00:00 0 
40404000-40407000 ---p 40404000 00:00 0 
40407000-40505000 rwxp 40407000 00:00 0 
40505000-40508000 ---p 40505000 00:00 0 
40508000-40606000 rwxp 40508000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-4080b000 ---p 40808000 00:00 0 
4080b000-40909000 rwxp 4080b000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
40a0a000-40a0b000 ---p 40a0a000 00:00 0 
40a0b000-40b0b000 rwxp 40a0b000 00:00 0 
40b0b000-40b0e000 ---p 40b0b000 00:00 0 
40b0e000-40c0c000 rwxp 40b0e000 00:00 0 
2aaaaaac2000-2aaaaaaca000 r-xp 00000000 08:01 12517977                   /lib/librt-2.6.1.so
2aaaaaaca000-2aaaaacc9000 ---p 00008000 08:01 12517977                   /lib/librt-2.6.1.so
2aaaaacc9000-2aaaaaccb000 rw-p 00007000 08:01 12517977                   /lib/librt-2.6.1.so
2aaaaaccb000-2aaaaaccc000 r--p 2aaaaaccb000 00:00 0 
2aaaaaccc000-2aaaaaccd000 rw-p 2aaaaaccc000 00:00 0 
2aaaaaccd000-2aaaaacd5000 r-xp 00000000 08:01 10422814                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd5000-2aaaaaed4000 ---p 00008000 08:01 10422814                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed4000-2aaaaaed6000 rw-p 00007000 08:01 10422814                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed6000-2aaaaaede000 rw-s 00000000 08:01 3801163                    /tmp/hsperfdata_cameron/6183
2aaaaaeeb000-2aaaaaf01000 r-xp 00000000 08:01 12517967                   /lib/libnsl-2.6.1.so
2aaaaaf01000-2aaaab100000 ---p 00016000 08:01 12517967                   /lib/libnsl-2.6.1.so
2aaaab100000-2aaaab102000 rw-p 00015000 08:01 12517967                   /lib/libnsl-2.6.1.so
2aaaab102000-2aaaab104000 rw-p 2aaaab102000 00:00 0 
2aaaab104000-2aaaab10c000 r-xp 00000000 08:01 12517968                   /lib/libnss_compat-2.6.1.so
2aaaab10c000-2aaaab30b000 ---p 00008000 08:01 12517968                   /lib/libnss_compat-2.6.1.so
2aaaab30b000-2aaaab30d000 rw-p 00007000 08:01 12517968                   /lib/libnss_compat-2.6.1.so
2aaaab30d000-2aaaab317000 r-xp 00000000 08:01 12517972                   /lib/libnss_nis-2.6.1.so
2aaaab317000-2aaaab516000 ---p 0000a000 08:01 12517972                   /lib/libnss_nis-2.6.1.so
2aaaab516000-2aaaab518000 rw-p 00009000 08:01 12517972                   /lib/libnss_nis-2.6.1.so
2aaaab518000-2aaaab522000 r-xp 00000000 08:01 12517970                   /lib/libnss_files-2.6.1.so
2aaaab522000-2aaaab721000 ---p 0000a000 08:01 12517970                   /lib/libnss_files-2.6.1.so
2aaaab721000-2aaaab723000 rw-p 00009000 08:01 12517970                   /lib/libnss_files-2.6.1.so
2aaaab723000-2aaaab731000 r-xp 00000000 08:01 10422811                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab731000-2aaaab930000 ---p 0000e000 08:01 10422811                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab930000-2aaaab932000 rw-p 0000d000 08:01 10422811                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab932000-2aaaab960000 r-xp 00000000 08:01 10422792                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab960000-2aaaabb5f000 ---p 0002e000 08:01 10422792                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5f000-2aaaabb63000 rw-p 0002d000 08:01 10422792                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb63000-2aaaabb73000 r-xp 00000000 08:01 10422812                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb73000-2aaaabd73000 ---p 00010000 08:01 10422812                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd73000-2aaaabd75000 rw-p 00010000 08:01 10422812                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd75000-2aaaabfe5000 rwxp 2aaaabd75000 00:00 0 
2aaaabfe5000-2aaaaed75000 rwxp 2aaaabfe5000 00:00 0 
2aaaaed75000-2aaaaed7f000 rwxp 2aaaaed75000 00:00 0 
2aaaaed7f000-2aaaaee35000 rwxp 2aaaaed7f000 00:00 0 
2aaaaee40000-2aaab0300000 rwxp 2aaaaee40000 00:00 0 
2aaab0300000-2aaab9640000 rwxp 2aaab0300000 00:00 0 
2aaab9640000-2aaabb590000 rwxp 2aaab9640000 00:00 0 
2aaabb590000-2aaad8ba0000 rwxp 2aaabb590000 00:00 0 
2aaad8ba0000-2aaad9b40000 rwxp 2aaad8ba0000 00:00 0 
2aaad9b40000-2aaae8640000 rwxp 2aaad9b40000 00:00 0 
2aaae8640000-2aaae864b000 rwxp 2aaae8640000 00:00 0 
2aaae864b000-2aaae8694000 rwxp 2aaae864b000 00:00 0 
2aaae8694000-2aaae86a4000 rwxp 2aaae8694000 00:00 0 
2aaae86a4000-2aaae878e000 rwxp 2aaae86a4000 00:00 0 
2aaae878e000-2aaae8797000 rwxp 2aaae878e000 00:00 0 
2aaae8797000-2aaae880c000 rwxp 2aaae8797000 00:00 0 
2aaae880c000-2aaae881d000 rwxp 2aaae880c000 00:00 0 
2aaae881d000-2aaae8908000 rwxp 2aaae881d000 00:00 0 
2aaae8908000-2aaae8913000 rwxp 2aaae8908000 00:00 0 
2aaae8913000-2aaae895c000 rwxp 2aaae8913000 00:00 0 
2aaae895c000-2aaae8984000 rw-p 2aaae895c000 00:00 0 
2aaae8984000-2aaae8afe000 r--s 035c6000 08:01 10306348                   /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaae8afe000-2aaae8b91000 rw-p 2aaae8afe000 00:00 0 
2aaae8b91000-2aaae8bd0000 r--p 00000000 08:01 9978873                    /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaae8bd0000-2aaae8bd7000 r--s 00000000 08:01 9929227                    /usr/lib/gconv/gconv-modules.cache
2aaae8bd7000-2aaae8c75000 r-xp 00000000 08:01 10422781                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae8c75000-2aaae8e74000 ---p 0009e000 08:01 10422781                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae8e74000-2aaae8e80000 rw-p 0009d000 08:01 10422781                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae8e80000-2aaae8ea4000 rw-p 2aaae8e80000 00:00 0 
2aaae8ea4000-2aaae8eec000 r-xp 00000000 08:01 10422819                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae8eec000-2aaae90ec000 ---p 00048000 08:01 10422819                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae90ec000-2aaae90ef000 rw-p 00048000 08:01 10422819                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae90ef000-2aaae90f1000 rw-p 2aaae90ef000 00:00 0 
2aaae90f1000-2aaae90fa000 r--s 00065000 08:01 10306321                   /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaae9106000-2aaae9108000 r-xp 00000000 08:01 9913661                    /usr/lib/libXinerama.so.1.0.0
2aaae9108000-2aaae9307000 ---p 00002000 08:01 9913661                    /usr/lib/libXinerama.so.1.0.0
2aaae9307000-2aaae9308000 rw-p 00001000 08:01 9913661                    /usr/lib/libXinerama.so.1.0.0
2aaae9308000-2aaae9319000 r-xp 00000000 08:01 9913651                    /usr/lib/libXext.so.6.4.0
2aaae9319000-2aaae9518000 ---p 00011000 08:01 9913651                    /usr/lib/libXext.so.6.4.0
2aaae9518000-2aaae9519000 rw-p 00010000 08:01 9913651                    /usr/lib/libXext.so.6.4.0
2aaae9519000-2aaae951e000 r-xp 00000000 08:01 9913679                    /usr/lib/libXtst.so.6.1.0
2aaae951e000-2aaae971e000 ---p 00005000 08:01 9913679                    /usr/lib/libXtst.so.6.1.0
2aaae971e000-2aaae971f000 rw-p 00005000 08:01 9913679                    /usr/lib/libXtst.so.6.1.0
2aaae971f000-2aaae9727000 r-xp 00000000 08:01 9913659                    /usr/lib/libXi.so.6.0.0
2aaae9727000-2aaae9927000 ---p 00008000 08:01 9913659                    /usr/lib/libXi.so.6.0.0
2aaae9927000-2aaae9928000 rw-p 00008000 08:01 9913659                    /usr/lib/libXi.so.6.0.0
2aaae9928000-2aaae996e000 r-xp 00000000 08:01 10422784                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae996e000-2aaae9b6d000 ---p 00046000 08:01 10422784                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae9b6d000-2aaae9b71000 rw-p 00045000 08:01 10422784                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae9b71000-2aaae9b81000 rw-p 2aaae9b71000 00:00 0 
2aaae9b96000-2aaae9c10000 r-xp 00000000 08:01 9913852                    /usr/lib/libfreetype.so.6.3.16
2aaae9c10000-2aaae9e10000 ---p 0007a000 08:01 9913852                    /usr/lib/libfreetype.so.6.3.16
2aaae9e10000-2aaae9e15000 rw-p 0007a000 08:01 9913852                    /usr/lib/libfreetype.so.6.3.16
2aaae9e15000-2aaae9e22000 r-xp 00000000 08:01 12517442                   /lib/libgcc_s.so.1
2aaae9e22000-2aaaea022000 ---p 0000d000 08:01 12517442                   /lib/libgcc_s.so.1
2aaaea022000-2aaaea023000 rw-p 0000d000 08:01 12517442                   /lib/libgcc_s.so.1
2aaaea023000-2aaaea039000 r-xp 00000000 08:01 9914412                    /usr/lib/libz.so.1.2.3.3
2aaaea039000-2aaaea239000 ---p 00016000 08:01 9914412                    /usr/lib/libz.so.1.2.3.3
2aaaea239000-2aaaea23a000 rw-p 00016000 08:01 9914412                    /usr/lib/libz.so.1.2.3.3
2aaaea23a000-2aaaea240000 r--s 000f6000 08:01 10306345                   /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaaea240000-2aaaea26f000 r-xp 00000000 08:01 10422801                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaaea26f000-2aaaea46e000 ---p 0002f000 08:01 10422801                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaaea46e000-2aaaea470000 rw-p 0002e000 08:01 10422801                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaaea470000-2aaaea472000 rw-p 2aaaea470000 00:00 0 
2aaaea692000-2aaaea699000 r--s 00000000 08:01 14550147                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaea699000-2aaaea69e000 r--s 00000000 08:01 14550001                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaea69e000-2aaaea6a4000 r--s 00000000 08:01 14550149                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaea6a4000-2aaaea6ae000 r--s 00000000 08:01 14550217                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaea6ae000-2aaaea6af000 r--s 00000000 08:01 14550004                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaea6af000-2aaaea6b7000 r--s 00000000 08:01 14550005                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaea6b7000-2aaaea6bd000 r--s 00000000 08:01 14550150                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaea6bd000-2aaaea6be000 r--s 00000000 08:01 14550007                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaea6be000-2aaaea6bf000 r--s 00000000 08:01 14550151                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaaea6bf000-2aaaea6c0000 r--s 00000000 08:01 14550008                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaea6c0000-2aaaea6c3000 r--s 00000000 08:01 14550009                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaea6c3000-2aaaea6c6000 r--s 00000000 08:01 14550010                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaea6c6000-2aaaea6cc000 r--s 00000000 08:01 14550011                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaea6cc000-2aaaea6d3000 r--s 00000000 08:01 14550012                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaea6d3000-2aaaea6d4000 r--s 00000000 08:01 14550013                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaea6d4000-2aaaea6d6000 r--s 00000000 08:01 14550014                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaea6d6000-2aaaea6d7000 r--s 00000000 08:01 14550015                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaea6d7000-2aaaea6d9000 r--s 00000000 08:01 14550016                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaea6d9000-2aaaea6e2000 r--s 00000000 08:01 14550152                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaea6e2000-2aaaea6e6000 r--s 00000000 08:01 14550018                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaea6e6000-2aaaea6e9000 r--s 00000000 08:01 14550153                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaaea6e9000-2aaaea6ea000 r--s 00000000 08:01 14550154                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaaea6ea000-2aaaea6eb000 r--s 00000000 08:01 14550020                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaea6eb000-2aaaea6ec000 r--s 00000000 08:01 14550021                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaaea6ec000-2aaaea6f6000 r--s 00000000 08:01 14549809                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaaea6f6000-2aaaea6fa000 r--s 00000000 08:01 14549062                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaaea6fa000-2aaaea701000 r--s 00000000 08:01 14549986                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaaea701000-2aaaea704000 r--s 00000000 08:01 14549987                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaaea704000-2aaaea723000 r--s 00000000 08:01 14550057                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaaea723000-2aaaea724000 r--s 00000000 08:01 14549988                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaaea724000-2aaaea72c000 r--s 00000000 08:01 14549989                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaaea72c000-2aaaea737000 r--s 00000000 08:01 14549990                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaaea737000-2aaaea73a000 r--s 00000000 08:01 14549991                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaaea73a000-2aaaea742000 r--s 00000000 08:01 14550218                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaaea742000-2aaaea744000 r--s 00000000 08:01 14549993                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaaea744000-2aaaea748000 r--s 00000000 08:01 14549994                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaaea748000-2aaaea749000 r--s 00000000 08:01 14549995                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaaea749000-2aaaea74a000 r--s 00000000 08:01 14549996                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaaea74a000-2aaaea74f000 r--s 00000000 08:01 14549997                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaaea74f000-2aaaea752000 r--s 00000000 08:01 14549998                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaaea752000-2aaaea75a000 r--s 00000000 08:01 14549077                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaaea97d000-2aaaea984000 r--s 00000000 08:01 14550147                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaaea984000-2aaaea989000 r--s 00000000 08:01 14550001                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaaea989000-2aaaea98f000 r--s 00000000 08:01 14550149                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaaea98f000-2aaaea999000 r--s 00000000 08:01 14550217                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaaea999000-2aaaea99a000 r--s 00000000 08:01 14550004                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaaea99a000-2aaaea9a2000 r--s 00000000 08:01 14550005                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaaea9a2000-2aaaea9a8000 r--s 00000000 08:01 14550150                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaaea9a8000-2aaaea9a9000 r--s 00000000 08:01 14550007                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaaea9a9000-2aaaea9aa000 r--s 00000000 08:01 14550151                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaaea9aa000-2aaaea9ab000 r--s 00000000 08:01 14550008                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaaea9ab000-2aaaea9ae000 r--s 00000000 08:01 14550009                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaaea9ae000-2aaaea9b1000 r--s 00000000 08:01 14550010                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaaea9b1000-2aaaea9b7000 r--s 00000000 08:01 14550011                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaaea9b7000-2aaaea9be000 r--s 00000000 08:01 14550012                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaaea9be000-2aaaea9bf000 r--s 00000000 08:01 14550013                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaaea9bf000-2aaaea9c1000 r--s 00000000 08:01 14550014                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaaea9c1000-2aaaea9c2000 r--s 00000000 08:01 14550015                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaaea9c2000-2aaaea9c4000 r--s 00000000 08:01 14550016                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaaea9c4000-2aaaea9cd000 r--s 00000000 08:01 14550152                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaaea9cd000-2aaaea9d1000 r--s 00000000 08:01 14550018                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaaea9d1000-2aaaea9d4000 r--s 00000000 08:01 14550153                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaaea9d4000-2aaaea9d5000 r--s 00000000 08:01 14550154                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaaea9d5000-2aaaea9d6000 r--s 00000000 08:01 14550020                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaaea9d6000-2aaaea9d7000 r--s 00000000 08:01 14550021                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaaea9d7000-2aaaea9e1000 r--s 00000000 08:01 14549809                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaaea9e1000-2aaaea9e5000 r--s 00000000 08:01 14549062                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaaea9e5000-2aaaea9ec000 r--s 00000000 08:01 14549986                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaaea9ec000-2aaaea9ef000 r--s 00000000 08:01 14549987                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaaea9ef000-2aaaeaa0e000 r--s 00000000 08:01 14550057                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaaeaa0e000-2aaaeaa0f000 r--s 00000000 08:01 14549988                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaaeaa0f000-2aaaeaa17000 r--s 00000000 08:01 14549989                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaaeaa17000-2aaaeaa22000 r--s 00000000 08:01 14549990                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaaeaa22000-2aaaeaa25000 r--s 00000000 08:01 14549991                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaaeaa25000-2aaaeaa2d000 r--s 00000000 08:01 14550218                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaaeaa2d000-2aaaeaa2f000 r--s 00000000 08:01 14549993                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaaeaa2f000-2aaaeaa33000 r--s 00000000 08:01 14549994                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaaeaa33000-2aaaeaa34000 r--s 00000000 08:01 14549995                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaaeaa34000-2aaaeaa35000 r--s 00000000 08:01 14549996                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaaeaa35000-2aaaeaa3a000 r--s 00000000 08:01 14549997                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaaeaa3a000-2aaaeaa3d000 r--s 00000000 08:01 14549998                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaaeaa3d000-2aaaeaa45000 r--s 00000000 08:01 14549077                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaaec000000-2aaaec081000 rw-p 2aaaec000000 00:00 0 
2aaaec081000-2aaaf0000000 ---p 2aaaec081000 00:00 0 
2b823accd000-2b823acea000 r-xp 00000000 08:01 12517388                   /lib/ld-2.6.1.so
2b823acea000-2b823aced000 rw-p 2b823acea000 00:00 0 
2b823aee9000-2b823aeeb000 rw-p 0001c000 08:01 12517388                   /lib/ld-2.6.1.so
2b823aeeb000-2b823af01000 r-xp 00000000 08:01 12517975                   /lib/libpthread-2.6.1.so
2b823af01000-2b823b100000 ---p 00016000 08:01 12517975                   /lib/libpthread-2.6.1.so
2b823b100000-2b823b102000 rw-p 00015000 08:01 12517975                   /lib/libpthread-2.6.1.so
2b823b102000-2b823b106000 rw-p 2b823b102000 00:00 0 
2b823b106000-2b823b210000 r-xp 00000000 08:01 9913630                    /usr/lib/libX11.so.6.2.0
2b823b210000-2b823b410000 ---p 0010a000 08:01 9913630                    /usr/lib/libX11.so.6.2.0
2b823b410000-2b823b417000 rw-p 0010a000 08:01 9913630                    /usr/lib/libX11.so.6.2.0
2b823b417000-2b823b427000 r-xp 00000000 08:01 10422779                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b823b427000-2b823b627000 ---p 00010000 08:01 10422779                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b823b627000-2b823b629000 rw-p 00010000 08:01 10422779                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2b823b629000-2b823b62a000 rw-p 2b823b629000 00:00 0 
2b823b62a000-2b823b62c000 r-xp 00000000 08:01 12517891                   /lib/libdl-2.6.1.so
2b823b62c000-2b823b82c000 ---p 00002000 08:01 12517891                   /lib/libdl-2.6.1.so
2b823b82c000-2b823b82e000 rw-p 00002000 08:01 12517891                   /lib/libdl-2.6.1.so
2b823b82e000-2b823b980000 r-xp 00000000 08:01 12517888                   /lib/libc-2.6.1.so
2b823b980000-2b823bb7f000 ---p 00152000 08:01 12517888                   /lib/libc-2.6.1.so
2b823bb7f000-2b823bb82000 r--p 00151000 08:01 12517888                   /lib/libc-2.6.1.so
2b823bb82000-2b823bb84000 rw-p 00154000 08:01 12517888                   /lib/libc-2.6.1.so
2b823bb84000-2b823bb89000 rw-p 2b823bb84000 00:00 0 
2b823bb89000-2b823bb8b000 r-xp 00000000 08:01 9913636                    /usr/lib/libXau.so.6.0.0
2b823bb8b000-2b823bd8a000 ---p 00002000 08:01 9913636                    /usr/lib/libXau.so.6.0.0
2b823bd8a000-2b823bd8b000 rw-p 00001000 08:01 9913636                    /usr/lib/libXau.so.6.0.0
2b823bd8b000-2b823bd8c000 rw-p 2b823bd8b000 00:00 0 
2b823bd8c000-2b823bd91000 r-xp 00000000 08:01 9913647                    /usr/lib/libXdmcp.so.6.0.0
2b823bd91000-2b823bf90000 ---p 00005000 08:01 9913647                    /usr/lib/libXdmcp.so.6.0.0
2b823bf90000-2b823bf91000 rw-p 00004000 08:01 9913647                    /usr/lib/libXdmcp.so.6.0.0
2b823bf91000-2b823bf93000 rw-p 2b823bf91000 00:00 0 
2b823bf93000-2b823c6db000 r-xp 00000000 08:01 10422816                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b823c6db000-2b823c8db000 ---p 00748000 08:01 10422816                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b823c8db000-2b823c955000 rw-p 00748000 08:01 10422816                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2b823c955000-2b823c98f000 rw-p 2b823c955000 00:00 0 
2b823c9a4000-2b823ca24000 r-xp 00000000 08:01 12517965                   /lib/libm-2.6.1.so
2b823ca24000-2b823cc23000 ---p 00080000 08:01 12517965                   /lib/libm-2.6.1.so
2b823cc23000-2b823cc25000 rw-p 0007f000 08:01 12517965                   /lib/libm-2.6.1.so
7fff6fdc8000-7fff6fddd000 rwxp 7fff6fdc8000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Dapplication.home=/usr/lib/jvm/java-7-icedtea/jre 
java_command: sun.applet.PluginMain /home/cameron/.gcjwebplugin/gcj-instance-6162-0-plugin-to-appletviewer /home/cameron/.gcjwebplugin/gcj-instance-6162-0-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=cameron
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server:/usr/lib/jvm/java-7-icedtea/jre/lib/amd64:/usr/lib/jvm/java-7-icedtea/jre/../lib/amd64:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mre/mre
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4ccc50], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 24373, NOFILE 1024, AS infinity
load average:1.53 0.72 0.27

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 11, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 3072284k(2330304k free), swap 9759952k(9759952k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Mon Feb 25 20:38:38 2008
elapsed time: 2 seconds

```

---

### Post by scott_g on 2008-02-27
I had one of these too...  Not sure if its connected, but my PC seems to be freezing/in an infinite loop every couple of hours...  I just installed the x64 and am using Firefox.

Scott

---

### Post by aliencam on 2008-02-27
my computer doesn't freeze ever, but it sems like it's a java based website, but i don't remember having any open that weren't working.

---

### Post by scott_g on 2008-02-28
The freezes are likely unconnected then...  Maybe this should be in the 64bit forum to get more hits?

---

