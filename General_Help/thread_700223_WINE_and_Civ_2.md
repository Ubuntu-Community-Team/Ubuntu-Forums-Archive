---
title: "WINE and Civ 2"
date: 2008-02-18
forum: General Help
---

### Post by JazonEsti on 2008-02-18
I have a PC with 2 hard disks, my primary has Ubuntu 7.10 while the other is an old HD with Windows. The old one contains some old games I want to play. When I right click then Run with Wine Civ2.exe, nothing happens. Same happens when I double left click it. 

Please help me play Civ 2 again. :)

Thanks!

---

### Post by kesman on 2008-02-18
run wine in terminal, type
```

wine /path/to/the/game

```
and make sure you ahve the newest version of wine from the wine repository, get it from wine's web page.

---

### Post by JazonEsti on 2008-02-18
Admittedly I'm new to Ubuntu (or Linux in general, only installed 3 weeks ago. :)

Okay so I typed 
```
wine /home/jason/Civilization 2/civ2.exe
```
(I right clicked on the Civ2.exe file then Properties then copied the location)

I got this message 
```
wine: cannot find '/home/jason/Civilization'
```

What did I get wrong? Thanks!

---

### Post by kesman on 2008-02-18
use TAB to auto-complete directory names for you. For example, after typing "/home/jason/Ci" hit TAB-key so it will auto-complete the rest of the name for you. There's a space in the directory name which causes trouble usually.

---

### Post by JazonEsti on 2008-02-18
I renamed the directory to Civ2.

Okay so after repeating the process, I got this:

