---
title: "wine + gta SA - failure after update"
date: 2008-05-22
forum: General Help
---

### Post by benste on 2008-05-22
i'm using
env WINEPREFIX="/home/benste/.wine" wine "C:\Programme\Rockstar Games\Grand Theft Auto San Andreas\gta_sa.exe"
to start GTA, normally it worked, but I updated to wine v1rc1 and now the game isn't playable and causes several errors:
```
benste@vaiofe31m:~$ env WINEPREFIX="/home/benste/.wine" wine "C:\Programme\Rockstar Games\Grand Theft Auto San Andreas\gta_sa.exe"
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
wine: Unhandled page fault on read access to 0x00000000 at address 0x746979 (thread 0013), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00746979).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 8c2e96f8 in module L"gta_sa"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00746979 ESP:0177fd58 EBP:0177ff08 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:7b866760
Stack dump:
0x0177fd58:  00748782 7b8b3884 01000002 00000000
0x0177fd68:  00828cf3 00856cc0 008a5a08 7b8b3884
0x0177fd78:  ffffffff 00c9ad0c 00400000 7b8b3884
0x0177fd88:  00000002 7b866760 0177fdb0 7b86670c
0x0177fd98:  00000002 00000000 0177fdd8 00821d5d
0x0177fda8:  7b8b3884 00000000 0177fde0 7b86678c
Backtrace:
=>1 0x00746979 in gta_sa (+0x346979) (0x0177ff08)
  2 0x7b876f57 in kernel32 (+0x56f57) (0x0177ffe8)
0x00746979: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (69 modules)
PE	  230000-  239000	Deferred        ogg
PE	  240000-  348000	Deferred        vorbis
PE	  350000-  380000	Deferred        eax
PE	  400000- 1577000	Export          gta_sa
PE	10000000-10011000	Deferred        vorbisfile
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e4fa000-7e520000	Deferred        msacm32<elf>
  \-PE	7e500000-7e520000	\               msacm32
ELF	7e520000-7e5e3000	Deferred        libasound.so.2
ELF	7e5e8000-7e5fc000	Deferred        midimap<elf>
  \-PE	7e5f0000-7e5fc000	\               midimap
ELF	7e5fc000-7e631000	Deferred        winealsa<elf>
  \-PE	7e610000-7e631000	\               winealsa
ELF	7e631000-7e63a000	Deferred        libxcursor.so.1
ELF	7e63a000-7e63f000	Deferred        libxfixes.so.3
ELF	7e63f000-7e642000	Deferred        libxcomposite.so.1
ELF	7e642000-7e648000	Deferred        libxrandr.so.2
ELF	7e648000-7e650000	Deferred        libxrender.so.1
ELF	7e650000-7e653000	Deferred        libxinerama.so.1
ELF	7e653000-7e673000	Deferred        imm32<elf>
  \-PE	7e660000-7e673000	\               imm32
ELF	7e673000-7e678000	Deferred        libxdmcp.so.6
ELF	7e678000-7e690000	Deferred        libxcb.so.1
ELF	7e690000-7e692000	Deferred        libxcb-xlib.so.0
ELF	7e692000-7e695000	Deferred        libxau.so.6
ELF	7e695000-7e77c000	Deferred        libx11.so.6
ELF	7e77c000-7e78a000	Deferred        libxext.so.6
ELF	7e78a000-7e78f000	Deferred        libxxf86vm.so.1
ELF	7e78f000-7e7a7000	Deferred        libice.so.6
ELF	7e7a7000-7e7af000	Deferred        libsm.so.6
ELF	7e7af000-7e7c6000	Deferred        msacm32<elf>
  \-PE	7e7b0000-7e7c6000	\               msacm32
ELF	7e7c8000-7e85e000	Deferred        winex11<elf>
  \-PE	7e7e0000-7e85e000	\               winex11
ELF	7e8a0000-7e8c1000	Deferred        libexpat.so.1
ELF	7e8c1000-7e8eb000	Deferred        libfontconfig.so.1
ELF	7e8eb000-7e900000	Deferred        libz.so.1
ELF	7e900000-7e970000	Deferred        libfreetype.so.6
ELF	7e970000-7e9d1000	Deferred        rpcrt4<elf>
  \-PE	7e980000-7e9d1000	\               rpcrt4
ELF	7e9d1000-7ea75000	Deferred        ole32<elf>
  \-PE	7e9e0000-7ea75000	\               ole32
ELF	7ea75000-7ea88000	Deferred        libresolv.so.2
ELF	7eaa1000-7eabf000	Deferred        iphlpapi<elf>
  \-PE	7eab0000-7eabf000	\               iphlpapi
ELF	7eabf000-7eaeb000	Deferred        ws2_32<elf>
  \-PE	7ead0000-7eaeb000	\               ws2_32
ELF	7eaeb000-7eb3d000	Deferred        advapi32<elf>
  \-PE	7eb00000-7eb3d000	\               advapi32
ELF	7eb3d000-7ebd8000	Deferred        gdi32<elf>
  \-PE	7eb50000-7ebd8000	\               gdi32
ELF	7ebd8000-7ed1f000	Deferred        user32<elf>
  \-PE	7ebf0000-7ed1f000	\               user32
ELF	7ed1f000-7edb1000	Deferred        winmm<elf>
  \-PE	7ed30000-7edb1000	\               winmm
ELF	7ef9f000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efc2000	Deferred        libnsl.so.1
ELF	7efc2000-7efe7000	Deferred        libm.so.6
ELF	b7d10000-b7d1a000	Deferred        libnss_nis.so.2
ELF	b7d1b000-b7d1f000	Deferred        libdl.so.2
ELF	b7d1f000-b7e6e000	Deferred        libc.so.6
ELF	b7e6f000-b7e87000	Deferred        libpthread.so.0
ELF	b7e87000-b7e90000	Deferred        libnss_compat.so.2
ELF	b7ea0000-b7fd6000	Deferred        libwine.so.1
ELF	b7fd8000-b7ff4000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000028   15
	00000009    0
0000000c 
	00000024    0
	0000001e    0
	00000019    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000011    0
	00000010    0
00000016 
	0000001a    0
	00000018    0
	00000017    0
0000001b 
	00000020    0
	0000001f    0
	0000001d    0
	0000001c    0
00000021 
	00000025    0
	00000023    0
	00000022    0
00000026 
	00000027    0
0000003d 
	00000041    0
	00000040   15
	0000003f    0
0000002a (D) C:\Programme\Rockstar Games\Grand Theft Auto San Andreas\gta_sa.exe
	00000013    0 <==
Backtrace:
=>1 0x00746979 in gta_sa (+0x346979) (0x0177ff08)
  2 0x7b876f57 in kernel32 (+0x56f57) (0x0177ffe8)

``` 

someone able to help me?
PS: wine works fine with other games

---

### Post by pedro_orange on 2008-05-22
Easiest possible solution: Roll back to the version of Wine you were previously using.

---

### Post by benste on 2008-05-22
I'll try if it will work

---

### Post by kenweill on 2008-05-22
how did you configure wine to run such games.
i have tried installing other games to wine, it works, only, grafx sux. its like fps is sooooo low. 

how did you tweak wine?

---

### Post by chinchilla2392 on 2008-05-22
ahh.. this is interesting..
ive pondered on the thought of trying to run GTA SA from within ubuntu. but... i hear wine sux to the max when it comes to playing games any more complex than ... pong 
:lolflag:
if you have any success with this. please dont hesitate to let me know :D

---

### Post by benste on 2008-05-22
GTA SA runs better with wine than with windows !!!

for more infos on which games work look into
[http://appdb.winehq.org/appbrowse.php]("http://appdb.winehq.org/appbrowse.php")

+ create your own account and share your experiences

---

