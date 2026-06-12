---
title: "Google Earth Pro 7.3 crashes on Lubuntu 17.04"
date: 2017-07-10
forum: General Help
---

### Post by rattskjelke on 2017-07-10
I have been running Google Earth Pro v 7.1 with no problems since it was released on Lubuntu 16.04.2 LTS and 17.04.
Today Google Earth Pro got upgraded to version 7.3 and it will not run.
When I run it from a terminal window I get:
```
$ google-earth-pro
Google Earth has caught signal 11.

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

  /home/[username]/.googleearth/crashlogs/crashlog-[########].txt

Please include this file if you submit a bug report to Google.
```
The last part of the crashlog filename looks like a random hex number that changes with each crash.

Here is an actual crash log file ~/.googleearth/crashlogs/crashlog-5963cdfe.txt
```

Major Version 7
Minor Version 3
Build Number 0000
Build Date Jul  6 2017
Build Time 21:11:41
OS Type 3
OS Major Version 4
OS Minor Version 10
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1499713022
Up Time 0.025034

Stacktrace from glibc:
/opt/google/earth/pro/libgoogleearth_pro.so(+0x23b560)[0x7fac54412560]
/opt/google/earth/pro/libgoogleearth_pro.so(+0x23b8cd)[0x7fac544128cd]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x11670)[0x7fac550ea670]
/lib/x86_64-linux-gnu/libpthread.so.0(pthread_cond_signal+0xb)[0x7fac550e6b7b]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(+0xb520)[0x7fac447df520]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(+0xb665)[0x7fac447df665]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(xcb_wait_for_reply64+0x41)[0x7fac447df781]
/usr/lib/x86_64-linux-gnu/libX11.so.6(_XReply+0x128)[0x7fac52073a78]
/usr/lib/x86_64-linux-gnu/libX11.so.6(XOpenDisplay+0xb1b)[0x7fac5206407b]
/opt/google/earth/pro/libQt5XcbQpa.so.5(_ZN14QXcbConnectionC1EP19QXcbNativeInterfacebjPKc+0x159)[0x7fac4b43fc89]
/opt/google/earth/pro/libQt5XcbQpa.so.5(_ZN15QXcbIntegrationC1ERK11QStringListRiPPc+0x32b)[0x7fac4b4474eb]
/opt/google/earth/pro/plugins/platforms/libqxcb.so(+0x162e)[0x7fac3dedd62e]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN27QPlatformIntegrationFactory6createERK7QStringRK11QStringListRiPPcS2_+0x1f8)[0x7fac538ab0e8]
/opt/google/earth/pro/libQt5Gui.so.5(+0x11a757)[0x7fac538bf757]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN22QGuiApplicationPrivate25createPlatformIntegrationEv+0x5ad)[0x7fac538c0c6d]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN22QGuiApplicationPrivate21createEventDispatcherEv+0x30)[0x7fac538c2880]
/opt/google/earth/pro/libQt5Core.so.5(_ZN16QCoreApplication4initEv+0x432)[0x7fac51091002]
/opt/google/earth/pro/libQt5Core.so.5(_ZN16QCoreApplicationC2ER23QCoreApplicationPrivate+0x25)[0x7fac51091255]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN15QGuiApplicationC2ER22QGuiApplicationPrivate+0xd)[0x7fac538c264d]
/opt/google/earth/pro/libQt5Widgets.so.5(_ZN12QApplicationC2ERiPPci+0x52)[0x7fac52fef7a2]
/opt/google/earth/pro/libgoogleearth_pro.so(_ZN19QtSingleApplicationC1ERiPPc+0xe)[0x7fac5441369e]
/opt/google/earth/pro/libgoogleearth_pro.so(_ZN5earth6client11ApplicationC1ERiPPc+0x69)[0x7fac544a3119]
/opt/google/earth/pro/libgoogleearth_pro.so(+0x23b16a)[0x7fac5441216a]
/opt/google/earth/pro/libgoogleearth_pro.so(earthmain+0x4cd)[0x7fac54412dcd]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf1)[0x7fac54a293f1]
./googleearth-bin[0x400819]

```

