---
title: "Need help debugging wine problem"
date: 2007-07-15
forum: General Help
---

### Post by Old *ix Geek on 2007-07-15
I FINALLY got *Paint Shop Pro 8* installed and running beautifully on my newest laptop. However, *Animation Shop* (which is included with PSP) will not run.  It installed normally and starts up looking perfectly normal, then exits abruptly with this output:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
wine: Unhandled page fault on read access to 0x00000288 at address 0x53e8a1 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x00000288 in 32-bit code (0x0053e8a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0053e8a1 ESP:0033f294 EBP:005fbff0 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:0033f2a4 EDX:0020327c
 ESI:01c45a88 EDI:002083f8
Stack dump:
0x0033f294:  00000000 01c45a88 00000001 000000db
0x0033f2a4:  5f4d1c58 0033f2d0 005a82e8 00000000
0x0033f2b4:  0054d8e5 00000001 01c45a88 7ee3adb0
0x0033f2c4:  00000007 00000000 0033f2f0 0033f2f0
0x0033f2d4:  005a8ff9 ffffffff 0054be9b 00000000
0x0033f2e4:  01c45a88 001fdfd0 001a6cf8 0033f370
Backtrace:
=>1 0x0053e8a1 in anim (+0x13e8a1) (0x005fbff0)
  2 0x00000001 (0x005af390)
  3 0x00409cc0 in anim (+0x9cc0) (0x0059564e)
0x0053e8a1: movl	0x288(%eax),%ecx
Modules:
Module	Address			Debug info	Name (104 modules)
PE	  340000-  353000	Deferred        jmem
PE	  360000-  3ab000	Deferred        pcdlib32
PE	  3b0000-  3d2000	Deferred        jpeglib
PE	  3e0000-  3f2000	Deferred        jlem
PE	  400000-  750000	Export          anim
PE	  750000-  95f000	Deferred        jff
PE	  960000-  9c5000	Deferred        fpxlib
PE	  9d0000-  9e9000	Deferred        jbrwsutil
PE	  9f0000-  a22000	Deferred        jcmyk
PE	  a30000-  a39000	Deferred        jcm
PE	  a40000-  b0f000	Deferred        jcontrols
PE	  b10000-  b5f000	Deferred        jbrws
PE	  b60000-  c3f000	Deferred        sxlrt308
PE	10000000-10011000	Deferred        jcap
PE	5f400000-5f4f2000	Deferred        mfc42
PE	780a0000-780b2000	Deferred        msvcirt
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b929000	Deferred        kernel32<elf>
  \-PE	7b820000-7b929000	\               kernel32
ELF	7bc00000-7bc98000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bc98000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e034000-7e038000	Deferred        libgpg-error.so.0
ELF	7e038000-7e089000	Deferred        libgcrypt.so.11
ELF	7e089000-7e09e000	Deferred        libtasn1.so.3
ELF	7e09e000-7e0cc000	Deferred        libcrypt.so.1
ELF	7e0cf000-7e0e3000	Deferred        shfolder<elf>
  \-PE	7e0e0000-7e0e3000	\               shfolder
ELF	7e0e3000-7e153000	Deferred        libgnutls.so.13
ELF	7e153000-7e184000	Deferred        libcups.so.2
ELF	7e1a3000-7e1d5000	Deferred        uxtheme<elf>
  \-PE	7e1b0000-7e1d5000	\               uxtheme
ELF	7e1d5000-7e1ea000	Deferred        midimap<elf>
  \-PE	7e1e0000-7e1ea000	\               midimap
ELF	7e1ea000-7e202000	Deferred        msacm32<elf>
  \-PE	7e1f0000-7e202000	\               msacm32
ELF	7e202000-7e2c7000	Deferred        libasound.so.2
ELF	7e2c7000-7e2f9000	Deferred        winealsa<elf>
  \-PE	7e2d0000-7e2f9000	\               winealsa
ELF	7e2fb000-7e300000	Deferred        libxfixes.so.3
ELF	7e300000-7e309000	Deferred        libxcursor.so.1
ELF	7e309000-7e326000	Deferred        imm32<elf>
  \-PE	7e310000-7e326000	\               imm32
ELF	7e326000-7e32c000	Deferred        libxrandr.so.2
ELF	7e32c000-7e334000	Deferred        libxrender.so.1
ELF	7e334000-7e33d000	Deferred        libdrm.so.2
ELF	7e33d000-7e39d000	Deferred        libgl.so.1
ELF	7e39d000-7e3a2000	Deferred        libxdmcp.so.6
ELF	7e3a2000-7e493000	Deferred        libx11.so.6
ELF	7e493000-7e4a1000	Deferred        libxext.so.6
ELF	7e4a1000-7e4a6000	Deferred        libxxf86vm.so.1
ELF	7e4a6000-7e4be000	Deferred        libice.so.6
ELF	7e4be000-7e4c7000	Deferred        libsm.so.6
ELF	7e4c7000-7e556000	Deferred        winex11<elf>
  \-PE	7e4e0000-7e556000	\               winex11
ELF	7e633000-7e653000	Deferred        libexpat.so.1
ELF	7e653000-7e67e000	Deferred        libfontconfig.so.1
ELF	7e67e000-7e6e9000	Deferred        libfreetype.so.6
ELF	7e6e9000-7e71c000	Deferred        winspool<elf>
  \-PE	7e6f0000-7e71c000	\               winspool
ELF	7e71c000-7e7bd000	Deferred        comdlg32<elf>
  \-PE	7e720000-7e7bd000	\               comdlg32
ELF	7e7bd000-7e816000	Deferred        shlwapi<elf>
  \-PE	7e7d0000-7e816000	\               shlwapi
ELF	7e816000-7e913000	Deferred        shell32<elf>
  \-PE	7e830000-7e913000	\               shell32
ELF	7e913000-7e97a000	Deferred        msvcrt<elf>
  \-PE	7e920000-7e97a000	\               msvcrt
ELF	7e97a000-7e98d000	Deferred        libresolv.so.2
ELF	7e98d000-7e9ab000	Deferred        iphlpapi<elf>
  \-PE	7e990000-7e9ab000	\               iphlpapi
ELF	7e9ab000-7ea00000	Deferred        rpcrt4<elf>
  \-PE	7e9c0000-7ea00000	\               rpcrt4
ELF	7ea00000-7ea9f000	Deferred        ole32<elf>
  \-PE	7ea10000-7ea9f000	\               ole32
ELF	7ea9f000-7eb5c000	Deferred        comctl32<elf>
  \-PE	7eab0000-7eb5c000	\               comctl32
ELF	7eb5c000-7eb83000	Deferred        msvfw32<elf>
  \-PE	7eb60000-7eb83000	\               msvfw32
ELF	7eb83000-7ebcb000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebcb000	\               advapi32
ELF	7ebcb000-7ebd7000	Deferred        libgcc_s.so.1
ELF	7ecc1000-7ed81000	Deferred        gdi32<elf>
  \-PE	7ece0000-7ed81000	\               gdi32
ELF	7ed81000-7eebe000	Deferred        user32<elf>
  \-PE	7eda0000-7eebe000	\               user32
ELF	7eebe000-7ef4d000	Deferred        winmm<elf>
  \-PE	7eed0000-7ef4d000	\               winmm
ELF	7ef4d000-7ef73000	Deferred        msacm32<elf>
  \-PE	7ef50000-7ef73000	\               msacm32
ELF	7ef73000-7efad000	Deferred        avifil32<elf>
  \-PE	7ef80000-7efad000	\               avifil32
ELF	7efad000-7efb8000	Deferred        libnss_files.so.2
ELF	7efb8000-7efc2000	Deferred        libnss_nis.so.2
ELF	7efc2000-7efe9000	Deferred        libm.so.6
ELF	7efe9000-7f000000	Deferred        libnsl.so.1
ELF	b7cc0000-b7cc9000	Deferred        libnss_compat.so.2
ELF	b7cca000-b7cce000	Deferred        libdl.so.2
ELF	b7cce000-b7e0f000	Deferred        libc.so.6
ELF	b7e10000-b7e27000	Deferred        libpthread.so.0
ELF	b7e27000-b7e2a000	Deferred        libxau.so.6
ELF	b7e2a000-b7e3e000	Deferred        libz.so.1
ELF	b7e3e000-b7f52000	Deferred        libwine.so.1
ELF	b7f54000-b7f6f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000019 (D) C:\Program Files\Jasc Software Inc\Animation Shop 3\anim.exe
	0000001a    0 <==
0000000a 
	0000000c    0
	0000000b    0
00000008 
	0000000f    0
	0000000e    0
	0000000d    0
	00000009    0

```

I'm at a loss as to what the problem(s) may be.  If you have any ideas after perusing the above, kindly let me know! :)

---

### Post by splintercellguy on 2007-07-15
I honestly don't know, but you may wish to file an AppDb/Bugtraq report :).

---

