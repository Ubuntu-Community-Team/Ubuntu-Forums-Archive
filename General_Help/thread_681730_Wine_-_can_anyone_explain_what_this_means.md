---
title: "Wine - can anyone explain what this means?"
date: 2008-01-29
forum: General Help
---

### Post by thered on 2008-01-29
I'm trying to get a photo imaging program to run in Wine.  It's ebuyer's own photopaint -a lot like paint shop pro ver6 and I think I would prefer the interface to GIMP (Sorry GIMP fans

It seemed to install ok apart from this:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

 when I try and run it get the following output in terminal:

err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABTool.dll") not found
err:module:import_dll Library ABTool.dll (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABTool.dll") not found
err:module:import_dll Library ABTool.dll (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABShare.DLL") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABShare.DLL") not found
err:module:import_dll Library ABShare.DLL (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Ebuyer Photo Paint\\ABPhoto.exe" failed, status c0000135

ABTool.dll and ABShare.dll are there but the extension on the latter is lowercase. The others, obviously windoze files, aren't in the installation folder nor in any of the other Wine folders, e.g. system32.

What I really want to know 'Is it worth persevering with? - or would I be better spending my time getting used to GIMP :)

---

### Post by zvacet on 2008-01-29
You can find missing dll [here](http://www.dll-files.com/).

---

### Post by thered on 2008-01-29
Nope -put them installation folder and system 32

Now getting this:

0000001d (D) C:\Program Files\Ebuyer Photo Paint\ABPhoto.exe
        0000001e    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
wine: Call from 0x1000d53a to unimplemented function MFC42.DLL.6571, aborting
wine: Call from 0x1000d53a to unimplemented function MFC42.DLL.6571, aborting
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
wine: Call from 0x1000d53a to unimplemented function MFC42.DLL.6571, aborting
wine: Unimplemented function MFC42.DLL.6571 called at address 0x1000d53a (thread 0022), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6571 called in 32-bit code (0x7bc42cfc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc42cfc ESP:0034fc78 EBP:0034fcdc EFLAGS:00000206(   - 00      - -IP1)
 EAX:000019ab EBX:7bc8443c ECX:00000080 EDX:00110024
 ESI:0034fc84 EDI:100710ac
Stack dump:
0x0034fc78:  00129670 00129a00 00000000 80000100
0x0034fc88:  00000001 00000000 1000d53a 00000002
0x0034fc98:  1005894c 000019ab 00129670 7bc320df
0x0034fca8:  001295d8 7bc8443c 0034fd10 7bc40e45
0x0034fcb8:  00110020 7eabbec6 00000000 00000001
0x0034fcc8:  00000000 00000000 7eac3168 7ee39fc4
Backtrace:
=>1 0x7bc42cfc stub_entry_point+0x4c(dll=0x1005894c, name=0x19ab) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll (0x0034fcdc)
  2 0x1000d53a in abtool (+0xd53a) (0x0034fd2c)
  3 0x10048710 in abtool (+0x48710) (0x0034fd58)
  4 0x7bc41cf5 call_dll_entry_point+0x15() in ntdll (0x0034fd78)
  5 0x7bc436bd MODULE_InitDLL+0x8d(wm=<register EDI not in topmost frame>, reason=<register ESI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:890] in ntdll (0x0034fe08)
  6 0x7bc43d14 process_attach+0x174(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:963] in ntdll (0x0034fe58)
  7 0x7bc43c42 process_attach+0xa2(wm=<register EDI not in topmost frame>, lpReserved=0x1) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:955] in ntdll (0x0034fea8)
  8 0x7bc467c6 LdrInitializeThunk+0x2b6(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:2316] in ntdll (0x0034ff08)
  9 0x7b874c4a start_process+0xba(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:829] in kernel32 (0x0034ffe8)
  10 0xb7eb99d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc42cfc stub_entry_point+0x4c [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:189] in ntdll: subl     $4,%esp
Unable to open file '/build/buildd/wine-0.9.46/dlls/ntdll/loader.c'
Modules:
Module  Address                 Debug info      Name (76 modules)
PE        360000-  3c4000       Deferred        abshare
PE        400000-  47a000       Deferred        abphoto
PE      10000000-1007b000       Export          abtool
PE      5f400000-5f4ed000       Deferred        mfc42
PE      780a0000-780b5000       Deferred        msvcirt
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e22b000-7e240000       Deferred        midimap<elf>
  \-PE  7e230000-7e240000       \               midimap
ELF     7e240000-7e267000       Deferred        msacm32<elf>
  \-PE  7e250000-7e267000       \               msacm32
ELF     7e267000-7e27f000       Deferred        msacm32<elf>
  \-PE  7e270000-7e27f000       \               msacm32
ELF     7e27f000-7e2b9000       Deferred        wineoss<elf>
  \-PE  7e290000-7e2b9000       \               wineoss
ELF     7e2b9000-7e2eb000       Deferred        uxtheme<elf>
  \-PE  7e2c0000-7e2eb000       \               uxtheme
ELF     7e375000-7e37e000       Deferred        libxcursor.so.1
ELF     7e37e000-7e39b000       Deferred        imm32<elf>
  \-PE  7e390000-7e39b000       \               imm32
ELF     7e39b000-7e3a3000       Deferred        libxrender.so.1
ELF     7e3b1000-7e451000       Deferred        libgl.so.1
ELF     7e451000-7e456000       Deferred        libxdmcp.so.6
ELF     7e456000-7e547000       Deferred        libx11.so.6
ELF     7e547000-7e555000       Deferred        libxext.so.6
ELF     7e555000-7e55a000       Deferred        libxxf86vm.so.1
ELF     7e55a000-7e572000       Deferred        libice.so.6
ELF     7e572000-7e57a000       Deferred        libsm.so.6
ELF     7e57d000-7e582000       Deferred        libxfixes.so.3
ELF     7e582000-7e588000       Deferred        libxrandr.so.2
ELF     7e588000-7e613000       Deferred        winex11<elf>
  \-PE  7e5a0000-7e613000       \               winex11
ELF     7e68a000-7e6aa000       Deferred        libexpat.so.1
ELF     7e6aa000-7e6d5000       Deferred        libfontconfig.so.1
ELF     7e6d5000-7e6ea000       Deferred        libz.so.1
ELF     7e6ea000-7e75a000       Deferred        libfreetype.so.6
ELF     7e75a000-7e7f8000       Deferred        oleaut32<elf>
  \-PE  7e770000-7e7f8000       \               oleaut32
ELF     7e7f8000-7e80b000       Deferred        libresolv.so.2
ELF     7e80b000-7e829000       Deferred        iphlpapi<elf>
  \-PE  7e810000-7e829000       \               iphlpapi
ELF     7e829000-7e882000       Deferred        rpcrt4<elf>
  \-PE  7e840000-7e882000       \               rpcrt4
ELF     7e882000-7e923000       Deferred        ole32<elf>
  \-PE  7e890000-7e923000       \               ole32
ELF     7e923000-7e97c000       Deferred        shlwapi<elf>
  \-PE  7e930000-7e97c000       \               shlwapi
ELF     7e97c000-7ea7f000       Deferred        shell32<elf>
  \-PE  7e990000-7ea7f000       \               shell32
ELF     7ea7f000-7eb0d000       Deferred        winmm<elf>
  \-PE  7ea90000-7eb0d000       \               winmm
ELF     7eb0d000-7ebcb000       Deferred        comctl32<elf>
  \-PE  7eb20000-7ebcb000       \               comctl32
ELF     7ebcb000-7ed09000       Deferred        user32<elf>
  \-PE  7ebf0000-7ed09000       \               user32
ELF     7ed09000-7ed52000       Deferred        advapi32<elf>
  \-PE  7ed20000-7ed52000       \               advapi32
ELF     7ed52000-7eded000       Deferred        gdi32<elf>
  \-PE  7ed70000-7eded000       \               gdi32
ELF     7eded000-7ee55000       Deferred        msvcrt<elf>
  \-PE  7ee00000-7ee55000       \               msvcrt
ELF     7ee74000-7ee7f000       Deferred        libnss_files.so.2
ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1
ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2
ELF     7eea0000-7eea3000       Deferred        libxau.so.6
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d3d000-b7d41000       Deferred        libdl.so.2
ELF     b7d41000-b7e8b000       Deferred        libc.so.6
ELF     b7e8c000-b7ea4000       Deferred        libpthread.so.0
ELF     b7eb2000-b7fc6000       Dwarf           libwine.so.1
ELF     b7fc8000-b7fe4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000021 (D) C:\Program Files\Ebuyer Photo Paint\ABPhoto.exe
        00000022    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0
wine: Call from 0x1000d53a to unimplemented function MFC42.DLL.6571, aborting

So I'm totally at a loss. Going to assume it won't run unless someone can help.

---

### Post by haydent on 2008-07-19
> Invalid.  Wine doesn't ship with mfc42.dll, so you must have copied a native
version from somewhere, and the version you copied does not have the function
that's being called.  I just tried the app with mfc42.dll from dlldump, and it
worked fine.

[http://www.winehq.org/pipermail/wine-bugs/2006-September/038872.html](http://www.winehq.org/pipermail/wine-bugs/2006-September/038872.html)

i initially had dlls  from dll-files.com but had same error...

dlldump has the goods to boot :)

---

