---
title: "Ubuntu strange problems and error with NVDIA gtx650ti"
date: 2015-01-11
forum: General Help
---

### Post by kkkk2 on 2015-01-11
I have gtx650ti graphic card. 

I had trouble with windows and ubuntu. I had to unplug my usb devices in order to install the ubuntu and than I had to unplug the usb devices when i boot in to the login screen. After that I plugged them back in but after 20-30mins the computer crashed and I had to restart. So I tired this solution "
I looked for the latest NVIDIA driver in the Ubuntu repositories, named nvidia-xyz, where xyz is the largest number you can find there and installed it. For example:
 [TABLE]
[TR]
[TD="class: gutter"]1
2
[/TD]
[TD="class: code"]$ sudo apt-get update
$ sudo apt install nvidia-331"


[/TD]
[/TR]
[/TABLE]

So far it seems this solution works It didnt crash since. But now I have different problems. I only have 2 games on this computer right now. Counter strike global offensive and witcher 2. Both worked before I did the step above (well they worked but they crashed all the time a long with the computer) and now they dont work properly. I can run cs;go but there are strange anomalies for example cant download files from servers. 

and for witcher 2 when I run witcher 2 I just get straight error box;
 Crash reason:  SIGSEGV
Crash address: 0x3b377265


Here is all of the error box if u want;


Output of command: ''/home/kkk/.local/share/Steam/steamapps/common/the witcher 2/crash_reporting/minidump_stackwalk' '/home/kkk/.local/share/cdprojektred/witcher2//3df18240-27f5-cabc-1a3552e8-2ea96486.dmp' '/home/kkk/.local/share/Steam/steamapps/common/the witcher 2/crash_reporting/symbols/''
===============================================================================================
Operating system: Linux
                  0.0.0 Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64
CPU: x86
     AuthenticAMD family 21 model 2 stepping 0
     1 CPU

Crash reason:  SIGSEGV
Crash address: 0x3b377265

Thread 14 (crashed)
 0  libc-2.19.so + 0x47f5f
    eip = 0xf706ff5f   esp = 0xe8dfec20   ebp = 0xe8dff138   ebx = 0xf71d3000
    esi = 0x4a21e8b8   edi = 0x3b377265   eax = 0x00000000   ecx = 0xffffffff
    edx = 0x00000053   efl = 0x00210246
    Found by: given as instruction pointer in context
 1  witcher2!eON_Logging::logMessageVA(int, char const*, char*) [Logging.cpp : 260 + 0x23]
    eip = 0x480495d2   esp = 0xe8dff140   ebp = 0x3b377265
    Found by: previous frame's frame pointer
 2  witcher2!eON_Log [Logging.cpp : 308 + 0x18]
    eip = 0x480497af   esp = 0xe8dff1c0   ebp = 0x3b377265   ebx = 0xe93366c0
    esi = 0x206e690a   edi = 0x00001d28
    Found by: call frame info
 3  witcher2!ShaderCache::VetCompiledShaderForIndex(unsigned int) [shadercache.cpp : 196 + 0x18]
    eip = 0x48100fb8   esp = 0xe8dff1e0   ebp = 0x3b377265   ebx = 0xe93366c0
    esi = 0x206e690a   edi = 0x00001d28
    Found by: call frame info
 4  witcher2!ShaderCache::PrecompileNextShaderOrProgramInTable(OpenGLContextCache*) [shadercache.cpp : 228 + 0xc]
    eip = 0x48107555   esp = 0xe8dff230   ebp = 0x00001d28   ebx = 0xe93366c0
    esi = 0xe9064578   edi = 0x0000026e
    Found by: call frame info
 5  witcher2!Direct3DDevice9Imp::OpenGLThreadRunloop() [direct3ddevice9imp.cpp : 933 + 0x12]
    eip = 0x480b998a   esp = 0xe8dff280   ebp = 0x00000000   ebx = 0xf09e4808
    esi = 0x00000000   edi = 0x00000000
    Found by: call frame info
 6  witcher2!OpenGLThreadFunction(void*) [direct3ddevice9imp.cpp : 914 + 0xf]
    eip = 0x480b9a1b   esp = 0xe8dff2c0   ebp = 0xe8dff3e8   ebx = 0xe9336658
    esi = 0xe8dffb40   edi = 0xe8dff2fe
    Found by: call frame info
 7  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xe8dff2e0   ebp = 0xe8dff3e8   ebx = 0xe9336658
    esi = 0xe8dffb40   edi = 0xe8dff2fe
    Found by: call frame info
 8  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xe8dff320   ebp = 0xe8dff3e8   ebx = 0xf71f1000
    esi = 0xe8dffb40   edi = 0x003d0f00
    Found by: call frame info
 9  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xe8dff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 0
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xffc97c10   ebp = 0xffc97c30   ebx = 0xffc97c38
    esi = 0xf74ef6ec   edi = 0xffc97c38   eax = 0xfffffdfc   ecx = 0xffc97c30
    edx = 0xf7614b74   efl = 0x00200293
    Found by: given as instruction pointer in context
 1  0x7f330d
    eip = 0x007f330d   esp = 0xffc97c38   ebp = 0x00000000
    Found by: previous frame's frame pointer
 2  libSDL2-2.0.so.0 + 0xfcb74
    eip = 0xf7614b74   esp = 0xffc97c50   ebp = 0x00000000
    Found by: stack scanning
 3  libSDL2-2.0.so.0 + 0x4140e
    eip = 0xf755940e   esp = 0xffc97c60   ebp = 0x00000000
    Found by: stack scanning
 4  witcher2!eON_Timers::msSinceProcessStart() [timers.cpp : 54 + 0x5]
    eip = 0x48042a57   esp = 0xffc97c80   ebp = 0xffc97df8
    Found by: stack scanning
 5  witcher2!eON_Core::runLoop() [runLoop.cpp : 687 + 0x13]
    eip = 0x48042913   esp = 0xffc97cc0   ebp = 0xffc97df8   ebx = 0xffc97cd8
    esi = 0xffc97cd8
    Found by: call frame info
 6  witcher2!main [main.cpp : 132 + 0x5]
    eip = 0x48033cd5   esp = 0xffc97d30   ebp = 0xffc97df8   ebx = 0xffc97dcc
    esi = 0xffc97d60   edi = 0xffc97dc8
    Found by: call frame info
 7  libc-2.19.so + 0x19a83
    eip = 0xf7041a83   esp = 0xffc97e00   ebp = 0x00000000
    Found by: previous frame's frame pointer
 8  libc-2.19.so + 0x19a83
    eip = 0xf7041a83   esp = 0xffc97e10   ebp = 0x00000000
    Found by: stack scanning
 9  ld-2.19.so + 0xecea
    eip = 0xf7786cea   esp = 0xffc97e20   ebp = 0xffc97eac
    Found by: stack scanning
10  0xffc99e84
    eip = 0xffc99e84   esp = 0xffc97eb4   ebp = 0xffc99e7b
    Found by: previous frame's frame pointer
11  0x6b6b6b3d
    eip = 0x6b6b6b3d   esp = 0xffc99e83   ebp = 0x52455355
    Found by: previous frame's frame pointer