```
wine: Unhandled page fault on read access to 0x00000000 at address 0x5c19e8 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x005c19e8).
fixme:dbghelp_msc:pe_load_debug_directory This guy has FPO information
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:005c19e8 ESP:0034f380 EBP:0034f390 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000000 EBX:7b8b0888 ECX:00000000 EDX:7bc8443c
 ESI:005f6e90 EDI:7ffdf000
Stack dump:
0x0034f380:  7ffdf000 005f6e90 7b8b0888 0063fe08
0x0034f390:  0034f448 005cf70c 00000000 00000000
0x0034f3a0:  7ffdf000 005f6e90 7b8b0888 0063fe50
0x0034f3b0:  7bc8443c 00000000 00000000 0034f40c
0x0034f3c0:  7bc40210 00000000 00000001 0034f583
0x0034f3d0:  b7de61d3 7bc8443c 7bc3be7a 00000017
Backtrace:
=>1 0x005c19e8 in civ2 (+0x1c19e8) (0x0034f390)
  2 0x005cf70c in civ2 (+0x1cf70c) (0x0034f448)
  3 0x005cedef in civ2 (+0x1cedef) (0x0034f47c)
  4 0x0044ac28 in civ2 (+0x4ac28) (0x0034f4a8)
  5 0x0044afc3 in civ2 (+0x4afc3) (0x0034f4ec)
  6 0x0044b4d6 in civ2 (+0x4b4d6) (0x0034f620)
  7 0x0041b5f6 in civ2 (+0x1b5f6) (0x0034f650)
  8 0x0041f94b in civ2 (+0x1f94b) (0x0034fe48)
  9 0x004c428b in civ2 (+0xc428b) (0x0034fe5c)
  10 0x0055ae20 in civ2 (+0x15ae20) (0x0034fe78)
  11 0x005f7075 in civ2 (+0x1f7075) (0x0034ff08)
  12 0x7b874c7e start_process+0xee(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:839] in kernel32 (0x0034ffe8)
  13 0xb7e0a9d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x005c19e8: movl        0x0(%eax,%ecx,4),%eax
Modules:
Module  Address                 Debug info      Name (100 modules)
PE        400000-  70c000       Export          civ2
PE      10000000-10026000       Deferred        xdaemon
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c60b000-7c622000       Deferred        mcicda<elf>
  \-PE  7c610000-7c622000       \               mcicda
ELF     7c6c5000-7c716000       Deferred        libgcrypt.so.11
ELF     7c716000-7c71a000       Deferred        libgpg-error.so.0
ELF     7c71a000-7c72a000       Deferred        libtasn1.so.3
ELF     7c72a000-7c732000       Deferred        libkrb5support.so.0
ELF     7c732000-7c760000       Deferred        libcrypt.so.1
ELF     7c760000-7c7d0000       Deferred        libgnutls.so.13
ELF     7c7d0000-7c7f5000       Deferred        libk5crypto.so.3
ELF     7c7f5000-7c87d000       Deferred        libkrb5.so.3
ELF     7c87d000-7c8a6000       Deferred        libgssapi_krb5.so.2
ELF     7c8a6000-7c8db000       Deferred        libcups.so.2
ELF     7c99a000-7c9cc000       Deferred        uxtheme<elf>
  \-PE  7c9a0000-7c9cc000       \               uxtheme
ELF     7d5d6000-7d5eb000       Deferred        midimap<elf>
  \-PE  7d5e0000-7d5eb000       \               midimap
ELF     7d5eb000-7d603000       Deferred        msacm32<elf>
  \-PE  7d5f0000-7d603000       \               msacm32
ELF     7d603000-7d63d000       Deferred        wineoss<elf>
  \-PE  7d610000-7d63d000       \               wineoss
ELF     7d63d000-7d642000       Deferred        libxfixes.so.3
ELF     7d642000-7d65f000       Deferred        imm32<elf>
  \-PE  7d650000-7d65f000       \               imm32
ELF     7d65f000-7d667000       Deferred        libxrender.so.1
ELF     7d671000-7d673000       Deferred        libkeyutils.so.1
ELF     7d673000-7d676000       Deferred        libcom_err.so.2
ELF     7da26000-7da28000       Deferred        libnvidia-tls.so.1
ELF     7da28000-7e2ae000       Deferred        libglcore.so.1
ELF     7e2ae000-7e33a000       Deferred        libgl.so.1
ELF     7e33a000-7e33f000       Deferred        libxdmcp.so.6
ELF     7e33f000-7e342000       Deferred        libxau.so.6
ELF     7e342000-7e433000       Deferred        libx11.so.6
ELF     7e433000-7e441000       Deferred        libxext.so.6
ELF     7e441000-7e446000       Deferred        libxxf86vm.so.1
ELF     7e446000-7e45e000       Deferred        libice.so.6
ELF     7e45e000-7e466000       Deferred        libsm.so.6
ELF     7e466000-7e46f000       Deferred        libxcursor.so.1
ELF     7e46f000-7e475000       Deferred        libxrandr.so.2
ELF     7e477000-7e502000       Deferred        winex11<elf>
  \-PE  7e490000-7e502000       \               winex11
ELF     7e584000-7e5a4000       Deferred        libexpat.so.1
ELF     7e5a4000-7e5cf000       Deferred        libfontconfig.so.1
ELF     7e5cf000-7e5e4000       Deferred        libz.so.1
ELF     7e5e4000-7e654000       Deferred        libfreetype.so.6
ELF     7e654000-7e6a9000       Deferred        ddraw<elf>
  \-PE  7e660000-7e6a9000       \               ddraw
ELF     7e6a9000-7e6d0000       Deferred        msvfw32<elf>
  \-PE  7e6b0000-7e6d0000       \               msvfw32
ELF     7e6d0000-7e6f7000       Deferred        msacm32<elf>
  \-PE  7e6e0000-7e6f7000       \               msacm32
ELF     7e6f7000-7e731000       Deferred        avifil32<elf>
  \-PE  7e700000-7e731000       \               avifil32
ELF     7e731000-7e766000       Deferred        winspool<elf>
  \-PE  7e740000-7e766000       \               winspool
ELF     7e766000-7e807000       Deferred        comdlg32<elf>
  \-PE  7e770000-7e807000       \               comdlg32
ELF     7e807000-7e8c5000       Deferred        comctl32<elf>
  \-PE  7e810000-7e8c5000       \               comctl32
ELF     7e8c5000-7e91e000       Deferred        shlwapi<elf>
  \-PE  7e8d0000-7e91e000       \               shlwapi
ELF     7e91e000-7ea21000       Deferred        shell32<elf>
  \-PE  7e930000-7ea21000       \               shell32
ELF     7ea21000-7ea7a000       Deferred        rpcrt4<elf>
  \-PE  7ea30000-7ea7a000       \               rpcrt4
ELF     7ea7a000-7eb1b000       Deferred        ole32<elf>
  \-PE  7ea90000-7eb1b000       \               ole32
ELF     7eb1b000-7eba9000       Deferred        winmm<elf>
  \-PE  7eb30000-7eba9000       \               winmm
ELF     7eba9000-7ebdd000       Deferred        dplayx<elf>
  \-PE  7ebb0000-7ebdd000       \               dplayx
ELF     7ebdd000-7ebf0000       Deferred        libresolv.so.2
ELF     7ec01000-7ec1f000       Deferred        iphlpapi<elf>
  \-PE  7ec10000-7ec1f000       \               iphlpapi
ELF     7ec1f000-7ec4c000       Deferred        ws2_32<elf>
  \-PE  7ec30000-7ec4c000       \               ws2_32
ELF     7ec4c000-7ec66000       Deferred        wsock32<elf>
  \-PE  7ec50000-7ec66000       \               wsock32
ELF     7ec66000-7ecaf000       Deferred        advapi32<elf>
  \-PE  7ec70000-7ecaf000       \               advapi32
ELF     7ecaf000-7ed4a000       Deferred        gdi32<elf>
  \-PE  7ecc0000-7ed4a000       \               gdi32
ELF     7ed4a000-7ee88000       Deferred        user32<elf>
  \-PE  7ed70000-7ee88000       \               user32
ELF     7efa7000-7efb2000       Deferred        libnss_files.so.2
ELF     7efb2000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7efef000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c82000-b7c8b000       Deferred        libnss_compat.so.2
ELF     b7c8c000-b7c90000       Deferred        libdl.so.2
ELF     b7c90000-b7dda000       Deferred        libc.so.6
ELF     b7dda000-b7df2000       Deferred        libpthread.so.0
ELF     b7e03000-b7f17000       Dwarf           libwine.so.1
ELF     b7f19000-b7f35000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) H:\Civ2\civ2.exe
        00000009    0 <==

```

