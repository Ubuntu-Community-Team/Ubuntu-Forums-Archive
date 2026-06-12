---
title: "Plugin Error"
date: 2015-03-11
forum: General Help
---

### Post by mountainman70 on 2015-03-11
Can someone tell me how to correct this plugin error? 

```
Unhandled exception: page fault on read access to 0x0000005c in 32-bit code (0x7ec316bb).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ec316bb ESP:0068e560 EBP:0068e588 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e5e8000 ECX:00000000 EDX:00146978
 ESI:0014e448 EDI:00010020
Stack dump:
0x0068e560:  0014e448 00010020 7e575115 7e5ac645
0x0068e570:  00010020 00147518 7bcd3000 7e5ac60a
0x0068e580:  00010020 00010020 0068e608 7e5ad2a8
0x0068e590:  0032003b 00001a85 0000001c 0068e5d4
0x0068e5a0:  00000000 00000000 0068e608 7bc52493
0x0068e5b0:  00110060 00000013 0032003b 0068e67c
Backtrace:
=>0 0x7ec316bb ExtEscape+0x2b() in gdi32 (0x0068e588)
  1 0x7e5ad2a8 X11DRV_GetDC+0xf7() in winex11 (0x0068e608)
  2 0x7e8fdfed in user32 (+0x6dfec) (0x0068e728)
  3 0x7e8fed18 GetDCEx+0x387() in user32 (0x0068e778)
  4 0x7e8ff41c GetDC+0x6b() in user32 (0x0068e7a8)
  5 0x101fc7f4 in npswf32_16_0_0_305 (+0x1fc7f3) (0x0068e840)
0x7ec316bb ExtEscape+0x2b in gdi32: movl    0x5c(%ecx),%edi
Modules:
Module    Address            Debug info    Name (139 modules)
PE      400000-  487000    Deferred        pluginloader
PE    10000000-1110a000    Export          npswf32_16_0_0_305
ELF    7a800000-7a91e000    Deferred        opengl32<elf>
  \-PE    7a820000-7a91e000    \               opengl32
ELF    7b800000-7ba66000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba66000    \               kernel32
ELF    7bc00000-7bcf0000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf0000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cdf2000-7cdfb000    Deferred        libogg.so.0
ELF    7cdfb000-7ce27000    Deferred        libvorbis.so.0
ELF    7ce27000-7cf9f000    Deferred        libvorbisenc.so.2
ELF    7cf9f000-7cfd3000    Deferred        libflac.so.8
ELF    7cfd3000-7cfda000    Deferred        libasyncns.so.0
ELF    7cfda000-7d04c000    Deferred        libsndfile.so.1
ELF    7d04c000-7d056000    Deferred        libwrap.so.0
ELF    7d056000-7d0c5000    Deferred        libpulsecommon-4.0.so
ELF    7d0c5000-7d0d0000    Deferred        libjson-c.so.2
ELF    7d0d0000-7d11f000    Deferred        libpulse.so.0
ELF    7d138000-7d162000    Deferred        winepulse<elf>
  \-PE    7d140000-7d162000    \               winepulse
ELF    7d162000-7d185000    Deferred        mmdevapi<elf>
  \-PE    7d170000-7d185000    \               mmdevapi
ELF    7d19a000-7d1ca000    Deferred        p11-kit-trust.so
ELF    7d1ca000-7d1f9000    Deferred        netapi32<elf>
  \-PE    7d1d0000-7d1f9000    \               netapi32
ELF    7d1f9000-7d22c000    Deferred        secur32<elf>
  \-PE    7d200000-7d22c000    \               secur32
ELF    7d22c000-7d255000    Deferred        mlang<elf>
  \-PE    7d230000-7d255000    \               mlang
ELF    7d255000-7d25e000    Deferred        librt.so.1
ELF    7d25e000-7d265000    Deferred        libffi.so.6
ELF    7d265000-7d26a000    Deferred        libgpg-error.so.0
ELF    7d26a000-7d282000    Deferred        libresolv.so.2
ELF    7d282000-7d2cd000    Deferred        libdbus-1.so.3
ELF    7d2cd000-7d309000    Deferred        libp11-kit.so.0
ELF    7d309000-7d31d000    Deferred        libtasn1.so.6
ELF    7d31d000-7d3a4000    Deferred        libgcrypt.so.11
ELF    7d3a4000-7d3b0000    Deferred        libkrb5support.so.0
ELF    7d3b0000-7d3e0000    Deferred        libk5crypto.so.3
ELF    7d3e0000-7d49e000    Deferred        libkrb5.so.3
ELF    7d49e000-7d4b0000    Deferred        libavahi-client.so.3
ELF    7d4b0000-7d576000    Deferred        libgnutls.so.26
ELF    7d576000-7d5bb000    Deferred        libgssapi_krb5.so.2
ELF    7d5bb000-7d628000    Deferred        libcups.so.2
ELF    7d628000-7d65f000    Deferred        uxtheme<elf>
  \-PE    7d630000-7d65f000    \               uxtheme
ELF    7d65f000-7d686000    Deferred        iphlpapi<elf>
  \-PE    7d670000-7d686000    \               iphlpapi
ELF    7d686000-7d6db000    Deferred        liblcms2.so.2
ELF    7d6db000-7d6fc000    Deferred        mscms<elf>
  \-PE    7d6e0000-7d6fc000    \               mscms
ELF    7d6fc000-7d73f000    Deferred        winspool<elf>
  \-PE    7d700000-7d73f000    \               winspool
ELF    7d73f000-7d84b000    Deferred        comctl32<elf>
  \-PE    7d750000-7d84b000    \               comctl32
ELF    7d84b000-7d938000    Deferred        comdlg32<elf>
  \-PE    7d850000-7d938000    \               comdlg32
ELF    7d938000-7d954000    Deferred        dinput8<elf>
  \-PE    7d940000-7d954000    \               dinput8
ELF    7d954000-7d99f000    Deferred        dsound<elf>
  \-PE    7d960000-7d99f000    \               dsound
ELF    7d99f000-7da42000    Deferred        urlmon<elf>
  \-PE    7d9b0000-7da42000    \               urlmon
ELF    7da42000-7db87000    Deferred        oleaut32<elf>
  \-PE    7da60000-7db87000    \               oleaut32
ELF    7db87000-7dc57000    Deferred        crypt32<elf>
  \-PE    7db90000-7dc57000    \               crypt32
ELF    7dc57000-7dc91000    Deferred        ws2_32<elf>
  \-PE    7dc60000-7dc91000    \               ws2_32
ELF    7dc91000-7decb000    Deferred        shell32<elf>
  \-PE    7dca0000-7decb000    \               shell32
ELF    7decb000-7df45000    Deferred        shlwapi<elf>
  \-PE    7dee0000-7df45000    \               shlwapi
ELF    7df45000-7df6d000    Deferred        mpr<elf>
  \-PE    7df50000-7df6d000    \               mpr
ELF    7df6d000-7dfea000    Deferred        wininet<elf>
  \-PE    7df80000-7dfea000    \               wininet
ELF    7dfea000-7e0a3000    Deferred        winmm<elf>
  \-PE    7dff0000-7e0a3000    \               winmm
ELF    7e0c9000-7e0d0000    Deferred        libnss_dns.so.2
ELF    7e0d4000-7e0e9000    Deferred        schannel<elf>
  \-PE    7e0e0000-7e0e9000    \               schannel
ELF    7e0e9000-7e106000    Deferred        libgcc_s.so.1
ELF    7e1ef000-7e226000    Deferred        libtxc_dxtn_s2tc.so.0
ELF    7e228000-7e22c000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e22c000-7e23f000    Deferred        gnome-keyring-pkcs11.so
ELF    7e23f000-7e38a000    Deferred        wined3d<elf>
  \-PE    7e250000-7e38a000    \               wined3d
ELF    7e38a000-7e390000    Deferred        libxfixes.so.3
ELF    7e390000-7e39b000    Deferred        libxcursor.so.1
ELF    7e39b000-7e3ac000    Deferred        libxi.so.6
ELF    7e3ac000-7e3b0000    Deferred        libxcomposite.so.1
ELF    7e3b0000-7e3bb000    Deferred        libxrandr.so.2
ELF    7e3bb000-7e3c6000    Deferred        libxrender.so.1
ELF    7e3c6000-7e3cc000    Deferred        libxxf86vm.so.1
ELF    7e3cc000-7e3d0000    Deferred        libxinerama.so.1
ELF    7e3d0000-7e3d7000    Deferred        libxdmcp.so.6
ELF    7e3d7000-7e3db000    Deferred        libxau.so.6
ELF    7e3db000-7e3fd000    Deferred        libxcb.so.1
ELF    7e3fd000-7e531000    Deferred        libx11.so.6
ELF    7e531000-7e544000    Deferred        libxext.so.6
ELF    7e544000-7e548000    Deferred        libkeyutils.so.1
ELF    7e548000-7e54d000    Deferred        libcom_err.so.2
ELF    7e54d000-7e55b000    Deferred        libavahi-common.so.3
ELF    7e55d000-7e5f3000    Dwarf           winex11<elf>
  \-PE    7e570000-7e5f3000    \               winex11
ELF    7e5f3000-7e618000    Deferred        imm32<elf>
  \-PE    7e600000-7e618000    \               imm32
ELF    7e691000-7e6ba000    Deferred        libexpat.so.1
ELF    7e6ba000-7e6f5000    Deferred        libfontconfig.so.1
ELF    7e6f5000-7e71d000    Deferred        libpng12.so.0
ELF    7e71d000-7e737000    Deferred        libz.so.1
ELF    7e737000-7e7d7000    Deferred        libfreetype.so.6
ELF    7e7d7000-7e85b000    Deferred        rpcrt4<elf>
  \-PE    7e7e0000-7e85b000    \               rpcrt4
ELF    7e85b000-7e875000    Deferred        version<elf>
  \-PE    7e860000-7e875000    \               version
ELF    7e875000-7e9e9000    Dwarf           user32<elf>
  \-PE    7e890000-7e9e9000    \               user32
ELF    7e9e9000-7eb2b000    Deferred        ole32<elf>
  \-PE    7ea00000-7eb2b000    \               ole32
ELF    7eb2b000-7ebdc000    Deferred        msvcrt<elf>
  \-PE    7eb40000-7ebdc000    \               msvcrt
ELF    7ebdc000-7ecf4000    Dwarf           gdi32<elf>
  \-PE    7ebf0000-7ecf4000    \               gdi32
ELF    7ecf4000-7ed6f000    Deferred        advapi32<elf>
  \-PE    7ed00000-7ed6f000    \               advapi32
ELF    7ef6f000-7ef7c000    Deferred        libnss_files.so.2
ELF    7ef7c000-7ef88000    Deferred        libnss_nis.so.2
ELF    7ef88000-7efa1000    Deferred        libnsl.so.1
ELF    7efa1000-7efe7000    Deferred        libm.so.6
ELF    b73f1000-b73fa000    Deferred        libnss_compat.so.2
ELF    b73fb000-b7400000    Deferred        libdl.so.2
ELF    b7400000-b75ae000    Deferred        libc.so.6
ELF    b75af000-b75cb000    Deferred        libpthread.so.0
ELF    b75e4000-b77a8000    Dwarf           libwine.so.1
ELF    b77aa000-b77cc000    Deferred        ld-linux.so.2
ELF    b77cc000-b77cd000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 pluginloader.exe
    0000003e    0
    0000003d    0
    00000029   15
    00000026    0
    00000025    0
    00000024   15
    00000009    0
0000000e services.exe
    0000001d    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 explorer.exe
    00000021    0
0000003f pluginloader.exe
    00000042    0
    0000003c    0
    0000000c   15
    00000045    0
    00000044    0
    00000043   15
    00000040    0
00000041 (D) Z:\usr\share\pipelight\pluginloader.exe
    0000005e    0
    0000005d    0
    0000002f   15
    00000046    0
    0000000b    0
    00000022   15
    0000000d    0 <==
System information:
    Wine build: wine-1.7.38 (Staging)
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-46-generic
```

Thanks for any replies.

---

