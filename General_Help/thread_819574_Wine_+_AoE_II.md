---
title: "Wine + AoE II"
date: 2008-06-05
forum: General Help
---

### Post by HpZ on 2008-06-05
Okay, so I just installed wine and haven't touched the settings. I have a disc of Age of Empires II. How do I make these two work together? Do I just put the disc in and wine does what has to be done itself?

---

### Post by phidia on 2008-06-05
You will need to try to install aoe thru wine. Sometimes you can just double click the .exe and wine will start and try to install it. 
You may want to check out the different resources [here]("http://www.winehq.org/").

---

### Post by HpZ on 2008-06-05
I put the CD in and the Icon came up on desktop so I clicked it which lead to a folder in Wine (I think). But when I click any .exe file, nothing happens. I found one that, when clicked prompts the "Loading" AoE screen, but it soon disapears after about 10 seconds. Halp?

---

### Post by Kernel_Krunch on 2008-06-05
The setup.exe is what you want to use, the msi window(looks the same as windows install window) should popup.  If not, type winecfg in console and change your windows version too... XP or NT or something.  Thats all i can do since i don't have the game sry, hope it helps.

---

### Post by ajgreeny on 2008-06-05
Let's assume your cdrom is /media/cdrom0 and that somewhere on the AoE cd there is a file called setup.exe.

Open a terminal and type the command ```
wine /media/cdrom0/path/to/setup.exe
```

The install should start and go through just like in windows.

Good luck, hope it works for you.

---

