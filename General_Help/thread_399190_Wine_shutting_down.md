---
title: "Wine shutting down"
date: 2007-04-02
forum: General Help
---

### Post by Majorix on 2007-04-02
Well I have an exe file that I am trying to run with wine.. But wine shuts down a few seconds after starting. I experienced this same issue with another file of same type (I mean they are the same, self-extracting rar archives) but not with any other file.

Here is the error log when I try running this file on terminal:

```

majorix@gaul:~$ wine Dark*.exe
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:shdocvw:PersistStreamInit_InitNew (0x172d70)
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x172e04)->((null) 1 0x33ba44 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172e04)->((null) 25 2 0x33ba58 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x172e04)->((null) 26 2 0x33ba58 (nil))
fixme:mshtml:OleControl_OnAmbientPropertyChange offline connection is not supported
fixme:mshtml:OleObject_SetClientSite silent == true
fixme:shdocvw:ClientSite_GetContainer (0x172e04)->(0x33ba94)
fixme:shdocvw:ClOleCommandTarget_Exec (0x172e04)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33bbb8 (nil))
fixme:mshtml:PersistMoniker_Load silent == true
fixme:mshtml:PersistMoniker_Load offline == true
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x173210)->(L"" L"" 0 0x33bbcc)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x173210)->(0x33bbd0 0x33baf4)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x671818)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x66f2b0)
fixme:mshtml:PersistStreamInit_InitNew (0x1738f0)
fixme:shdocvw:OleObject_Close (0x172d70)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1738f0)->((nil))
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x172d70)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x172d70)
wine: Unhandled page fault on write access to 0x00000024 at address 0x60236c72 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000024 in 32-bit code (0x60236c72).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:60236c72 ESP:003338cc EBP:003338e0 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000024 EBX:00110001 ECX:00000001 EDX:00000002
 ESI:006c1bd4 EDI:0033d960
Stack dump:
0x003338cc:  0000f842 006b249c 006aa8d8 00001499
0x003338dc:  00110001 0033d97c 60236268 00001498
0x003338ec:  0000f842 0033d91c 0033d920 00000000
0x003338fc:  00000040 0069c808 00000000 00000000
0x0033390c:  00333910 01010100 00000101 00000000
0x0033391c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x60236c72 in gkgfxwin (+0x6c72) (0x003338e0)
  2 0x60236268 in gkgfxwin (+0x6268) (0x0033d97c)
  3 0x60237023 in gkgfxwin (+0x7023) (0x0033d9b8)
  4 0x602382ad in gkgfxwin (+0x82ad) (0x0033d9f0)
  5 0x602395bc in gkgfxwin (+0x95bc) (0x0033da24)
  6 0x6023a165 in gkgfxwin (+0xa165) (0x0033da58)
  7 0x6023422c in gkgfxwin (+0x422c) (0x0033db24)
  8 0x602aa449 in gklayout (+0x4a449) (0x0033de14)
  9 0x602aabbf in gklayout (+0x4abbf) (0x0033e120)
  10 0x602c7573 in gklayout (+0x67573) (0x0033e278)
  11 0x602a1a98 in gklayout (+0x41a98) (0x0033e2b4)
  12 0x602a188b in gklayout (+0x4188b) (0x0033e300)
  13 0x602a16f0 in gklayout (+0x416f0) (0x0033e3c0)
  14 0x602a0813 in gklayout (+0x40813) (0x0033e46c)
  15 0x602a0062 in gklayout (+0x40062) (0x0033e514)
  16 0x6029f010 in gklayout (+0x3f010) (0x0033e708)
  17 0x602c67f3 in gklayout (+0x667f3) (0x0033e73c)
  18 0x602a12ad in gklayout (+0x412ad) (0x0033ea5c)
  19 0x602a05a5 in gklayout (+0x405a5) (0x0033eb00)
  20 0x602a0062 in gklayout (+0x40062) (0x0033eba8)
  21 0x6029f010 in gklayout (+0x3f010) (0x0033ed9c)
  22 0x602af2f3 in gklayout (+0x4f2f3) (0x0033edc4)
  23 0x602ae52e in gklayout (+0x4e52e) (0x0033ef10)
  24 0x602af2f3 in gklayout (+0x4f2f3) (0x0033ef38)
  25 0x602ba28f in gklayout (+0x5a28f) (0x0033f038)
  26 0x602ba34a in gklayout (+0x5a34a) (0x0033f114)
  27 0x602ba6a9 in gklayout (+0x5a6a9) (0x0033f23c)
  28 0x602af2f3 in gklayout (+0x4f2f3) (0x0033f264)
  29 0x602af919 in gklayout (+0x4f919) (0x0033f474)
  30 0x6027269e in gklayout (+0x1269e) (0x0033f568)
  31 0x602791eb in gklayout (+0x191eb) (0x0033f61c)
  32 0x60278f70 in gklayout (+0x18f70) (0x0033f64c)
  33 0x6116e1d0 in xpcom_core (+0x2e1d0) (0x60f741e0)
0x60236c72: orl %edx,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (147 modules)
PE      400000-420000   Deferred        dark messiah of might and magic Z:\home\majorix\Dark Messiah of Might and Magic SETUP.part01.exe
PE      600a0000-600d9000       Deferred        appcomps
PE      600e0000-600f0000       Deferred        appshell
PE      60120000-6012f000       Deferred        caps
PE      60130000-60140000       Deferred        chrome
PE      60150000-60159000       Deferred        cookie
PE      60160000-6018c000       Deferred        docshell
PE      60200000-6021e000       Deferred        embedcomponents
PE      60230000-60254000       Export          gkgfxwin
PE      60260000-6052d000       Export          gklayout
PE      60530000-60568000       Deferred        gkparser
PE      605a0000-605c5000       Deferred        gkwidget
PE      605d0000-605fe000       Deferred        i18n
PE      60610000-60635000       Deferred        imglib2
PE      606d0000-606dd000       Deferred        jar50
PE      606e0000-606ef000       Deferred        jsd3250
PE      60940000-609bb000       Deferred        necko
PE      609e0000-609ec000       Deferred        oji
PE      60a00000-60a18000       Deferred        palmsync
PE      60a20000-60a27000       Deferred        perms
PE      60a30000-60a38000       Deferred        pipboot
PE      60a90000-60a9e000       Deferred        profile
PE      60aa0000-60aba000       Deferred        rdf
PE      60af0000-60af7000       Deferred        sroaming
PE      60b40000-60b4c000       Deferred        typeaheadfind
PE      60b50000-60c0b000       Deferred        uconv
PE      60c70000-60c7e000       Deferred        webbrwsr
PE      60cf0000-60d22000       Deferred        xpc3250
PE      60d30000-60d37000       Deferred        xpcom_compat_c
PE      60d70000-60d7c000       Deferred        xppref32
PE      60d80000-60d96000       Deferred        gkgfx
PE      60da0000-60e09000       Deferred        js3250
PE      60e10000-60e23000       Deferred        jsj3250
PE      60ec0000-60ed1000       Deferred        mozz
PE      60ee0000-60f14000       Deferred        msgbsutl
PE      60f60000-60f87000       Deferred        nspr4
PE      60f90000-60fe9000       Deferred        nss3
PE      60ff0000-6102a000       Deferred        nssckbi
PE      61030000-61037000       Deferred        palmsyncproxy
PE      61040000-61047000       Deferred        plc4
PE      61050000-61056000       Deferred        plds4
PE      61060000-61068000       Deferred        npnul32
PE      61070000-6108a000       Deferred        smime3
PE      61090000-610ea000       Deferred        softokn3
PE      610f0000-6110b000       Deferred        ssl3
PE      61110000-61116000       Deferred        xpcom
PE      61120000-61134000       Deferred        xpcom_compat
PE      61140000-611a5000       Export          xpcom_core
PE      611b0000-611b6000       Deferred        xpistub
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bd85000-7bd99000       Deferred        lz32<elf>
  \-PE  7bd90000-7bd99000       \               lz32
ELF     7bd99000-7bdb2000       Deferred        version<elf>
  \-PE  7bda0000-7bdb2000       \               version
ELF     7bdb2000-7be19000       Deferred        msvcrt<elf>
  \-PE  7bdc0000-7be19000       \               msvcrt
ELF     7be19000-7be46000       Deferred        ws2_32<elf>
  \-PE  7be20000-7be46000       \               ws2_32
ELF     7be46000-7beb8000       Deferred        mshtml<elf>
  \-PE  7be50000-7beb8000       \               mshtml
ELF     7beb8000-7bf00000       Deferred        wininet<elf>
  \-PE  7bec0000-7bf00000       \               wininet
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf10000-7bf2f000       Deferred        mpr<elf>
  \-PE  7bf20000-7bf2f000       \               mpr
ELF     7bf2f000-7bf65000       Deferred        urlmon<elf>
  \-PE  7bf40000-7bf65000       \               urlmon
ELF     7bf65000-7c000000       Deferred        oleaut32<elf>
  \-PE  7bf80000-7c000000       \               oleaut32
ELF     7c335000-7c34f000       Deferred        wsock32<elf>
  \-PE  7c340000-7c34f000       \               wsock32
ELF     7c34f000-7c389000       Deferred        shdocvw<elf>
  \-PE  7c360000-7c389000       \               shdocvw
ELF     7c389000-7c3cd000       Deferred        riched20<elf>
  \-PE  7c390000-7c3cd000       \               riched20
ELF     7c3cd000-7c3e1000       Deferred        riched32<elf>
  \-PE  7c3d0000-7c3e1000       \               riched32
ELF     7c3e1000-7c3e5000       Deferred        libgpg-error.so.0
ELF     7c3e5000-7c436000       Deferred        libgcrypt.so.11
ELF     7c436000-7c44b000       Deferred        libtasn1.so.3
ELF     7c44b000-7c479000       Deferred        libcrypt.so.1
ELF     7c487000-7c4f7000       Deferred        libgnutls.so.13
ELF     7c4f7000-7c528000       Deferred        libcups.so.2
ELF     7c555000-7c587000       Deferred        uxtheme<elf>
  \-PE  7c560000-7c587000       \               uxtheme
ELF     7c587000-7c590000       Deferred        libxcursor.so.1
ELF     7c590000-7c5ad000       Deferred        imm32<elf>
  \-PE  7c5a0000-7c5ad000       \               imm32
ELF     7c5ad000-7c5b3000       Deferred        libxrandr.so.2
ELF     7cfdd000-7cfe5000       Deferred        libxrender.so.1
ELF     7d0e3000-7d0e8000       Deferred        libxfixes.so.3
ELF     7d978000-7d981000       Deferred        librt.so.1
ELF     7d982000-7d985000       Deferred        libxinerama.so.1
ELF     7da49000-7e3a8000       Deferred        fglrx_dri.so
ELF     7e3a8000-7e448000       Deferred        libgl.so.1
ELF     7e448000-7e44d000       Deferred        libxdmcp.so.6
ELF     7e44d000-7e465000       Deferred        libxcb.so.1
ELF     7e465000-7e467000       Deferred        libxcb-xlib.so.0
ELF     7e467000-7e552000       Deferred        libx11.so.6
ELF     7e552000-7e560000       Deferred        libxext.so.6
ELF     7e560000-7e565000       Deferred        libxxf86vm.so.1
ELF     7e565000-7e57d000       Deferred        libice.so.6
ELF     7e57d000-7e586000       Deferred        libsm.so.6
ELF     7e586000-7e614000       Deferred        winex11<elf>
  \-PE  7e5a0000-7e614000       \               winex11
ELF     7e684000-7e6a4000       Deferred        libexpat.so.1
ELF     7e6a4000-7e6cf000       Deferred        libfontconfig.so.1
ELF     7e6cf000-7e6e3000       Deferred        libz.so.1
ELF     7e6e3000-7e74d000       Deferred        libfreetype.so.6
ELF     7e74d000-7e780000       Deferred        winspool<elf>
  \-PE  7e760000-7e780000       \               winspool
ELF     7e780000-7e793000       Deferred        libresolv.so.2
ELF     7e793000-7e7b1000       Deferred        iphlpapi<elf>
  \-PE  7e7a0000-7e7b1000       \               iphlpapi
ELF     7e7b1000-7e806000       Deferred        rpcrt4<elf>
  \-PE  7e7c0000-7e806000       \               rpcrt4
ELF     7e806000-7e8a0000       Deferred        ole32<elf>
  \-PE  7e820000-7e8a0000       \               ole32
ELF     7e8a0000-7e8f9000       Deferred        shlwapi<elf>
  \-PE  7e8b0000-7e8f9000       \               shlwapi
ELF     7e8f9000-7e9ee000       Deferred        shell32<elf>
  \-PE  7e910000-7e9ee000       \               shell32
ELF     7e9ee000-7ea8e000       Deferred        comdlg32<elf>
  \-PE  7ea00000-7ea8e000       \               comdlg32
ELF     7ea8e000-7ea9a000       Deferred        libgcc_s.so.1
ELF     7ea9a000-7ea9d000       Deferred        libxau.so.6
ELF     7eb92000-7ec4f000       Deferred        gdi32<elf>
  \-PE  7ebb0000-7ec4f000       \               gdi32
ELF     7ec4f000-7ed8b000       Deferred        user32<elf>
  \-PE  7ec70000-7ed8b000       \               user32
ELF     7ed8b000-7ee47000       Deferred        comctl32<elf>
  \-PE  7ed90000-7ee47000       \               comctl32
ELF     7ee47000-7ee8d000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee8d000       \               advapi32
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcb000       Deferred        libnsl.so.1
ELF     7efcb000-7eff2000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d67000-b7d6b000       Deferred        libdl.so.2
ELF     b7d6b000-b7eac000       Deferred        libc.so.6
ELF     b7ead000-b7ec4000       Deferred        libpthread.so.0
ELF     b7ed2000-b7fe3000       Deferred        libwine.so.1
ELF     b7fe5000-b8000000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\majorix\Dark Messiah of Might and Magic SETUP.part01.exe
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0 <==

```

---

### Post by zvacet on 2007-04-02
I don´t know if I´m right but i think you have to unrar that file.You can do it outside of wine and after that put unrared file in .wine>Z>program files>click on it.But it i still a chance that I´m completly wrong.

---

### Post by Majorix on 2007-04-02
No the purpose of that file itself is to unrar. Alright I am new but you have taken me for a complete newbie :lolflag:

It used to work with my older Ubuntu 6.06 with an older version of Wine. So there must be something wrong with either Wine or Ubuntu 7.04.

Since I can't remove 7.04, I decided to go to Wine's site to download a newer version hoping that would fix. But there was only packages for 6.10 and older releases there, not for 7.04 :(

Where do the developers get the Wine package for 7.04? Do they create it themselves? If not, where can I download it?

Thanks a lot.

---

### Post by Majorix on 2007-04-03
Anyone? Any ideas? Thanks.

---

