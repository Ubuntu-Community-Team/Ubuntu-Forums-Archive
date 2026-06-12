---
title: "Opera 9.51 crashes by Java-Applet"
date: 2008-07-04
forum: General Help
---

### Post by mac-duff on 2008-07-04
Hi,
I dont now why Opera has everytime problems with flash or java. This time its crashes everytime by lunching a java-applet.

I attached the log file and this is the output from the console:

opera
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x062270fc, pid=12849, tid=3026492304
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode linux-x86)
# Problematic frame:
# V  [libjvm.so+0x2270fc]
#
# An error report file with more information is saved as:
# /home/stephan/hs_err_pid12849.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

(operapluginwrapper:12914): Gdk-WARNING **: GdkWindow 0x4400074 unexpectedly destroyed
Aborted


I hope someone can help me with this

---

### Post by mac-duff on 2008-07-04
ok, as I can see the log file is to big to attach:


> 
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x062270fc, pid=25956, tid=3030481808
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode linux-x86)
# Problematic frame:
# V  [libjvm.so+0x2270fc]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0xad524000):  JavaThread "Thread-9" [_thread_in_vm, id=28660, stack(0xb49c7000,0xb4a18000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=1 (SEGV_MAPERR), si_addr=0x00000000

Registers:
EAX=0x00000000, EBX=0xad524000, ECX=0x00000800, EDX=0x00000ffc
ESP=0xb4a16c10, EBP=0xb4a16c58, ESI=0xb4a16c10, EDI=0xad5240f4
EIP=0x062270fc, CR2=0x00000000, EFLAGS=0x00210246

Top of Stack: (sp=0xb4a16c10)
0xb4a16c10:   ad524000 00000000 a2f68c90 ffffffff
0xb4a16c20:   ad524000 00000000 b4a16c78 0623c72f
0xb4a16c30:   ad524000 a77482b4 0000000a 00000000
0xb4a16c40:   00000000 0000000a 00000000 ad5240f4
0xb4a16c50:   00000000 ad5240f4 b4a16c78 08941d0a
0xb4a16c60:   ad5240f4 00000000 a2f68c90 00000000
0xb4a16c70:   00000000 00000000 b4a16cc8 08941f7a
0xb4a16c80:   ad5240f4 00000000 00000000 00000000 

Instructions: (pc=0x062270fc)
0x062270ec:   43 04 8d 75 b8 85 c0 0f 85 d8 00 00 00 8b 45 0c
0x062270fc:   8b 00 8b 40 04 52 83 c0 08 52 8b 48 34 51 57 e8 

Stack: [0xb49c7000,0xb4a18000],  sp=0xb4a16c10,  free space=319k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x2270fc]
C  [opera+0x8f9d0a]
C  [opera+0x8f9f7a]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x21c5cd]
V  [libjvm.so+0x310748]
V  [libjvm.so+0x21bee0]
V  [libjvm.so+0x21bf6d]
V  [libjvm.so+0x28c175]
V  [libjvm.so+0x391f8d]
V  [libjvm.so+0x3113f9]
C  [libpthread.so.0+0x54fb]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x0ad68000 JavaThread "Image Fetcher 3" daemon [_thread_blocked, id=28675, stack(0xb47f2000,0xb4843000)]
  0x0ad9d800 JavaThread "Image Fetcher 2" daemon [_thread_blocked, id=28674, stack(0xb4843000,0xb4894000)]
  0x0ad6b400 JavaThread "Image Fetcher 1" daemon [_thread_blocked, id=28673, stack(0xb4894000,0xb48e5000)]
  0x0acf9400 JavaThread "Image Fetcher 0" daemon [_thread_blocked, id=28672, stack(0xb4a69000,0xb4aba000)]
  0x0afaf000 JavaThread "AWT-EventQueue-3" [_thread_blocked, id=28669, stack(0xb48e5000,0xb4936000)]
  0x0ad6ac00 JavaThread "Thread-11" [_thread_blocked, id=28664, stack(0xb4976000,0xb49c7000)]
  0x0acb5800 JavaThread "AWT-EventQueue-4" [_thread_blocked, id=28661, stack(0xb4a18000,0xb4a69000)]