### Post by HpZ on 2008-06-05
```
wine: cannot find '/media/aeo2/aeosetup.exe'
andy@andy-desktop:~$ wine /media/AOE2/aoesetup.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
andy@andy-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0018), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:7f22f28c EBP:7f22f2b8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:7f22f900 EBX:7e03cec8 ECX:00000000 EDX:00010026
 ESI:7f0283f8 EDI:00010026
Stack dump:
0x7f22f28c:  7e0382c0 7f0283f8 00000000 00010026
0x7f22f29c:  7f22f2b0 0041927e 00010026 00000000
0x7f22f2ac:  7e03827a 7ee2070c 00000000 7f22f2c8
0x7f22f2bc:  00419159 7f0283f8 7f0283f8 7f22f334
0x7f22f2cc:  0043d2a0 00010026 00000100 00000110
0x7f22f2dc:  00000002 7ffd80cc 7f22f324 7b88e4e6
Backtrace:
=>1 0x00000000 (0x7f22f2b8)
  2 0x00419159 in ebu21e (+0x19159) (0x7f22f2c8)
  3 0x0043d2a0 in ebu21e (+0x3d2a0) (0x7f22f334)
  4 0x7edfb69a WINPROC_wrapper+0x1a() in user32 (0x7f22f364)
  5 0x7edfd4d8 in user32 (+0xad4d8) (0x7f22f3a4)
  6 0x7ee00615 in user32 (+0xb0615) (0x7f22f874)
  7 0x7ee00f40 in user32 (+0xb0f40) (0x7f22f8b4)
  8 0x7ed8ab87 DefDlgProcW+0x87() in user32 (0x7f22f8e4)
  9 0x7edfb69a WINPROC_wrapper+0x1a() in user32 (0x7f22f914)
  10 0x7edfbd7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f954)
  11 0x7ee01151 in user32 (+0xb1151) (0x7f22f994)
  12 0x7edc487a in user32 (+0x7487a) (0x7f22fa04)
  13 0x7edc7afd in user32 (+0x77afd) (0x7f22fa64)
  14 0x7edc7f6a SendMessageW+0x4a() in user32 (0x7f22faa4)
  15 0x7ed9043c in user32 (+0x4043c) (0x7f22fc74)
  16 0x7ed91666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fc94)
  17 0x7ed91791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fcc4)
  18 0x0043cd5c in ebu21e (+0x3cd5c) (0x7f22fd04)
  19 0x0042d54c in ebu21e (+0x2d54c) (0x7f22fd18)
  20 0x0043cd01 in ebu21e (+0x3cd01) (0x7f22fd24)
  21 0x0043cfc3 in ebu21e (+0x3cfc3) (0x7f22fd34)
  22 0x0040456b in ebu21e (+0x456b) (0x7f22ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x7f22ffe8)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  400000-  497000	Export          ebu21e
PE	10000000-1021c000	Deferred        ebu428
ELF	7b800000-7b92c000	Export          kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e020000-7e03f000	Deferred        imm32<elf>
  \-PE	7e030000-7e03f000	\               imm32
ELF	7e03f000-7e053000	Deferred        winejoystick<elf>
  \-PE	7e040000-7e053000	\               winejoystick
ELF	7e053000-7e067000	Deferred        midimap<elf>
  \-PE	7e060000-7e067000	\               midimap
ELF	7e067000-7e08d000	Deferred        msacm32<elf>
  \-PE	7e070000-7e08d000	\               msacm32
ELF	7e08d000-7e0a4000	Deferred        msacm32<elf>
  \-PE	7e090000-7e0a4000	\               msacm32
ELF	7e0a4000-7e167000	Deferred        libasound.so.2
ELF	7e167000-7e19d000	Deferred        winealsa<elf>
  \-PE	7e170000-7e19d000	\               winealsa
ELF	7e19d000-7e1a1000	Deferred        libgpg-error.so.0
ELF	7e1a1000-7e1ee000	Deferred        libgcrypt.so.11
ELF	7e1ee000-7e1fe000	Deferred        libtasn1.so.3
ELF	7e1fe000-7e201000	Deferred        libkeyutils.so.1
ELF	7e201000-7e209000	Deferred        libkrb5support.so.0
ELF	7e209000-7e23b000	Deferred        libcrypt.so.1
ELF	7e23b000-7e2b1000	Deferred        libgnutls.so.13
ELF	7e2b1000-7e2d4000	Deferred        libk5crypto.so.3
ELF	7e2d4000-7e361000	Deferred        libkrb5.so.3
ELF	7e361000-7e38a000	Deferred        libgssapi_krb5.so.2
ELF	7e38a000-7e3bd000	Deferred        libcups.so.2
ELF	7e416000-7e448000	Deferred        uxtheme<elf>
  \-PE	7e420000-7e448000	\               uxtheme
ELF	7e448000-7e451000	Deferred        libxcursor.so.1
ELF	7e451000-7e456000	Deferred        libxfixes.so.3
ELF	7e456000-7e459000	Deferred        libxcomposite.so.1
ELF	7e459000-7e45f000	Deferred        libxrandr.so.2
ELF	7e45f000-7e467000	Deferred        libxrender.so.1
ELF	7e467000-7e46a000	Deferred        libxinerama.so.1
ELF	7e46a000-7e46f000	Deferred        libxdmcp.so.6
ELF	7e46f000-7e487000	Deferred        libxcb.so.1
ELF	7e487000-7e56e000	Deferred        libx11.so.6
ELF	7e56e000-7e57c000	Deferred        libxext.so.6
ELF	7e57c000-7e594000	Deferred        libice.so.6
ELF	7e594000-7e59c000	Deferred        libsm.so.6
ELF	7e5a7000-7e5aa000	Deferred        libcom_err.so.2
ELF	7e5ac000-7e63d000	Deferred        winex11<elf>
  \-PE	7e5c0000-7e63d000	\               winex11
ELF	7e677000-7e698000	Deferred        libexpat.so.1
ELF	7e698000-7e6c2000	Deferred        libfontconfig.so.1
ELF	7e6d2000-7e6e7000	Deferred        libz.so.1
ELF	7e6e7000-7e757000	Deferred        libfreetype.so.6
ELF	7e757000-7e7e5000	Deferred        winmm<elf>
  \-PE	7e760000-7e7e5000	\               winmm
ELF	7e7e5000-7e7f9000	Deferred        lz32<elf>
  \-PE	7e7f0000-7e7f9000	\               lz32
ELF	7e7f9000-7e812000	Deferred        version<elf>
  \-PE	7e800000-7e812000	\               version
ELF	7e812000-7e825000	Deferred        libresolv.so.2
ELF	7e825000-7e843000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e843000	\               iphlpapi
ELF	7e843000-7e8a3000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a3000	\               rpcrt4
ELF	7e8a3000-7e947000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e947000	\               ole32
ELF	7e947000-7e97d000	Deferred        winspool<elf>
  \-PE	7e950000-7e97d000	\               winspool
ELF	7e97d000-7e9d6000	Deferred        shlwapi<elf>
  \-PE	7e990000-7e9d6000	\               shlwapi
ELF	7e9d6000-7eae0000	Deferred        shell32<elf>
  \-PE	7e9f0000-7eae0000	\               shell32
ELF	7eae0000-7eb89000	Deferred        comdlg32<elf>
  \-PE	7eaf0000-7eb89000	\               comdlg32
ELF	7eb89000-7ec48000	Deferred        comctl32<elf>
  \-PE	7eb90000-7ec48000	\               comctl32
ELF	7ec48000-7ec99000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec99000	\               advapi32
ELF	7ec99000-7ed34000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed34000	\               gdi32
ELF	7ed34000-7ee7a000	Export          user32<elf>
  \-PE	7ed50000-7ee7a000	\               user32
ELF	7ee7a000-7ee92000	Deferred        libnsl.so.1
ELF	7ee92000-7ee9b000	Deferred        libnss_compat.so.2
ELF	7ee9b000-7ee9d000	Deferred        libxcb-xlib.so.0
ELF	7ee9d000-7eea0000	Deferred        libxau.so.6
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	7eff0000-7eff5000	Deferred        libxxf86vm.so.1
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7c93000-b7c9d000	Deferred        libnss_nis.so.2
ELF	b7c9f000-b7ca3000	Deferred        libdl.so.2
ELF	b7ca3000-b7df2000	Deferred        libc.so.6
ELF	b7df2000-b7e0a000	Deferred        libpthread.so.0
ELF	b7e1a000-b7f2f000	Deferred        libwine.so.1
ELF	b7f31000-b7f4d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000016    0
	00000014    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000013    0
	00000012    0
00000017 (D) C:\windows\temp\EBU21e.EXE
	00000018    0 <==
00000019 
	0000001b    0
	0000001a    0
Backtrace:
=>1 0x00000000 (0x7f22f2b8)
  2 0x00419159 in ebu21e (+0x19159) (0x7f22f2c8)
  3 0x0043d2a0 in ebu21e (+0x3d2a0) (0x7f22f334)
  4 0x7edfb69a WINPROC_wrapper+0x1a() in user32 (0x7f22f364)
  5 0x7edfd4d8 in user32 (+0xad4d8) (0x7f22f3a4)
  6 0x7ee00615 in user32 (+0xb0615) (0x7f22f874)
  7 0x7ee00f40 in user32 (+0xb0f40) (0x7f22f8b4)
  8 0x7ed8ab87 DefDlgProcW+0x87() in user32 (0x7f22f8e4)
  9 0x7edfb69a WINPROC_wrapper+0x1a() in user32 (0x7f22f914)
  10 0x7edfbd7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f954)
  11 0x7ee01151 in user32 (+0xb1151) (0x7f22f994)
  12 0x7edc487a in user32 (+0x7487a) (0x7f22fa04)
  13 0x7edc7afd in user32 (+0x77afd) (0x7f22fa64)
  14 0x7edc7f6a SendMessageW+0x4a() in user32 (0x7f22faa4)
  15 0x7ed9043c in user32 (+0x4043c) (0x7f22fc74)
  16 0x7ed91666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fc94)
  17 0x7ed91791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fcc4)
  18 0x0043cd5c in ebu21e (+0x3cd5c) (0x7f22fd04)
  19 0x0042d54c in ebu21e (+0x2d54c) (0x7f22fd18)
  20 0x0043cd01 in ebu21e (+0x3cd01) (0x7f22fd24)
  21 0x0043cfc3 in ebu21e (+0x3cfc3) (0x7f22fd34)
  22 0x0040456b in ebu21e (+0x456b) (0x7f22ff08)
  23 0x7b875be7 in kernel32 (+0x55be7) (0x7f22ffe8)

```

---

### Post by Kernel_Krunch on 2008-06-05
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by HpZ on 2008-06-05
> **Kernel_Krunch said:**
> [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

```
andy@andy-desktop:~$ sudo sysctl -w vm.mmap_min_addr=0
vm.mmap_min_addr = 0
andy@andy-desktop:~$ 

```
Is that suppose to happen?

---

### Post by HpZ on 2008-06-05
Bamp

---

### Post by Kernel_Krunch on 2008-06-06
> **HpZ said:**
> 
Is that suppose to happen?

yes, do you still get the error?

what version of Ubuntu and wine do you have?

---

### Post by HpZ on 2008-06-08
Ubutnu 8.04 and wine 0.9.59

---

