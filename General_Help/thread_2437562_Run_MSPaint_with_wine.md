---
title: "Run MSPaint with wine"
date: 2020-02-25
forum: General Help
---

### Post by sevensixtwo on 2020-02-25
Hi.  I got a copy of mspaint.exe Windows 10 version.  I DLed wine, and I was getting an error about some .DLL.  I used winetricks to load the .DLL but now I am getting another error.  When I do
```
wine mspaint.exe
```

the first thing that happens is that I get this MSPaint error:
[IMG]https://i.ibb.co/mRmWW9T/image.png[/IMG]

When I click ok, this prints to the terminal:
```
wine: Call from 0x7b43c8bc to unimplemented function api-ms-win-core-processthreads-l1-1-2.dll.GetProcessMitigationPolicy, aborting
wine: Unimplemented function api-ms-win-core-processthreads-l1-1-2.dll.GetProcessMitigationPolicy called at address 0x7bcd0023:0x7b43c8bc (thread 0009), starting debugger...

```

and this window pops up:
[IMG]https://i.ibb.co/2yMqbst/image.png[/IMG]

The ''show details'' output in the window is
```
Unhandled exception: unimplemented function api-ms-win-core-processthreads-.GetProcessMitigationPolicy called in 32-bit code (0x7b43c8bc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:7b43c8bc ESP:0033ec84 EBP:0033ed08 EFLAGS:00000216(   - --  I   -A-P- )
 EAX:7b429209 EBX:00000004 ECX:0033ecb0 EDX:0033ed34
 ESI:7f1c0b50 EDI:7f89e020
Stack dump:
0x0033ec84:  00000002 00a50000 00000000 00000000
0x0033ec94:  0033ecb0 00a50014 80000100 00000001
0x0033eca4:  00000000 7b43c8bc 00000002 7f1c0b50
0x0033ecb4:  7f1c0bab 0033ece8 7f62c809 5f809623
0x0033ecc4:  00a540d0 7f610745 7f62c809 00a50000
0x0033ecd4:  00000000 00a540d0 7f62c7ca 00000001
f78a00d: sel=7bc5006f base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x7b43c8bc in kernel32 (+0x2c8bc) (0x0033ed08)
  1 0x7f1c0b37 (0x0033ed48)
  2 0x7f1c07e1 (0x0033ed80)
  3 0x00468df7 in mspaint (+0x68df6) (0x0033edcc)
  4 0x00441ef3 in mspaint (+0x41ef2) (0x0033fe1c)
  5 0x5f812566 in mfc42u (+0x12565) (0x0033fec0)
  6 0x7b461a7c in kernel32 (+0x51a7b) (0x0033fed8)
  7 0x7b4634ce in kernel32 (+0x534cd) (0x0033ffd8)
  8 0x7b461a8a in kernel32 (+0x51a89) (0x0033ffec)
0x7b43c8bc: addl    $12,%esp
Modules:
Module    Address            Debug info    Name (47 modules)
PE      400000-  a42000    Export          mspaint
PE    5f800000-5f8f2000    Export          mfc42u
PE    7ac10000-7ac23000    Deferred        riched20
PE    7b410000-7b5b6000    Export          kernel32
PE    7bc10000-7bc14000    Deferred        ntdll
PE    7d770000-7d774000    Deferred        sti
PE    7d7b0000-7d7ba000    Deferred        actxprxy
PE    7d8d0000-7d8d4000    Deferred        uiribbon
PE    7d930000-7d933000    Deferred        usp10
PE    7d980000-7d984000    Deferred        gdiplus
PE    7e590000-7e594000    Deferred        msftedit
PE    7e5b0000-7e5b4000    Deferred        uxtheme
PE    7e810000-7e814000    Deferred        winex11
PE    7e8a0000-7e8a4000    Deferred        imm32
PE    7eb60000-7eb69000    Deferred        msacm32
PE    7eb90000-7ec08000    Deferred        winmm
PE    7ec40000-7ec44000    Deferred        propsys
PE    7ec70000-7ec7a000    Deferred        winspool
PE    7ecb0000-7ee12000    Deferred        shell32
PE    7ef00000-7ef99000    Deferred        comdlg32
PE    7efe0000-7f030000    Deferred        comctl32
PE    7f100000-7f103000    Deferred        api-ms-win-eventing-provider-l1-C:\windows\system32\api-ms-win-eventing-provider-l1-1-0.dll
PE    7f110000-7f113000    Deferred        api-ms-win-core-timezone-l1-1-0
PE    7f130000-7f133000    Deferred        api-ms-win-core-registry-l1-1-0
PE    7f140000-7f143000    Deferred        api-ms-win-core-file-l1-2-1
PE    7f150000-7f153000    Deferred        api-ms-win-core-libraryloader-l1C:\windows\system32\api-ms-win-core-libraryloader-l1-2-0.dll
PE    7f160000-7f163000    Deferred        api-ms-win-core-sysinfo-l1-2-1
PE    7f180000-7f183000    Deferred        api-ms-win-core-profile-l1-1-0
PE    7f190000-7f193000    Deferred        api-ms-win-core-debug-l1-1-1
PE    7f1a0000-7f1a3000    Deferred        api-ms-win-core-errorhandling-l1C:\windows\system32\api-ms-win-core-errorhandling-l1-1-1.dll
PE    7f1b0000-7f1b3000    Deferred        api-ms-win-core-processthreads-lC:\windows\system32\api-ms-win-core-processthreads-l1-1-2.dll
PE    7f1d0000-7f1d3000    Deferred        api-ms-win-core-synch-l1-2-0
PE    7f1e0000-7f1e3000    Deferred        api-ms-win-core-string-l1-1-0
PE    7f1f0000-7f1f3000    Deferred        api-ms-win-core-winrt-error-l1-1C:\windows\system32\api-ms-win-core-winrt-error-l1-1-1.dll
PE    7f210000-7f213000    Deferred        api-ms-win-core-winrt-l1-1-0
PE    7f220000-7f223000    Deferred        combase
PE    7f240000-7f243000    Deferred        api-ms-win-core-winrt-string-l1-C:\windows\system32\api-ms-win-core-winrt-string-l1-1-0.dll
PE    7f250000-7f253000    Deferred        api-ms-win-core-com-l1-1-1
PE    7f270000-7f274000    Deferred        rpcrt4
PE    7f300000-7f328000    Deferred        ole32
PE    7f460000-7f468000    Deferred        oleaut32
PE    7f580000-7f588000    Deferred        shlwapi
PE    7f600000-7f604000    Deferred        msvcrt
PE    7f6b0000-7f776000    Deferred        user32
PE    7f890000-7f897000    Deferred        gdi32
PE    7f9c0000-7f9c4000    Deferred        advapi32
PE    7ffd0000-7ffd4000    Deferred        version
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\god\Documents\Paint\mspaint.exe
    00000039    0
    00000038    0
    00000009    0 <==
0000000e services.exe
    00000032    0
    00000026    0
    00000023    0
    0000001e    0
    00000018    0
    00000015    0
    00000014    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001d    0
    00000017    0
    00000016    0
    00000012    0
0000001b plugplay.exe
    00000020    0
    0000001f    0
    0000001c    0
00000021 winedevice.exe
    0000002b    0
    00000027    0
    00000025    0
    00000024    0
    00000022    0
00000029 explorer.exe
    0000002e    0
    0000002d    0
    0000002c    0
    0000002a    0
00000030 svchost.exe
    0000003b    0
    0000003a    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
    00000031    0
System information:
    Wine build: wine-3.0 (Ubuntu 3.0-1ubuntu1)
    Platform: i386 (WOW64)
    Version: Windows 7
    Host system: Linux
    Host version: 5.3.0-40-generic
```

