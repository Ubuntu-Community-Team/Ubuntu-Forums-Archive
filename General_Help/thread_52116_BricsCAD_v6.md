---
title: "BricsCAD v6"
date: 2005-07-26
forum: General Help
---

### Post by Dgurion on 2005-07-26
Well, I am contemplating about installing BricsCAD v6 which has support for Redhat9 Fedora Cores 1,2,3.. but it doesn't say anything about the other linux distros, I am wondering if this program would work on my Ubuntu installation.

---

### Post by cutecuervo on 2006-03-27
I downloaded the trial version and used alien to make it a debian. Installation looked normal, no error messages. It needs wine to work so I installed it. I dony no how to launch it. This is my second week using any linux and still getting used to it. If I can't get this program to work I'll be stuck with windows thanks to Autodesk. If you have any luck please posst. Thanks.

---

### Post by mattster2002 on 2007-03-01
Hey cutecuervo - I tried today to install BricsCAD and ran into the same problems as you. I removed WINE and installed an older version (0.9.17) and it worked fine.

So just grab an older package from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) (I used the package from there) and everything seems to work nice ad sweet.

---

### Post by Leloup on 2007-03-04
Hi, I tried with wine 9.17 but bricscad ask me a serial number, even if it's the demo version...And i have to know if it works before to by it, so how can i do?
Thanks
(hope my english is not too bad... ;))

---

### Post by mattster2002 on 2007-03-07
Hey mate,
I encountered the same problem - I contacted BricsCAD and they sent me thru a serial that is an evaluation key (only lasts 30 days).

It is

8HLH-4KGU-6DKF-PWZB-1RVN


I must say, I have encountered a few problems along the way however BricsCAD support is second to none. I'll keep you guys updated

---

### Post by Leloup on 2007-03-12
Yes, it works "better", i see the bricscad logo ;) ....The terminal send me this : 
fixme:ole:CoRegisterMessageFilter stub
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  245
  Current serial number in output stream:  245
Maybe a problem with my graphic card?

---

### Post by theferretguy on 2007-08-30
Installed with the .deb and alien with wine 9.17 but got this:

sudo alien --scripts -i Bricscad-6.0.0020-1.en_US.i386.rpm 
wine: Unhandled page fault on read access to 0x00000204 at address 0xb7f2725d (thread 0009), starting debugger...
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\regapp.exe.so
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\mfc42.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\mfc42.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\regapp.exe.so
Unhandled exception: page fault on read access to 0x00000204 in 32-bit code (0xb7f2725d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:b7f2725d ESP:7fb7f570 EBP:7fb7f598 EFLAGS:00210292(   - 00      -RISA1)
 EAX:b7f2ece0 EBX:b7f2eff4 ECX:b7f21f89 EDX:b7d8c6bc
 ESI:00000000 EDI:00000000
Stack dump:
0x7fb7f570:  00000024 b7ed26e0 b7ed22a8 b7ef9f84
0x7fb7f580:  b7d8d49c b7ef9a08 00000001 b7d8fff4
0x7fb7f590:  00000000 7c003138 7fb7f5a8 b7d8dcc4
0x7fb7f5a0:  00000000 b7f2eff4 7fb7f688 b7f21fa6
0x7fb7f5b0:  00000000 00000000 00000000 00000001
0x7fb7f5c0:  7c003140 7c003148 7c003144 b7d8c6bc
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0xb7f2725d in ld-linux.so.2 (+0x1225d) (0xb7f2725d)
  2 0xb7d8dcc4 GLIBC_2+0xcc4 in libdl.so.2 (0xb7d8dcc4)
  3 0xb7f21fa6 in ld-linux.so.2 (+0xcfa6) (0xb7f21fa6)
  4 0xb7d8e2ac in libdl.so.2 (+0x12ac) (0xb7d8e2ac)
  5 0xb7d8dcfa GLIBC_2+0xcfa in libdl.so.2 (0xb7d8dcfa)
  6 0xb7efd05b wine_get_es+0xa5f in libwine.so.1 (0xb7efd05b)
  7 0xb7efd11a wine_get_es+0xb1e in libwine.so.1 (0xb7efd11a)
  8 0x7ff992a5 in ntdll (+0x292a5) (0x7ff992a5)
  9 0x7ff9a0a4 LdrUnloadDll+0x1cb in ntdll (0x7ff9a0a4)
  10 0x7fc3d4f1 FreeLibrary+0x3f in kernel32 (0x7fc3d4f1)
  11 0x7e9f8838 _Z22_AfxInitCommonControlsP23tagINITCOMMONCONTROLSEXl+0x78 in libmfc42<elf> (0x7e9f8838)
  12 0x7e9fa252 _Z24AfxEndDeferRegisterClassl+0x392 in libmfc42<elf> (0x7e9fa252)
  13 0x7e97543c _ZN4CWnd17CreateDlgIndirectEPK14tagDLGTEMPLATEPS_P11HINSTANCE__+0x3c in libmfc42<elf> (0x7e97543c)
  14 0x7e975ee5 _ZN7CDialog7DoModalEv+0xf5 in libmfc42<elf> (0x7e975ee5)
  15 0x7e3249cd checkLicenseFromInstaller+0x11d in licensemanager3<elf> (0x7e3249cd)
  16 0x7eab41b2 (0x7eab41b2)
  17 0x7fb8d14e main+0x7e in regapp<elf> (0x7fb8d14e)
  18 0x7fb9e0fc __wine_spec_exe_entry+0x8c in regapp<elf> (0x7fb9e0fc)
  19 0x7fc4b94f in kernel32 (+0x4b94f) (0x7fc4b94f)
  20 0xb7efe523 wine_switch_to_stack+0x17 in libwine.so.1 (0xb7efe523)
0xb7f2725d: testb       $0x8,0x204(%edi)
Modules:
Module  Address                 Debug info      Name (94 modules)
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e07c000-7e0cd000       Deferred        libgcrypt.so.11
ELF     7e0cd000-7e0e2000       Deferred        libtasn1.so.3
ELF     7e0e2000-7e110000       Deferred        libcrypt.so.1
ELF     7e11f000-7e18f000       Deferred        libgnutls.so.13
ELF     7e18f000-7e1c0000       Deferred        libcups.so.2
ELF     7e204000-7e208000       Deferred        libgpg-error.so.0
ELF     7e219000-7e24a000       Deferred        uxtheme<elf>
  \-PE  7e220000-7e24a000       \               uxtheme
ELF     7e24a000-7e318000       Deferred        libstd<elf>
ELF     7e318000-7e34a000       Export          licensemanager3<elf>
  \-PE  7e330000-7e34a000       \               licensemanager3
ELF     7e354000-7e373000       Deferred        mpr<elf>
  \-PE  7e360000-7e373000       \               mpr
ELF     7e373000-7e3ba000       Deferred        wininet<elf>
  \-PE  7e380000-7e3ba000       \               wininet
ELF     7e3ba000-7e3db000       Deferred        cabinet<elf>
  \-PE  7e3c0000-7e3db000       \               cabinet
ELF     7e3db000-7e40c000       Deferred        urlmon<elf>
  \-PE  7e3e0000-7e40c000       \               urlmon
ELF     7e40c000-7e426000       Deferred        oledlg<elf>
  \-PE  7e410000-7e426000       \               oledlg
ELF     7e426000-7e4b6000       Deferred        oleaut32<elf>
  \-PE  7e440000-7e4b6000       \               oleaut32
ELF     7e4b6000-7e4ca000       Deferred        olepro32<elf>
  \-PE  7e4c0000-7e4ca000       \               olepro32
ELF     7e4ca000-7e4f9000       Deferred        winspool<elf>
  \-PE  7e4d0000-7e4f9000       \               winspool
ELF     7e4f9000-7e5bb000       Deferred        comctl32<elf>
  \-PE  7e500000-7e5bb000       \               comctl32
ELF     7e5bb000-7e5da000       Deferred        iphlpapi<elf>
  \-PE  7e5c0000-7e5da000       \               iphlpapi
ELF     7e5da000-7e627000       Deferred        rpcrt4<elf>
  \-PE  7e5f0000-7e627000       \               rpcrt4
ELF     7e627000-7e6b6000       Deferred        ole32<elf>
  \-PE  7e640000-7e6b6000       \               ole32
ELF     7e6b6000-7e70c000       Deferred        shlwapi<elf>
  \-PE  7e6c0000-7e70c000       \               shlwapi
ELF     7e70c000-7e7e5000       Deferred        shell32<elf>
  \-PE  7e720000-7e7e5000       \               shell32
ELF     7e7e5000-7e880000       Deferred        comdlg32<elf>
  \-PE  7e7f0000-7e880000       \               comdlg32
ELF     7e880000-7eab3000       Export          libmfc42<elf>
  \-PE  7ea30000-7eab3000       \               mfc42
PE      7eac0000-7eac7000       --none--        regapp
ELF     7eac9000-7eace000       Deferred        libxfixes.so.3
ELF     7eace000-7ead7000       Deferred        libxcursor.so.1
ELF     7ead7000-7eaf3000       Deferred        imm32<elf>
  \-PE  7eae0000-7eaf3000       \               imm32
ELF     7eaf3000-7eaf9000       Deferred        libxrandr.so.2
ELF     7eaf9000-7eb01000       Deferred        libxrender.so.1
ELF     7eb03000-7eb05000       Deferred        libnvidia-tls.so.1
ELF     7eb05000-7f38b000       Deferred        libglcore.so.1
ELF     7f38b000-7f417000       Deferred        libgl.so.1
ELF     7f417000-7f41c000       Deferred        libxdmcp.so.6
ELF     7f41c000-7f41f000       Deferred        libxau.so.6
ELF     7f41f000-7f510000       Deferred        libx11.so.6
ELF     7f510000-7f51e000       Deferred        libxext.so.6
ELF     7f51e000-7f523000       Deferred        libxxf86vm.so.1
ELF     7f523000-7f528000       Deferred        libxxf86dga.so.1
ELF     7f528000-7f540000       Deferred        libice.so.6
ELF     7f540000-7f549000       Deferred        libsm.so.6
ELF     7f549000-7f5cc000       Deferred        winex11<elf>
  \-PE  7f560000-7f5cc000       \               winex11
ELF     7f61b000-7f63b000       Deferred        libexpat.so.1
ELF     7f63b000-7f666000       Deferred        libfontconfig.so.1
ELF     7f666000-7f67a000       Deferred        libz.so.1
ELF     7f67a000-7f6e5000       Deferred        libfreetype.so.6
ELF     7f6e5000-7f746000       Deferred        msvcrt<elf>
  \-PE  7f6f0000-7f746000       \               msvcrt
ELF     7f746000-7f788000       Deferred        advapi32<elf>
  \-PE  7f750000-7f788000       \               advapi32
ELF     7f788000-7f794000       Deferred        libgcc_s.so.1
ELF     7f88d000-7f93e000       Deferred        gdi32<elf>
  \-PE  7f8a0000-7f93e000       \               gdi32
ELF     7f93e000-7fa70000       Deferred        user32<elf>
  \-PE  7f960000-7fa70000       \               user32
ELF     7fb8c000-7fba0000       Export          regapp<elf>
ELF     7fb90000-7fba0000       Export          regapp<elf>
ELF     7fbdf000-7fce0000       Export          kernel32<elf>
  \-PE  7fc00000-7fce0000       \               kernel32
ELF     7fdfc000-7fe07000       Deferred        libnss_files.so.2
ELF     7fe07000-7fe11000       Deferred        libnss_nis.so.2
ELF     7fe11000-7fe28000       Deferred        libnsl.so.1
ELF     7fe28000-7fe31000       Deferred        libnss_compat.so.2
ELF     7fe43000-7fe6a000       Deferred        libm.so.6
ELF     7fe6a000-7ff62000       Deferred        libwine_unicode.so.1
ELF     7ff62000-7ffe0000       Export          ntdll<elf>
  \-PE  7ff70000-7ffe0000       \               ntdll
ELF     b7d8d000-b7d91000       Export          libdl.so.2
ELF     b7d91000-b7ed2000       Deferred        libc.so.6
ELF     b7ed3000-b7eea000       Deferred        libpthread.so.0
ELF     b7ef9000-b7f13000       Export          libwine.so.1
ELF     b7f15000-b7f30000       Export          ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) c:\windows\system32\regapp.exe.so
        00000009    0 <==
wine client error:9: write: Bad file descriptor
cat: /opt/bricscad/release.txt: No such file or directory

---

