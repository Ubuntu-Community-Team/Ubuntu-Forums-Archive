---
title: "open office bugs"
date: 2007-11-12
forum: General Help
---

### Post by koulanji on 2007-11-12
Ok, so I open open office to get some stuff done and whenever I try to format anything or use a menu item the program locks up and freezes. So, I do the next best thing and run the program through the terminal, and I get this 

* glibc detected *** /usr/lib/openoffice/program/soffice.bin: double free or corruption (out): 0x08917d90 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6a5cd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6a60800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb6355961]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5752d29]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11SalGraphics22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x17b)[0xb7d2fa8b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x103)[0xb7df0633]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ListBox6ResizeEv+0x18c)[0xb7e39d9c]
/usr/lib/openoffice/program/libvcl680li.so[0xb7dd6d14]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0xca)[0xb7dd94ea]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ListBoxC1EP6WindowRK5ResId+0xd6)[0xb7e38576]
/usr/lib/openoffice/program/libcui680li.so[0xad61ce98]
/usr/lib/openoffice/program/libcui680li.so[0xad61d68e]
/usr/lib/openoffice/program/libsfx680li.so[0xb3157114]
/usr/lib/openoffice/program/libsfx680li.so[0xb31572c4]
/usr/lib/openoffice/program/libsfx680li.so(_ZN12SfxTabDialog7ExecuteEv+0x37)[0xb31574a7]
/usr/lib/openoffice/program/libswui680li.so[0xad73d317]
/usr/lib/openoffice/program/libsw680li.so[0xaf46eb02]
/usr/lib/openoffice/program/libsw680li.so[0xaf4667a4]
/usr/lib/openoffice/program/libsfx680li.so[0xb3094b4a]
/usr/lib/openoffice/program/libsfx680li.so[0xb30952e8]
/usr/lib/openoffice/program/libsfx680li.so[0xb3095358]
/usr/lib/openoffice/program/libsfx680li.so[0xb30c4ce5]
/usr/lib/openoffice/program/libsfx680li.so[0xb30c4c89]
/usr/lib/openoffice/program/libvcl680li.so[0xb7deae66]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay21DispatchInternalEventEv+0xbc)[0xb533316c]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5732041]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5732081]
/usr/lib/libglib-2.0.so.0[0xb634c551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb634e11c]
/usr/lib/libglib-2.0.so.0[0xb635155f]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb6351ac5]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb5734171]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN14X11SalInstance5YieldEbb+0x37)[0xb533a927]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5YieldEb+0x59)[0xb7bea559]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application7ExecuteEv+0x3c)[0xb7bea67c]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x145d)[0x806f07d]
/usr/lib/openoffice/program/libvcl680li.so[0xb7bf034c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7bf0455]
/usr/lib/openoffice/program/soffice.bin(main+0xcf)[0x806150f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb6a09050]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window15SetPosSizePixelEllllt+0x365)[0x80613d1]
======= Memory map: ========
08048000-0809d000 r-xp 00000000 08:01 8601628    /usr/lib/openoffice/program/soffice.bin
0809d000-0809e000 rw-p 00054000 08:01 8601628    /usr/lib/openoffice/program/soffice.bin
0809e000-08a4d000 rw-p 0809e000 00:00 0          [heap]
ad200000-ad221000 rw-p ad200000 00:00 0 
ad221000-ad300000 ---p ad221000 00:00 0 
ad3f5000-ad6d7000 r-xp 00000000 08:01 8601663    /usr/lib/openoffice/program/libcui680li.so
ad6d7000-ad6ed000 rw-p 002e2000 08:01 8601663    /usr/lib/openoffice/program/libcui680li.so
ad6ed000-ad8ed000 r-xp 00000000 08:01 7307446    /usr/lib/openoffice/program/libswui680li.so
ad8ed000-ad901000 rw-p 001ff000 08:01 7307446    /usr/lib/openoffice/program/libswui680li.so
ad901000-ad9fe000 r--p 00000000 08:01 7274870    /usr/lib/openoffice/help/en/swriter.ht
ad9fe000-adb20000 r--p 00000000 08:01 7274645    /usr/lib/openoffice/help/en/swriter.db
adb20000-adb3a000 r-xp 00000000 08:01 8602176    /usr/lib/openoffice/program/svtmisc.uno.so
adb3a000-adb3c000 rw-p 0001900

Could someone please tell me what this means.....so far I have been frustrated and pissed off at the sloppiness of this new release. None of my problems are fixed, and yes I have reinstalled this dumb OS and I still have bugs. This is incredibly obnoxious

---

### Post by mlentink on 2007-11-12
Have you thoroughly checked your hardware yet?

---

### Post by koulanji on 2007-11-13
Yes, but then again why would that matter. I've been running ubuntu 6.06 on this machine. Why would my hardware all of a sudden not work in a later version?

---

### Post by FuturePilot on 2007-11-13
It's a bug in Open Office. Try changing your theme or remove the openoffice.org-gtk package. It's supposed to be fixed in 2.3.1. And this is an Open Office issue, not an Ubuntu specific issue.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526")

---