Thread 1
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xf1c1f250   ebp = 0x00000080   ebx = 0x483ebf04
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200202
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xf1c1f258   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!TimerThreadFunction [synchronisationPrimitives.cpp : 347 + 0x14]
    eip = 0x48155f14   esp = 0xf1c1f280   ebp = 0xf1c1f3e8
    Found by: stack scanning
 3  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xf1c1f2e0   ebp = 0xf1c1f3e8   ebx = 0x4a2d1368
    esi = 0xf1c1fb40   edi = 0xf1c1f2fe
    Found by: call frame info
 4  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xf1c1f320   ebp = 0xf1c1f3e8   ebx = 0xf71f1000
    esi = 0xf1c1fb40   edi = 0x003d0f00
    Found by: call frame info
 5  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xf1c1f3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 2
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xf1b1e270   ebp = 0x00000080   ebx = 0x483ebf44
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200206
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xf1b1e278   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!OverlappedIOThreadFunction [synchronisationPrimitives.cpp : 600 + 0x14]
    eip = 0x48155bc4   esp = 0xf1b1e2a0   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xf1b1e2e0   ebp = 0xf1b1e3e8   ebx = 0x4a2d1588
    esi = 0xf1b1eb40   edi = 0xf1b1e2fe
    Found by: call frame info
 4  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xf1b1e320   ebp = 0xf1b1e3e8   ebx = 0xf71f1000
    esi = 0xf1b1eb40   edi = 0x003d0f00
    Found by: call frame info
 5  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xf1b1e3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 3
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xf0f0d028   ebp = 0x00000080   ebx = 0x482fd2d8
    esi = 0x00000000   edi = 0x00000000   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000002   efl = 0x00200202
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xd9e2
    eip = 0xf71e59e2   esp = 0xf0f0d030   ebp = 0x00000080
    Found by: stack scanning
 2  libpthread-2.19.so + 0x19000
    eip = 0xf71f1000   esp = 0xf0f0d038   ebp = 0x00000080
    Found by: stack scanning
 3  libpthread-2.19.so + 0x9267
    eip = 0xf71e1267   esp = 0xf0f0d040   ebp = 0x00000080
    Found by: stack scanning
 4  libc-2.19.so + 0x4d263
    eip = 0xf7075263   esp = 0xf0f0d050   ebp = 0x00000080
    Found by: stack scanning
 5  witcher2!eON_Logging::logMessageVA(int, char const*, char*) [Logging.cpp : 254 + 0xc]
    eip = 0x4804959e   esp = 0xf0f0d070   ebp = 0x00000080
    Found by: stack scanning
 6  witcher2!eON_Log [Logging.cpp : 308 + 0x18]
    eip = 0x480497af   esp = 0xf0f0d0f0   ebp = 0x00000080   ebx = 0xf096c274
    esi = 0xf096c270   edi = 0x00000360
    Found by: call frame info
 7  witcher2!Direct3DSurface9Imp::InitializeCommonVariables() [direct3dsurface9imp.cpp : 288 + 0x18]
    eip = 0x480c73a4   esp = 0xf0f0d110   ebp = 0x00000080   ebx = 0xf096c274
    esi = 0xf096c270   edi = 0x00000360
    Found by: call frame info
 8  witcher2!Direct3DTexture9Imp::Initialize(IDirect3DDevice9*, unsigned int, unsigned int, unsigned int, unsigned int, _D3DFORMAT, _D3DPOOL) [direct3dtexture9imp.cpp : 80 + 0x53]
    eip = 0x480ca3cc   esp = 0xf0f0d140   ebp = 0x00000080   ebx = 0xf09ff694
    esi = 0xf096c270   edi = 0x00000360
    Found by: call frame info
 9  witcher2!Direct3DDevice9Imp::CreateScreenBuffers() [direct3dtexture9imp.h : 69 + 0x3c]
    eip = 0x4809d546   esp = 0xf0f0d1b0   ebp = 0xf09839b0   ebx = 0xf09ff690
    esi = 0xf09e4808   edi = 0xf09ff694
    Found by: call frame info
10  witcher2!Direct3DDevice9Imp::Initialize(OpenGLDisplay*, void*, _D3DPRESENT_PARAMETERS*, IDirect3D9*, unsigned int, unsigned int) [direct3ddevice9imp.cpp : 1139 + 0x8]
    eip = 0x480b81c9   esp = 0xf0f0d1e0   ebp = 0xf09839b0   ebx = 0x00000001
    esi = 0xf09e4808   edi = 0xf0f0d308
    Found by: call frame info
11  witcher2!Direct3D9Imp::CreateDevice(unsigned int, _D3DDEVTYPE, void*, unsigned int, _D3DPRESENT_PARAMETERS*, IDirect3DDevice9**) [direct3d9imp.cpp : 583 + 0x33]
    eip = 0x4808551b   esp = 0xf0f0d250   ebp = 0xf09839b0   ebx = 0xf0989024
    esi = 0x00000000   edi = 0xf09e47f8
    Found by: call frame info
12  witcher2!Direct3D9::CreateDevice(unsigned int, _D3DDEVTYPE, void*, unsigned int, _D3DPRESENT_PARAMETERS*, IDirect3DDevice9**) [direct3d9imp.h : 93 + 0x38]
    eip = 0x4806e251   esp = 0xf0f0d2b0   ebp = 0xf0f0d2d4   ebx = 0x00000001
    esi = 0xf0f0d378   edi = 0xf0f0d340
    Found by: call frame info
13  0x52d5d0
    eip = 0x0052d5d0   esp = 0xf0f0d2dc   ebp = 0xf0f0dd7c   ebx = 0x00000001
    esi = 0xf0f0d378   edi = 0xf0f0d340
    Found by: call frame info
14  0x99d64c
    eip = 0x0099d64c   esp = 0xf0f0dd84   ebp = 0xf0f0de28
    Found by: previous frame's frame pointer
15  0x9a064a
    eip = 0x009a064a   esp = 0xf0f0de30   ebp = 0xf0f0de58
    Found by: previous frame's frame pointer
16  0xa82d61
    eip = 0x00a82d61   esp = 0xf0f0de60   ebp = 0xf0f0dfb8
    Found by: previous frame's frame pointer
17  0xa82097
    eip = 0x00a82097   esp = 0xf0f0dfc0   ebp = 0xf0f0e22c
    Found by: previous frame's frame pointer
18  0x66faaa
    eip = 0x0066faaa   esp = 0xf0f0e234   ebp = 0xf0f0e2bc
    Found by: previous frame's frame pointer
19  0xf0f0eb40
    eip = 0xf0f0eb40   esp = 0xf0f0e2c4   ebp = 0xf0f0e3e8
    Found by: previous frame's frame pointer
20  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xf0f0e3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 4
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xef01f064   ebp = 0x00000189   ebx = 0xeea034d4
    esi = 0xef01f1f4   edi = 0x483ebed0   eax = 0xfffffdfc   ecx = 0x00000189
    edx = 0x000010bf   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xb12d
    eip = 0xf71e312d   esp = 0xef01f06c   ebp = 0x00000189
    Found by: stack scanning
 2  libpthread-2.19.so + 0xb03b
    eip = 0xf71e303b   esp = 0xef01f08c   ebp = 0x00000189
    Found by: stack scanning
 3  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1260 + 0x1b]
    eip = 0x48158df7   esp = 0xef01f0a0   ebp = 0x00000189
    Found by: stack scanning
 4  witcher2!eON_Sleep [winthreads.cpp : 1976 + 0x33]
    eip = 0x4816890c   esp = 0xef01f230   ebp = 0xef01f254   ebx = 0x0a6d2cd0
    esi = 0x02568d70   edi = 0x00000000
    Found by: call frame info
 5  0xa6e29f
    eip = 0x00a6e29f   esp = 0xef01f25c   ebp = 0xef01f28c   ebx = 0x0a6d2cd0
    esi = 0x02568d70   edi = 0x00000000
    Found by: call frame info
 6  0xa81e96
    eip = 0x00a81e96   esp = 0xef01f294   ebp = 0xef01f294
    Found by: previous frame's frame pointer
 7  0x66fb41
    eip = 0x0066fb41   esp = 0xef01f29c   ebp = 0xef01f2cc
    Found by: previous frame's frame pointer
 8  0x66fbcb
    eip = 0x0066fbcb   esp = 0xef01f2d4   ebp = 0xef01f2d8
    Found by: previous frame's frame pointer
 9  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xef01f2e0   ebp = 0xef01f3e8
    Found by: previous frame's frame pointer
10  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xef01f320   ebp = 0xef01f3e8   ebx = 0xf71f1000
    esi = 0xef01fb40   edi = 0x003d0f00
    Found by: call frame info
11  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xef01f3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 5
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xeee7e064   ebp = 0x00000189   ebx = 0xf09858a4
    esi = 0xeee7e1f4   edi = 0x483ebed0   eax = 0xfffffdfc   ecx = 0x00000189
    edx = 0x00000d0d   efl = 0x00200282
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xb12d
    eip = 0xf71e312d   esp = 0xeee7e06c   ebp = 0x00000189
    Found by: stack scanning
 2  libpthread-2.19.so + 0xb03b
    eip = 0xf71e303b   esp = 0xeee7e08c   ebp = 0x00000189
    Found by: stack scanning
 3  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1260 + 0x1b]
    eip = 0x48158df7   esp = 0xeee7e0a0   ebp = 0x00000189
    Found by: stack scanning
 4  witcher2!eON_Sleep [winthreads.cpp : 1976 + 0x33]
    eip = 0x4816890c   esp = 0xeee7e230   ebp = 0xeee7e254   ebx = 0x0a6d2d00
    esi = 0x02568d70   edi = 0x00000000
    Found by: call frame info
 5  0xa6e29f
    eip = 0x00a6e29f   esp = 0xeee7e25c   ebp = 0xeee7e28c   ebx = 0x0a6d2d00
    esi = 0x02568d70   edi = 0x00000000
    Found by: call frame info
 6  0xa81e96
    eip = 0x00a81e96   esp = 0xeee7e294   ebp = 0xeee7e294
    Found by: previous frame's frame pointer
 7  0x66fb41
    eip = 0x0066fb41   esp = 0xeee7e29c   ebp = 0xeee7e2cc
    Found by: previous frame's frame pointer
 8  0x66fbcb
    eip = 0x0066fbcb   esp = 0xeee7e2d4   ebp = 0xeee7e2d8
    Found by: previous frame's frame pointer
 9  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xeee7e2e0   ebp = 0xeee7e3e8
    Found by: previous frame's frame pointer
