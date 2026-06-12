---
title: "[SOLVED] Need help with Wine!"
date: 2007-09-07
forum: General Help
---

### Post by Amazona aestiva on 2007-09-07
I'd like to run Protel 99 SE Service Pack 6 under wine.

Now Wine 0.9.44 installs it but I get this when try to run:
> nandor@nandor-desktop:~$ wine '/home/nandor/.wine/drive_c/Program Files/Design Explorer 99 SE/Client99SE.exe'
Warning: the specified Windows directory L"%SystemRoot%" is not accessible.
Warning: the specified Windows directory L"%SystemRoot%" is not accessible.
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7b843f40 (thread 0009), starting debugger...
Warning: the specified Windows directory L"%SystemRoot%" is not accessible.
First chance exception: 0xc0000025 in 32-bit code (0x7bc39a7c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc39a7c ESP:0033f8f4 EBP:0033f958 EFLAGS:00000282(   - 00      - -IS1)
 EAX:0033f900 EBX:7bc8497c ECX:00110020 EDX:0033fce0
 ESI:0033fce0 EDI:0033f964
Stack dump:
0x0033f8f4:  7bc60b2a 00000005 0033fa24 c0000025
0x0033f904:  00000001 0033fce0 00000003 00000000
0x0033f914:  7bc8497c 00000000 0033f9c4 0033fa00
0x0033f924:  7bc60dd9 00000002 0033f944 00000000
0x0033f934:  00135188 00000004 7b88c830 0033f944
0x0033f944:  00000000 00000000 7ee17c24 7bc39a30
Backtrace:
=>1 0x7bc39a7c __regs_RtlRaiseException+0x4c() in ntdll (0x0033f958)
  2 0x7bc72623 in ntdll (+0x62623) (0x0033fcbc)
  3 0x7bc39046 RtlRaiseException+0x6() in ntdll (0x0033fd34)
  4 0x005086a8 in csrtl50.bpl (+0x86a8) (0x0033fd88)
  5 0x00508b91 in csrtl50.bpl (+0x8b91) (0x0033fdc8)
  6 0x00511e3f in csrtl50.bpl (+0x11e3f) (0x0033fdec)
  7 0x40004766 in vcl50.bpl (+0x4766) (0x0033ff08)
  8 0x7b874cce in kernel32 (+0x54cce) (0x0033ffe8)
  9 0xb7eaa9a7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc39a7c __regs_RtlRaiseException+0x4c in ntdll: subl $4,%esp
Modules:
Module  Address                 Debug info      Name (101 modules)
PE        340000-  3f8000       Deferred        protelcomponents50.bpl
PE        400000-  4ff000       Deferred        client99se
PE        500000-  5c8000       Export          csrtl50.bpl
PE      40000000-401f2000       Export          vcl50.bpl
PE      402f0000-40333000       Deferred        vclx50.bpl
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Export          ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c6fa000-7c70f000       Deferred        midimap<elf>
  \-PE  7c700000-7c70f000       \               midimap
ELF     7c70f000-7c735000       Deferred        msacm32<elf>
  \-PE  7c720000-7c735000       \               msacm32
ELF     7c735000-7c7fa000       Deferred        libasound.so.2
ELF     7c7fa000-7c82f000       Deferred        winealsa<elf>
  \-PE  7c810000-7c82f000       \               winealsa
ELF     7c82f000-7c880000       Deferred        libgcrypt.so.11
ELF     7c880000-7c895000       Deferred        libtasn1.so.3
ELF     7c895000-7c8c3000       Deferred        libcrypt.so.1
ELF     7c8c3000-7c933000       Deferred        libgnutls.so.13
ELF     7c933000-7c964000       Deferred        libcups.so.2
ELF     7d0f2000-7d124000       Deferred        uxtheme<elf>
  \-PE  7d100000-7d124000       \               uxtheme
ELF     7d371000-7d389000       Deferred        msacm32<elf>
  \-PE  7d380000-7d389000       \               msacm32
ELF     7d389000-7d38e000       Deferred        libxfixes.so.3
ELF     7d38e000-7d397000       Deferred        libxcursor.so.1
ELF     7d397000-7d3b4000       Deferred        imm32<elf>
  \-PE  7d3a0000-7d3b4000       \               imm32
ELF     7d3b4000-7d3bc000       Deferred        libxrender.so.1
ELF     7d3c7000-7d3cb000       Deferred        libgpg-error.so.0
ELF     7d8f3000-7e179000       Deferred        libglcore.so.1
ELF     7e179000-7e205000       Deferred        libgl.so.1
ELF     7e205000-7e20a000       Deferred        libxdmcp.so.6
ELF     7e20a000-7e2fb000       Deferred        libx11.so.6
ELF     7e2fb000-7e309000       Deferred        libxext.so.6
ELF     7e309000-7e30e000       Deferred        libxxf86vm.so.1
ELF     7e30e000-7e326000       Deferred        libice.so.6
ELF     7e326000-7e32f000       Deferred        libsm.so.6
ELF     7e32f000-7e335000       Deferred        libxrandr.so.2
ELF     7e340000-7e3ca000       Deferred        winex11<elf>
  \-PE  7e350000-7e3ca000       \               winex11
ELF     7e434000-7e454000       Deferred        libexpat.so.1
ELF     7e454000-7e47f000       Deferred        libfontconfig.so.1
ELF     7e47f000-7e493000       Deferred        libz.so.1
ELF     7e493000-7e4fe000       Deferred        libfreetype.so.6
ELF     7e4fe000-7e524000       Deferred        odbc32<elf>
  \-PE  7e510000-7e524000       \               odbc32
ELF     7e524000-7e5b2000       Deferred        winmm<elf>
  \-PE  7e530000-7e5b2000       \               winmm
ELF     7e5b2000-7e5d4000       Deferred        oledlg<elf>
  \-PE  7e5c0000-7e5d4000       \               oledlg
ELF     7e5d4000-7e601000       Deferred        ws2_32<elf>
  \-PE  7e5e0000-7e601000       \               ws2_32
ELF     7e601000-7e61b000       Deferred        wsock32<elf>
  \-PE  7e610000-7e61b000       \               wsock32
ELF     7e61b000-7e650000       Deferred        winspool<elf>
  \-PE  7e620000-7e650000       \               winspool
ELF     7e650000-7e6a9000       Deferred        shlwapi<elf>
  \-PE  7e660000-7e6a9000       \               shlwapi
ELF     7e6a9000-7e7ac000       Deferred        shell32<elf>
  \-PE  7e6c0000-7e7ac000       \               shell32
ELF     7e7ac000-7e84d000       Deferred        comdlg32<elf>
  \-PE  7e7b0000-7e84d000       \               comdlg32
ELF     7e84d000-7e90b000       Deferred        comctl32<elf>
  \-PE  7e860000-7e90b000       \               comctl32
ELF     7e90b000-7e91f000       Deferred        lz32<elf>
  \-PE  7e910000-7e91f000       \               lz32
ELF     7e91f000-7e939000       Deferred        version<elf>
  \-PE  7e930000-7e939000       \               version
ELF     7e939000-7e959000       Deferred        mpr<elf>
  \-PE  7e940000-7e959000       \               mpr
ELF     7e959000-7e96c000       Deferred        libresolv.so.2
ELF     7e96c000-7e98a000       Deferred        iphlpapi<elf>
  \-PE  7e970000-7e98a000       \               iphlpapi
ELF     7e98a000-7e9e3000       Deferred        rpcrt4<elf>
  \-PE  7e9a0000-7e9e3000       \               rpcrt4
ELF     7e9e3000-7ea82000       Deferred        ole32<elf>
  \-PE  7e9f0000-7ea82000       \               ole32
ELF     7ea82000-7eb20000       Deferred        oleaut32<elf>
  \-PE  7ea90000-7eb20000       \               oleaut32
ELF     7eb20000-7eb68000       Deferred        advapi32<elf>
  \-PE  7eb30000-7eb68000       \               advapi32
ELF     7eb68000-7eb74000       Deferred        libgcc_s.so.1
ELF     7ec5e000-7ec61000       Deferred        libxau.so.6
ELF     7ec6f000-7ed2f000       Deferred        gdi32<elf>
  \-PE  7ec90000-7ed2f000       \               gdi32
ELF     7ed2f000-7ee6d000       Deferred        user32<elf>
  \-PE  7ed50000-7ee6d000       \               user32
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7efef000-7eff1000       Deferred        libnvidia-tls.so.1
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d35000-b7d39000       Deferred        libdl.so.2
ELF     b7d39000-b7e7a000       Deferred        libc.so.6
ELF     b7e7b000-b7e92000       Deferred        libpthread.so.0
ELF     b7ea3000-b7fb7000       Export          libwine.so.1
ELF     b7fb9000-b7fd4000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\Design Explorer 99 SE\Client99SE.exe
        00000009    0 <==
nandor@nandor-desktop:~$


Is there anybody who understands this?

Thanks for reading...

---

### Post by hikaricore on 2007-09-07
[http://appdb.winehq.org/appview.php?iVersionId=4910](http://appdb.winehq.org/appview.php?iVersionId=4910)

Everything after the first few lines is junk (as far as we need to be concerned).

The main issue is at the top and printed about 3 times:

> Warning: the specified Windows directory L"%SystemRoot%" is not accessible.

You may want to run:

```
winecfg
```

as well as 

```
wineprefixcreate
```

To make sure wine is configured properly and all the directories exist.  Otherwise I know nothing of this software so check the link I provided.

**P.S.  It does not look like this software runs very well via WINE, but good luck anyway.**

---

### Post by Amazona aestiva on 2007-09-07
I saw the link before... It is about Slackware and other linuxes.
And It's about Wine 0.9.2x. I use the 0.9.44, because this is the first which starts the installer!!!!

So winecfg: What should I modify?
And wineprefixcreate say this:
> nandor@nandor-desktop:~$ wineprefixcreate
Warning: the specified Windows directory L"%SystemRoot%" is not accessible.
Warning: the specified Windows directory L"%SystemRoot%" is not accessible.
/home/nandor/.wine updated successfully.
nandor@nandor-desktop:~$

---

### Post by hikaricore on 2007-09-07
You didn't need to modify anything, I just wanted you to run winecfg incase you never had.
It sets up the config/directories if they do not exist.

Next wineprefixcreate should never return that message.  Something is wrong with your WINE installation/configuration.

Did you modify anything before attempting to install the program you're wanting to run?

---

### Post by Amazona aestiva on 2007-09-07
Modified Windows emulation from win2000 (I run Supreme Commander) to win98.
And for SupCom I had to add the DVD drive to the devices. (I've removed it)

Should I reinstall Wine?

---

### Post by Amazona aestiva on 2007-09-07
One more thing:
An other Windows software still works.
However It says "Warning: the specified Windows directory L"%SystemRoot%" is not accessible." too.

---

### Post by Amazona aestiva on 2007-10-08
I'll wait for newer Wine.

Thanks anyway.

---