=>0xad524000 JavaThread "Thread-9" [_thread_in_vm, id=28660, stack(0xb49c7000,0xb4a18000)]
  0xacfc5400 JavaThread "Thread-7" [_thread_blocked, id=28650, stack(0xb4aba000,0xb4b0b000)]
  0xb3c1e800 JavaThread "Thread-6" [_thread_blocked, id=28627, stack(0xb4d29000,0xb4d7a000)]
  0x0af1c800 JavaThread "AWT-EventQueue-2" [_thread_blocked, id=27582, stack(0xb4d7a000,0xb4dcb000)]
  0xafaab800 JavaThread "Thread-4" [_thread_blocked, id=27581, stack(0xb4baf000,0xb4c00000)]
  0xacf8b800 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=26568, stack(0xb5619000,0xb566a000)]
  0xad298800 JavaThread "AWT-Shutdown" [_thread_blocked, id=26567, stack(0xb566a000,0xb56bb000)]
  0x0b2e4c00 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=26566, stack(0xb56bb000,0xb570c000)]
  0x095f3400 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=26561, stack(0xb570c000,0xb575d000)]
  0x0950e800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=26557, stack(0xb58af000,0xb5900000)]
  0x0953e400 JavaThread "CompilerThread0" daemon [_thread_blocked, id=26556, stack(0xb5900000,0xb5981000)]
  0x095ae800 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=26555, stack(0xb5981000,0xb59d2000)]
  0x095c2c00 JavaThread "Finalizer" daemon [_thread_blocked, id=26554, stack(0xb59d2000,0xb5a23000)]
  0x0966c400 JavaThread "Reference Handler" daemon [_thread_blocked, id=26553, stack(0xb5a23000,0xb5a74000)]
  0x0966e000 JavaThread "main" [_thread_in_native, id=25956, stack(0xbff63000,0xbffb3000)]

Other Threads:
  0x0952a800 VMThread [stack: 0xb5a74000,0xb5af5000] [id=26552]
  0x09617000 WatcherThread [stack: 0xb582e000,0xb58af000] [id=26558]

VM state:synchronizing (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x0a4fc9d8/0x0b454cd8] Threads_lock - owner thread: 0x0952a800
[0x09d96628/0x099b1068] Heap_lock - owner thread: 0xacfc5400

Heap
 def new generation   total 960K, used 959K [0xa2f00000, 0xa3000000, 0xa33e0000)
  eden space 896K,  99% used [0xa2f00000, 0xa2fdfda8, 0xa2fe0000)
  from space 64K,  99% used [0xa2fe0000, 0xa2fefff8, 0xa2ff0000)
  to   space 64K,   0% used [0xa2ff0000, 0xa2ff0000, 0xa3000000)
 tenured generation   total 10524K, used 8901K [0xa33e0000, 0xa3e27000, 0xa6f00000)
   the space 10524K,  84% used [0xa33e0000, 0xa3c917b0, 0xa3c91800, 0xa3e27000)
 compacting perm gen  total 12288K, used 8801K [0xa6f00000, 0xa7b00000, 0xaaf00000)
   the space 12288K,  71% used [0xa6f00000, 0xa7798538, 0xa7798600, 0xa7b00000)
No shared spaces configured.

