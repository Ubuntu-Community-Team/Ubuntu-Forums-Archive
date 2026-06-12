---
title: "Problem with Wine in Edgy"
date: 2007-01-22
forum: General Help
---

### Post by skate_metaly on 2007-01-22
hi
i installed wine in my edgy
everytime i want to start a .exe format. it gives me :
i removed and reinstalled but i got the same thing. please help me

```
wine: Unhandled page fault on read access to 0x7c224320 at address 0xb7d145c7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x7c224320 in 32-bit code (0xb7d145c7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d145c7 ESP:0033dcb8 EBP:0033dce8 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000047 EBX:7ea6253c ECX:7ea5a82c EDX:7c224320
 ESI:00000047 EDI:7ea5a859
Stack dump:
0x0033dcb8:  7ea659c8 7ea29b75 7ea659c8 7ea5a81a
0x0033dcc8:  0033dce8 7ea285d4 7c1ede98 7ea5a243
0x0033dcd8:  7ea29afd 7ea6253c 7ea5a1b2 7c1ede98
0x0033dce8:  0033dd68 7ea2a636 7c224320 7ea5a859
0x0033dcf8:  0033dd54 7ea5a07c 7e81d34f 7c01a4d8
0x0033dd08:  00000050 00000048 7c020980 7c018cd8
Backtrace:
=>1 0xb7d145c7 strstr+0x27() in libc.so.6 (0x0033dce8)
  2 0x7ea2a636 in winex11 (+0x3a636) (0x0033dd68)
  3 0x7ea2a9c6 X11DRV_setup_opengl_visual+0x66() in winex11 (0x0033ddf8)
  4 0x7ea3efdf in winex11 (+0x4efdf) (0x0033df48)
  5 0x7ea4f6b3 in winex11 (+0x5f6b3) (0x0033df68)
  6 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033df88)
  7 0x7bc390dc in ntdll (+0x290dc) (0x0033e038)
  8 0x7bc3957d in ntdll (+0x2957d) (0x0033e078)
  9 0x7bc3b487 LdrLoadDll+0x87() in ntdll (0x0033e0a8)
  10 0x7b861aeb in kernel32 (+0x41aeb) (0x0033e2f8)
  11 0x7b861d00 LoadLibraryExW+0x50() in kernel32 (0x0033e328)
  12 0x7b861e23 LoadLibraryExA+0x43() in kernel32 (0x0033e348)
  13 0x7b861e5d LoadLibraryA+0x2d() in kernel32 (0x0033e368)
  14 0x7ec68bc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0033e4d8)
  15 0x7ec645d0 CreateDCW+0x60() in gdi32 (0x0033e788)
  16 0x7ed2dbd0 CreateIconFromResourceEx+0x420() in user32 (0x0033e828)
  17 0x7ed2e567 in user32 (+0x2e567) (0x0033e888)
  18 0x7ed2eaab LoadImageW+0x3fb() in user32 (0x0033e928)
  19 0x7ed2f196 LoadImageA+0x56() in user32 (0x0033ea08)
  20 0x7ed2f434 LoadCursorA+0x44() in user32 (0x0033ea38)
  21 0x7ed2520f in user32 (+0x2520f) (0x0033ea58)
  22 0x7ed2525d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0033ea68)
  23 0x7ed993f2 in user32 (+0x993f2) (0x0033eae8)
  24 0x7edad343 in user32 (+0xad343) (0x0033eb08)
  25 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033eb28)
  26 0x7bc390dc in ntdll (+0x290dc) (0x0033ebd8)
  27 0x7bc3957d in ntdll (+0x2957d) (0x0033ec18)
  28 0x7bc3b487 LdrLoadDll+0x87() in ntdll (0x0033ec48)
  29 0x7b861aeb in kernel32 (+0x41aeb) (0x0033ee98)
  30 0x7b861d00 LoadLibraryExW+0x50() in kernel32 (0x0033eec8)
  31 0x7b861e23 LoadLibraryExA+0x43() in kernel32 (0x0033eee8)
  32 0x7b861e5d LoadLibraryA+0x2d() in kernel32 (0x0033ef08)
  33 0x7ee81230 in wineconsole (+0x11230) (0x0033ef28)
  34 0x7ee76240 in wineconsole (+0x6240) (0x0033fb88)
  35 0x7ee80d5c WinMain+0x18c() in wineconsole (0x0033fe58)
  36 0x7ee813a3 main+0xa3() in wineconsole (0x0033fed8)
  37 0x7ee812cb in wineconsole (+0x112cb) (0x0033ff08)
  38 0x7b8703ae in kernel32 (+0x503ae) (0x0033ffe8)
  39 0xb7e05587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d145c7 strstr+0x27 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (40 modules)
ELF     7b800000-7b91c000       Export          kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e639000-7e875000       Deferred        radeon_dri.so
ELF     7e875000-7e87c000       Deferred        libdrm.so.2
ELF     7e87c000-7e8eb000       Deferred        libgl.so.1
ELF     7e8eb000-7e8f0000       Deferred        libxdmcp.so.6
ELF     7e8f0000-7e9b9000       Deferred        libx11.so.6
ELF     7e9b9000-7e9c6000       Deferred        libxext.so.6
ELF     7e9c6000-7e9de000       Deferred        libice.so.6
ELF     7e9de000-7ea6b000       Export          winex11<elf>
  \-PE  7e9f0000-7ea6b000       \               winex11
ELF     7ea6b000-7ea89000       Deferred        libexpat.so.1
ELF     7ea89000-7eab8000       Deferred        libfontconfig.so.1
ELF     7eab8000-7eacc000       Deferred        libz.so.1
ELF     7eacc000-7eb36000       Deferred        libfreetype.so.6
ELF     7eb36000-7eb41000       Deferred        libgcc_s.so.1
ELF     7eb44000-7eb47000       Deferred        libxau.so.6
ELF     7eb47000-7eb50000       Deferred        libsm.so.6
ELF     7ec2f000-7ece5000       Export          gdi32<elf>
  \-PE  7ec40000-7ece5000       \               gdi32
ELF     7ece5000-7ee1d000       Export          user32<elf>
  \-PE  7ed00000-7ee1d000       \               user32
ELF     7ee1d000-7ee63000       Deferred        advapi32<elf>
  \-PE  7ee30000-7ee63000       \               advapi32
ELF     7ee63000-7ee96000       Export          wineconsole<elf>
  \-PE  7ee70000-7ee96000       \               wineconsole
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff2000-7eff7000       Deferred        libxxf86vm.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca3000-b7ca7000       Deferred        libdl.so.2
ELF     b7ca7000-b7ddb000       Export          libc.so.6
ELF     b7ddc000-b7def000       Deferred        libpthread.so.0
ELF     b7dfe000-b7f0f000       Export          libwine.so.1
ELF     b7f11000-b7f2c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\wineconsole.exe
        00000009    0 <==
```