10  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xeee7e320   ebp = 0xeee7e3e8   ebx = 0xf71f1000
    esi = 0xeee7eb40   edi = 0x003d0f00
    Found by: call frame info
11  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xeee7e3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 6
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xf170f12c   ebp = 0x00000002   ebx = 0xeeb00ba0
    esi = 0xf0977580   edi = 0xf2d1d540   eax = 0xfffffdfc   ecx = 0x00000002
    edx = 0x000001b7   efl = 0x00200293
    Found by: given as instruction pointer in context
 1  libc-2.19.so + 0xdd51b
    eip = 0xf710551b   esp = 0xf170f134   ebp = 0x00000002
    Found by: stack scanning
 2  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xf170f138   ebp = 0x00000002
    Found by: stack scanning
 3  libpulse.so.0.13.5 + 0x35586
    eip = 0xf2d1d586   esp = 0xf170f140   ebp = 0x00000002
    Found by: stack scanning
 4  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xf170f154   ebp = 0x00000002
    Found by: stack scanning
 5  libpulse.so.0.13.5 + 0x27116
    eip = 0xf2d0f116   esp = 0xf170f158   ebp = 0x00000002
    Found by: stack scanning
 6  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xf170f15c   ebp = 0x00000002
    Found by: stack scanning
 7  libpulse.so.0.13.5 + 0x23460
    eip = 0xf2d0b460   esp = 0xf170f160   ebp = 0x00000002
    Found by: stack scanning
 8  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xf170f174   ebp = 0x00000002
    Found by: stack scanning
 9  libpulse.so.0.13.5 + 0x35540
    eip = 0xf2d1d540   esp = 0xf170f17c   ebp = 0x00000002
    Found by: stack scanning
10  libpulse.so.0.13.5 + 0x237ea
    eip = 0xf2d0b7ea   esp = 0xf170f180   ebp = 0x00000002
    Found by: stack scanning
11  libc-2.19.so + 0xc2d8
    eip = 0xf70342d8   esp = 0xf170f194   ebp = 0x00000002
    Found by: stack scanning
12  libpulsecommon-1.1.so + 0x1fde0
    eip = 0xf19d7de0   esp = 0xf170f19c   ebp = 0x00000002
    Found by: stack scanning
13  libpthread-2.19.so + 0x2685
    eip = 0xf71da685   esp = 0xf170f1cc   ebp = 0x00000002
    Found by: stack scanning
14  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xf170f1d0   ebp = 0x00000002
    Found by: stack scanning
15  libpulse.so.0.13.5 + 0x24047
    eip = 0xf2d0c047   esp = 0xf170f1e0   ebp = 0xf170f3e8
    Found by: stack scanning
16  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xf170f3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 7
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xea9f71e0   ebp = 0x0000008b   ebx = 0xf0988d74
    esi = 0x00000000   edi = 0xf0977580   eax = 0xfffffdff   ecx = 0x0000008b
    edx = 0x00000161   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad1d
    eip = 0xf71e2d1d   esp = 0xea9f71e8   ebp = 0x0000008b
    Found by: stack scanning
 2  libpulsecommon-1.1.so + 0x63ff4
    eip = 0xf1a1bff4   esp = 0xea9f7200   ebp = 0x0000008b
    Found by: stack scanning
 3  libpulsecommon-1.1.so + 0x457bb
    eip = 0xf19fd7bb   esp = 0xea9f7210   ebp = 0x0000008b
    Found by: stack scanning
 4  libpulsecommon-1.1.so + 0x63ff4
    eip = 0xf1a1bff4   esp = 0xea9f721c   ebp = 0x0000008b
    Found by: stack scanning
 5  libpulsecommon-1.1.so + 0x463e4
    eip = 0xf19fe3e4   esp = 0xea9f7220   ebp = 0x0000008b
    Found by: stack scanning
 6  libpulsecommon-1.1.so + 0x46150
    eip = 0xf19fe150   esp = 0xea9f7228   ebp = 0x0000008b
    Found by: stack scanning
 7  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xea9f722c   ebp = 0x0000008b
    Found by: stack scanning
 8  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xea9f7240   ebp = 0x0000008b
    Found by: stack scanning
 9  libpulse.so.0.13.5 + 0x4cff4
    eip = 0xf2d34ff4   esp = 0xea9f724c   ebp = 0x0000008b
    Found by: stack scanning
10  libpulse.so.0.13.5 + 0x35d5e
    eip = 0xf2d1dd5e   esp = 0xea9f7250   ebp = 0x0000008b
    Found by: stack scanning
11  pulse-shm-2753270814 + 0x50000
    eip = 0xeaa48000   esp = 0xea9f7268   ebp = 0x0000008b
    Found by: stack scanning
12  libopenal-eon.so.1 + 0x56ad8
    eip = 0xf73bead8   esp = 0xea9f7278   ebp = 0xea9f7b40
    Found by: stack scanning
13  0xf0979618
    eip = 0xf0979618   esp = 0xea9f7b48   ebp = 0xea9f7b40
    Found by: previous frame's frame pointer

