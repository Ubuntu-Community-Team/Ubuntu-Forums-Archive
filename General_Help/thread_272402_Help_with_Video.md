---
title: "Help with Video"
date: 2006-10-06
forum: General Help
---

### Post by mccurry on 2006-10-06
I am getting really wierd looking screens in WoW (world of warcraft) and I am getting a video driver error when I run it. WoW runs fine except sound and this error. Sound I can live without, but would be nice but the screen shows the ground all normal but building are all out of whack. I have screen shots if anyone likes i can mail them so you can see. but here is the log:


Lots of info. Thanks for the help ahead of time.

Matt

also msg me on google talk at mccurry@gmail (dot) com
or yahoo at muerto.chongo

---

### Post by cronholio on 2006-10-06
I've seen this reported somewhere else. IIRC, the reason is that you are running WoW using Direct3D. You should use OpenGL instead:

```
wine WoW.exe -opengl
```

---

### Post by mccurry on 2006-10-06
thanks but thats the only way it will work. when I opengl it. my entire machine crashes.

---

### Post by mccurry on 2006-10-06
ok I tried that again after some tweaking and the best I got was a crash of wow itself, here is the log.

==============================================================================
World of WarCraft (build 5875)

Exe:      D:\home\mizza\wow\wow.exe
Time:     Oct  6, 2006  3:53:05.013 PM
User:     mizza
Computer: mizza-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	D:\home\mizza\wow\wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".


WoWBuild: 5875
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00180000  EBX=7E2A636C  ECX=00000003  EDX=0033FAC0  ESI=7C0806B8
EDI=7C030180  EBP=0033FAD8  ESP=0033FA6C  EIP=00000000  FLG=00210202
CS =0073      DS =007B      ES =007B      SS =007B      FS =003B      GS =0033


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

00000000 0033FAD8 0000:00000000 D:\home\mizza\wow\wow.exe
7E2704CB 0033FB48 0001:0003F4CB c:\windows\system32\winex11.drv
7EB6F489 0033FB88 0001:0003E489 c:\windows\system32\gdi32.dll
0058C4FB 0033FC14 0001:0018B4FB D:\home\mizza\wow\wow.exe
0058C34C 0033FC24 0001:0018B34C D:\home\mizza\wow\wow.exe
0058CEC6 0033FC74 0001:0018BEC6 D:\home\mizza\wow\wow.exe
00591F95 0033FC80 0001:00190F95 D:\home\mizza\wow\wow.exe
0058CC21 0033FCA0 0001:0018BC21 D:\home\mizza\wow\wow.exe
00589AF7 0033FCB4 0001:00188AF7 D:\home\mizza\wow\wow.exe
0063A483 0033FD20 0001:00239483 D:\home\mizza\wow\wow.exe
004027EC 0033FE68 0001:000017EC D:\home\mizza\wow\wow.exe
004021E0 0033FE78 0001:000011E0 D:\home\mizza\wow\wow.exe
0040411E 0033FF08 0001:0000311E D:\home\mizza\wow\wow.exe
7EE99F5F 0033FFE8 0001:00048F5F c:\windows\system32\kernel32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

