---
title: "wine quit working for FoxitReader.exe today"
date: 2007-06-02
forum: General Help
---

### Post by futz on 2007-06-02
I dislike all the linux pdf readers, so I use the old version of FoxitReader.exe with Wine. I'm running Edgy on this machine.

It has always worked fine. Worked fine last night.

Today I did some (suggested) updates and later when I went to read a pdf, foxit won't start. I wonder what changed in wine? QuickPar still works fine with wine.

Absolutely nothing has changed on my computer except those updates.

Here's the error I'm getting:
```
futz@xblade:~$ wine /home/futz/FoxitReader.exe
wine: Call from 0x7b8411e0 to unimplemented function gdiplus.dll.GdiplusStartup, aborting
wine: Unimplemented function gdiplus.dll.GdiplusStartup called at address 0x7b8411e0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function gdiplus.dll.GdiplusStartup called in 32-bit code (0x7b841258).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841258 ESP:0033fc2c EBP:0033fc90 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82be0d EBX:7b8ad880 ECX:00000000 EDX:00627570
 ESI:00627570 EDI:00627450
Stack dump:
0x0033fc2c:  0033fcb4 00000008 7cc3a0e8 7cc20000
0x0033fc3c:  80000100 00000001 00000000 7b8411e0
0x0033fc4c:  00000002 7cc34550 7cc37b92 7bc3a9bd
0x0033fc5c:  7bc83424 ffffffff 00000000 0033fc84
0x0033fc6c:  7b863150 0033fc84 7bc83424 7bc4ef2c
0x0033fc7c:  00602524 0033fcd0 00004e48 7b8ad880
Backtrace:
=>1 0x7b841258 RaiseException+0x78() in kernel32 (0x0033fc90)
  2 0x7cc344f1 in gdiplus (+0x144f1) (0x0033fcc0)
  3 0x7cc3429b in gdiplus (+0x1429b) (0x00000048)
  4 0x00000000 (0x00000000)
0x7b841258 RaiseException+0x78 in kernel32: movl        0xfffffffc(%ebp),%ebx
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  6cb000       Deferred        foxitreader
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cc1d000-7cc3f000       Export          gdiplus<elf>
  \-PE  7cc20000-7cc3f000       \               gdiplus
ELF     7cc99000-7cce7000       Deferred        libgcrypt.so.11
ELF     7cce7000-7ccfa000       Deferred        libtasn1.so.3
ELF     7ccfa000-7cd28000       Deferred        libcrypt.so.1
ELF     7cd41000-7cdb0000       Deferred        libgnutls.so.13
ELF     7cdb0000-7cddf000       Deferred        libcups.so.2
ELF     7ceb8000-7ceea000       Deferred        uxtheme<elf>
  \-PE  7cec0000-7ceea000       \               uxtheme
ELF     7d184000-7d188000       Deferred        libgpg-error.so.0
ELF     7d18a000-7d18f000       Deferred        libxfixes.so.3
ELF     7d18f000-7d198000       Deferred        libxcursor.so.1
ELF     7d198000-7d1b5000       Deferred        imm32<elf>
  \-PE  7d1a0000-7d1b5000       \               imm32
ELF     7d1b5000-7d1d3000       Deferred        ximcp.so.2
ELF     7d1d3000-7d1d5000       Deferred        xlcutf8load.so.2
ELF     7d1d5000-7d1d8000       Deferred        libxrandr.so.2
ELF     7d1d8000-7d1e0000       Deferred        libxrender.so.1
ELF     7d1e0000-7d1e3000       Deferred        libxinerama.so
ELF     7d97e000-7e2ef000       Deferred        libglcore.so.1
ELF     7e2ef000-7e383000       Deferred        libgl.so.1
ELF     7e383000-7e388000       Deferred        libxdmcp.so.6
ELF     7e388000-7e451000       Deferred        libx11.so.6
ELF     7e451000-7e45e000       Deferred        libxext.so.6
ELF     7e45e000-7e476000       Deferred        libice.so.6
ELF     7e476000-7e47f000       Deferred        libsm.so.6
ELF     7e47f000-7e50e000       Deferred        winex11<elf>
  \-PE  7e490000-7e50e000       \               winex11
ELF     7e50e000-7e52c000       Deferred        libexpat.so.1
ELF     7e52c000-7e55b000       Deferred        libfontconfig.so.1
ELF     7e55b000-7e56f000       Deferred        libz.so.1
ELF     7e56f000-7e5d9000       Deferred        libfreetype.so.6
ELF     7e5d9000-7e605000       Deferred        ws2_32<elf>
  \-PE  7e5e0000-7e605000       \               ws2_32
ELF     7e605000-7e61f000       Deferred        wsock32<elf>
  \-PE  7e610000-7e61f000       \               wsock32
ELF     7e61f000-7e63f000       Deferred        mpr<elf>
  \-PE  7e630000-7e63f000       \               mpr
ELF     7e63f000-7e688000       Deferred        wininet<elf>
  \-PE  7e650000-7e688000       \               wininet
ELF     7e688000-7e722000       Deferred        oleaut32<elf>
  \-PE  7e6a0000-7e722000       \               oleaut32
ELF     7e722000-7e735000       Deferred        libresolv.so.2
ELF     7e737000-7e73a000       Deferred        libxau.so.6
ELF     7e73a000-7e74e000       Deferred        olepro32<elf>
  \-PE  7e740000-7e74e000       \               olepro32
ELF     7e74e000-7e76c000       Deferred        iphlpapi<elf>
  \-PE  7e760000-7e76c000       \               iphlpapi
ELF     7e76c000-7e7c1000       Deferred        rpcrt4<elf>
  \-PE  7e780000-7e7c1000       \               rpcrt4
ELF     7e7c1000-7e85f000       Deferred        ole32<elf>
  \-PE  7e7d0000-7e85f000       \               ole32
ELF     7e85f000-7e881000       Deferred        oledlg<elf>
  \-PE  7e870000-7e881000       \               oledlg
ELF     7e881000-7e8b4000       Deferred        winspool<elf>
  \-PE  7e890000-7e8b4000       \               winspool
ELF     7e8b4000-7e971000       Deferred        comctl32<elf>
  \-PE  7e8c0000-7e971000       \               comctl32
ELF     7e971000-7e9ca000       Deferred        shlwapi<elf>
  \-PE  7e980000-7e9ca000       \               shlwapi
ELF     7e9ca000-7eac6000       Deferred        shell32<elf>
  \-PE  7e9e0000-7eac6000       \               shell32
ELF     7eac6000-7eb67000       Deferred        comdlg32<elf>
  \-PE  7ead0000-7eb67000       \               comdlg32
ELF     7eb67000-7ebae000       Deferred        advapi32<elf>
  \-PE  7eb70000-7ebae000       \               advapi32
ELF     7ec8d000-7ed48000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed48000       \               gdi32
ELF     7ed48000-7ee83000       Deferred        user32<elf>
  \-PE  7ed60000-7ee83000       \               user32
ELF     7ef8d000-7ef98000       Deferred        libnss_files.so.2
ELF     7ef98000-7efa2000       Deferred        libnss_nis.so.2
ELF     7efa2000-7efb8000       Deferred        libnsl.so.1
ELF     7efb8000-7efc1000       Deferred        libnss_compat.so.2
ELF     7efc1000-7efe7000       Deferred        libm.so.6
ELF     7efe7000-7efe9000       Deferred        libnvidia-tls.so.1
ELF     7efe9000-7efee000       Deferred        libxxf86vm.so.1
ELF     7efee000-7eff9000       Deferred        libgcc_s.so.1
ELF     b7d32000-b7d36000       Deferred        libdl.so.2
ELF     b7d36000-b7e6a000       Deferred        libc.so.6
ELF     b7e6b000-b7e7e000       Deferred        libpthread.so.0
ELF     b7e97000-b7fab000       Deferred        libwine.so.1
ELF     b7fad000-b7fc8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\futz\FoxitReader.exe
        00000009    0 <==

```

---

### Post by thelinuxguy on 2007-06-03
No idea about the above....but Foxit has got a Linux version. However, it 'segfault'ed when I tried it. Worth a try?

---

### Post by futz on 2007-06-03
> **thelinuxguy said:**
> No idea about the above....but Foxit has got a Linux version. However, it 'segfault'ed when I tried it. Worth a try?
Ya, I tried that thing a while back. It was buggy and horrible and useless then. I wonder if they've done any more work on it since?

EDIT: Tried it again. Still buggy and useless. Some day they'll make it work, I guess...

---

### Post by futz on 2007-06-06
Fixed it. Foxit Reader v1.3 (not 2.0) works with Wine once again.

The fix is to download gdiplus.dll and put it in the ~/.wine/drive_c/windows/system32 directory.

---