Once I got this in the terminal window:
```

$ /opt/google/earth/pro/google-earth-pro
*** Error in `./googleearth-bin': free(): invalid pointer: 0x000000000157dfc8 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7908b)[0x7fb70087408b]
/lib/x86_64-linux-gnu/libc.so.6(+0x82c3a)[0x7fb70087dc3a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7fb700881d2c]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(+0xbefd)[0x7fb6f05d1efd]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(+0x9ed1)[0x7fb6f05cfed1]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(+0xb617)[0x7fb6f05d1617]
/usr/lib/x86_64-linux-gnu/libxcb.so.1(xcb_wait_for_reply64+0x41)[0x7fb6f05d1781]
/usr/lib/x86_64-linux-gnu/libX11.so.6(_XReply+0x128)[0x7fb6fde65a78]
/usr/lib/x86_64-linux-gnu/libX11.so.6(XOpenDisplay+0xb1b)[0x7fb6fde5607b]
/opt/google/earth/pro/libQt5XcbQpa.so.5(_ZN14QXcbConnectionC1EP19QXcbNativeInterfacebjPKc+0x159)[0x7fb6f7231c89]
/opt/google/earth/pro/libQt5XcbQpa.so.5(_ZN15QXcbIntegrationC1ERK11QStringListRiPPc+0x32b)[0x7fb6f72394eb]
/opt/google/earth/pro/plugins/platforms/libqxcb.so(+0x162e)[0x7fb6e9ccf62e]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN27QPlatformIntegrationFactory6createERK7QStringRK11QStringListRiPPcS2_+0x1f8)[0x7fb6ff69d0e8]
/opt/google/earth/pro/libQt5Gui.so.5(+0x11a757)[0x7fb6ff6b1757]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN22QGuiApplicationPrivate25createPlatformIntegrationEv+0x5ad)[0x7fb6ff6b2c6d]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN22QGuiApplicationPrivate21createEventDispatcherEv+0x30)[0x7fb6ff6b4880]
/opt/google/earth/pro/libQt5Core.so.5(_ZN16QCoreApplication4initEv+0x432)[0x7fb6fce83002]
/opt/google/earth/pro/libQt5Core.so.5(_ZN16QCoreApplicationC2ER23QCoreApplicationPrivate+0x25)[0x7fb6fce83255]
/opt/google/earth/pro/libQt5Gui.so.5(_ZN15QGuiApplicationC2ER22QGuiApplicationPrivate+0xd)[0x7fb6ff6b464d]
/opt/google/earth/pro/libQt5Widgets.so.5(_ZN12QApplicationC2ERiPPci+0x52)[0x7fb6fede17a2]
/opt/google/earth/pro/libgoogleearth_pro.so(_ZN19QtSingleApplicationC1ERiPPc+0xe)[0x7fb70020569e]
/opt/google/earth/pro/libgoogleearth_pro.so(_ZN5earth6client11ApplicationC1ERiPPc+0x69)[0x7fb700295119]
/opt/google/earth/pro/libgoogleearth_pro.so(+0x23b16a)[0x7fb70020416a]
/opt/google/earth/pro/libgoogleearth_pro.so(earthmain+0x4cd)[0x7fb700204dcd]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf1)[0x7fb70081b3f1]
./googleearth-bin[0x400819]
======= Memory map: ========
00400000-00401000 r-xp 00000000 08:05 1052771                            /opt/google/earth/pro/googleearth-bin
00600000-00601000 r--p 00000000 08:05 1052771                            /opt/google/earth/pro/googleearth-bin
00601000-00602000 rw-p 00001000 08:05 1052771                            /opt/google/earth/pro/googleearth-bin
014f5000-015ac000 rw-p 00000000 00:00 0                                  [heap]
7fb6e4000000-7fb6e4021000 rw-p 00000000 00:00 0 
7fb6e4021000-7fb6e8000000 ---p 00000000 00:00 0 
7fb6e9cce000-7fb6e9cd0000 r-xp 00000000 08:05 1052754                    /opt/google/earth/pro/plugins/platforms/libqxcb.so
7fb6e9cd0000-7fb6e9ecf000 ---p 00002000 08:05 1052754                    /opt/google/earth/pro/plugins/platforms/libqxcb.so
7fb6e9ecf000-7fb6e9ed0000 r--p 00001000 08:05 1052754                    /opt/google/earth/pro/plugins/platforms/libqxcb.so
7fb6e9ed0000-7fb6e9ed1000 rw-p 00002000 08:05 1052754                    /opt/google/earth/pro/plugins/platforms/libqxcb.so
7fb6e9ed1000-7fb6ea1ac000 r--p 00000000 08:05 656737                     /usr/lib/locale/locale-archive
7fb6ea1ac000-7fb6ea1c3000 r-xp 00000000 08:05 1052743                    /opt/google/earth/pro/libwebbrowser.so
7fb6ea1c3000-7fb6ea3c2000 ---p 00017000 08:05 1052743                    /opt/google/earth/pro/libwebbrowser.so
7fb6ea3c2000-7fb6ea3c4000 r--p 00016000 08:05 1052743                    /opt/google/earth/pro/libwebbrowser.so
7fb6ea3c4000-7fb6ea3c5000 rw-p 00018000 08:05 1052743                    /opt/google/earth/pro/libwebbrowser.so
7fb6ea3c5000-7fb6ea3fd000 r-xp 00000000 08:05 1052733                    /opt/google/earth/pro/libwmsbase.so
7fb6ea3fd000-7fb6ea5fd000 ---p 00038000 08:05 1052733                    /opt/google/earth/pro/libwmsbase.so
7fb6ea5fd000-7fb6ea601000 r--p 00038000 08:05 1052733                    /opt/google/earth/pro/libwmsbase.so
7fb6ea601000-7fb6ea602000 rw-p 0003c000 08:05 1052733                    /opt/google/earth/pro/libwmsbase.so
7fb6ea602000-7fb6ea674000 r-xp 00000000 08:05 925153                     /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fb6ea674000-7fb6ea873000 ---p 00072000 08:05 925153                     /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fb6ea873000-7fb6ea874000 r--p 00071000 08:05 925153                     /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fb6ea874000-7fb6ea875000 rw-p 00072000 08:05 925153                     /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fb6ea875000-7fb6ea87a000 r-xp 00000000 08:05 664648                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fb6ea87a000-7fb6eaa79000 ---p 00005000 08:05 664648                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fb6eaa79000-7fb6eaa7a000 r--p 00004000 08:05 664648                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fb6eaa7a000-7fb6eaa7b000 rw-p 00005000 08:05 664648                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7fb6eaa7b000-7fb6eaa7d000 r-xp 00000000 08:05 664637                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fb6eaa7d000-7fb6eac7d000 ---p 00002000 08:05 664637                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fb6eac7d000-7fb6eac7e000 r--p 00002000 08:05 664637                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fb6eac7e000-7fb6eac7f000 rw-p 00003000 08:05 664637                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7fb6eac7f000-7fb6eadb8000 r-xp 00000000 08:05 1052850                    /opt/google/earth/pro/libIGSg.so
7fb6eadb8000-7fb6eafb8000 ---p 00139000 08:05 1052850                    /opt/google/earth/pro/libIGSg.so
7fb6eafb8000-7fb6eafca000 r--p 00139000 08:05 1052850                    /opt/google/earth/pro/libIGSg.so
7fb6eafca000-7fb6eafd4000 rw-p 0014b000 08:05 1052850                    /opt/google/earth/pro/libIGSg.so
7fb6eafd4000-7fb6eafd7000 rw-p 00000000 00:00 0 
7fb6eafd7000-7fb6eb57e000 r-xp 00000000 08:05 1053012                    /opt/google/earth/pro/libIGGfx.so
7fb6eb57e000-7fb6eb77e000 ---p 005a7000 08:05 1053012                    /opt/google/earth/pro/libIGGfx.so
7fb6eb77e000-7fb6eb79d000 r--p 005a7000 08:05 1053012                    /opt/google/earth/pro/libIGGfx.so
7fb6eb79d000-7fb6eb8fb000 rw-p 005c6000 08:05 1053012                    /opt/google/earth/pro/libIGGfx.so
7fb6eb8fb000-7fb6eb8ff000 rw-p 00000000 00:00 0 
7fb6eb8ff000-7fb6eb9a2000 r-xp 00000000 08:05 1052769                    /opt/google/earth/pro/libIGAttrs.so
7fb6eb9a2000-7fb6ebba1000 ---p 000a3000 08:05 1052769                    /opt/google/earth/pro/libIGAttrs.so
7fb6ebba1000-7fb6ebbad000 r--p 000a2000 08:05 1052769                    /opt/google/earth/pro/libIGAttrs.so
7fb6ebbad000-7fb6ebbb2000 rw-p 000ae000 08:05 1052769                    /opt/google/earth/pro/libIGAttrs.so
7fb6ebbb2000-7fb6ebbb3000 rw-p 00000000 00:00 0 
7fb6ebbb3000-7fb6ebd2f000 r-xp 00000000 08:05 1052844                    /opt/google/earth/pro/liblayer.so
7fb6ebd2f000-7fb6ebf2e000 ---p 0017c000 08:05 1052844                    /opt/google/earth/pro/liblayer.so
7fb6ebf2e000-7fb6ebf38000 r--p 0017b000 08:05 1052844                    /opt/google/earth/pro/liblayer.so
7fb6ebf38000-7fb6ebf3c000 rw-p 00185000 08:05 1052844                    /opt/google/earth/pro/liblayer.so
7fb6ebf3c000-7fb6ebf3d000 rw-p 00000000 00:00 0 
7fb6ebf3d000-7fb6ebf68000 r-xp 00000000 08:05 1052940                    /opt/google/earth/pro/libfilmstrip.so
7fb6ebf68000-7fb6ec168000 ---p 0002b000 08:05 1052940                    /opt/google/earth/pro/libfilmstrip.so
7fb6ec168000-7fb6ec169000 r--p 0002b000 08:05 1052940                    /opt/google/earth/pro/libfilmstrip.so
7fb6ec169000-7fb6ec16a000 rw-p 0002c000 08:05 1052940                    /opt/google/earth/pro/libfilmstrip.so
7fb6ec16a000-7fb6ec16d000 r-xp 00000000 08:05 1052738                    /opt/google/earth/pro/libfusioncommon.so
7fb6ec16d000-7fb6ec36d000 ---p 00003000 08:05 1052738                    /opt/google/earth/pro/libfusioncommon.so
7fb6ec36d000-7fb6ec36e000 r--p 00003000 08:05 1052738                    /opt/google/earth/pro/libfusioncommon.so
7fb6ec36e000-7fb6ec36f000 rw-p 00004000 08:05 1052738                    /opt/google/earth/pro/libfusioncommon.so
7fb6ec36f000-7fb6ec3c9000 r-xp 00000000 08:05 1052998                    /opt/google/earth/pro/libIGMath.so
7fb6ec3c9000-7fb6ec5c9000 ---p 0005a000 08:05 1052998                    /opt/google/earth/pro/libIGMath.so
7fb6ec5c9000-7fb6ec5d0000 r--p 0005a000 08:05 1052998                    /opt/google/earth/pro/libIGMath.so
7fb6ec5d0000-7fb6ec5d1000 rw-p 00061000 08:05 1052998                    /opt/google/earth/pro/libIGMath.so
7fb6ec5d1000-7fb6ec5d2000 rw-p 00000000 00:00 0 
7fb6ec5d2000-7fb6ec6e3000 r-xp 00000000 08:05 925075                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.5200.0
7fb6ec6e3000-7fb6ec8e3000 ---p 00111000 08:05 925075                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.5200.0
7fb6ec8e3000-7fb6ec8e4000 r--p 00111000 08:05 925075                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.5200.0
7fb6ec8e4000-7fb6ec8e5000 rw-p 00112000 08:05 925075                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.5200.0
7fb6ec8e5000-7fb6ec8e6000 rw-p 00000000 00:00 0 
7fb6ec8e6000-7fb6ec8e7000 r-xp 00000000 08:05 665162                     /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.5200.0
7fb6ec8e7000-7fb6ecae6000 ---p 00001000 08:05 665162                     /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.5200.0
7fb6ecae6000-7fb6ecae7000 r--p 00000000 08:05 665162                     /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.5200.0
7fb6ecae7000-7fb6ecae8000 rw-p 00001000 08:05 665162                     /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0.5200.0
7fb6ecae8000-7fb6ee312000 r--p 00000000 08:05 1053029                    /opt/google/earth/pro/libicudata.so.54
7fb6ee312000-7fb6ee511000 ---p 0182a000 08:05 1053029                    /opt/google/earth/pro/libicudata.so.54
7fb6ee511000-7fb6ee512000 r--p 01829000 08:05 1053029                    /opt/google/earth/pro/libicudata.so.54
7fb6ee512000-7fb6ee6a6000 r-xp 00000000 08:05 1052730                    /opt/google/earth/pro/libicuuc.so.54
7fb6ee6a6000-7fb6ee8a6000 ---p 00194000 08:05 1052730                    /opt/google/earth/pro/libicuuc.so.54
7fb6ee8a6000-7fb6ee8b6000 r--p 00194000 08:05 1052730                    /opt/google/earth/pro/libicuuc.so.54
7fb6ee8b6000-7fb6ee8b7000 rw-p 001a4000 08:05 1052730                    /opt/google/earth/pro/libicuuc.so.54
7fb6ee8b7000-7fb6ee8bb000 rw-p 00000000 00:00 0 
7fb6ee8bb000-7fb6eeb37000 r-xp 00000000 08:05 1052939                    /opt/google/earth/pro/libicui18n.so.54
7fb6eeb37000-7fb6eed36000 ---p 0027c000 08:05 1052939                    /opt/google/earth/pro/libicui18n.so.54
7fb6eed36000-7fb6eed45000 r--p 0027b000 08:05 1052939                    /opt/google/earth/pro/libicui18n.so.54
7fb6eed45000-7fb6eed47000 rw-p 0028a000 08:05 1052939                    /opt/google/earth/pro/libicui18n.so.54
7fb6eed47000-7fb6eed56000 r-xp 00000000 08:05 664880                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7fb6eed56000-7fb6eef56000 ---p 0000f000 08:05 664880                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7fb6eef56000-7fb6eef57000 r--p 0000f000 08:05 664880                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7fb6eef57000-7fb6eef58000 rw-p 00010000 08:05 664880                     /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
7fb6eef58000-7fb6eef5d000 r-xp 00000000 08:05 664686                     /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fb6eef5d000-7fb6ef15c000 ---p 00005000 08:05 664686                     /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fb6ef15c000-7fb6ef15d000 r--p 00004000 08:05 664686                     /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fb6ef15d000-7fb6ef15e000 rw-p 00005000 08:05 664686                     /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1.0.0
7fb6ef15e000-7fb6ef162000 r-xp 00000000 08:05 665797                     /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7fb6ef162000-7fb6ef361000 ---p 00004000 08:05 665797                     /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7fb6ef361000-7fb6ef362000 r--p 00003000 08:05 665797                     /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7fb6ef362000-7fb6ef363000 rw-p 00004000 08:05 665797                     /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0.0.0
7fb6ef363000-7fb6ef37a000 r-xp 00000000 08:05 665801                     /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7fb6ef37a000-7fb6ef579000 ---p 00017000 08:05 665801                     /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7fb6ef579000-7fb6ef57b000 r--p 00016000 08:05 665801                     /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7fb6ef57b000-7fb6ef57c000 rw-p 00018000 08:05 665801                     /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0.0.0
7fb6ef57c000-7fb6ef57d000 r-xp 00000000 08:05 664631                     /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7fb6ef57d000-7fb6ef77c000 ---p 00001000 08:05 664631                     /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7fb6ef77c000-7fb6ef77d000 r--p 00000000 08:05 664631                     /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7fb6ef77d000-7fb6ef77e000 rw-p 00001000 08:05 664631                     /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1.0.0
7fb6ef77e000-7fb6ef783000 r-xp 00000000 08:05 664652                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fb6ef783000-7fb6ef982000 ---p 00005000 08:05 664652                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fb6ef982000-7fb6ef983000 r--p 00004000 08:05 664652                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fb6ef983000-7fb6ef984000 rw-p 00005000 08:05 664652                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fb6ef984000-7fb6ef986000 r-xp 00000000 08:05 664646                     /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7fb6ef986000-7fb6efb85000 ---p 00002000 08:05 664646                     /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7fb6efb85000-7fb6efb86000 r--p 00001000 08:05 664646                     /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7fb6efb86000-7fb6efb87000 rw-p 00002000 08:05 664646                     /usr/lib/x86_64-linux-gnu/libXdamage.so.1.1.0
7fb6efb87000-7fb6efbb1000 r-xp 00000000 08:05 665069                     /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7fb6efbb1000-7fb6efdb0000 ---p 0002a000 08:05 665069                     /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7fb6efdb0000-7fb6efdb4000 r--p 00029000 08:05 665069                     /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7fb6efdb4000-7fb6efdb5000 rw-p 0002d000 08:05 665069                     /usr/lib/x86_64-linux-gnu/libglapi.so.0.0.0
7fb6efdb5000-7fb6efdb6000 rw-p 00000000 00:00 0 
7fb6efdb6000-7fb6efdb7000 r-xp 00000000 08:05 665841                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7fb6efdb7000-7fb6effb7000 ---p 00001000 08:05 665841                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7fb6effb7000-7fb6effb8000 r--p 00001000 08:05 665841                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7fb6effb8000-7fb6effb9000 rw-p 00002000 08:05 665841                     /usr/lib/x86_64-linux-gnu/libxshmfence.so.1.0.0
7fb6effb9000-7fb6effbe000 r-xp 00000000 08:05 665813                     /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7fb6effbe000-7fb6f01be000 ---p 00005000 08:05 665813                     /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7fb6f01be000-7fb6f01bf000 r--p 00005000 08:05 665813                     /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7fb6f01bf000-7fb6f01c0000 rw-p 00006000 08:05 665813                     /usr/lib/x86_64-linux-gnu/libxcb-sync.so.1.0.0
7fb6f01c0000-7fb6f01c2000 r-xp 00000000 08:05 665803                     /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7fb6f01c2000-7fb6f03c1000 ---p 00002000 08:05 665803                     /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7fb6f03c1000-7fb6f03c2000 r--p 00001000 08:05 665803                     /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7fb6f03c2000-7fb6f03c3000 rw-p 00002000 08:05 665803                     /usr/lib/x86_64-linux-gnu/libxcb-present.so.0.0.0
7fb6f03c3000-7fb6f03c5000 r-xp 00000000 08:05 665799                     /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7fb6f03c5000-7fb6f05c4000 ---p 00002000 08:05 665799                     /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7fb6f05c4000-7fb6f05c5000 r--p 00001000 08:05 665799                     /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7fb6f05c5000-7fb6f05c6000 rw-p 00002000 08:05 665799                     /usr/lib/x86_64-linux-gnu/libxcb-dri3.so.0.0.0
7fb6f05c6000-7fb6f05e7000 r-xp 00000000 08:05 665819                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fb6f05e7000-7fb6f07e6000 ---p 00021000 08:05 665819                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fb6f07e6000-7fb6f07e7000 r--p 00020000 08:05 665819                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fb6f07e7000-7fb6f07e8000 rw-p 00021000 08:05 665819                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7fb6f07e8000-7fb6f0818000 r-xp 00000000 08:05 665501                     /usr/lib/x86_64-linux-gnu/libpng16.so.16.28.0
7fb6f0818000-7fb6f0a18000 ---p 00030000 08:05 665501                     /usr/lib/x86_64-linux-gnu/libpng16.so.16.28.0
7fb6f0a18000-7fb6f0a19000 r--p 00030000 08:05 665501                     /usr/lib/x86_64-linux-gnu/libpng16.so.16.28.0
7fb6f0a19000-7fb6f0a1a000 rw-p 00031000 08:05 665501                     /usr/lib/x86_64-linux-gnu/libpng16.so.16.28.0
7fb6f0a1a000-7fb6f0a40000 r-xp 00000000 08:05 1053008                    /opt/google/earth/pro/libexpat.so.1
7fb6f0a40000-7fb6f0c40000 ---p 00026000 08:05 1053008                    /opt/google/earth/pro/libexpat.so.1
7fb6f0c40000-7fb6f0c42000 r--p 00026000 08:05 1053008                    /opt/google/earth/pro/libexpat.so.1
7fb6f0c42000-7fb6f0c43000 rw-p 00028000 08:05 1053008                    /opt/google/earth/pro/libexpat.so.1
7fb6f0c43000-7fb6f0c5e000 r-xp 00000000 08:05 925208                     /lib/x86_64-linux-gnu/libz.so.1.2.11
7fb6f0c5e000-7fb6f0e5d000 ---p 0001b000 08:05 925208                     /lib/x86_64-linux-gnu/libz.so.1.2.11
7fb6f0e5d000-7fb6f0e5e000 r--p 0001a000 08:05 925208                     /lib/x86_64-linux-gnu/libz.so.1.2.11
7fb6f0e5e000-7fb6f0e5f000 rw-p 0001b000 08:05 925208                     /lib/x86_64-linux-gnu/libz.so.1.2.11
7fb6f0e5f000-7fb6f0ee5000 r-xp 00000000 08:05 1052941                    /opt/google/earth/pro/libswscale.so.4
7fb6f0ee5000-7fb6f10e5000 ---p 00086000 08:05 1052941                    /opt/google/earth/pro/libswscale.so.4
7fb6f10e5000-7fb6f10e6000 r--p 00086000 08:05 1052941                    /opt/google/earth/pro/libswscale.so.4
7fb6f10e6000-7fb6f10e7000 rw-p 00087000 08:05 1052941                    /opt/google/earth/pro/libswscale.so.4
7fb6f10e7000-7fb6f10ef000 rw-p 00000000 00:00 0 
7fb6f10ef000-7fb6f110a000 r-xp 00000000 08:05 1052991                    /opt/google/earth/pro/libswresample.so.2
7fb6f110a000-7fb6f1309000 ---p 0001b000 08:05 1052991                    /opt/google/earth/pro/libswresample.so.2
7fb6f1309000-7fb6f130b000 r--p 0001a000 08:05 1052991                    /opt/google/earth/pro/libswresample.so.2
7fb6f130b000-7fb6f130c000 rw-p 0001c000 08:05 1052991                    /opt/google/earth/pro/libswresample.so.2
7fb6f130c000-7fb6f135d000 r-xp 00000000 08:05 1052721                    /opt/google/earth/pro/libavutil.so.55
7fb6f135d000-7fb6f155c000 ---p 00051000 08:05 1052721                    /opt/google/earth/pro/libavutil.so.55
7fb6f155c000-7fb6f156d000 r--p 00050000 08:05 1052721                    /opt/google/earth/pro/libavutil.so.55
7fb6f156d000-7fb6f156e000 rw-p 00061000 08:05 1052721                    /opt/google/earth/pro/libavutil.so.55
7fb6f156e000-7fb6f1582000 rw-p 00000000 00:00 0 
7fb6f1582000-7fb6f171e000 r-xp 00000000 08:05 1052929                    /opt/google/earth/pro/libavformat.so.57
7fb6f171e000-7fb6f191d000 ---p 0019c000 08:05 1052929                    /opt/google/earth/pro/libavformat.so.57
7fb6f191d000-7fb6f192f000 r--p 0019b000 08:05 1052929                    /opt/google/earth/pro/libavformat.so.57
7fb6f192f000-7fb6f1945000 rw-p 001ad000 08:05 1052929                    /opt/google/earth/pro/libavformat.so.57
7fb6f1945000-7fb6f1f34000 r-xp 00000000 08:05 1052725                    /opt/google/earth/pro/libavcodec.so.57
7fb6f1f34000-7fb6f2133000 ---p 005ef000 08:05 1052725                    /opt/google/earth/pro/libavcodec.so.57
7fb6f2133000-7fb6f214e000 r--p 005ee000 08:05 1052725                    /opt/google/earth/pro/libavcodec.so.57
7fb6f214e000-7fb6f2159000 rw-p 00609000 08:05 1052725                    /opt/google/earth/pro/libavcodec.so.57
7fb6f2159000-7fb6f2575000 rw-p 00000000 00:00 0 
7fb6f2575000-7fb6f26e3000 r-xp 00000000 08:05 1052996                    /opt/google/earth/pro/libxsltransform.so
7fb6f26e3000-7fb6f28e3000 ---p 0016e000 08:05 1052996                    /opt/google/earth/pro/libxsltransform.so
7fb6f28e3000-7fb6f28eb000 r--p 0016e000 08:05 1052996                    /opt/google/earth/pro/libxsltransform.so
7fb6f28eb000-7fb6f28ef000 rw-p 00176000 08:05 1052996                    /opt/google/earth/pro/libxsltransform.so
7fb6f28ef000-7fb6f28f0000 rw-p 00000000 00:00 0 
7fb6f28f0000-7fb6f2ae9000 r-xp 00000000 08:05 1052942                    /opt/google/earth/pro/libspatial.so
7fb6f2ae9000-7fb6f2ce9000 ---p 001f9000 08:05 1052942                    /opt/google/earth/pro/libspatial.so
7fb6f2ce9000-7fb6f2cec000 r--p 001f9000 08:05 1052942                    /opt/google/earth/pro/libspatial.so
7fb6f2cec000-7fb6f2cf1000 rw-p 001fc000 08:05 1052942                    /opt/google/earth/pro/libspatial.so
7fb6f2cf1000-7fb6f2cf2000 rw-p 00000000 00:00 0 
7fb6f2cf2000-7fb6f2e84000 r-xp 00000000 08:05 1052739                    /opt/google/earth/pro/libsgutil.so
7fb6f2e84000-7fb6f3083000 ---p 00192000 08:05 1052739                    /opt/google/earth/pro/libsgutil.so
7fb6f3083000-7fb6f3087000 r--p 00191000 08:05 1052739                    /opt/google/earth/pro/libsgutil.so
7fb6f3087000-7fb6f308a000 rw-p 00195000 08:05 1052739                    /opt/google/earth/pro/libsgutil.so
7fb6f308a000-7fb6f308d000 rw-p 00000000 00:00 0 
7fb6f308d000-7fb6f309a000 r-xp 00000000 08:05 1052716                    /opt/google/earth/pro/libreporting.so
7fb6f309a000-7fb6f329a000 ---p 0000d000 08:05 1052716                    /opt/google/earth/pro/libreporting.soGoogle Earth has caught signal 6.