---

### Post by scrooge_74 on 2007-01-22
any program in particular? it would seem it is looking for libraries.

Does the program you want to run is listed in winehq database as supported?

---

### Post by skate_metaly on 2007-01-22
not a particular problem .
it`s just for any program  i want to get runing
for example  dev-c++ 
it gives me the same error
borland c++ same error
trillian same error
and so long

---

### Post by scrooge_74 on 2007-01-22
did you try opening the programs inside the c:\windows directory that wine installs?

---

### Post by skate_metaly on 2007-01-22
sorry( i`m beginer in  ubuntu ; wine etc ) 
how do i start the program with the  c:/windows?

---

### Post by scrooge_74 on 2007-01-22
Open a terminal window

cd .wine/drive_c/windows

then 

wine notepad.exe

---

### Post by skate_metaly on 2007-01-22
it gives me this :

```
metaly@metaly:~$ cd .wine/drive_c/windows
metaly@metaly:~/.wine/drive_c/windows$ wine notepad.exe
libGL warning: 3D driver claims to not support visual 0x4b
wine: Unhandled page fault on read access to 0x7c226dc0 at address 0xb7dbe5c7 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x7c226dc0 in 32-bit code (0xb7dbe5c7).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7dbe5c7 ESP:0033ed98 EBP:0033edc8 EFLAGS:00010216(   - 00      -RIAP1)
 EAX:00000047 EBX:7e61253c ECX:7e60a82c EDX:7c226dc0
 ESI:00000047 EDI:7e60a859
Stack dump:
0x0033ed98:  7e6159c8 7e5d9b75 7e6159c8 7e60a81a
0x0033eda8:  0033edc8 7e5d85d4 7c1f06d8 7e60a243
0x0033edb8:  7e5d9afd 7e61253c 7e60a1b2 7c1f06d8
0x0033edc8:  0033ee48 7e5da636 7c226dc0 7e60a859
0x0033edd8:  0033ee34 7e60a07c 7e3cd34f 7c01bb90
0x0033ede8:  00000050 00000048 7c04d400 7c01cca8
Backtrace:
=>1 0xb7dbe5c7 strstr+0x27() in libc.so.6 (0x0033edc8)
  2 0x7e5da636 in winex11 (+0x3a636) (0x0033ee48)
  3 0x7e5da9c6 X11DRV_setup_opengl_visual+0x66() in winex11 (0x0033eed8)
  4 0x7e5eefdf in winex11 (+0x4efdf) (0x0033f028)
  5 0x7e5ff6b3 in winex11 (+0x5f6b3) (0x0033f048)
  6 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033f068)
  7 0x7bc390dc in ntdll (+0x290dc) (0x0033f118)
  8 0x7bc3957d in ntdll (+0x2957d) (0x0033f158)
  9 0x7bc3b487 LdrLoadDll+0x87() in ntdll (0x0033f188)
  10 0x7b861aeb in kernel32 (+0x41aeb) (0x0033f3d8)
  11 0x7b861d00 LoadLibraryExW+0x50() in kernel32 (0x0033f408)
  12 0x7b861e23 LoadLibraryExA+0x43() in kernel32 (0x0033f428)
  13 0x7b861e5d LoadLibraryA+0x2d() in kernel32 (0x0033f448)
  14 0x7e9f3bc0 DRIVER_load_driver+0x1c0() in gdi32 (0x0033f5b8)
  15 0x7e9ef5d0 CreateDCW+0x60() in gdi32 (0x0033f868)
  16 0x7eab8bd0 CreateIconFromResourceEx+0x420() in user32 (0x0033f908)
  17 0x7eab9567 in user32 (+0x29567) (0x0033f968)
  18 0x7eab9aab LoadImageW+0x3fb() in user32 (0x0033fa08)
  19 0x7eaba196 LoadImageA+0x56() in user32 (0x0033fae8)
  20 0x7eaba434 LoadCursorA+0x44() in user32 (0x0033fb18)
  21 0x7eab020f in user32 (+0x2020f) (0x0033fb38)
  22 0x7eab025d CLASS_RegisterBuiltinClasses+0x1d() in user32 (0x0033fb48)
  23 0x7eb243f2 in user32 (+0x943f2) (0x0033fbc8)
  24 0x7eb38343 in user32 (+0xa8343) (0x0033fbe8)
  25 0x7bc37de5 call_dll_entry_point+0x15() in ntdll (0x0033fc08)
  26 0x7bc390dc in ntdll (+0x290dc) (0x0033fcb8)
  27 0x7bc3957d in ntdll (+0x2957d) (0x0033fcf8)
  28 0x7bc394c2 in ntdll (+0x294c2) (0x0033fd38)
  29 0x7bc394c2 in ntdll (+0x294c2) (0x0033fd78)
  30 0x7bc394c2 in ntdll (+0x294c2) (0x0033fdb8)
  31 0x7bc394c2 in ntdll (+0x294c2) (0x0033fdf8)
  32 0x7bc394c2 in ntdll (+0x294c2) (0x0033fe38)
  33 0x7bc3c131 LdrInitializeThunk+0x371() in ntdll (0x0033ff08)
  34 0x7b87037a in kernel32 (+0x5037a) (0x0033ffe8)
  35 0xb7eaf587 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7dbe5c7 strstr+0x27 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (59 modules)
ELF     7b800000-7b91c000       Export          kernel32<elf>
  \-PE  7b820000-7b91c000       \               kernel32
ELF     7bc00000-7bc83000       Export          ntdll<elf>
  \-PE  7bc10000-7bc83000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e1e9000-7e425000       Deferred        radeon_dri.so
ELF     7e425000-7e42c000       Deferred        libdrm.so.2
ELF     7e42c000-7e49b000       Deferred        libgl.so.1
ELF     7e49b000-7e4a0000       Deferred        libxdmcp.so.6
ELF     7e4a0000-7e569000       Deferred        libx11.so.6
ELF     7e569000-7e576000       Deferred        libxext.so.6
ELF     7e576000-7e58e000       Deferred        libice.so.6
ELF     7e58e000-7e61b000       Export          winex11<elf>
  \-PE  7e5a0000-7e61b000       \               winex11
ELF     7e61b000-7e639000       Deferred        libexpat.so.1
ELF     7e639000-7e668000       Deferred        libfontconfig.so.1
ELF     7e668000-7e67c000       Deferred        libz.so.1
ELF     7e67c000-7e6e6000       Deferred        libfreetype.so.6
ELF     7e6e6000-7e74a000       Deferred        msvcrt<elf>
  \-PE  7e700000-7e74a000       \               msvcrt
ELF     7e74a000-7e77c000       Deferred        winspool<elf>
  \-PE  7e750000-7e77c000       \               winspool
ELF     7e77c000-7e83c000       Deferred        comctl32<elf>
  \-PE  7e790000-7e83c000       \               comctl32
ELF     7e83c000-7e84f000       Deferred        libresolv.so.2
ELF     7e84f000-7e86d000       Deferred        iphlpapi<elf>
  \-PE  7e860000-7e86d000       \               iphlpapi
ELF     7e86d000-7e8c1000       Deferred        rpcrt4<elf>
  \-PE  7e880000-7e8c1000       \               rpcrt4
ELF     7e8c1000-7e8cc000       Deferred        libgcc_s.so.1
ELF     7e8cf000-7e8d2000       Deferred        libxau.so.6
ELF     7e8d2000-7e8db000       Deferred        libsm.so.6
ELF     7e9ba000-7ea70000       Export          gdi32<elf>
  \-PE  7e9d0000-7ea70000       \               gdi32
ELF     7ea70000-7eba8000       Export          user32<elf>
  \-PE  7ea90000-7eba8000       \               user32
ELF     7eba8000-7ebee000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebee000       \               advapi32
ELF     7ebee000-7ec87000       Deferred        ole32<elf>
  \-PE  7ec00000-7ec87000       \               ole32
ELF     7ec87000-7ecdf000       Deferred        shlwapi<elf>
  \-PE  7eca0000-7ecdf000       \               shlwapi
ELF     7ecdf000-7edd1000       Deferred        shell32<elf>
  \-PE  7ecf0000-7edd1000       \               shell32
ELF     7edd1000-7ee71000       Deferred        comdlg32<elf>
  \-PE  7ede0000-7ee71000       \               comdlg32
ELF     7ee71000-7eea0000       Deferred        notepad<elf>
  \-PE  7ee80000-7eea0000       \               notepad
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff1000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d43000-b7d4c000       Deferred        libnss_compat.so.2
ELF     b7d4d000-b7d51000       Deferred        libdl.so.2
ELF     b7d51000-b7e85000       Export          libc.so.6
ELF     b7e86000-b7e99000       Deferred        libpthread.so.0
ELF     b7ea8000-b7fb9000       Export          libwine.so.1
ELF     b7fbb000-b7fd6000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\notepad.exe
        00000009    0 <==
metaly@metaly:~/.wine/drive_c/windows$ 


```

