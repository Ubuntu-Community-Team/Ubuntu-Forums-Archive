---
title: "[SOLVED] Strange question about Wine"
date: 2007-09-08
forum: General Help
---

### Post by Amazona aestiva on 2007-09-08
I installed a game(Aura2) successfully.

I'd like to run it, BUT:

If I type:
```
wine '/home/nandor/.wine/drive_c/Program Files/The Adventure Company/Aura 2 The Sacred Rings/TSR.exe'
```
It won't run.

If I start the link on the desktop: (installer took it to there)
It runs.

BUT if I copy the link's command into the terminal it won't run.

Why can I start it from the link on my desktop, and why can't I start it from terminal or nautilus???????

---

### Post by Amazona aestiva on 2007-09-08
Is it too strange?:(

---

### Post by bogdan_5844 on 2007-09-08
no really,i think the problem is in the terminal
it doesn't handle really well the spaces in file names (e.g. /drive_c/Program Files/)
dunno how to type filenames with spaces in them
but i don't see the problem,if it works from the shortcut,why do you want to launch it from terminal ?

---

### Post by Amazona aestiva on 2007-09-08
It isn't working perfectly so I wanted to see what the terminal shows when lunch the app.

---

### Post by little_penguin on 2007-09-08
> **Amazona aestiva said:**
> I installed a game(Aura2) successfully.

I'd like to run it, BUT:

If I type:
```
wine '/home/nandor/.wine/drive_c/Program Files/The Adventure Company/Aura 2 The Sacred Rings/TSR.exe'
```
It won't run.

--------

Have you tried using double quotes, instead of single quotes?

---

### Post by Amazona aestiva on 2007-09-09
Yes I tried ' and " too.
I got:
> nandor@nandor-desktop:~$ wine "/home/nandor/.wine/drive_c/Program Files/The Adventure Company/Aura 2 The Sacred Rings/TSR.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec84,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1691f8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x168eb8)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x168eb8)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1692d0)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0xd78e38)->((nil),00000008)
fixme:avifile:AVIFileExit (): stub!
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0xde0468) : stub
fixme:d3d:IWineD3DSwapChainImpl_Present Unhandled present options 0x33f524/0x33f514
wine: Unhandled page fault on read access to 0x00000034 at address 0x24020426 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000034 in 32-bit code (0x24020426).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:24020426 ESP:0033fe24 EBP:0033fe24 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00404900 EBX:00000000 ECX:00000000 EDX:00404900
 ESI:001223e0 EDI:7ffdf000
Stack dump:
0x0033fe24:  0033fe3c 00401414 00000000 00404900
0x0033fe34:  00000000 00000000 0033fe64 00401364
0x0033fe44:  00404900 00010024 0000000f 00000000
0x0033fe54:  00000000 00001983 00000144 0000005f
0x0033fe64:  0033fe6c 004026ba 0033ff08 00402a04
0x0033fe74:  00400000 00000000 001223e0 0000000a
Backtrace:
=>1 0x24020426 in ck2 (+0x20426) (0x0033fe24)
  2 0x00401414 in tsr (+0x1414) (0x0033fe3c)
  3 0x00401364 in tsr (+0x1364) (0x0033fe64)
  4 0x004026ba in tsr (+0x26ba) (0x0033fe6c)
  5 0x00402a04 in tsr (+0x2a04) (0x0033ff08)
  6 0x7b874cce in kernel32 (+0x54cce) (0x0033ffe8)
  7 0xb7de19a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x24020426: movl        0x34(%ecx),%ecx