```
I tried uninstalling and reinstalling.
I tried uninstalling, apt-get autoremove --purge, deleted the google config folders and reinstalling.
I tried dpkg --configure -a and apt-get install -f. I don't think there are missing dependencies.
I thought maybe Google's repo had some problem so I downloaded both the 32 and 64 bit .deb packages. They install with no errors but will not run.
Are there other system logs I should look at?
Anybody know how to fix this?

---

### Post by monkeybrain20122 on 2017-07-10
I just made a web app out of google-earth web [https://www.google.com/earth/](https://www.google.com/earth/)
No installation, doesn't take up much space, fast (just a standalone instance of Chrome), no config to mess with, never crashes.


Edited: installed it in 16.04 to check it out. It didn't crash, but didn't work either, tried some search, nothing happened, the main window was transparent so I saw Firefox which was behind it. Looked like it was running in wine. Removed it, the web version is much better.

---

### Post by rattskjelke on 2017-07-10
> **monkeybrain20122 said:**
> I just made a web app out of google-earth web 
I have no idea what a web app is or how to make one.

The Google Earth for Chrome app on their web site won't run on Firefox so I installed chromium-browser. It won't run on that either.
I uninstalled chromium-browser and installed Google Chrome from the .deb file but it won't run on the linux version.

---

### Post by monkeybrain20122 on 2017-07-10
> **rattskjelke said:**
> I have no idea what a web app is or how to make one.

The Google Earth for Chrome app on their web site won't run on Firefox so I installed chromium-browser. It won't run on that either.
I uninstalled chromium-browser and installed Google Chrome from the .deb file but it won't run on the linux version.


It runs perfectly on Chrome here. 

To make a web app, open Chrome or Chromium. Go to [google-earth]("https://www.google.com/earth/") Click the three dots on the right upper corner to see the Chrome menu, choose More Tools > Add to Desktop. Check "Open as Window"
 then you will get a launcher on  your desktop and ~/.local/share/applications it will show up in your menu or dash.

---

### Post by rattskjelke on 2017-07-11
> **monkeybrain20122 said:**
> It runs perfectly on Chrome here. 

To make a web app, open Chrome or Chromium. Go to [google-earth]("https://www.google.com/earth/") Click the three dots on the right upper corner to see the Chrome menu, choose More Tools > Add to Desktop. Check "Open as Window"
 then you will get a launcher on  your desktop and ~/.local/share/applications it will show up in your menu or dash.

I installed chromium again and tried made the desktop web app. It still doesn't work. When you try to open Google Earth in chromium or click the Launch Google Earth button it says:
*Aw snap! The new Google Earth isn't supported by your browser yet. Try this link in Chrome instead. If you don't have Chrome installed, download it here.*

---

### Post by monkeybrain20122 on 2017-07-11
> **rattskjelke said:**
> I installed chromium again and tried made the desktop web app. It still doesn't work. When you try to open Google Earth in chromium or click the Launch Google Earth button it says:
*Aw snap! The new Google Earth isn't supported by your browser yet. Try this link in Chrome instead. If you don't have Chrome installed, download it here.*

Then install Chrome. Many people are confused, Chromium is NOT Chrome, but a crippled, poorly maintained beta/alpha. Get Chrome for Linux from its [site]("https://www.google.com/chrome/browser/desktop/index.html"). I see no point for Chromium, it is neither here nor there, either Firefox for full open source or Chrome (I use both)

---

### Post by rattskjelke on 2017-07-11
> **monkeybrain20122 said:**
> Then install Chrome. 
I did that yesterday and it didn't work.
Instead of getting the browser not supported message it says:
*Loading in progress. 0 of 4.543 billion years processed.*
Then nothing else happens.

---

### Post by oldos2er on 2017-07-11
That's what it does for me too, after which I see a slowly spinning globe; the program is waiting for input. Is this what you're seeing?

---

### Post by monkeybrain20122 on 2017-07-11
> **rattskjelke said:**
> I did that yesterday and it didn't work.
Instead of getting the browser not supported message it says:
*Loading in progress. 0 of 4.543 billion years processed.*
Then nothing else happens.

That is normal. wait a bit for it to load. Then you will see the spinning globe, it is good to go. The menu is on the side bar.

---

### Post by rattskjelke on 2017-07-11
> **monkeybrain20122 said:**
> That is normal. wait a bit for it to load.
How long? I left it for about 15 minutes once and it never finished loading. Never saw anything more than your first screen shot.
I don't know if this is a Google problem or my Lubuntu installation is corrupted or something.

---

### Post by monkeybrain20122 on 2017-07-11
> **rattskjelke said:**
> How long? I left it for about 15 minutes once and it never finished loading. Never saw anything more than your first screen shot.
I don't know if this is a Google problem or my Lubuntu installation is corrupted or something.


Strange. It took me about 3 secs. 

Let's try a few things. First, start with a new profile, close chrome. Go to ~/.config and rename the folder google-chrome to something else, like google-chrome-bk. Now start chrome and go to the google-earth site to see if it loads (to restore the old profile, close chrome, go to ~/.config, remove the folder google-chrome and rename  google-chrome-bk back to googole-chrome)

If still doesn't work, start chrome with the command 

```
google-chrome
```

Then navigate to google-earth's webpage and try to load it to see if there is any error message.

---

### Post by rattskjelke on 2017-07-12
I installed chrome and chromium several times (but not both installed at the same time) and each time I deleted the cache and configuration folders. They both appear to work normally on other web sites but not Google Earth Web.

Over on Google's product support forums other people are also experiencing Google Earth 7.3 not working on Ubuntu and Fedora and  posted the same type crash logs I got. Maybe Google will eventually fix it.

---

### Post by vasa1 on 2017-07-12
> **rattskjelke said:**
> ...
Over on Google's product support forums other people are also experiencing Google Earth 7.3 not working on Ubuntu and Fedrora and  posted the same type crash logs I got. Maybe Google will eventually fix it.
These Ubuntu users, were they on 17.04 or 16.04 or something else? monkeybrain's webapp route works for me on Ubuntu 16.04.

---

### Post by monkeybrain20122 on 2017-07-12
> **rattskjelke said:**
> I installed chrome and chromium several times (but not both installed at the same time) and each time I deleted the cache and configuration folders. They both appear to work normally on other web sites but not Google Earth Web.

Over on Google's product support forums other people are also experiencing Google Earth 7.3 not working on Ubuntu and Fedrora and  posted the same type crash logs I got. Maybe Google will eventually fix it.

Google earth pro doesn't work (17.04 crashes, 16.04 clicks no response) but Google earth (not pro) desktop does work in 17.04 and 16.04 and Fedora 25 (haven't installed it in Fedora 26) . Web app works both in 17.04 and 16.04 (haven't checked fedora, but my bet is it works too). Did you run chrome from the terminal and check the error message?

---

### Post by rattskjelke on 2017-07-12
> **monkeybrain20122 said:**
> Did you run chrome from the terminal and check the error message?
Not yesterday. I installed it again and get this:
```
$ google-chrome
[16275:16308:0712/123128.472850:ERROR:service_manager.cc(158)] Connection InterfaceProviderSpec prevented service: content_browser from binding interface: content::mojom::Child exposed by: nacl_loader
[1,1099280448:17:31:28.480039] Native Client module will be loaded at base address 0x000000e600000000
[16275:16308:0712/123140.725973:ERROR:service_manager.cc(158)] Connection InterfaceProviderSpec prevented service: content_browser from binding interface: content::mojom::Child exposed by: nacl_loader
[1,1099280448:17:31:40.731780] Native Client module will be loaded at base address 0x00005cc100000000
[16275:16308:0712/123140.945890:ERROR:service_manager.cc(158)] Connection InterfaceProviderSpec prevented service: content_browser from binding interface: content::mojom::Child exposed by: nacl_loader
[1,1099280448:17:31:40.955784] Native Client module will be loaded at base address 0x0000580500000000
[0712/173141.849480:WARNING:ipc_message_attachment_set.cc(49)] MessageAttachmentSet destroyed with unconsumed attachments: 0/1