Thread 8
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xea6ff094   ebp = 0x00000189   ebx = 0xea4034bc
    esi = 0xea6ff224   edi = 0x483ebed0   eax = 0xfffffdfc   ecx = 0x00000189
    edx = 0x000010ef   efl = 0x00200282
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xb12d
    eip = 0xf71e312d   esp = 0xea6ff09c   ebp = 0x00000189
    Found by: stack scanning
 2  libpthread-2.19.so + 0xb03b
    eip = 0xf71e303b   esp = 0xea6ff0bc   ebp = 0x00000189
    Found by: stack scanning
 3  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1260 + 0x1b]
    eip = 0x48158df7   esp = 0xea6ff0d0   ebp = 0x00000189
    Found by: stack scanning
 4  witcher2!eON_Sleep [winthreads.cpp : 1976 + 0x33]
    eip = 0x4816890c   esp = 0xea6ff260   ebp = 0xea6ff288   ebx = 0xf09857e8
    esi = 0x0ceb0c98   edi = 0xea6ff2fe
    Found by: call frame info
 5  0x2912d05
    eip = 0x02912d05   esp = 0xea6ff290   ebp = 0xea6ff2a4   ebx = 0xf09857e8
    esi = 0x0ceb0c98   edi = 0xea6ff2fe
    Found by: call frame info
 6  0x2a3248d
    eip = 0x02a3248d   esp = 0xea6ff2ac   ebp = 0xea6ff2d8
    Found by: previous frame's frame pointer
 7  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xea6ff2e0   ebp = 0xea6ff3e8
    Found by: previous frame's frame pointer
 8  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xea6ff320   ebp = 0xea6ff3e8   ebx = 0xf71f1000
    esi = 0xea6ffb40   edi = 0x003d0f00
    Found by: call frame info
 9  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xea6ff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 9
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xea3ff094   ebp = 0x00000189   ebx = 0xea10349c
    esi = 0xea3ff224   edi = 0x483ebed0   eax = 0xfffffdfc   ecx = 0x00000189
    edx = 0x00000cc5   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xb12d
    eip = 0xf71e312d   esp = 0xea3ff09c   ebp = 0x00000189
    Found by: stack scanning
 2  libpthread-2.19.so + 0xb03b
    eip = 0xf71e303b   esp = 0xea3ff0bc   ebp = 0x00000189
    Found by: stack scanning
 3  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1260 + 0x1b]
    eip = 0x48158df7   esp = 0xea3ff0d0   ebp = 0x00000189
    Found by: stack scanning
 4  witcher2!eON_Sleep [winthreads.cpp : 1976 + 0x33]
    eip = 0x4816890c   esp = 0xea3ff260   ebp = 0xea3ff288   ebx = 0xf097a370
    esi = 0x0ceadeb0   edi = 0xea3ff2fe
    Found by: call frame info
 5  0x2912d05
    eip = 0x02912d05   esp = 0xea3ff290   ebp = 0xea3ff2a4   ebx = 0xf097a370
    esi = 0x0ceadeb0   edi = 0xea3ff2fe
    Found by: call frame info
 6  0x2a3248d
    eip = 0x02a3248d   esp = 0xea3ff2ac   ebp = 0xea3ff2d8
    Found by: previous frame's frame pointer
 7  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xea3ff2e0   ebp = 0xea3ff3e8
    Found by: previous frame's frame pointer
 8  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xea3ff320   ebp = 0xea3ff3e8   ebx = 0xf71f1000
    esi = 0xea3ffb40   edi = 0x003d0f00
    Found by: call frame info
 9  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xea3ff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 10
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xea0ff090   ebp = 0x00000080   ebx = 0xe9e034f4
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000b53   efl = 0x00200282
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xea0ff098   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1242 + 0x17]
    eip = 0x48158eea   esp = 0xea0ff0c0   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!eON_WaitForSingleObject [winthreads.cpp : 1939 + 0x32]
    eip = 0x4816880b   esp = 0xea0ff250   ebp = 0xea0ff274   ebx = 0xf0976d98
    esi = 0x0d0503f0   edi = 0xea0ff2fe
    Found by: call frame info
 4  0x291354c
    eip = 0x0291354c   esp = 0xea0ff27c   ebp = 0xea0ff2a4   ebx = 0xf0976d98
    esi = 0x0d0503f0   edi = 0xea0ff2fe
    Found by: call frame info
 5  0x2a3248d
    eip = 0x02a3248d   esp = 0xea0ff2ac   ebp = 0xea0ff2d8
    Found by: previous frame's frame pointer
 6  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xea0ff2e0   ebp = 0xea0ff3e8
    Found by: previous frame's frame pointer
 7  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xea0ff320   ebp = 0xea0ff3e8   ebx = 0xf71f1000
    esi = 0xea0ffb40   edi = 0x003d0f00
    Found by: call frame info
 8  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xea0ff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 11
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xe9dff090   ebp = 0x00000080   ebx = 0xe9b0349c
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xe9dff098   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1242 + 0x17]
    eip = 0x48158eea   esp = 0xe9dff0c0   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!eON_WaitForSingleObject [winthreads.cpp : 1939 + 0x32]
    eip = 0x4816880b   esp = 0xe9dff250   ebp = 0xe9dff27c   ebx = 0xf0977218
    esi = 0x0120d30c   edi = 0x481687d0
    Found by: call frame info
 4  0x6b9f7c
    eip = 0x006b9f7c   esp = 0xe9dff284   ebp = 0xe9dff2cc   ebx = 0xf0977218
    esi = 0x0120d30c   edi = 0x481687d0
    Found by: call frame info
 5  0x66fbcb
    eip = 0x0066fbcb   esp = 0xe9dff2d4   ebp = 0xe9dff2d8
    Found by: previous frame's frame pointer
 6  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xe9dff2e0   ebp = 0xe9dff3e8
    Found by: previous frame's frame pointer
 7  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xe9dff320   ebp = 0xe9dff3e8   ebx = 0xf71f1000
    esi = 0xe9dffb40   edi = 0x003d0f00
    Found by: call frame info
 8  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xe9dff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 12
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xe9aff090   ebp = 0x00000080   ebx = 0xe98034ac
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xe9aff098   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1242 + 0x17]
    eip = 0x48158eea   esp = 0xe9aff0c0   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!eON_WaitForSingleObject [winthreads.cpp : 1939 + 0x32]
    eip = 0x4816880b   esp = 0xe9aff250   ebp = 0xe9aff27c   ebx = 0xf09592b0
    esi = 0x0120d38c   edi = 0x481687d0
    Found by: call frame info
 4  0x6b9f7c
    eip = 0x006b9f7c   esp = 0xe9aff284   ebp = 0xe9aff2cc   ebx = 0xf09592b0
    esi = 0x0120d38c   edi = 0x481687d0
    Found by: call frame info
 5  0x66fbcb
    eip = 0x0066fbcb   esp = 0xe9aff2d4   ebp = 0xe9aff2d8
    Found by: previous frame's frame pointer
 6  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xe9aff2e0   ebp = 0xe9aff3e8
    Found by: previous frame's frame pointer
 7  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xe9aff320   ebp = 0xe9aff3e8   ebx = 0xf71f1000
    esi = 0xe9affb40   edi = 0x003d0f00
    Found by: call frame info
 8  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xe9aff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Thread 13
 0  linux-gate.so + 0x425
    eip = 0xf779f425   esp = 0xe97ff090   ebp = 0x00000080   ebx = 0xe95034ac
    esi = 0x00000000   edi = 0x483ebed0   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200286
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71e2d4b   esp = 0xe97ff098   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!Synchronisation_WaitForMultipleObjects [synchronisationPrimitives.cpp : 1242 + 0x17]
    eip = 0x48158eea   esp = 0xe97ff0c0   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!eON_WaitForSingleObject [winthreads.cpp : 1939 + 0x32]
    eip = 0x4816880b   esp = 0xe97ff250   ebp = 0xe97ff27c   ebx = 0xf0982b88
    esi = 0x0120d40c   edi = 0x481687d0
    Found by: call frame info
 4  0x6b9f7c
    eip = 0x006b9f7c   esp = 0xe97ff284   ebp = 0xe97ff2cc   ebx = 0xf0982b88
    esi = 0x0120d40c   edi = 0x481687d0
    Found by: call frame info
 5  0x66fbcb
    eip = 0x0066fbcb   esp = 0xe97ff2d4   ebp = 0xe97ff2d8
    Found by: previous frame's frame pointer
 6  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x4816700c   esp = 0xe97ff2e0   ebp = 0xe97ff3e8
    Found by: previous frame's frame pointer
 7  libpthread-2.19.so + 0x6f70
    eip = 0xf71def70   esp = 0xe97ff320   ebp = 0xe97ff3e8   ebx = 0xf71f1000
    esi = 0xe97ffb40   edi = 0x003d0f00
    Found by: call frame info
 8  libc-2.19.so + 0xec47e
    eip = 0xf711447e   esp = 0xe97ff3f0   ebp = 0x00000000
    Found by: previous frame's frame pointer

