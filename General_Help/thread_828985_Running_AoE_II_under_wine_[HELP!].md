---
title: "Running AoE II under wine [HELP!]"
date: 2008-06-14
forum: General Help
---

### Post by HpZ on 2008-06-14
I'm having trouble installing Age of Empires under wine 0.9.59.

When I put the CD in the file manager pops up and I click aoesetup.exe but nothing happens. So I drag the .exe file into wine and I try to run the .exe file but I get this error from wine: "Setup was unable to find (or could not read) the language specific setup resource dll, unable to continue. Please reboot and try again.

So I try and run from the terminal and I get this error:

```
andy@andy-desktop:~$ wine /media/aoe2/aoesetup.exe
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
andy@andy-desktop:~$ fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 002f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033f28c EBP:0033f2b8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0033f900 EBX:7e034ec8 ECX:00000000 EDX:00050050
 ESI:00138430 EDI:00050050
Stack dump:
0x0033f28c:  7e0302c0 00138430 00000000 00050050
0x0033f29c:  0033f2b0 0041927e 00050050 00000000
0x0033f2ac:  7e03027a 7ee1370c 00000000 0033f2c8
0x0033f2bc:  00419159 00138430 00138430 0033f334
0x0033f2cc:  0043d2a0 00050050 00000100 00000110
0x0033f2dc:  00000002 7ffd80cc 0033f324 7b88e4e6
Backtrace:
=>1 0x00000000 (0x0033f2b8)
  2 0x00419159 in ebub0d8 (+0x19159) (0x0033f2c8)
  3 0x0043d2a0 in ebub0d8 (+0x3d2a0) (0x0033f334)
  4 0x7edee69a WINPROC_wrapper+0x1a() in user32 (0x0033f364)
  5 0x7edf04d8 in user32 (+0xb04d8) (0x0033f3a4)
  6 0x7edf3615 in user32 (+0xb3615) (0x0033f874)
  7 0x7edf3f40 in user32 (+0xb3f40) (0x0033f8b4)
  8 0x7ed7db87 DefDlgProcW+0x87() in user32 (0x0033f8e4)
  9 0x7edee69a WINPROC_wrapper+0x1a() in user32 (0x0033f914)
  10 0x7edeed7e WINPROC_wrapper+0x6fe() in user32 (0x0033f954)
  11 0x7edf4151 in user32 (+0xb4151) (0x0033f994)
  12 0x7edb787a in user32 (+0x7787a) (0x0033fa04)
  13 0x7edbaafd in user32 (+0x7aafd) (0x0033fa64)
  14 0x7edbaf6a SendMessageW+0x4a() in user32 (0x0033faa4)
  15 0x7ed8343c in user32 (+0x4343c) (0x0033fc74)
  16 0x7ed84666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fc94)
  17 0x7ed84791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fcc4)
  18 0x0043cd5c in ebub0d8 (+0x3cd5c) (0x0033fd04)
  19 0x0042d54c in ebub0d8 (+0x2d54c) (0x0033fd18)
  20 0x0043cd01 in ebub0d8 (+0x3cd01) (0x0033fd24)
  21 0x0043cfc3 in ebub0d8 (+0x3cfc3) (0x0033fd34)
  22 0x0040456b in ebub0d8 (+0x456b) (0x0033ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x0033ffe8)
  24 0xb7e8b9c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00000000: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  400000-  497000	Export          ebub0d8
PE	10000000-1021c000	Deferred        ebub216
ELF	7b800000-7b92c000	Export          kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e018000-7e037000	Deferred        imm32<elf>
  \-PE	7e020000-7e037000	\               imm32
ELF	7e037000-7e04b000	Deferred        winejoystick<elf>
  \-PE	7e040000-7e04b000	\               winejoystick
ELF	7e04b000-7e05f000	Deferred        midimap<elf>
  \-PE	7e050000-7e05f000	\               midimap
ELF	7e05f000-7e085000	Deferred        msacm32<elf>
  \-PE	7e070000-7e085000	\               msacm32
ELF	7e085000-7e09c000	Deferred        msacm32<elf>
  \-PE	7e090000-7e09c000	\               msacm32
ELF	7e09c000-7e15f000	Deferred        libasound.so.2
ELF	7e15f000-7e195000	Deferred        winealsa<elf>
  \-PE	7e170000-7e195000	\               winealsa
ELF	7e195000-7e199000	Deferred        libgpg-error.so.0
ELF	7e199000-7e1e6000	Deferred        libgcrypt.so.11
ELF	7e1e6000-7e1f6000	Deferred        libtasn1.so.3
ELF	7e1f6000-7e1f9000	Deferred        libkeyutils.so.1
ELF	7e1f9000-7e201000	Deferred        libkrb5support.so.0
ELF	7e201000-7e233000	Deferred        libcrypt.so.1
ELF	7e233000-7e2a9000	Deferred        libgnutls.so.13
ELF	7e2a9000-7e2cc000	Deferred        libk5crypto.so.3
ELF	7e2cc000-7e359000	Deferred        libkrb5.so.3
ELF	7e359000-7e382000	Deferred        libgssapi_krb5.so.2
ELF	7e382000-7e3b5000	Deferred        libcups.so.2
ELF	7e40f000-7e441000	Deferred        uxtheme<elf>
  \-PE	7e420000-7e441000	\               uxtheme
ELF	7e441000-7e44a000	Deferred        libxcursor.so.1
ELF	7e44a000-7e44f000	Deferred        libxfixes.so.3
ELF	7e44f000-7e452000	Deferred        libxcomposite.so.1
ELF	7e452000-7e458000	Deferred        libxrandr.so.2
ELF	7e458000-7e460000	Deferred        libxrender.so.1
ELF	7e460000-7e463000	Deferred        libxinerama.so.1
ELF	7e463000-7e468000	Deferred        libxdmcp.so.6
ELF	7e468000-7e480000	Deferred        libxcb.so.1
ELF	7e480000-7e482000	Deferred        libxcb-xlib.so.0
ELF	7e482000-7e485000	Deferred        libxau.so.6
ELF	7e485000-7e56c000	Deferred        libx11.so.6
ELF	7e56c000-7e57a000	Deferred        libxext.so.6
ELF	7e57a000-7e57f000	Deferred        libxxf86vm.so.1
ELF	7e57f000-7e597000	Deferred        libice.so.6
ELF	7e597000-7e59f000	Deferred        libsm.so.6
ELF	7e5ab000-7e5ae000	Deferred        libcom_err.so.2
ELF	7e5b0000-7e641000	Deferred        winex11<elf>
  \-PE	7e5c0000-7e641000	\               winex11
ELF	7e669000-7e68a000	Deferred        libexpat.so.1
ELF	7e68a000-7e6b4000	Deferred        libfontconfig.so.1
ELF	7e6c5000-7e6da000	Deferred        libz.so.1
ELF	7e6da000-7e74a000	Deferred        libfreetype.so.6
ELF	7e74a000-7e7d8000	Deferred        winmm<elf>
  \-PE	7e760000-7e7d8000	\               winmm
ELF	7e7d8000-7e7ec000	Deferred        lz32<elf>
  \-PE	7e7e0000-7e7ec000	\               lz32
ELF	7e7ec000-7e805000	Deferred        version<elf>
  \-PE	7e7f0000-7e805000	\               version
ELF	7e805000-7e818000	Deferred        libresolv.so.2
ELF	7e818000-7e836000	Deferred        iphlpapi<elf>
  \-PE	7e820000-7e836000	\               iphlpapi
ELF	7e836000-7e896000	Deferred        rpcrt4<elf>
  \-PE	7e840000-7e896000	\               rpcrt4
ELF	7e896000-7e93a000	Deferred        ole32<elf>
  \-PE	7e8a0000-7e93a000	\               ole32
ELF	7e93a000-7e970000	Deferred        winspool<elf>
  \-PE	7e940000-7e970000	\               winspool
ELF	7e970000-7e9c9000	Deferred        shlwapi<elf>
  \-PE	7e980000-7e9c9000	\               shlwapi
ELF	7e9c9000-7ead3000	Deferred        shell32<elf>
  \-PE	7e9e0000-7ead3000	\               shell32
ELF	7ead3000-7eb7c000	Deferred        comdlg32<elf>
  \-PE	7eae0000-7eb7c000	\               comdlg32
ELF	7eb7c000-7ec3b000	Deferred        comctl32<elf>
  \-PE	7eb80000-7ec3b000	\               comctl32
ELF	7ec3b000-7ec8c000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8c000	\               advapi32
ELF	7ec8c000-7ed27000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed27000	\               gdi32
ELF	7ed27000-7ee6d000	Export          user32<elf>
  \-PE	7ed40000-7ee6d000	\               user32
ELF	7ee6d000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee90000	Deferred        libnsl.so.1
ELF	7ee90000-7ee99000	Deferred        libnss_compat.so.2
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d08000-b7d0c000	Deferred        libdl.so.2
ELF	b7d0c000-b7e5b000	Deferred        libc.so.6
ELF	b7e5b000-b7e73000	Deferred        libpthread.so.0
ELF	b7e84000-b7f99000	Export          libwine.so.1
ELF	b7f9b000-b7fb7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	0000001d    0
	0000001c    0
	0000001b    0
	00000009    0
0000000c 
	00000016    0
	0000000e    0
	0000000d    0
00000012 
	00000015    0
	00000014    0
	00000013    0
00000018 
	0000001a    0
	00000019    0
0000002e (D) C:\windows\temp\EBUb0d8.EXE
	0000002f    0 <==
Backtrace:
=>1 0x00000000 (0x0033f2b8)
  2 0x00419159 in ebub0d8 (+0x19159) (0x0033f2c8)
  3 0x0043d2a0 in ebub0d8 (+0x3d2a0) (0x0033f334)
  4 0x7edee69a WINPROC_wrapper+0x1a() in user32 (0x0033f364)
  5 0x7edf04d8 in user32 (+0xb04d8) (0x0033f3a4)
  6 0x7edf3615 in user32 (+0xb3615) (0x0033f874)
  7 0x7edf3f40 in user32 (+0xb3f40) (0x0033f8b4)
  8 0x7ed7db87 DefDlgProcW+0x87() in user32 (0x0033f8e4)
  9 0x7edee69a WINPROC_wrapper+0x1a() in user32 (0x0033f914)
  10 0x7edeed7e WINPROC_wrapper+0x6fe() in user32 (0x0033f954)
  11 0x7edf4151 in user32 (+0xb4151) (0x0033f994)
  12 0x7edb787a in user32 (+0x7787a) (0x0033fa04)
  13 0x7edbaafd in user32 (+0x7aafd) (0x0033fa64)
  14 0x7edbaf6a SendMessageW+0x4a() in user32 (0x0033faa4)
  15 0x7ed8343c in user32 (+0x4343c) (0x0033fc74)
  16 0x7ed84666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fc94)
  17 0x7ed84791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fcc4)
  18 0x0043cd5c in ebub0d8 (+0x3cd5c) (0x0033fd04)
  19 0x0042d54c in ebub0d8 (+0x2d54c) (0x0033fd18)
  20 0x0043cd01 in ebub0d8 (+0x3cd01) (0x0033fd24)
  21 0x0043cfc3 in ebub0d8 (+0x3cfc3) (0x0033fd34)
  22 0x0040456b in ebub0d8 (+0x456b) (0x0033ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x0033ffe8)
  24 0xb7e8b9c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

```

The disc is fine because I've successfully installed it on a windows PC.

Someone help?

---

### Post by Joeb454 on 2008-06-14
You *may* run into some issues trying to get this game working under Wine :(

I just checked the Wine website [AoE II AppDB Page]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=99")

---

### Post by HpZ on 2008-06-14
Okay, so how do I get imm32.dll?

---

### Post by HpZ on 2008-06-14
no-one knows?

---

### Post by XemeX on 2008-06-14
It's easy :)

[http://www.dll-files.com/dllindex/dll-files.shtml?imm32](http://www.dll-files.com/dllindex/dll-files.shtml?imm32)

Put it into /home/<username>/.wine/drive_c/windows/system32

Nevertheless your problem seems to be of different nature since there is no direct reference to the missing DLL but it's just a guess so feel free to try it.

---

### Post by igoddard on 2008-06-21
See my reply to the Cpuboye11's VB thread.

Ian

---