Dynamic libraries:
06000000-0641b000 r-xp 00000000 08:01 826053     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
0641b000-06435000 rw-p 0041a000 08:01 826053     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client/libjvm.so
06435000-06855000 rw-p 06435000 00:00 0 
08048000-08ac8000 r-xp 00000000 08:01 801320     /usr/lib/opera/9.51/opera
08ac8000-08b1b000 rw-p 00a80000 08:01 801320     /usr/lib/opera/9.51/opera
08b1b000-0bab7000 rw-p 08b1b000 00:00 0          [heap]
a2f00000-a3000000 rwxp a2f00000 00:00 0 
a3000000-a33e0000 rwxp a3000000 00:00 0 
a33e0000-a3e27000 rwxp a33e0000 00:00 0 
a3e27000-a6f00000 rwxp a3e27000 00:00 0 
a6f00000-a7b00000 rwxp a6f00000 00:00 0 
a7b00000-aaf00000 rwxp a7b00000 00:00 0 
aaf00000-aaff8000 rwxp aaf00000 00:00 0 
aaff8000-acf00000 rwxp aaff8000 00:00 0 
acf00000-acfec000 rw-p acf00000 00:00 0 
acfec000-ad000000 ---p acfec000 00:00 0 
ad000000-ad0eb000 rw-p ad000000 00:00 0 
ad0eb000-ad100000 ---p ad0eb000 00:00 0 
ad100000-ad1e2000 rw-p ad100000 00:00 0 
ad1e2000-ad200000 ---p ad1e2000 00:00 0 
ad200000-ad300000 rw-p ad200000 00:00 0 
ad300000-ad3e1000 rw-p ad300000 00:00 0 
ad3e1000-ad400000 ---p ad3e1000 00:00 0 
ad400000-ad4e1000 rw-p ad400000 00:00 0 
ad4e1000-ad500000 ---p ad4e1000 00:00 0 
ad500000-ad5f4000 rw-p ad500000 00:00 0 
ad5f4000-ad600000 ---p ad5f4000 00:00 0 
aef00000-aeffd000 rw-p aef00000 00:00 0 
aeffd000-af000000 ---p aeffd000 00:00 0 
af900000-af9fe000 rw-p af900000 00:00 0 
af9fe000-afa00000 ---p af9fe000 00:00 0 
afa00000-afae9000 rw-p afa00000 00:00 0 
afae9000-afb00000 ---p afae9000 00:00 0 
afb00000-afc00000 rw-p afb00000 00:00 0 
afcff000-afd00000 ---p afcff000 00:00 0 
afd00000-b0500000 rwxp afd00000 00:00 0 
b0500000-b05e9000 rw-p b0500000 00:00 0 
b05e9000-b0600000 ---p b05e9000 00:00 0 
b06fe000-b06ff000 ---p b06fe000 00:00 0 
b06ff000-b0eff000 rwxp b06ff000 00:00 0 
b0eff000-b0f00000 ---p b0eff000 00:00 0 
b0f00000-b1700000 rwxp b0f00000 00:00 0 
b1700000-b17e9000 rw-p b1700000 00:00 0 
b17e9000-b1800000 ---p b17e9000 00:00 0 
b1896000-b2000000 r--p 00000000 08:01 571245     /usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf
b2000000-b20f0000 rw-p b2000000 00:00 0 
b20f0000-b2100000 ---p b20f0000 00:00 0 
b2100000-b21f8000 rw-p b2100000 00:00 0 
b21f8000-b2200000 ---p b21f8000 00:00 0 
b2200000-b22e5000 rw-p b2200000 00:00 0 
b22e5000-b2300000 ---p b22e5000 00:00 0 
b2600000-b27f1000 rw-p b2600000 00:00 0 
b27f1000-b2800000 ---p b27f1000 00:00 0 
b2800000-b28e1000 rw-p b2800000 00:00 0 
b28e1000-b2900000 ---p b28e1000 00:00 0 
b2900000-b2a00000 rw-p b2900000 00:00 0 
b2a00000-b2afa000 rw-p b2a00000 00:00 0 
b2afa000-b2b00000 ---p b2afa000 00:00 0 
b3c00000-b3cfd000 rw-p b3c00000 00:00 0 
b3cfd000-b3d00000 ---p b3cfd000 00:00 0 
b3d0b000-b3d1a000 r--p 00000000 08:01 571333     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraSeBd.ttf
b3d1a000-b3d4b000 rw-p b3d1a000 00:00 0 
b3d64000-b3d7c000 r--p 00000000 08:01 579439     /usr/share/fonts/type1/gsfonts/n022003l.pfb
b3da9000-b3db9000 r--p 00000000 08:01 571327     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraIt.ttf
b3db9000-b3dbb000 r-xp 00000000 08:01 701854     /lib/libnss_mdns4.so.2
b3dbb000-b3dbc000 rw-p 00001000 08:01 701854     /lib/libnss_mdns4.so.2
b3dc4000-b3dcd000 r--p 00000000 08:01 566033     /usr/share/fonts/X11/Type1/c0648bt_.pfb
b47f2000-b47f5000 ---p b47f2000 00:00 0 
b47f5000-b4843000 rwxp b47f5000 00:00 0 
b4843000-b4846000 ---p b4843000 00:00 0 
b4846000-b4894000 rwxp b4846000 00:00 0 
b4894000-b4897000 ---p b4894000 00:00 0 
b4897000-b48e5000 rwxp b4897000 00:00 0 
b48e5000-b48e8000 ---p b48e5000 00:00 0 
b48e8000-b4936000 rwxp b48e8000 00:00 0 
b4936000-b4976000 rw-p b4936000 00:00 0 
b4976000-b4979000 ---p b4976000 00:00 0 
b4979000-b49c7000 rwxp b4979000 00:00 0 
b49c7000-b49ca000 ---p b49c7000 00:00 0 
b49ca000-b4a18000 rwxp b49ca000 00:00 0 
b4a18000-b4a1b000 ---p b4a18000 00:00 0 
b4a1b000-b4a69000 rwxp b4a1b000 00:00 0 
b4a69000-b4a6c000 ---p b4a69000 00:00 0 
b4a6c000-b4aba000 rwxp b4a6c000 00:00 0 
b4aba000-b4abd000 ---p b4aba000 00:00 0 
b4abd000-b4b0b000 rwxp b4abd000 00:00 0 
b4b0b000-b4b1c000 r--s 00000000 08:01 579409     /usr/share/fonts/type1/gsfonts/n019023l.pfb
b4b1c000-b4b32000 r--s 00000000 08:01 579436     /usr/share/fonts/type1/gsfonts/n021024l.pfb
b4b43000-b4b5e000 r--s 00000000 08:01 579391     /usr/share/fonts/type1/gsfonts/c059016l.pfb
b4b5e000-b4b75000 r--s 00000000 08:01 579433     /usr/share/fonts/type1/gsfonts/n021023l.pfb
b4b75000-b4b89000 r--s 00000000 08:01 579403     /usr/share/fonts/type1/gsfonts/n019003l.pfb
b4b89000-b4b92000 r--s 00000000 08:01 566029     /usr/share/fonts/X11/Type1/c0632bt_.pfb
b4b92000-b4b9c000 r--s 00000000 08:01 566027     /usr/share/fonts/X11/Type1/c0611bt_.pfb
b4b9c000-b4ba6000 r--s 00000000 08:01 566023     /usr/share/fonts/X11/Type1/c0582bt_.pfb
b4ba6000-b4baf000 r--s 00000000 08:01 566035     /usr/share/fonts/X11/Type1/c0649bt_.pfb
b4baf000-b4bb2000 ---p b4baf000 00:00 0 
b4bb2000-b4c00000 rwxp b4bb2000 00:00 0 
b4c00000-b4cea000 rw-p b4c00000 00:00 0 
b4cea000-b4d00000 ---p b4cea000 00:00 0 
b4d03000-b4d0d000 r--s 00000000 08:01 566021     /usr/share/fonts/X11/Type1/c0419bt_.pfb
b4d29000-b4d2c000 ---p b4d29000 00:00 0 
b4d2c000-b4d7a000 rwxp b4d2c000 00:00 0 
b4d7a000-b4d7d000 ---p b4d7a000 00:00 0 
b4d7d000-b4dcb000 rwxp b4d7d000 00:00 0 
b4dcb000-b4dd2000 r-xp 00000000 08:01 826067     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
b4dd2000-b4dd3000 rw-p 00006000 08:01 826067     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnio.so
b4dd3000-b4dd4000 ---p b4dd3000 00:00 0 
b4dd4000-b55d4000 rwxp b4dd4000 00:00 0 
b55d4000-b55e3000 r-xp 00000000 08:01 719446     /lib/tls/i686/cmov/libresolv-2.7.so
b55e3000-b55e5000 rw-p 0000f000 08:01 719446     /lib/tls/i686/cmov/libresolv-2.7.so
b55e5000-b55e7000 rw-p b55e5000 00:00 0 
b55e7000-b55eb000 r-xp 00000000 08:01 719433     /lib/tls/i686/cmov/libnss_dns-2.7.so
b55eb000-b55ed000 rw-p 00003000 08:01 719433     /lib/tls/i686/cmov/libnss_dns-2.7.so
b55ed000-b55ef000 r-xp 00000000 08:01 701855     /lib/libnss_mdns4_minimal.so.2
b55ef000-b55f0000 rw-p 00001000 08:01 701855     /lib/libnss_mdns4_minimal.so.2
b55f3000-b5602000 r--p 00000000 08:01 571332     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraSe.ttf
b5604000-b5605000 r--s 0001c000 08:01 244884     /tmp/jar_cache3755.tmp (deleted)
b5605000-b5618000 r-xp 00000000 08:01 826066     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
b5618000-b5619000 rw-p 00013000 08:01 826066     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libnet.so
b5619000-b561c000 ---p b5619000 00:00 0 
b561c000-b566a000 rwxp b561c000 00:00 0 
b566a000-b566d000 ---p b566a000 00:00 0 
b566d000-b56bb000 rwxp b566d000 00:00 0 
b56bb000-b56be000 ---p b56bb000 00:00 0 
b56be000-b570c000 rwxp b56be000 00:00 0 
b570c000-b570f000 ---p b570c000 00:00 0 
b570f000-b575d000 rwxp b570f000 00:00 0 
b575d000-b57db000 r-xp 00000000 08:01 826085     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
b57db000-b57e5000 rw-p 0007e000 08:01 826085     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libfontmanager.so
b57e5000-b57ea000 rw-p b57e5000 00:00 0 
b57ea000-b582b000 r-xp 00000000 08:01 826080     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
b582b000-b582e000 rw-p 00040000 08:01 826080     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/xawt/libmawt.so
b582e000-b582f000 ---p b582e000 00:00 0 
b582f000-b58af000 rwxp b582f000 00:00 0 
b58af000-b58b2000 ---p b58af000 00:00 0 
b58b2000-b5900000 rwxp b58b2000 00:00 0 
b5900000-b5903000 ---p b5900000 00:00 0 
b5903000-b5981000 rwxp b5903000 00:00 0 
b5981000-b5984000 ---p b5981000 00:00 0 
b5984000-b59d2000 rwxp b5984000 00:00 0 
b59d2000-b59d5000 ---p b59d2000 00:00 0 
b59d5000-b5a23000 rwxp b59d5000 00:00 0 
b5a23000-b5a26000 ---p b5a23000 00:00 0 
b5a26000-b5a74000 rwxp b5a26000 00:00 0 
b5a74000-b5a75000 ---p b5a74000 00:00 0 
b5a75000-b5af5000 rwxp b5a75000 00:00 0 
b5af5000-b5c80000 r--s 02df0000 08:01 826276     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/rt.jar
b5c80000-b5c89000 r--s 000e2000 08:01 826277     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/plugin.jar
b5c89000-b5c90000 rwxp b5c89000 00:00 0 
b5c90000-b5caa000 rwxp b5c90000 00:00 0 
b5caa000-b5cb0000 rwxp b5caa000 00:00 0 
b5cb0000-b5cc8000 rwxp b5cb0000 00:00 0 
b5cc8000-b5cc9000 rwxp b5cc8000 00:00 0 
b5cc9000-b5cca000 rwxp b5cc9000 00:00 0 
b5cca000-b5cd0000 rwxp b5cca000 00:00 0 
b5cd0000-b5ce8000 rwxp b5cd0000 00:00 0 
b5ce8000-b5cee000 rwxp b5ce8000 00:00 0 
b5cee000-b5d08000 rwxp b5cee000 00:00 0 
b5d08000-b5d0d000 rwxp b5d08000 00:00 0 
b5d0d000-b5d89000 rwxp b5d0d000 00:00 0 
b5d89000-b5d98000 r-xp 00000000 08:01 826062     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b5d98000-b5d9a000 rw-p 0000e000 08:01 826062     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libzip.so
b5d9a000-b5da1000 r-xp 00000000 08:01 719448     /lib/tls/i686/cmov/librt-2.7.so
b5da1000-b5da3000 rw-p 00006000 08:01 719448     /lib/tls/i686/cmov/librt-2.7.so
b5da3000-b5da4000 r--s 00016000 08:01 244871     /tmp/jar_cache3753.tmp (deleted)
b5da4000-b5da5000 r--s 0001c000 08:01 244870     /tmp/jar_cache3752.tmp (deleted)
b5da5000-b5da9000 r-xp 00000000 08:01 458331     /usr/lib/libXtst.so.6.1.0
b5da9000-b5daa000 rw-p 00003000 08:01 458331     /usr/lib/libXtst.so.6.1.0
b5daa000-b5dad000 r--s 00013000 08:01 736216     /usr/share/opera/java/opera.jar
b5dad000-b5db5000 rw-s 00000000 08:01 244868     /tmp/hsperfdata_stephan/25956
b5db5000-b5dfc000 rw-p b5db5000 00:00 0 
b5dfc000-b5e02000 r-xp 00000000 08:01 826047     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b5e02000-b5e03000 rw-p 00006000 08:01 826047     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads/libhpi.so
b5e03000-b5e12000 r--p 00000000 08:01 571326     /usr/share/fonts/truetype/ttf-bitstream-vera/VeraBd.ttf
b5e12000-b5e13000 ---p b5e12000 00:00 0 
b5e13000-b6613000 rwxp b5e13000 00:00 0 
b6613000-b661e000 r-xp 00000000 08:01 679393     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b661e000-b661f000 rw-p 0000b000 08:01 679393     /usr/lib/qt3/plugins/inputmethods/libqxim.so
b661f000-b6644000 r-xp 00000000 08:01 679392     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6644000-b6645000 rw-p 00024000 08:01 679392     /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6645000-b6649000 r-xp 00000000 08:01 679391     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6649000-b664a000 rw-p 00003000 08:01 679391     /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b664a000-b6653000 r-xp 00000000 08:01 719435     /lib/tls/i686/cmov/libnss_files-2.7.so
b6653000-b6655000 rw-p 00008000 08:01 719435     /lib/tls/i686/cmov/libnss_files-2.7.so
b6655000-b665d000 r-xp 00000000 08:01 719439     /lib/tls/i686/cmov/libnss_nis-2.7.so
b665d000-b665f000 rw-p 00007000 08:01 719439     /lib/tls/i686/cmov/libnss_nis-2.7.so
b665f000-b6666000 r-xp 00000000 08:01 719431     /lib/tls/i686/cmov/libnss_compat-2.7.so
b6666000-b6668000 rw-p 00006000 08:01 719431     /lib/tls/i686/cmov/libnss_compat-2.7.so
b6668000-b6669000 rwxp b6668000 00:00 0 
b6669000-b666a000 ---p b6669000 00:00 0 
b666a000-b6670000 rw-p b666a000 00:00 0 
b6670000-b6679000 r-xp 00000000 08:01 679390     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6679000-b667a000 rw-p 00009000 08:01 679390     /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b667a000-b667f000 r-xp 00000000 08:01 457760     /usr/lib/liblirc_client.so.0.2.0
b667f000-b6680000 rw-p 00004000 08:01 457760     /usr/lib/liblirc_client.so.0.2.0
b6680000-b672a000 r-xp 00000000 08:01 458362     /usr/lib/libaspell.so.15.1.4
b672a000-b672f000 rw-p 000a9000 08:01 458362     /usr/lib/libaspell.so.15.1.4
b672f000-b6732000 rw-p b672f000 00:00 0 
b6732000-b6736000 r-xp 00000000 08:01 801319     /usr/lib/opera/9.51/spellcheck.so
b6736000-b6737000 rw-p 00004000 08:01 801319     /usr/lib/opera/9.51/spellcheck.so
b6737000-b6738000 ---p b6737000 00:00 0 
b6738000-b6f38000 rwxp b6738000 00:00 0 
b6f38000-b6f5b000 rw-p b6f38000 00:00 0 
b6f5b000-b6f6c000 r--p 00000000 08:01 571324     /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b6f6c000-b6f6d000 r-xp 00000000 08:01 801318     /usr/lib/opera/9.51/missingsyms.so
b6f6d000-b6f6e000 rw-p 00000000 08:01 801318     /usr/lib/opera/9.51/missingsyms.so
b6f6e000-b6f74000 r--s 00000000 08:01 925171     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6f74000-b6f77000 r--s 00000000 08:01 925165     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6f77000-b6f78000 r--s 00000000 08:01 925164     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6f78000-b6f79000 r--s 00000000 08:01 925163     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6f79000-b6f7c000 r--s 00000000 08:01 925161     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6f7c000-b6f83000 r--s 00000000 08:01 925150     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6f83000-b6f86000 r--s 00000000 08:01 925148     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6f86000-b6f8e000 r--s 00000000 08:01 925093     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6f8e000-b6f96000 r--s 00000000 08:01 925091     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6f96000-b6f97000 r--s 00000000 08:01 925085     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6f97000-b6f9a000 r--s 00000000 08:01 925084     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6f9a000-b6fa1000 r--s 00000000 08:01 925083     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6fa1000-b6fa7000 r--s 00000000 08:01 922157     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6fa7000-b6fa9000 r--s 00000000 08:01 922147     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6fa9000-b6fe8000 r--p 00000000 08:01 482492     /usr/lib/locale/en_US.utf8/LC_CTYPE
b6fe8000-b70c9000 r--p 00000000 08:01 482491     /usr/lib/locale/en_US.utf8/LC_COLLATE
b70c9000-b70cb000 rw-p b70c9000 00:00 0 
b70cb000-b70cf000 r-xp 00000000 08:01 458299     /usr/lib/libXdmcp.so.6.0.0
b70cf000-b70d0000 rw-p 00003000 08:01 458299     /usr/lib/libXdmcp.so.6.0.0
b70d0000-b70d4000 r-xp 00000000 08:01 458305     /usr/lib/libXfixes.so.3.1.0
b70d4000-b70d5000 rw-p 00003000 08:01 458305     /usr/lib/libXfixes.so.3.1.0
b70d5000-b70d6000 rw-p b70d5000 00:00 0 
b70d6000-b70f5000 r-xp 00000000 08:01 458525     /usr/lib/libexpat.so.1.5.2
b70f5000-b70f7000 rw-p 0001e000 08:01 458525     /usr/lib/libexpat.so.1.5.2
b70f7000-b710b000 r-xp 00000000 08:01 719429     /lib/tls/i686/cmov/libnsl-2.7.so
b710b000-b710d000 rw-p 00013000 08:01 719429     /lib/tls/i686/cmov/libnsl-2.7.so
b710d000-b710f000 rw-p b710d000 00:00 0 
b710f000-b711a000 r-xp 00000000 08:01 826058     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b711a000-b711b000 rw-p 0000b000 08:01 826058     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libverify.so
b711b000-b711d000 r-xp 00000000 08:01 458288     /usr/lib/libXau.so.6.0.0
b711d000-b711e000 rw-p 00001000 08:01 458288     /usr/lib/libXau.so.6.0.0
b711e000-b711f000 rw-p b711e000 00:00 0 
b711f000-b7136000 r-xp 00000000 08:01 459129     /usr/lib/libxcb.so.1.0.0
b7136000-b7137000 rw-p 00016000 08:01 459129     /usr/lib/libxcb.so.1.0.0
b7137000-b7138000 r-xp 00000000 08:01 459127     /usr/lib/libxcb-xlib.so.0.0.0
b7138000-b7139000 rw-p 00000000 08:01 459127     /usr/lib/libxcb-xlib.so.0.0.0
b7139000-b71a5000 r-xp 00000000 08:01 458541     /usr/lib/libfreetype.so.6.3.16
b71a5000-b71a9000 rw-p 0006b000 08:01 458541     /usr/lib/libfreetype.so.6.3.16
b71a9000-b71ba000 r-xp 00000000 08:01 458309     /usr/lib/libXft.so.2.1.2
b71ba000-b71bb000 rw-p 00010000 08:01 458309     /usr/lib/libXft.so.2.1.2
b71bb000-b71bd000 r-xp 00000000 08:01 458313     /usr/lib/libXinerama.so.1.0.0
b71bd000-b71be000 rw-p 00001000 08:01 458313     /usr/lib/libXinerama.so.1.0.0
b71be000-b71bf000 rw-p b71be000 00:00 0 
b71bf000-b71c7000 r-xp 00000000 08:01 458295     /usr/lib/libXcursor.so.1.0.2
b71c7000-b71c8000 rw-p 00007000 08:01 458295     /usr/lib/libXcursor.so.1.0.2
b71c8000-b71cd000 r-xp 00000000 08:01 458323     /usr/lib/libXrandr.so.2.1.0
b71cd000-b71ce000 rw-p 00005000 08:01 458323     /usr/lib/libXrandr.so.2.1.0
b71ce000-b71d5000 r-xp 00000000 08:01 458325     /usr/lib/libXrender.so.1.3.0
b71d5000-b71d6000 rw-p 00007000 08:01 458325     /usr/lib/libXrender.so.1.3.0
b71d6000-b71dd000 r-xp 00000000 08:01 458311     /usr/lib/libXi.so.6.0.0
b71dd000-b71de000 rw-p 00006000 08:01 458311     /usr/lib/libXi.so.6.0.0
b71de000-b7203000 r-xp 00000000 08:01 458249     /usr/lib/libpng12.so.0.24.0
b7203000-b7204000 rw-p 00024000 08:01 458249     /usr/lib/libpng12.so.0.24.0
b7204000-b7223000 r-xp 00000000 08:01 458818     /usr/lib/libjpeg.so.62.0.0
b7223000-b7224000 rw-p 0001e000 08:01 458818     /usr/lib/libjpeg.so.62.0.0
b7224000-b7225000 rw-p b7224000 00:00 0 
b7225000-b7272000 r-xp 00000000 08:01 458329     /usr/lib/libXt.so.6.0.0
b7272000-b7276000 rw-p 0004c000 08:01 458329     /usr/lib/libXt.so.6.0.0
b7276000-b728b000 r-xp 00000000 08:01 459656     /usr/lib/libaudio.so.2.4
b728b000-b728c000 rw-p 00015000 08:01 459656     /usr/lib/libaudio.so.2.4
b728c000-b72b5000 r-xp 00000000 08:01 458533     /usr/lib/libfontconfig.so.1.3.0
b72b5000-b72b6000 rw-p 00029000 08:01 458533     /usr/lib/libfontconfig.so.1.3.0
b72b6000-b72d9000 r-xp 00000000 08:01 826059     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b72d9000-b72db000 rw-p 00023000 08:01 826059     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libjava.so
b72db000-b7424000 r-xp 00000000 08:01 719418     /lib/tls/i686/cmov/libc-2.7.so
b7424000-b7425000 r--p 00149000 08:01 719418     /lib/tls/i686/cmov/libc-2.7.so
b7425000-b7427000 rw-p 0014a000 08:01 719418     /lib/tls/i686/cmov/libc-2.7.so
b7427000-b742b000 rw-p b7427000 00:00 0 
b742b000-b7435000 r-xp 00000000 08:01 701824     /lib/libgcc_s.so.1
b7435000-b7436000 rw-p 0000a000 08:01 701824     /lib/libgcc_s.so.1
b7436000-b7459000 r-xp 00000000 08:01 719426     /lib/tls/i686/cmov/libm-2.7.so
b7459000-b745b000 rw-p 00023000 08:01 719426     /lib/tls/i686/cmov/libm-2.7.so
b745b000-b7543000 r-xp 00000000 08:01 459066     /usr/lib/libstdc++.so.6.0.9
b7543000-b7546000 r--p 000e8000 08:01 459066     /usr/lib/libstdc++.so.6.0.9
b7546000-b7548000 rw-p 000eb000 08:01 459066     /usr/lib/libstdc++.so.6.0.9
b7548000-b754e000 rw-p b7548000 00:00 0 
b754e000-b7562000 r-xp 00000000 08:01 459141     /usr/lib/libz.so.1.2.3.3
b7562000-b7563000 rw-p 00013000 08:01 459141     /usr/lib/libz.so.1.2.3.3
b7563000-b7565000 r-xp 00000000 08:01 719424     /lib/tls/i686/cmov/libdl-2.7.so
b7565000-b7567000 rw-p 00001000 08:01 719424     /lib/tls/i686/cmov/libdl-2.7.so
b7567000-b757b000 r-xp 00000000 08:01 719444     /lib/tls/i686/cmov/libpthread-2.7.so
b757b000-b757d000 rw-p 00013000 08:01 719444     /lib/tls/i686/cmov/libpthread-2.7.so
b757d000-b7581000 rw-p b757d000 00:00 0 
b7581000-b7582000 r--p 00000000 08:01 482497     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7582000-b7583000 r--p 00000000 08:01 482500     /usr/lib/locale/en_US.utf8/LC_TIME
b7583000-b7584000 r--p 00000000 08:01 482495     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7584000-b7585000 r--p 00000000 08:01 489646     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7585000-b7586000 r--p 00000000 08:01 482498     /usr/lib/locale/en_US.utf8/LC_PAPER
b7586000-b7587000 r--p 00000000 08:01 482496     /usr/lib/locale/en_US.utf8/LC_NAME
b7587000-b7588000 r--p 00000000 08:01 482490     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7588000-b7589000 r--p 00000000 08:01 482499     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7589000-b758a000 r--p 00000000 08:01 482494     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b758a000-b7591000 r--s 00000000 08:01 359279     /usr/lib/gconv/gconv-modules.cache
b7591000-b7592000 r--p 00000000 08:01 482493     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7592000-b75a7000 r-xp 00000000 08:01 458252     /usr/lib/libICE.so.6.3.0
b75a7000-b75a8000 rw-p 00014000 08:01 458252     /usr/lib/libICE.so.6.3.0
b75a8000-b75aa000 rw-p b75a8000 00:00 0 
b75aa000-b75b1000 r-xp 00000000 08:01 458276     /usr/lib/libSM.so.6.0.0
b75b1000-b75b2000 rw-p 00006000 08:01 458276     /usr/lib/libSM.so.6.0.0
b75b2000-b75bf000 r-xp 00000000 08:01 458303     /usr/lib/libXext.so.6.4.0
b75bf000-b75c0000 rw-p 0000d000 08:01 458303     /usr/lib/libXext.so.6.4.0
b75c0000-b76a4000 r-xp 00000000 08:01 458282     /usr/lib/libX11.so.6.2.0
b76a4000-b76a7000 rw-p 000e4000 08:01 458282     /usr/lib/libX11.so.6.2.0
b76a7000-b7e7d000 r-xp 00000000 08:01 459659     /usr/lib/libqt-mt.so.3.3.8
b7e7d000-b7ec3000 rw-p 007d5000 08:01 459659     /usr/lib/libqt-mt.so.3.3.8
b7ec3000-b7ec7000 rw-p b7ec3000 00:00 0 
b7ec7000-b7f42000 r-xp 00000000 08:01 826077     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
b7f42000-b7f49000 rw-p 0007b000 08:01 826077     /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/libawt.so
b7f49000-b7f70000 rw-p b7f49000 00:00 0 
b7f70000-b7f71000 r-xp b7f70000 00:00 0          [vdso]
b7f71000-b7f8b000 r-xp 00000000 08:01 701779     /lib/ld-2.7.so
b7f8b000-b7f8d000 rw-p 00019000 08:01 701779     /lib/ld-2.7.so
bff63000-bff66000 ---p bff63000 00:00 0 
bff66000-bffb3000 rwxp bffb2000 00:00 0          [stack]
bffb3000-bffb4000 rw-p bffff000 00:00 0 

