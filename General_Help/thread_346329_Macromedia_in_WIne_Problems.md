---
title: "Macromedia in WIne Problems"
date: 2007-01-25
forum: General Help
---

### Post by skate_metaly on 2007-01-25
hi; 
i`m runing ubuntu edgy
i installed wine just for my macromedia flash
the install of flash was ok 
but when i want to launch it . it apears the loading with the Flash mx 2004 bla bla bla
and  in terminal 
it gives me 
```
libGL warning: 3D driver claims to not support visual 0x4b
err:shell:SHGetFileInfoW pidl is null!
fixme:wintab32:WTInfoW (0, 0, (nil)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:imm:ImmSetCandidateWindow (0x162e98, 0x33be30): stub
fixme:imm:ImmReleaseContext (0xd003e, 0x162e98): stub
fixme:imm:ImmReleaseContext (0xd003e, 0x162e98): stub
wine: Unhandled page fault on read access to 0x000007e0 at address 0x7e0 (thread 0030), starting debugger...
Unhandled exception: page fault on read access to 0x000007e0 in 32-bit code (0x000007e0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:000007e0 ESP:0033e9ac EBP:00000000 EFLAGS:00210212(   - 00      - RIA1)
 EAX:0000010a EBX:000003ef ECX:00000014 EDX:00000014
 ESI:00002270 EDI:01430478
Stack dump:
0x0033e9ac:  0000001f 00002270 0033eb1c 0033eaa4
0x0033e9bc:  00000014 04cc7390 00cb24a3 00002254
0x0033e9cc:  000003ef 00000000 0519c6c0 0519c6c0
0x0033e9dc:  0033eb1c 01b57b9f 00ccb2a3 01880000
0x0033e9ec:  00000000 00000001 044bd94c 00000000
0x0033e9fc:  00000000 01016b08 00002260 00000000
Backtrace:
=>1 0x000007e0 (0x00000000)
0x000007e0: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (119 modules)
PE      400000-154d000  Deferred        flash
PE      1990000-1d52000 Deferred        flashresources
PE      1d60000-1e63000 Deferred        mfc71
PE      4da0000-4da7000 Deferred        flfile
PE      10000000-1022f000       Deferred        flash_8_video_extension
PE      12000000-121ae000       Deferred        xerces-c_2_6
PE      13000000-13191000       Deferred        mmxptresources
PE      30000000-30256000       Deferred        authplay
ELF     7b800000-7b91c000       Deferred        kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bfe1000-7c000000       Deferred        wintab32<elf>
  \-PE  7bff0000-7c000000       \               wintab32
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7c5fe000-7c61e000       Deferred        mlang<elf>
  \-PE  7c610000-7c61e000       \               mlang
ELF     7c61e000-7c66c000       Deferred        crypt32<elf>
  \-PE  7c630000-7c66c000       \               crypt32
ELF     7c66c000-7c686000       Deferred        wsock32<elf>
  \-PE  7c670000-7c686000       \               wsock32
ELF     7c686000-7c69b000       Deferred        midimap<elf>
  \-PE  7c690000-7c69b000       \               midimap
PE      7c6a0000-7c6b3000       --none--        msacm32
ELF     7c6b3000-7c6ef000       Deferred        wineoss<elf>
  \-PE  7c6c0000-7c6ef000       \               wineoss
ELF     7c6ef000-7c6f3000       Deferred        libgpg-error.so.0
ELF     7c6f3000-7c741000       Deferred        libgcrypt.so.11
ELF     7c741000-7c754000       Deferred        libtasn1.so.3
ELF     7c754000-7c782000       Deferred        libcrypt.so.1
ELF     7c791000-7c800000       Deferred        libgnutls.so.13
ELF     7c800000-7c82f000       Deferred        libcups.so.2
ELF     7c848000-7c87a000       Deferred        uxtheme<elf>
  \-PE  7c850000-7c87a000       \               uxtheme
ELF     7c87c000-7c881000       Deferred        libxfixes.so.3
ELF     7c881000-7c88a000       Deferred        libxcursor.so.1
ELF     7c88a000-7c8a8000       Deferred        ximcp.so.2
ELF     7c8a8000-7c8aa000       Deferred        xlcutf8load.so.2
ELF     7c8aa000-7c8ad000       Deferred        libxrandr.so.2
ELF     7c8ad000-7c8b5000       Deferred        libxrender.so.1
ELF     7c8b5000-7c8b8000       Deferred        libxinerama.so.1
ELF     7dfa9000-7e1e5000       Deferred        radeon_dri.so
ELF     7e1e5000-7e1ec000       Deferred        libdrm.so.2
ELF     7e1ec000-7e25b000       Deferred        libgl.so.1
ELF     7e25b000-7e260000       Deferred        libxdmcp.so.6
ELF     7e260000-7e329000       Deferred        libx11.so.6
ELF     7e329000-7e336000       Deferred        libxext.so.6
ELF     7e336000-7e34e000       Deferred        libice.so.6
ELF     7e34e000-7e3db000       Deferred        winex11<elf>
  \-PE  7e360000-7e3db000       \               winex11
ELF     7e3db000-7e3f9000       Deferred        libexpat.so.1
ELF     7e3f9000-7e428000       Deferred        libfontconfig.so.1
ELF     7e428000-7e43c000       Deferred        libz.so.1
ELF     7e43c000-7e4a6000       Deferred        libfreetype.so.6
ELF     7e4a6000-7e4c8000       Deferred        oledlg<elf>
  \-PE  7e4b0000-7e4c8000       \               oledlg
ELF     7e4c8000-7e4e7000       Deferred        mpr<elf>
  \-PE  7e4d0000-7e4e7000       \               mpr
ELF     7e4e7000-7e52e000       Deferred        wininet<elf>
  \-PE  7e4f0000-7e52e000       \               wininet
ELF     7e52e000-7e55a000       Deferred        ws2_32<elf>
  \-PE  7e540000-7e55a000       \               ws2_32
ELF     7e55a000-7e5f2000       Deferred        oleaut32<elf>
  \-PE  7e570000-7e5f2000       \               oleaut32
ELF     7e5f2000-7e606000       Deferred        msimg32<elf>
  \-PE  7e600000-7e606000       \               msimg32
ELF     7e606000-7e622000       Deferred        imm32<elf>
  \-PE  7e610000-7e622000       \               imm32
ELF     7e622000-7e637000       Deferred        psapi<elf>
  \-PE  7e630000-7e637000       \               psapi
ELF     7e637000-7e65e000       Deferred        msvfw32<elf>
  \-PE  7e640000-7e65e000       \               msvfw32
ELF     7e65e000-7e684000       Deferred        msacm32<elf>
ELF     7e684000-7e6be000       Deferred        avifil32<elf>
  \-PE  7e690000-7e6be000       \               avifil32
ELF     7e6be000-7e74c000       Deferred        winmm<elf>
  \-PE  7e6d0000-7e74c000       \               winmm
ELF     7e74c000-7e760000       Deferred        lz32<elf>
  \-PE  7e750000-7e760000       \               lz32
ELF     7e760000-7e779000       Deferred        version<elf>
  \-PE  7e770000-7e779000       \               version
ELF     7e779000-7e7ab000       Deferred        winspool<elf>
  \-PE  7e780000-7e7ab000       \               winspool
ELF     7e7ab000-7e84b000       Deferred        comdlg32<elf>
  \-PE  7e7b0000-7e84b000       \               comdlg32
ELF     7e84b000-7e90b000       Deferred        comctl32<elf>
  \-PE  7e850000-7e90b000       \               comctl32
ELF     7e90b000-7e91e000       Deferred        libresolv.so.2
ELF     7e91e000-7e93c000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e93c000       \               iphlpapi
ELF     7e93c000-7e990000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e990000       \               rpcrt4
ELF     7e990000-7eac8000       Deferred        user32<elf>
  \-PE  7e9b0000-7eac8000       \               user32
ELF     7eac8000-7eb61000       Deferred        ole32<elf>
  \-PE  7eae0000-7eb61000       \               ole32
ELF     7eb61000-7ebb9000       Deferred        shlwapi<elf>
  \-PE  7eb70000-7ebb9000       \               shlwapi
ELF     7ebb9000-7ecab000       Deferred        shell32<elf>
  \-PE  7ebd0000-7ecab000       \               shell32
ELF     7ecab000-7ecb6000       Deferred        libgcc_s.so.1
ELF     7ecb9000-7ecbc000       Deferred        libxau.so.6
ELF     7ecbc000-7ecc5000       Deferred        libsm.so.6
ELF     7eda4000-7ee5a000       Deferred        gdi32<elf>
  \-PE  7edc0000-7ee5a000       \               gdi32
ELF     7ee5a000-7eea0000       Deferred        advapi32<elf>
  \-PE  7ee70000-7eea0000       \               advapi32
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c82000-b7c8b000       Deferred        libnss_compat.so.2
ELF     b7c8c000-b7c90000       Deferred        libdl.so.2
ELF     b7c90000-b7dc4000       Deferred        libc.so.6
ELF     b7dc5000-b7dd8000       Deferred        libpthread.so.0
ELF     b7de7000-b7ef8000       Deferred        libwine.so.1
ELF     b7efa000-b7f15000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001e (D) C:\Program Files\Macromedia\Flash 8\flash.exe
        00000040    0
        00000045    0
        0000001d   15
        00000030    0 <==
00000020 
        00000041    0
        0000001a    0
        0000003f    0
        0000002d    0
        00000025    0
        00000024    0
        00000023    0
        00000022    0
        00000021    0
0000000a 
        0000000c    0
        0000000b    0

```
Can someone just  tell me what is wrong or some fix
i really really really need this program:|
thank  you

---