Loaded modules:
0x48000000 - 0x482effff  witcher2  ???  (main)
0xe9f60000 - 0xe9f61fff  glszjLPy (deleted)  ???
0xea590000 - 0xea591fff  glszjLPy (deleted)  ???
0xea9f8000 - 0xee9f8fff  pulse-shm-2753270814  ???  (WARNING: No symbols, pulse-shm-2753270814, 000000000000000000000000000000000)
0xef020000 - 0xef35efff  libsteam.so  ???
0xef360000 - 0xef382fff  libnssutil3.so  ???
0xef388000 - 0xef3a6fff  libselinux.so.1  ???
0xef3a8000 - 0xef3e3fff  libnspr4.so  ???
0xef3e8000 - 0xef411fff  libsmime3.so  ???
0xef418000 - 0xef545fff  libnss3.so  ???
0xef548000 - 0xef69efff  libgio-2.0.so.0.3200.3  ???
0xef6a0000 - 0xef6dbfff  libpcre.so.3.12.1  ???
0xef6e0000 - 0xf07dafff  steamclient.so  ???
0xf0b08000 - 0xf0b11fff  libgudev-1.0.so.0.1.1  ???
0xf0b18000 - 0xf0b27fff  libudev.so.0.13.0  ???
0xf0b28000 - 0xf0b83fff  libnm-util.so.2.3.0  ???
0xf0b88000 - 0xf0bbffff  libnm-glib.so.4.3.0  ???
0xf0bc0000 - 0xf0be5fff  libdbus-glib-1.so.2.2.2  ???
0xf0be8000 - 0xf0ce0fff  libglib-2.0.so.0.3200.3  ???
0xf0ce8000 - 0xf0d36fff  libgobject-2.0.so.0.3200.3  ???
0xf0d38000 - 0xf0d81fff  libopenal.so.1.13.0  ???
0xf0d88000 - 0xf0dc4fff  libvstdlib_s.so  ???
0xf0dd8000 - 0xf0e01fff  libtier0_s.so  ???
0xf1710000 - 0xf173afff  libvorbis.so.0.4.5  ???
0xf1740000 - 0xf18b7fff  libvorbisenc.so.2.0.8  ???
0xf18b8000 - 0xf1905fff  libFLAC.so.8.2.0  ???
0xf1908000 - 0xf191efff  libnsl-2.19.so  ???
0xf1928000 - 0xf192cfff  libplds4.so  ???
0xf1930000 - 0xf193ffff  libusb-1.0.so.0.1.0  ???
0xf1940000 - 0xf19adfff  libsndfile.so.1.0.25  ???
0xf19b8000 - 0xf1a1cfff  libpulsecommon-1.1.so  ???  (WARNING: No symbols, libpulsecommon-1.1.so, 6A781A28412D8981C081A2D0F298A8CE0)
0xf1c20000 - 0xf23d2fff  icudt52l.dat  ???
0xf25e0000 - 0xf25e5fff  libplc4.so  ???
0xf2cb8000 - 0xf2cbcfff  libgmodule-2.0.so.0.3200.3  ???
0xf2cc0000 - 0xf2cc6fff  libffi.so.6.0.0  ???
0xf2cc8000 - 0xf2ccffff  libogg.so.0.7.1  ???
0xf2cd0000 - 0xf2cd6fff  libasyncns.so.0.3.1  ???
0xf2cd8000 - 0xf2ce1fff  libwrap.so.0.7.6  ???
0xf2ce8000 - 0xf2d35fff  libpulse.so.0.13.5  ???  (WARNING: No symbols, libpulse.so.0.13.5, 82C073F2D9C418E0D88EF55BC313559F0)
0xf2d38000 - 0xf2d61fff  libpng12.so.0.46.0  ???
0xf2d68000 - 0xf2d71fff  libnih-dbus.so.1.0.0  ???
0xf2d78000 - 0xf2d90fff  libnih.so.1.0.0  ???
0xf2d98000 - 0xf2db5fff  libcgmanager.so.0.0.0  ???
0xf2db8000 - 0xf2dcafff  libudev.so.1.3.5  ???
0xf2dd0000 - 0xf2dd5fff  libuuid.so.1.3.0  ???
0xf2dd8000 - 0xf2de0fff  libjson.so.0.0.1  ???
0xf2de8000 - 0xf2deefff  gconv-modules.cache  ???
0xf2f50000 - 0xf2f99fff  libdbus-1.so.3.5.8  ???
0xf2fa0000 - 0xf2fa5fff  libXxf86vm.so.1.0.0  ???
0xf2fa8000 - 0xf2fabfff  libXss.so.1.0.0  ???
0xf2fb0000 - 0xf2fb8fff  libXrandr.so.2.2.0  ???
0xf2fc0000 - 0xf2fcffff  libXi.so.6.1.0  ???
0xf2fd0000 - 0xf2fd3fff  libXinerama.so.1.0.0  ???
0xf2fd8000 - 0xf2fddfff  libXfixes.so.3.1.0  ???
0xf2fe0000 - 0xf2fe9fff  libXrender.so.1.3.0  ???
0xf2ff0000 - 0xf3020fff  kkk-Shm_97805504  ???
0xf3028000 - 0xf4028fff  kkk-Shm_dcc1b09a  ???
0xf40d0000 - 0xf41d0fff  kkk-Shm_c519b24  ???
0xf41d8000 - 0xf4258fff  kkk-Shm_205384dd  ???
0xf4260000 - 0xf42dffff  kkk-ValveIPCSharedObjects5  ???
0xf4328000 - 0xf4331fff  libcrypt-2.19.so  ???
0xf4360000 - 0xf4403fff  libsqlite3.so.0.8.6  ???
0xf4408000 - 0xf444efff  libhx509.so.5.0.0  ???
0xf4450000 - 0xf445efff  libheimbase.so.1.0.0  ???
0xf4460000 - 0xf4488fff  libwind.so.0.0.0  ???
0xf4490000 - 0xf4493fff  libkeyutils.so.1.4  ???
0xf4498000 - 0xf449cfff  libgpg-error.so.0.8.0  ???
0xf44a0000 - 0xf44b1fff  libp11-kit.so.0.0.0  ???
0xf44b8000 - 0xf44c9fff  libtasn1.so.3.1.12  ???
0xf44d0000 - 0xf44e5fff  libroken.so.18.1.0  ???
0xf44e8000 - 0xf451bfff  libhcrypto.so.4.1.0  ???
0xf4520000 - 0xf45c4fff  libasn1.so.8.0.0  ???
0xf45c8000 - 0xf464afff  libkrb5.so.26.0.0  ???
0xf4650000 - 0xf4657fff  libheimntlm.so.0.1.0  ???
0xf4658000 - 0xf465efff  libXdmcp.so.6.0.0  ???
0xf4660000 - 0xf4663fff  libXau.so.6.0.0  ???
0xf4668000 - 0xf4670fff  libkrb5support.so.0.1  ???
0xf4678000 - 0xf467cfff  libcom_err.so.2.1  ???
0xf4680000 - 0xf46a7fff  libk5crypto.so.3.1  ???
0xf46a8000 - 0xf4776fff  libkrb5.so.3.3  ???
0xf4778000 - 0xf47fcfff  libgcrypt.so.11.7.0  ???
0xf4800000 - 0xf48c3fff  libgnutls.so.26.21.8  ???
0xf48c8000 - 0xf4904fff  libgssapi.so.3.0.0  ???
0xf4908000 - 0xf4923fff  libsasl2.so.2.0.25  ???
0xf4928000 - 0xf493dfff  libresolv-2.19.so  ???
0xf4940000 - 0xf4961fff  libxcb.so.1.1.0  ???
0xf4968000 - 0xf4981fff  librtmp.so.0  ???
0xf4988000 - 0xf4b2ffff  libcrypto.so.1.0.0  ???
0xf4b38000 - 0xf4b8ffff  libssl.so.1.0.0  ???
0xf4b90000 - 0xf4bcdfff  libgssapi_krb5.so.2.2  ???
0xf4bd0000 - 0xf4c20fff  libldap_r-2.4.so.2.8.1  ???
0xf4c28000 - 0xf4c36fff  liblber-2.4.so.2.8.1  ???
0xf4c38000 - 0xf4c6bfff  libidn.so.11.6.6  ???
0xf4c70000 - 0xf4c85fff  libz.so.1.2.3.4  ???
0xf4c88000 - 0xf4c99fff  libXext.so.6.4.0  ???
0xf4ca0000 - 0xf4dd2fff  libX11.so.6.3.0  ???
0xf4dd8000 - 0xf7006fff  libnvidia-glcore.so.331.113  ???
0xf7020000 - 0xf7023fff  libnvidia-tls.so.331.113  ???
0xf7028000 - 0xf71d3fff  libc-2.19.so  ???  (WARNING: No symbols, libc-2.19.so, 248F5F497A43BD9AFA7B5651819C51130)
0xf71d8000 - 0xf71f1fff  libpthread-2.19.so  ???  (WARNING: No symbols, libpthread-2.19.so, 3A20DCD71118224076A30B3305B1355C0)
0xf71f8000 - 0xf7212fff  libgcc_s.so.1  ???
0xf7218000 - 0xf725dfff  libm-2.19.so  ???
0xf7260000 - 0xf7341fff  libstdc++.so.6.0.18  ???
0xf7350000 - 0xf7361fff  libsteam_api.so  ???
0xf7368000 - 0xf73cffff  libopenal-eon.so.1  ???  (WARNING: No symbols, libopenal-eon.so.1, A8BD998381DBABC124C8CAB810A7254A0)
0xf73d8000 - 0xf7434fff  libcurl.so.4.2.0  ???
0xf7438000 - 0xf74d1fff  libfreetype.so.6.8.0  ???
0xf74d8000 - 0xf74dcfff  libdl-2.19.so  ???
0xf74e0000 - 0xf74e8fff  librt-2.19.so  ???
0xf74f0000 - 0xf7506fff  libSDL2_image-2.0.so.0.0.0  ???
0xf7518000 - 0xf7616fff  libSDL2-2.0.so.0  ???  (WARNING: No symbols, libSDL2-2.0.so.0, EB4AA6D736146AECAEEF156EA70161200)
0xf7620000 - 0xf7715fff  libGL.so.331.113  ???
0xf7730000 - 0xf773afff  libXcursor.so.1.0.2  ???
0xf7740000 - 0xf7775fff  gameoverlayrenderer.so  ???
0xf7778000 - 0xf7799fff  ld-2.19.so  ???  (WARNING: No symbols, ld-2.19.so, CDBDF512BD6AA45F11D5DB326AFCECE60)
0xf779f000 - 0xf779ffff  linux-gate.so  ???  (WARNING: No symbols, linux-gate.so, F7DEFD53DE65481EEF3B580C4B0D681A0)
===============================================================================================
Output of command: 'uname -a 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Linux kkk-desktop 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
===============================================================================================
Output of command: 'lsb_release -a 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty
===============================================================================================
Output of command: 'grep "model name" /proc/cpuinfo | head -n1 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
model name    : AMD FX(tm)-8320 Eight-Core Processor
===============================================================================================
Output of command: 'free 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
             total       used       free     shared    buffers     cached
