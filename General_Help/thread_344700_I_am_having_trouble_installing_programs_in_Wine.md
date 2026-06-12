---
title: "I am having trouble installing programs in Wine"
date: 2007-01-23
forum: General Help
---

### Post by noalternative on 2007-01-23
I am trying to install myst III with wine and I keep getting errors, and it ultimately fails to install.  Here are the errors I am getting.

[INDENT]oldcomputer@ubuntu:/media/cdrom0$ wine Setup.exe
wine: Unhandled illegal instruction at address 0x7f2a9f3d (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: illegal instruction in 32-bit code (0x7f2a9f3d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f2a9f3d ESP:7fb9ee70 EBP:7fb9ef68 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c028df8 ECX:00000001 EDX:00000001
 ESI:00000000 EDI:00000000
Stack dump:
0x7fb9ee70:  7c028590 7c028df8 7fb9ef20 7fb9ef1c
0x7fb9ee80:  00000001 00000000 00008000 00000000
0x7fb9ee90:  00000000 00000000 00000000 00000000
0x7fb9eea0:  00000000 00000000 00000000 00000000
0x7fb9eeb0:  00008000 00000000 00000000 00000000
0x7fb9eec0:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f2a9f3d glXChooseVisual+0x1ed in libgl.so.1 (0x7f2a9f3d)
  2 0x7f41f013 X11DRV_setup_opengl_visual+0x61 in winex11 (0x7f41f013)
  3 0x7f43005c DllMain+0x1183 in winex11 (0x7f43005c)
  4 0x7f43f442 in winex11 (+0x5f442) (0x7f43f442)
  5 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  6 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  7 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  8 0x7ffa088e LdrLoadDll+0x77 in ntdll (0x7ffa088e)
  9 0x7fc4e016 in kernel32 (+0x3e016) (0x7fc4e016)
  10 0x7fc4e215 LoadLibraryExW+0x4f in kernel32 (0x7fc4e215)
  11 0x7fc4e339 LoadLibraryExA+0x43 in kernel32 (0x7fc4e339)
  12 0x7fc4e370 LoadLibraryA+0x2d in kernel32 (0x7fc4e370)
  13 0x7f82ad21 DRIVER_load_driver+0x1ae in gdi32 (0x7f82ad21)
  14 0x7f826fdb CreateDCW+0x60 in gdi32 (0x7f826fdb)
  15 0x7f8ebc8f CreateIconFromResourceEx+0x42a in user32 (0x7f8ebc8f)
  16 0x7f8ecdf2 in user32 (+0x2cdf2) (0x7f8ecdf2)
  17 0x7f8ed32c LoadImageW+0x408 in user32 (0x7f8ed32c)
  18 0x7f8ed8c4 LoadImageA+0x58 in user32 (0x7f8ed8c4)
  19 0x7f8edb60 LoadCursorA+0x44 in user32 (0x7f8edb60)
  20 0x7f8e24da in user32 (+0x224da) (0x7f8e24da)
  21 0x7f8e2541 CLASS_RegisterBuiltinClasses+0x1d in user32 (0x7f8e2541)
  22 0x7f95532d DllMain+0x105 in user32 (0x7f95532d)
  23 0x7f9689de in user32 (+0xa89de) (0x7f9689de)
  24 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  25 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  26 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  27 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  28 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  29 0x7ffa061f LdrInitializeThunk+0x372 in ntdll (0x7ffa061f)
  30 0x7fc5b2dd in kernel32 (+0x4b2dd) (0x7fc5b2dd)
  31 0xb7f5bddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f5bddb)
0x7f2a9f3d glXChooseVisual+0x1ed in libgl.so.1: cmovna  %edx,%edi
Usage:
        winedbg [ [ --gdb ] [ prog-name [ prog-args ] | <num> | file.mdmp | --help ]
oldcomputer@ubuntu:/media/cdrom0$[/INDENT]

Just to be sure it wasn't just that program I tried to install an old 16 bit opera browser.  This wasn't successful either.

[INDENT]oldcomputer@ubuntu:~$ wine ow36*
wine: Unhandled illegal instruction at address 0x7f508f3d (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: illegal instruction in 32-bit code (0x7f508f3d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f508f3d ESP:7fb8eeb0 EBP:7fb8efa8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c027578 ECX:00000001 EDX:00000001
 ESI:00000000 EDI:00000000
Stack dump:
0x7fb8eeb0:  7c026d10 7c027578 7fb8ef60 7fb8ef5c
0x7fb8eec0:  00000001 00000000 00008000 00000000
0x7fb8eed0:  00000000 00000000 00000000 00000000
0x7fb8eee0:  00000000 00000000 00000000 00000000
0x7fb8eef0:  00008000 00000000 00000000 00000000
0x7fb8ef00:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f508f3d glXChooseVisual+0x1ed in libgl.so.1 (0x7f508f3d)
  2 0x7f68b013 X11DRV_setup_opengl_visual+0x61 in winex11 (0x7f68b013)
  3 0x7f69c05c DllMain+0x1183 in winex11 (0x7f69c05c)
  4 0x7f6ab442 in winex11 (+0x5b442) (0x7f6ab442)
  5 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  6 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  7 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  8 0x7ffa088e LdrLoadDll+0x77 in ntdll (0x7ffa088e)
  9 0x7fc4e016 in kernel32 (+0x3e016) (0x7fc4e016)
  10 0x7fc4e215 LoadLibraryExW+0x4f in kernel32 (0x7fc4e215)
  11 0x7fc4e339 LoadLibraryExA+0x43 in kernel32 (0x7fc4e339)
  12 0x7fc4e370 LoadLibraryA+0x2d in kernel32 (0x7fc4e370)
  13 0x7f8dad21 DRIVER_load_driver+0x1ae in gdi32 (0x7f8dad21)
  14 0x7f8d6fdb CreateDCW+0x60 in gdi32 (0x7f8d6fdb)
  15 0x7f99bc8f CreateIconFromResourceEx+0x42a in user32 (0x7f99bc8f)
  16 0x7f99cdf2 in user32 (+0x2cdf2) (0x7f99cdf2)
  17 0x7f99d32c LoadImageW+0x408 in user32 (0x7f99d32c)
  18 0x7f99d8c4 LoadImageA+0x58 in user32 (0x7f99d8c4)
  19 0x7f99db60 LoadCursorA+0x44 in user32 (0x7f99db60)
  20 0x7f9924da in user32 (+0x224da) (0x7f9924da)
  21 0x7f992541 CLASS_RegisterBuiltinClasses+0x1d in user32 (0x7f992541)
  22 0x7fa0532d DllMain+0x105 in user32 (0x7fa0532d)
  23 0x7fa189de in user32 (+0xa89de) (0x7fa189de)
  24 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  25 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  26 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  27 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  28 0x7ffa061f LdrInitializeThunk+0x372 in ntdll (0x7ffa061f)
  29 0x7fc5b2dd in kernel32 (+0x4b2dd) (0x7fc5b2dd)
  30 0xb7fc1ddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7fc1ddb)
0x7f508f3d glXChooseVisual+0x1ed in libgl.so.1: cmovna  %edx,%edi
Modules:
Module  Address                 Debug info      Name (44 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7f46d000-7f471000     Deferred        libxfixes.so.3
ELF     0x7f471000-7f47a000     Deferred        libxcursor.so.1
ELF     0x7f47a000-7f496000     Deferred        imm32<elf>
  \-PE  0x7f480000-7f496000     \               imm32
ELF     0x7f496000-7f536000     Export          libgl.so.1
ELF     0x7f536000-7f61c000     Deferred        libx11.so.6
ELF     0x7f61c000-7f629000     Deferred        libxext.so.6
ELF     0x7f629000-7f641000     Deferred        libice.so.6
ELF     0x7f641000-7f6c4000     Export          winex11<elf>
  \-PE  0x7f650000-7f6c4000     \               winex11
ELF     0x7f6c4000-7f6e3000     Deferred        libexpat.so.1
ELF     0x7f6e3000-7f711000     Deferred        libfontconfig.so.1
ELF     0x7f711000-7f725000     Deferred        libz.so.1
ELF     0x7f725000-7f78e000     Deferred        libfreetype.so.6
ELF     0x7f78e000-7f7ce000     Deferred        advapi32<elf>
  \-PE  0x7f7a0000-7f7ce000     \               advapi32
ELF     0x7f8a3000-7f954000     Export          gdi32<elf>
  \-PE  0x7f8c0000-7f954000     \               gdi32
ELF     0x7f954000-7fa80000     Export          user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
ELF     0x7fb9b000-7fbb0000     Deferred        winevdm<elf>
  \-PE  0x7fba0000-7fbb0000     \               winevdm
ELF     0x7fbb3000-7fbb6000     Deferred        libxau.so.6
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86vm.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe02000-7fe0c000     Deferred        libgcc_s.so.1
ELF     0x7fe0c000-7fe16000     Deferred        libnss_files.so.2
ELF     0x7fe16000-7fe1f000     Deferred        libnss_nis.so.2
ELF     0x7fe1f000-7fe34000     Deferred        libnsl.so.1
ELF     0x7fe34000-7fe3d000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e6d000-b7e70000     Deferred        libdl.so.2
ELF     0xb7e70000-b7f9f000     Deferred        libc.so.6
ELF     0xb7f9f000-b7fb0000     Deferred        libpthread.so.0
ELF     0xb7fbd000-b7fd7000     Export          libwine.so.1
ELF     0xb7fd9000-b7fef000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winevdm.exe
        00000009    0 <==
oldcomputer@ubuntu:~$[/INDENT]

I have no idea what the problem is and I don't know how to begin to solve it.](*,)

---

### Post by pizzutz on 2007-01-23
Is this your first time using wine?
did you run winecfg to set up the directory tree?
have you gotten any apps to install with wine?


[http://appdb.winehq.org/appview.php?iVersionId=1820](http://appdb.winehq.org/appview.php?iVersionId=1820)

contains some known issues with Myst III although it looks like you are running into problems with wine in general.

---

### Post by noalternative on 2007-01-23
> **pizzutz said:**
> Is this your first time using wine?
did you run winecfg to set up the directory tree?
have you gotten any apps to install with wine?


[http://appdb.winehq.org/appview.php?iVersionId=1820](http://appdb.winehq.org/appview.php?iVersionId=1820)

contains some known issues with Myst III although it looks like you are running into problems with wine in general.

Yes, it is my first time.  I ran winecfg. I guess it is suppose to be a gui configuration tool, but no gui came up.  Just characters in the terminal.
[INDENT]oldcomputer@ubuntu:~$ winecfg
wine: Unhandled illegal instruction at address 0x7f073f3d (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: illegal instruction in 32-bit code (0x7f073f3d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f073f3d ESP:7fb4edb0 EBP:7fb4eea8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c029ee0 ECX:00000001 EDX:00000001
 ESI:00000000 EDI:00000000
Stack dump:
0x7fb4edb0:  7c029678 7c029ee0 7fb4ee60 7fb4ee5c
0x7fb4edc0:  00000001 00000000 00008000 00000000
0x7fb4edd0:  00000000 00000000 00000000 00000000
0x7fb4ede0:  00000000 00000000 00000000 00000000
0x7fb4edf0:  00008000 00000000 00000000 00000000
0x7fb4ee00:  00000000 00000000 00000000 00000000
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f073f3d glXChooseVisual+0x1ed in libgl.so.1 (0x7f073f3d)
  2 0x7f1e9013 X11DRV_setup_opengl_visual+0x61 in winex11 (0x7f1e9013)
  3 0x7f1fa05c DllMain+0x1183 in winex11 (0x7f1fa05c)
  4 0x7f209442 in winex11 (+0x59442) (0x7f209442)
  5 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  6 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  7 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  8 0x7ffa088e LdrLoadDll+0x77 in ntdll (0x7ffa088e)
  9 0x7fc4e016 in kernel32 (+0x3e016) (0x7fc4e016)
  10 0x7fc4e215 LoadLibraryExW+0x4f in kernel32 (0x7fc4e215)
  11 0x7fc4e339 LoadLibraryExA+0x43 in kernel32 (0x7fc4e339)
  12 0x7fc4e370 LoadLibraryA+0x2d in kernel32 (0x7fc4e370)
  13 0x7f605d21 DRIVER_load_driver+0x1ae in gdi32 (0x7f605d21)
  14 0x7f601fdb CreateDCW+0x60 in gdi32 (0x7f601fdb)
  15 0x7f6c6c8f CreateIconFromResourceEx+0x42a in user32 (0x7f6c6c8f)
  16 0x7f6c7df2 in user32 (+0x27df2) (0x7f6c7df2)
  17 0x7f6c832c LoadImageW+0x408 in user32 (0x7f6c832c)
  18 0x7f6c88c4 LoadImageA+0x58 in user32 (0x7f6c88c4)
  19 0x7f6c8b60 LoadCursorA+0x44 in user32 (0x7f6c8b60)
  20 0x7f6bd4da in user32 (+0x1d4da) (0x7f6bd4da)
  21 0x7f6bd541 CLASS_RegisterBuiltinClasses+0x1d in user32 (0x7f6bd541)
  22 0x7f73032d DllMain+0x105 in user32 (0x7f73032d)
  23 0x7f7439de in user32 (+0xa39de) (0x7f7439de)
  24 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  25 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  26 0x7ff9d7fa in ntdll (+0x1d7fa) (0x7ff9d7fa)
  27 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  28 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  29 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  30 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  31 0x7ff9d7ce in ntdll (+0x1d7ce) (0x7ff9d7ce)
  32 0x7ffa061f LdrInitializeThunk+0x372 in ntdll (0x7ffa061f)
  33 0x7fc5b2dd in kernel32 (+0x4b2dd) (0x7fc5b2dd)
  34 0xb7f9fddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f9fddb)
0x7f073f3d glXChooseVisual+0x1ed in libgl.so.1: cmovna  %edx,%edi
Modules:
Module  Address                 Debug info      Name (64 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7efd0000-7efd4000     Deferred        libxfixes.so.3
ELF     0x7efd4000-7efdd000     Deferred        libxcursor.so.1
ELF     0x7efdd000-7efe5000     Deferred        libxrender.so.1
ELF     0x7efe5000-7f001000     Deferred        imm32<elf>
  \-PE  0x7eff0000-7f001000     \               imm32
ELF     0x7f001000-7f0a1000     Export          libgl.so.1
ELF     0x7f0a1000-7f187000     Deferred        libx11.so.6
ELF     0x7f187000-7f19f000     Deferred        libice.so.6
ELF     0x7f19f000-7f222000     Export          winex11<elf>
  \-PE  0x7f1b0000-7f222000     \               winex11
ELF     0x7f222000-7f241000     Deferred        libexpat.so.1
ELF     0x7f241000-7f26f000     Deferred        libfontconfig.so.1
ELF     0x7f26f000-7f283000     Deferred        libz.so.1
ELF     0x7f283000-7f2ec000     Deferred        libfreetype.so.6
ELF     0x7f2ec000-7f31d000     Deferred        uxtheme<elf>
  \-PE  0x7f2f0000-7f31d000     \               uxtheme
ELF     0x7f31d000-7f3a5000     Deferred        winmm<elf>
  \-PE  0x7f330000-7f3a5000     \               winmm
ELF     0x7f3a5000-7f3d1000     Deferred        winspool<elf>
  \-PE  0x7f3b0000-7f3d1000     \               winspool
ELF     0x7f3d1000-7f491000     Deferred        comctl32<elf>
  \-PE  0x7f3e0000-7f491000     \               comctl32
ELF     0x7f491000-7f4b0000     Deferred        iphlpapi<elf>
  \-PE  0x7f4a0000-7f4b0000     \               iphlpapi
ELF     0x7f4b0000-7f4f9000     Deferred        rpcrt4<elf>
  \-PE  0x7f4c0000-7f4f9000     \               rpcrt4
ELF     0x7f5ce000-7f67f000     Export          gdi32<elf>
  \-PE  0x7f5e0000-7f67f000     \               gdi32
ELF     0x7f67f000-7f7ab000     Export          user32<elf>
  \-PE  0x7f6a0000-7f7ab000     \               user32
ELF     0x7f7ab000-7f7eb000     Deferred        advapi32<elf>
  \-PE  0x7f7c0000-7f7eb000     \               advapi32
ELF     0x7f7eb000-7f87c000     Deferred        ole32<elf>
  \-PE  0x7f800000-7f87c000     \               ole32
ELF     0x7f87c000-7f8d7000     Deferred        shlwapi<elf>
  \-PE  0x7f890000-7f8d7000     \               shlwapi
ELF     0x7f8d7000-7f9a3000     Deferred        shell32<elf>
  \-PE  0x7f8f0000-7f9a3000     \               shell32
ELF     0x7f9a3000-7fa40000     Deferred        comdlg32<elf>
  \-PE  0x7f9b0000-7fa40000     \               comdlg32
ELF     0x7fb50000-7fb5d000     Deferred        libxext.so.6
ELF     0x7fb5d000-7fbb0000     Deferred        winecfg<elf>
  \-PE  0x7fb70000-7fbb0000     \               winecfg
ELF     0x7fbb3000-7fbb6000     Deferred        libxau.so.6
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86vm.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe02000-7fe0c000     Deferred        libgcc_s.so.1
ELF     0x7fe0c000-7fe16000     Deferred        libnss_files.so.2
ELF     0x7fe16000-7fe1f000     Deferred        libnss_nis.so.2
ELF     0x7fe1f000-7fe34000     Deferred        libnsl.so.1
ELF     0x7fe34000-7fe3d000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e4b000-b7e4e000     Deferred        libdl.so.2
ELF     0xb7e4e000-b7f7d000     Deferred        libc.so.6
ELF     0xb7f7d000-b7f8e000     Deferred        libpthread.so.0
ELF     0xb7f9b000-b7fb5000     Export          libwine.so.1
ELF     0xb7fb7000-b7fcd000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==
oldcomputer@ubuntu:~$:confused:
[/INDENT]

---

### Post by pizzutz on 2007-01-23
What Version of wine are you running?  
Did you install the package, or did you compile from source?

---

### Post by noalternative on 2007-01-23
Wine 0.9.9 installed from the ubuntu package.

---

### Post by Enverex on 2007-01-23
Update, you're 20 versions behind the current one. If you can't run Winecfg then it also means that your machine is broken in one way or another (but I'd update first to eliminate any other issues).

---

### Post by noalternative on 2007-01-23
> **Enverex said:**
> Update, you're 20 versions behind the current one. If you can't run Winecfg then it also means that your machine is broken in one way or another (but I'd update first to eliminate any other issues).

I tried the most recent version from the wine repositories and got the same errors.

---