---

### Post by scrooge_74 on 2007-01-22
in a terminal just type winecfg it should open a console to make changes to wine.

From the top of the error message it seems some problem with your video card.

What card you have?  It says something abot 3D, do you have 3D acceleration enable?

---

### Post by skate_metaly on 2007-01-22
if i start winecfg 
it gives me the same output . but it start winecfg

i have compiz runing but  not the original drivers because it crash down my video card
if i to the glxinfo | grep rendering . it  tels me that it`s yes
i have a 
Ati Mobility M6 LY (Ati Radeon 9000) video board
and compiz runing(if this would be a help ...dunno why)

---

### Post by scrooge_74 on 2007-01-22
I saw in another thread that this could be giving you the problem.

Try playing with the video config of wine maybe that will fix some of the error messages.  This something that you have to config my PC at a time, it wont give the same results on my equipment.

sorry I cant be of much help.

Did you check the program you want to use in [winehq app database?]("http://appdb.winehq.org/")

---

### Post by fredster001 on 2007-01-22
dont know about the others, but DevC++ won't work on linux, but there are other compilers available. I tried multiple times with that as well. 

fredster001

---

### Post by skate_metaly on 2007-01-22
i took the winrar 3.62 with in winehq is ok. 
at the graphics : 
i disabled DirectX apps to stop the mouse leaving their windows
disabled the allow the window manager to control the windows
disabled the emualte a virtual desktop 
and vertex shader support : emulated
and disabled allow pixel shader 
same error
so i neeed wingoz...not again:-<
but reallly really tenx for the help;)

---

