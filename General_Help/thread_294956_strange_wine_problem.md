---
title: "strange wine problem"
date: 2006-11-07
forum: General Help
---

### Post by toddr on 2006-11-07
Hello All
I hope someone can help me.  I have installed a game (1602 A.D) on my son's box through Wine. The install went fine and everything works. I can access the game through winefile by clicking on the .exe file but when I type the command in the command line I get an error message (shown below). I know the path is right because I double checked it and I wouldn't get an error message if it wasn't. I really would like to get this working so I can add a link in the applications menu.](*,) 

nick@ubuntu:~$ wine "c:\program files\1602 A.D\1602.exe"
wine: Unhandled page fault on read access to 0x00000000 at address 0x474452 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00474452).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
EIP:00474452 ESP:0033fbcc EBP:00000001 EFLAGS:00210246( - 00 -RIZP1)
EAX:00000000 EBX:00000080 ECX:ffffffff EDX:005b7790
ESI:005b7688 EDI:00000000
Stack dump:
0x0033fbcc: 005b6faa 0049d070 00000000 00000004
0x0033fbdc: 00000001 00474605 0049530f 0049c498
0x0033fbec: 0049c4a4 0000165c 7ffdf000 00000001
0x0033fbfc: 0033ff08 00000000 00000320 00000258
0x0033fc0c: 00000030 00001020 00492ea0 00000000
0x0033fc1c: 00000000 00400000 0000114e 00000000
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x00474452 in 1602 (+0x74452) (0x00000001)
2 0x00000000 (0x00000000)
0x00474452: repne scasb %es%edi)
Modules:
Module Address Debug info Name (95 modules)
PE 340000-35b000 Deferred smackw32
PE 360000-3ac000 Deferred language
PE 400000-72e000 Export 1602
PE 10000000-10028000 Deferred maxnet
PE 28100000-2810e000 Deferred maxsound
ELF 7b800000-7b917000 Deferred kernel32<elf>
\-PE 7b820000-7b917000 \ kernel32
ELF 7bc00000-7bc7f000 Deferred ntdll<elf>
\-PE 7bc10000-7bc7f000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7c3e7000-7c3fc000 Deferred midimap<elf>
\-PE 7c3f0000-7c3fc000 \ midimap
ELF 7c422000-7c43a000 Deferred msacm32<elf>
\-PE 7c430000-7c43a000 \ msacm32
ELF 7c43a000-7c4ef000 Deferred libasound.so.2
ELF 7c4ef000-7c518000 Deferred winealsa<elf>
\-PE 7c500000-7c518000 \ winealsa
ELF 7c518000-7c564000 Deferred libgcrypt.so.11
ELF 7c564000-7c574000 Deferred libtasn1.so.2
ELF 7c574000-7c5a1000 Deferred libcrypt.so.1
ELF 7c5b1000-7c61a000 Deferred libgnutls.so.12
ELF 7c61a000-7c648000 Deferred libcups.so.2
ELF 7da23000-7da27000 Deferred libgpg-error.so.0
ELF 7da41000-7da73000 Deferred uxtheme<elf>
\-PE 7da50000-7da73000 \ uxtheme
ELF 7da73000-7da7c000 Deferred libxcursor.so.1
ELF 7da7c000-7da98000 Deferred imm32<elf>
\-PE 7da80000-7da98000 \ imm32
ELF 7da98000-7daa0000 Deferred libxrender.so.1
ELF 7daa0000-7daa3000 Deferred libxinerama.so.1
ELF 7dc84000-7e3d5000 Deferred libglcore.so.1
ELF 7e3d5000-7e44d000 Deferred libgl.so.1
ELF 7e44d000-7e4d9000 Deferred winex11<elf>
\-PE 7e460000-7e4d9000 \ winex11
ELF 7e4d9000-7e4f8000 Deferred libexpat.so.1
ELF 7e4f8000-7e526000 Deferred libfontconfig.so.1
ELF 7e526000-7e53a000 Deferred libz.so.1
ELF 7e53a000-7e5a3000 Deferred libfreetype.so.6
ELF 7e5a3000-7e5eb000 Deferred dsound<elf>
\-PE 7e5b0000-7e5eb000 \ dsound
ELF 7e5eb000-7e64d000 Deferred msvcrt<elf>
\-PE 7e600000-7e64d000 \ msvcrt
ELF 7e64d000-7e6d5000 Deferred winmm<elf>
\-PE 7e660000-7e6d5000 \ winmm
ELF 7e6d5000-7e708000 Deferred dplayx<elf>
\-PE 7e6e0000-7e708000 \ dplayx
ELF 7e708000-7e7ee000 Deferred libx11.so.6
ELF 7e7ee000-7e7fb000 Deferred libxext.so.6
ELF 7e7fb000-7e813000 Deferred libice.so.6
ELF 7e813000-7e860000 Deferred ddraw<elf>
\-PE 7e820000-7e860000 \ ddraw
ELF 7e860000-7e874000 Deferred lz32<elf>
\-PE 7e870000-7e874000 \ lz32
ELF 7e874000-7e88d000 Deferred version<elf>
\-PE 7e880000-7e88d000 \ version
ELF 7e88d000-7e8bc000 Deferred winspool<elf>
\-PE 7e8a0000-7e8bc000 \ winspool
ELF 7e8bc000-7e97d000 Deferred comctl32<elf>
\-PE 7e8d0000-7e97d000 \ comctl32
ELF 7e97d000-7e990000 Deferred libresolv.so.2
ELF 7e990000-7e9af000 Deferred iphlpapi<elf>
\-PE 7e9a0000-7e9af000 \ iphlpapi
ELF 7e9af000-7ea01000 Deferred rpcrt4<elf>
\-PE 7e9c0000-7ea01000 \ rpcrt4
ELF 7ea01000-7ea92000 Deferred ole32<elf>
\-PE 7ea10000-7ea92000 \ ole32
ELF 7ea92000-7eae8000 Deferred shlwapi<elf>
\-PE 7eaa0000-7eae8000 \ shlwapi
ELF 7eae8000-7ebcf000 Deferred shell32<elf>
\-PE 7eb00000-7ebcf000 \ shell32
ELF 7ebcf000-7ec6b000 Deferred comdlg32<elf>
\-PE 7ebe0000-7ec6b000 \ comdlg32
ELF 7ec6b000-7ecaf000 Deferred advapi32<elf>
\-PE 7ec80000-7ecaf000 \ advapi32
ELF 7ecaf000-7ecb9000 Deferred libgcc_s.so.1
ELF 7ed8e000-7ee41000 Deferred gdi32<elf>
\-PE 7eda0000-7ee41000 \ gdi32
ELF 7ee41000-7ef73000 Deferred user32<elf>
\-PE 7ee60000-7ef73000 \ user32
ELF 7efa6000-7efb0000 Deferred libnss_files.so.2
ELF 7efb0000-7efb9000 Deferred libnss_nis.so.2
ELF 7efb9000-7efce000 Deferred libnsl.so.1
ELF 7efce000-7eff0000 Deferred libm.so.6
ELF 7eff3000-7eff7000 Deferred libxfixes.so.3
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
ELF b7cf0000-b7cf3000 Deferred libxrandr.so.2
ELF b7cf5000-b7cf7000 Deferred libnvidia-tls.so.1
ELF b7cf9000-b7cfc000 Deferred libdl.so.2
ELF b7cfc000-b7e2b000 Deferred libc.so.6
ELF b7e2b000-b7e3d000 Deferred libpthread.so.0
ELF b7e3d000-b7e40000 Deferred libxau.so.6
ELF b7e40000-b7e45000 Deferred libxxf86vm.so.1
ELF b7e45000-b7e4d000 Deferred libsm.so.6
ELF b7e4d000-b7f5e000 Deferred libwine.so.1
ELF b7f61000-b7f77000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000b
0000000d 0
0000000c 0
00000008 (D) C:\program files\1602 A.D\1602.exe
0000000a 0
00000009 0 <==
nick@ubuntu:~$
Thanks so much.

---

