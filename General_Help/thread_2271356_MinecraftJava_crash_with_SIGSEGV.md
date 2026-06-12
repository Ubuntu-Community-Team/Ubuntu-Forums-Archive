---
title: "Minecraft/Java crash with SIGSEGV"
date: 2015-03-29
forum: General Help
---

### Post by chellrose on 2015-03-29
I'm running Xubuntu 14.10, 64-bit system with Intel 4600 graphics.  I run a small private Minecraft server (with myself and one other player) from this machine, and the server runs just beautifully.  However, my client will crash with a segfault while I'm playing on the server.  There is no obvious cause for the crash; sometimes it happens after I've been in the game for only a few minutes and other times I can play for over an hour before it crashes.

At the time of crash, my Minecraft client freezes and I have zero or very limited control over any GUI functions; I typically can't alt-tab or mouse to a different window.  The client will eventually finish crashing (i.e. return to the launcher screen) after 5-10 minutes.  (Alternately, I can drop to a terminal and force-kill the Java processes).  Minecraft generates an error log that usually seems to point to my graphics driver, but sometimes points to libc.so instead.  Here's an excerpt (the full file is very large and is included as an attachment to this post):


graphics driver error:
```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fcb2523a899, pid=6207, tid=140512524936960
#
# JRE version: Java(TM) SE Runtime Environment (8.0_40-b25) (build 1.8.0_40-b25)
# Java VM: Java HotSpot(TM) 64-Bit Server VM (25.40-b25 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [i965_dri.so+0x36f899]
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

libc.so error:
```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f22262e8f89, pid=5359, tid=139784625858304
#
# JRE version: Java(TM) SE Runtime Environment (8.0_40-b25) (build 1.8.0_40-b25)
# Java VM: Java HotSpot(TM) 64-Bit Server VM (25.40-b25 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libc.so.6+0x97f89]
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```

I have updated my graphics drivers using the Linux Intel Graphics Updater linked to on Intel's website, to no avail.  I posted this over at the Minecraft Forums as well but have received little input thus far.  Any suggestions are greatly appreciated.

Edit: Apparently the error file is too big for a UF attachment.  I'll post more of it below.

---

### Post by chellrose on 2015-03-31
Crashed yesterday because I tried to post the whole error log.  Here it is in part:

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f22262e8f89, pid=5359, tid=139784625858304
#
# JRE version: Java(TM) SE Runtime Environment (8.0_40-b25) (build 1.8.0_40-b25)
# Java VM: Java HotSpot(TM) 64-Bit Server VM (25.40-b25 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libc.so.6+0x97f89]
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.java.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x00007f222000c000):  JavaThread "Client thread" [_thread_in_native, id=5360, stack(0x00007f2224d82000,0x00007f2224f83000)]

siginfo: si_signo: 11 (SIGSEGV), si_code: 1 (SEGV_MAPERR), si_addr: 0x0000000000000000

Registers:
RAX=0x00007f22214952cc, RBX=0x00007f2221490520, RCX=0x0000000000000058, RDX=0x000000000000002c
RSP=0x00007f2224f807c8, RBP=0x00007f22214952f8, RSI=0x00007f22214952f8, RDI=0x0000000000000000
R8 =0x000000000000000b, R9 =0xffffffffffffffff, R10=0x0000000000000001, R11=0x0000000000000246
R12=0x0000000000000001, R13=0x0000000000000000, R14=0x00007f222144f230, R15=0x00007f222144f540
RIP=0x00007f22262e8f89, EFLAGS=0x0000000000010206, CSGSFS=0x0000000000000033, ERR=0x0000000000000006
  TRAPNO=0x000000000000000e

Top of Stack: (sp=0x00007f2224f807c8)
0x00007f2224f807c8:   00007f219eb60c78 00000000000002b9
0x00007f2224f807d8:   00007f222147adc0 00007f2221455cc8
0x00007f2224f807e8:   00007f219ea1d887 00007f222000c000
0x00007f2224f807f8:   00000000000002ba 0000000000000e00
0x00007f2224f80808:   00007f2221455cc8 ffffffffffffff40
0x00007f2224f80818:   00007f2221490520 00007f222000c000
0x00007f2224f80828:   00007f219eb57288 00007f21b8be2e80
0x00007f2224f80838:   00007f2224f808a0 0000000000000000
0x00007f2224f80848:   0000000000000000 00007f2224f80890
0x00007f2224f80858:   00007f22111ae0c4 0000000000000000
0x00007f2224f80868:   00007f22127cf960 c068400000000000
0x00007f2224f80878:   000000003f4ccccd 00000000dea4a870
0x00007f2224f80888:   0000000084044068 0000000084044068
0x00007f2224f80898:   00000000dea4a870 0000000084065a28
0x00007f2224f808a8:   00007f2212b0a5f4 0000000085c0dfc0
0x00007f2224f808b8:   0000000085c0e0d0 0000000000000000
0x00007f2224f808c8:   0000000085c0e7b8 000000003f800000
0x00007f2224f808d8:   00007f221303323c 0000000000000000
0x00007f2224f808e8:   00007f221330ffb8 000000008f670090
0x00007f2224f808f8:   00007f2200000000 0000000083c164d0
0x00007f2224f80908:   0000000083c164f0 00000000de9faa28
0x00007f2224f80918:   00007f2225b92e4f 00000000000049b8
0x00007f2224f80928:   0000000008a85b2f 000000008f670388
0x00007f2224f80938:   00007f22132a152c 0000000100038518
0x00007f2224f80948:   0000112a03b9c508 0000002083c1d868
0x00007f2224f80958:   ffffff40000000d0 000000e000000030
0x00007f2224f80968:   0000000100011300 de9fab90de9faa28
0x00007f2224f80978:   000000808f670090 0000004300000000
0x00007f2224f80988:   00000000000000f6 ffffff300000000d
0x00007f2224f80998:   00000000de9fa988 00000ff000000001
0x00007f2224f809a8:   000000008f670090 00000000de9faa28
0x00007f2224f809b8:   0000000100000000 00000001de9fa988 

Instructions: (pc=0x00007f22262e8f89)
0x00007f22262e8f69:   f8 48 29 d0 48 39 c8 0f 82 07 01 00 00 48 83 fa
0x00007f22262e8f79:   10 0f 86 8b 01 00 00 f3 44 0f 6f 06 48 83 fa 20
0x00007f22262e8f89:   f3 44 0f 7f 07 f3 44 0f 6f 44 16 f0 f3 44 0f 7f
0x00007f22262e8f99:   44 17 f0 77 12 48 89 f8 c3 66 66 66 66 66 2e 0f 

Register to memory mapping:

RAX=0x00007f22214952cc is an unknown value
RBX=0x00007f2221490520 is an unknown value
RCX=0x0000000000000058 is an unknown value
RDX=0x000000000000002c is an unknown value
RSP=0x00007f2224f807c8 is pointing into the stack for thread: 0x00007f222000c000
RBP=0x00007f22214952f8 is an unknown value
RSI=0x00007f22214952f8 is an unknown value
RDI=0x0000000000000000 is an unknown value
R8 =0x000000000000000b is an unknown value
R9 =0xffffffffffffffff is an unknown value
R10=0x0000000000000001 is an unknown value
R11=0x0000000000000246 is an unknown value
R12=0x0000000000000001 is an unknown value
R13=0x0000000000000000 is an unknown value
R14=0x00007f222144f230 is an unknown value
R15=0x00007f222144f540 is an unknown value


Stack: [0x00007f2224d82000,0x00007f2224f83000],  sp=0x00007f2224f807c8,  free space=2041k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libc.so.6+0x97f89]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
J 8526  org.lwjgl.opengl.GL11.nglDrawArrays(IIIJ)V (0 bytes) @ 0x00007f22111ae04a [0x00007f22111ae000+0x4a]
J 11194 C2 net.minecraft.client.renderer.Tessellator.func_78381_a()I (346 bytes) @ 0x00007f2212b0a5f4 [0x00007f2212b09e20+0x7d4]
J 14815 C2 WorldRendererSmooth.postRenderBlocksSmooth(ILnet/minecraft/entity/EntityLivingBase;Z)V (137 bytes) @ 0x00007f221330ffb8 [0x00007f221330fea0+0x118]
J 18776 C2 WorldRendererSmooth.updateRenderer(J)Z (1318 bytes) @ 0x00007f22132a152c [0x00007f22132a0880+0xcac]
J 14119 C2 WrUpdaterSmooth.updateRenderer(LWorldRendererSmooth;)Z (45 bytes) @ 0x00007f2213925434 [0x00007f22139253e0+0x54]
J 15865 C2 WrUpdaterSmooth.updateRenderersImpl(Lnet/minecraft/client/renderer/RenderGlobal;Lnet/minecraft/entity/EntityLivingBase;Z)V (615 bytes) @ 0x00007f22135f0364 [0x00007f22135f00e0+0x284]
J 15006 C2 net.minecraft.client.renderer.RenderGlobal.func_72716_a(Lnet/minecraft/entity/EntityLivingBase;Z)Z (449 bytes) @ 0x00007f2211e06bc8 [0x00007f2211e06ae0+0xe8]
J 15672 C2 net.minecraft.client.renderer.EntityRenderer.func_78471_a(FJ)V (1819 bytes) @ 0x00007f2212c1dc68 [0x00007f2212c1d040+0xc28]
J 15975 C2 net.minecraft.client.renderer.EntityRenderer.func_78480_b(F)V (1306 bytes) @ 0x00007f2212e73614 [0x00007f2212e72de0+0x834]
J 15175 C2 net.minecraft.client.Minecraft.func_71411_J()V (773 bytes) @ 0x00007f221284cc7c [0x00007f221284bd40+0xf3c]
J 19916% C1 net.minecraft.client.Minecraft.func_99999_d()V (211 bytes) @ 0x00007f2212e53f6c [0x00007f2212e53de0+0x18c]
j  net.minecraft.client.main.Main.main([Ljava/lang/String;)V+1012
v  ~StubRoutines::call_stub
j  sun.reflect.NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+0
j  sun.reflect.NativeMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;+100
J 2122 C1 sun.reflect.DelegatingMethodAccessorImpl.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object; (10 bytes) @ 0x00007f2211362d84 [0x00007f2211362c80+0x104]
J 2121 C1 java.lang.reflect.Method.invoke(Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object; (62 bytes) @ 0x00007f2211364cc4 [0x00007f22113648e0+0x3e4]
j  net.minecraft.launchwrapper.Launch.launch([Ljava/lang/String;)V+664
j  net.minecraft.launchwrapper.Launch.main([Ljava/lang/String;)V+8
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00007f2160007000 JavaThread "Netty Client IO #4" daemon [_thread_in_native, id=5588, stack(0x00007f20fdd6e000,0x00007f20fdf6f000)]
  0x00007f2144003000 JavaThread "Netty Client IO #3" daemon [_thread_in_native, id=5584, stack(0x00007f20fdb6d000,0x00007f20fdd6e000)]
  0x00007f2198103800 JavaThread "Netty Client IO #2" daemon [_thread_in_native, id=5581, stack(0x00007f214bdff000,0x00007f214c000000)]
  0x00007f2181020000 JavaThread "Server Pinger #1" daemon [_thread_blocked, id=5580, stack(0x00007f2178364000,0x00007f2178565000)]
  0x00007f2160004000 JavaThread "Keep-Alive-SocketCleaner" daemon [_thread_blocked, id=5529, stack(0x00007f21bb579000,0x00007f21bb77a000)]
  0x00007f2160001800 JavaThread "Netty Client IO #1" daemon [_thread_in_native, id=5442, stack(0x00007f2178765000,0x00007f2178966000)]
  0x00007f2198100800 JavaThread "Netty Client IO #0" daemon [_thread_in_native, id=5439, stack(0x00007f21b96c3000,0x00007f21b98c4000)]
  0x00007f21837c4800 JavaThread "Server Pinger #0" daemon [_thread_blocked, id=5438, stack(0x00007f21bb378000,0x00007f21bb579000)]
  0x00007f2174001000 JavaThread "Thread-13" [_thread_blocked, id=5423, stack(0x00007f2195bb7000,0x00007f2195db8000)]
  0x00007f2198009800 JavaThread "Thread-12" [_thread_blocked, id=5422, stack(0x00007f21959b6000,0x00007f2195bb7000)]
  0x00007f2220ba0000 JavaThread "Timer hack thread" daemon [_thread_blocked, id=5388, stack(0x00007f21b98c4000,0x00007f21b9ac5000)]
  0x00007f2220b81000 JavaThread "Snooper Timer" daemon [_thread_blocked, id=5387, stack(0x00007f21b9ac5000,0x00007f21b9cc6000)]
  0x00007f22207e6800 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=5382, stack(0x00007f21bbbf9000,0x00007f21bbdfa000)]
  0x00007f22207c5800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=5381, stack(0x00007f21dc3d9000,0x00007f21dc5da000)]
  0x00007f22200d8000 JavaThread "Service Thread" daemon [_thread_blocked, id=5379, stack(0x00007f21df8fb000,0x00007f21dfafc000)]
  0x00007f22200ca800 JavaThread "C1 CompilerThread3" daemon [_thread_blocked, id=5378, stack(0x00007f21dfafc000,0x00007f21dfbfd000)]
  0x00007f22200c8800 JavaThread "C2 CompilerThread2" daemon [_thread_blocked, id=5377, stack(0x00007f21dfbfd000,0x00007f21dfcfe000)]
  0x00007f22200c6800 JavaThread "C2 CompilerThread1" daemon [_thread_blocked, id=5376, stack(0x00007f21dfcfe000,0x00007f21dfdff000)]
  0x00007f22200c3800 JavaThread "C2 CompilerThread0" daemon [_thread_blocked, id=5375, stack(0x00007f220c0b3000,0x00007f220c1b4000)]
  0x00007f22200c2000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=5374, stack(0x00007f21dfdff000,0x00007f21e0000000)]
  0x00007f2220089800 JavaThread "Finalizer" daemon [_thread_blocked, id=5373, stack(0x00007f220cb86000,0x00007f220cd87000)]
  0x00007f2220087800 JavaThread "Reference Handler" daemon [_thread_blocked, id=5372, stack(0x00007f220cd87000,0x00007f220cf88000)]
=>0x00007f222000c000 JavaThread "Client thread" [_thread_in_native, id=5360, stack(0x00007f2224d82000,0x00007f2224f83000)]

Other Threads:
  0x00007f2220082800 VMThread [stack: 0x00007f220cf88000,0x00007f220d089000] [id=5371]
  0x00007f22200da800 WatcherThread [stack: 0x00007f21df7fa000,0x00007f21df8fb000] [id=5380]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap:
 PSYoungGen      total 268288K, used 177520K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 190464K, 81% used [0x00000000d5600000,0x00000000ded87768,0x00000000e1000000)
  from space 77824K, 28% used [0x00000000e1000000,0x00000000e25d4be0,0x00000000e5c00000)
  to   space 73728K, 0% used [0x00000000e6200000,0x00000000e6200000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 735723K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 96% used [0x0000000080000000,0x00000000ace7ac20,0x00000000aea00000)
 Metaspace       used 83727K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K

Card table byte_map: [0x00007f2210418000,0x00007f2210819000] byte_map_base: 0x00007f2210018000

Marking Bits: (ParMarkBitMap*) 0x00007f22262266c0
 Begin Bits: [0x00007f21e8000000, 0x00007f21ea000000)
 End Bits:   [0x00007f21ea000000, 0x00007f21ec000000)

Polling page: 0x00007f2226e6c000

CodeCache: size=245760Kb used=52415Kb max_used=52424Kb free=193344Kb
 bounds [0x00007f2210bd9000, 0x00007f2213f79000, 0x00007f221fbd9000]
 total_blobs=14216 nmethods=13041 adapters=1084
 compilation: enabled

Compilation events (10 events):
Event: 2005.617 Thread 0x00007f22200c8800 20979       4       drzhark.mocreatures.entity.MoCEntityAmbient::func_70612_e (1764 bytes)
Event: 2005.617 Thread 0x00007f22200c6800 20980       4       drzhark.mocreatures.entity.MoCEntityInsect::func_70636_d (375 bytes)
Event: 2005.627 Thread 0x00007f22200c6800 nmethod 20980 0x00007f2213ed8d90 code [0x00007f2213ed9020, 0x00007f2213ed9920]
Event: 2005.633 Thread 0x00007f22200c8800 nmethod 20979 0x00007f2213f74cd0 code [0x00007f2213f750c0, 0x00007f2213f76320]
Event: 2005.670 Thread 0x00007f22200c3800 20981       4       drzhark.mocreatures.entity.MoCEntityInsect::getMoveSpeed (17 bytes)
Event: 2005.671 Thread 0x00007f22200c3800 nmethod 20981 0x00007f22139a35d0 code [0x00007f22139a3760, 0x00007f22139a3838]
Event: 2006.086 Thread 0x00007f22200c6800 20982       4       thaumcraft.client.fx.particles.FXGeneric::func_70539_a (69 bytes)
Event: 2006.087 Thread 0x00007f22200c6800 nmethod 20982 0x00007f22127128d0 code [0x00007f2212712a40, 0x00007f2212712b68]
Event: 2006.759 Thread 0x00007f22200ca800 20983       3       net.minecraft.pathfinding.PathNavigate::func_75491_a (6 bytes)
Event: 2006.759 Thread 0x00007f22200ca800 nmethod 20983 0x00007f2211247650 code [0x00007f22112477a0, 0x00007f22112478f0]

GC Heap History (10 events):
Event: 1985.564 GC heap before
{Heap before GC invocations=524 (full 9):
 PSYoungGen      total 262144K, used 200916K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 180224K, 100% used [0x00000000d5600000,0x00000000e0600000,0x00000000e0600000)
  from space 81920K, 25% used [0x00000000e5a00000,0x00000000e6e35350,0x00000000eaa00000)
  to   space 83968K, 0% used [0x00000000e0600000,0x00000000e0600000,0x00000000e5800000)
 ParOldGen       total 763904K, used 726144K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000ac5200f0,0x00000000aea00000)
 Metaspace       used 83706K, capacity 84465K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11266K, committed 11392K, reserved 1048576K
Event: 1985.577 GC heap after
Heap after GC invocations=524 (full 9):
 PSYoungGen      total 264192K, used 21035K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 180224K, 0% used [0x00000000d5600000,0x00000000d5600000,0x00000000e0600000)
  from space 83968K, 25% used [0x00000000e0600000,0x00000000e1a8ad60,0x00000000e5800000)
  to   space 83968K, 0% used [0x00000000e5800000,0x00000000e5800000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 727973K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000ac6e95c0,0x00000000aea00000)
 Metaspace       used 83706K, capacity 84465K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11266K, committed 11392K, reserved 1048576K
}
Event: 1990.074 GC heap before
{Heap before GC invocations=525 (full 9):
 PSYoungGen      total 264192K, used 201259K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 180224K, 100% used [0x00000000d5600000,0x00000000e0600000,0x00000000e0600000)
  from space 83968K, 25% used [0x00000000e0600000,0x00000000e1a8ad60,0x00000000e5800000)
  to   space 83968K, 0% used [0x00000000e5800000,0x00000000e5800000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 727973K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000ac6e95c0,0x00000000aea00000)
 Metaspace       used 83718K, capacity 84465K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11266K, committed 11392K, reserved 1048576K
Event: 1990.101 GC heap after
Heap after GC invocations=525 (full 9):
 PSYoungGen      total 266240K, used 20789K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 182272K, 0% used [0x00000000d5600000,0x00000000d5600000,0x00000000e0800000)
  from space 83968K, 24% used [0x00000000e5800000,0x00000000e6c4d4f0,0x00000000eaa00000)
  to   space 81920K, 0% used [0x00000000e0800000,0x00000000e0800000,0x00000000e5800000)
 ParOldGen       total 763904K, used 731457K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000aca50770,0x00000000aea00000)
 Metaspace       used 83718K, capacity 84465K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11266K, committed 11392K, reserved 1048576K
}
Event: 1995.004 GC heap before
{Heap before GC invocations=526 (full 9):
 PSYoungGen      total 266240K, used 203061K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 182272K, 100% used [0x00000000d5600000,0x00000000e0800000,0x00000000e0800000)
  from space 83968K, 24% used [0x00000000e5800000,0x00000000e6c4d4f0,0x00000000eaa00000)
  to   space 81920K, 0% used [0x00000000e0800000,0x00000000e0800000,0x00000000e5800000)
 ParOldGen       total 763904K, used 731457K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000aca50770,0x00000000aea00000)
 Metaspace       used 83722K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
Event: 1995.011 GC heap after
Heap after GC invocations=526 (full 9):
 PSYoungGen      total 264192K, used 20221K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 182272K, 0% used [0x00000000d5600000,0x00000000d5600000,0x00000000e0800000)
  from space 81920K, 24% used [0x00000000e0800000,0x00000000e1bbf540,0x00000000e5800000)
  to   space 79872K, 0% used [0x00000000e5c00000,0x00000000e5c00000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 732254K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000acb17850,0x00000000aea00000)
 Metaspace       used 83722K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
}
Event: 1999.093 GC heap before
{Heap before GC invocations=527 (full 9):
 PSYoungGen      total 264192K, used 202493K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 182272K, 100% used [0x00000000d5600000,0x00000000e0800000,0x00000000e0800000)
  from space 81920K, 24% used [0x00000000e0800000,0x00000000e1bbf540,0x00000000e5800000)
  to   space 79872K, 0% used [0x00000000e5c00000,0x00000000e5c00000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 732254K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000acb17850,0x00000000aea00000)
 Metaspace       used 83723K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
Event: 1999.100 GC heap after
Heap after GC invocations=527 (full 9):
 PSYoungGen      total 270336K, used 23622K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 190464K, 0% used [0x00000000d5600000,0x00000000d5600000,0x00000000e1000000)
  from space 79872K, 29% used [0x00000000e5c00000,0x00000000e73119c0,0x00000000eaa00000)
  to   space 77824K, 0% used [0x00000000e1000000,0x00000000e1000000,0x00000000e5c00000)
 ParOldGen       total 763904K, used 732532K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000acb5d2a0,0x00000000aea00000)
 Metaspace       used 83723K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
}
Event: 2003.472 GC heap before
{Heap before GC invocations=528 (full 9):
 PSYoungGen      total 270336K, used 214086K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 190464K, 100% used [0x00000000d5600000,0x00000000e1000000,0x00000000e1000000)
  from space 79872K, 29% used [0x00000000e5c00000,0x00000000e73119c0,0x00000000eaa00000)
  to   space 77824K, 0% used [0x00000000e1000000,0x00000000e1000000,0x00000000e5c00000)
 ParOldGen       total 763904K, used 732532K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 95% used [0x0000000080000000,0x00000000acb5d2a0,0x00000000aea00000)
 Metaspace       used 83724K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
Event: 2003.482 GC heap after
Heap after GC invocations=528 (full 9):
 PSYoungGen      total 268288K, used 22354K [0x00000000d5600000, 0x00000000eaa00000, 0x0000000100000000)
  eden space 190464K, 0% used [0x00000000d5600000,0x00000000d5600000,0x00000000e1000000)
  from space 77824K, 28% used [0x00000000e1000000,0x00000000e25d4be0,0x00000000e5c00000)
  to   space 73728K, 0% used [0x00000000e6200000,0x00000000e6200000,0x00000000eaa00000)
 ParOldGen       total 763904K, used 735723K [0x0000000080000000, 0x00000000aea00000, 0x00000000d5600000)
  object space 763904K, 96% used [0x0000000080000000,0x00000000ace7ac20,0x00000000aea00000)
 Metaspace       used 83724K, capacity 84471K, committed 84824K, reserved 1122304K
  class space    used 11072K, capacity 11267K, committed 11392K, reserved 1048576K
}

Deoptimization events (10 events):
Event: 2005.155 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22139a5224 method=drzhark.mocreatures.entity.MoCEntityInsect.func_70636_d()V @ 13
Event: 2005.201 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22118e8888 method=drzhark.mocreatures.entity.MoCEntityInsect.getMoveSpeed()F @ 8
Event: 2005.201 Thread 0x00007f222000c000 Uncommon trap: reason=speculate_class_check action=maybe_recompile pc=0x00007f2213ec9f44 method=drzhark.mocreatures.entity.MoCEntityAmbient.func_70612_e(FF)V @ 887
Event: 2005.201 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22139a5224 method=drzhark.mocreatures.entity.MoCEntityInsect.func_70636_d()V @ 13
Event: 2005.262 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22118e8888 method=drzhark.mocreatures.entity.MoCEntityInsect.getMoveSpeed()F @ 8
Event: 2005.262 Thread 0x00007f222000c000 Uncommon trap: reason=speculate_class_check action=maybe_recompile pc=0x00007f2213ec9f44 method=drzhark.mocreatures.entity.MoCEntityAmbient.func_70612_e(FF)V @ 887
Event: 2005.262 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22139a5224 method=drzhark.mocreatures.entity.MoCEntityInsect.func_70636_d()V @ 13
Event: 2005.308 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22118e8888 method=drzhark.mocreatures.entity.MoCEntityInsect.getMoveSpeed()F @ 8
Event: 2005.308 Thread 0x00007f222000c000 Uncommon trap: reason=speculate_class_check action=maybe_recompile pc=0x00007f2213ec9f44 method=drzhark.mocreatures.entity.MoCEntityAmbient.func_70612_e(FF)V @ 887
Event: 2005.308 Thread 0x00007f222000c000 Uncommon trap: reason=class_check action=maybe_recompile pc=0x00007f22139a5224 method=drzhark.mocreatures.entity.MoCEntityInsect.func_70636_d()V @ 13

Internal exceptions (10 events):
Event: 2006.606 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000dd14e6a0) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.633 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31d878) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.660 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31da78) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.684 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31dc78) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.708 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31de78) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.710 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31eb98) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.736 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31ed98) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.761 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31ef98) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.762 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31f198) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]
Event: 2006.785 Thread 0x00007f2198009800 Exception <a 'java/lang/InterruptedException': sleep interrupted> (0x00000000de31f398) thrown at [/HUDSON/workspace/8-2-build-linux-amd64/jdk8u40/2855/hotspot/src/share/vm/prims/jvm.cpp, line 3211]

Events (10 events):
Event: 2005.308 Thread 0x00007f222000c000 DEOPT PACKING pc=0x00007f22118e8888 sp=0x00007f2224f80a80
Event: 2005.308 Thread 0x00007f222000c000 DEOPT UNPACKING pc=0x00007f2210bde229 sp=0x00007f2224f80a30 mode 2
Event: 2005.308 Thread 0x00007f222000c000 Uncommon trap: trap_request=0xffffff76 fr.pc=0x00007f2213ec9f44
Event: 2005.308 Thread 0x00007f222000c000 DEOPT PACKING pc=0x00007f2213ec9f44 sp=0x00007f2224f80980
Event: 2005.308 Thread 0x00007f222000c000 DEOPT UNPACKING pc=0x00007f2210bde229 sp=0x00007f2224f80900 mode 2
Event: 2005.308 Thread 0x00007f222000c000 Uncommon trap: trap_request=0xffffffde fr.pc=0x00007f22139a5224
Event: 2005.308 Thread 0x00007f222000c000 DEOPT PACKING pc=0x00007f22139a5224 sp=0x00007f2224f80aa0
Event: 2005.308 Thread 0x00007f222000c000 DEOPT UNPACKING pc=0x00007f2210bde229 sp=0x00007f2224f80a70 mode 2
Event: 2005.671 Thread 0x00007f22200c3800 flushing nmethod 0x00007f22112475d0
Event: 2006.760 Thread 0x00007f22200ca800 flushing nmethod 0x00007f22116ad3d0


Dynamic libraries:
00400000-00401000 r-xp 00000000 08:03 1576930                            /usr/lib/jvm/java-8-oracle/jre/bin/java
00600000-00601000 rw-p 00000000 08:03 1576930                            /usr/lib/jvm/java-8-oracle/jre/bin/java
009ac000-009cd000 rw-p 00000000 00:00 0                                  [heap]
80000000-aea00000 rw-p 00000000 00:00 0 
aea00000-d5600000 ---p 00000000 00:00 0 
d5600000-eaa00000 rw-p 00000000 00:00 0 
eaa00000-100000000 ---p 00000000 00:00 0 
100000000-100b20000 rw-p 00000000 00:00 0 
100b20000-140000000 ---p 00000000 00:00 0 

```

