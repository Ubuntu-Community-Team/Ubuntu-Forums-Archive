---
title: "Problems running Chikka with Wine"
date: 2007-10-07
forum: General Help
---

### Post by cyberblade3001 on 2007-10-07
Hi all, I'm fairly new to Ubuntu and wine, so please inform me if I missed something.

I'm running Ubuntu 7.04 and Wine 0.9.46

The program I'm trying to run is Chikka ([www.chikka.com](www.chikka.com))

I completed the install with wine, and it put an icon on my desktop. When I would double click it it wouldn't run and it would say it was missing some dll's. I read the Wine user guide and ran wine with WINEDEBUG=+loaddll as it said, to find the missing dll's. I then put them all in place.

Now when I try to run it from the icon nothing happens, when I run it from the terminal I get the following:

.wine/drive_c/Program Files/Chikka Messenger/Chikka v.4$ wine ChikkaLauncher.exe
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:create_server class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {079aa557-4a18-424a-8eee-e39f0a8d41b9} could be created for context 0x17
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:create_server class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {079aa557-4a18-424a-8eee-e39f0a8d41b9} could be created for context 0x17
fixme:shdocvw:WebBrowser_QueryInterface (0x139650)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x33f558) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x139650)->(0x33f524)
fixme:shdocvw:OleControl_FreezeEvents (0x139650)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x139650)->(0)
fixme:winstation:OpenInputDesktop (0,0,0): stub
wine: Unhandled page fault on read access to 0x00000064 at address 0x7c27cec2 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000064 in 32-bit code (0x7c27cec2).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7c27cec2 ESP:0033eb88 EBP:0033eba4 EFLAGS:00210246( - 00 -RIZP1)
EAX:b78c2eb8 EBX:5001000b ECX:00000000 EDX:00000000
ESI:0000005c EDI:0033ebac
Stack dump:
0x0033eb88: 0033ecec 005beda0 7c27ce9a 005beda0
0x0033eb98: 0033eba0 0033ebac 0000005c 00528810
0x0033eba8: 008f5661 b78c2eb8 0033ebb8 0034ac3a
0x0033ebb8: 00000000 0033ec4c 00921c08 00000000
0x0033ebc8: 0091f64d 005beda0 00000006 00527c20
0x0033ebd8: 0033ecec 00528810 0033ebcc 00000000
Backtrace:
=>1 0x7c27cec2 in mfc70u (+0x2cec2) (0x0033eba4)
2 0x008f5661 in uiskinengine (+0x5661) (0x00528810)
3 0x00000001 (0x00929020)
4 0x00900530 in uiskinengine (+0x10530) (0x008fe4a0)
5 0x9090c300 (0x928dd8b8)
6 0x00000000 (0x00000000)
0x7c27cec2: divl 0x8(%esi),%eax
Modules:
Module Address Debug info Name (105 modules)
PE 340000- 395000 Deferred msvcr70
PE 3a0000- 3be000 Deferred dataclasslib
PE 3c0000- 3e1000 Deferred chikkautils
PE 400000- 409000 Deferred chikkalauncher
PE 630000- 6a7000 Deferred msvcp70
PE 800000- 80a000 Deferred chikka
PE 810000- 81a000 Deferred chikkaenglish
PE 860000- 8e4000 Deferred chikkaui
PE 8f0000- 953000 Export uiskinengine
PE 960000- 976000 Deferred chikkadynamicui
PE ba0000- bed000 Deferred ctmprotocollib
PE bf0000- c07000 Deferred networklib
PE c10000- c26000 Deferred plugin
PE 10000000-10017000 Deferred chikkacontroller
PE 4d4f0000-4d548000 Deferred winhttp
PE 70d00000-70e91000 Deferred gdiplus
ELF 78c5f000-78cfd000 Deferred oleaut32<elf>
\-PE 78c70000-78cfd000 \ oleaut32
ELF 78cfd000-78e00000 Deferred shell32<elf>
\-PE 78d10000-78e00000 \ shell32
ELF 7b800000-7b929000 Deferred kernel32<elf>
\-PE 7b820000-7b929000 \ kernel32
ELF 7b938000-7b972000 Deferred shdocvw<elf>
\-PE 7b940000-7b972000 \ shdocvw
ELF 7b972000-7ba00000 Deferred winmm<elf>
\-PE 7b980000-7ba00000 \ winmm
ELF 7bc00000-7bca0000 Deferred ntdll<elf>
\-PE 7bc10000-7bca0000 \ ntdll
ELF 7bcad000-7bcc2000 Deferred midimap<elf>
\-PE 7bcb0000-7bcc2000 \ midimap
ELF 7bcc2000-7bce8000 Deferred msacm32<elf>
\-PE 7bcd0000-7bce8000 \ msacm32
ELF 7bce8000-7bd00000 Deferred msacm32<elf>
\-PE 7bcf0000-7bd00000 \ msacm32
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7bf11000-7bf4b000 Deferred wineoss<elf>
\-PE 7bf20000-7bf4b000 \ wineoss
ELF 7bf4b000-7bf5f000 Deferred msimg32<elf>
\-PE 7bf50000-7bf5f000 \ msimg32
ELF 7bf5f000-7c000000 Deferred ole32<elf>
\-PE 7bf70000-7c000000 \ ole32
PE 7c250000-7c33e000 Export mfc70u
ELF 7c373000-7c3cc000 Deferred rpcrt4<elf>
\-PE 7c380000-7c3cc000 \ rpcrt4
ELF 7c3cc000-7c3df000 Deferred libresolv.so.2
ELF 7c3eb000-7c418000 Deferred ws2_32<elf>
\-PE 7c3f0000-7c418000 \ ws2_32
ELF 7c61e000-7c63c000 Deferred iphlpapi<elf>
\-PE 7c630000-7c63c000 \ iphlpapi
ELF 7c63c000-7c656000 Deferred wsock32<elf>
\-PE 7c640000-7c656000 \ wsock32
ELF 7c656000-7c6be000 Deferred msvcrt<elf>
\-PE 7c670000-7c6be000 \ msvcrt
ELF 7c6be000-7c6d2000 Deferred lz32<elf>
\-PE 7c6c0000-7c6d2000 \ lz32
ELF 7c6d2000-7c6ec000 Deferred version<elf>
\-PE 7c6e0000-7c6ec000 \ version
ELF 7c6ec000-7c71e000 Deferred uxtheme<elf>
\-PE 7c6f0000-7c71e000 \ uxtheme
ELF 7c735000-7c73a000 Deferred libxfixes.so.3
ELF 7c73a000-7c743000 Deferred libxcursor.so.1
ELF 7c743000-7c760000 Deferred imm32<elf>
\-PE 7c750000-7c760000 \ imm32
ELF 7c760000-7c766000 Deferred libxrandr.so.2
ELF 7c767000-7c76d000 Deferred libnss_dns.so.2
ELF 7c76d000-7c770000 Deferred libnss_mdns4_minimal.so.2
ELF 7e572000-7e7c8000 Deferred i915_dri.so
ELF 7e7c8000-7e7d1000 Deferred libdrm.so.2
ELF 7e7d1000-7e831000 Deferred libgl.so.1
ELF 7e831000-7e836000 Deferred libxdmcp.so.6
ELF 7e836000-7e839000 Deferred libxau.so.6
ELF 7e839000-7e92a000 Deferred libx11.so.6
ELF 7e92a000-7e938000 Deferred libxext.so.6
ELF 7e938000-7e93d000 Deferred libxxf86vm.so.1
ELF 7e93d000-7e955000 Deferred libice.so.6
ELF 7e955000-7e95e000 Deferred libsm.so.6
ELF 7e960000-7e968000 Deferred libxrender.so.1
ELF 7e96a000-7e9f5000 Deferred winex11<elf>
\-PE 7e980000-7e9f5000 \ winex11
ELF 7ea75000-7ea95000 Deferred libexpat.so.1
ELF 7ea95000-7eac0000 Deferred libfontconfig.so.1
ELF 7eac0000-7ead4000 Deferred libz.so.1
ELF 7ead4000-7eb3f000 Deferred libfreetype.so.6
ELF 7eb4b000-7ec09000 Deferred comctl32<elf>
\-PE 7eb50000-7ec09000 \ comctl32
ELF 7ec09000-7ed47000 Deferred user32<elf>
\-PE 7ec30000-7ed47000 \ user32
ELF 7ed47000-7eda0000 Deferred shlwapi<elf>
\-PE 7ed60000-7eda0000 \ shlwapi
ELF 7eda0000-7edb4000 Deferred oleacc<elf>
\-PE 7edb0000-7edb4000 \ oleacc
ELF 7edb4000-7edfd000 Deferred advapi32<elf>
\-PE 7edc0000-7edfd000 \ advapi32
ELF 7edfd000-7ee98000 Deferred gdi32<elf>
\-PE 7ee10000-7ee98000 \ gdi32
ELF 7efab000-7efb6000 Deferred libnss_files.so.2
ELF 7efb6000-7efcd000 Deferred libnsl.so.1
ELF 7efcd000-7eff4000 Deferred libm.so.6
ELF 7eff6000-7f000000 Deferred libnss_nis.so.2
ELF b7ce2000-b7ceb000 Deferred libnss_compat.so.2
ELF b7cec000-b7cf0000 Deferred libdl.so.2
ELF b7cf0000-b7e31000 Deferred libc.so.6
ELF b7e32000-b7e49000 Deferred libpthread.so.0
ELF b7e55000-b7f69000 Deferred libwine.so.1
ELF b7f6b000-b7f86000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000a
0000000c 0
0000000b 0
00000008 (D) C:\Program Files\Chikka Messenger\Chikka v.4\ChikkaLauncher.exe
00000012 0
00000011 0
00000010 0
0000000f 0
00000009 0 <==
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:CoGetClassObject class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
err:ole:create_server class {079aa557-4a18-424a-8eee-e39f0a8d41b9} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {079aa557-4a18-424a-8eee-e39f0a8d41b9} could be created for context 0x17

What should I do next?

Thanks!

---

