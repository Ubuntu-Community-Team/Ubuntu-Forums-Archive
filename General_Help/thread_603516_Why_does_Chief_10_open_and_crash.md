---
title: "Why does Chief 10 open and crash?"
date: 2007-11-05
forum: General Help
---

### Post by kdarkentity on 2007-11-05
Chief architect 10 opens up in wine smoothly at first but then immediately crashes after it starts up, why is this and how may i fix it?

--------------------terminal output---------------

kevin@S204Ubuntu:~$ wine '/home/kevin/Desktop/Chief Architect 10.0 Full Version/Chief Architect 10 Full.exe' 
fixme:wtsapi:WTSQuerySessionInformationA Stub (nil) 0xffffffff 4 0x330624 0x330618
wine: Unhandled division by zero at address 0x7e6fa120 (thread 0009), starting debugger...
Unhandled exception: divide by zero in 32-bit code (0x7e6fa120).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e6fa120 ESP:0033e31c EBP:0033e374 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:0000000b EBX:7e72523c ECX:0000000c EDX:00000000
 ESI:00000000 EDI:001b49e0
Stack dump:
0x0033e31c:  0001006e 00000000 00000000 0001006e
0x0033e32c:  00000000 00000014 00000014 7e72523c
0x0033e33c:  001b49e0 00000420 0033f89c 0001006e
0x0033e34c:  00000000 00000001 001b7260 7e72523c
0x0033e35c:  00000000 00000427 7e6fa05d 7e72523c
0x0033e36c:  001b49e0 00000427 0033f024 7e6fc999
Backtrace:
=>1 0x7e6fa120 in comctl32 (+0x7a120) (0x0033e374)
  2 0x7e6fc999 in comctl32 (+0x7c999) (0x0033f024)
  3 0x7ea64f8a WINPROC_wrapper+0x1a() in user32 (0x0033f054)
  4 0x7ea6569e in user32 (+0xa569e) (0x0033f094)
  5 0x7ea685b1 WINPROC_CallProcAtoW+0xb1() in user32 (0x0033f554)
  6 0x7ea69745 CallWindowProcA+0x155() in user32 (0x0033f5a4)
  7 0x00bf11d7 in chief architect 10 full (+0x7f11d7) (0x02285388)
  8 0x00000000 (0x00e0ac2c)
  9 0x00a070c0 in chief architect 10 full (+0x6070c0) (0x00a070b0)
0x7e6fa120: idivl       %esi,%eax
Modules:
Module  Address                 Debug info      Name (127 modules)
PE        340000-  390000       Deferred        dd_gi
PE        390000-  396000       Deferred        dd_alloc
PE        3a0000-  3dc000       Deferred        dd_root
PE        3e0000-  3fe000       Deferred        sx32w
PE        400000- 134a000       Export          chief architect 10 full
PE       1350000- 173b000       Deferred        dd_db
PE       1740000- 17b0000       Deferred        dd_ge
PE       17b0000- 1877000       Deferred        spr32d35
PE       2040000- 208a000       Deferred        tb24p
PE      10000000-10039000       Deferred        ssce5432
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7d152000-7d167000       Deferred        wtsapi32<elf>
  \-PE  7d160000-7d167000       \               wtsapi32
ELF     7d167000-7d1b8000       Deferred        libgcrypt.so.11
ELF     7d1b8000-7d1e6000       Deferred        libcrypt.so.1
ELF     7d1e6000-7d256000       Deferred        libgnutls.so.13
ELF     7d256000-7d27b000       Deferred        libk5crypto.so.3
ELF     7d27b000-7d303000       Deferred        libkrb5.so.3
ELF     7d303000-7d32c000       Deferred        libgssapi_krb5.so.2
ELF     7d32c000-7d361000       Deferred        libcups.so.2
ELF     7d361000-7d376000       Deferred        midimap<elf>
  \-PE  7d370000-7d376000       \               midimap
ELF     7d376000-7d38e000       Deferred        msacm32<elf>
  \-PE  7d380000-7d38e000       \               msacm32
ELF     7d48e000-7d492000       Deferred        libgpg-error.so.0
ELF     7d492000-7d4a2000       Deferred        libtasn1.so.3
ELF     7d4a2000-7d568000       Deferred        libasound.so.2
ELF     7d576000-7d5ac000       Deferred        winealsa<elf>
  \-PE  7d580000-7d5ac000       \               winealsa
ELF     7d5dc000-7d5de000       Deferred        libkeyutils.so.1
ELF     7d5fe000-7d630000       Deferred        uxtheme<elf>
  \-PE  7d610000-7d630000       \               uxtheme
ELF     7d630000-7d639000       Deferred        libxcursor.so.1
ELF     7d639000-7d656000       Deferred        imm32<elf>
  \-PE  7d640000-7d656000       \               imm32
ELF     7d656000-7d659000       Deferred        libxcomposite.so.1
ELF     7d659000-7d65f000       Deferred        libxrandr.so.2
ELF     7d65f000-7d667000       Deferred        libxrender.so.1
ELF     7d668000-7d670000       Deferred        libkrb5support.so.0
ELF     7d670000-7d673000       Deferred        libcom_err.so.2
ELF     7dd68000-7df99000       Deferred        r300_dri.so
ELF     7df99000-7e026000       Deferred        winex11<elf>
  \-PE  7dfb0000-7e026000       \               winex11