Mem:       8010448    3333592    4676856      83052      41204    2134780
-/+ buffers/cache:    1157608    6852840
Swap:      4095996          0    4095996
===============================================================================================
Output of command: 'set | egrep '^(LANG|LC_)' 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
LANG='en_GB.UTF-8'
LANGUAGE='en_GB:en'
===============================================================================================
Output of command: 'ulimit -a 2>&1'
===============================================================================================
time(seconds)        unlimited
file(blocks)         unlimited
data(kbytes)         unlimited
stack(kbytes)        8192
coredump(blocks)     0
memory(kbytes)       unlimited
locked memory(kbytes) 64
process              60764
nofiles              4096
vmemory(kbytes)      unlimited
locks                unlimited
===============================================================================================
Output of command: 'lspci -nn -k 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
lspci: /home/kkk/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libpci.so.3: version `LIBPCI_3.2' not found (required by lspci)
===============================================================================================
Output of command: 'lsusb 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Bus 004 Device 002: ID 0461:4e22 Primax Electronics, Ltd 
Bus 005 Device 002: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
===============================================================================================
Output of command: 'lsmod 2>&1'
===============================================================================================
ERROR: ld.so: object '/home/kkk/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  12 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
joydev                 17381  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
nvidia              10744943  53 
kvm_amd                60026  0 
kvm                   455835  1 kvm_amd
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
eeepc_wmi              13151  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
asus_wmi               24191  1 eeepc_wmi
snd_timer              29482  2 snd_pcm,snd_seq
sparse_keymap          13948  1 asus_wmi
crct10dif_pclmul       14289  0 
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
drm                   303102  2 nvidia
edac_core              62291  0 
snd                    69322  34 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
aesni_intel            55624  0 
psmouse               106714  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
soundcore              12680  1 snd
sp5100_tco             13979  0 
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
wmi                    19177  2 mxm_wmi,asus_wmi
ablk_helper            13597  1 aesni_intel
edac_mce_amd           22617  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
k10temp                13126  0 
fam15h_power           13119  0 
i2c_piix4              22155  0 
serio_raw              13462  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
r8169                  67581  0 
ahci                   25819  3 
mii                    13934  1 r8169
libahci                32716  1 ahci
===============================================================================================
Output of command: 'glxinfo -l 2>&1'
===============================================================================================
sh: 1: glxinfo: not found
===============================================================================================
[thread ffffffff][I][0]: Log system initialised
[thread ffffffff][I][0]: Default allowed number of simultaneously open files in the system is 2448.
[thread ffffffff][I][0]: Current memlock limit is 65536.
[thread ffffffff][I][0]: setrlimit(RLIMIT_MEMLOCK) failed, (1) Operation not permitted
[thread 00000001][I][227]: OpenGL information:
[thread 00000001][I][227]:     renderer: GeForce GTX 650 Ti/PCIe/SSE2
[thread 00000001][I][227]:     vendor: NVIDIA Corporation
[thread 00000001][I][227]:     version: 3.2.0 NVIDIA 331.113
[thread 00000001][I][227]:     GLSL version: 1.50 NVIDIA via Cg compiler
[thread 00000004][W][295]: Game is trying to enable termination on heap corruption. We don't have it implemented at the moment, implement it? This warning will be issued only once per run.
[thread 00000004][W][341]: eON_LoadLibraryEx() couldn't load 'C:\home\kkk\.local\share\Steam\steamapps\common\the witcher 2\bin\telemetry32.dll', returning NULL!
[thread 00000004][W][8221]: REGISTRY OPERATION: RegOpenKeyExW() returns ERROR_NOT_FOUND (subkey not found) key = HKEY_CURRENT_USER, subkey = SOFTWARE\PersonalAudio\MyEars
[thread 00000004][W][13153]: eON_LoadLibraryEx() couldn't load 'LightFX.dll', returning NULL!
[thread 00000004][W][13153]: eON_LoadLibraryEx() couldn't load 'nvapi.dll', returning NULL!
[thread 00000004][W][13193]: eON_LoadLibraryEx() couldn't load 'wintab32.dll', returning NULL!
[thread 00000004][I][13210]: Direct3D9Imp::CreateDevice() - moving hFocusWindow to adapter 0's monitor
[thread 00000004][I][13277]: Available video memory: 0
[thread 00000004][I][13277]: Available texture memory: 0
[thread 00000004][W][13288]: Precompiled shaders file has incorrect content. Deleting file, and disabling precompiled shaders!
[thread 00000004][W][13288]: deleteFile() - failed to delete (null), (14) Bad address
[thread 0000000d][I][13288]: OPENGL: OpenGL thread start
[thread 0000000d][I][13329]: OpenGL backend to Direct3D9: SUMMARY OF FALLBACKS AND INEFFICIENCIES:
[thread 0000000d][I][13329]:  - Anisotropic texture filtering not supported in OpenGL! This may produce incorrect rendering results in game, as other texture filtering modes will be used instead.
[thread 0000000d][I][13329]: OpenGL backend to Direct3D9: END OF SUMMARY
[thread 0000000d][I][13366]: Recommended max number of vertices addressed in one glDrawRangeElements() call: 1048576
[thread 0000000d][I][13366]: Recommended max number of indices addressed in one glDrawRangeElements() call: 1048576
[thread 0000000d][I][13366]: Shader precompilation start: unprepared shaders: 623, unlinked programs: 496
[thread 0000000d][E][13366]: Fragment shader failed to compile!



help please...

[TABLE]
[TR]
[TD="class: gutter"][/TD]
[TD="class: code"][/TD]
[/TR]
[/TABLE]

---

### Post by vetulani on 2015-01-17
Hi
I'm having a similar issue since a few days, this is my error:

Output of command: ''/home/jasiek/Gry/witcher2gog/content/crash_reporting/minidump_stackwalk' '/home/jasiek/.local/share/cdprojektred/witcher2//0836b78b-df68-859f-1a80205f-6b71ab3f.dmp' '/home/jasiek/Gry/witcher2gog/content/crash_reporting/symbols/''
===============================================================================================
Operating system: Linux
                  0.0.0 Linux 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64
CPU: x86
     AuthenticAMD family 21 model 2 stepping 0
     1 CPU


Crash reason:  SIGSEGV
Crash address: 0x8


Thread 3 (crashed)
 0  0xad12c7
    eip = 0x00ad12c7   esp = 0xf2013a30   ebp = 0xf2013a40   ebx = 0xf2013cc8
    esi = 0xf2013a60   edi = 0x00000000   eax = 0xf2013a60   ecx = 0xf2013a80
    edx = 0xf1704b08   efl = 0x00210246
    Found by: given as instruction pointer in context
 1  0x4062d1
    eip = 0x004062d1   esp = 0xf2013a48   ebp = 0xf2013aa8
    Found by: previous frame's frame pointer
 2  0xab2380
    eip = 0x00ab2380   esp = 0xf2013ab0   ebp = 0xf2013e34
    Found by: previous frame's frame pointer
 3  0xab25f7
    eip = 0x00ab25f7   esp = 0xf2013e3c   ebp = 0xf2013e60
    Found by: previous frame's frame pointer
 4  0xad4590
    eip = 0x00ad4590   esp = 0xf2013e68   ebp = 0xf2013fa8
    Found by: previous frame's frame pointer
 5  0xad3f9c
    eip = 0x00ad3f9c   esp = 0xf2013fb0   ebp = 0xf201421c
    Found by: previous frame's frame pointer
 6  0x73ff4a
    eip = 0x0073ff4a   esp = 0xf2014224   ebp = 0xf20142ac
    Found by: previous frame's frame pointer
 7  0xf2014b40
    eip = 0xf2014b40   esp = 0xf20142b4   ebp = 0xf20143e8
    Found by: previous frame's frame pointer
 8  libc-2.19.so + 0xec47e
    eip = 0xf710c47e   esp = 0xf20143f0   ebp = 0x00000000
    Found by: previous frame's frame pointer


Thread 0
 0  linux-gate.so + 0x425
    eip = 0xf7786425   esp = 0xffc3fcc0   ebp = 0xffc3fce0   ebx = 0xffc3fce8
    esi = 0xf75fd6ec   edi = 0xffc3fce8   eax = 0xfffffdfc   ecx = 0xffc3fce0
    edx = 0xf75f7000   efl = 0x00200293
    Found by: given as instruction pointer in context
 1  0x168544
    eip = 0x00168544   esp = 0xffc3fce8   ebp = 0x00000000
    Found by: previous frame's frame pointer
 2  ld-2.19.so + 0xe181
    eip = 0xf776e181   esp = 0xffc3fcf8   ebp = 0x00000000
    Found by: stack scanning
 3  libSDL2-2.0.so.0.2.0 + 0x10f000
    eip = 0xf75f7000   esp = 0xffc3fd00   ebp = 0x00000000
    Found by: stack scanning
 4  libSDL2-2.0.so.0.2.0 + 0x47940
    eip = 0xf752f940   esp = 0xffc3fd10   ebp = 0x00000000
    Found by: stack scanning
 5  libSDL2-2.0.so.0.2.0 + 0x10f000
    eip = 0xf75f7000   esp = 0xffc3fd40   ebp = 0x00000000
    Found by: stack scanning
 6  libSDL2-2.0.so.0.2.0 + 0x41294
    eip = 0xf7529294   esp = 0xffc3fd50   ebp = 0xffc3fea8
    Found by: stack scanning
 7  libc-2.19.so + 0x19a83
    eip = 0xf7039a83   esp = 0xffc3feb0   ebp = 0x00000000
    Found by: previous frame's frame pointer
 8  libc-2.19.so + 0x19a83
    eip = 0xf7039a83   esp = 0xffc3fec0   ebp = 0x00000000
    Found by: stack scanning
 9  ld-2.19.so + 0xecea
    eip = 0xf776ecea   esp = 0xffc3fed0   ebp = 0xffc3ff5c
    Found by: stack scanning
10  0xffc408ea
    eip = 0xffc408ea   esp = 0xffc3ff64   ebp = 0xffc408d3
    Found by: previous frame's frame pointer
11  0x454b5f45
    eip = 0x454b5f45   esp = 0xffc408db   ebp = 0x4d4f4e47
    Found by: previous frame's frame pointer


Thread 1
 0  linux-gate.so + 0x425
    eip = 0xf7786425   esp = 0xf2a17240   ebp = 0x00000080   ebx = 0x043cee64
    esi = 0x00000000   edi = 0x043cee30   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200202
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71dad4b   esp = 0xf2a17248   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!TimerThreadFunction [synchronisationPrimitives.cpp : 347 + 0x14]
    eip = 0x0414b214   esp = 0xf2a17270   ebp = 0xf2a173e8
    Found by: stack scanning
 3  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x0415c343   esp = 0xf2a172d0   ebp = 0xf2a173e8   ebx = 0x05645348
    esi = 0xf2a17308   edi = 0xf2a172f8
    Found by: call frame info
 4  libpthread-2.19.so + 0x6f70
    eip = 0xf71d6f70   esp = 0xf2a17320   ebp = 0xf2a173e8   ebx = 0xf71e9000
    esi = 0xf2a17b40   edi = 0x003d0f00
    Found by: call frame info
 5  libc-2.19.so + 0xec47e
    eip = 0xf710c47e   esp = 0xf2a173f0   ebp = 0x00000000
    Found by: previous frame's frame pointer


Thread 2
 0  linux-gate.so + 0x425
    eip = 0xf7786425   esp = 0xf2916260   ebp = 0x00000080   ebx = 0x043ceea4
    esi = 0x00000000   edi = 0x043cee30   eax = 0xfffffe00   ecx = 0x00000080
    edx = 0x00000001   efl = 0x00200202
    Found by: given as instruction pointer in context
 1  libpthread-2.19.so + 0xad4b
    eip = 0xf71dad4b   esp = 0xf2916268   ebp = 0x00000080
    Found by: stack scanning
 2  witcher2!OverlappedIOThreadFunction [synchronisationPrimitives.cpp : 600 + 0x14]
    eip = 0x0414aec4   esp = 0xf2916290   ebp = 0x00000080
    Found by: stack scanning
 3  witcher2!ThreadRun [winthreads.cpp : 563 + 0x8]
    eip = 0x0415c343   esp = 0xf29162d0   ebp = 0xf29163e8   ebx = 0x05645570
    esi = 0xf2916308   edi = 0xf29162f8
    Found by: call frame info
 4  libpthread-2.19.so + 0x6f70
    eip = 0xf71d6f70   esp = 0xf2916320   ebp = 0xf29163e8   ebx = 0xf71e9000
    esi = 0xf2916b40   edi = 0x003d0f00
    Found by: call frame info
 5  libc-2.19.so + 0xec47e
    eip = 0xf710c47e   esp = 0xf29163f0   ebp = 0x00000000
    Found by: previous frame's frame pointer


Loaded modules:
0x04000000 - 0x042d3fff  witcher2  ???  (main)
0xf2a18000 - 0xf31cafff  icudt52l.dat  ???
0xf36e0000 - 0xf36e9fff  libnih-dbus.so.1.0.0  ???
0xf36f0000 - 0xf3708fff  libnih.so.1.0.0  ???
0xf3710000 - 0xf372dfff  libcgmanager.so.0.0.0  ???
0xf3730000 - 0xf3742fff  libudev.so.1.3.5  ???
0xf3770000 - 0xf3776fff  gconv-modules.cache  ???
0xf38d0000 - 0xf38d9fff  libcrypt-2.19.so  ???
0xf3908000 - 0xf39c3fff  libsqlite3.so.0.8.6  ???
0xf39c8000 - 0xf3a0dfff  libhx509.so.5.0.0  ???
0xf3a10000 - 0xf3a1efff  libheimbase.so.1.0.0  ???
0xf3a20000 - 0xf3a48fff  libwind.so.0.0.0  ???
0xf3a50000 - 0xf3a58fff  libogg.so.0.8.1  ???
0xf3a60000 - 0xf3a8dfff  libvorbis.so.0.4.7  ???
0xf3a90000 - 0xf3b1efff  libvorbisenc.so.2.0.10  ???
0xf3b20000 - 0xf3b53fff  libFLAC.so.8.3.0  ???
0xf3b58000 - 0xf3b6efff  libnsl-2.19.so  ???
0xf3b78000 - 0xf3b8dfff  libroken.so.18.1.0  ???
0xf3b90000 - 0xf3bc3fff  libhcrypto.so.4.1.0  ???
0xf3bc8000 - 0xf3c6dfff  libasn1.so.8.0.0  ???
0xf3c70000 - 0xf3cf5fff  libkrb5.so.26.0.0  ???
0xf3cf8000 - 0xf3d00fff  libheimntlm.so.0.1.0  ???
0xf3d08000 - 0xf3d0bfff  libkeyutils.so.1.4  ???
0xf3d10000 - 0xf3d14fff  libgpg-error.so.0.10.0  ???
0xf3d18000 - 0xf3d53fff  libp11-kit.so.0.0.0  ???
0xf3d58000 - 0xf3d6bfff  libtasn1.so.6.2.0  ???
0xf3d70000 - 0xf3d76fff  libasyncns.so.0.3.1  ???
0xf3d78000 - 0xf3de5fff  libsndfile.so.1.0.25  ???
0xf3df0000 - 0xf3df9fff  libwrap.so.0.7.6  ???
0xf3e00000 - 0xf3e06fff  libXdmcp.so.6.0.0  ???
0xf3e08000 - 0xf3e0bfff  libXau.so.6.0.0  ???
0xf3e10000 - 0xf3e4afff  libgssapi.so.3.0.0  ???
0xf3e50000 - 0xf3e6afff  libsasl2.so.2.0.25  ???
0xf3e70000 - 0xf3e85fff  libresolv-2.19.so  ???
0xf3e88000 - 0xf3e93fff  libkrb5support.so.0.1  ???
0xf3e98000 - 0xf3e9cfff  libcom_err.so.2.1  ???
0xf3ea0000 - 0xf3ecffff  libk5crypto.so.3.1  ???
0xf3ed0000 - 0xf3f8dfff  libkrb5.so.3.3  ???
0xf3f90000 - 0xf4015fff  libgcrypt.so.11.8.2  ???
0xf4018000 - 0xf40ddfff  libgnutls.so.26.22.6  ???
0xf40e0000 - 0xf40eefff  libjbig.so.0  ???
0xf40f0000 - 0xf4115fff  liblzma.so.5.0.0  ???
0xf4118000 - 0xf411efff  libffi.so.6.0.1  ???
0xf4120000 - 0xf4125fff  libXfixes.so.3.1.0  ???
0xf4128000 - 0xf4132fff  libXrender.so.1.3.0  ???
0xf4138000 - 0xf4182fff  libdbus-1.so.3.7.6  ???
0xf4188000 - 0xf4192fff  libjson-c.so.2.0.0  ???
0xf4198000 - 0xf4206fff  libpulsecommon-4.0.so  ???
0xf4208000 - 0xf4229fff  libxcb.so.1.1.0  ???
0xf4230000 - 0xf4280fff  libldap_r-2.4.so.2.8.3  ???
0xf4288000 - 0xf4296fff  liblber-2.4.so.2.8.3  ???
0xf4298000 - 0xf42dcfff  libgssapi_krb5.so.2.2  ???
0xf42e0000 - 0xf4489fff  libcrypto.so.1.0.0  ???
0xf4490000 - 0xf44e7fff  libssl.so.1.0.0  ???
0xf44e8000 - 0xf4502fff  librtmp.so.0  ???
0xf4508000 - 0xf453afff  libidn.so.11.6.11  ???
0xf4540000 - 0xf4559fff  libz.so.1.2.8  ???
0xf4560000 - 0xf45adfff  libwebp.so.5.0.0  ???
0xf45b0000 - 0xf4621fff  libtiff.so.5.2.0  ???
0xf4628000 - 0xf4672fff  libjpeg.so.8.0.2  ???
0xf4688000 - 0xf46affff  libpng12.so.0.50.0  ???
0xf46b0000 - 0xf46ebfff  libxkbcommon.so.0.0.0  ???
0xf46f0000 - 0xf46f8fff  libwayland-cursor.so.0.0.0  ???
0xf4700000 - 0xf470bfff  libwayland-client.so.0.2.0  ???
0xf4710000 - 0xf4712fff  libwayland-egl.so.1.0.0  ???
0xf4718000 - 0xf471dfff  libXxf86vm.so.1.0.0  ???
0xf4720000 - 0xf4723fff  libXss.so.1.0.0  ???
0xf4728000 - 0xf4732fff  libXrandr.so.2.2.0  ???
0xf4738000 - 0xf4748fff  libXi.so.6.1.0  ???
0xf4750000 - 0xf4753fff  libXinerama.so.1.0.0  ???
0xf4758000 - 0xf4762fff  libXcursor.so.1.0.2  ???
0xf4768000 - 0xf47b6fff  libpulse.so.0.16.2  ???
0xf47b8000 - 0xf47bcfff  libpulse-simple.so.0.0.4  ???
0xf47c0000 - 0xf48b5fff  libasound.so.2.0.0  ???
0xf48b8000 - 0xf48cafff  libXext.so.6.4.0  ???
0xf48d0000 - 0xf4a02fff  libX11.so.6.3.0  ???
0xf4a08000 - 0xf6ffcfff  libnvidia-glcore.so.343.36  ???
0xf7018000 - 0xf701cfff  libnvidia-tls.so.343.36  ???
0xf7020000 - 0xf71cbfff  libc-2.19.so  ???  (WARNING: No symbols, libc-2.19.so, 248F5F497A43BD9AFA7B5651819C51130)
0xf71d0000 - 0xf71e9fff  libpthread-2.19.so  ???  (WARNING: No symbols, libpthread-2.19.so, 3A20DCD71118224076A30B3305B1355C0)
0xf71f0000 - 0xf720cfff  libgcc_s.so.1  ???
0xf7210000 - 0xf7255fff  libm-2.19.so  ???
0xf7258000 - 0xf7339fff  libstdc++.so.6.0.19  ???
0xf7348000 - 0xf73affff  libopenal-eon.so.1  ???
0xf73b8000 - 0xf741ffff  libcurl.so.4.3.0  ???
0xf7420000 - 0xf74bffff  libfreetype.so.6.11.1  ???
0xf74c0000 - 0xf74d6fff  libSDL2_image-2.0.so.0.0.0  ???
0xf74e8000 - 0xf75f9fff  libSDL2-2.0.so.0.2.0  ???  (WARNING: No symbols, libSDL2-2.0.so.0.2.0, B9B3C28A99D390A7CD9E7A68B7EC23310)
0xf7600000 - 0xf770afff  libGL.so.343.36  ???
0xf7720000 - 0xf7728fff  librt-2.19.so  ???
0xf7730000 - 0xf7734fff  libdl-2.19.so  ???
0xf7760000 - 0xf7781fff  ld-2.19.so  ???  (WARNING: No symbols, ld-2.19.so, CDBDF512BD6AA45F11D5DB326AFCECE60)
0xf7786000 - 0xf7786fff  linux-gate.so  ???  (WARNING: No symbols, linux-gate.so, BDB000BACD3AF3A87A637ED5F8D5CA1D0)
===============================================================================================
Output of command: 'uname -a 2>&1'
===============================================================================================
Linux szoszon 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
===============================================================================================
Output of command: 'lsb_release -a 2>&1'
===============================================================================================
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty
===============================================================================================
Output of command: 'grep "model name" /proc/cpuinfo | head -n1 2>&1'
===============================================================================================
model name	: AMD FX(tm)-6300 Six-Core Processor
===============================================================================================
Output of command: 'free 2>&1'
===============================================================================================
             total       used       free     shared    buffers     cached
Mem:      16317356    1778432   14538924      31448     135884     726752
-/+ buffers/cache:     915796   15401560
Swap:            0          0          0
===============================================================================================
Output of command: 'set | egrep '^(LANG|LC_)' 2>&1'
===============================================================================================
LANG='pl_PL.UTF-8'
LANGUAGE='pl_PL:en'
LC_COLLATE='pl_PL.UTF-8'
LC_CTYPE='pl_PL.UTF-8'
LC_MESSAGES='pl_PL.UTF-8'
===============================================================================================
Output of command: 'ulimit -a 2>&1'
===============================================================================================
time(seconds)        unlimited
file(blocks)         unlimited
data(kbytes)         unlimited
stack(kbytes)        8192
coredump(blocks)     0
memory(kbytes)       unlimited
locked memory(kbytes) 64
process              127250
nofiles              1024
vmemory(kbytes)      unlimited
locks                unlimited
===============================================================================================
Output of command: 'lspci -nn -k 2>&1'
===============================================================================================
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD/ATI] RD990 I/O Memory Management Unit (IOMMU) [1002:5a23]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16]
	Kernel driver in use: pcieport
00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
	Kernel driver in use: pcieport
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ohci-pci
00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ehci-pci
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ohci-pci
00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: piix4_smbus
00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:d693]
	Kernel driver in use: snd_hda_intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ohci-pci
00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0]
	Kernel driver in use: pcieport
00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ohci-pci
00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: ehci-pci
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
	Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
	Kernel driver in use: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:8a96]
	Kernel driver in use: nvidia
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:8a96]
	Kernel driver in use: snd_hda_intel
02:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: xhci_hcd
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7693]
	Kernel driver in use: r8169
===============================================================================================
Output of command: 'lsusb 2>&1'
===============================================================================================
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 09da:054f A4 Tech Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 041e:4097 Creative Technology, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 056a:0065 Wacom Co., Ltd Bamboo
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
===============================================================================================
Output of command: 'lsmod 2>&1'
===============================================================================================
Module                  Size  Used by
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
dm_crypt               23177  0 
snd_hda_codec_hdmi     46207  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17381  0 
snd_usb_audio         153411  1 
videobuf2_core         40664  1 uvcvideo
snd_usbmidi_lib        29215  1 snd_usb_audio
wacom                  62856  0 
videodev              134688  2 uvcvideo,videobuf2_core
mxm_wmi                13021  0 
kvm_amd                59987  0 
kvm                   451511  1 kvm_amd
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_hda_codec_realtek    61438  1 
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  2 snd_usbmidi_lib,snd_seq_midi
snd_hda_intel          52355  5 
edac_core              62291  0 
fam15h_power           13119  0 
serio_raw              13462  0 
k10temp                13126  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
edac_mce_amd           22617  0 
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
nvidia              11057029  41 
snd_pcm               102099  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
sp5100_tco             13979  0 
snd_timer              29482  2 snd_pcm,snd_seq
i2c_piix4              22155  0 
snd                    69238  25 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   302817  2 nvidia
soundcore              12680  1 snd
wmi                    19177  1 mxm_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  6 hid_generic,usbhid,hid_logitech_dj
psmouse               102222  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  2 
pata_atiixp            13271  0 
libahci                32168  1 ahci
===============================================================================================
Output of command: 'glxinfo -l 2>&1'
===============================================================================================
sh: 1: glxinfo: not found
===============================================================================================
[thread ffffffff][I][8]: Log system initialised
[thread ffffffff][I][371]: Default allowed number of simultaneously open files in the system is 1024.
[thread ffffffff][I][371]: Current memlock limit is 65536.
[thread ffffffff][I][371]: setrlimit(RLIMIT_MEMLOCK) failed, (1) Operation not permitted
[thread 00000001][I][587]: OpenGL information:
[thread 00000001][I][587]:     renderer: GeForce GTX 650/PCIe/SSE2
[thread 00000001][I][587]:     vendor: NVIDIA Corporation
[thread 00000001][I][587]:     version: 3.2.0 NVIDIA 343.36
[thread 00000001][I][587]:     GLSL version: 1.50 NVIDIA via Cg compiler
[thread 00000004][W][2800]: Game is trying to enable termination on heap corruption. We don't have it implemented at the moment, implement it? This warning will be issued only once per run.
[thread 00000004][W][2838]: eON_LoadLibraryEx() couldn't load 'C:\home\jasiek\Gry\witcher2gog\content\bin\telemetry32.dll', returning NULL!

---