VM Arguments:
jvm_args: abort exit -Xbootclasspath/p:/usr/share/opera/java/opera.jar:/usr/share/opera/java/lc.jar:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/plugin.jar -Djava.security.policy=/usr/share/opera/java/opera.policy -Dbrowser.opera.classpath=/usr/share/opera/java/opera.jar:/usr/share/opera/java/lc.jar 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/Adobe/Reader8/bin
USERNAME=stephan
LD_LIBRARY_PATH=/usr/lib/opera/9.51:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/native_threads:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/server:/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/classic:/usr/lib
LD_PRELOAD=
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
SIGINT: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x3115f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
libc:glibc 2.7 NPTL 2.7 
rlimit: STACK 8192k, CORE 0k, NPROC 16371, NOFILE 1024, AS infinity
load average:1.28 1.21 0.94

CPU:total 2 (2 cores per cpu, 1 threads per core) family 6 model 15 stepping 13, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3

Memory: 4k page, physical 2074140k(115224k free), swap 6072528k(6072528k free)

vm_info: Java HotSpot(TM) Client VM (10.0-b22) for linux-x86 JRE (1.6.0_06-b02), built on Mar 25 2008 00:39:19 by "java_re" with gcc 3.2.1-7a (J2SE release)

time: Fri Jul  4 22:47:42 2008
elapsed time: 179 seconds



---

### Post by jamesstansell on 2008-07-04
The sun-java6 package on launchpad has other bugs related to libjvm.so but offhand I don't remember any that related to opera.  Still, you might like to take a look.

---

### Post by mac-duff on 2008-07-05
ah yes..... ok, so what can I do? dont use Opera? :)

---

### Post by jamesstansell on 2008-07-05
> **mac-duff said:**
> ah yes..... ok, so what can I do? dont use Opera? :)

Well, that's an interesting thought.  Does firefox 3 work for you with this applet?

What applet is it, anyway?

I can see that you have sun-java6-jre installed, but tell us more about your system.  Is it 32bit Ubuntu 8.04 LTS?  Did you install opera from the ubuntu repository?

Hopefully someone else can chime in, because I'm not an opera user.

-james.

---

