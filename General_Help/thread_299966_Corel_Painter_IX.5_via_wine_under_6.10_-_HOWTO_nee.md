---
title: "Corel Painter IX.5 via wine under 6.10 - HOWTO needed"
date: 2006-11-15
forum: General Help
---

### Post by JHawk24821 on 2006-11-15
My girlfriend wants to switch from Windows (boo!) to Ubuntu (yay!) - but won't give up her favorite application: Corel's Painter IX.5. ](*,) Painter installed just fine via wine, however starting it up leads to an error loop that I have to send two CTRL+C's yo get out of.  When it does so, it launches a debugger and dumps the output to the screen.  I thought that perhaps the community could make some sense of this (I can't) and possibly point me in the right direction.

I have tried starting Painter by right clicking the main program executable (Painter IX.EXE) and telling it to start using wine, as well as by using a simple launcher script.  The command line option has a few extra errors, as outlined below.

launcher script: **painter.sh**
```
#!/bin/bash
WINEDEBUG=fixme-all wine C:/Program\ Files/Corel/Corel\ Painter\ IX/Painter\ IX.exe
"$@"
```

command line:
```
hawk@hawk-desktop:~/.wine/drive_c/Program Files/Corel/Corel Painter IX$ wine Painter\ IX.exe
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:win:WINNLSEnableIME hUnknown1 0x10026 bUnknown2 1: stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
**The rest of the error log matches the log below**
```