Modules:
Module  Address                 Debug info      Name (137 modules)
PE        340000-  34d000       Deferred        streko
PE        350000-  358000       Deferred        buildingblocksaddons2
PE        360000-  37b000       Deferred        grids
PE        3c0000-  3da000       Deferred        toolkit_30sp1
PE        3e0000-  3ea000       Deferred        midimanager
PE        3f0000-  3fa000       Deferred        cryptedloader
PE        400000-  407000       Export          tsr
PE        740000-  7f6000       Deferred        ck2_3d
PE        a10000-  a1c000       Deferred        vcrypt
PE        a20000-  a26000       Deferred        binkreader
PE        a30000-  b48000       Deferred        shader
PE        b50000-  ba6000       Deferred        vslmanager
PE        bb0000-  c02000       Deferred        vslrt
PE        c10000-  c4d000       Deferred        luamanager_test
PE        c50000-  c6a000       Deferred        jpgloader
PE      10000000-10010000       Deferred        ckzlib
PE      24000000-24076000       Export          ck2
PE      24280000-242dc000       Deferred        vxmath
PE      24500000-2450a000       Deferred        imagereader
PE      24580000-245bd000       Deferred        ddsreader
PE      24640000-24648000       Deferred        virtoolsloaderr
PE      24680000-24693000       Deferred        xloaderr
PE      24700000-24707000       Deferred        wavreader
PE      24740000-24746000       Deferred        avireader
PE      24840000-24855000       Deferred        pngloader
PE      248c0000-248fd000       Deferred        tiffreader
PE      24ac0000-24aca000       Deferred        dx5inputmanager
PE      24b40000-24b64000       Deferred        parameteroperations
PE      24bc0000-24bc9000       Deferred        dx7soundmanager
PE      24cc0000-24d3c000       Deferred        ckdx9rasterizer
PE      25000000-25039000       Deferred        3dtransfo
PE      25080000-2509d000       Deferred        particlesystems
PE      25100000-25121000       Deferred        buildingblocksaddons1
PE      25180000-2518a000       Deferred        cameras
PE      25200000-2520c000       Deferred        controllers
PE      25280000-2528d000       Deferred        characters
PE      25300000-25329000       Deferred        collisions
PE      25380000-2539d000       Deferred        interface
PE      25400000-25408000       Deferred        lights
PE      25480000-254b2000       Deferred        logics
PE      25500000-25511000       Deferred        materials
PE      25580000-25596000       Deferred        meshmodifiers
PE      25680000-2568e000       Deferred        narratives
PE      25700000-2570c000       Deferred        sounds
PE      25780000-257a5000       Deferred        visuals
PE      25880000-2588b000       Deferred        worldenvironments
PE      30000000-3006e000       Deferred        binkw32
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c799000-7c7c0000       Deferred        dmusic<elf>
  \-PE  7c7a0000-7c7c0000       \               dmusic
ELF     7c7e6000-7c815000       Deferred        d3d9<elf>
  \-PE  7c7f0000-7c815000       \               d3d9
ELF     7c823000-7c859000       Deferred        dinput<elf>
  \-PE  7c830000-7c859000       \               dinput
ELF     7c859000-7c8a2000       Deferred        dsound<elf>
  \-PE  7c860000-7c8a2000       \               dsound
ELF     7c8a2000-7c8be000       Deferred        d3dxof<elf>
  \-PE  7c8b0000-7c8be000       \               d3dxof
ELF     7c8be000-7c993000       Deferred        wined3d<elf>
  \-PE  7c8d0000-7c993000       \               wined3d
ELF     7c993000-7c9be000       Deferred        d3d8<elf>
  \-PE  7c9a0000-7c9be000       \               d3d8
ELF     7c9be000-7c9e5000       Deferred        msvfw32<elf>
  \-PE  7c9d0000-7c9e5000       \               msvfw32
ELF     7c9e5000-7ca1f000       Deferred        avifil32<elf>
  \-PE  7c9f0000-7ca1f000       \               avifil32
ELF     7d1ad000-7d1df000       Deferred        uxtheme<elf>
  \-PE  7d1b0000-7d1df000       \               uxtheme
ELF     7d1df000-7d29d000       Deferred        comctl32<elf>
  \-PE  7d1f0000-7d29d000       \               comctl32
ELF     7d29d000-7d2f6000       Deferred        shlwapi<elf>
  \-PE  7d2b0000-7d2f6000       \               shlwapi
ELF     7d2f6000-7d3f9000       Deferred        shell32<elf>
  \-PE  7d310000-7d3f9000       \               shell32
ELF     7d3f9000-7d40e000       Deferred        midimap<elf>
  \-PE  7d400000-7d40e000       \               midimap
