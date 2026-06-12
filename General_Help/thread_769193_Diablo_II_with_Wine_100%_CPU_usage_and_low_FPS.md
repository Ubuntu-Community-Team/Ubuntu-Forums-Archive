---
title: "Diablo II with Wine: 100% CPU usage and low FPS"
date: 2008-04-26
forum: General Help
---

### Post by alyndaker on 2008-04-26
I've been running Diablo II for a long time with Wine and had no troubles.  I then took a break for about 6 months and tried to play again to find that when I run the game, I end up with 100% CPU usage and a low (~15) framerate instead of the usual 75 fps.  I don't know for sure that it didn't previously use the full CPU.  

Things I've tried:
1)  Every relevant permutation of settings with winecfg
2)  All permutations of graphics with Diablo (fullscreen, windowed, D3D, DirectDraw, sound quality, video resolution, lighting quality
3)  Both D2Loader and the game from the CD
4)  Different hardware (my mainboard died in between)

Here's the output from Wine while running the game:

```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f8ec,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:ntdll:NtQueryInformationToken Unhandled Token Information class 11!
wine: Unhandled page fault on read access to 0x7c260048 at address 0x6f9b9859 (thread 001d), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x7c260048 in 32-bit code (0x6f9b9859).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6f9b9859 ESP:79ddda14 EBP:00000000 EFLAGS:00210206(   - 00      - RIP1)
 EAX:7c260000 EBX:7c260000 ECX:7ee46520 EDX:7ee46524
 ESI:7c260000 EDI:0001ffff
Stack dump:
0x79ddda14:  6f9b9800 00000000 79ddda48 7bc89704
0x79ddda24:  00001344 00000000 00000000 00869330
0x79ddda34:  00070c30 000014fc 7bc6b0de 00000000
0x79ddda44:  6f9b9800 79dddae8 7bc6b772 6f9b9800
0x79ddda54:  00000000 10012a03 00000000 00000020
0x79ddda64:  7c114418 00000000 7c114410 00000000
Backtrace:
0x6f9b9859: cmpl	%ebp,0x48(%eax)
Modules:
Module	Address			Debug info	Name (134 modules)
PE	  400000-  40b038	Deferred        game
PE	10000000-1001a000	Deferred        smackw32
PE	60000000-6002e000	Deferred        ijl11
PE	6f8c0000-6f8d3000	Deferred        d2ddraw
PE	6f8e0000-6f9ae000	Deferred        d2win
PE	6f9b0000-6f9c9000	Export          d2sound
PE	6f9d0000-6fa0f000	Deferred        d2multi
PE	6fa20000-6fa34000	Deferred        d2mcpclient
PE	6fa40000-6fa6d000	Deferred        d2launch
PE	6fa80000-6faa1000	Deferred        d2gfx
PE	6fab0000-6fbe5000	Deferred        d2client
PE	6fbf0000-6fc50000	Deferred        storm
PE	6fd50000-6fdf9000	Deferred        d2common
PE	6fe10000-6ff17000	Deferred        d2cmp
PE	6ff20000-6ff42000	Deferred        bnclient
PE	6ff50000-6ffac000	Deferred        fog
ELF	7aceb000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c38b000-7c42f000	Deferred        libgl.so.1
ELF	7c42f000-7c530000	Deferred        wined3d<elf>
  \-PE	7c440000-7c530000	\               wined3d
PE	7c9a0000-7c9e1000	Deferred        binkw32
ELF	7c9ea000-7ca40000	Deferred        ddraw<elf>
  \-PE	7c9f0000-7ca40000	\               ddraw
ELF	7d281000-7d296000	Deferred        psapi<elf>
  \-PE	7d290000-7d296000	\               psapi
ELF	7d296000-7d2e0000	Deferred        dbghelp<elf>
  \-PE	7d2a0000-7d2e0000	\               dbghelp
ELF	7d3f8000-7d40f000	Deferred        imagehlp<elf>
  \-PE	7d400000-7d40f000	\               imagehlp
ELF	7daa5000-7dab0000	Deferred        libgcc_s.so.1
ELF	7dce2000-7dce8000	Deferred        libnss_dns.so.2
ELF	7dce8000-7dceb000	Deferred        libnss_mdns4_minimal.so.2
ELF	7df28000-7df2a000	Deferred        libnvidia-tls.so.1
ELF	7df2a000-7df3e000	Deferred        midimap<elf>
  \-PE	7df30000-7df3e000	\               midimap
ELF	7df3e000-7df64000	Deferred        msacm32<elf>
  \-PE	7df40000-7df64000	\               msacm32
ELF	7df64000-7df7b000	Deferred        msacm32<elf>
  \-PE	7df70000-7df7b000	\               msacm32
ELF	7df7b000-7e03e000	Deferred        libasound.so.2
ELF	7e03e000-7e074000	Deferred        winealsa<elf>
  \-PE	7e050000-7e074000	\               winealsa
ELF	7e074000-7e0be000	Deferred        dsound<elf>
  \-PE	7e080000-7e0be000	\               dsound
ELF	7e0be000-7e0dd000	Deferred        imm32<elf>
  \-PE	7e0c0000-7e0dd000	\               imm32
ELF	7e0dd000-7e16b000	Deferred        winmm<elf>
  \-PE	7e0f0000-7e16b000	\               winmm
ELF	7e16b000-7e197000	Deferred        ws2_32<elf>
  \-PE	7e170000-7e197000	\               ws2_32
ELF	7e197000-7e1b1000	Deferred        wsock32<elf>
  \-PE	7e1a0000-7e1b1000	\               wsock32
ELF	7e1b1000-7e1fe000	Deferred        libgcrypt.so.11
ELF	7e1fe000-7e20e000	Deferred        libtasn1.so.3
ELF	7e20e000-7e216000	Deferred        libkrb5support.so.0
ELF	7e216000-7e248000	Deferred        libcrypt.so.1
ELF	7e248000-7e2bd000	Deferred        libgnutls.so.13
ELF	7e2bd000-7e2e0000	Deferred        libk5crypto.so.3
ELF	7e2e0000-7e36d000	Deferred        libkrb5.so.3
ELF	7e36d000-7e396000	Deferred        libgssapi_krb5.so.2
ELF	7e396000-7e3c9000	Deferred        libcups.so.2
ELF	7e3f9000-7e40c000	Deferred        libresolv.so.2
ELF	7e418000-7e436000	Deferred        iphlpapi<elf>
  \-PE	7e420000-7e436000	\               iphlpapi
ELF	7e436000-7e496000	Deferred        rpcrt4<elf>
  \-PE	7e440000-7e496000	\               rpcrt4
ELF	7e496000-7e53a000	Deferred        ole32<elf>
  \-PE	7e4a0000-7e53a000	\               ole32
ELF	7e55f000-7e591000	Deferred        uxtheme<elf>
  \-PE	7e570000-7e591000	\               uxtheme
ELF	7e591000-7e59a000	Deferred        libxcursor.so.1
ELF	7e59a000-7e59f000	Deferred        libxfixes.so.3
ELF	7e59f000-7e5a2000	Deferred        libxcomposite.so.1
ELF	7e5a2000-7e5a8000	Deferred        libxrandr.so.2
ELF	7e5a8000-7e5b0000	Deferred        libxrender.so.1
ELF	7e5b0000-7e5b3000	Deferred        libxinerama.so.1
ELF	7e5b3000-7e5b8000	Deferred        libxdmcp.so.6
ELF	7e5b8000-7e5d0000	Deferred        libxcb.so.1
ELF	7e5d0000-7e5d2000	Deferred        libxcb-xlib.so.0
ELF	7e5d2000-7e6b9000	Deferred        libx11.so.6
ELF	7e6b9000-7e6c7000	Deferred        libxext.so.6
ELF	7e6c7000-7e6cc000	Deferred        libxxf86vm.so.1
ELF	7e6cc000-7e6e4000	Deferred        libice.so.6
ELF	7e6e4000-7e6ec000	Deferred        libsm.so.6
ELF	7e6ec000-7e6f0000	Deferred        libgpg-error.so.0
ELF	7e6f0000-7e6f3000	Deferred        libkeyutils.so.1
ELF	7e6f3000-7e6f6000	Deferred        libcom_err.so.2
ELF	7e6f8000-7e789000	Deferred        winex11<elf>
  \-PE	7e710000-7e789000	\               winex11
ELF	7e7cf000-7e7f0000	Deferred        libexpat.so.1
ELF	7e7f0000-7e81a000	Deferred        libfontconfig.so.1
ELF	7e826000-7e83b000	Deferred        libz.so.1
ELF	7e83b000-7e8ab000	Deferred        libfreetype.so.6
ELF	7e8ab000-7e8ae000	Deferred        libxau.so.6
ELF	7e8b7000-7e920000	Deferred        msvcrt<elf>
  \-PE	7e8d0000-7e920000	\               msvcrt
ELF	7e920000-7e934000	Deferred        lz32<elf>
  \-PE	7e930000-7e934000	\               lz32
ELF	7e934000-7e94d000	Deferred        version<elf>
  \-PE	7e940000-7e94d000	\               version
ELF	7e94d000-7e983000	Deferred        winspool<elf>
  \-PE	7e950000-7e983000	\               winspool
ELF	7e983000-7ea42000	Deferred        comctl32<elf>
  \-PE	7e990000-7ea42000	\               comctl32
ELF	7ea42000-7ea9b000	Deferred        shlwapi<elf>
  \-PE	7ea50000-7ea9b000	\               shlwapi
ELF	7ea9b000-7eba5000	Deferred        shell32<elf>
  \-PE	7eab0000-7eba5000	\               shell32
ELF	7eba5000-7ec4e000	Deferred        comdlg32<elf>
  \-PE	7ebb0000-7ec4e000	\               comdlg32
ELF	7ec4e000-7ec9f000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ec9f000	\               advapi32
ELF	7ec9f000-7ed3a000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3a000	\               gdi32
ELF	7ed3a000-7ee80000	Deferred        user32<elf>
  \-PE	7ed50000-7ee80000	\               user32
ELF	7efa2000-7efad000	Deferred        libnss_files.so.2
ELF	7efad000-7efb7000	Deferred        libnss_nis.so.2
ELF	7efb7000-7efcf000	Deferred        libnsl.so.1
ELF	7efcf000-7eff4000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
PE	7f610000-7f624000	Deferred        d2lang
PE	7fa70000-7fa7d000	Deferred        d2net
PE	7fb90000-7fcb2000	Deferred        d2game
ELF	b7cf1000-b7cf5000	Deferred        libdl.so.2
ELF	b7cf5000-b7e44000	Deferred        libc.so.6
ELF	b7e44000-b7e5c000	Deferred        libpthread.so.0
ELF	b7e68000-b7f7d000	Deferred        libwine.so.1
ELF	b7f7f000-b7f9b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Diablo II\Game.exe
	0000001d    0 <==
	00000018    1
	00000017    0
	00000009    0
0000000c 
	0000000e    0
	0000000d    0
00000019 
	0000001b    0
	0000001a    0
Backtrace:


```

The only other thought I had was that perhaps wine was updated in the time I took off from the game.  Has anyone got any other suggestion?  I'm going to try reverting to an old version to see if that makes a difference.

---