** Signal 11 from untrusted code: pc=580500000000
[16275:16308:0712/123141.880095:ERROR:nacl_process_host.cc(259)] NaCl process exited with status 62720 (0xf500)
```

---

### Post by monkeybrain20122 on 2017-07-12
I have no idea why the signal 11 panic. Hope that someone more knowledgeable will come along.

Just a wild guess, it  might have something to do with the graphic driver Try

```
glxinfo | grep OpenGL
```

and post the output


Also open Chrome and type in the url
```
chrome://gpu
```

and post the output.

---

### Post by rattskjelke on 2017-07-12
$ glxinfo | grep OpenGL```

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD SUMO2 (DRM 2.49.0 / 4.10.0-26-generic, LLVM 4.0.0)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 17.0.3
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.0.3
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```
chrome://gpu
```
Graphics Feature Status
Canvas: Software only, hardware acceleration unavailable
Flash: Software only, hardware acceleration unavailable
Flash Stage3D: Software only, hardware acceleration unavailable
Flash Stage3D Baseline profile: Software only, hardware acceleration unavailable
Compositing: Software only, hardware acceleration unavailable
Multiple Raster Threads: Disabled
Native GpuMemoryBuffers: Software only. Hardware acceleration disabled
Rasterization: Software only, hardware acceleration unavailable
Video Decode: Software only, hardware acceleration unavailable
Video Encode: Software only, hardware acceleration unavailable
WebGL: Hardware accelerated but at reduced performance
WebGL2: Unavailable
Driver Bug Workarounds
adjust_src_dst_region_for_blitframebuffer
clear_uniforms_before_first_program_use
decode_encode_srgb_for_generatemipmap
disable_framebuffer_cmaa
dont_remove_invariant_for_fragment_input
force_cube_map_positive_x_allocation
init_texture_max_anisotropy
regenerate_struct_names
remove_invariant_and_centroid_for_essl3
scalarize_vec_and_mat_constructor_args
disable_software_to_accelerated_canvas_upgrade
Problems Detected
ATI/AMD cards with older drivers in Linux are crash-prone: 71381, 76428, 73910, 101225, 136240, 357314
Disabled Features: flash_stage3d, gpu_compositing, panel_fitting, flash3d, gpu_rasterization, accelerated_2d_canvas, accelerated_video_decode, webgl2, accelerated_webgl, flash_stage3d_baseline, accelerated_video_encode
Accelerated video decode is unavailable on Linux: 137247
Disabled Features: accelerated_video_decode
Accelerated video encode is unavailable on Linux
Disabled Features: accelerated_video_encode
Clear uniforms before first program use on all platforms: 124764, 349137
Applied Workarounds: clear_uniforms_before_first_program_use
Linux AMD drivers incorrectly return initial value of 1 for TEXTURE_MAX_ANISOTROPY: 348237
Applied Workarounds: init_texture_max_anisotropy
Always rewrite vec/mat constructors to be consistent: 398694
Applied Workarounds: scalarize_vec_and_mat_constructor_args
Linux AMD drivers handle struct scopes incorrectly: 403957
Applied Workarounds: regenerate_struct_names
Linux ATI drivers crash on binding incomplete cube map texture to FBO: 518889
Applied Workarounds: force_cube_map_positive_x_allocation
Limited enabling of Chromium GL_INTEL_framebuffer_CMAA: 535198
Applied Workarounds: disable_framebuffer_cmaa
adjust src/dst region if blitting pixels outside read framebuffer on Linux AMD: 664740
Applied Workarounds: adjust_src_dst_region_for_blitframebuffer
AMD drivers in Linux require invariant qualifier to match between vertex and fragment shaders: 659326, 639760
Applied Workarounds: remove_invariant_and_centroid_for_essl3, dont_remove_invariant_for_fragment_input
Disable KHR_blend_equation_advanced until cc shaders are updated: 661715
Decode and Encode before generateMipmap for srgb format textures on Linux AMD: 634519
Applied Workarounds: decode_encode_srgb_for_generatemipmap
Software to Accelerated canvas update breaks Linux AMD: 710029
Applied Workarounds: disable_software_to_accelerated_canvas_upgrade
Raster is using a single thread.
Disabled Features: multiple_raster_threads
Native GpuMemoryBuffers have been disabled, either via about:flags or command line.
Disabled Features: native_gpu_memory_buffers
Version Information
Data exported	7/12/2017, 2:43:07 PM
Chrome version	Chrome/59.0.3071.115
Operating system	Linux 4.10.0-26-generic
Software rendering list version	13.8
Driver bug list version	10.102
ANGLE commit id	a9042d3c1952
2D graphics backend	Skia/59 ef6f9c65527412ec4057ea0551f2e051beb94d32
Command Line Args	--flag-switches-begin --flag-switches-end
Driver Information
Initialization time	0
In-process GPU	true
Passthrough Command Decoder	false
Supports overlays	false
Sandboxed	false
GPU0	VENDOR = 0x1002, DEVICE= 0x9649
Optimus	false
Optimus	false
AMD switchable	false
Driver vendor	Google Inc.
Driver version	3.3.0.2
Driver date	2017/04/07
Pixel shader version	3.0
Vertex shader version	3.0
Max. MSAA samples	4
Machine model name	
Machine model version	
GL_VENDOR	Google Inc.
GL_RENDERER	Google SwiftShader
GL_VERSION	OpenGL ES 2.0 SwiftShader
GL_EXTENSIONS	
Disabled Extensions	GL_KHR_blend_equation_advanced GL_KHR_blend_equation_advanced_coherent
Window system binding vendor	
Window system binding version	
Window system binding extensions	
Window manager	Openbox
XDG_CURRENT_DESKTOP	LXDE
GDMSESSION	Lubuntu
Compositing manager	No
Direct rendering	Yes
Reset notification strategy	0x0000
GPU process crash count	0
System visual ID	0
RGBA visual ID	0
Compositor Information
Tile Update Mode	One-copy
Partial Raster	Enabled
GpuMemoryBuffers Status
ATC	Software only
ATCIA	Software only
DXT1	Software only
DXT5	Software only
ETC1	Software only
R_8	Software only
RG_88	Software only
BGR_565	Software only
RGBA_4444	Software only
RGBX_8888	Software only
RGBA_8888	Software only
BGRX_8888	Software only
BGRA_8888	Software only
RGBA_F16	Software only
YVU_420	Software only
YUV_420_BIPLANAR	Software only
UYVY_422	Software only
```

---

### Post by monkeybrain20122 on 2017-07-12
I don't know if it is because webgl2 is unavailable in your Chrome. Try this, go to the url
chorme://flags

find WebGL2.0 change it to enable, then restart Chrome. Check chrome://gpu again and go to google-earth again and see does it make a difference.


**Edited:** You may also need override software software rendering list -> enable

---

### Post by rattskjelke on 2017-07-12
WebGL 2.0 was set to Default. I enabled it and it didn't work.
Enabling software rendering list made it work but generates a stream of errors or warnings in the terminal window.
I set WebGL 2.0 back to Default and Disabled and it still works as long as software rendering list is enabled. Still get a lot of errors.
If I go to Settings and disable hardware acceleration then it doesn't work.

This is a 5 year old low end HP laptop with a AMD A4 processor and Radeon 6480 GPU that doesn't support most hardware acceleration. 

The Google Earth web app really sucks bad compared to the Google Earth Pro desktop app. I guess I'll just have to wait until they fix it.

---

### Post by rattskjelke on 2017-07-13
I saw this today on the Google Maps & Earth Help Forum. It's a hack to fix the Google Earth Pro 7.3 linux desktop app.
https://productforums.google.com/forum/#!topic/maps/bXKFMLRQxQs;context-place=topicsearchin/maps/category$3A(google-earth)$20is$3Afirstpost%7Csort:date
I tried the replacement file posted there (after scanning it with ClamAV) and it seems to work. At least it doesn't crash on startup.

There is still no official fix from Google.

---

### Post by mc4man on 2017-07-13
GE pro 7.3 works fine here with Ubuntu 16.04 (Haswell, Intel iGPU

Google Earth Pro
7.3.0.3827 (64-bit)

Whether it matters??
```
$  glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.0.0
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 17.0.0
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.0.0
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
OpenGL ES profile extensions:

```

---

### Post by rattskjelke on 2017-07-17
Today I noticed that Google pulled version 7.3 from the download page and repo.
Now the current Linux version reverted back to 7.1.8.3036.

---

### Post by rattskjelke on 2017-07-18
Today Google released Google Earth Pro version 7.3.0.3830.
They fixed whatever was causing it to crash.

---

