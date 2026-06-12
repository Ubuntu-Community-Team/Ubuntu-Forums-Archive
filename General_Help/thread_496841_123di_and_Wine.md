---
title: "123di and Wine"
date: 2007-07-09
forum: General Help
---

### Post by SneakPeak on 2007-07-09
Hi there.

Firstly: I originally posted this under Art and Design, which is clearly the wrong place.  I have marked it as solved there and reposted it here.  I hope that isn't violating any rules.  I couldn't find a way to move the post!  Here is my problem:

I am trying to get some software to run using wine. The software is basically a software reference book for digital imaging. You can't get the book in hardcopy and you can't print it. It worked fine under windows. There is no linux version available. I am trying to switch completely to linux. I use this book a lot and I want to get it running with wine.

When I first tried I got an error message that the Mozilla ActiveX plugin was not installed. I manged to install a windows version of Firefox 1.5 using wine. I then installed the ActiveX plugin.

When I now try to run 123di with wine I get a long error message which I have pasted below.

Anyone able to help?

Thanks

SneakPeak

fixmele:CoResumeClassObjects stub
wine: Unhandled exception 0x0eedfade at address 0x0000:0x7fc2e770 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
First chance exception: 0xc0000025 in 32-bit code (0x7ff949b4).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
EIP:7ff949b4 ESP:7fbaf394 EBP:7fbaf3f8 EFLAGS:00000282( - 00 - -IS1)
EAX:7fbaf3a0 EBX:7ffd51fc ECX:7fcf0020 EDX:00000000
ESI:7fbaf780 EDI:7fbaf404
Stack dump:
0x7fbaf394: 7ffd51fc 00000004 7fc9d2c0 c0000025
0x7fbaf3a4: 00000001 7fbaf780 00000001 00000000
0x7fbaf3b4: 7fbaf410 ffffffff 0000000f 7ffd51fc
0x7fbaf3c4: 000068a8 00001c09 7fbaf3fe 00000000
0x7fbaf3d4: 7fbaf550 00000001 7ffd51fc 7fbaf410
0x7fbaf3e4: 7ff9c390 7fc10000 7fbaf44c 7ff9496c
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7ff949b4 __regs_RtlRaiseException+0x48 in ntdll (0x7ff949b4)
2 0x7ffc37d3 in ntdll (+0x437d3) (0x7ffc37d3)
3 0x7ff93ff6 RtlRaiseException+0x6 in ntdll (0x7ff93ff6)
4 0x0049186c in 123di_v40 (+0x9186c) (0x0049186c)
5 0x004918b5 in 123di_v40 (+0x918b5) (0x004918b5)
6 0x0049535b in 123di_v40 (+0x9535b) (0x0049535b)
7 0x00495161 in 123di_v40 (+0x95161) (0x00495161)
8 0x0049cf85 in 123di_v40 (+0x9cf85) (0x0049cf85)
9 0x0049ca05 in 123di_v40 (+0x9ca05) (0x0049ca05)
10 0x00421224 in 123di_v40 (+0x21224) (0x00421224)
11 0x00421459 in 123di_v40 (+0x21459) (0x00421459)
12 0x0042170f in 123di_v40 (+0x2170f) (0x0042170f)
13 0x00421678 in 123di_v40 (+0x2167 (0x0042167
14 0x0042632f in 123di_v40 (+0x2632f) (0x0042632f)
15 0x004655be in 123di_v40 (+0x655be) (0x004655be)
16 0x00469be5 in 123di_v40 (+0x69be5) (0x00469be5)
17 0x004214ec in 123di_v40 (+0x214ec) (0x004214ec)
18 0x0042170f in 123di_v40 (+0x2170f) (0x0042170f)
19 0x00421648 in 123di_v40 (+0x2164 (0x0042164
20 0x0042632f in 123di_v40 (+0x2632f) (0x0042632f)
21 0x004655be in 123di_v40 (+0x655be) (0x004655be)
22 0x00469be5 in 123di_v40 (+0x69be5) (0x00469be5)
23 0x00484bea in 123di_v40 (+0x84bea) (0x00484bea)
24 0x0042250a in 123di_v40 (+0x2250a) (0x0042250a)
25 0x0041f548 in 123di_v40 (+0x1f54 (0x0041f54
26 0x0041b885 in 123di_v40 (+0x1b885) (0x0041b885)
27 0x0041ba59 in 123di_v40 (+0x1ba59) (0x0041ba59)
28 0x0041baeb in 123di_v40 (+0x1baeb) (0x0041baeb)
29 0x0048448c in 123di_v40 (+0x8448c) (0x0048448c)
30 0x004c66e1 in 123di_v40 (+0xc66e1) (0x004c66e1)
31 0x0048d8fb in 123di_v40 (+0x8d8fb) (0x0048d8fb)
32 0x004c848d in 123di_v40 (+0xc848d) (0x004c848d)
33 0x7fc5b311 in kernel32 (+0x4b311) (0x7fc5b311)
34 0xb7f66ddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7f66ddb)
0x7ff949b4 __regs_RtlRaiseException+0x48 in ntdll: subl $4,%esp
Modules:
Module Address Debug info Name (117 modules)
PE 0x00400000-004fc000 Export 123di_v40
PE 0x10000000-10006000 Deferred mozctlx
PE 0x30000000-30026000 Deferred nspr4
PE 0x55900000-55961000 Deferred msvcp60
ELF 0x7bf00000-7bf03000 Deferred <wine-loader>
PE 0x7d900000-7d928000 Deferred docshell
PE 0x7d930000-7d9ea000 Deferred uconv
PE 0x7db10000-7db44000 Deferred gkparser
PE 0x7db50000-7db6a000 Deferred rdf
PE 0x7db70000-7db80000 Deferred chrome
PE 0x7db90000-7dba4000 Deferred xpcom_compat
PE 0x7dbb0000-7dbb7000 Deferred xpcom_compat_c
PE 0x7dbc0000-7dbcf000 Deferred profile
PE 0x7dbd0000-7dbfe000 Deferred i18n
PE 0x7dd10000-7dd1d000 Deferred mozz
PE 0x7dd20000-7dd91000 Deferred necko
PE 0x7dda0000-7ddad000 Deferred xppref32
PE 0x7ddb0000-7dddf000 Deferred xpc3250
PE 0x7dde0000-7ddf0000 Deferred caps
PE 0x7de00000-7de54000 Deferred js3250
PE 0x7de60000-7de7e000 Deferred embedcomponents
ELF 0x7dfa3000-7e040000 Deferred comdlg32<elf>
\-PE 0x7dfb0000-7e040000 \ comdlg32
PE 0x7e040000-7e046000 Deferred plds4
PE 0x7e050000-7e057000 Deferred plc4
ELF 0x7e05b000-7e086000 Deferred ws2_32<elf>
\-PE 0x7e060000-7e086000 \ ws2_32
ELF 0x7e086000-7e0a0000 Deferred wsock32<elf>
\-PE 0x7e090000-7e0a0000 \ wsock32
PE 0x7e0a0000-7e0ff000 Deferred xpcom
PE 0x7e100000-7e130000 Deferred mozctl
ELF 0x7e136000-7e197000 Deferred msvcrt<elf>
\-PE 0x7e150000-7e197000 \ msvcrt
ELF 0x7e197000-7e1c9000 Deferred shdocvw<elf>
\-PE 0x7e1a0000-7e1c9000 \ shdocvw
ELF 0x7e4fc000-7e510000 Deferred olepro32<elf>
\-PE 0x7e500000-7e510000 \ olepro32
ELF 0x7e6cb000-7e6cf000 Deferred libgpg-error.so.0
ELF 0x7e6cf000-7e71b000 Deferred libgcrypt.so.11
ELF 0x7e71b000-7e72b000 Deferred libtasn1.so.2
ELF 0x7e72b000-7e758000 Deferred libcrypt.so.1
ELF 0x7e769000-7e7d2000 Deferred libgnutls.so.12
ELF 0x7e7d2000-7e800000 Deferred libcups.so.2
ELF 0x7e800000-7e831000 Deferred uxtheme<elf>
\-PE 0x7e810000-7e831000 \ uxtheme
ELF 0x7e84f000-7e858000 Deferred libxcursor.so.1
ELF 0x7e858000-7e874000 Deferred imm32<elf>
\-PE 0x7e860000-7e874000 \ imm32
ELF 0x7e874000-7f037000 Deferred libglcore.so.1
ELF 0x7f037000-7f0bc000 Deferred libgl.so.1
ELF 0x7f0bc000-7f1a2000 Deferred libx11.so.6
ELF 0x7f1a2000-7f1ba000 Deferred libice.so.6
ELF 0x7f1ba000-7f23d000 Deferred winex11<elf>
\-PE 0x7f1d0000-7f23d000 \ winex11
ELF 0x7f23d000-7f25c000 Deferred libexpat.so.1
ELF 0x7f25c000-7f28a000 Deferred libfontconfig.so.1
ELF 0x7f28a000-7f29e000 Deferred libz.so.1
ELF 0x7f29e000-7f308000 Deferred libfreetype.so.6
ELF 0x7f308000-7f327000 Deferred mpr<elf>
\-PE 0x7f310000-7f327000 \ mpr
ELF 0x7f327000-7f36e000 Deferred wininet<elf>
\-PE 0x7f330000-7f36e000 \ wininet
ELF 0x7f36e000-7f38f000 Deferred cabinet<elf>
\-PE 0x7f370000-7f38f000 \ cabinet
ELF 0x7f38f000-7f3c4000 Deferred urlmon<elf>
\-PE 0x7f3a0000-7f3c4000 \ urlmon
ELF 0x7f3c4000-7f41f000 Deferred shlwapi<elf>
\-PE 0x7f3e0000-7f41f000 \ shlwapi
ELF 0x7f41f000-7f4eb000 Deferred shell32<elf>
\-PE 0x7f430000-7f4eb000 \ shell32
ELF 0x7f4eb000-7f517000 Deferred winspool<elf>
\-PE 0x7f4f0000-7f517000 \ winspool
ELF 0x7f517000-7f5d7000 Deferred comctl32<elf>
\-PE 0x7f520000-7f5d7000 \ comctl32
ELF 0x7f5d7000-7f5eb000 Deferred lz32<elf>
\-PE 0x7f5e0000-7f5eb000 \ lz32
ELF 0x7f5eb000-7f604000 Deferred version<elf>
\-PE 0x7f5f0000-7f604000 \ version
ELF 0x7f604000-7f623000 Deferred iphlpapi<elf>
\-PE 0x7f610000-7f623000 \ iphlpapi
ELF 0x7f623000-7f66c000 Deferred rpcrt4<elf>
\-PE 0x7f630000-7f66c000 \ rpcrt4
ELF 0x7f66c000-7f6fd000 Deferred ole32<elf>
\-PE 0x7f680000-7f6fd000 \ ole32
ELF 0x7f6fd000-7f793000 Deferred oleaut32<elf>
\-PE 0x7f710000-7f793000 \ oleaut32
ELF 0x7f793000-7f7d3000 Deferred advapi32<elf>
\-PE 0x7f7a0000-7f7d3000 \ advapi32
ELF 0x7f7d3000-7f7dd000 Deferred libgcc_s.so.1
ELF 0x7f7dd000-7f7e1000 Deferred libxfixes.so.3
ELF 0x7f7e1000-7f7ee000 Deferred libxext.so.6
ELF 0x7f8c3000-7f974000 Deferred gdi32<elf>
\-PE 0x7f8e0000-7f974000 \ gdi32
ELF 0x7f974000-7faa0000 Deferred user32<elf>
\-PE 0x7f990000-7faa0000 \ user32
ELF 0x7fbb3000-7fbbb000 Deferred libxrender.so.1
ELF 0x7fbee000-7fcf0000 Export kernel32<elf>
\-PE 0x7fc10000-7fcf0000 \ kernel32
ELF 0x7fe00000-7fe03000 Deferred libxrandr.so.2
ELF 0x7fe03000-7fe08000 Deferred libxxf86vm.so.1
ELF 0x7fe08000-7fe12000 Deferred libnss_files.so.2
ELF 0x7fe12000-7fe1b000 Deferred libnss_nis.so.2
ELF 0x7fe1b000-7fe30000 Deferred libnsl.so.1
ELF 0x7fe30000-7fe39000 Deferred libnss_compat.so.2
ELF 0x7fe3b000-7fe40000 Deferred libxxf86dga.so.1
ELF 0x7fe42000-7fe4a000 Deferred libsm.so.6
ELF 0x7fe4c000-7fe4e000 Deferred libnvidia-tls.so.1
ELF 0x7fe4e000-7fe70000 Deferred libm.so.6
ELF 0x7fe70000-7ff66000 Deferred libwine_unicode.so.1
ELF 0x7ff66000-7ffe0000 Export ntdll<elf>
\-PE 0x7ff80000-7ffe0000 \ ntdll
ELF 0xb7e00000-b7e03000 Deferred libxau.so.6
ELF 0xb7e0c000-b7e0f000 Deferred libdl.so.2
ELF 0xb7e0f000-b7f3e000 Deferred libc.so.6
ELF 0xb7f3e000-b7f50000 Deferred libpthread.so.0
ELF 0xb7f62000-b7f7c000 Export libwine.so.1
ELF 0xb7f7f000-b7f95000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:\Program Files\123di_40\123di_V40.exe
0000000e 0
0000000d 0
0000000c 0
0000000b 0
0000000a 0
00000009 0 <==
__________________

---

