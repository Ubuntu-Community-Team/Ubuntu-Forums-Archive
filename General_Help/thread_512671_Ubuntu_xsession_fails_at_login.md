---
title: "Ubuntu xsession fails at login"
date: 2007-07-29
forum: General Help
---

### Post by phil.rhinehart on 2007-07-29
When I login to ubuntu (Feisty) I get the error "Your session only lasted less that 10 seconds..."
Once I press ok I am logged out.
I am not sure what is causing the problem. [IMG]http://img243.imageshack.us/img243/7246/screenshot1fv3.png[/IMG]

Here is the xsession-error file:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "phil"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/phil-laptop:/tmp/.ICE-unix/5728
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Initializing gnome-mount extension
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x08260a60 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76476fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb764860e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb775e2c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7af3db0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7af51e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7af8f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7af91c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7af927f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7dae440]
x-session-manager[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb77573c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7756df2]
/usr/lib/libglib-2.0.so.0[0xb7759dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb775a179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c8e044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75f4ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:04 1124324    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:04 1124324    /usr/bin/gnome-session
08069000-08284000 rw-p 08069000 00:00 0          [heap]
b5a00000-b5a21000 rw-p b5a00000 00:00 0 
b5a21000-b5b00000 ---p b5a21000 00:00 0 
b5b3d000-b5b48000 r-xp 00000000 08:04 830752     /lib/libgcc_s.so.1
b5b48000-b5b49000 rw-p 0000a000 08:04 830752     /lib/libgcc_s.so.1
b5b5c000-b5b5d000 ---p b5b5c000 00:00 0 
b5b5d000-b635d000 rw-p b5b5d000 00:00 0 
b635d000-b63da000 r--p 00000000 08:04 1338874    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b63da000-b63dc000 r-xp 00000000 08:04 1205695    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b63dc000-b63dd000 rw-p 00001000 08:04 1205695    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b63dd000-b63e3000 r--s 00000000 08:04 358430     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b63e3000-b63e4000 r--s 00000000 08:04 363109     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b63e4000-b63e7000 r--s 00000000 08:04 363108     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b63e7000-b63e8000 r--s 00000000 08:04 363107     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b63e8000-b63e9000 r--s 00000000 08:04 363106     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b63e9000-b63ed000 r--s 00000000 08:04 358427     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b63ed000-b63ee000 r--s 00000000 08:04 363104     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b63ee000-b63f0000 r--s 00000000 08:04 363072     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b63f0000-b63f2000 r--s 00000000 08:04 363071     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b63f2000-b63f3000 r--s 00000000 08:04 363066     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b63f3000-b63f5000 r--s 00000000 08:04 363065     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b63f5000-b63fb000 r--s 00000000 08:04 363062     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b63fb000-b63fd000 r--s 00000000 08:04 363061     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b63fd000-b63ff000 r--s 00000000 08:04 363058     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b63ff000-b6407000 r--s 00000000 08:04 363056     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6407000-b640d000 r--s 00000000 08:04 363054     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b640d000-b640e000 r--s 00000000 08:04 363051     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b640e000-b6410000 r--s 00000000 08:04 363018     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6410000-b6416000 r--s 00000000 08:04 363017     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6416000-b6419000 r--s 00000000 08:04 363016     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6419000-b641d000 r--s 00000000 08:04 358412     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b641d000-b6424000 r--s 00000000 08:04 360573     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6424000-b6425000 r--s 00000000 08:04 363525     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6425000-b6426000 r--s 00000000 08:04 363497     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6426000-b6427000 r--s 00000000 08:04 363496     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6427000-b6428000 r--s 00000000 08:04 363492     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6428000-b6429000 r--s 00000000 08:04 363485     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6429000-b642c000 r--s 00000000 08:04 363484     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b642c000-b6431000 r--s 00000000 08:04 363483     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6431000-b6433000 r--s 00000000 08:04 363456     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6433000-b6434000 r--s 00000000 08:04 363455     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6434000-b6436000 r--s 00000000 08:04 363448     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6436000-b6437000 r--s 00000000 08:04 363438     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6437000-b643c000 r--s 00000000 08:04 363437     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b643c000-b6440000 r--s 00000000 08:04 363436     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6440000-b6442000 r--s 00000000 08:04 363435     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6442000-b6445000 r--s 00000000 08:04 363434     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6445000-b6446000 r--s 00000000 08:04 363404     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6446000-b6448000 r--s 00000000 08:04 363403     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6448000-b644c000 r--s 00000000 08:04 363402     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b644c000-b6452000 r--s 00000000 08:04 363401     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6452000-b645a000 r--s 00000000 08:04 363299     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b645a000-b6647000 r--p 00000000 08:04 1434004    /usr/share/icons/hicolor/icon-theme.cache
b6647000-b6cee000 r--p 00000000 08:04 1438283    /usr/share/icons/gnome/icon-theme.cache
b6cee000-b6cf5000 r-xp 00000000 08:04 1189103    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6cf5000-b6cf6000 rw-p 00007000 08:04 1189103    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6cf6000-b6d56000 rw-s 00000000 00:08 819203     /SYSV00000000 (deleted)
b6d56000-b6dc3000 rw-p b6d56000 00:00 0 
b6dc3000-b6dca000 r-xp 00000000 08:04 1125346    /usr/lib/libfam.so.0.0.0
b6dca000-b6dcb000 rw-p 00006000 08:04 1125346    /usr/lib/libfam.so.0.0.0
b6dcb000-b6dd1000 r-xp 00000000 08:04 830715     /lib/libacl.so.1.1.0
b6dd1000-b6dd2000 rw-p 00005000 08:04 830715     /lib/libacl.so.1.1.0
b6dd2000-b6dd5000 r-xp 00000000 08:04 830719     /lib/libattr.so.1.1.0
b6dd5000-b6dd6000 rw-p 00002000 08:04 830719     /lib/libattr.so.1.1.0
b6dd7000-b6dd8000 r--s 00000000 08:04 363300     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6dd8000-b6dda000 r--s 00000000 08:04 363298     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6dda000-b6ddd000 r--s 00000000 08:04 363297     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6ddd000-b6de4000 r--s 00000000 08:04 360379     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6de4000-b6de8000 r-xp 00000000 08:04 1189129    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6de8000-b6de9000 rw-p 00003000 08:04 1189129    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6de9000-b6df5000 r-xp 00000000 08:04 1189052    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6df5000-b6df6000 rw-p 0000b000 08:04 1189052    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6df6000-b6df7000 r-xp 00000000 08:04 782006     /usr/lib/gconv/ISO8859-1.so
b6df7000-b6df9000 rw-p 00000000 08:04 782006     /usr/lib/gconv/ISO8859-1.so
b6df9000-b6e34000 r--p 00000000 08:04 1190101    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e34000-b6f0b000 r--p 00000000 08:04 1190100    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f0b000-b6f14000 r-xp 00000000 08:04 864436     /lib/tls/i686/cmov/libnss_files-2.5.so
b6f14000-b6f16000 rw-p 00008000 08:04 864436     /lib/tls/i686/cmov/libnss_files-2.5.so
b6f16000-b6f1e000 r-xp 00000000 08:04 864440     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f1e000-b6f20000 rw-p 00007000 08:04 864440     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f20000-b6f27000 r-xp 00000000 08:04 864432     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f27000-b6f29000 rw-p 00006000 08:04 864432     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f29000-b6f2c000 rw-p b6f29000 00:00 0 
b6f2c000-b6f62000 r-xp 00000000 08:04 830806     /lib/libsepol.so.1
b6f62000-b6f63000 rw-p 00035000 08:04 830806     /lib/libsepol.so.1
b6f63000-b6f6d000 rw-p b6f63000 00:00 0 
b6f6d000-b6f70000 r-xp 00000000 08:04 1125499    /usr/lib/libgpg-error.so.0.3.0
b6f70000-b6f71000 rw-p 00002000 08:04 1125499    /usr/lib/libgpg-error.so.0.3.0
b6f71000-b6fc0000 r-xp 00000000 08:04 1125387    /usr/lib/libgcrypt.so.11.2.2
b6fc0000-b6fc2000 rw-p 0004e000 08:04 1125387    /usr/lib/libgcrypt.so.11.2.2
b6fc2000-b6fc3000 rw-p b6fc2000 00:00 0 
b6fc3000-b6fd7000 r-xp 00000000 08:04 1125843    /usr/lib/libtasn1.so.3.0.6
b6fd7000-b6fd8000 rw-p 00013000 08:04 1125843    /usr/lib/libtasn1.so.3.0.6
b6fd8000-b6fda000 r-xp 00000000 08:04 864453     /lib/tls/i686/cmov/libutil-2.5.so
b6fda000-b6fdc000 rw-p 00001000 08:04 864453     /lib/tls/i686/cmov/libutil-2.5.so
b6fdc000-b6ff0000 r-xp 00000000 08:04 830805     /lib/libselinux.so.1
b6ff0000-b6ff2000 rw-p 00013000 08:04 830805     /lib/libselinux.so.1
b6ff2000-b7001000 r-xp 00000000 08:04 864447     /lib/tls/i686/cmov/libresolv-2.5.so
b7001000-b7003000 rw-p 0000f000 08:04 864447     /lib/tls/i686/cmov/libresolv-2.5.so
b7003000-b7005000 rw-p b7003000 00:00 0 
b7005000-b7013000 r-xp 00000000 08:04 1125225    /usr/lib/libavahi-client.so.3.2.2
b7013000-b7014000 rw-p 0000e000 08:04 1125225    /usr/lib/libavahi-client.so.3.2.2
b7014000-b7015000 rw-p b7014000 00:00 0 
b7015000-b701f000 r-xp 00000000 08:04 1125227    /usr/lib/libavahi-common.so.3.4.3
b701f000-b7020000 rw-p 00009000 08:04 1125227    /usr/lib/libavahi-common.so.3.4.3
b7020000-b7022000 r-xp 00000000 08:04 1125231    /usr/lib/libavahi-glib.so.1.0.1
b7022000-b7023000 rw-p 00001000 08:04 1125231    /usr/lib/libavahi-glib.so.1.0.1
b7023000-b708d000 r-xp 00000000 08:04 1125495    /usr/lib/libgnutls.so.13.0.9
b708d000-b7093000 rw-p 0006a000 08:04 1125495    /usr/lib/libgnutls.so.13.0.9
b7093000-b70b5000 r-xp 00000000 08:04 1126405    /usr/lib/libpng12.so.0.15.0
b70b5000-b70b6000 rw-p 00021000 08:04 1126405    /usr/lib/libpng12.so.0.15.0
b70b6000-b70d4000 r-xp 00000000 08:04 1125342    /usr/lib/libexpat.so.1.0.0
b70d4000-b70d6000 rw-p 0001d000 08:04 1125342    /usr/lib/libexpat.so.1.0.0
b70d6000-b70d7000 rw-p b70d6000 00:00 0 
b70d7000-b713f000 r-xp 00000000 08:04 1126402    /usr/lib/libfreetype.so.6.3.10
b713f000-b7142000 rw-p 00068000 08:04 1126402    /usr/lib/libfreetype.so.6.3.10
b7142000-b7155000 r-xp 00000000 08:04 1125901    /usr/lib/libz.so.1.2.3
b7155000-b7156000 rw-p 00012000 08:04 1125901    /usr/lib/libz.so.1.2.3
b7156000-b7169000 r-xp 00000000 08:04 864430     /lib/tls/i686/cmov/libnsl-2.5.so
b7169000-b716b000 rw-p 00012000 08:04 864430     /lib/tls/i686/cmov/libnsl-2.5.so
b716b000-b716d000 rw-p b716b000 00:00 0 
b716d000-b7171000 r-xp 00000000 08:04 1125132    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7171000-b7172000 rw-p 00003000 08:04 1125132    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7172000-b7173000 rw-p b7172000 00:00 0 
b7173000-b7177000 r-xp 00000000 08:04 1125157    /usr/lib/libXdmcp.so.6.0.0
b7177000-b7178000 rw-p 00003000 08:04 1125157    /usr/lib/libXdmcp.so.6.0.0
b7178000-b7196000 r-xp 00000000 08:04 1125624    /usr/lib/libjpeg.so.62.0.0
b7196000-b7197000 rw-p 0001d000 08:04 1125624    /usr/lib/libjpeg.so.62.0.0
b7197000-b719f000 r-xp 00000000 08:04 1125833    /usr/lib/libstartup-notification-1.so.0.0.0
b719f000-b71a0000 rw-p 00007000 08:04 1125833    /usr/lib/libstartup-notification-1.so.0.0.0
b71a0000-b71a1000 rw-p b71a0000 00:00 0 
b71a1000-b71a8000 r-xp 00000000 08:04 864449     /lib/tls/i686/cmov/librt-2.5.so
b71a8000-b71aa000 rw-p 00006000 08:04 864449     /lib/tls/i686/cmov/librt-2.5.so
b71aa000-b71ae000 r-xp 00000000 08:04 1125551    /usr/lib/libgthread-2.0.so.0.1200.11
b71ae000-b71af000 rw-p 00003000 08:04 1125551    /usr/lib/libgthread-2.0.so.0.1200.11
b71af000-b71b1000 r-xp 00000000 08:04 864425     /lib/tls/i686/cmov/libdl-2.5.so
b71b1000-b71b3000 rw-p 00001000 08:04 864425     /lib/tls/i686/cmov/libdl-2.5.so
b71b3000-b71b5000 r-xp 00000000 08:04 1125453    /usr/lib/libgmodule-2.0.so.0.1200.11
b71b5000-b71b6000 rw-p 00002000 08:04 1125453    /usr/lib/libgmodule-2.0.so.0.1200.11
b71b6000-b720c000 r-xp 00000000 08:04 1125487    /usr/lib/libgnomevfs-2.so.0.1800.1
b720c000-b720f000 rw-p 00055000 08:04 1125487    /usr/lib/libgnomevfs-2.so.0.1800.1
b720f000-b727d000 r-xp 00000000 08:04 1125250    /usr/lib/libcairo.so.2.11.1
b727d000-b727f000 rw-p 0006d000 08:04 1125250    /usr/lib/libcairo.so.2.11.1
b727f000-b7280000 rw-p b727f000 00:00 0 
b7280000-b7284000 r-xp 00000000 08:04 1125163    /usr/lib/libXfixes.so.3.1.0
b7284000-b7285000 rw-p 00003000 08:04 1125163    /usr/lib/libXfixes.so.3.1.0
b7285000-b728d000 r-xp 00000000 08:04 1125153    /usr/lib/libXcursor.so.1.0.2
b728d000-b728e000 rw-p 00007000 08:04 1125153    /usr/lib/libXcursor.so.1.0.2
b728e000-b7295000 r-xp 00000000 08:04 1125169    /usr/lib/libXi.so.6.0.0
b7295000-b7296000 rw-p 00006000 08:04 1125169    /usr/lib/libXi.so.6.0.0
b7296000-b7298000 r-xp 00000000 08:04 1125171    /usr/lib/libXinerama.so.1.0.0
b7298000-b7299000 rw-p 00001000 08:04 1125171    /usr/lib/libXinerama.so.1.0.0
b7299000-b72a0000 r-xp 00000000 08:04 1125183    /usr/lib/libXrender.so.1.3.0
b72a0000-b72a1000 rw-p 00006000 08:04 1125183    /usr/lib/libXrender.so.1.3.0
b72a1000-b72ae000 r-xp 00000000 08:04 1125161    /usr/lib/libXext.so.6.4.0
b72ae000-b72af000 rw-p 0000d000 08:04 1125161    /usr/lib/libXext.so.6.4.0
b72af000-b72b0000 rw-p b72af000 00:00 0 
b72b0000-b72d3000 r-xp 00000000 08:04 1125348    /usr/lib/libfontconfig.so.1.2.0
b72d3000-b72db000 rw-p 00023000 08:04 1125348    /usr/lib/libfontconfig.so.1.2.0
b72db000-b72e2000 r-xp 00000000 08:04 1125732    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72e2000-b72e3000 rw-p 00007000 08:04 1125732    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72e3000-b730d000 r-xp 00000000 08:04 1125734    /usr/lib/libpangoft2-1.0.so.0.1600.2
b730d000-b730e000 rw-p 0002a000 08:04 1125734    /usr/lib/libpangoft2-1.0.so.0.1600.2
b730e000-b7322000 r-xp 00000000 08:04 1125209    /usr/lib/libart_lgpl_2.so.2.3.17
b7322000-b7323000 rw-p 00013000 08:04 1125209    /usr/lib/libart_lgpl_2.so.2.3.17
b7323000-b732a000 r-xp 00000000 08:04 830795     /lib/libpopt.so.0.0.0
b732a000-b732b000 rw-p 00006000 08:04 830795     /lib/libpopt.so.0.0.0
b732b000-b7354000 r-xp 00000000 08:04 1125469    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7354000-b7355000 rw-p 00029000 08:04 1125469    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7355000-b7356000 rw-p b7355000 00:00 0 
b7356000-b73b1000 r-xp 00000000 08:04 1125246    /usr/lib/libbonoboui-2.so.0.0.0
b73b1000-b73b4000 rw-p 0005a000 08:04 1125246    /usr/lib/libbonoboui-2.so.0.0.0
b73b4000-b74cb000 r-xp 00000000 08:04 1125895    /usr/lib/libxml2.so.2.6.27
b74cb000-b74d1000 rw-p 00116000 08:04 1125895    /usr/lib/libxml2.so.2.6.27
b74d1000-b7591000 r-xp 00000000 08:04 1125211    /usr/lib/libasound.so.2.0.0
b7591000-b7596000 rw-p 000bf000 08:04 1125211    /usr/lib/libasound.so.2.0.0
b7596000-b75bb000 r-xp 00000000 08:04 864427     /lib/tls/i686/cmov/libm-2.5.so
b75bb000-b75bd000 rw-p 00024000 08:04 864427     /lib/tls/i686/cmov/libm-2.5.so
b75bd000-b75dd000 r-xp 00000000 08:04 1125223    /usr/lib/libaudiofile.so.0.0.2
b75dd000-b75df000 rw-p 00020000 08:04 1125223    /usr/lib/libaudiofile.so.0.0.2
b75df000-b771a000 r-xp 00000000 08:04 864419     /lib/tls/i686/cmov/libc-2.5.so
b771a000-b771b000 r--p 0013b000 08:04 864419     /lib/tls/i686/cmov/libc-2.5.so
b771b000-b771d000 rw-p 0013c000 08:04 864419     /lib/tls/i686/cmov/libc-2.5.so
b771d000-b7721000 rw-p b771d000 00:00 0 
b7721000-b7728000 r-xp 00000000 08:04 830826     /lib/libwrap.so.0.7.6
b7728000-b7729000 rw-p 00007000 08:04 830826     /lib/libwrap.so.0.7.6
b7729000-b77bd000 r-xp 00000000 08:04 1125443    /usr/lib/libglib-2.0.so.0.1200.11
b77bd000-b77be000 rw-p 00093000 08:04 1125443    /usr/lib/libglib-2.0.so.0.1200.11
b77be000-b77ca000 r-xp 00000000 08:04 1125459    /usr/lib/libgnome-keyring.so.0.0.1
b77ca000-b77cb000 rw-p 0000b000 08:04 1125459    /usr/lib/libgnome-keyring.so.0.0.1
b77cb000-b7804000 r-xp 00000000 08:04 1125497    /usr/lib/libgobject-2.0.so.0.1200.11
b7804000-b7805000 rw-p 00039000 08:04 1125497    /usr/lib/libgobject-2.0.so.0.1200.11
b7805000-b7836000 r-xp 00000000 08:04 1125284    /usr/lib/libdbus-1.so.3.2.0
b7836000-b7837000 rw-p 00031000 08:04 1125284    /usr/lib/libdbus-1.so.3.2.0
b7837000-b7851000 r-xp 00000000 08:04 1125286    /usr/lib/libdbus-glib-1.so.2.1.0
b7851000-b7852000 rw-p 0001a000 08:04 1125286    /usr/lib/libdbus-glib-1.so.2.1.0
b7852000-b7853000 rw-p b7852000 00:00 0 
b7853000-b7866000 r-xp 00000000 08:04 864445     /lib/tls/i686/cmov/libpthread-2.5.so
b7866000-b7868000 rw-p 00013000 08:04 864445     /lib/tls/i686/cmov/libpthread-2.5.so
b7868000-b786a000 rw-p b7868000 00:00 0 
b786a000-b78b3000 r-xp 00000000 08:04 1125128    /usr/lib/libORBit-2.so.0.1.0
b78b3000-b78bd000 rw-p 00048000 08:04 1125128    /usr/lib/libORBit-2.so.0.1.0
b78bd000-b78ec000 r-xp 00000000 08:04 1125385    /usr/lib/libgconf-2.so.4.1.2
b78ec000-b78ef000 rw-p 0002e000 08:04 1125385    /usr/lib/libgconf-2.so.4.1.2
b78ef000-b7902000 r-xp 00000000 08:04 1125244    /usr/lib/libbonobo-activation.so.4.0.0
b7902000-b7904000 rw-p 00013000 08:04 1125244    /usr/lib/libbonobo-activation.so.4.0.0
b7904000-b7956000 r-xp 00000000 08:04 1125242    /usr/lib/libbonobo-2.so.0.0.0
b7956000-b7960000 rw-p 00051000 08:04 1125242    /usr/lib/libbonobo-2.so.0.0.0
b7960000-b7961000 rw-p b7960000 00:00 0 
b7961000-b7a4e000 r-xp 00000000 08:04 1125140    /usr/lib/libX11.so.6.2.0
b7a4e000-b7a52000 rw-p 000ed000 08:04 1125140    /usr/lib/libX11.so.6.2.0
b7a52000-b7a8e000 r-xp 00000000 08:04 1125730    /usr/lib/libpango-1.0.so.0.1600.2
b7a8e000-b7a90000 rw-p 0003b000 08:04 1125730    /usr/lib/libpango-1.0.so.0.1600.2
b7a90000-b7a95000 r-xp 00000000 08:04 1125181    /usr/lib/libXrandr.so.2.1.0
b7a95000-b7a96000 rw-p 00005000 08:04 1125181    /usr/lib/libXrandr.so.2.1.0
b7a96000-b7aac000 r-xp 00000000 08:04 1125407    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aac000-b7aad000 rw-p 00015000 08:04 1125407    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aad000-b7ac6000 r-xp 00000000 08:04 1125217    /usr/lib/libatk-1.0.so.0.1809.1
b7ac6000-b7ac8000 rw-p 00018000 08:04 1125217    /usr/lib/libatk-1.0.so.0.1809.1
b7ac8000-b7b4b000 r-xp 00000000 08:04 1125405    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b4b000-b7b4e000 rw-p 00083000 08:04 1125405    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b4e000-b7b4f000 rw-p b7b4e000 00:00 0 
b7b4f000-b7ea0000 r-xp 00000000 08:04 1125554    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea0000-b7ea6000 rw-p 00351000 08:04 1125554    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea6000-b7ea7000 rw-p b7ea6000 00:00 0 
b7ea7000-b7ebb000 r-xp 00000000 08:04 1125455    /usr/lib/libgnome-2.so.0.1800.0
b7ebb000-b7ebc000 rw-p 00014000 08:04 1125455    /usr/lib/libgnome-2.so.0.1800.0
b7ebc000-b7ed1000 r-xp 00000000 08:04 1125118    /usr/lib/libICE.so.6.3.0
b7ed1000-b7ed3000 rw-p 00014000 08:04 1125118    /usr/lib/libICE.so.6.3.0
b7ed3000-b7ed4000 rw-p b7ed3000 00:00 0 
b7ed4000-b7edc000 r-xp 00000000 08:04 1125136    /usr/lib/libSM.so.6.0.0
b7edc000-b7edd000 rw-p 00007000 08:04 1125136    /usr/lib/libSM.so.6.0.0
b7edd000-b7f67000 r-xp 00000000 08:04 1125485    /usr/lib/libgnomeui-2.so.0.1788.4
b7f67000-b7f6b000 rw-p 00089000 08:04 1125485    /usr/lib/libgnomeui-2.so.0.1788.4
b7f6b000-b7f7f000 r-xp 00000000 08:04 1125457    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f7f000-b7f80000 rw-p 00014000 08:04 1125457    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f80000-b7f81000 rw-p b7f80000 00:00 0 
b7f81000-b7f8a000 r-xp 00000000 08:04 1125333    /usr/lib/libesd.so.0.2.36
b7f8a000-b7f8b000 rw-p 00009000 08:04 1125333    /usr/lib/libesd.so.0.2.36
b7f8b000-b7f8d000 r-xp 00000000 08:04 1125146    /usr/lib/libXau.so.6.0.0
b7f8d000-b7f8e000 rw-p 00001000 08:04 1125146    /usr/lib/libXau.so.6.0.0
b7f8e000-b7f90000 r--s 00000000 08:04 358442     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b7f90000-b7f91000 r--p 00000000 08:04 1190106    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f91000-b7f92000 r--p 00000000 08:04 1190109    /usr/lib/locale/en_US.utf8/LC_TIME
b7f92000-b7f93000 r--p 00000000 08:04 1190104    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f93000-b7f94000 r--p 00000000 08:04 1205340    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f94000-b7f95000 r--p 00000000 08:04 1190107    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f95000-b7f96000 r--p 00000000 08:04 1190105    /usr/lib/locale/en_US.utf8/LC_NAME
b7f96000-b7f97000 r--p 00000000 08:04 1190099    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f97000-b7f98000 r--p 00000000 08:04 1190108    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f98000-b7f99000 r--p 00000000 08:04 1190103    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f99000-b7fa0000 r--s 00000000 08:04 782059     /usr/lib/gconv/gconv-modules.cache
b7fa0000-b7fa1000 r--p 00000000 08:04 1190102    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fa1000-b7fa3000 rw-p b7fa1000 00:00 0 
b7fa3000-b7fbc000 r-xp 00000000 08:04 830709     /lib/ld-2.5.so
b7fbc000-b7fbe000 rw-p 00019000 08:04 830709     /lib/ld-2.5.so
bfb5f000-bfb74000 rw-p bfb5f000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]