ELF     7e0b4000-7e0d4000       Deferred        libexpat.so.1
ELF     7e0d4000-7e0ff000       Deferred        libfontconfig.so.1
ELF     7e10d000-7e122000       Deferred        libz.so.1
ELF     7e122000-7e192000       Deferred        libfreetype.so.6
ELF     7e192000-7e1fa000       Deferred        msvcrt<elf>
  \-PE  7e1a0000-7e1fa000       \               msvcrt
ELF     7e1fa000-7e227000       Deferred        ws2_32<elf>
  \-PE  7e200000-7e227000       \               ws2_32
ELF     7e227000-7e241000       Deferred        wsock32<elf>
  \-PE  7e230000-7e241000       \               wsock32
ELF     7e241000-7e2e1000       Deferred        oleaut32<elf>
  \-PE  7e250000-7e2e1000       \               oleaut32
ELF     7e2e1000-7e2f5000       Deferred        msimg32<elf>
  \-PE  7e2f0000-7e2f5000       \               msimg32
ELF     7e2f5000-7e32a000       Deferred        winspool<elf>
  \-PE  7e300000-7e32a000       \               winspool
ELF     7e32a000-7e3cb000       Deferred        comdlg32<elf>
  \-PE  7e330000-7e3cb000       \               comdlg32
ELF     7e3cb000-7e3de000       Deferred        libresolv.so.2
ELF     7e3de000-7e3fc000       Deferred        iphlpapi<elf>
  \-PE  7e3f0000-7e3fc000       \               iphlpapi
ELF     7e3fc000-7e455000       Deferred        rpcrt4<elf>
  \-PE  7e410000-7e455000       \               rpcrt4
ELF     7e455000-7e4f6000       Deferred        ole32<elf>
  \-PE  7e460000-7e4f6000       \               ole32
ELF     7e4f6000-7e51d000       Deferred        msvfw32<elf>
  \-PE  7e500000-7e51d000       \               msvfw32
ELF     7e51d000-7e5ab000       Deferred        winmm<elf>
  \-PE  7e530000-7e5ab000       \               winmm
ELF     7e5ab000-7e5d2000       Deferred        msacm32<elf>
  \-PE  7e5b0000-7e5d2000       \               msacm32
ELF     7e5d2000-7e60c000       Deferred        avifil32<elf>
  \-PE  7e5e0000-7e60c000       \               avifil32
ELF     7e60c000-7e62d000       Deferred        mpr<elf>
  \-PE  7e610000-7e62d000       \               mpr
ELF     7e62d000-7e679000       Deferred        wininet<elf>
  \-PE  7e640000-7e679000       \               wininet
ELF     7e679000-7e738000       Export          comctl32<elf>
  \-PE  7e680000-7e738000       \               comctl32
ELF     7e738000-7e790000       Deferred        shlwapi<elf>
  \-PE  7e750000-7e790000       \               shlwapi
ELF     7e790000-7e893000       Deferred        shell32<elf>
  \-PE  7e7a0000-7e893000       \               shell32
ELF     7e893000-7e8a7000       Deferred        shfolder<elf>
  \-PE  7e8a0000-7e8a7000       \               shfolder
ELF     7e8a7000-7e8bd000       Deferred        glu32<elf>
  \-PE  7e8b0000-7e8bd000       \               glu32
ELF     7e8bd000-7e906000       Deferred        advapi32<elf>
  \-PE  7e8d0000-7e906000       \               advapi32
ELF     7e906000-7e9a1000       Deferred        gdi32<elf>
  \-PE  7e920000-7e9a1000       \               gdi32
ELF     7e9a1000-7eadf000       Export          user32<elf>
  \-PE  7e9c0000-7eadf000       \               user32
ELF     7eadf000-7eaea000       Deferred        libgcc_s.so.1
ELF     7ebdd000-7ebe7000       Deferred        libdrm.so.2
ELF     7ebe7000-7ebec000       Deferred        libxfixes.so.3
ELF     7ebec000-7ebef000       Deferred        libxdamage.so.1
ELF     7ebef000-7ebf4000       Deferred        libxdmcp.so.6
ELF     7ebf4000-7ec77000       Deferred        libglu.so.1
ELF     7ec77000-7ecd8000       Deferred        libgl.so.1
ELF     7ecd8000-7edc9000       Deferred        libx11.so.6
ELF     7edc9000-7edd7000       Deferred        libxext.so.6
ELF     7edd7000-7eddc000       Deferred        libxxf86vm.so.1
ELF     7eddc000-7edf4000       Deferred        libice.so.6
ELF     7edf4000-7edfc000       Deferred        libsm.so.6
ELF     7ee0a000-7ee8b000       Deferred        opengl32<elf>
  \-PE  7ee20000-7ee8b000       \               opengl32
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff3000-7eff6000       Deferred        libxau.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d34000-b7d3d000       Deferred        libnss_compat.so.2
ELF     b7d3e000-b7d42000       Deferred        libdl.so.2
ELF     b7d42000-b7e8c000       Deferred        libc.so.6
ELF     b7e8d000-b7ea5000       Deferred        libpthread.so.0
ELF     b7eb3000-b7fc7000       Deferred        libwine.so.1
ELF     b7fc9000-b7fe5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\kevin\Desktop\Chief Architect 10.0 Full Version\Chief Architect 10 Full.exe
        00000009    0 <==

---

