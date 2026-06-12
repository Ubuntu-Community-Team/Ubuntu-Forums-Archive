---
title: "Thunderbird freeze"
date: 2007-06-02
forum: General Help
---

### Post by DougieFresh4U on 2007-06-02
On my Feisty machine, when ever I open Thunderbird and it loads the mail, it freezes. then when I click to close, I get the "wait or force window". I click force close and re-open Thunderbird and all is ok.  It only freezes when loading new mail on start up. Once the mail is loaded and I force quit and re-open, the new mail is there that was previously loaded. 
Any one else have the same issue?

---

### Post by kellemes on 2007-06-02
Run thunderbird from terminal, messages will tell you some more about the problem.

---

### Post by simpsonatwork on 2007-08-02
I have exactly the same problem. Here's the log from Terminal:
```
*** glibc detected *** /opt/thunderbird/thunderbird-bin: free(): invalid pointer: 0x099106a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73787cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb737be30]
/usr/lib/libfontconfig.so.1[0xb754b6c0]
/usr/lib/libfontconfig.so.1(FcPatternDestroy+0x71)[0xb754b901]
/opt/thunderbird/thunderbird-bin[0x8267468]
/opt/thunderbird/thunderbird-bin[0x826789a]
/opt/thunderbird/thunderbird-bin[0x8264460]
/opt/thunderbird/thunderbird-bin[0x826454a]
/opt/thunderbird/thunderbird-bin[0x8ad17d9]
/opt/thunderbird/thunderbird-bin[0x8ad11ef]
/opt/thunderbird/thunderbird-bin[0x82c899a]
/opt/thunderbird/thunderbird-bin[0x86104c4]
/opt/thunderbird/thunderbird-bin[0x86dda70]
/opt/thunderbird/thunderbird-bin[0x86e4bf6]
/opt/thunderbird/thunderbird-bin[0x86dc034]
/opt/thunderbird/thunderbird-bin[0x8501ebe]
/opt/thunderbird/libxpcom_core.so(PL_HandleEvent+0x27)[0xb7eb66a7]
/opt/thunderbird/libxpcom_core.so(PL_ProcessPendingEvents+0x84)[0xb7eb65d4]
/opt/thunderbird/libxpcom_core.so[0xb7eb825d]
/opt/thunderbird/thunderbird-bin[0x829b1c5]
/usr/lib/libglib-2.0.so.0[0xb78ee40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb78c4df2]
/usr/lib/libglib-2.0.so.0[0xb78c7dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb78c8179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7bb1044]
/opt/thunderbird/thunderbird-bin[0x829b508]
/opt/thunderbird/thunderbird-bin[0x8740567]
/opt/thunderbird/thunderbird-bin[0x807faed]
/opt/thunderbird/thunderbird-bin(g_type_class_ref+0x13c)[0x807b444]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7326ebc]
/opt/thunderbird/thunderbird-bin(gtk_widget_grab_focus+0x39)[0x807b371]
======= Memory map: ========
08048000-08d04000 r-xp 00000000 08:03 1474902    /opt/thunderbird/thunderbird-bin
08d04000-08d1e000 rwxp 00cbb000 08:03 1474902    /opt/thunderbird/thunderbird-bin
08d1e000-0993a000 rwxp 08d1e000 00:00 0          [heap]
b253e000-b253f000 ---p b253e000 00:00 0 
b253f000-b2d3f000 rwxp b253f000 00:00 0 
b2d3f000-b2db7000 r-xp 00000000 08:03 3867149    /home/certainlyakey/.fonts/SEGOEUIB.TTF
b2db7000-b2e34000 r-xp 00000000 08:03 3867150    /home/certainlyakey/.fonts/SEGOEUI.TTF
b2e34000-b2e35000 ---p b2e34000 00:00 0 
b2e35000-b3635000 rwxp b2e35000 00:00 0 
b3635000-b3639000 r-xp 00000000 08:03 3523857    /lib/tls/i686/cmov/libnss_dns-2.5.so
b3639000-b363b000 rwxp 00003000 08:03 3523857    /lib/tls/i686/cmov/libnss_dns-2.5.so
b363b000-b363d000 r-xp 00000000 08:03 3489881    /lib/libnss_mdns4_minimal.so.2
b363d000-b363e000 rwxp 00001000 08:03 3489881    /lib/libnss_mdns4_minimal.so.2
b3649000-b364a000 ---p b3649000 00:00 0 
b364a000-b3e4a000 rwxp b364a000 00:00 0 
b3e4a000-b3e4e000 r-xp 00000000 08:03 2359409    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b3e4e000-b3e4f000 rwxp 00003000 08:03 2359409    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b3e4f000-b3e53000 r-xp 00000000 08:03 1474729    /opt/thunderbird/components/libmozgnome.so
b3e53000-b3e54000 rwxp 00003000 08:03 1474729    /opt/thunderbird/components/libmozgnome.so
b3e54000-b3e90000 r-xp 00000000 08:03 1474839    /opt/thunderbird/libnssckbi.so
b3e90000-b3e9a000 rwxp 0003b000 08:03 1474839    /opt/thunderbird/libnssckbi.so
b3e9a000-b3ed6000 r-xp 00000000 08:03 1474834    /opt/thunderbird/libfreebl3.so
b3ed6000-b3ed7000 rwxp 0003c000 08:03 1474834    /opt/thunderbird/libfreebl3.so
b3ed7000-b3ed8000 ---p b3ed7000 00:00 0 
b3ed8000-b46d8000 rwxp b3ed8000 00:00 0 
b46d8000-b46d9000 ---p b46d8000 00:00 0 
b46d9000-b4eda000 rwxp b46d9000 00:00 0 
b4eda000-b4f3a000 rwxs 00000000 00:08 16941115   /SYSV00000000 (deleted)
b4f3a000-b4fb0000 r-xp 00000000 08:03 2508587    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4fb0000-b4fb2000 r-xp 00000000 08:03 2425496    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4fb2000-b4fb3000 rwxp 00001000 08:03 2425496    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4fb3000-b5030000 r-xp 00000000 08:03 2508591    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5030000-b50ad000


```

update: i managed to find out that this was caused by a theme, ["Tango Icons"]("https://addons.mozilla.org/en-US/thunderbird/addon/2258"). It somehow prevented the notifications from working and thus TB freezed or crashed. After changing the theme - no problems.
update 2: it seems that a lot of themes force TB on Ubuntu FF to crash due to the same notifications related problems. At least, it happens again with another one - "[Cylence]("https://addons.mozilla.org/en-US/thunderbird/addon/3954")". So it's maybe time to report to Launchpad about it. Has someone ever had such crashes, except me? Desktop Effects are running, but there were no other similar updates installed (like Beryl or Compiz Fusion).

---