---

### Post by phil.rhinehart on 2007-07-29
Also this is my fstab file. Could something in this be causing the problem?

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda4 :
UUID=fe3544ad-005e-454a-8697-ac252df88d57 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda3 :
UUID=1C10A43710A41A32 /media/Media ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda1 :
UUID=EC740C6B740C3B3A /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=1f3639f1-2b60-4a67-a1e3-71495ff7d286 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0


---

### Post by bettlebrox on 2007-07-29
Change your session to the Gnome failsafe session and see if you can login.

---

### Post by phil.rhinehart on 2007-07-30
I get the same error while doing that. I have been looking around bun can't find a solution. I really hope I don't have to reinstall.
Any other ideas?

---

### Post by bettlebrox on 2007-07-30
what is the output from the ifconfig command?

---

### Post by phil.rhinehart on 2007-07-31
> **bettlebrox said:**
> what is the output from the ifconfig command?

Here is the output:

> ath0      Link encap:Ethernet  HWaddr 00:14:A4:73:C5:D2  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe73:c5d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123683 (120.7 KiB)  TX bytes:8234 (8.0 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F2:2E:52  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E4:F2:2E:52  
          inet addr:169.254.6.251  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:258 (258.0 b)  TX bytes:258 (258.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-73-C5-D2-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2409 errors:0 dropped:0 overruns:0 frame:1763
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:291193 (284.3 KiB)  TX bytes:17536 (17.1 KiB)
          Interrupt:17 



---

### Post by bettlebrox on 2007-07-31
I was thinking that the *lo* interface mightn't be up and that can cause problems. But, that's not it, cause *lo* is up!

What I'd suggest is renaming your .gnome directories and see if you can login with a fresh session.

That screen shot looks really good, what is the theme, and what is the bar with the icons at the bottom?

---

### Post by phil.rhinehart on 2007-07-31
When you say rename the .gnome directories which ones do you mean?


Second, the bar at the bottom is AWN which works really well. I am running beryl but it doesn't load right now due to this problem so the background doesn't cover the full screen and there are no window borders.

---

### Post by Oldbones on 2007-07-31
I to am experiencing this problem.  I'm running Compiz and haven't rebooted since it updated.  I logged in with a KDE session which seems unaffected.  I didn't even know it was an option.
the problem was something about libavahi-client.so.3  not found.


this KDE session shares all the same files.  I was worried my bookmarks and such were gone.  What a lifeboat!

---

### Post by phil.rhinehart on 2007-08-06
I have still been unable to find a solution to my problem. If anyone has an idea please let me know.

---

### Post by phil.rhinehart on 2007-08-12
-

---

### Post by bettlebrox on 2007-08-13
> **phil.rhinehart said:**
> When you say rename the .gnome directories which ones do you mean?


Second, the bar at the bottom is AWN which works really well. I am running beryl but it doesn't load right now due to this problem so the background doesn't cover the full screen and there are no window borders.

.gnome/
.gnome2/
and
.gconf/  
.gconfd/

Maybe Beryl is causing your problems?

---

### Post by shad0w_walker on 2007-08-13
I would suggest you create a new user and try logging into that account, if it works with out issues then you know its something in your home folder, probably a startup program or a screwed up config file.

---