7E2704CB winex11.drv  X11DRV_DescribePixelFormat+561 (0x0018FB88,0x00000001,0x00000028,0x0033FBDC)
7EB6F489 gdi32.dll    DescribePixelFormat+87 (0x00000350,0x00000001,0x00000028,0x0033FBDC)
0058C4FB wow.exe      <unknown symbol>+0 (0x0033FC74,0x00000000,0x0033FC74,0x0058CEC6)
0058C34C wow.exe      <unknown symbol>+0 (0x0033FC3C,0x000002E4,0x011CCF30,0x011CC008)
0058CEC6 wow.exe      <unknown symbol>+0 (0x0033FCCC,0x0033FCA0,0x0058CC21,0x0042CFE0)
00591F95 wow.exe      <unknown symbol>+0 (0x0042CFE0,0x0033FCCC,0x0033FD04,0x0042CFE0)
0058CC21 wow.exe      <unknown symbol>+0 (0x0042CFE0,0x0033FCCC,0x00000000,0x0033FD20)
00589AF7 wow.exe      <unknown symbol>+0 (0x0033FCCC,0x7FFDF000,0x00000000,0x7EED3B00)
0063A483 wow.exe      <unknown symbol>+0 (0x00000001,0x6C726F57,0x666F2064,0x72615720)
004027EC wow.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0033FF08,0x0040411E)
004021E0 wow.exe      <unknown symbol>+0 (0x004099A0,0x00400000,0x00000000,0x001163B8)
0040411E wow.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7EE99F5F kernel32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
B7DFF387              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00340000 - 0x003D6000  D:\home\mizza\wow\fmod.dll
0x00400000 - 0x00D06000  D:\home\mizza\wow\wow.exe
0x10000000 - 0x10069000  D:\home\mizza\wow\DivxDecoder.dll
0x7C580000 - 0x7C58B000  c:\windows\system32\psapi.dll
0x7C590000 - 0x7C5D0000  c:\windows\system32\dbghelp.dll
0x7C800000 - 0x7C807000  c:\windows\system32\midimap.dll
0x7C830000 - 0x7C85B000  c:\windows\system32\wineoss.drv
0x7C8B0000 - 0x7C8D5000  c:\windows\system32\uxtheme.dll
0x7E230000 - 0x7E2AF000  c:\windows\system32\winex11.drv
0x7E380000 - 0x7E398000  c:\windows\system32\mpr.dll
0x7E3A0000 - 0x7E3DF000  c:\windows\system32\wininet.dll
0x7E3F0000 - 0x7E441000  c:\windows\system32\msvcrt.dll
0x7E450000 - 0x7E467000  c:\windows\system32\msacm32.drv
0x7E470000 - 0x7E4EF000  c:\windows\system32\winmm.dll
0x7E500000 - 0x7E50B000  c:\windows\system32\imm32.dll
0x7E740000 - 0x7E79E000  c:\windows\system32\opengl32.dll
0x7E7B0000 - 0x7E7C8000  c:\windows\system32\ws2_32.dll
0x7E7D0000 - 0x7E7E2000  c:\windows\system32\wsock32.dll
0x7E800000 - 0x7E814000  c:\windows\system32\iphlpapi.dll
0x7E820000 - 0x7E864000  c:\windows\system32\rpcrt4.dll
0x7E870000 - 0x7E8F5000  c:\windows\system32\ole32.dll
0x7E900000 - 0x7E94B000  c:\windows\system32\shlwapi.dll
0x7E960000 - 0x7EA31000  c:\windows\system32\shell32.dll
0x7EB30000 - 0x7EBC2000  c:\windows\system32\gdi32.dll
0x7EBE0000 - 0x7ECF4000  c:\windows\system32\user32.dll
0x7ED00000 - 0x7EDB6000  c:\windows\system32\comctl32.dll
0x7EDC0000 - 0x7EDFA000  c:\windows\system32\advapi32.dll
0x7EE50000 - 0x7EF2F000  c:\windows\system32\kernel32.dll
0x7EF90000 - 0x7F000000  c:\windows\system32\ntdll.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000000)

00000000: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0033FA6C)

