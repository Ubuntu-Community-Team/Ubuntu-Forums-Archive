---
title: "wine does not work with openchrome video driver"
date: 2008-01-23
forum: General Help
---

### Post by hdoria on 2008-01-23
Hi,

I can not run wine, winecfg and none apps that needs wine when im using the openchrome video driver.

I installed  xserver-xorg-video-openchrome using apt. Everything else works.

xserver-xorg-video-unichrome and xserver-xorg-video-via does not work (x does not start)

Heres my card:

```
$ lspci | grep -i vga
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)
```

Error when i try to run winecfg (and all wine apps):

```
$ winecfg
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d17583 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d17583).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d17583 ESP:0034eccc EBP:0034ece8 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7decff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x0034eccc:  b7d172c5 00000000 00000048 00000048
0x0034ecdc:  7e5a7588 00000033 7e5ac358 0034ed78
0x0034ecec:  7e570d1c 00000000 00000048 7c0296a8
0x0034ecfc:  00000001 00000000 00000001 bfa81048
0x0034ed0c:  081572e7 08755078 7c0296a8 7c026298
0x0034ed1c:  00000048 00000000 7c042220 0034ee78
Backtrace:
=>1 0xb7d17583 strlen+0x33() in libc.so.6 (0x0034ece8)
  2 0x7e570d1c in winex11 (+0x40d1c) (0x0034ed78)
  3 0x7e573a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034ee78)
  4 0x7e583510 in winex11 (+0x53510) (0x0034f058)
  5 0x7e594178 in winex11 (+0x64178) (0x0034f078)
  6 0x7bc42e95 call_dll_entry_point+0x15() in ntdll (0x0034f098)
  7 0x7bc45352 in ntdll (+0x35352) (0x0034f128)
  8 0x7bc455ec in ntdll (+0x355ec) (0x0034f168)
  9 0x7bc47c7b LdrLoadDll+0x67() in ntdll (0x0034f188)
  10 0x7b8623c2 in kernel32 (+0x423c2) (0x0034f3f8)
  11 0x7b86269b LoadLibraryExW+0x43() in kernel32 (0x0034f418)
  12 0x7b86277a LoadLibraryExA+0x43() in kernel32 (0x0034f438)
  13 0x7b8627b1 LoadLibraryA+0x2d() in kernel32 (0x0034f458)
  14 0x7ea65bfd in gdi32 (+0x25bfd) (0x0034f5e8)
  15 0x7ea5f928 CreateDCW+0x60() in gdi32 (0x0034f898)
  16 0x7eb0ce05 CreateIconFromResourceEx+0x6c1() in user32 (0x0034f968)
  17 0x7eb0d3c4 in user32 (+0x2d3c4) (0x0034f9d8)
  18 0x7eb0fd3a LoadImageW+0x45f() in user32 (0x0034fa78)
  19 0x7eb10528 LoadImageA+0x1c0() in user32 (0x0034fb78)
  20 0x7eb106da LoadCursorA+0x55() in user32 (0x0034fba8)
  21 0x7eb0486e in user32 (+0x2486e) (0x0034fbd8)
  22 0x7eb048c1 in user32 (+0x248c1) (0x0034fbf8)
  23 0x7eb79c82 in user32 (+0x99c82) (0x0034fca8)
  24 0x7eb8d69c in user32 (+0xad69c) (0x0034fcc8)
  25 0x7bc42e95 call_dll_entry_point+0x15() in ntdll (0x0034fce8)
  26 0x7bc45352 in ntdll (+0x35352) (0x0034fd78)
  27 0x7bc455ec in ntdll (+0x355ec) (0x0034fdb8)
  28 0x7bc45671 in ntdll (+0x35671) (0x0034fdf8)
  29 0x7bc45671 in ntdll (+0x35671) (0x0034fe38)
  30 0x7bc45671 in ntdll (+0x35671) (0x0034fe78)
  31 0x7bc45671 in ntdll (+0x35671) (0x0034feb8)
  32 0x7bc47f77 LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  33 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  34 0xb7e1f1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d17583 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (62 modules)
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e14c000-7e376000       Deferred        unichrome_dri.so
ELF     7e376000-7e380000       Deferred        libdrm.so.2
ELF     7e380000-7e385000       Deferred        libxfixes.so.3
ELF     7e385000-7e388000       Deferred        libxdamage.so.1
ELF     7e388000-7e3e9000       Deferred        libgl.so.1
ELF     7e3e9000-7e3ee000       Deferred        libxdmcp.so.6
ELF     7e3ee000-7e3f1000       Deferred        libxau.so.6
ELF     7e3f1000-7e4e2000       Deferred        libx11.so.6
ELF     7e4e2000-7e4f0000       Deferred        libxext.so.6
ELF     7e4f0000-7e4f5000       Deferred        libxxf86vm.so.1
ELF     7e4f5000-7e50d000       Deferred        libice.so.6
ELF     7e50d000-7e515000       Deferred        libsm.so.6
ELF     7e523000-7e5ad000       Export          winex11<elf>
  \-PE  7e530000-7e5ad000       \               winex11
ELF     7e62a000-7e64a000       Deferred        libexpat.so.1
ELF     7e64a000-7e675000       Deferred        libfontconfig.so.1
ELF     7e675000-7e68a000       Deferred        libz.so.1
ELF     7e68a000-7e6fa000       Deferred        libfreetype.so.6
ELF     7e6fa000-7e72c000       Deferred        uxtheme<elf>
  \-PE  7e700000-7e72c000       \               uxtheme
ELF     7e72c000-7e7b8000       Deferred        winmm<elf>
  \-PE  7e740000-7e7b8000       \               winmm
ELF     7e7b8000-7e7cb000       Deferred        libresolv.so.2
ELF     7e7d9000-7e7f8000       Deferred        iphlpapi<elf>
  \-PE  7e7e0000-7e7f8000       \               iphlpapi
ELF     7e7f8000-7e855000       Deferred        rpcrt4<elf>
  \-PE  7e800000-7e855000       \               rpcrt4
ELF     7e855000-7e8f4000       Deferred        ole32<elf>
  \-PE  7e860000-7e8f4000       \               ole32
ELF     7e8f4000-7e929000       Deferred        winspool<elf>
  \-PE  7e900000-7e929000       \               winspool
ELF     7e929000-7e9e8000       Deferred        comctl32<elf>
  \-PE  7e930000-7e9e8000       \               comctl32
ELF     7e9e8000-7ea31000       Deferred        advapi32<elf>
  \-PE  7e9f0000-7ea31000       \               advapi32
ELF     7ea31000-7eac8000       Export          gdi32<elf>
  \-PE  7ea40000-7eac8000       \               gdi32
ELF     7eac8000-7ebff000       Export          user32<elf>
  \-PE  7eae0000-7ebff000       \               user32
ELF     7ebff000-7ec56000       Deferred        shlwapi<elf>
  \-PE  7ec10000-7ec56000       \               shlwapi
ELF     7ec56000-7ed5a000       Deferred        shell32<elf>
  \-PE  7ec70000-7ed5a000       \               shell32
ELF     7ed5a000-7edfa000       Deferred        comdlg32<elf>
  \-PE  7ed60000-7edfa000       \               comdlg32
ELF     7ee15000-7ee81000       Deferred        winecfg<elf>
  \-PE  7ee20000-7ee81000       \               winecfg
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca3000-b7ca7000       Deferred        libdl.so.2
ELF     b7ca7000-b7df1000       Export          libc.so.6
ELF     b7df2000-b7e0a000       Deferred        libpthread.so.0
ELF     b7e18000-b7f2c000       Export          libwine.so.1
ELF     b7f2e000-b7f4a000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\winecfg.exe
        00000009    0 <==
Backtrace:
=>1 0xb7d17583 strlen+0x33() in libc.so.6 (0x0034ece8)
  2 0x7e570d1c in winex11 (+0x40d1c) (0x0034ed78)
  3 0x7e573a66 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0034ee78)
  4 0x7e583510 in winex11 (+0x53510) (0x0034f058)
  5 0x7e594178 in winex11 (+0x64178) (0x0034f078)
  6 0x7bc42e95 call_dll_entry_point+0x15() in ntdll (0x0034f098)
  7 0x7bc45352 in ntdll (+0x35352) (0x0034f128)
  8 0x7bc455ec in ntdll (+0x355ec) (0x0034f168)
  9 0x7bc47c7b LdrLoadDll+0x67() in ntdll (0x0034f188)
  10 0x7b8623c2 in kernel32 (+0x423c2) (0x0034f3f8)
  11 0x7b86269b LoadLibraryExW+0x43() in kernel32 (0x0034f418)
  12 0x7b86277a LoadLibraryExA+0x43() in kernel32 (0x0034f438)
  13 0x7b8627b1 LoadLibraryA+0x2d() in kernel32 (0x0034f458)
  14 0x7ea65bfd in gdi32 (+0x25bfd) (0x0034f5e8)
  15 0x7ea5f928 CreateDCW+0x60() in gdi32 (0x0034f898)
  16 0x7eb0ce05 CreateIconFromResourceEx+0x6c1() in user32 (0x0034f968)
  17 0x7eb0d3c4 in user32 (+0x2d3c4) (0x0034f9d8)
  18 0x7eb0fd3a LoadImageW+0x45f() in user32 (0x0034fa78)
  19 0x7eb10528 LoadImageA+0x1c0() in user32 (0x0034fb78)
  20 0x7eb106da LoadCursorA+0x55() in user32 (0x0034fba8)
  21 0x7eb0486e in user32 (+0x2486e) (0x0034fbd8)
  22 0x7eb048c1 in user32 (+0x248c1) (0x0034fbf8)
  23 0x7eb79c82 in user32 (+0x99c82) (0x0034fca8)
  24 0x7eb8d69c in user32 (+0xad69c) (0x0034fcc8)
  25 0x7bc42e95 call_dll_entry_point+0x15() in ntdll (0x0034fce8)
  26 0x7bc45352 in ntdll (+0x35352) (0x0034fd78)
  27 0x7bc455ec in ntdll (+0x355ec) (0x0034fdb8)
  28 0x7bc45671 in ntdll (+0x35671) (0x0034fdf8)
  29 0x7bc45671 in ntdll (+0x35671) (0x0034fe38)
  30 0x7bc45671 in ntdll (+0x35671) (0x0034fe78)
  31 0x7bc45671 in ntdll (+0x35671) (0x0034feb8)
  32 0x7bc47f77 LdrInitializeThunk+0x27a() in ntdll (0x0034ff08)
  33 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  34 0xb7e1f1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

Any sugestions?

---

### Post by Liam-Gorham on 2008-01-24
try downloading it from the add/remove application it should automaticaly install itself. Hopefully it should work.

---