results: **[*1]** = endless loop, **[*2]** = prints about 50-60 lines
```
hawk@hawk-desktop:~$ ./painter.sh 
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
**[*1]**
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3     **<-- CTRL+C**
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
**[*1]**
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3     **<-- CTRL+C**
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
**[*2]**
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ed7e320, level 2): Holding 0x7ec74960, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec74960 level 3
wine: Unhandled exception 0x80000003 at address 0x7b88304c (thread 0009), starting debugger...
0x7b88304d _CheckNotSysLevel+0x3d in kernel32: addl     $36,%esp
Modules:
Module  Address                 Debug info      Name (126 modules)
PE      340000-34b000   Deferred        corememory
PE      350000-357000   Deferred        coreerrorcodes
PE      360000-3ab000   Deferred        painterriplib
PE      3e0000-3f5000   Deferred        crlrcvyintl
PE      400000-a12000   Deferred        painter ix
PE      a20000-ade000   Deferred        brushengine
PE      ae0000-dc5000   Deferred        asi32_14
PE      dd0000-e26000   Deferred        mccore
PE      1aa0000-1ae4000 Deferred        crlrcvycore
PE      1af0000-1bf2000 Deferred        mfc71u
PE      1c00000-1c26000 Deferred        painterintl
PE      1e50000-1fad000 Deferred        psikey
PE      10000000-1006f000       Deferred        pspformatsdk
ELF     7b800000-7b917000       Export          kernel32<elf>
  \-PE  7b820000-7b917000       \               kernel32
ELF     7bc00000-7bc80000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc80000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c140000-7c243000       Deferred        mfc71
PE      7c340000-7c396000       Deferred        msvcr71
PE      7c3a0000-7c41b000       Deferred        msvcp71
ELF     7c7ad000-7c7c1000       Deferred        oleacc<elf>
  \-PE  7c7b0000-7c7c1000       \               oleacc
ELF     7c7c1000-7c807000       Deferred        dbghelp<elf>
  \-PE  7c7d0000-7c807000       \               dbghelp
ELF     7d2b1000-7da74000       Deferred        libglcore.so.1
ELF     7da74000-7db00000       Deferred        winex11<elf>
  \-PE  7da80000-7db00000       \               winex11
ELF     7dd02000-7dd17000       Deferred        psapi<elf>
  \-PE  7dd10000-7dd17000       \               psapi
ELF     7dd17000-7dd2e000       Deferred        imagehlp<elf>
  \-PE  7dd20000-7dd2e000       \               imagehlp
ELF     7dd34000-7dda6000       Deferred        wineps<elf>
  \-PE  7dd50000-7dda6000       \               wineps
ELF     7de3a000-7de81000       Deferred        wininet<elf>
  \-PE  7de40000-7de81000       \               wininet
ELF     7de81000-7de85000       Deferred        libgpg-error.so.0
ELF     7de85000-7ded3000       Deferred        libgcrypt.so.11
ELF     7ded3000-7dee6000       Deferred        libtasn1.so.3
ELF     7dee6000-7df14000       Deferred        libcrypt.so.1
ELF     7df24000-7df93000       Deferred        libgnutls.so.13
ELF     7df93000-7dfc2000       Deferred        libcups.so.2
ELF     7dfea000-7e01c000       Deferred        uxtheme<elf>
  \-PE  7dff0000-7e01c000       \               uxtheme
ELF     7e01c000-7e031000       Deferred        midimap<elf>
  \-PE  7e020000-7e031000       \               midimap
ELF     7e031000-7e06d000       Deferred        wineoss<elf>
  \-PE  7e040000-7e06d000       \               wineoss
PE      7e290000-7e29d000       --none--        msacm32
ELF     7e29f000-7e2a4000       Deferred        libxfixes.so.3
ELF     7e2a4000-7e2ad000       Deferred        libxcursor.so.1
ELF     7e2ad000-7e2cb000       Deferred        ximcp.so.2
ELF     7e2cb000-7e2cd000       Deferred        xlcutf8load.so.2
ELF     7e2cd000-7e2d0000       Deferred        libxrandr.so.2
ELF     7e2d0000-7e2d8000       Deferred        libxrender.so.1
ELF     7e2d8000-7e2db000       Deferred        libxinerama.so.1
ELF     7e2f2000-7e377000       Deferred        libgl.so.1
ELF     7e377000-7e37c000       Deferred        libxdmcp.so.6
ELF     7e37c000-7e445000       Deferred        libx11.so.6
ELF     7e445000-7e452000       Deferred        libxext.so.6
ELF     7e452000-7e46a000       Deferred        libice.so.6
ELF     7e46a000-7e488000       Deferred        libexpat.so.1
ELF     7e488000-7e4b7000       Deferred        libfontconfig.so.1
ELF     7e4b7000-7e4cb000       Deferred        libz.so.1
ELF     7e4cb000-7e535000       Deferred        libfreetype.so.6
ELF     7e535000-7e551000       Deferred        imm32<elf>
  \-PE  7e540000-7e551000       \               imm32
ELF     7e551000-7e570000       Deferred        mpr<elf>
  \-PE  7e560000-7e570000       \               mpr
ELF     7e570000-7e605000       Deferred        oleaut32<elf>
  \-PE  7e580000-7e605000       \               oleaut32
ELF     7e605000-7e636000       Deferred        winspool<elf>
  \-PE  7e610000-7e636000       \               winspool
ELF     7e636000-7e71d000       Deferred        shell32<elf>
  \-PE  7e650000-7e71d000       \               shell32
ELF     7e71d000-7e7b9000       Deferred        comdlg32<elf>
  \-PE  7e730000-7e7b9000       \               comdlg32
ELF     7e7b9000-7e810000       Deferred        shlwapi<elf>
  \-PE  7e7d0000-7e810000       \               shlwapi
ELF     7e810000-7e824000       Deferred        sensapi<elf>
  \-PE  7e820000-7e824000       \               sensapi
ELF     7e824000-7e84f000       Deferred        ws2_32<elf>
  \-PE  7e830000-7e84f000       \               ws2_32
ELF     7e84f000-7e869000       Deferred        wsock32<elf>
  \-PE  7e860000-7e869000       \               wsock32
ELF     7e869000-7e87c000       Deferred        libresolv.so.2
ELF     7e87c000-7e89b000       Deferred        iphlpapi<elf>
  \-PE  7e880000-7e89b000       \               iphlpapi
ELF     7e89b000-7e8ed000       Deferred        rpcrt4<elf>
  \-PE  7e8b0000-7e8ed000       \               rpcrt4
ELF     7e8ed000-7e97e000       Deferred        ole32<elf>
  \-PE  7e900000-7e97e000       \               ole32
ELF     7e97e000-7e992000       Deferred        lz32<elf>
  \-PE  7e980000-7e992000       \               lz32
ELF     7e992000-7e9ab000       Deferred        version<elf>
  \-PE  7e9a0000-7e9ab000       \               version
ELF     7e9ab000-7ea6c000       Deferred        comctl32<elf>
  \-PE  7e9b0000-7ea6c000       \               comctl32
ELF     7ea6c000-7ea93000       Deferred        msvfw32<elf>
  \-PE  7ea70000-7ea93000       \               msvfw32
ELF     7ea93000-7ead7000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead7000       \               advapi32
ELF     7ead7000-7eae2000       Deferred        libgcc_s.so.1
ELF     7eae4000-7eae6000       Deferred        libnvidia-tls.so.1
ELF     7eae6000-7eae9000       Deferred        libxau.so.6
ELF     7eae9000-7eaf2000       Deferred        libsm.so.6
ELF     7ebd1000-7ec85000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec85000       \               gdi32
ELF     7ec85000-7edb8000       Deferred        user32<elf>
  \-PE  7eca0000-7edb8000       \               user32
ELF     7edb8000-7ee40000       Deferred        winmm<elf>
  \-PE  7edc0000-7ee40000       \               winmm
ELF     7ee40000-7ee66000       Deferred        msacm32<elf>
ELF     7ee66000-7ee9f000       Deferred        avifil32<elf>
  \-PE  7ee70000-7ee9f000       \               avifil32
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d01000-b7d0a000       Deferred        libnss_compat.so.2
ELF     b7d0b000-b7d0f000       Deferred        libdl.so.2
ELF     b7d0f000-b7e43000       Deferred        libc.so.6
ELF     b7e44000-b7e57000       Deferred        libpthread.so.0
ELF     b7e67000-b7f78000       Deferred        libwine.so.1
ELF     b7f7a000-b7f95000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Corel\Corel Painter IX\Painter IX.exe
        00000009    0 <==
hawk@hawk-desktop:~$
```

Any help you have to offer will be greatly appreciated - even if it's just to say that I am stuck with having to dual-boot! :rolleyes:

---

### Post by nickej on 2008-01-02
Well, it's been a year. Any solutions to this one? Using 7.10, even?

---

### Post by darkmaster on 2008-02-28
For as long as I know, no chance that Painter will run on wine, sorry. You can try Artrage or deep painter instead, they are great softwares, the latter is much more professional than the former but they are both very col softwares. They both work in Wine. See my article:

[http://thedarkmaster.wordpress.com/2007/08/12/painting-programs-for-linux/](http://thedarkmaster.wordpress.com/2007/08/12/painting-programs-for-linux/)

---

