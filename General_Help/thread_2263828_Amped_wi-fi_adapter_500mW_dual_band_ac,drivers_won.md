---
title: "Amped wi-fi adapter 500mW dual band ac,drivers wont load up with kali"
date: 2015-02-03
forum: General Help
---

### Post by memasonman on 2015-02-03
hi i just bought a Amped wi-fi adapter 500mW dual band ac,and when i try installing the drivers on kali i get this.




Unhandled exception: unimplemented function setupapi.dll.SetupAddToSourceListA called in 32-bit code (0x7b83b581).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83b581 ESP:0033f8b8 EBP:0033f91c EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b827b45 EBX:7b8a5ff4 ECX:00000000 EDX:0033f93c
 ESI:0033f93c EDI:00000006
Stack dump:
0x0033f8b8:  0033f93c 00000008 00000000 80000100
0x0033f8c8:  00000001 00000000 7b83b581 00000002
0x0033f8d8:  7edab540 7edac77b 7ee04b40 00000006
0x0033f8e8:  0033f908 7bc58dc1 00000044 00000000
0x0033f8f8:  7bc58dc1 7bcb7ff4 7bcb7ff4 7ee04b40
0x0033f908:  0033f928 7bc40eca 00000000 7b83b539
Backtrace:
=>0 0x7b83b581 in kernel32 (+0x2b581) (0x0033f91c)
  1 0x7edab508 in setupapi (+0x3b507) (0x0033f94c)
  2 0x7ed818e5 in setupapi (+0x118e4) (0x00000006)
  3 0x00403945 in setdrv (+0x3944) (0x00000006)
0x7b83b581: movl    0xfffffffc(%ebp),%ebx
Modules:
Module    Address            Debug info    Name (77 modules)
PE      400000-  40a000    Export          setdrv
ELF    7b800000-7ba3a000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba3a000    \               kernel32
ELF    7bc00000-7bcd4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcd4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e234000-7e2d2000    Deferred        msvcrt<elf>
  \-PE    7e250000-7e2d2000    \               msvcrt
ELF    7e2d2000-7e2db000    Deferred        librt.so.1
ELF    7e2db000-7e327000    Deferred        libdbus-1.so.3
ELF    7e327000-7e339000    Deferred        libp11-kit.so.0
ELF    7e339000-7e3be000    Deferred        libgcrypt.so.11
ELF    7e3be000-7e3d0000    Deferred        libtasn1.so.3
ELF    7e3d0000-7e3e4000    Deferred        libresolv.so.2
ELF    7e3e4000-7e3e9000    Deferred        libkeyutils.so.1
ELF    7e3e9000-7e3f2000    Deferred        libkrb5support.so.0
ELF    7e3f2000-7e41c000    Deferred        libk5crypto.so.3
ELF    7e41c000-7e4ee000    Deferred        libkrb5.so.3
ELF    7e4ee000-7e500000    Deferred        libavahi-client.so.3
ELF    7e500000-7e5c9000    Deferred        libgnutls.so.26
ELF    7e5c9000-7e607000    Deferred        libgssapi_krb5.so.2
ELF    7e607000-7e65d000    Deferred        libcups.so.2
ELF    7e665000-7e676000    Deferred        gnome-keyring-pkcs11.so
ELF    7e676000-7e67c000    Deferred        libxfixes.so.3
ELF    7e67c000-7e686000    Deferred        libxcursor.so.1
ELF    7e686000-7e68a000    Deferred        libgpg-error.so.0
ELF    7e68a000-7e68f000    Deferred        libcom_err.so.2
ELF    7e68f000-7e69d000    Deferred        libavahi-common.so.3
ELF    7e6bd000-7e6e5000    Deferred        libexpat.so.1
ELF    7e6e5000-7e71b000    Deferred        libfontconfig.so.1
ELF    7e71b000-7e72a000    Deferred        libxi.so.6
ELF    7e72a000-7e72d000    Deferred        libxcomposite.so.1
ELF    7e72d000-7e735000    Deferred        libxrandr.so.2
ELF    7e735000-7e73f000    Deferred        libxrender.so.1
ELF    7e73f000-7e745000    Deferred        libxxf86vm.so.1
ELF    7e745000-7e748000    Deferred        libxinerama.so.1
ELF    7e748000-7e76c000    Deferred        imm32<elf>
  \-PE    7e750000-7e76c000    \               imm32