I can't even begin to understand that.

---

### Post by geo909 on 2008-02-18
OK, sorry for posting 'alternative' solutions (I hate when it happens to me)
but just wanted to mention that between the games in the add/remove programs, there is a civilization 2 replica for ubuntu. It's pretty much the same and I think you can also import maps etc from the original but I am not sure cause I haven't played it..

Also, do consider to run your civ from DosBox, it may work..

---

### Post by JazonEsti on 2008-02-18
I tried DOSBOX, but apparently it cannot run Civ 2. I get an illegal operation or something. I can run Darklands, though, a DOS game.

---

### Post by kesman on 2008-02-19
You should check out if there's a how-to in wine's application database. They usually have one for each game, and a ranking that tells you if a game is playable.

---

### Post by JazonEsti on 2008-02-20
Sigh. Apparently, a game as old as Civ2 is not compatible with WINE. I checked out WINE's compatibility list. Anyway, thanks for the help!

---

### Post by kesman on 2008-02-21
Search for freeciv in add/remove programs, it's a free clone of civ2 that runs natively on ubuntu.

---

### Post by JazonEsti on 2008-02-21
I tried it, but it's too clunky, too crude.

Civ 2 is better, in my opinion. :)

---

### Post by geo909 on 2008-02-22
> **JazonEsti said:**
> I tried it, but it's too clunky, too crude.

Civ 2 is better, in my opinion. :)

 Hmm.. Why I'm not surprised...
Games! Maybe our grandsons will have descent ones on Linux..

---