After I close the window, the last thing to print to the terminal is
```
0034:err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d

```

---

### Post by Impavidus on 2020-02-26
It appears that MS Paint needs some Windows functions that are not available in Wine. That's normal, Wine doesn't always work. I suggest you try a native Linux painting program. Have a look at this thread: [https://ubuntuforums.org/showthread.php?t=2437517](https://ubuntuforums.org/showthread.php?t=2437517).

---

### Post by Philip_Edwards on 2020-02-26
Do you absolutely have to have MSPaint. Just yesterday I discovered Kolourpaint, a virtual clone of MS Paint.

Phil

---

### Post by kesetyan on 2020-02-26
Hi sevensixtwo,

I can vouch for KolourPaint, it's the nearest equivalent to MSPaint I've tried in Linux systems - it's very good and user friendly.  It might not have all the extras of the Gimp, for example, but it is quite a competent handler of basic requirements of image file handling.  However, if you really need something to run in Wine, consider PhotoFiltre which is available as a portable program.  I've been using a portable version of PhotoFiltre 7 for some time - the developers are French so, if you want English text in menus etc., check that you download the correct version. Download from: **[https://portableapps.com/apps/graphics_pictures/photofiltre_portable](https://portableapps.com/apps/graphics_pictures/photofiltre_portable)** .  You can install the program on a usb memory stick and run it from there when you plug it into your Linux Mint computer but you can also copy all the folders and their contents from the memory stick to your computer if you want it always to hand.

---