* = addr                                         **                       *   
0033FA60: D4 E8 2A 7E  80 01 03 7C  D8 FA 33 00  98 DE 26 7E  ..*~...|..3...&~
0033FA70: 80 01 03 7C  00 00 18 00  0B 80 00 00  C0 FA 33 00  ...|..........3.
0033FA80: DC 3A DD B7  20 53 DD B7  F0 FF FF FF  A8 FA 33 00  .:.. S........3.
0033FA90: C4 FA 33 00  C0 FA 33 00  14 8C 2A 7E  30 EE 29 7E  ..3...3...*~0.)~
0033FAA0: 20 FB 33 00  01 00 00 00  00 00 00 00  00 00 00 00   .3.............
0033FAB0: B8 06 08 7C  01 00 00 00  27 00 00 00  19 96 FA 7E  ...|....'......~
0033FAC0: 00 00 00 00  00 00 00 00  43 00 00 00  6C 63 2A 7E  ........C...lc*~
0033FAD0: D4 E8 2A 7E  D4 E8 2A 7E  48 FB 33 00  CB 04 27 7E  ..*~..*~H.3...'~
0033FAE0: 38 FB 33 00  00 00 00 00  24 FB 33 00  38 9C BA 7E  8.3.....$.3.8..~
0033FAF0: 50 03 00 00  FF FF 00 00  28 FB 33 00  F4 56 B6 7E  P.......(.3..V.~
0033FB00: 20 18 BB 7E  38 FB 33 00  48 FB 33 00  D4 E8 2A 7E   ..~8.3.H.3...*~
0033FB10: A8 05 08 7C  30 FA 18 00  20 18 BB 7E  38 9C BA 7E  ...|0... ..~8..~
0033FB20: 00 00 00 00  01 00 00 00  48 FB 33 00  BC 11 B4 7E  ........H.3....~
0033FB30: 50 03 00 00  FF FF 00 00  00 00 00 00  38 9C BA 7E  P...........8..~
0033FB40: 00 00 00 00  30 FA 18 00  88 FB 33 00  89 F4 B6 7E  ....0.....3....~
0033FB50: 88 FB 18 00  01 00 00 00  28 00 00 00  DC FB 33 00  ........(.....3.
0033FB60: 50 03 00 00  00 00 00 00  00 00 00 00  00 00 00 00  P...............
0033FB70: 5C F6 C9 7E  94 FB 33 00  5A 98 C5 7E  32 F4 B6 7E  \..~..3.Z..~2..~
0033FB80: 50 03 00 00  01 00 00 00  14 FC 33 00  FB C4 58 00  P.........3...X.
0033FB90: 50 03 00 00  01 00 00 00  28 00 00 00  DC FB 33 00  P.......(.....3.
0033FBA0: 08 C0 1C 01  74 FC 33 00  08 C0 1C 01  30 00 00 00  ....t.3.....0...
0033FBB0: 20 00 00 00  99 74 C1 7E  00 00 00 00  00 00 00 00   ....t.~........
0033FBC0: 00 00 40 00  00 00 00 00  00 00 00 00  00 00 00 00  ..@.............
0033FBD0: 00 00 00 00  24 A9 85 00  00 00 00 00  28 00 01 00  ....$.......(...
0033FBE0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FBF0: 00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
0033FC00: 00 00 00 00  00 00 40 00  2D C0 00 00  01 00 00 00  ......@.-.......
0033FC10: 26 00 01 00  24 FC 33 00  4C C3 58 00  74 FC 33 00  &...$.3.L.X.t.3.
0033FC20: 00 00 00 00  74 FC 33 00  C6 CE 58 00  3C FC 33 00  ....t.3...X.<.3.
0033FC30: E4 02 00 00  30 CF 1C 01  08 C0 1C 01  00 00 00 00  ....0...........
0033FC40: 01 00 00 00  01 01 00 00  05 00 00 00  00 04 00 00  ................
0033FC50: 00 03 00 00  01 00 00 00  01 00 00 00  00 00 00 00  ................
0033FC60: 01 00 00 00  3C 00 00 00  00 00 00 00  00 00 00 00  ....<...........
0033FC70: 00 00 00 00  80 FC 33 00  95 1F 59 00  CC FC 33 00  ......3...Y...3.
0033FC80: A0 FC 33 00  21 CC 58 00  E0 CF 42 00  CC FC 33 00  ..3.!.X...B...3.
0033FC90: 04 FD 33 00  E0 CF 42 00  00 3B ED 7E  E4 02 00 00  ..3...B..;.~....
0033FCA0: B4 FC 33 00  F7 9A 58 00  E0 CF 42 00  CC FC 33 00  ..3...X...B...3.
0033FCB0: 00 00 00 00  20 FD 33 00  83 A4 63 00  CC FC 33 00  .... .3...c...3.
0033FCC0: 00 F0 FD 7F  00 00 00 00  00 3B ED 7E  00 00 00 00  .........;.~....
0033FCD0: 01 00 00 00  01 01 00 00  05 00 00 00  00 04 00 00  ................
0033FCE0: 00 03 00 00  01 00 00 00  01 00 00 00  00 00 00 00  ................
0033FCF0: 01 00 00 00  3C 00 00 00  00 00 00 00  00 00 00 00  ....<...........
0033FD00: 00 00 00 00  00 04 00 00  00 03 00 00  20 00 00 00  ............ ...
0033FD10: 3C 00 00 00  2C FD 33 00  00 00 00 00  DD 27 00 00  <...,.3......'..
0033FD20: 68 FE 33 00  EC 27 40 00  01 00 00 00  57 6F 72 6C  h.3..'@.....Worl
0033FD30: 64 20 6F 66  20 57 61 72  63 72 61 66  74 00 FB 7E  d of Warcraft..~
0033FD40: 5C FE 33 00  54 FD 33 00  98 FD 33 00  1E 6E FB 7E  \.3.T.3...3..n.~
0033FD50: 01 00 00 00  38 00 00 00  00 00 11 00  38 C7 16 00  ....8.......8...
0033FD60: 00 00 00 00  28 00 00 00  38 00 11 00  80 52 FF 7E  ....(...8....R.~
0033FD70: 00 00 11 00  00 C7 16 00  98 FD 33 00  C8 74 FB 7E  ..........3..t.~
0033FD80: CC FD 33 00  00 00 06 00  38 C7 16 00  19 96 FA 7E  ..3.....8......~
0033FD90: 00 C7 16 00  80 52 FF 7E  E8 FD 33 00  1E 6E FB 7E  .....R.~..3..n.~
0033FDA0: 20 00 11 00  00 3B ED 7E  3C FE 33 00  30 C2 26 45   ....;.~<.3.0.&E
0033FDB0: CC FD 33 00  FC E4 02 00  30 C2 26 45  A4 5C FB 7E  ..3.....0.&E.\.~
0033FDC0: 38 FE 33 00  00 00 11 00  00 00 11 00  27 9C FA 7E  8.3.........'..~
0033FDD0: 00 00 11 00  00 00 06 00  20 C3 16 00  19 96 FA 7E  ........ ......~
0033FDE0: F8 C2 16 00  80 52 FF 7E  48 FE 33 00  40 7B FB 7E  .....R.~H.3.@{.~
0033FDF0: 20 00 11 00  00 C0 FD 7F  18 FE 33 00  C2 93 FA 7E   .........3....~
0033FE00: 00 00 11 00  00 00 00 00  20 00 00 00  80 52 FF 7E  ........ ....R.~
0033FE10: E5 D1 EA 7E  E0 3B C5 00  38 FE 33 00  00 00 00 00  ...~.;..8.3.....
0033FE20: 00 00 11 00  00 C3 16 00  06 00 00 00  27 9C FA 7E  ............'..~
0033FE30: 65 6E 00 7E  00 3B ED 7E  00 00 11 00  00 3B ED 7E  en.~.;.~.....;.~
0033FE40: 55 53 00 7E  00 F0 FD 7F  00 3B ED 7E  64 FE 33 00  US.~.....;.~d.3.
0033FE50: 57 44 42 43  0B 00 00 00  2C 00 00 00  00 F0 FD 7F  WDBC....,.......
0033FE60: A4 02 00 00  88 6D 1C 01  78 FE 33 00  E0 21 40 00  .....m..x.3..!@.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3336

Percent memory used:    13
Total physical memory:  528199680
Free Memory:            312123392
Page file:              1258426368
Total virtual memory:   2147352575

---

### Post by cronholio on 2006-10-06
You might want to check [this page.]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine")

---