ELF    7e76c000-7e772000    Deferred        libxdmcp.so.6
ELF    7e772000-7e795000    Deferred        libxcb.so.1
ELF    7e795000-7e79b000    Deferred        libuuid.so.1
ELF    7e79b000-7e8d3000    Deferred        libx11.so.6
ELF    7e8d3000-7e8e5000    Deferred        libxext.so.6
ELF    7e8e5000-7e8fe000    Deferred        libice.so.6
ELF    7e8fe000-7e906000    Deferred        libsm.so.6
ELF    7e906000-7e9a2000    Deferred        winex11<elf>
  \-PE    7e910000-7e9a2000    \               winex11
ELF    7e9a2000-7e9bb000    Deferred        libz.so.1
ELF    7e9bb000-7ea57000    Deferred        libfreetype.so.6
ELF    7ea70000-7eaf0000    Deferred        rpcrt4<elf>
  \-PE    7ea80000-7eaf0000    \               rpcrt4
ELF    7eaf0000-7eb0a000    Deferred        version<elf>
  \-PE    7eb00000-7eb0a000    \               version
ELF    7eb0a000-7ebd7000    Deferred        gdi32<elf>
  \-PE    7eb20000-7ebd7000    \               gdi32
ELF    7ebd7000-7ed2b000    Deferred        user32<elf>
  \-PE    7ebf0000-7ed2b000    \               user32
ELF    7ed2b000-7ed68000    Deferred        winspool<elf>
  \-PE    7ed30000-7ed68000    \               winspool
ELF    7ed68000-7edd5000    Dwarf           setupapi<elf>
  \-PE    7ed70000-7edd5000    \               setupapi
ELF    7edd5000-7ee41000    Deferred        advapi32<elf>
  \-PE    7ede0000-7ee41000    \               advapi32
ELF    7ee41000-7ee4d000    Deferred        libnss_files.so.2
ELF    7ee4d000-7ee64000    Deferred        libnsl.so.1
ELF    7ee64000-7ee7d000    Deferred        cfgmgr32<elf>
  \-PE    7ee70000-7ee7d000    \               cfgmgr32
ELF    7efda000-7f000000    Deferred        libm.so.6
ELF    b74c0000-b74c3000    Deferred        libxau.so.6
ELF    b74c3000-b74ce000    Deferred        libnss_nis.so.2
ELF    b74cf000-b74d3000    Deferred        libdl.so.2
ELF    b74d3000-b7636000    Deferred        libc.so.6
ELF    b7637000-b7650000    Deferred        libpthread.so.0
ELF    b7650000-b7793000    Dwarf           libwine.so.1
ELF    b7793000-b779b000    Deferred        libnss_compat.so.2
ELF    b77ae000-b77cc000    Deferred        ld-linux.so.2
ELF    b77cc000-b77cd000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000c services.exe
    00000029    0
    00000028    0
    0000000e    0
    0000000d    0
00000012 explorer.exe
    00000013    0
00000025 winedevice.exe
    0000002c    0
    0000002b    0
    00000027    0
    00000026    0
0000002d autorun.exe
    00000032    0
    00000031    0
    0000002f    0
    0000002e    0
00000035 setup.exe
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
00000043 (D) C:\Program Files\Amped Wireless ACA1 Wi-Fi Driver\Driver\SetDrv.exe
    00000044    0 <==
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.14-kali1-686-pae



can anyone tell me why and whats wrong ,please,thnx

---

