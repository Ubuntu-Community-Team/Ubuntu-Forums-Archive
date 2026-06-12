---
title: "OpenOffice Drawing - broken, dead window"
date: 2008-04-25
forum: General Help
---

### Post by BkkBonanza on 2008-04-25
Have installed OpenOffice Suite. Word, Spreadsheet work fine, have been using.
Drawing app was added to my graphics menu but every time I try to use I just get a full screen dead window - it can be un-maximized but has no content and never re-paints itself.
I tried re-installation with Synaptic and after that running it caused a recovery screen for untitled doc upon start up. Recover or no recover ends with dead window again.

Anyone have any idea why this app appears to be dead after a simple default install from Synaptic? Are others seeing this too?
Thanks.

Edit: Tried oodraw from terminal - got this long list of messages, if this helps...

 *** glibc detected *** /usr/lib/openoffice/program/soffice.bin: free(): invalid pointer: 0x08783990 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6abbd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6abf800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb63a1961]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57c3d29]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11SalGraphics22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueR16SalControlHandleRKN3rtl8OUStringERS0_SC_PK12OutputDevice+0x17b)[0xb7d87a8b]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window22GetNativeControlRegionEmmRK6RegionmRK16ImplControlValueN3rtl8OUStringERS0_S8_+0x103)[0xb7e48633]