followed by about 65,000 lines that look like this:

```

7f20c5e7b000-7f20c5e83000 rw-s 141225000 00:05 10498                     /dev/dri/card0
7f20c5e83000-7f20c5e8b000 rw-s 00000000 00:04 93961                      /drm mm object (deleted)
7f20c5e8b000-7f20c5e93000 rw-s 00000000 00:04 93960                      /drm mm object (deleted)
7f20c5e93000-7f20c5e9b000 rw-s 00000000 00:04 93959                      /drm mm object (deleted)
7f20c5e9b000-7f20c5ea3000 rw-s 00000000 00:04 93958                      /drm mm object (deleted)
7f20c5ea3000-7f20c5eab000 rw-s 14121d000 00:05 10498                     /dev/dri/card0
7f20c5eab000-7f20c5eb3000 rw-s 141215000 00:05 10498                     /dev/dri/card0
7f20c5eb3000-7f20c5ebb000 rw-s 14120d000 00:05 10498                     /dev/dri/card0
7f20c5ebb000-7f20c5ec3000 rw-s 141205000 00:05 10498                     /dev/dri/card0
7f20c5ec3000-7f20c5ecb000 rw-s 1411fd000 00:05 10498                     /dev/dri/card0
7f20c5ecb000-7f20c5ed3000 rw-s 1411f5000 00:05 10498                     /dev/dri/card0
7f20c5ed3000-7f20c5edb000 rw-s 1411ed000 00:05 10498                     /dev/dri/card0
7f20c5edb000-7f20c5ee3000 rw-s 1411e5000 00:05 10498                     /dev/dri/card0
7f20c5ee3000-7f20c5eeb000 rw-s 00000000 00:04 93953                      /drm mm object (deleted)
7f20c5eeb000-7f20c5ef3000 rw-s 00000000 00:04 93952                      /drm mm object (deleted)
7f20c5ef3000-7f20c5efb000 rw-s 00000000 00:04 93951                      /drm mm object (deleted)
7f20c5efb000-7f20c5f03000 rw-s 00000000 00:04 93950                      /drm mm object (deleted)
7f20c5f03000-7f20c5f0b000 rw-s 1411dd000 00:05 10498                     /dev/dri/card0
7f20c5f0b000-7f20c5f13000 rw-s 1411d5000 00:05 10498                     /dev/dri/card0

```

