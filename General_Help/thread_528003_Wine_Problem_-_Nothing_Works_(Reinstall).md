---
title: "Wine Problem - Nothing Works (Reinstall?)"
date: 2007-08-17
forum: General Help
---

### Post by kasio on 2007-08-17
Hi,

Somehow, I've managed to mess up my wine install bad.

When I start any program with wine I get the following in terminal:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
wine: Unhandled page fault on read access to 0x36b84510 at address 0x36b84510 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x36b84510 in 32-bit code (0x36b84510).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:36b84510 ESP:0033c6f8 EBP:0033e7dc EFLAGS:00210202(   - 00      - -RI1)
 EAX:36b84510 EBX:b7e1aff4 ECX:00000000 EDX:0033e7c0
 ESI:0033ee18 EDI:b7e1b580
Stack dump:
0x0033c6f8:  b7d2b846 0033e7c0 b7e2d070 b7e1b580
0x0033c708:  7e6278b0 0033e718 00000032 00000001
0x0033c718:  62696c58 6520203a 6e657478 6e6f6973
0x0033c728:  4c472220 6d202258 69737369 6f20676e
0x0033c738:  6964206e 616c7073 3a222079 22302e30
0x0033c748:  00000a2e 00000000 00000000 00000000
Backtrace:
=>1 0x36b84510 (0x0033e7dc)
  2 0xb7d27586 _IO_vfprintf+0x76() in libc.so.6 (0x0033edf0)
  3 0xb7d30362 fprintf+0x22() in libc.so.6 (0x0033ee08)
  4 0x7e6272c7 in libxext.so.6 (+0xc2c7) (0x0033ee28)
  5 0x7e62725b XMissingExtension+0x3b() in libxext.so.6 (0x0033ee48)
  6 0x7e4d9578 in libgl.so.1 (+0x30578) (0x7c078338)
  7 0x7c01ce28 (0x00000000)
0x36b84510: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (50 modules)
PE        400000-  419000       Deferred        setup
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7dd58000-7e4a9000       Deferred        libglcore.so.1
ELF     7e4a9000-7e522000       Export          libgl.so.1
ELF     7e522000-7e527000       Deferred        libxdmcp.so.6
ELF     7e527000-7e52a000       Deferred        libxau.so.6
ELF     7e52a000-7e61b000       Deferred        libx11.so.6
ELF     7e61b000-7e629000       Export          libxext.so.6
ELF     7e629000-7e62e000       Deferred        libxxf86vm.so.1
ELF     7e62e000-7e646000       Deferred        libice.so.6
ELF     7e646000-7e64f000       Deferred        libsm.so.6
ELF     7e663000-7e6ed000       Deferred        winex11<elf>
  \-PE  7e670000-7e6ed000       \               winex11
ELF     7e7f2000-7e812000       Deferred        libexpat.so.1
ELF     7e812000-7e83d000       Deferred        libfontconfig.so.1
ELF     7e83d000-7e851000       Deferred        libz.so.1
ELF     7e851000-7e8c1000       Deferred        libfreetype.so.6
ELF     7e8c1000-7e97e000       Deferred        comctl32<elf>
  \-PE  7e8d0000-7e97e000       \               comctl32
ELF     7e97e000-7e990000       Deferred        libresolv.so.2
ELF     7e990000-7e9ae000       Deferred        iphlpapi<elf>
  \-PE  7e9a0000-7e9ae000       \               iphlpapi
ELF     7e9ae000-7ea07000       Deferred        rpcrt4<elf>
  \-PE  7e9c0000-7ea07000       \               rpcrt4
ELF     7ea07000-7eaa6000       Deferred        ole32<elf>
  \-PE  7ea20000-7eaa6000       \               ole32
ELF     7eaa6000-7eb44000       Deferred        oleaut32<elf>
  \-PE  7eac0000-7eb44000       \               oleaut32
ELF     7eb44000-7eb8c000       Deferred        advapi32<elf>
  \-PE  7eb50000-7eb8c000       \               advapi32
ELF     7eb8c000-7eb98000       Deferred        libgcc_s.so.1
ELF     7ec96000-7ed56000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed56000       \               gdi32
ELF     7ed56000-7ee94000       Deferred        user32<elf>
  \-PE  7ed70000-7ee94000       \               user32
ELF     7efa6000-7efb0000       Deferred        libnss_files.so.2
ELF     7efb0000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     7efec000-7efee000       Deferred        libnvidia-tls.so.1
ELF     7efee000-7eff8000       Deferred        libnss_nis.so.2
ELF     7eff8000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ce7000-b7ceb000       Deferred        libdl.so.2
ELF     b7ceb000-b7e1f000       Export          libc.so.6
ELF     b7e20000-b7e37000       Deferred        libpthread.so.0
ELF     b7e4b000-b7f5f000       Deferred        libwine.so.1
ELF     b7f60000-b7f7c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\kasio\setup.exe
        00000009    0 <==


```

I'm using Wine 0.9.43. The icons for Notepad, Wine Configure, File Browser etc. have disappeared from my menus. Even when I reinstall wine through synaptic, it stays the same.

Can some1 help me?

---

### Post by Vince4Amy on 2007-08-17
What was the last thing you did before WINE broke?

---

### Post by kasio on 2007-08-17
I have no idea. I think I was trying to uninstall it from Automatix and then reinstall using Synaptic.

---

### Post by kasio on 2007-08-17
bump

need this quickly

---

### Post by diatribe on 2007-08-17
go to synaptic and use the complete removal option and see if it works.  also automatix is not necessary to install wine

---

### Post by kasio on 2007-08-17
still didn't work

---

### Post by kasio on 2007-08-18
bump

---

