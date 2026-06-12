---
title: "Epiphany crashes a lot"
date: 2007-10-25
forum: General Help
---

### Post by Rotarychainsaw on 2007-10-25
Hey all,
I have gutsy on both of my computers. On the desktop, epiphany runs fine and almost never crashes. On my laptop, epiphany crashes at least once an hour. I can't figure out why this is happening. I have the newest flash (r64) on both machines, I have the same themes and compix settings, and everything is all updated. Anyone have any ideas?

---

### Post by Rotarychainsaw on 2007-10-25
hmm, seems to be replicatable by letting the browser sit on this post for 5 minutes not doing anything. Heres what the terminal says. 

```
*** glibc detected *** epiphany-browser: double free or corruption (fasttop): 0x0872e478 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6eecd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6ef0800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb700e961]
/usr/lib/libgnomevfs-2.so.0[0xb7b07bd7]
/usr/lib/libavahi-client.so.3(avahi_service_resolver_event+0x5a4)[0xb6c1a764]
/usr/lib/libavahi-client.so.3[0xb6c14e8e]
/usr/lib/libdbus-1.so.3(dbus_connection_dispatch+0x382)[0xb7db7c22]
/usr/lib/libavahi-client.so.3[0xb6c1c0ec]
/usr/lib/libavahi-glib.so.1[0xb6c2c3e9]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb700711c]
/usr/lib/libglib-2.0.so.0[0xb700a55f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb700a909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb77bc9e4]
epiphany-browser(main+0x880)[0x807b970]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb6e99050]
epiphany-browser[0x807ae01]
======= Memory map: ========
08048000-08159000 r-xp 00000000 08:01 1376287    /usr/bin/epiphany
08159000-08164000 rw-p 00110000 08:01 1376287    /usr/bin/epiphany
08164000-098c1000 rw-p 08164000 00:00 0          [heap]
ad2df000-ad36a000 r--p 00000000 08:01 1654825    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
ad36a000-ad657000 r--p 00000000 08:01 1608539    /usr/share/fonts/truetype/baekmuk/dotum.ttf
ad657000-ad658000 ---p ad657000 00:00 0 
ad658000-ade58000 rwxp ad658000 00:00 0 
ade91000-adec8000 r--p 00000000 08:01 2556003    /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
adec8000-adefb000 r--p 00000000 08:01 2556001    /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
adf1a000-adf47000 r-xp 00000000 08:01 2016672    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_nscp.so
adf47000-adf4d000 rw-p 0002d000 08:01 2016672    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjavaplugin_nscp.so
adf4d000-ae22d000 rw-p adf4d000 00:00 0 
ae22d000-aef4d000 ---p ae22d000 00:00 0 
aef4d000-af6c1000 r-xp 00000000 08:01 6176914    /usr/lib/flashplugin-nonfree/libflashplayer.so
af6c1000-af705000 rw-p 00773000 08:01 6176914    /usr/lib/flashplugin-nonfree/libflashplayer.so
af705000-af7dc000 rw-p af705000 00:00 0 
b0ff8000-b100e000 r-xp 00000000 08:01 2441217    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
b100e000-b1012000 rw-p 00015000 08:01 2441217    /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so
b1012000-b1025000 r-xp 00000000 08:01 49161      /usr/lib/totem/libtotem-narrowspace-plugin.so
b1025000-b1026000 rw-p 00012000 08:01 49161      /usr/lib/totem/libtotem-narrowspace-plugin.so
b1026000-b1033000 r-xp 00000000 08:01 49160      /usr/lib/totem/libtotem-mully-plugin.so
b1033000-b1034000 rw-p 0000d000 08:01 49160      /usr/lib/totem/libtotem-mully-plugin.so
b1034000-b1049000 r-xp 00000000 08:01 49159      /usr/lib/totem/libtotem-gmp-plugin.so
b1049000-b104a000 rw-p 00015000 08:01 49159      /usr/lib/totem/libtotem-gmp-plugin.so
b104a000-b106d000 r--p 00000000 08:01 2556020    /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
b1081000-b10a0000 r--p 00000000 08:01 2555986    /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
b10a0000-b1100000 rw-s 00000000 00:09 1409039    /SYSV00000000 (deleted)
b1100000-b1341000 rw-p b1100000 00:00 0 
b1341000-b13f6000 r-xp 00000000 08:01 1376858    /usr/lib/libaspell.so.15.1.4
b13f6000-b13fa000 rw-p 000b4000 08:01 1376858    /usr/lib/libaspell.so.15.1.4
b13fa000-b13fe000 rw-p b13fa000 00:00 0 
b13fe000-b13ff000 ---p b13fe000 00:00 0 
b13ff000-b1bff000 rwxp b13ff000 00:00 0 
b1bff000-b1c00000 ---p b1bff000 00:00 0 
b1c00000-b2400000 rwxp b1c00000 00:00 0 
b2400000-b24f5000 rw-p b2400000 00:00 0 
b24f5000-b2500000 ---p b24f5000 00:00 0 
b2502000-b2504000 r-xp 00000000 08:01 1525378    /usr/lib/pango/1.6.0/modules/pango-hangul-fc.so
b2504000-b2505000 rw-p 00001000 08:01 1525378    /usr/lib/pango/1.6.0/modules/pango-hangul-fc.so
b2505000-b250a000 r-xp 00000000 08:01 5963779    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b250a000-b250b000 rw-p 00004000 08:01 5963779    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
b250b000-b2518000 r-xp 00000000 08:01 49158      /usr/lib/totem/libtotem-basic-plugin.so
b2518000-b2519000 rw-p 0000d000 08:01 49158      /usr/lib/totem/libtotem-basic-plugin.so
b2519000-b251b000 r-xp 00000000 08:01 1376754    /usr/lib/firefox/plugins/libunixprintplugin.so
b251b000-b251c000 rw-p 00001000 08:01 1376754    /usr/lib/firefox/plugins/libunixprintplugin.so
b251c000-b2562000 r--p 00000000 08:01 2556002    /usr/share/fonts/truetype/msttcorefon


```

---

### Post by Rotarychainsaw on 2007-10-26
hmmm, I updated the theme I was using (aurora) and it seems to be more stable now. This must be the same thing in a GTK theme that is taking down Open Office GTK. Weird.

---

### Post by Crafty Kisses on 2007-10-26
> **Rotarychainsaw said:**
> Hey all,
I have gutsy on both of my computers. On the desktop, epiphany runs fine and almost never crashes. On my laptop, epiphany crashes at least once an hour. I can't figure out why this is happening. I have the newest flash (r64) on both machines, I have the same themes and compix settings, and everything is all updated. Anyone have any ideas?

RAM issue?

---

### Post by ssadhale on 2008-03-28
Well same experience here. I am on Dell Inspiron laptop. Core 2 Duo Processor and 2GB RAM (so I dont think its a RAM problem). Epiphany feels a lot faster than Firefox - only when it works! It kept crashing on me every now and then. Especially it seems to have an allergy of YouTube. But I could notice similar crashes on other sites. Not sure if they all were making use of flash. It could be a flash plugin problem. But cant say that for sure. Sadly I had to uninstall it and switch to Firefox again.

---