and finally this:

```

7f218685a000-7f218685b000 ---p 00000000 00:00 0 
7f218685b000-7f218705b000 rw-p 00000000 00:00 0                          [stack:5425]
7f218705b000-7f2187062000 r-xp 00000000 08:03 6167402                    /usr/lib/x86_64-linux-gnu/libogg.so.0.8.2
7f2187062000-7f2187262000 ---p 00007000 08:03 6167402                    /usr/lib/x86_64-linux-gnu/libogg.so.0.8.2
7f2187262000-7f2187263000 r--p 00007000 08:03 6167402                    /usr/lib/x86_64-linux-gnu/libogg.so.0.8.2
7f2187263000-7f2187264000 rw-p 00008000 08:03 6167402                    /usr/lib/x86_64-linux-gnu/libogg.so.0.8.2
7f2187264000-7f2187290000 r-xp 00000000 08:03 6167430                    /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f2187290000-7f218748f000 ---p 0002c000 08:03 6167430                    /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f218748f000-7f2187490000 r--p 0002b000 08:03 6167430                    /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f2187490000-7f2187491000 rw-p 0002c000 08:03 6167430                    /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f2187491000-7f2187744000 r-xp 00000000 08:03 6167414                    /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f2187744000-7f2187943000 ---p 002b3000 08:03 6167414                    /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f2187943000-7f218795f000 r--p 002b2000 08:03 6167414                    /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f218795f000-7f2187960000 rw-p 002ce000 08:03 6167414                    /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f2187960000-7f2187990000 r-xp 00000000 08:03 6164682                    /usr/lib/x86_64-linux-gnu/libFLAC.so.8.3.0
7f2187990000-7f2187b90000 ---p 00030000 08:03 6164682                    /usr/lib/x86_64-linux-gnu/libFLAC.so.8.3.0
7f2187b90000-7f2187b92000 r--p 00030000 08:03 6164682                    /usr/lib/x86_64-linux-gnu/libFLAC.so.8.3.0
7f2187b92000-7f2187b93000 rw-p 00032000 08:03 6164682                    /usr/lib/x86_64-linux-gnu/libFLAC.so.8.3.0
7f2187b93000-7f2187b98000 r-xp 00000000 08:03 6162801                    /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f2187b98000-7f2187d97000 ---p 00005000 08:03 6162801                    /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f2187d97000-7f2187d98000 r--p 00004000 08:03 6162801                    /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f2187d98000-7f2187d99000 rw-p 00005000 08:03 6162801                    /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f2187d99000-7f2187dfa000 r-xp 00000000 08:03 6160653                    /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7f2187dfa000-7f2187ff9000 ---p 00061000 08:03 6160653                    /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7f2187ff9000-7f2187ffb000 r--p 00060000 08:03 6160653                    /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7f2187ffb000-7f2187ffc000 rw-p 00062000 08:03 6160653                    /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7f2187ffc000-7f2188000000 rw-p 00000000 00:00 0 
7f2188000000-7f21880fb000 rw-p 00000000 00:00 0 
7f21880fb000-7f218c000000 ---p 00000000 00:00 0 
7f218c000000-7f218c545000 rw-p 00000000 00:00 0 
7f218c545000-7f2190000000 ---p 00000000 00:00 0 
7f2190000000-7f219018f000 rw-p 00000000 00:00 0 
7f219018f000-7f2194000000 ---p 00000000 00:00 0 
7f2194000000-7f2194001000 r--s 00000000 08:03 2759578                    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-4
7f2194001000-7f2194005000 r--s 00000000 08:03 2759414                    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-4
7f2194005000-7f2194015000 rw-s 00000000 00:04 51735                      /drm mm object (deleted)
7f2194015000-7f219401d000 rw-s 00000000 00:04 54574                      /drm mm object (deleted)
7f219401d000-7f2194025000 rw-s 00000000 00:04 54573                      /drm mm object (deleted)
7f2194025000-7f219402d000 rw-s 00000000 00:04 54572                      /drm mm object (deleted)
7f219402d000-7f2194031000 rw-s 00000000 00:04 54571                      /drm mm object (deleted)
7f2194031000-7f2194035000 rw-s 00000000 00:04 54570                      /drm mm object (deleted)
7f2194035000-7f2194039000 rw-s 00000000 00:04 54569                      /drm mm object (deleted)
7f2194039000-7f219403d000 rw-s 00000000 00:04 54568                      /drm mm object (deleted)
7f219403d000-7f2194045000 rw-s 00000000 00:04 54567                      /drm mm object (deleted)
7f2194045000-7f219404d000 r-xp 00000000 08:03 5247030                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f219404d000-7f219424c000 ---p 00008000 08:03 5247030                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f219424c000-7f219424d000 r--p 00007000 08:03 5247030                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f219424d000-7f219424e000 rw-p 00008000 08:03 5247030                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f219424e000-7f219424f000 rw-p 00000000 00:00 0 
7f219424f000-7f2194295000 r-xp 00000000 08:03 5242976                    /lib/x86_64-linux-gnu/libdbus-1.so.3.8.7
7f2194295000-7f2194494000 ---p 00046000 08:03 5242976                    /lib/x86_64-linux-gnu/libdbus-1.so.3.8.7
7f2194494000-7f2194496000 r--p 00045000 08:03 5242976                    /lib/x86_64-linux-gnu/libdbus-1.so.3.8.7
7f2194496000-7f2194497000 rw-p 00047000 08:03 5242976                    /lib/x86_64-linux-gnu/libdbus-1.so.3.8.7
7f2194497000-7f2194503000 r-xp 00000000 08:03 6423479                    /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-4.0.so
7f2194503000-7f2194702000 ---p 0006c000 08:03 6423479                    /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-4.0.so
7f2194702000-7f2194703000 r--p 0006b000 08:03 6423479                    /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-4.0.so
7f2194703000-7f2194704000 rw-p 0006c000 08:03 6423479                    /usr/lib/x86_64-linux-gnu/pulseaudio/libpulsecommon-4.0.so
7f2194704000-7f219470e000 r-xp 00000000 08:03 5242984                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f219470e000-7f219490d000 ---p 0000a000 08:03 5242984                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f219490d000-7f219490e000 r--p 00009000 08:03 5242984                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f219490e000-7f219490f000 rw-p 0000a000 08:03 5242984                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
7f219490f000-7f219495b000 r-xp 00000000 08:03 6164222                    /usr/lib/x86_64-linux-gnu/libpulse.so.0.16.2
7f219495b000-7f2194b5a000 ---p 0004c000 08:03 6164222                    /usr/lib/x86_64-linux-gnu/libpulse.so.0.16.2
7f2194b5a000-7f2194b5c000 r--p 0004b000 08:03 6164222                    /usr/lib/x86_64-linux-gnu/libpulse.so.0.16.2
7f2194b5c000-7f2194b5d000 rw-p 0004d000 08:03 6164222                    /usr/lib/x86_64-linux-gnu/libpulse.so.0.16.2
7f2194b5d000-7f2194bb2000 r-xp 00000000 08:03 3804758                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/libopenal64.so
7f2194bb2000-7f2194db1000 ---p 00055000 08:03 3804758                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/libopenal64.so
7f2194db1000-7f2194db4000 r--p 00054000 08:03 3804758                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/libopenal64.so
7f2194db4000-7f2194db5000 rw-p 00057000 08:03 3804758                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/libopenal64.so
7f2194db5000-7f2194fb6000 rw-p 00000000 00:00 0 
7f2194fb6000-7f21951b6000 rw-p 00000000 00:00 0 
7f21951b6000-7f21953b6000 rw-p 00000000 00:00 0 
7f21953b6000-7f21955b6000 rw-p 00000000 00:00 0 
7f21955b6000-7f21957b6000 rw-p 00000000 00:00 0 
7f21957b6000-7f21959b6000 rw-p 00000000 00:00 0 
7f21959b6000-7f21959b9000 ---p 00000000 00:00 0 
7f21959b9000-7f2195bb7000 rw-p 00000000 00:00 0                          [stack:5422]
7f2195bb7000-7f2195bba000 ---p 00000000 00:00 0 
7f2195bba000-7f2195fb8000 rw-p 00000000 00:00 0                          [stack:5423]
7f2195fb8000-7f21961b8000 rw-p 00000000 00:00 0 
7f21961b8000-7f21963b8000 rw-p 00000000 00:00 0 
7f21963b8000-7f21965b8000 rw-p 00000000 00:00 0 
7f21965b8000-7f21965ea000 r-xp 00000000 08:03 1577194                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libsunec.so
7f21965ea000-7f21967e9000 ---p 00032000 08:03 1577194                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libsunec.so
7f21967e9000-7f21967ef000 rw-p 00031000 08:03 1577194                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libsunec.so
7f21967ef000-7f21969ff000 rw-p 00000000 00:00 0 
7f21969ff000-7f2196bff000 rw-p 00000000 00:00 0 
7f2196bff000-7f2196df5000 rw-p 00000000 00:00 0 
7f2196df5000-7f2196dff000 ---p 00000000 00:00 0 
7f2196dff000-7f2196fff000 rw-p 00000000 00:00 0 
7f2196fff000-7f2198000000 rw-p 00000000 00:00 0 
7f2198000000-7f219810c000 rw-p 00000000 00:00 0 
7f219810c000-7f219c000000 ---p 00000000 00:00 0 
7f219c000000-7f219c008000 rw-s 00000000 00:04 54566                      /drm mm object (deleted)
7f219c008000-7f219c010000 rw-s 00000000 00:04 54565                      /drm mm object (deleted)
7f219c010000-7f219c018000 rw-s 00000000 00:04 54564                      /drm mm object (deleted)
7f219c018000-7f219c020000 rw-s 00000000 00:04 54563                      /drm mm object (deleted)
7f219c020000-7f219c028000 rw-s 00000000 00:04 54562                      /drm mm object (deleted)
7f219c028000-7f219c030000 rw-s 00000000 00:04 54561                      /drm mm object (deleted)
7f219c030000-7f219c038000 rw-s 00000000 00:04 54560                      /drm mm object (deleted)
7f219c038000-7f219c040000 rw-s 00000000 00:04 54559                      /drm mm object (deleted)
7f219c040000-7f219c044000 rw-s 00000000 00:04 54558                      /drm mm object (deleted)
7f219c044000-7f219c048000 rw-s 00000000 00:04 54557                      /drm mm object (deleted)
7f219c048000-7f219c04c000 rw-s 00000000 00:04 54556                      /drm mm object (deleted)
7f219c04c000-7f219c050000 rw-s 00000000 00:04 54555                      /drm mm object (deleted)
7f219c050000-7f219c058000 rw-s 00000000 00:04 54554                      /drm mm object (deleted)
7f219c058000-7f219c05c000 rw-s 00000000 00:04 54553                      /drm mm object (deleted)
7f219c05c000-7f219c060000 rw-s 00000000 00:04 54552                      /drm mm object (deleted)
7f219c060000-7f219c064000 rw-s 00000000 00:04 54551                      /drm mm object (deleted)
7f219c064000-7f219c068000 rw-s 00000000 00:04 54550                      /drm mm object (deleted)
7f219c068000-7f219c06c000 rw-s 00000000 00:04 54549                      /drm mm object (deleted)
7f219c06c000-7f219c070000 rw-s 00000000 00:04 54548                      /drm mm object (deleted)
7f219c070000-7f219c074000 rw-s 00000000 00:04 54547                      /drm mm object (deleted)
7f219c074000-7f219c078000 rw-s 00000000 00:04 54546                      /drm mm object (deleted)
7f219c078000-7f219c094000 rw-s 00000000 00:04 54545                      /drm mm object (deleted)
7f219c094000-7f219c098000 rw-s 00000000 00:04 54544                      /drm mm object (deleted)
7f219c098000-7f219c09c000 rw-s 00000000 00:04 54543                      /drm mm object (deleted)
7f219c09c000-7f219c0a0000 rw-s 00000000 00:04 54542                      /drm mm object (deleted)
7f219c0a0000-7f219c0a4000 rw-s 00000000 00:04 52582                      /drm mm object (deleted)
7f219c0a4000-7f219c0a8000 rw-s 00000000 00:04 52581                      /drm mm object (deleted)
7f219c0a8000-7f219c0ac000 rw-s 00000000 00:04 52580                      /drm mm object (deleted)
7f219c0ac000-7f219c0b0000 rw-s 00000000 00:04 52579                      /drm mm object (deleted)
7f219c0b0000-7f219c0b4000 rw-s 00000000 00:04 52578                      /drm mm object (deleted)
7f219c0b4000-7f219c0b8000 rw-s 00000000 00:04 52577                      /drm mm object (deleted)
7f219c0b8000-7f219c0bc000 rw-s 00000000 00:04 52576                      /drm mm object (deleted)
7f219c0bc000-7f219c0c0000 rw-s 00000000 00:04 52575                      /drm mm object (deleted)
7f219c0c0000-7f219c0c4000 rw-s 00000000 00:04 52574                      /drm mm object (deleted)
7f219c0c4000-7f219c0c8000 rw-s 00000000 00:04 52573                      /drm mm object (deleted)
7f219c0c8000-7f219c0d0000 rw-s 00000000 00:04 52572                      /drm mm object (deleted)
7f219c0d0000-7f219c0d3000 r--s 00015000 08:03 3804797                    /home/lavaslayer/.minecraft/mods/carpentersblocks/CarpentersBlocksCachedResources.zip
7f219c0d3000-7f219c0d4000 r--s 00000000 08:03 2759560                    /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le64.cache-4
7f219c0d4000-7f219c0d6000 rw-s 00000000 00:04 30716                      /drm mm object (deleted)
7f219c0d6000-7f219c0de000 rw-s 100c45000 00:05 10498                     /dev/dri/card0
7f219c0de000-7f219c0fa000 rw-s 00000000 00:04 54528                      /drm mm object (deleted)
7f219c0fa000-7f219c116000 rw-s 00000000 00:04 54527                      /drm mm object (deleted)
7f219c116000-7f219c316000 rw-p 00000000 00:00 0 
7f219c316000-7f219c516000 rw-p 00000000 00:00 0 
7f219c516000-7f219c52d000 r-xp 00000000 08:03 5244098                    /lib/x86_64-linux-gnu/libresolv-2.19.so
7f219c52d000-7f219c72d000 ---p 00017000 08:03 5244098                    /lib/x86_64-linux-gnu/libresolv-2.19.so
7f219c72d000-7f219c72e000 r--p 00017000 08:03 5244098                    /lib/x86_64-linux-gnu/libresolv-2.19.so
7f219c72e000-7f219c72f000 rw-p 00018000 08:03 5244098                    /lib/x86_64-linux-gnu/libresolv-2.19.so
7f219c72f000-7f219c731000 rw-p 00000000 00:00 0 
7f219c731000-7f219c736000 r-xp 00000000 08:03 5244086                    /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f219c736000-7f219c935000 ---p 00005000 08:03 5244086                    /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f219c935000-7f219c936000 r--p 00004000 08:03 5244086                    /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f219c936000-7f219c937000 rw-p 00005000 08:03 5244086                    /lib/x86_64-linux-gnu/libnss_dns-2.19.so
7f219c937000-7f219c939000 r-xp 00000000 08:03 5246953                    /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f219c939000-7f219cb38000 ---p 00002000 08:03 5246953                    /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f219cb38000-7f219cb39000 r--p 00001000 08:03 5246953                    /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f219cb39000-7f219cb3a000 rw-p 00002000 08:03 5246953                    /lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2
7f219cb3a000-7f219da3f000 rw-p 00000000 00:00 0 
7f219da3f000-7f219da76000 r-xp 00000000 08:03 6167876                    /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0.0.0
7f219da76000-7f219dc75000 ---p 00037000 08:03 6167876                    /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0.0.0
7f219dc75000-7f219dc76000 r--p 00036000 08:03 6167876                    /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0.0.0
7f219dc76000-7f219dc77000 rw-p 00037000 08:03 6167876                    /usr/lib/x86_64-linux-gnu/libtxc_dxtn_s2tc.so.0.0.0
7f219dc77000-7f219dc8f000 r-xp 00000000 08:03 5247033                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f219dc8f000-7f219de8e000 ---p 00018000 08:03 5247033                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f219de8e000-7f219de8f000 r--p 00017000 08:03 5247033                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f219de8f000-7f219de90000 rw-p 00018000 08:03 5247033                    /lib/x86_64-linux-gnu/libz.so.1.2.8
7f219de90000-7f219de98000 r-xp 00000000 08:03 6166555                    /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
7f219de98000-7f219e097000 ---p 00008000 08:03 6166555                    /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
7f219e097000-7f219e098000 r--p 00007000 08:03 6166555                    /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
7f219e098000-7f219e099000 rw-p 00008000 08:03 6166555                    /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.1
7f219e099000-7f219e189000 r-xp 00000000 08:03 6166236                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.20
7f219e189000-7f219e389000 ---p 000f0000 08:03 6166236                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.20
7f219e389000-7f219e391000 r--p 000f0000 08:03 6166236                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.20
7f219e391000-7f219e393000 rw-p 000f8000 08:03 6166236                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.20
7f219e393000-7f219e3a8000 rw-p 00000000 00:00 0 
7f219e3a8000-7f219e3b4000 r-xp 00000000 08:03 6160651                    /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
7f219e3b4000-7f219e5b3000 ---p 0000c000 08:03 6160651                    /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
7f219e5b3000-7f219e5b4000 r--p 0000b000 08:03 6160651                    /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
7f219e5b4000-7f219e5b5000 rw-p 0000c000 08:03 6160651                    /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
7f219e5b5000-7f219e5bb000 r-xp 00000000 08:03 6160614                    /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0
7f219e5bb000-7f219e7ba000 ---p 00006000 08:03 6160614                    /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0
7f219e7ba000-7f219e7bb000 r--p 00005000 08:03 6160614                    /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0
7f219e7bb000-7f219e7bc000 rw-p 00006000 08:03 6160614                    /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0
7f219e7bc000-7f219e7dd000 r-xp 00000000 08:03 6160609                    /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
7f219e7dd000-7f219e9dc000 ---p 00021000 08:03 6160609                    /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
7f219e9dc000-7f219e9dd000 r--p 00020000 08:03 6160609                    /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
7f219e9dd000-7f219e9de000 rw-p 00021000 08:03 6160609                    /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
7f219e9de000-7f219ef1b000 r-xp 00000000 08:03 6422886                    /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
7f219ef1b000-7f219f11b000 ---p 0053d000 08:03 6422886                    /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
7f219f11b000-7f219f136000 r--p 0053d000 08:03 6422886                    /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
7f219f136000-7f219f13c000 rw-p 00558000 08:03 6422886                    /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
7f219f13c000-7f219f146000 rw-p 00000000 00:00 0 
7f219f146000-7f219f1b2000 r-xp 00000000 08:03 5243851                    /lib/x86_64-linux-gnu/libpcre.so.3.13.1
7f219f1b2000-7f219f3b1000 ---p 0006c000 08:03 5243851                    /lib/x86_64-linux-gnu/libpcre.so.3.13.1
7f219f3b1000-7f219f3b2000 r--p 0006b000 08:03 5243851                    /lib/x86_64-linux-gnu/libpcre.so.3.13.1
7f219f3b2000-7f219f3b3000 rw-p 0006c000 08:03 5243851                    /lib/x86_64-linux-gnu/libpcre.so.3.13.1
7f219f3b3000-7f219f3d4000 r-xp 00000000 08:03 5243850                    /lib/x86_64-linux-gnu/libselinux.so.1
7f219f3d4000-7f219f5d3000 ---p 00021000 08:03 5243850                    /lib/x86_64-linux-gnu/libselinux.so.1
7f219f5d3000-7f219f5d4000 r--p 00020000 08:03 5243850                    /lib/x86_64-linux-gnu/libselinux.so.1
7f219f5d4000-7f219f5d5000 rw-p 00021000 08:03 5243850                    /lib/x86_64-linux-gnu/libselinux.so.1
7f219f5d5000-7f219f5d7000 rw-p 00000000 00:00 0 
7f219f5d7000-7f219f5e7000 r-xp 00000000 08:03 5244310                    /lib/x86_64-linux-gnu/libudev.so.1.4.0
7f219f5e7000-7f219f7e7000 ---p 00010000 08:03 5244310                    /lib/x86_64-linux-gnu/libudev.so.1.4.0
7f219f7e7000-7f219f7e8000 r--p 00010000 08:03 5244310                    /lib/x86_64-linux-gnu/libudev.so.1.4.0
7f219f7e8000-7f219f7e9000 rw-p 00011000 08:03 5244310                    /lib/x86_64-linux-gnu/libudev.so.1.4.0
7f219f7e9000-7f219f7f4000 r-xp 00000000 08:03 6160604                    /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7f219f7f4000-7f219f9f3000 ---p 0000b000 08:03 6160604                    /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7f219f9f3000-7f219f9f4000 r--p 0000a000 08:03 6160604                    /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7f219f9f4000-7f219f9f5000 rw-p 0000b000 08:03 6160604                    /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7f219f9f5000-7f219f9f6000 r-xp 00000000 08:03 6167036                    /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7f219f9f6000-7f219fbf5000 ---p 00001000 08:03 6167036                    /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7f219fbf5000-7f219fbf6000 r--p 00000000 08:03 6167036                    /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7f219fbf6000-7f219fbf7000 rw-p 00001000 08:03 6167036                    /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7f219fbf7000-7f219fbfc000 r-xp 00000000 08:03 6167965                    /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7f219fbfc000-7f219fdfb000 ---p 00005000 08:03 6167965                    /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7f219fdfb000-7f219fdfc000 r--p 00004000 08:03 6167965                    /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7f219fdfc000-7f219fdfd000 rw-p 00005000 08:03 6167965                    /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7f219fdfd000-7f219fdff000 r-xp 00000000 08:03 6167957                    /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7f219fdff000-7f219fffe000 ---p 00002000 08:03 6167957                    /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7f219fffe000-7f219ffff000 r--p 00001000 08:03 6167957                    /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7f219ffff000-7f21a0000000 rw-p 00002000 08:03 6167957                    /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7f21a0000000-7f21a0021000 rw-p 00000000 00:00 0 
7f21a0021000-7f21a4000000 ---p 00000000 00:00 0 
7f21a4000000-7f21a4021000 rw-p 00000000 00:00 0 
7f21a4021000-7f21a8000000 ---p 00000000 00:00 0 
7f21a8000000-7f21a8021000 rw-p 00000000 00:00 0 
7f21a8021000-7f21ac000000 ---p 00000000 00:00 0 
7f21ac000000-7f21ac08a000 rw-p 00000000 00:00 0 
7f21ac08a000-7f21b0000000 ---p 00000000 00:00 0 
7f21b0000000-7f21b0021000 rw-p 00000000 00:00 0 
7f21b0021000-7f21b4000000 ---p 00000000 00:00 0 
7f21b4000000-7f21b4021000 rw-p 00000000 00:00 0 
7f21b4021000-7f21b8000000 ---p 00000000 00:00 0 
7f21b8000000-7f21b8001000 rw-s 00000000 00:04 51700                      /drm mm object (deleted)
7f21b8001000-7f21b8004000 r--s 00015000 08:03 3804797                    /home/lavaslayer/.minecraft/mods/carpentersblocks/CarpentersBlocksCachedResources.zip
7f21b8004000-7f21b800c000 rw-s 100c3d000 00:05 10498                     /dev/dri/card0
7f21b800c000-7f21b801c000 rw-s 100c2d000 00:05 10498                     /dev/dri/card0
7f21b801c000-7f21b801d000 rw-s 00000000 00:04 80447                      /drm mm object (deleted)
7f21b801d000-7f21b801e000 rw-s 00000000 00:04 80446                      /drm mm object (deleted)
7f21b801e000-7f21b801f000 rw-s 00000000 00:04 80445                      /drm mm object (deleted)
7f21b801f000-7f21b8020000 rw-s 00000000 00:04 80444                      /drm mm object (deleted)
7f21b8020000-7f21b8028000 rw-s 00000000 00:04 71447                      /drm mm object (deleted)
7f21b8028000-7f21b802c000 rw-s 00000000 00:04 64947                      /drm mm object (deleted)
7f21b802c000-7f21b809c000 rw-s 00000000 00:04 52554                      /drm mm object (deleted)
7f21b809c000-7f21b80a1000 r--s 0003f000 08:03 1577097                    /usr/lib/jvm/java-8-oracle/jre/lib/ext/sunjce_provider.jar
7f21b80a1000-7f21b80a2000 r--s 00009000 08:03 1577088                    /usr/lib/jvm/java-8-oracle/jre/lib/ext/sunec.jar
7f21b80a2000-7f21b80a5000 r--s 0003a000 08:03 1577094                    /usr/lib/jvm/java-8-oracle/jre/lib/ext/sunpkcs11.jar
7f21b80a5000-7f21b80bf000 r--s 00196000 08:03 3803251                    /home/lavaslayer/.minecraft/mods/JustAnotherSpawner-0.16.18.jar
7f21b80bf000-7f21b80c3000 r--s 0001b000 08:03 3803250                    /home/lavaslayer/.minecraft/mods/zCraftingManager 0.7.5 mc1.7.10.zip
7f21b80c3000-7f21b80c7000 r--s 00038000 08:03 3803206                    /home/lavaslayer/.minecraft/mods/yArchimedesShips-1.7.1.jar
7f21b80c7000-7f21b80ca000 r--s 00013000 08:03 3803249                    /home/lavaslayer/.minecraft/mods/WildCaves3-0.4.3.6(1.7.2).jar
7f21b80ca000-7f21b80d0000 r--s 00040000 08:03 3803248                    /home/lavaslayer/.minecraft/mods/weaponmod-1.14.3.jar
7f21b80d0000-7f21b80da000 r--s 00096000 08:03 3803247                    /home/lavaslayer/.minecraft/mods/UndergroundBiomesConstructs-1.7.2-test39.jar
7f21b80da000-7f21b80dc000 r--s 00005000 08:03 3803246                    /home/lavaslayer/.minecraft/mods/TooMuchLoot-1.7.10-3.0.1.B22-universal.jar
7f21b80dc000-7f21b80dd000 r--s 00004000 08:03 3803245                    /home/lavaslayer/.minecraft/mods/ThaumcraftMobAspects-1.7.2-2A.jar
7f21b80dd000-7f21b80e0000 r--s 0001b000 08:03 3803243                    /home/lavaslayer/.minecraft/mods/Thaumcarpentry-0.0.1.5-1.7.10.jar
7f21b80e0000-7f21b80e1000 r--s 00014000 08:03 3803242                    /home/lavaslayer/.minecraft/mods/Staircraftmod 1.7 - 1.7.10 Forge.jar
7f21b80e1000-7f21b80e3000 r--s 00015000 08:03 3803241                    /home/lavaslayer/.minecraft/mods/SpecialAI-1.7.10-1.1.0.jar
7f21b80e3000-7f21b80e6000 r--s 00019000 08:03 3803240                    /home/lavaslayer/.minecraft/mods/Slabcraftmod 1.7 - 1.7.10 Forge.jar
7f21b80e6000-7f21b80e9000 r--s 00022000 08:03 3803238                    /home/lavaslayer/.minecraft/mods/Ruins-1.7.10.zip
7f21b80e9000-7f21b80f0000 r--s 0005b000 08:03 3803236                    /home/lavaslayer/.minecraft/mods/roguelike-1.7.10-1.3.5.jar
7f21b80f0000-7f21b810f000 r--s 004c6000 08:03 3803235                    /home/lavaslayer/.minecraft/mods/ProjectZulu-1.7.10-1.3f.jar
7f21b810f000-7f21b8141000 r--s 0010e000 08:03 3803234                    /home/lavaslayer/.minecraft/mods/plantmegapack-4.10-1.7.10-1230.jar
7f21b8141000-7f21b8142000 r--s 00009000 08:03 3803233                    /home/lavaslayer/.minecraft/mods/NewDungeons-0.3(1.7.10).jar
7f21b8142000-7f21b8155000 r--s 014a8000 08:03 3803232                    /home/lavaslayer/.minecraft/mods/musiccraft-2.9.8.2.jar
7f21b8155000-7f21b8161000 r--s 0019b000 08:03 3803231                    /home/lavaslayer/.minecraft/mods/MrCrayfishFurnitureModv3.4.7(1.7.10).jar
7f21b8161000-7f21b8169000 r--s 00086000 08:03 3803228                    /home/lavaslayer/.minecraft/mods/MoarSigns-1.7.10-1.1.3.jar
7f21b8169000-7f21b8171000 r--s 00126000 08:03 3803227                    /home/lavaslayer/.minecraft/mods/malisisdoors-1.7.10-1.3.3.jar
7f21b8171000-7f21b81a0000 r--s 01d47000 08:03 3803225                    /home/lavaslayer/.minecraft/mods/LycanitesMobsComplete 1.10.7.9 [1.7.10].jar
7f21b81a0000-7f21b81a7000 r--s 0005b000 08:03 3803224                    /home/lavaslayer/.minecraft/mods/Lots of Food-1.7.10 v6.jar
7f21b81a7000-7f21b81b3000 r--s 00074000 08:03 3801362                    /home/lavaslayer/.minecraft/mods/GardenStuff-1.7.10-1.3.2.jar
7f21b81b3000-7f21b81b5000 r-xp 00000000 08:03 6167953                    /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7f21b81b5000-7f21b83b4000 ---p 00002000 08:03 6167953                    /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7f21b83b4000-7f21b83b5000 r--p 00001000 08:03 6167953                    /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7f21b83b5000-7f21b83b6000 rw-p 00002000 08:03 6167953                    /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7f21b83b6000-7f21b83b9000 r-xp 00000000 08:03 6167951                    /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7f21b83b9000-7f21b85b9000 ---p 00003000 08:03 6167951                    /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7f21b85b9000-7f21b85ba000 r--p 00003000 08:03 6167951                    /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7f21b85ba000-7f21b85bb000 rw-p 00004000 08:03 6167951                    /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7f21b85bb000-7f21b85d0000 r-xp 00000000 08:03 6167955                    /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7f21b85d0000-7f21b87cf000 ---p 00015000 08:03 6167955                    /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7f21b87cf000-7f21b87d1000 r--p 00014000 08:03 6167955                    /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7f21b87d1000-7f21b87d2000 rw-p 00016000 08:03 6167955                    /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7f21b87d2000-7f21b87d3000 r-xp 00000000 08:03 6162621                    /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7f21b87d3000-7f21b89d2000 ---p 00001000 08:03 6162621                    /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7f21b89d2000-7f21b89d3000 r--p 00000000 08:03 6162621                    /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7f21b89d3000-7f21b89d4000 rw-p 00001000 08:03 6162621                    /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7f21b89d4000-7f21b89d6000 r-xp 00000000 08:03 6166549                    /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f21b89d6000-7f21b8bd5000 ---p 00002000 08:03 6166549                    /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f21b8bd5000-7f21b8bd6000 r--p 00001000 08:03 6166549                    /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f21b8bd6000-7f21b8bd7000 rw-p 00002000 08:03 6166549                    /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7f21b8bd7000-7f21b8bfc000 r-xp 00000000 08:03 6160826                    /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7f21b8bfc000-7f21b8dfb000 ---p 00025000 08:03 6160826                    /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7f21b8dfb000-7f21b8dfe000 r--p 00024000 08:03 6160826                    /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7f21b8dfe000-7f21b8dff000 rw-p 00027000 08:03 6160826                    /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7f21b8dff000-7f21b8e00000 rw-p 00000000 00:00 0 
7f21b8e00000-7f21b8e26000 r-xp 00000000 08:03 5244187                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
7f21b8e26000-7f21b9025000 ---p 00026000 08:03 5244187                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
7f21b9025000-7f21b9028000 r--p 00025000 08:03 5244187                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
7f21b9028000-7f21b9029000 rw-p 00028000 08:03 5244187                    /lib/x86_64-linux-gnu/libexpat.so.1.6.0
7f21b9029000-7f21b90bf000 r-xp 00000000 08:03 6422536                    /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
7f21b90bf000-7f21b92be000 ---p 00096000 08:03 6422536                    /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
7f21b92be000-7f21b92c1000 r--p 00095000 08:03 6422536                    /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
7f21b92c1000-7f21b92c2000 rw-p 00098000 08:03 6422536                    /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1.2.0
7f21b92c2000-7f21b94c3000 rw-p 00000000 00:00 0 
7f21b94c3000-7f21b96c3000 rw-p 00000000 00:00 0 
7f21b96c3000-7f21b96c6000 ---p 00000000 00:00 0 
7f21b96c6000-7f21b98c4000 rw-p 00000000 00:00 0                          [stack:5439]
7f21b98c4000-7f21b98c7000 ---p 00000000 00:00 0 
7f21b98c7000-7f21b9ac5000 rw-p 00000000 00:00 0                          [stack:5388]
7f21b9ac5000-7f21b9ac8000 ---p 00000000 00:00 0 
7f21b9ac8000-7f21b9ec6000 rw-p 00000000 00:00 0                          [stack:5387]
7f21b9ec6000-7f21b9eca000 r-xp 00000000 08:03 6167068                    /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f21b9eca000-7f21ba0ca000 ---p 00004000 08:03 6167068                    /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f21ba0ca000-7f21ba0cb000 r--p 00004000 08:03 6167068                    /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f21ba0cb000-7f21ba0cc000 rw-p 00005000 08:03 6167068                    /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7f21ba0cc000-7f21ba0d5000 r-xp 00000000 08:03 6167050                    /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f21ba0d5000-7f21ba2d4000 ---p 00009000 08:03 6167050                    /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f21ba2d4000-7f21ba2d5000 r--p 00008000 08:03 6167050                    /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f21ba2d5000-7f21ba2d6000 rw-p 00009000 08:03 6167050                    /usr/lib/x86_64-linux-gnu/libXrandr.so.2.2.0
7f21ba2d6000-7f21ba342000 r-xp 00000000 08:03 3804752                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/liblwjgl64.so
7f21ba342000-7f21ba541000 ---p 0006c000 08:03 3804752                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/liblwjgl64.so
7f21ba541000-7f21ba543000 r--p 0006b000 08:03 3804752                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/liblwjgl64.so
7f21ba543000-7f21ba544000 rw-p 0006d000 08:03 3804752                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309/liblwjgl64.so
7f21ba544000-7f21ba545000 r-xp 00000000 08:03 1577233                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjawt.so
7f21ba545000-7f21ba744000 ---p 00001000 08:03 1577233                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjawt.so
7f21ba744000-7f21ba745000 rw-p 00000000 08:03 1577233                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjawt.so
7f21ba745000-7f21ba945000 rw-p 00000000 00:00 0 
7f21ba945000-7f21ba964000 r-xp 00000000 08:03 1577248                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libunpack.so
7f21ba964000-7f21bab63000 ---p 0001f000 08:03 1577248                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libunpack.so
7f21bab63000-7f21bab67000 rw-p 0001e000 08:03 1577248                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libunpack.so
7f21bab67000-7f21bb378000 rw-p 00000000 00:00 0 
7f21bb378000-7f21bb37b000 ---p 00000000 00:00 0 
7f21bb37b000-7f21bb579000 rw-p 00000000 00:00 0                          [stack:5438]
7f21bb579000-7f21bb57c000 ---p 00000000 00:00 0 
7f21bb57c000-7f21bb77a000 rw-p 00000000 00:00 0                          [stack:5529]
7f21bb77a000-7f21bb7e3000 r-xp 00000000 08:03 1577204                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libt2k.so
7f21bb7e3000-7f21bb9e2000 ---p 00069000 08:03 1577204                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libt2k.so
7f21bb9e2000-7f21bb9e9000 rw-p 00068000 08:03 1577204                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libt2k.so
7f21bb9e9000-7f21bbbf9000 rw-p 00000000 00:00 0 
7f21bbbf9000-7f21bbbfc000 ---p 00000000 00:00 0 
7f21bbbfc000-7f21bbdfa000 rw-p 00000000 00:00 0                          [stack:5382]
7f21bbdfa000-7f21bbdff000 r-xp 00000000 08:03 6161623                    /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f21bbdff000-7f21bbffe000 ---p 00005000 08:03 6161623                    /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f21bbffe000-7f21bbfff000 r--p 00004000 08:03 6161623                    /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f21bbfff000-7f21bc000000 rw-p 00005000 08:03 6161623                    /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f21bc000000-7f21bc021000 rw-p 00000000 00:00 0 
7f21bc021000-7f21c0000000 ---p 00000000 00:00 0 
7f21c0000000-7f21c0021000 rw-p 00000000 00:00 0 
7f21c0021000-7f21c4000000 ---p 00000000 00:00 0 
7f21c4000000-7f21c6551000 rw-p 00000000 00:00 0 
7f21c6551000-7f21c8000000 ---p 00000000 00:00 0 
7f21c8000000-7f21c9742000 rw-p 00000000 00:00 0 
7f21c9742000-7f21cc000000 ---p 00000000 00:00 0 
7f21cc000000-7f21ce481000 rw-p 00000000 00:00 0 
7f21ce481000-7f21d0000000 ---p 00000000 00:00 0 
7f21d0000000-7f21d2b76000 rw-p 00000000 00:00 0 
7f21d2b76000-7f21d4000000 ---p 00000000 00:00 0 
7f21d4000000-7f21d4021000 rw-p 00000000 00:00 0 
7f21d4021000-7f21d8000000 ---p 00000000 00:00 0 
7f21d8000000-7f21d8021000 rw-p 00000000 00:00 0 
7f21d8021000-7f21dc000000 ---p 00000000 00:00 0 
7f21dc000000-7f21dc003000 r--s 00016000 08:03 3803230                    /home/lavaslayer/.minecraft/mods/MoVillages-1.3.1.jar
7f21dc003000-7f21dc006000 r--s 00019000 08:03 3803229                    /home/lavaslayer/.minecraft/mods/MobProperties-1.7.10-0.3.4(1).jar
7f21dc006000-7f21dc007000 r--s 00011000 08:03 3803223                    /home/lavaslayer/.minecraft/mods/LostBooks-1.7.10-1.2.2.jar
7f21dc007000-7f21dc009000 r--s 00026000 08:03 3802572                    /home/lavaslayer/.minecraft/mods/Generatormods-0.1.7(1.7.10).jar
7f21dc009000-7f21dc00c000 r--s 00017000 08:03 3803221                    /home/lavaslayer/.minecraft/mods/EnchantingPlus-1.7.10-3.0.2-d.jar
7f21dc00c000-7f21dc04b000 r--s 0144a000 08:03 3803220                    /home/lavaslayer/.minecraft/mods/DrZharks MoCreatures Mod v6.3.1-modified.zip
7f21dc04b000-7f21dc04e000 r--s 0008a000 08:03 3803219                    /home/lavaslayer/.minecraft/mods/DoomlikeDungeons-1.4.0-MC1.7.2.jar
7f21dc04e000-7f21dc05f000 r--s 00747000 08:03 3803218                    /home/lavaslayer/.minecraft/mods/Decocraft-v1.12b_1.7.10.jar
7f21dc05f000-7f21dc068000 r--s 00047000 08:03 3802570                    /home/lavaslayer/.minecraft/mods/CraftGuide-1.6.8.1.zip
7f21dc068000-7f21dc06a000 r--s 00001000 08:03 3803217                    /home/lavaslayer/.minecraft/mods/ConvenientRecipes-1.7.10-1.3.1.jar
7f21dc06a000-7f21dc06c000 r--s 0000b000 08:03 3803216                    /home/lavaslayer/.minecraft/mods/colorfultools-1.7.10-1.6.jar
7f21dc06c000-7f21dc079000 r--s 00054000 08:03 3803215                    /home/lavaslayer/.minecraft/mods/colorfularmor-1.7.10-2.5.jar
7f21dc079000-7f21dc0b8000 r--s 003a7000 08:03 3803213                    /home/lavaslayer/.minecraft/mods/Chisel2-2.3.5.31.jar
7f21dc0b8000-7f21dc0ba000 r--s 00018000 08:03 3803212                    /home/lavaslayer/.minecraft/mods/ChickenChunks-1.7.10-1.3.4.16-universal.jar
7f21dc0ba000-7f21dc0c5000 r--s 0013d000 08:03 3803211                    /home/lavaslayer/.minecraft/mods/Carpenter's Blocks v3.3.5 - MC 1.7.10.jar
7f21dc0c5000-7f21dc0c9000 r--s 0003d000 08:03 3803209                    /home/lavaslayer/.minecraft/mods/BiblioWoods[BiomesOPlenty][v1.9].jar
7f21dc0c9000-7f21dc0e5000 r--s 00556000 08:03 3803210                    /home/lavaslayer/.minecraft/mods/BiomesOPlenty-1.7.10-2.1.0.1036-universal.jar
7f21dc0e5000-7f21dc0f9000 r--s 00498000 08:03 3803208                    /home/lavaslayer/.minecraft/mods/BiblioCraft[v1.9.2][MC1.7.10].jar
7f21dc0f9000-7f21dc106000 r--s 0009b000 08:03 3803207                    /home/lavaslayer/.minecraft/mods/BetterStorage-1.7.10-0.11.3.123.jar
7f21dc106000-7f21dc108000 r--s 00016000 08:03 3802584                    /home/lavaslayer/.minecraft/mods/1.7.10/Baubles-1.7.10-1.0.1.10.jar
7f21dc108000-7f21dc10d000 r--s 000b6000 08:03 3803205                    /home/lavaslayer/.minecraft/mods/animalsPlus-1.2.jar
7f21dc10d000-7f21dc111000 r--s 0002d000 08:03 3803201                    /home/lavaslayer/.minecraft/mods/[1.7.10]bspkrsCore-universal-6.14.jar
7f21dc111000-7f21dc115000 r--s 0001c000 08:03 3803200                    /home/lavaslayer/.minecraft/mods/[1.7.10]Better_Furnaces_V4.3.jar
7f21dc115000-7f21dc117000 r--s 0000e000 08:03 3803203                    /home/lavaslayer/.minecraft/mods/1.7.2.4 Roxas Tall Doors Mod.jar
7f21dc117000-7f21dc118000 r--s 00000000 08:03 2759543                    /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le64.cache-4
7f21dc118000-7f21dc119000 r--s 00000000 08:03 2759496                    /var/cache/fontconfig/0c9eb80ebd1c36541ebe2852d3bb0c49-le64.cache-4
7f21dc119000-7f21dc11a000 rw-s 00000000 00:04 80443                      /drm mm object (deleted)
7f21dc11a000-7f21dc11b000 rw-s 00000000 00:04 55168                      /drm mm object (deleted)
7f21dc11b000-7f21dc11c000 rw-s 00000000 00:04 55167                      /drm mm object (deleted)
7f21dc11c000-7f21dc11d000 rw-s 00000000 00:04 80442                      /drm mm object (deleted)
7f21dc11d000-7f21dc125000 rw-s 00000000 00:04 51732                      /drm mm object (deleted)
7f21dc125000-7f21dc126000 rw-s 00000000 00:04 78481                      /drm mm object (deleted)
7f21dc126000-7f21dc127000 rw-s 00000000 00:04 80441                      /drm mm object (deleted)
7f21dc127000-7f21dc128000 rw-s 00000000 00:04 33685                      /drm mm object (deleted)
7f21dc128000-7f21dc12f000 r--s 00000000 08:03 6427829                    /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f21dc12f000-7f21dc132000 ---p 00000000 00:00 0 
7f21dc132000-7f21dc168000 rw-p 00000000 00:00 0 
7f21dc168000-7f21dc17b000 r--s 00344000 08:03 1577072                    /usr/lib/jvm/java-8-oracle/jre/lib/resources.jar
7f21dc17b000-7f21dc1ad000 r--s 00bca000 08:03 3803244                    /home/lavaslayer/.minecraft/mods/Thaumcraft-1.7.10-4.2.3.5.jar
7f21dc1ad000-7f21dc1cf000 r--s 000b8000 08:03 3802573                    /home/lavaslayer/.minecraft/mods/OptiFine_1.7.10_HD_U_B5.jar
7f21dc1cf000-7f21dc1d8000 r-xp 00000000 08:03 6167024                    /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f21dc1d8000-7f21dc3d7000 ---p 00009000 08:03 6167024                    /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f21dc3d7000-7f21dc3d8000 r--p 00008000 08:03 6167024                    /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f21dc3d8000-7f21dc3d9000 rw-p 00009000 08:03 6167024                    /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f21dc3d9000-7f21dc3dc000 ---p 00000000 00:00 0 
7f21dc3dc000-7f21dc7da000 rw-p 00000000 00:00 0                          [stack:5381]
7f21dc7da000-7f21dc7f0000 r-xp 00000000 08:03 5242973                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f21dc7f0000-7f21dc9ef000 ---p 00016000 08:03 5242973                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f21dc9ef000-7f21dc9f0000 r--p 00015000 08:03 5242973                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f21dc9f0000-7f21dc9f1000 rw-p 00016000 08:03 5242973                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f21dc9f1000-7f21dca56000 r-xp 00000000 08:03 1577221                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libfontmanager.so
7f21dca56000-7f21dcc55000 ---p 00065000 08:03 1577221                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libfontmanager.so
7f21dcc55000-7f21dcc59000 rw-p 00064000 08:03 1577221                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libfontmanager.so
7f21dcc59000-7f21dcc6a000 rw-p 00000000 00:00 0 
7f21dcc6a000-7f21dcc6f000 r-xp 00000000 08:03 6160561                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f21dcc6f000-7f21dce6e000 ---p 00005000 08:03 6160561                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f21dce6e000-7f21dce6f000 r--p 00004000 08:03 6160561                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f21dce6f000-7f21dce70000 rw-p 00005000 08:03 6160561                    /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f21dce70000-7f21dce72000 r-xp 00000000 08:03 6167017                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f21dce72000-7f21dd072000 ---p 00002000 08:03 6167017                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f21dd072000-7f21dd073000 r--p 00002000 08:03 6167017                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f21dd073000-7f21dd074000 rw-p 00003000 08:03 6167017                    /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f21dd074000-7f21dd091000 r-xp 00000000 08:03 6167971                    /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f21dd091000-7f21dd291000 ---p 0001d000 08:03 6167971                    /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f21dd291000-7f21dd292000 r--p 0001d000 08:03 6167971                    /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f21dd292000-7f21dd293000 rw-p 0001e000 08:03 6167971                    /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f21dd293000-7f21dd2a2000 r-xp 00000000 08:03 6162611                    /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f21dd2a2000-7f21dd4a1000 ---p 0000f000 08:03 6162611                    /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f21dd4a1000-7f21dd4a2000 r--p 0000e000 08:03 6162611                    /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f21dd4a2000-7f21dd4a3000 rw-p 0000f000 08:03 6162611                    /usr/lib/x86_64-linux-gnu/libXi.so.6.1.0
7f21dd4a3000-7f21dd4a8000 r-xp 00000000 08:03 6167058                    /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f21dd4a8000-7f21dd6a7000 ---p 00005000 08:03 6167058                    /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f21dd6a7000-7f21dd6a8000 r--p 00004000 08:03 6167058                    /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f21dd6a8000-7f21dd6a9000 rw-p 00005000 08:03 6167058                    /usr/lib/x86_64-linux-gnu/libXtst.so.6.1.0
7f21dd6a9000-7f21dd6b2000 r-xp 00000000 08:03 6167052                    /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f21dd6b2000-7f21dd8b1000 ---p 00009000 08:03 6167052                    /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f21dd8b1000-7f21dd8b2000 r--p 00008000 08:03 6167052                    /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f21dd8b2000-7f21dd8b3000 rw-p 00009000 08:03 6167052                    /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f21dd8b3000-7f21dd9e6000 r-xp 00000000 08:03 6166217                    /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f21dd9e6000-7f21ddbe6000 ---p 00133000 08:03 6166217                    /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f21ddbe6000-7f21ddbe7000 r--p 00133000 08:03 6166217                    /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f21ddbe7000-7f21ddbeb000 rw-p 00134000 08:03 6166217                    /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f21ddbeb000-7f21ddbec000 rw-p 00000000 00:00 0 
7f21ddbec000-7f21ddbfd000 r-xp 00000000 08:03 6168231                    /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f21ddbfd000-7f21dddfc000 ---p 00011000 08:03 6168231                    /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f21dddfc000-7f21dddfd000 r--p 00010000 08:03 6168231                    /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f21dddfd000-7f21dddfe000 rw-p 00011000 08:03 6168231                    /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f21dddfe000-7f21dddff000 rw-s 00000000 00:04 33680                      /drm mm object (deleted)
7f21dddff000-7f21dde00000 rwxp 00000000 00:00 0 
7f21dde00000-7f21dde01000 rw-s 00000000 00:04 52535                      /drm mm object (deleted)
7f21dde01000-7f21dde02000 rw-s 100c20000 00:05 10498                     /dev/dri/card0
7f21dde02000-7f21dde0a000 r--s 00067000 08:03 3803226                    /home/lavaslayer/.minecraft/mods/malisiscore-1.7.10-0.10.3.jar
7f21dde0a000-7f21dde0d000 r--s 0001a000 08:03 1577255                    /usr/lib/jvm/java-8-oracle/jre/lib/jce.jar
7f21dde0d000-7f21dde0e000 r--s 00013000 08:03 3801271                    /home/lavaslayer/.minecraft/mods/fastcraft-1.19.jar
7f21dde0e000-7f21dde14000 r--s 00044000 08:03 3802585                    /home/lavaslayer/.minecraft/mods/1.7.10/CodeChickenLib-1.7.10-1.1.1.99-universal.jar
7f21dde14000-7f21dde68000 r-xp 00000000 08:03 1577246                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt_xawt.so
7f21dde68000-7f21de068000 ---p 00054000 08:03 1577246                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt_xawt.so
7f21de068000-7f21de06c000 rw-p 00054000 08:03 1577246                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt_xawt.so
7f21de06c000-7f21de06d000 rw-p 00000000 00:00 0 
7f21de06d000-7f21de10f000 r-xp 00000000 08:03 1577232                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt.so
7f21de10f000-7f21de30f000 ---p 000a2000 08:03 1577232                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt.so
7f21de30f000-7f21de31b000 rw-p 000a2000 08:03 1577232                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libawt.so
7f21de31b000-7f21de53f000 rw-p 00000000 00:00 0 
7f21de53f000-7f21ded40000 rw-p 00000000 00:00 0 
7f21ded40000-7f21ded44000 r--s 00023000 08:03 3803214                    /home/lavaslayer/.minecraft/mods/CodeChickenCore-1.7.10-1.0.4.29-universal.jar
7f21ded44000-7f21ded46000 r--s 0001c000 08:03 3803202                    /home/lavaslayer/.minecraft/mods/[1.7.10]Gender-1.0.2.jar
7f21ded46000-7f21ded55000 r--s 000f8000 08:03 3803204                    /home/lavaslayer/.minecraft/mods/1.7.10-MB_Battlegear2-Bullseye-1.0.7.0.jar
7f21ded55000-7f21def55000 rw-p 00000000 00:00 0 
7f21def55000-7f21def5a000 r--s 00094000 08:03 1577086                    /usr/lib/jvm/java-8-oracle/jre/lib/jsse.jar
7f21def5a000-7f21def65000 r--s 00116000 08:03 1577096                    /usr/lib/jvm/java-8-oracle/jre/lib/ext/localedata.jar
7f21def65000-7f21def81000 r--s 00393000 08:03 1577090                    /usr/lib/jvm/java-8-oracle/jre/lib/ext/cldrdata.jar
7f21def81000-7f21def92000 r-xp 00000000 08:03 1577242                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnio.so
7f21def92000-7f21df191000 ---p 00011000 08:03 1577242                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnio.so
7f21df191000-7f21df192000 rw-p 00010000 08:03 1577242                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnio.so
7f21df192000-7f21df1a8000 r-xp 00000000 08:03 1577239                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnet.so
7f21df1a8000-7f21df3a8000 ---p 00016000 08:03 1577239                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnet.so
7f21df3a8000-7f21df3a9000 rw-p 00016000 08:03 1577239                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libnet.so
7f21df3a9000-7f21df3b1000 r-xp 00000000 08:03 1577247                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libmanagement.so
7f21df3b1000-7f21df5b1000 ---p 00008000 08:03 1577247                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libmanagement.so
7f21df5b1000-7f21df5b2000 rw-p 00008000 08:03 1577247                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libmanagement.so
7f21df5b2000-7f21df5e4000 r--s 004d2000 08:03 3802462                    /home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291.jar
7f21df5e4000-7f21df5e6000 r--s 0000b000 08:03 3801498                    /home/lavaslayer/.minecraft/libraries/tv/twitch/twitch/5.16/twitch-5.16.jar
7f21df5e6000-7f21df5ea000 r--s 00027000 08:03 3801443                    /home/lavaslayer/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl_util/2.9.1/lwjgl_util-2.9.1.jar
7f21df5ea000-7f21df5f8000 r--s 000ea000 08:03 3801511                    /home/lavaslayer/.minecraft/libraries/org/lwjgl/lwjgl/lwjgl/2.9.1/lwjgl-2.9.1.jar
7f21df5f8000-7f21df606000 r--s 00099000 08:03 3801442                    /home/lavaslayer/.minecraft/libraries/org/apache/logging/log4j/log4j-core/2.0-beta9/log4j-core-2.0-beta9.jar
7f21df606000-7f21df609000 r--s 00018000 08:03 3801505                    /home/lavaslayer/.minecraft/libraries/org/apache/logging/log4j/log4j-api/2.0-beta9/log4j-api-2.0-beta9.jar
7f21df609000-7f21df60c000 r--s 0000d000 08:03 3801460                    /home/lavaslayer/.minecraft/libraries/com/mojang/authlib/1.5.16/authlib-1.5.16.jar
7f21df60c000-7f21df611000 r--s 0002a000 08:03 3801479                    /home/lavaslayer/.minecraft/libraries/com/google/code/gson/gson/2.2.4/gson-2.2.4.jar
7f21df611000-7f21df612000 r--s 00001000 08:03 3801484                    /home/lavaslayer/.minecraft/libraries/net/java/jutils/jutils/1.0.0/jutils-1.0.0.jar
7f21df612000-7f21df616000 r--s 0002f000 08:03 3801441                    /home/lavaslayer/.minecraft/libraries/net/java/jinput/jinput/2.0.5/jinput-2.0.5.jar
7f21df616000-7f21df61d000 r--s 0003a000 08:03 3801438                    /home/lavaslayer/.minecraft/libraries/commons-codec/commons-codec/1.9/commons-codec-1.9.jar
7f21df61d000-7f21df621000 r--s 0002a000 08:03 3801440                    /home/lavaslayer/.minecraft/libraries/commons-io/commons-io/2.4/commons-io-2.4.jar
7f21df621000-7f21df628000 r--s 00058000 08:03 3802560                    /home/lavaslayer/.minecraft/libraries/org/apache/commons/commons-lang3/3.2.1/commons-lang3-3.2.1.jar
7f21df628000-7f21df653000 r--s 001f5000 08:03 3802567                    /home/lavaslayer/.minecraft/libraries/com/google/guava/guava/16.0/guava-16.0.jar
7f21df653000-7f21df66c000 r--s 0014a000 08:03 3801512                    /home/lavaslayer/.minecraft/libraries/io/netty/netty-all/4.0.10.Final/netty-all-4.0.10.Final.jar
7f21df66c000-7f21df66e000 r--s 00004000 08:03 3801436                    /home/lavaslayer/.minecraft/libraries/com/paulscode/libraryjavasound/20101123/libraryjavasound-20101123.jar
7f21df66e000-7f21df670000 r--s 00018000 08:03 3801483                    /home/lavaslayer/.minecraft/libraries/com/paulscode/codecjorbis/20101023/codecjorbis-20101023.jar
7f21df670000-7f21df686000 r--s 0017a000 08:03 3801495                    /home/lavaslayer/.minecraft/libraries/com/ibm/icu/icu4j-core-mojang/51.2/icu4j-core-mojang-51.2.jar
7f21df686000-7f21df6ae000 r--s 00241000 08:03 3801430                    /home/lavaslayer/.minecraft/libraries/net/sf/trove4j/trove4j/3.0.3/trove4j-3.0.3.jar
7f21df6ae000-7f21df6b4000 r--s 0003f000 08:03 3801439                    /home/lavaslayer/.minecraft/libraries/org/apache/httpcomponents/httpcore/4.3.2/httpcore-4.3.2.jar
7f21df6b4000-7f21df6bf000 r--s 00085000 08:03 3801429                    /home/lavaslayer/.minecraft/libraries/org/apache/httpcomponents/httpclient/4.3.3/httpclient-4.3.3.jar
7f21df6bf000-7f21df70a000 r--s 003eb000 08:03 3802535                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-reflect/2.11.1/scala-reflect-2.11.1.jar
7f21df70a000-7f21df7fa000 r--s 00c03000 08:03 3802519                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-compiler/2.11.1/scala-compiler-2.11.1.jar
7f21df7fa000-7f21df7fb000 ---p 00000000 00:00 0 
7f21df7fb000-7f21df8fb000 rw-p 00000000 00:00 0                          [stack:5380]
7f21df8fb000-7f21df8fe000 ---p 00000000 00:00 0 
7f21df8fe000-7f21dfafc000 rw-p 00000000 00:00 0                          [stack:5379]
7f21dfafc000-7f21dfaff000 ---p 00000000 00:00 0 
7f21dfaff000-7f21dfbfd000 rw-p 00000000 00:00 0                          [stack:5378]
7f21dfbfd000-7f21dfc00000 ---p 00000000 00:00 0 
7f21dfc00000-7f21dfcfe000 rw-p 00000000 00:00 0                          [stack:5377]
7f21dfcfe000-7f21dfd01000 ---p 00000000 00:00 0 
7f21dfd01000-7f21dfdff000 rw-p 00000000 00:00 0                          [stack:5376]
7f21dfdff000-7f21dfe02000 ---p 00000000 00:00 0 
7f21dfe02000-7f21e0000000 rw-p 00000000 00:00 0                          [stack:5374]
7f21e0000000-7f21e0021000 rw-p 00000000 00:00 0 
7f21e0021000-7f21e4000000 ---p 00000000 00:00 0 
7f21e4000000-7f21e4021000 rw-p 00000000 00:00 0 
7f21e4021000-7f21e8000000 ---p 00000000 00:00 0 
7f21e8000000-7f21ec000000 rw-p 00000000 00:00 0 
7f21ec000000-7f21ec021000 rw-p 00000000 00:00 0 
7f21ec021000-7f21f0000000 ---p 00000000 00:00 0 
7f21f0000000-7f21f0021000 rw-p 00000000 00:00 0 
7f21f0021000-7f21f4000000 ---p 00000000 00:00 0 
7f21f4000000-7f21f4021000 rw-p 00000000 00:00 0 
7f21f4021000-7f21f8000000 ---p 00000000 00:00 0 
7f21f8000000-7f21f8021000 rw-p 00000000 00:00 0 
7f21f8021000-7f21fc000000 ---p 00000000 00:00 0 
7f21fc000000-7f21fc021000 rw-p 00000000 00:00 0 
7f21fc021000-7f2200000000 ---p 00000000 00:00 0 
7f2200000000-7f2200021000 rw-p 00000000 00:00 0 
7f2200021000-7f2204000000 ---p 00000000 00:00 0 
7f2204000000-7f2204021000 rw-p 00000000 00:00 0 
7f2204021000-7f2208000000 ---p 00000000 00:00 0 
7f2208000000-7f2208021000 rw-p 00000000 00:00 0 
7f2208021000-7f220c000000 ---p 00000000 00:00 0 
7f220c000000-7f220c001000 r--s 0000f000 08:03 3801431                    /home/lavaslayer/.minecraft/libraries/com/paulscode/soundsystem/20120107/soundsystem-20120107.jar
7f220c001000-7f220c003000 r--s 00045000 08:03 3801432                    /home/lavaslayer/.minecraft/libraries/java3d/vecmath/1.3.1/vecmath-1.3.1.jar
7f220c003000-7f220c00a000 r--s 00053000 08:03 3801434                    /home/lavaslayer/.minecraft/libraries/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar
7f220c00a000-7f220c014000 r--s 00098000 08:03 3802541                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-xml_2.11/1.0.2/scala-xml_2.11-1.0.2.jar
7f220c014000-7f220c06d000 r--s 00502000 08:03 3802529                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-library/2.11.1/scala-library-2.11.1.jar
7f220c06d000-7f220c08e000 rw-p 00000000 00:00 0 
7f220c08e000-7f220c0b3000 r--s 0024b000 08:03 3802493                    /home/lavaslayer/.minecraft/libraries/com/typesafe/akka/akka-actor_2.11/2.3.3/akka-actor_2.11-2.3.3.jar
7f220c0b3000-7f220c0b6000 ---p 00000000 00:00 0 
7f220c0b6000-7f220c1b4000 rw-p 00000000 00:00 0                          [stack:5375]
7f220c1b4000-7f220cb86000 r--p 00000000 08:03 6165230                    /usr/lib/locale/locale-archive
7f220cb86000-7f220cb89000 ---p 00000000 00:00 0 
7f220cb89000-7f220cd87000 rw-p 00000000 00:00 0                          [stack:5373]
7f220cd87000-7f220cd8a000 ---p 00000000 00:00 0 
7f220cd8a000-7f220cf88000 rw-p 00000000 00:00 0                          [stack:5372]
7f220cf88000-7f220cf89000 ---p 00000000 00:00 0 
7f220cf89000-7f220ec28000 rw-p 00000000 00:00 0                          [stack:5371]
7f220ec28000-7f220ee00000 r--s 03d09000 08:03 1577036                    /usr/lib/jvm/java-8-oracle/jre/lib/rt.jar
7f220ee00000-7f220fa00000 rw-p 00000000 00:00 0 
7f220fa00000-7f220fa02000 r--s 0000e000 08:03 3801433                    /home/lavaslayer/.minecraft/libraries/commons-logging/commons-logging/1.1.3/commons-logging-1.1.3.jar
7f220fa02000-7f220fa07000 r--s 00052000 08:03 3801435                    /home/lavaslayer/.minecraft/libraries/com/mojang/realms/1.3.5/realms-1.3.5.jar
7f220fa07000-7f220fa1e000 r--s 0028f000 08:03 3802545                    /home/lavaslayer/.minecraft/libraries/net/minecraftforge/forge/1.7.10-10.13.2.1291/forge-1.7.10-10.13.2.1291.jar
7f220fa1e000-7f220fb67000 rw-p 00000000 00:00 0 
7f220fb67000-7f220fb68000 ---p 00000000 00:00 0 
7f220fb68000-7f220fc68000 rw-p 00000000 00:00 0                          [stack:5370]
7f220fc68000-7f220fc69000 ---p 00000000 00:00 0 
7f220fc69000-7f220fd69000 rw-p 00000000 00:00 0                          [stack:5369]
7f220fd69000-7f220fd6a000 ---p 00000000 00:00 0 
7f220fd6a000-7f220fe6a000 rw-p 00000000 00:00 0                          [stack:5368]
7f220fe6a000-7f220fe6b000 ---p 00000000 00:00 0 
7f220fe6b000-7f220ff6b000 rw-p 00000000 00:00 0                          [stack:5367]
7f220ff6b000-7f220ff6c000 ---p 00000000 00:00 0 
7f220ff6c000-7f221006c000 rw-p 00000000 00:00 0                          [stack:5366]
7f221006c000-7f221006d000 ---p 00000000 00:00 0 
7f221006d000-7f22102e2000 rw-p 00000000 00:00 0                          [stack:5365]
7f22102e2000-7f2210418000 ---p 00000000 00:00 0 
7f2210418000-7f221058d000 rw-p 00000000 00:00 0 
7f221058d000-7f22106c3000 ---p 00000000 00:00 0 
7f22106c3000-7f221076d000 rw-p 00000000 00:00 0 
7f221076d000-7f2210818000 ---p 00000000 00:00 0 
7f2210818000-7f22108e8000 rw-p 00000000 00:00 0 
7f22108e8000-7f2210bd9000 ---p 00000000 00:00 0 
7f2210bd9000-7f2214000000 rwxp 00000000 00:00 0 
7f2214000000-7f221fbd9000 ---p 00000000 00:00 0 
7f221fbd9000-7f221fbf3000 r-xp 00000000 08:03 1577235                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libzip.so
7f221fbf3000-7f221fdf3000 ---p 0001a000 08:03 1577235                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libzip.so
7f221fdf3000-7f221fdf4000 rw-p 0001a000 08:03 1577235                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libzip.so
7f221fdf4000-7f221fdff000 r-xp 00000000 08:03 5244103                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f221fdff000-7f221fffe000 ---p 0000b000 08:03 5244103                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f221fffe000-7f221ffff000 r--p 0000a000 08:03 5244103                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f221ffff000-7f2220000000 rw-p 0000b000 08:03 5244103                    /lib/x86_64-linux-gnu/libnss_files-2.19.so
7f2220000000-7f2224000000 rw-p 00000000 00:00 0 
7f2224000000-7f2224001000 r--s 00004000 08:03 3801437                    /home/lavaslayer/.minecraft/libraries/com/paulscode/librarylwjglopenal/20100824/librarylwjglopenal-20100824.jar
7f2224001000-7f2224003000 r--s 0000d000 08:03 3801497                    /home/lavaslayer/.minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar
7f2224003000-7f222400e000 r--s 000a9000 08:03 3802538                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-swing_2.11/1.0.1/scala-swing_2.11-1.0.1.jar
7f222400e000-7f222400f000 ---p 00000000 00:00 0 
7f222400f000-7f222410f000 rw-p 00000000 00:00 0                          [stack:5364]
7f222410f000-7f222411a000 r-xp 00000000 08:03 5244105                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
7f222411a000-7f2224319000 ---p 0000b000 08:03 5244105                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
7f2224319000-7f222431a000 r--p 0000a000 08:03 5244105                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
7f222431a000-7f222431b000 rw-p 0000b000 08:03 5244105                    /lib/x86_64-linux-gnu/libnss_nis-2.19.so
7f222431b000-7f2224332000 r-xp 00000000 08:03 5244089                    /lib/x86_64-linux-gnu/libnsl-2.19.so
7f2224332000-7f2224531000 ---p 00017000 08:03 5244089                    /lib/x86_64-linux-gnu/libnsl-2.19.so
7f2224531000-7f2224532000 r--p 00016000 08:03 5244089                    /lib/x86_64-linux-gnu/libnsl-2.19.so
7f2224532000-7f2224533000 rw-p 00017000 08:03 5244089                    /lib/x86_64-linux-gnu/libnsl-2.19.so
7f2224533000-7f2224535000 rw-p 00000000 00:00 0 
7f2224535000-7f222453e000 r-xp 00000000 08:03 5244090                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
7f222453e000-7f222473d000 ---p 00009000 08:03 5244090                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
7f222473d000-7f222473e000 r--p 00008000 08:03 5244090                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
7f222473e000-7f222473f000 rw-p 00009000 08:03 5244090                    /lib/x86_64-linux-gnu/libnss_compat-2.19.so
7f222473f000-7f2224769000 r-xp 00000000 08:03 1577230                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjava.so
7f2224769000-7f2224969000 ---p 0002a000 08:03 1577230                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjava.so
7f2224969000-7f222496b000 rw-p 0002a000 08:03 1577230                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libjava.so
7f222496b000-7f2224978000 r-xp 00000000 08:03 1577234                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libverify.so
7f2224978000-7f2224b78000 ---p 0000d000 08:03 1577234                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libverify.so
7f2224b78000-7f2224b7a000 rw-p 0000d000 08:03 1577234                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/libverify.so
7f2224b7a000-7f2224b81000 r-xp 00000000 08:03 5244106                    /lib/x86_64-linux-gnu/librt-2.19.so
7f2224b81000-7f2224d80000 ---p 00007000 08:03 5244106                    /lib/x86_64-linux-gnu/librt-2.19.so
7f2224d80000-7f2224d81000 r--p 00006000 08:03 5244106                    /lib/x86_64-linux-gnu/librt-2.19.so
7f2224d81000-7f2224d82000 rw-p 00007000 08:03 5244106                    /lib/x86_64-linux-gnu/librt-2.19.so
7f2224d82000-7f2224d85000 ---p 00000000 00:00 0 
7f2224d85000-7f2224f83000 rw-p 00000000 00:00 0                          [stack:5360]
7f2224f83000-7f2225088000 r-xp 00000000 08:03 5244085                    /lib/x86_64-linux-gnu/libm-2.19.so
7f2225088000-7f2225287000 ---p 00105000 08:03 5244085                    /lib/x86_64-linux-gnu/libm-2.19.so
7f2225287000-7f2225288000 r--p 00104000 08:03 5244085                    /lib/x86_64-linux-gnu/libm-2.19.so
7f2225288000-7f2225289000 rw-p 00105000 08:03 5244085                    /lib/x86_64-linux-gnu/libm-2.19.so
7f2225289000-7f2225f37000 r-xp 00000000 08:03 1577213                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/server/libjvm.so
7f2225f37000-7f2226136000 ---p 00cae000 08:03 1577213                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/server/libjvm.so
7f2226136000-7f222620d000 rw-p 00cad000 08:03 1577213                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/server/libjvm.so
7f222620d000-7f2226251000 rw-p 00000000 00:00 0 
7f2226251000-7f222640b000 r-xp 00000000 08:03 5244104                    /lib/x86_64-linux-gnu/libc-2.19.so
7f222640b000-7f222660a000 ---p 001ba000 08:03 5244104                    /lib/x86_64-linux-gnu/libc-2.19.so
7f222660a000-7f222660e000 r--p 001b9000 08:03 5244104                    /lib/x86_64-linux-gnu/libc-2.19.so
7f222660e000-7f2226610000 rw-p 001bd000 08:03 5244104                    /lib/x86_64-linux-gnu/libc-2.19.so
7f2226610000-7f2226615000 rw-p 00000000 00:00 0 
7f2226615000-7f2226618000 r-xp 00000000 08:03 5244092                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f2226618000-7f2226817000 ---p 00003000 08:03 5244092                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f2226817000-7f2226818000 r--p 00002000 08:03 5244092                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f2226818000-7f2226819000 rw-p 00003000 08:03 5244092                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f2226819000-7f222682e000 r-xp 00000000 08:03 1577208                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/jli/libjli.so
7f222682e000-7f2226a2e000 ---p 00015000 08:03 1577208                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/jli/libjli.so
7f2226a2e000-7f2226a2f000 rw-p 00015000 08:03 1577208                    /usr/lib/jvm/java-8-oracle/jre/lib/amd64/jli/libjli.so
7f2226a2f000-7f2226a48000 r-xp 00000000 08:03 5244093                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f2226a48000-7f2226c47000 ---p 00019000 08:03 5244093                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f2226c47000-7f2226c48000 r--p 00018000 08:03 5244093                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f2226c48000-7f2226c49000 rw-p 00019000 08:03 5244093                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f2226c49000-7f2226c4d000 rw-p 00000000 00:00 0 
7f2226c4d000-7f2226c70000 r-xp 00000000 08:03 5244099                    /lib/x86_64-linux-gnu/ld-2.19.so
7f2226c70000-7f2226c71000 r--s 00001000 08:03 3801490                    /home/lavaslayer/.minecraft/libraries/com/paulscode/codecwav/20101023/codecwav-20101023.jar
7f2226c71000-7f2226c7c000 r--s 0005f000 08:03 3802532                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-parser-combinators_2.11/1.0.1/scala-parser-combinators_2.11-1.0.1.jar
7f2226c7c000-7f2226c82000 r--s 0002e000 08:03 3802526                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/plugins/scala-continuations-plugin_2.11.1/1.0.2/scala-continuations-plugin_2.11.1-1.0.2.jar
7f2226c82000-7f2226c84000 r--s 00005000 08:03 3802523                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/plugins/scala-continuations-library_2.11/1.0.2/scala-continuations-library_2.11-1.0.2.jar
7f2226c84000-7f2226c86000 r--s 0000d000 08:03 3802513                    /home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-actors-migration_2.11/1.1.0/scala-actors-migration_2.11-1.1.0.jar
7f2226c86000-7f2226d52000 rw-p 00000000 00:00 0 
7f2226d52000-7f2226d53000 ---p 00000000 00:00 0 
7f2226d53000-7f2226e57000 rw-p 00000000 00:00 0                          [stack:5363]
7f2226e57000-7f2226e58000 r--s 00001000 08:03 3802561                    /home/lavaslayer/.minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar
7f2226e58000-7f2226e5c000 r--s 00032000 08:03 3802507                    /home/lavaslayer/.minecraft/libraries/com/typesafe/config/1.2.1/config-1.2.1.jar
7f2226e5c000-7f2226e61000 r--s 00036000 08:03 3802558                    /home/lavaslayer/.minecraft/libraries/org/ow2/asm/asm-all/5.0.3/asm-all-5.0.3.jar
7f2226e61000-7f2226e63000 r--s 00007000 08:03 3802569                    /home/lavaslayer/.minecraft/libraries/net/minecraft/launchwrapper/1.11/launchwrapper-1.11.jar
7f2226e63000-7f2226e6b000 rw-s 00000000 08:03 546932                     /tmp/hsperfdata_lavaslayer/5359
7f2226e6b000-7f2226e6c000 rw-p 00000000 00:00 0 
7f2226e6c000-7f2226e6d000 r--p 00000000 00:00 0 
7f2226e6d000-7f2226e6f000 rw-p 00000000 00:00 0 
7f2226e6f000-7f2226e70000 r--p 00022000 08:03 5244099                    /lib/x86_64-linux-gnu/ld-2.19.so
7f2226e70000-7f2226e71000 rw-p 00023000 08:03 5244099                    /lib/x86_64-linux-gnu/ld-2.19.so
7f2226e71000-7f2226e72000 rw-p 00000000 00:00 0 
7ffd4ffca000-7ffd4ffec000 rw-p 00000000 00:00 0                          [stack]
7ffd4fffc000-7ffd4fffe000 r-xp 00000000 00:00 0                          [vdso]
7ffd4fffe000-7ffd50000000 r--p 00000000 00:00 0                          [vvar]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
jvm_args: -Xms1G -Xmx2G -Xnoclassgc -XX:+UnlockExperimentalVMOptions -XX:+UseLargePages -Xss2M -Djava.library.path=/home/lavaslayer/.minecraft/versions/1.7.10-Forge10.13.2.1291/1.7.10-Forge10.13.2.1291-natives-16865327799309 
java_command: net.minecraft.launchwrapper.Launch --username chellrose --version 1.7.10-Forge10.13.2.1291 --gameDir /home/lavaslayer/.minecraft --assetsDir /home/lavaslayer/.minecraft/assets --assetIndex 1.7.10 --uuid 40ddbe3097ee4f8381ce1926e0d21cf2 --accessToken 0173e7c76eb84bd8a5fe0d14e867c802 --userProperties {} --userType legacy --tweakClass cpw.mods.fml.common.launcher.FMLTweaker
java_class_path (initial): /home/lavaslayer/.minecraft/libraries/net/minecraftforge/forge/1.7.10-10.13.2.1291/forge-1.7.10-10.13.2.1291.jar:/home/lavaslayer/.minecraft/libraries/net/minecraft/launchwrapper/1.11/launchwrapper-1.11.jar:/home/lavaslayer/.minecraft/libraries/org/ow2/asm/asm-all/5.0.3/asm-all-5.0.3.jar:/home/lavaslayer/.minecraft/libraries/com/typesafe/akka/akka-actor_2.11/2.3.3/akka-actor_2.11-2.3.3.jar:/home/lavaslayer/.minecraft/libraries/com/typesafe/config/1.2.1/config-1.2.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-actors-migration_2.11/1.1.0/scala-actors-migration_2.11-1.1.0.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-compiler/2.11.1/scala-compiler-2.11.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/plugins/scala-continuations-library_2.11/1.0.2/scala-continuations-library_2.11-1.0.2.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/plugins/scala-continuations-plugin_2.11.1/1.0.2/scala-continuations-plugin_2.11.1-1.0.2.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-library/2.11.1/scala-library-2.11.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-parser-combinators_2.11/1.0.1/scala-parser-combinators_2.11-1.0.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-reflect/2.11.1/scala-reflect-2.11.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-swing_2.11/1.0.1/scala-swing_2.11-1.0.1.jar:/home/lavaslayer/.minecraft/libraries/org/scala-lang/scala-xml_2.11/1.0.2/scala-xml_2.11-1.0.2.jar:/home/lavaslayer/.minecraft/libraries/net/sf/jopt-simple/jopt-simple/4.5/jopt-simple-4.5.jar:/home/lavaslayer/.minecraft/libraries/lzma/lzma/0.0.1/lzma-0.0.1.jar:/home/lavaslayer/.minecraft/libraries/com/mojang/realms/1.3.5/realms-1.3.5.jar:/home/lavaslayer/.minecraft/libraries/org/apache/commons/commons-compress/1.8.1/commons-compress-1.8.1.jar:/home/lavaslayer/.minecraft/libraries/org/apache/httpcomponents/httpclient/4.3.3/httpclient-4.3.3.jar:/home/lavaslayer/.minecraft/libraries/commons-logging/commons-logging/1.1.3/commons-
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0xaad2e0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGBUS: [libjvm.so+0xaad2e0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGFPE: [libjvm.so+0x90b550], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGPIPE: [libjvm.so+0x90b550], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGXFSZ: [libjvm.so+0x90b550], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGILL: [libjvm.so+0x90b550], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGUSR1: SIG_DFL, sa_mask[0]=00000000000000000000000000000000, sa_flags=none
SIGUSR2: [libjvm.so+0x90cb90], sa_mask[0]=00100000000000000000000000000000, sa_flags=SA_RESTART|SA_SIGINFO
SIGHUP: [libjvm.so+0x90dee0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGINT: [libjvm.so+0x90dee0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGTERM: [libjvm.so+0x90dee0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO
SIGQUIT: [libjvm.so+0x90dee0], sa_mask[0]=11111111011111111101111111111110, sa_flags=SA_RESTART|SA_SIGINFO


---------------  S Y S T E M  ---------------

OS:DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"

uname:Linux 3.16.0-34-generic #45-Ubuntu SMP Mon Mar 23 17:21:27 UTC 2015 x86_64
libc:glibc 2.19 NPTL 2.19 
rlimit: STACK 8192k, CORE 0k, NPROC 30638, NOFILE 4096, AS infinity
load average:1.82 3.32 2.94

/proc/meminfo:
MemTotal:        7865776 kB
MemFree:          816960 kB
MemAvailable:    2196148 kB
Buffers:          425260 kB
Cached:          2362992 kB
SwapCached:            0 kB
Active:          4816548 kB
Inactive:        1867136 kB
Active(anon):    3897112 kB
Inactive(anon):  1301348 kB
Active(file):     919436 kB
Inactive(file):   565788 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:       6008828 kB
SwapFree:        6008828 kB
Dirty:              5892 kB
Writeback:             0 kB
AnonPages:       3895976 kB
Mapped:          1226772 kB
Shmem:           1302724 kB
Slab:             241312 kB
SReclaimable:     125812 kB
SUnreclaim:       115500 kB
KernelStack:        7040 kB
PageTables:        33168 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9941716 kB
Committed_AS:    7775260 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      357024 kB
VmallocChunk:   34359367180 kB
HardwareCorrupted:     0 kB
AnonHugePages:   3061760 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       74904 kB
DirectMap2M:     2756608 kB
DirectMap1G:     5242880 kB


CPU:total 8 (4 cores per cpu, 2 threads per core) family 6 model 60 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, ssse3, sse4.1, sse4.2, popcnt, avx, avx2, aes, clmul, erms, rtm, lzcnt, ht, tsc, tscinvbit, bmi1, bmi2

/proc/cpuinfo:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4232.031
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 4
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 0
cpu cores    : 4
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 5
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 1
cpu cores    : 4
apicid        : 3
initial apicid    : 3
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 6
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 2
cpu cores    : 4
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:

processor    : 7
vendor_id    : GenuineIntel
cpu family    : 6
model        : 60
model name    : Intel(R) Core(TM) i7-4790K CPU @ 4.00GHz
stepping    : 3
microcode    : 0x19
cpu MHz        : 4200.000
cache size    : 8192 KB
physical id    : 0
siblings    : 8
core id        : 3
cpu cores    : 4
apicid        : 7
initial apicid    : 7
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips    : 7981.52
clflush size    : 64
cache_alignment    : 64
address sizes    : 39 bits physical, 48 bits virtual
power management:



Memory: 4k page, physical 7865776k(816960k free), swap 6008828k(6008828k free)

vm_info: Java HotSpot(TM) 64-Bit Server VM (25.40-b25) for linux-amd64 JRE (1.8.0_40-b25), built on Feb 10 2015 21:29:53 by "java_re" with gcc 4.3.0 20080428 (Red Hat 4.3.0-8)

time: Sat Mar 28 20:35:54 2015
elapsed time: 2007 seconds (0d 0h 33m 27s)


```

---

### Post by chellrose on 2015-04-04
bump

---

### Post by Aacron on 2015-04-05
I'm also experiencing the same issue. It also occurs with the same hardware in windows. at first I thought it was possible I had bad memory but I ran memtest86 for 2 days and it came up clean. I also know a few other people that are experiencing the same issue and are on both linux and windows machines, so I think there is something wrong with java itself, or a common factor which might be drivers. I'd love to hear a fix for it though, as it's getting quite annoying.

---

