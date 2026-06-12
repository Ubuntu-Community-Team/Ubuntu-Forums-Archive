---
title: "Wine Audio problem Edgy"
date: 2007-05-07
forum: General Help
---

### Post by widz on 2007-05-07
Hi! I'm having problems with the wine. When I got in the winecfg window, if I click on the Audio tab, the following text is appearing in my terminal:
```
*** glibc detected *** winecfg.exe: free(): invalid pointer: 0x7c2d93f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7cf38bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7cf3a44]
/usr/bin/../lib/libstdc++.so.6(_ZdlPv+0x21)[0x7e8c5fc1]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x18e)[0x73b8a71e]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x56)[0x73b5bf66]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts9ModuleDefC1ERNS_6BufferE+0xa4)[0x73b5c1be]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts10IDLFileReg7startupEv+0xb5)[0x73b5c279]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts14StartupManager7startupEv+0x3e)[0x73b3f742]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x80a)[0x73b7200c]
/usr/lib/libartscbackend.so.0(arts_backend_init+0x8d)[0x73e66e6f]
/usr/bin/../lib/libartsc.so.0(arts_init+0x231)[0x7c45b76c]
/usr/bin/../lib/wine/winearts.drv.so(ARTS_WaveInit+0x72)[0x7bfe7652]
/usr/bin/../lib/wine/winearts.drv.so(ARTS_DriverProc+0x96)[0x7bfe31e6]
/usr/bin/../lib/wine/winmm.dll.so[0x7e62a51a]
/usr/bin/../lib/wine/winmm.dll.so(DRIVER_TryOpenDriver32+0xe9)[0x7e62a889]
/usr/bin/../lib/wine/winmm.dll.so(OpenDriver+0x1cf)[0x7e62ac3f]
/usr/bin/../lib/wine/winmm.dll.so(OpenDriverA+0x45)[0x7e62ad05]
/usr/bin/../lib/wine/winecfg.exe.so[0x7edabe38]
/usr/bin/../lib/wine/winecfg.exe.so(AudioDlgProc+0x2cf)[0x7edada6f]
/usr/bin/../lib/wine/user32.dll.so[0x7ea66b4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea689f8]
/usr/bin/../lib/wine/user32.dll.so(WINPROC_CallDlgProcW+0x5a)[0x7ea6c23a]
/usr/bin/../lib/wine/user32.dll.so(DefDlgProcW+0x8a)[0x7e9fe45a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea66b4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6727e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea6c333]
/usr/bin/../lib/wine/user32.dll.so[0x7ea35458]
/usr/bin/../lib/wine/user32.dll.so(SendMessageTimeoutW+0x1a0)[0x7ea39bc0]
/usr/bin/../lib/wine/user32.dll.so(SendMessageW+0x50)[0x7ea39c30]
/usr/bin/../lib/wine/user32.dll.so[0x7ea03841]
/usr/bin/../lib/wine/user32.dll.so(CreateDialogIndirectParamAorW+0x36)[0x7ea048d6]
/usr/bin/../lib/wine/user32.dll.so(CreateDialogIndirectParamW+0x41)[0x7ea04921]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e715a42]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e71646f]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e71841f]
/usr/bin/../lib/wine/user32.dll.so[0x7ea66b4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea689f8]
/usr/bin/../lib/wine/user32.dll.so(WINPROC_CallDlgProcW+0x5a)[0x7ea6c23a]
/usr/bin/../lib/wine/user32.dll.so(DefDlgProcW+0x8a)[0x7e9fe45a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea66b4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6727e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea6c333]
/usr/bin/../lib/wine/user32.dll.so[0x7ea35458]
/usr/bin/../lib/wine/user32.dll.so(SendMessageTimeoutW+0x1a0)[0x7ea39bc0]
/usr/bin/../lib/wine/user32.dll.so(SendMessageW+0x50)[0x7ea39c30]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e72cd4a]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e7319dc]
/usr/bin/../lib/wine/user32.dll.so[0x7ea66b4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6727e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea6c333]
/usr/bin/../lib/wine/user32.dll.so(DispatchMessageW+0x153)[0x7ea35953]
/usr/bin/../lib/wine/user32.dll.so(IsDialogMessageW+0xfb)[0x7ea04e3b]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e7132f0]
/usr/bin/../lib/wine/comctl32.dll.so(PropertySheetW+0x25d)[0x7e7199fd]
/usr/bin/../lib/wine/winecfg.exe.so(WinMain+0x364)[0x7edb3d34]
/usr/bin/../lib/wine/winecfg.exe.so(main+0xa3)[0x7edb8f43]
/usr/bin/../lib/wine/winecfg.exe.so[0x7edb8e6b]
/usr/bin/../lib/wine/kernel32.dll.so[0x7ee90ede]
/usr/bin/../lib/libwine.so.1[0xb7de7567]
======= Memory map: ========
00000000-00110000 ---p 00000000 00:00 0 
00110000-00180000 rw-p 00110000 00:00 0 
00180000-00220000 ---p 00180000 00:00 0 
00220000-00221000 rw-p 00220000 00:00 0 
00221000-00230000 ---p 00221000 00:00 0 
00230000-00231000 ---p 00230000 00:00 0 
00231000-00340000 rw-p 00231000 00:00 0 
00340000-00348000 ---p 00340000 00:00 0 
00348000-00350000 ---p 00348000 00:00 0 
00350000-00370000 ---p 00350000 00:00 0 
00370000-00380000 rw-p 00370000 00:00 0 
00380000-60000000 ---p 00380000 00:00 0 
7399a000-739cd000 r-xp 00000000 03:07 135283     /usr/lib/libkmedia2_idl.so.1.0.0
739cd000-739db000 rw-p 00033000 03:07 135283     /usr/lib/libkmedia2_idl.so.1.0.0
739db000-739df000 r-xp 00000000 03:07 130069     /usr/lib/libogg.so.0.5.3
739df000-739e0000 rw-p 00003000 03:07 130069     /usr/lib/libogg.so.0.5.3
739e0000-739f9000 r-xp 00000000 03:07 130217     /usr/lib/libvorbis.so.0.3.1
739f9000-73a07000 rw-p 00019000 03:07 130217     /usr/lib/libvorbis.so.0.3.1
73a07000-73a12000 r-xp 00000000 03:07 130219     /usr/lib/libvorbisenc.so.2.0.2
73a12000-73b01000 rw-p 0000a000 03:07 130219     /usr/lib/libvorbisenc.so.2.0.2
73b01000-73b03000 rw-p 73b01000 00:00 0 
73b03000-73b99000 r-xp 00000000 03:07 135284     /usr/lib/libmcop.so.1.0.0
73b99000-73ba7000 rw-p 00096000 03:07 135284     /usr/lib/libmcop.so.1.0.0
73ba7000-73bf1000 r-xp 00000000 03:07 129549     /usr/lib/libXt.so.6.0.0
73bf1000-73bf5000 rw-p 00049000 03:07 129549     /usr/lib/libXt.so.6.0.0
73bf5000-73c0a000 r-xp 00000000 03:07 128987     /usr/lib/libaudio.so.2.4
73c0a000-73c0b000 rw-p 00014000 03:07 128987     /usr/lib/libaudio.so.2.4
73c0b000-73c29000 r-xp 00000000 03:07 129588     /usr/lib/libaudiofile.so.0.0.2
73c29000-73c2b000 rw-p 0001e000 03:07 129588     /usr/lib/libaudiofile.so.0.0.2
73c2b000-73cb3000 r-xp 00000000 03:07 135275     /usr/lib/libartsflow_idl.so.1.0.0
73cb3000-73cdb000 rw-p 00087000 03:07 135275     /usr/lib/libartsflow_idl.so.1.0.0
73cdb000-73d25000 r-xp 00000000 03:07 135287     /usr/lib/libsoundserver_idl.so.1.0.0
73d25000-73d3c000 rw-p 00049000 03:07 135287     /usr/lib/libsoundserver_idl.so.1.0.0
73d3c000-73e3b000 r-xp 00000000 03:07 135274     /usr/lib/libartsflow.so.1.0.0
73e3b000-73e59000 rw-p 000fe000 03:07 135274     /usr/lib/libartsflow.so.1.0.0
73e59000-73e5e000 rw-p 73e59000 00:00 0 
73e5e000-73e6b000 r-xp 00000000 03:07 135271     /usr/lib/libartscbackend.so.0.0.0
73e6b000-73e6e000 rw-p 0000d000 03:07 135271     /usr/lib/libartscbackend.so.0.0.0
73e6e000-73eff000 r-xp 00000000 03:07 129811     /usr/lib/libglib-2.0.so.0.1200.4
73eff000-73f00000 rw-p 00091000 03:07 129811     /usr/lib/libglib-2.0.so.0.1200.4
73f00000-7bf00000 rw-s 00003000 00:0d 9281       /dev/dri/card0
7bf00000-7bf02000 r-xp 00000000 03:07 135234     /usr/bin/wine-pthread
7bf02000-7bf03000 rw-p 00001000 03:07 135234     /usr/bin/wine-pthread
7bf03000-7bf09000 r-xp 00000000 03:07 135261     /usr/lib/libvorbisfile.so.3.1.1
7bf09000-7bf0a000 rw-p 00005000 03:07 135261     /usr/lib/libvorbisfile.so.3.1.1
7bf0a000-7bfbd000 r-xp 00000000 03:07 129573     /usr/lib/libasound.so.2.0.0
7bfbd000-7bfc2000 rw-p 000b2000 03:07 129573     /usr/lib/libasound.so.2.0.0
7bfc2000-7bfcb000 r-xp 00000000 03:07 129691     /usr/lib/libesd.so.0.2.36
7bfcb000-7bfcc000 rw-p 00008000 03:07 129691     /usr/lib/libesd.so.0.2.36
7bfcc000-7bfd0000 r-xp 00000000 03:07 129915     /usr/lib/libgthread-2.0.so.0.1200.4
7bfd0000-7bfd1000 rw-p 00003000 03:07 129915     /usr/lib/libgthread-2.0.so.0.1200.4
7bfd1000-7bfe0000 r-xp 00000000 03:07 183446     /usr/lib/wine/winearts.drv.so
7bfe0000-7bfe1000 rw-p 7bfe0000 00:00 0 
7bfe1000-7bfe9000 r-xp 00010000 03:07 183446     /usr/lib/wine/winearts.drv.so
7bfe9000-7bfea000 rwxp 00018000 03:07 183446     /usr/lib/wine/winearts.drv.so
7bfea000-7bfeb000 rw-p 7bfea000 00:00 0 
7bfeb000-7bff0000 r-xp 00000000 03:07 183321     /usr/lib/wine/midimap.dll.so
7bff0000-7bff1000 rw-p 7bff0000 00:00 0 
7bff1000-7bfff000 r-xp 00006000 03:07 183321     /usr/lib/wine/midimap.dll.so
7bfff000-7c000000 rwxp 00013000 03:07 183321     /usr/lib/wine/midimap.dll.so
7c000000-7c002000 r-xp 00001000 03:07 135235     /usr/bin/wine-preloader
7c002000-7c003000 rw-p 00002000 03:07 135235     /usr/bin/wine-preloader
7c003000-7c344000 rw-p 7c003000 00:00 0          [heap]
7c348000-7c34b000 r-xp 00000000 03:07 129823     /usr/lib/libgmodule-2.0.so.0.1200.4
7c34b000-7c34c000 rw-p 00002000 03:07 129823     /usr/lib/libgmodule-2.0.so.0.1200.4
7c34c000-7c350000 r-xp 00000000 03:07 183328     /usr/lib/wine/msacm32.dll.so
7c350000-7c351000 rw-p 7c350000 00:00 0 
7c351000-7c36e000 r-xp 00005000 03:07 183328     /usr/lib/wine/msacm32.dll.so
7c36e000-7c36f000 rw-p 00021000 03:07 183328     /usr/lib/wine/msacm32.dll.so
7c36f000-7c370000 rwxp 00022000 03:07 183328     /usr/lib/wine/msacm32.dll.so
7c370000-7c372000 rw-p 00023000 03:07 183328     /usr/lib/wine/msacm32.dll.so
7c372000-7c380000 r-xp 00000000 03:07 183329     /usr/lib/wine/msacm32.drv.so
7c380000-7c381000 rw-p 7c380000 00:00 0 
7c381000-7c389000 r-xp 0000f000 03:07 183329     /usr/lib/wine/msacm32.drv.so
7c389000-7c38a000 rwxp 00016000 03:07 183329     /usr/lib/wine/msacm32.drv.so
7c38a000-7c390000 r-xp 00000000 03:07 183452     /usr/lib/wine/wineoss.drv.so
7c390000-7c391000 rw-p 7c390000 00:00 0 
7c391000-7c3c0000 r-xp 00007000 03:07 183452     /usr/lib/wine/wineoss.drv.so
7c3c0000-7c3c1000 rwxp 00035000 03:07 183452     /usr/lib/wine/wineoss.drv.so
7c3c1000-7c3c2000 rw-p 00036000 03:07 183452     /usr/lib/wine/wineoss.drv.so
7c3c2000-7c3c6000 rw-p 7c3c2000 00:00 0 
7c3c6000-7c3c9000 r-xp 00000000 03:07 129865     /usr/lib/libgpg-error.so.0.2.0
7c3c9000-7c3ca000 rw-p 00002000 03:07 129865     /usr/lib/libgpg-error.so.0.2.0
7c3ca000-7c416000 r-xp 00000000 03:07 129747     /usr/lib/libgcrypt.so.11.2.1
7c416000-7c418000 rw-p 0004b000 03:07 129747     /usr/lib/libgcrypt.so.11.2.1
7c418000-7c42a000 r-xp 00000000 03:07 130198     /usr/lib/libtasn1.so.3.0.5
7c42a000-7c42b000 rw-p 00011000 03:07 130198     /usr/lib/libtasn1.so.3.0.5
7c42b000-7c430000 r-xp 00000000 03:07 49505      /lib/tls/i686/cmov/libcrypt-2.4.so
7c430000-7c432000 rw-p 00004000 03:07 49505      /lib/tls/i686/cmov/libcrypt-2.4.so
7c432000-7c459000 rw-p 7c432000 00:00 0 
7c45a000-7c45f000 r-xp 00000000 03:07 135230     /usr/lib/libartsc.so.0.0.0
7c45f000-7c460000 rw-p 00004000 03:07 135230     /usr/lib/libartsc.so.0.0.0
7c460000-7c465000 r--p 00000000 03:07 183209     /usr/share/wine/fonts/sserife.fon
7c465000-7c4ce000 r-xp 00000000 03:07 129861     /usr/lib/libgnutls.so.13.0.5
7c4ce000-7c4d4000 rw-p 00068000 03:07 129861     /usr/lib/libgnutls.so.13.0.5
7c4d4000-7c501000 r-xp 00000000 03:07 129635     /usr/lib/libcups.so.2
7c501000-7c503000 rw-p 0002d000 03:07 129635     /usr/lib/libcups.so.2
7c503000-7c523000 rw-s 00000000 00:08 4784141    /SYSV00000000 (deleted)
7c523000-7c52b000 rw-s 00000000 00:08 4751372    /SYSV00000000 (deleted)
7c52b000-7c530000 r--p 00000000 03:07 183209     /usr/share/wine/fonts/sserife.fon
7c530000-7c535000 r--p 00000000 03:07 183209     /usr/share/wine/fonts/sserife.fon
7c535000-7c53d000 r-xp 00000000 03:07 129515     /usr/lib/libXcursor.so.1.0.2
7c53d000-7c53e000 rw-p 00007000 03:07 129515     /usr/lib/libXcursor.so.1.0.2
7c53e000-7c550000 r-xp 00000000 03:07 183300     /usr/lib/wine/imm32.dll.so
7c550000-7c551000 rw-p 7c550000 00:00 0 
7c551000-7c558000 r-xp 00013000 03:07 183300     /usr/lib/wine/imm32.dll.so
7c558000-7c559000 rwxp 0001a000 03:07 183300     /usr/lib/wine/imm32.dll.so
7c559000-7c55a000 rw-p 0001b000 03:07 183300     /usr/lib/wine/imm32.dll.so
7c55a000-7c576000 r-xp 00000000 03:07 177852     /usr/lib/X11/locale/common/ximcp.so.2.0.0
7c576000-7c578000 rw-p 0001b000 03:07 177852     /usr/lib/X11/locale/common/ximcp.so.2.0.0
7c578000-7c59d000 rw-p 7c578000 00:00 0 
7c59d000-7ca9d000 rw-s 0000a000 00:0d 9281       /dev/dri/card0
7ca9d000-7cf9d000 rw-s 00009000 00:0d 9281       /dev/dri/card0
7cfa0000-7cfa2000 r--p 00000000 03:07 183219     /usr/share/wine/fonts/vgasys.fon
7cfa2000-7cfa9000 r-xp 00000000 03:07 129545     /usr/lib/libXrender.so.1.3.0
7cfa9000-7cfaa000 rw-p 00006000 03:07 129545     /usr/lib/libXrender.so.1.3.0
7cfaa000-7d0a8000 rw-p 7cfaa000 00:00 0 
7d0a8000-7d0ac000 r-xp 00000000 03:07 129525     /usr/lib/libXfixes.so.3.1.0
7d0ac000-7d0ad000 rw-p 00003000 03:07 129525     /usr/lib/libXfixes.so.3.1.0
7d0ad000-7d1ed000 rw-s 00016000 00:0d 9281       /dev/dri/card0
7d1ed000-7d82d000 rw-s 00007000 00:0d 9281       /dev/dri/card0
7d82d000-7d92d000 rw-s 00006000 00:0d 9281       /dev/dri/card0
7d92d000-7d92e000 rw-s 00005000 00:0d 9281       /dev/dri/card0
7d92e000-7d93e000 rw-s 00004000 00:0d 9281       /dev/dri/card0
7d93e000-7d945000 r-xp 00000000 03:07 49519      /lib/tls/i686/cmov/librt-2.4.so
7d945000-7d947000 rw-p 00006000 03:07 49519      /lib/tls/i686/cmov/librt-2.4.so
7d947000-7d948000 r-xp 00000000 03:07 180427     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
7d948000-7d949000 rw-p 00000000 03:07 180427     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
7d949000-7d94b000 r-xp 00000000 03:07 129543     /usr/lib/libXrandr.so.2.0.0
7d94b000-7d94c000 rw-p 00002000 03:07 129543     /usr/lib/libXrandr.so.2.0.0
7d94c000-7d953000 rwxp 7d94c000 00:00 0 
7d953000-7da03000 r-xp 00000000 03:07 130191     /usr/lib/libstdc++.so.5.0.7
7da03000-7da08000 rw-p 000af000 03:07 130191     /usr/lib/libstdc++.so.5.0.7
7da08000-7da0d000 rw-p 7da08000 00:00 0 
7da0d000-7e219000 r-xp 00000000 03:07 448937     /usr/lib/dri/fglrx_dri.so
7e219000-7e262000 rw-p 0080b000 03:07 448937     /usr/lib/dri/fglrx_dri.so
7e262000-7e2ec000 rw-p 7e262000 00:00 0 
7e2ec000-7e384000 r-xp 00000000 03:07 135514     /usr/lib/libGL.so.1.2
7e384000-7e389000 rw-p 00098000 03:07 135514     /usr/lib/libGL.so.1.2
7e389000-7e38c000 rw-p 7e389000 00:00 0 
7e38c000-7e452000 r-xp 00000000 03:07 130778     /usr/lib/libX11.so.6.2.0
7e452000-7e455000 rw-p 000c5000 03:07 130778     /usr/lib/libX11.so.6.2.0
7e455000-7e461000 r-xp 00000000 03:07 129523     /usr/lib/libXext.so.6.4.0
7e461000-7e462000 rw-p 0000c000 03:07 129523     /usr/lib/libXext.so.6.4.0
7e462000-7e477000 r-xp 00000000 03:07 129482     /usr/lib/libICE.so.6.3.0
7e477000-7e478000 rw-p 00014000 03:07 129482     /usr/lib/libICE.so.6.3.0
7e478000-7e47a000 rw-p 7e478000 00:00 0 
7e47a000-7e490000 r-xp 00000000 03:07 183471     /usr/lib/wine/winex11.drv.so
7e490000-7e491000 rw-p 7e490000 00:00 0 
7e491000-7e4fc000 r-xp 00017000 03:07 183471     /usr/lib/wine/winex11.drv.so
7e4fc000-7e4fe000 rw-p 00082000 03:07 183471     /usr/lib/wine/winex11.drv.so
7e4fe000-7e4ff000 rwxp 00084000 03:07 183471     /usr/lib/wine/winex11.drv.so
7e4ff000-7e501000 rw-p 00085000 03:07 183471     /usr/lib/wine/winex11.drv.so
7e501000-7e506000 rw-p 7e501000 00:00 0 
7e506000-7e522000 r-xp 00000000 03:07 129704     /usr/lib/libexpat.so.1.0.0
7e522000-7e524000 rw-p 0001c000 03:07 129704     /usr/lib/libexpat.so.1.0.0
7e524000-7e54d000 r-xp 00000000 03:07 129710     /usr/lib/libfontconfig.so.1.0.4
7e54d000-7e552000 rw-p 00028000 03:07 129710     /usr/lib/libfontconfig.so.1.0.4
7e552000-7e553000 rw-p 7e552000 00:00 0 
7e553000-7e566000 r-xp 00000000 03:07 130250     /usr/lib/libz.so.1.2.3
7e566000-7e567000 rw-p 00012000 03:07 130250     /usr/lib/libz.so.1.2.3
7e567000-7e5ce000 r-xp 00000000 03:07 129643     /usr/lib/libfreetype.so.6.3.10
7e5ce000-7e5d1000 rw-p 00067000 03:07 129643     /usr/lib/libfreetype.so.6.3.10
7e5d1000-7e5e0000 r-xp 00000000 03:07 183422     /usr/lib/wine/uxtheme.dll.so
7e5e0000-7e5e1000 rw-p 7e5e0000 00:00 0 
7e5e1000-7e601000 r-xp 00010000 03:07 183422     /usr/lib/wine/uxtheme.dll.so
7e601000-7e602000 rwxp 00030000 03:07 183422     /usr/lib/wine/uxtheme.dll.so
7e602000-7e603000 rw-p 00031000 03:07 183422     /usr/lib/wine/uxtheme.dll.so
7e603000-7e610000 r-xp 00000000 03:07 183443     /usr/lib/wine/winmm.dll.so
7e610000-7e611000 rw-p 7e610000 00:00 0 
7e611000-7e647000 r-xp 0000e000 03:07 183443     /usr/lib/wine/winmm.dll.so
7e647000-7e648000 rw-p 00044000 03:07 183443     /usr/lib/wine/winmm.dll.so
7e648000-7e649000 rwxp 00045000 03:07 183443     /usr/lib/wine/winmm.dll.so
7e649000-7e68c000 rw-p 00046000 03:07 183443     /usr/lib/wine/winmm.dll.so
7e68c000-7e690000 r-xp 00000000 03:07 183455     /usr/lib/wine/winspool.drv.so
7e690000-7e691000 rw-p 7e690000 00:00 0 
7e691000-7e6b8000 r-xp 00005000 03:07 183455     /usr/lib/wine/winspool.drv.so
7e6b8000-7e6b9000 rw-p 0002b000 03:07 183455     /usr/lib/wine/winspool.drv.so
7e6b9000-7e6ba000 rwxp 0002c000 03:07 183455     /usr/lib/wine/winspool.drv.so
7e6ba000-7e6bc000 rw-p 0002d000 03:07 183455     /usr/lib/wine/winspool.drv.so
7e6bc000-7e6d0000 r-xp 00000000 03:07 183246     /usr/lib/wine/comctl32.dll.so
7e6d0000-7e6d1000 rw-p 7e6d0000 00:00 0 
7e6d1000-7e76a000 r-xp 00015000 03:07 183246     /usr/lib/wine/comctl32.dll.so
7e76a000-7e76b000 rw-p 000ae000 03:07 183246     /usr/lib/wine/comctl32.dll.so
7e76b000-7e76c000 rwxp 000af000 03:07 183246     /usr/lib/wine/comctl32.dll.so
7e76c000-7e77b000 rw-p 000b0000 03:07 183246     /usr/lib/wine/comctl32.dll.so
7e77b000-7e77c000 rw-p 7e77b000 00:00 0 
7e77c000-7e78b000 r-xp 00000000 03:07 49518      /lib/tls/i686/cmov/libresolv-2.4.so
7e78b000-7e78d000 rw-p 0000f000 03:07 49518      /lib/tls/i686/cmov/libresolv-2.4.so
7e78d000-7e78f000 rw-p 7e78d000 00:00 0 
7e78f000-7e7a0000 r-xp 00000000 03:07 183303     /usr/lib/wine/iphlpapi.dll.so
7e7a0000-7e7a1000 rw-p 7e7a0000 00:00 0 
7e7a1000-7e7ab000 r-xp 00012000 03:07 183303     /usr/lib/wine/iphlpapi.dll.so
7e7ab000-7e7ac000 rw-p 0001b000 03:07 183303     /usr/lib/wine/iphlpapi.dll.so
7e7ac000-7e7ad000 rwxp 0001c000 03:07 183303     /usr/lib/wine/iphlpapi.dll.so
7e7ad000-7e7c0000 r-xp 00000000 03:07 183386     /usr/lib/wine/rpcrt4.dll.so
7e7c0000-7e7c1000 rw-p 7e7c0000 00:00 0 
7e7c1000-7e7f7000 r-xp 00014000 03:07 183386     /usr/lib/wine/rpcrt4.dll.so
7e7f7000-7e7fc000 rw-p 00049000 03:07 183386     /usr/lib/wine/rpcrt4.dll.so
7e7fc000-7e7fd000 rwxp 0004e000 03:07 183386     /usr/lib/wine/rpcrt4.dll.so
7e7fd000-7e7fe000 rw-p 0004f000 03:07 183386     /usr/lib/wine/rpcrt4.dll.so
7e7fe000-7e808000 r-xp 00000000 03:07 32131      /lib/libgcc_s.so.1
7e808000-7e809000 rw-p 00009000 03:07 32131      /lib/libgcc_s.so.1
7e80a000-7e80c000 rw-s 00002000 00:0d 9281       /dev/dri/card0
7e80c000-7e814000 r-xp 00000000 03:07 129500     /usr/lib/libSM.so.6.0.0
7e814000-7e815000 rw-p 00007000 03:07 129500     /usr/lib/libSM.so.6.0.0
7e815000-7e8e9000 r-xp 00000000 03:07 130193     /usr/lib/libstdc++.so.6.0.8
7e8e9000-7e8ec000 r--p 000d4000 03:07 130193     /usr/lib/libstdc++.so.6.0.8
7e8ec000-7e8ee000 rw-p 000d7000 03:07 130193     /usr/lib/libstdc++.so.6.0.8
7e8ee000-7e8f4000 rw-p 7e8ee000 00:00 0 
7e8f4000-7e910000 r-xp 00000000 03:07 183289     /usr/lib/wine/gdi32.dll.so
7e910000-7e911000 rw-p 7e910000 00:00 0 
7e911000-7e990000 r-xp 0001d000 03:07 183289     /usr/lib/wine/gdi32.dll.so
7e990000-7e993000 rw-p 0009c000 03:07 183289     /usr/lib/wine/gdi32.dll.so
7e993000-7e994000 rwxp 0009f000 03:07 183289     /usr/lib/wine/gdi32.dll.so
7e994000-7e999000 rw-p 000a0000 03:07 183289     /usr/lib/wine/gdi32.dll.so
7e999000-7e9a9000 rw-p 7e999000 00:00 0 
7e9a9000-7e9c0000 r-xp 00000000 03:07 183419     /usr/lib/wine/user32.dll.so
7e9c0000-7e9c1000 rw-p 7e9c0000 00:00 0 
7e9c1000-7ea87000 r-xp 00018000 03:07 183419     /usr/lib/wine/user32.dll.so
7ea87000-7ea8f000 rw-p 000de000 03:07 183419     /usr/lib/wine/user32.dll.so
7ea8f000-7ea90000 rwxp 000e6000 03:07 183419     /usr/lib/wine/user32.dll.so
7ea90000-7eaa6000 rw-p 000e7000 03:07 183419     /usr/lib/wine/user32.dll.so
7eaa6000-7eadf000 rw-p 7eaa6000 00:00 0 
7eadf000-7eaf0000 r-xp 00000000 03:07 183233     /usr/lib/wine/advapi32.dll.so
7eaf0000-7eaf1000 rw-p 7eaf0000 00:00 0 
7eaf1000-7eb20000 r-xp 00012000 03:07 183233     /usr/lib/wine/advapi32.dll.so
7eb20000-7eb23000 rw-p 00040000 03:07 183233     /usr/lib/wine/advapi32.dll.so
7eb23000-7eb25000 rwxp 00043000 03:07 183233     /usr/lib/wine/advapi32.dll.so
7eb25000-7eb30000 r-xp 00000000 03:07 183365     /usr/lib/wine/ole32.dll.so
7eb30000-7eb31000 rw-p 7eb30000 00:00 0 
7eb31000-7ebae000 r-xp 0000c000 03:07 183365     /usr/lib/wine/ole32.dll.so
7ebae000-7ebb1000 rw-p 00089000 03:07 183365     /usr/lib/wine/ole32.dll.so
7ebb1000-7ebb2000 rwxp 0008c000 03:07 183365     /usr/lib/wine/ole32.dll.so
7ebb2000-7ebb9000 rw-p 0008d000 03:07 183365     /usr/lib/wine/ole32.dll.so
7ebb9000-7ebd0000 r-xp 00000000 03:07 183401     /usr/lib/wine/shlwapi.dll.so
7ebd0000-7ebd1000 rw-p 7ebd0000 00:00 0 
7ebd1000-7ec0a000 r-xp 00018000 03:07 183401     /usr/lib/wine/shlwapi.dll.so
7ec0a000-7ec0d000 rw-p 00051000 03:07 183401     /usr/lib/wine/shlwapi.dll.so
7ec0d000-7ec0e000 rwxp 00054000 03:07 183401     /usr/lib/wine/shlwapi.dll.so
7ec0e000-7ec11000 rw-p 00055000 03:07 183401     /usr/lib/wine/shlwapi.dll.so
7ec11000-7ec20000 r-xp 00000000 03:07 183399     /usr/lib/wine/shell32.dll.so
7ec20000-7ec21000 rw-p 7ec20000 00:00 0 
7ec21000-7ec9b000 r-xp 00010000 03:07 183399     /usr/lib/wine/shell32.dll.so
7ec9b000-7eca0000 rw-p 00089000 03:07 183399     /usr/lib/wine/shell32.dll.so
7eca0000-7eca1000 rwxp 0008e000 03:07 183399     /usr/lib/wine/shell32.dll.so
7eca1000-7ecfb000 rw-p 0008f000 03:07 183399     /usr/lib/wine/shell32.dll.so
7ecfb000-7ed00000 r-xp 00000000 03:07 183248     /usr/lib/wine/comdlg32.dll.so
7ed00000-7ed01000 rw-p 7ed00000 00:00 0 
7ed01000-7ed3c000 r-xp 00006000 03:07 183248     /usr/lib/wine/comdlg32.dll.so
7ed3c000-7ed3e000 rwxp 00040000 03:07 183248     /usr/lib/wine/comdlg32.dll.so
7ed3e000-7ed97000 rw-p 00042000 03:07 183248     /usr/lib/wine/comdlg32.dll.so
7ed97000-7eda0000 r-xp 00000000 03:07 183494     /usr/lib/wine/winecfg.exe.so
7eda0000-7eda1000 rw-p 7eda0000 00:00 0 
7eda1000-7edbe000 r-xp 0000a000 03:07 183494     /usr/lib/wine/winecfg.exe.so
7edbe000-7edbf000 rwxp 00027000 03:07 183494     /usr/lib/wine/winecfg.exe.so
7edbf000-7edee000 rw-p 00028000 03:07 183494     /usr/lib/wine/winecfg.exe.so
7edee000-7ee21000 r--p 00000000 03:07 193388     /usr/lib/locale/en_US.utf8/LC_CTYPE
7ee21000-7ee40000 r-xp 00000000 03:07 183312     /usr/lib/wine/kernel32.dll.so
7ee40000-7ee41000 rw-p 7ee40000 00:00 0 
7ee41000-7eeca000 r-xp 00020000 03:07 183312     /usr/lib/wine/kernel32.dll.so
7eeca000-7eed2000 rw-p 000a8000 03:07 183312     /usr/lib/wine/kernel32.dll.so
7eed2000-7eed3000 rwxp 000b0000 03:07 183312     /usr/lib/wine/kernel32.dll.so
7eed3000-7ef24000 rw-p 000b1000 03:07 183312     /usr/lib/wine/kernel32.dll.so
7ef24000-7ef26000 rw-p 7ef24000 00:00 0 
7ef26000-7ef2f000 r-xp 00000000 03:07 49512      /lib/tls/i686/cmov/libnss_files-2.4.so
7ef2f000-7ef31000 rw-p 00008000 03:07 49512      /lib/tls/i686/cmov/libnss_files-2.4.so
7ef31000-7ef39000 r-xp 00000000 03:07 49514      /lib/tls/i686/cmov/libnss_nis-2.4.so
7ef39000-7ef3b000 rw-p 00007000 03:07 49514      /lib/tls/i686/cmov/libnss_nis-2.4.so
7ef3b000-7ef4d000 r-xp 00000000 03:07 49509      /lib/tls/i686/cmov/libnsl-2.4.so
7ef4d000-7ef4f000 rw-p 00011000 03:07 49509      /lib/tls/i686/cmov/libnsl-2.4.so
7ef4f000-7ef51000 rw-p 7ef4f000 00:00 0 
7ef51000-7ef58000 r-xp 00000000 03:07 49510      /lib/tls/i686/cmov/libnss_compat-2.4.so
7ef58000-7ef5a000 rw-p 00006000 03:07 49510      /lib/tls/i686/cmov/libnss_compat-2.4.so
7ef5a000-7ef7e000 r-xp 00000000 03:07 49507      /lib/tls/i686/cmov/libm-2.4.so
7ef7e000-7ef80000 rw-p 00023000 03:07 49507      /lib/tls/i686/cmov/libm-2.4.so
7ef80000-7ef90000 r-xp 00000000 03:07 183353     /usr/lib/wine/ntdll.dll.so
7ef90000-7ef91000 rw-p 7ef90000 00:00 0 
7ef91000-7eff3000 r-xp 00011000 03:07 183353     /usr/lib/wine/ntdll.dll.so
7eff3000-7effe000 rw-p 00072000 03:07 183353     /usr/lib/wine/ntdll.dll.so
7effe000-7f000000 rw-p 7effe000 00:00 0 
7f000000-7ffdc000 ---p 7f000000 00:00 0 
7ffdc000-7ffde000 rw-p 7ffdc000 00:00 0 
7ffde000-7ffdf000 ---p 7ffde000 00:00 0 
7ffdf000-7ffe0000 rw-p 7ffdf000 00:00 0 
7ffe0000-7ffff000 ---p 7ffe0000 00:00 0 
7ffff000-80000000 r-xp 7ffff000 00:00 0 
80000000-b7c80000 ---p 80000000 00:00 0 
b7c80000-b7c84000 r-xp 00000000 03:07 129519     /usr/lib/libXdmcp.so.6.0.0
b7c84000-b7c85000 rw-p 00003000 03:07 129519     /usr/lib/libXdmcp.so.6.0.0
b7c85000-b7c87000 r-xp 00000000 03:07 129510     /usr/lib/libXau.so.6.0.0
b7c87000-b7c88000 rw-p 00001000 03:07 129510     /usr/lib/libXau.so.6.0.0
b7c88000-b7c89000 rw-p b7c88000 00:00 0 
b7c89000-b7c8b000 r-xp 00000000 03:07 49506      /lib/tls/i686/cmov/libdl-2.4.so
b7c8b000-b7c8d000 rw-p 00001000 03:07 49506      /lib/tls/i686/cmov/libdl-2.4.so
b7c8d000-b7dba000 r-xp 00000000 03:07 49503      /lib/tls/i686/cmov/libc-2.4.so
b7dba000-b7dbc000 r--p 0012c000 03:07 49503      /lib/tls/i686/cmov/libc-2.4.so
b7dbc000-b7dbe000 rw-p 0012e000 03:07 49503      /lib/tls/i686/cmov/libc-2.4.so
b7dbe000-b7dc1000 rw-p b7dbe000 00:00 0 
b7dc1000-b7dd0000 r-xp 00000000 03:07 49517      /lib/tls/i686/cmov/libpthread-2.4.so
b7dd0000-b7dd2000 rw-p 0000f000 03:07 49517      /lib/tls/i686/cmov/libpthread-2.4.so
b7dd2000-b7dd4000 rw-p b7dd2000 00:00 0 
b7dd4000-b7dd8000 r-xp 00000000 03:07 129559     /usr/lib/libXxf86vm.so.1.0.0
b7dd8000-b7dd9000 rw-p 00003000 03:07 129559     /usr/lib/libXxf86vm.so.1.0.0
b7dd9000-b7de0000 r--s 00000000 03:07 144767     /usr/lib/gconv/gconv-modules.cache
b7de0000-b7edd000 r-xp 00000000 03:07 135251     /usr/lib/libwine.so.1.0
b7edd000-b7ede000 rw-p 000fd000 03:07 135251     /usr/lib/libwine.so.1.0
b7ede000-b7ef3000 rw-p b7ede000 00:00 0 
b7ef3000-b7f0c000 r-xp 00000000 03:07 32068      /lib/ld-2.4.so
b7f0c000-b7f0e000 rw-p 00018000 03:07 32068      /lib/ld-2.4.so
b7f10000-bfdb0000 ---p b7f10000 00:00 0 
bfdb8000-bfdcd000 rwxp bfdb8000 00:00 0          [stack]
bfdd0000-c0000000 ---p bfdd0000 00:00 0 
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
```

Can somebody tell me whats wrong and how to fix it? Because with it my wine - emulated games and programs got really bad sound with scretching and strange noises.

---