ELF     7d40e000-7d4d3000       Deferred        libasound.so.2
ELF     7d4d3000-7d508000       Deferred        winealsa<elf>
  \-PE  7d4e0000-7d508000       \               winealsa
ELF     7d508000-7d52e000       Deferred        msacm32<elf>
  \-PE  7d510000-7d52e000       \               msacm32
ELF     7d52e000-7d5bc000       Deferred        winmm<elf>
  \-PE  7d540000-7d5bc000       \               winmm
ELF     7d80a000-7d822000       Deferred        msacm32<elf>
  \-PE  7d810000-7d822000       \               msacm32
ELF     7d822000-7d827000       Deferred        libxfixes.so.3
ELF     7d827000-7d830000       Deferred        libxcursor.so.1
ELF     7d830000-7d84d000       Deferred        imm32<elf>
  \-PE  7d840000-7d84d000       \               imm32
ELF     7d84d000-7d855000       Deferred        libxrender.so.1
ELF     7dd8b000-7dd8d000       Deferred        libnvidia-tls.so.1
ELF     7dd8d000-7e613000       Deferred        libglcore.so.1
ELF     7e613000-7e69f000       Deferred        libgl.so.1
ELF     7e69f000-7e6a4000       Deferred        libxdmcp.so.6
ELF     7e6a4000-7e6a7000       Deferred        libxau.so.6
ELF     7e6a7000-7e798000       Deferred        libx11.so.6
ELF     7e798000-7e7a6000       Deferred        libxext.so.6
ELF     7e7a6000-7e7ab000       Deferred        libxxf86vm.so.1
ELF     7e7ab000-7e7c3000       Deferred        libice.so.6
ELF     7e7c3000-7e7cc000       Deferred        libsm.so.6
ELF     7e7cd000-7e7d3000       Deferred        libxrandr.so.2
ELF     7e7dc000-7e866000       Deferred        winex11<elf>
  \-PE  7e7f0000-7e866000       \               winex11
ELF     7e8d2000-7e8f2000       Deferred        libexpat.so.1
ELF     7e8f2000-7e91d000       Deferred        libfontconfig.so.1
ELF     7e91d000-7e931000       Deferred        libz.so.1
ELF     7e931000-7e99c000       Deferred        libfreetype.so.6
ELF     7e99c000-7e9af000       Deferred        libresolv.so.2
ELF     7e9af000-7e9cd000       Deferred        iphlpapi<elf>
  \-PE  7e9c0000-7e9cd000       \               iphlpapi
ELF     7e9cd000-7ea26000       Deferred        rpcrt4<elf>
  \-PE  7e9e0000-7ea26000       \               rpcrt4
ELF     7ea26000-7eac5000       Deferred        ole32<elf>
  \-PE  7ea40000-7eac5000       \               ole32
ELF     7eac5000-7eb2c000       Deferred        msvcrt<elf>
  \-PE  7eae0000-7eb2c000       \               msvcrt
ELF     7eb2c000-7eb74000       Deferred        advapi32<elf>
  \-PE  7eb40000-7eb74000       \               advapi32
ELF     7eb74000-7eb80000       Deferred        libgcc_s.so.1
ELF     7ec7a000-7ed3a000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed3a000       \               gdi32
ELF     7ed3a000-7ee78000       Deferred        user32<elf>
  \-PE  7ed60000-7ee78000       \               user32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c63000-b7c6c000       Deferred        libnss_compat.so.2
ELF     b7c6d000-b7c71000       Deferred        libdl.so.2
ELF     b7c71000-b7db2000       Deferred        libc.so.6
ELF     b7db3000-b7dca000       Deferred        libpthread.so.0
ELF     b7dda000-b7eee000       Export          libwine.so.1
ELF     b7ef0000-b7f0b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\The Adventure Company\Aura 2 The Sacred Rings\TSR.exe
        00000010   15
        0000000f   15
        0000000d    0
        00000009    2 <==
nandor@nandor-desktop:~$

---

### Post by Amazona aestiva on 2007-09-09
So it should run from terminal?
I think that too... BUT IT DOESN'T RUN FROM IT!!!!
:confused:

---

### Post by Amazona aestiva on 2007-10-08
Have no idea. Perhaps it's Wine's fault.

---