/usr/lib/openoffice/program/libvcl680li.so(_ZN7ListBox6ResizeEv+0x18c)[0xb7e91d9c]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e2ed14]
/usr/lib/openoffice/program/libvcl680li.so(_ZN6Window4ShowEht+0xca)[0xb7e314ea]
/usr/lib/openoffice/program/libsvx680li.so[0xb126d656]
/usr/lib/openoffice/program/libsvx680li.so(_ZN26SvxLineStyleToolBoxControl16CreateItemWindowEP6Window+0x51)[0xb12777d1]
/usr/lib/openoffice/program/libsfx680li.so(_ZN17SfxToolBoxControl16createItemWindowERKN3com3sun4star3uno9ReferenceINS2_3awt7XWindowEEE+0x47)[0xb3148237]
/usr/lib/openoffice/program/libfwk680li.so[0xb2ad0349]
/usr/lib/openoffice/program/libfwk680li.so[0xb2ad8172]
/usr/lib/openoffice/program/libfwk680li.so[0xb2ac71a4]
/usr/lib/openoffice/program/libfwk680li.so[0xb2ac27d3]
/usr/lib/openoffice/program/libfwk680li.so[0xb2a227ff]
/usr/lib/openoffice/program/libfwk680li.so[0xb29c9416]
/usr/lib/openoffice/program/libfwk680li.so[0xb29e4356]
/usr/lib/openoffice/program/libfwk680li.so[0xb29e2f8b]
/usr/lib/openoffice/program/libsd680li.so[0xb19702f6]
/usr/lib/openoffice/program/libsd680li.so[0xb19706b0]
/usr/lib/openoffice/program/libsd680li.so[0xb19706e8]
/usr/lib/openoffice/program/libvcl680li.so[0xb7e42e66]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN10SalDisplay21DispatchInternalEventEv+0xbc)[0xb53ab16c]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57a3041]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57a3081]
/usr/lib/libglib-2.0.so.0[0xb6398551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb639a11c]
/usr/lib/libglib-2.0.so.0[0xb639d55f]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb639dac5]
/usr/lib/openoffice/program/libvclplug_gtk680li.so[0xb57a5171]
/usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN14X11SalInstance5YieldEbb+0x37)[0xb53b2927]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application5YieldEb+0x59)[0xb7c42559]
/usr/lib/openoffice/program/libvcl680li.so(_ZN11Application7ExecuteEv+0x3c)[0xb7c4267c]
/usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop4MainEv+0x145d)[0x806f07d]
/usr/lib/openoffice/program/libvcl680li.so[0xb7c4834c]
/usr/lib/openoffice/program/libvcl680li.so(_Z6SVMainv+0x35)[0xb7c48455]
/usr/lib/openoffice/program/soffice.bin(main+0xcf)[0x806150f]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb6a68050]
/usr/lib/openoffice/program/soffice.bin(_ZN6Window15SetPosSizePixelEllllt+0x365)[0x80613d1]
======= Memory map: ========
08048000-0809d000 r-xp 00000000 08:02 1558887    /usr/lib/openoffice/program/soffice.bin
0809d000-0809e000 rw-p 00054000 08:02 1558887    /usr/lib/openoffice/program/soffice.bin
0809e000-08880000 rw-p 0809e000 00:00 0          [heap]
af300000-af321000 rw-p af300000 00:00 0 
af321000-af400000 ---p af321000 00:00 0 
af41a000-af41b000 ---p af41a000 00:00 0 
af41b000-afc1b000 rw-p af41b000 00:00 0 
afc1b000-afc96000 r-xp 00000000 08:02 1558830    /usr/lib/openoffice/program/libxstor.so
afc96000-afc99000 rw-p 0007b000 08:02 1558830    /usr/lib/openoffice/program/libxstor.so
afc99000-afcb9000 r-xp 00000000 08:02 1558597    /usr/lib/openoffice/program/fsstorage.uno.so
afcb9000-afcbb000 rw-p 0001f000 08:02 1558597    /usr/lib/openoffice/program/fsstorage.uno.so
afcbb000-afcd5000 r--s 00000000 08:02 1723454    /usr/share/fonts/type1/gsfonts/n019003l.pfb
afcd5000-afcf3000 r-xp 00000000 08:02 1558862    /usr/lib/openoffice/program/reflection.uno.so
afcf3000-afcf5000 rw-p 0001e000 08:02 1558862    /usr/lib/openoffice/program/reflection.uno.so
afcf5000-afd14000 r-xp 00000000 08:02 1558608    /usr/lib/openoffice/program/introspection.uno.so
afd14000-afd15000 rw-p 0001f000 08:02 1558608    /usr/lib/openoffice/program/introspection.uno.so
afd15000-afe76000 r-xp 00000000 08:02 1558650    /usr/lib/openoffice/program/libdbtools680li.so
afe76000-afe80000 rw-p 00160000 08:02 1558650    /usr/lib/openoffice/program/libdbtools680li.so
afe80000-b010d000 r-xp 00000000 08:02 1558679    /usr/lib/openoffice/program/libfrm680li.so
b010d000-b012d000 rw-p 0028d000 08:02 1558679    /usr/lib/openoffice/program/libfrm680li.so
b012d000-b012f000 rw-p b012d000 00:00 0 
b012f000-b014c000 r-xp 00000000 08:02 1558752    /usr/lib/openoffice/program/libscn680li.so
b014c000-b014e000 rw-p 0001c000 08:02 1558752    /usr/lib/openoffice/program/libscn680li.so
b014e000-b01d2000 r--s 00000000 08:02 1723369    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b01d2000-b01f0000 r-xp 00000000 08:02 1558718    /usr/lib/openoffice/program/liblocaledata_en.so
b01f0000-b01f5000 rw-p 0001e000 08:02 1558718    /usr/lib/openoffice/program/liblocaledata_en.so
b01f5000-b020a000 r-xp 00000000 08:02 1558915    /usr/lib/openoffice/program/vbaevents680li.uno.so
b020a000-b020b000 rw-p 00015000 08:02 1558915    /usr/lib/openoffice/program/vbaevents680li.uno.so
b020b000-b022e000 r--s 00000000 08:02 1723478    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b022e000-b0376000 r-xp 00000000 08:02 1492512    /usr/lib/libicui18n.so.36.0
b0376000-b037c000 rw-p 00147000 08:02 1492512    /usr/lib/libicui18n.so.36.0
b037c000-b0388000 r-xp 00000000 08:02 1558671    /usr/lib/openoffice/program/libevtatt.so
b0388000-b0389000 rw-p 0000c000 08:02 1558671    /usr/lib/openoffice/program/libevtatt.so
b0389000-b04dc000 r-xp 00000000 08:02 1558604    /usr/lib/openoffice/program/i18npool.uno.so
b04dc000-b04ec000 rw-p 00152000 08:02 1558604    /usr/lib/openoffice/program/i18npool.uno.so
b04ec000-b04ee000 rw-p b04ec000 00:00 0 
b04ee000-b04fd000 r-xp 00000000 08:02 1558693    /usr/lib/openoffice/program/libi18nutilgcc3.so
b04fd000-b04fe000 rw-p 0000f000 08:02 1558693    /usr/lib/openoffice/program/libi18nutilgcc3.so
b04fe000-b04ff000 rw-p b04fe000 00:00 0 
b04ff000-b058a000 r-xp 00000000 08:02 1558716    /usr/lib/openoffice/program/liblng680li.so
b058a000-b0590000 rw-p 0008a000 08:02 1558716    /usr/lib/openoffice/program/liblng680li.so
b0590000-b09ba000 r-xp 00000000 08:02 1558824    /usr/lib/openoffice/program/libxo680li.so
b09ba000-b09e2000 rw-p 00429000 08:02 1558824    /usr/lib/openoffice/program/libxo680li.so
b09e2000-b09e3000 rw-p b09e2000 00:00 0 
b09e3000-b0a07000 r-x

---

### Post by BkkBonanza on 2008-04-25
Really? Nobody seen this.
That message says "invalid pointer..."
Do I take it this should be reported as a bug then?
Chris :(

---

