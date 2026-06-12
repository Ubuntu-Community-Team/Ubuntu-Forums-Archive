---
title: "HELP!!! gnome has crashed and burned!!"
date: 2007-08-20
forum: General Help
---

### Post by strungoutfan78 on 2007-08-20
ok so i just installed frostwire through the repos and now i can't login to gnome.  i get an error message that reads:  

> Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

this is the output that follows:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "neil"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/deathstar:/tmp/.ICE-unix/6083
Initializing gnome-mount extension
Password:
/usr/bin/compiz.real
/usr/bin/ccsm
/usr/bin/compiz
/usr/bin/gtk-window-decorator
/usr/bin/emerald
Failed to load Pixbuf for '/usr/share/icons/hicolor/16x16/apps/frostwire'
Failed to load Pixbuf for '/usr/share/icons/hicolor/16x16/apps/frostwire'
Starting gdesklets-daemon...

Connecting to daemon [###          ]
Connecting to daemon [ ###         ]/usr/bin/metacity

Connecting to daemon [  ###        ]
Connecting to daemon [   ###       ]
** (kiba-dock:6181): CRITICAL **: kiba_icon_set_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

Connecting to daemon [    ###      ]*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x0825adb0 ***
======= Backtrace: =========
/lib/libc.so.6[0xb7610312]
/lib/libc.so.6[0xb7612637]
/lib/libc.so.6(__libc_malloc+0x85)[0xb7613d35]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77152c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7aabdb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7aad1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7ab0f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7ab11c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7ab127f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7d66440]
/usr/bin/gnome-session[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb770e3c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb770ddf2]
/usr/lib/libglib-2.0.so.0[0xb7710dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb7711335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb773740d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb770ddf2]
/usr/lib/libglib-2.0.so.0[0xb7710dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7711179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c46044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/libc.so.6(__libc_start_main+0xdc)[0xb75c1ebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:04 2458529    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:04 2458529    /usr/bin/gnome-session
08069000-082a3000 rw-p 08069000 00:00 0          [heap]
b5900000-b5921000 rw-p b5900000 00:00 0 
b5921000-b5a00000 ---p b5921000 00:00 0 
b5abf000-b5aca000 r-xp 00000000 08:01 1547374    /lib/libgcc_s.so.1
b5aca000-b5acb000 rw-p 0000a000 08:01 1547374    /lib/libgcc_s.so.1
b5ad9000-b5ada000 ---p b5ad9000 00:00 0 
b5ada000-b62d9000 rw-p b5ada000 00:00 0 
b62d9000-b6356000 r--p 00000000 08:04 803251     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6356000-b6358000 r-xp 00000000 08:04 1410232    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6358000-b6359000 rw-p 00001000 08:04 1410232    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6359000-b635f000 r--s 00000000 08:01 1059177    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b635f000-b6360000 r--s 00000000 08:01 1059134    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6360000-b6363000 r--s 00000000 08:01 1059133    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6363000-b6364000 r--s 00000000 08:01 1059132    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6364000-b6365000 r--s 00000000 08:01 1059131    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6365000-b6369000 r--s 00000000 08:01 1059130    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6369000-b636a000 r--s 00000000 08:01 1059128    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b636a000-b636c000 r--s 00000000 08:01 1059126    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b636c000-b636e000 r--s 00000000 08:01 1059105    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b636e000-b636f000 r--s 00000000 08:01 1059104    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b636f000-b6371000 r--s 00000000 08:01 1059103    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b6371000-b6377000 r--s 00000000 08:01 1059102    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6377000-b6379000 r--s 00000000 08:01 1059101    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6379000-b637b000 r--s 00000000 08:01 1059100    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b637b000-b6383000 r--s 00000000 08:01 1059099    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6383000-b6389000 r--s 00000000 08:01 1059098    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6389000-b638a000 r--s 00000000 08:01 1059097    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b638a000-b63a1000 r--s 00000000 08:01 1059623    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b63a1000-b63a3000 r--s 00000000 08:01 1059096    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b63a3000-b63a9000 r--s 00000000 08:01 1059025    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b63a9000-b63ac000 r--s 00000000 08:01 1058961    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b63ac000-b63b0000 r--s 00000000 08:01 1058960    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b63b0000-b63b2000 r--s 00000000 08:01 1058901    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b63b2000-b63b3000 r--s 00000000 08:01 1059671    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b63b3000-b63b4000 r--s 00000000 08:01 1059670    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b63b4000-b63b5000 r--s 00000000 08:01 1059669    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b63b5000-b63b6000 r--s 00000000 08:01 1059668    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b63b6000-b63b7000 r--s 00000000 08:01 1059678    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b63b7000-b63ba000 r--s 00000000 08:01 1059666    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b63ba000-b63bf000 r--s 00000000 08:01 1059677    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b63bf000-b63c1000 r--s 00000000 08:01 1059664    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b63c1000-b63c2000 r--s 00000000 08:01 1059663    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b63c2000-b63c4000 r--s 00000000 08:01 1059662    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b63c4000-b63c5000 r--s 00000000 08:01 1059661    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b63c5000-b63ca000 r--s 00000000 08:01 1059660    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b63ca000-b63ce000 r--s 00000000 08:01 1059659    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b63ce000-b63d0000 r--s 00000000 08:01 1059658    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b63d0000-b63d3000 r--s 00000000 08:01 1059631    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b63d3000-b63d4000 r--s 00000000 08:01 1059630    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b63d4000-b63d6000 r--s 00000000 08:01 1059629    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b63d6000-b63da000 r--s 00000000 08:01 1059657    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b63da000-b63e0000 r--s 00000000 08:01 1059627    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b63e0000-b63e1000 r--s 00000000 08:01 1059626    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b63e1000-b63e9000 r--s 00000000 08:01 1059624    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b63e9000-b63eb000 r--s 00000000 08:01 1059655    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b63eb000-b65e8000 r--p 00000000 08:04 821485     /usr/share/icons/hicolor/icon-theme.cache
b65e8000-b6c91000 r--p 00000000 08:04 837245     /usr/share/icons/gnome/icon-theme.cache
b6c91000-b6cb5000 r-xp 00000000 08:04 1410314    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cb5000-b6cb6000 rw-p 00024000 08:04 1410314    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cb6000-b6d16000 rw-s 00000000 00:08 1835011    /SYSV00000000 (deleted)
b6d16000-b6d8c000 rw-p b6d16000 00:00 0 
b6d8c000-b6d93000 r-xp 00000000 08:04 1394351    /usr/lib/libfam.so.0.0.0
b6d93000-b6d94000 rw-p 00006000 08:04 1394351    /usr/lib/libfam.so.0.0.0
b6d94000-b6d9a000 r-xp 00000000 08:01 1547378    /lib/libacl.so.1.1.0
b6d9a000-b6d9b000 rw-p 00005000 08:01 1547378    /lib/libacl.so.1.1.0
b6d9b000-b6d9e000 r-xp 00000000 08:01 1547362    /lib/libattr.so.1.1.0
b6d9e000-b6d9f000 rw-p 00002000 08:01 1547362    /lib/libattr.so.1.1.0
b6da0000-b6da3000 r--s 00000000 08:01 1059622    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6da3000-b6da5000 r--s 00000000 08:01 1059653    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6da5000-b6da7000 r--s 00000000 08:01 1059592    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6da7000-b6dab000 r-xp 00000000 08:04 1410248    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dab000-b6dac000 rw-p 00003000 08:04 1410248    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dad000-b6db9000 r-xp 00000000 08:04 1410293    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6db9000-b6dba000 rw-p 0000b000 08:04 1410293    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dba000-b6dbb000 r-xp 00000000 08:04 1395501    /usr/lib/gconv/ISO8859-1.so
b6dbb000-b6dbd000 rw-p 00000000 08:04 1395501    /usr/lib/gconv/ISO8859-1.so
b6dbd000-b6df8000 r--p 00000000 08:04 1409841    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6df8000-b6df9000 r--p 00000000 08:04 1409842    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6df9000-b6dfa000 r--p 00000000 08:04 1409843    /usr/lib/locale/en_US.utf8/LC_TIME
b6dfa000-b6ed1000 r--p 00000000 08:04 1409844    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ed1000-b6ed2000 r--p 00000000 08:04 1409845    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6ed2000-b6eda000 r-xp 00000000 08:01 1547525    /lib/libnss_files-2.5.so
b6eda000-b6edc000 rw-p 00007000 08:01 1547525    /lib/libnss_files-2.5.so
b6edc000-b6ee4000 r-xp 00000000 08:01 1547531    /lib/libnss_nis-2.5.so
b6ee4000-b6ee6000 rw-p 00007000 08:01 1547531    /lib/libnss_nis-2.5.so
b6ee6000-b6eec000 r-xp 00000000 08:01 1547521    /lib/libnss_compat-2.5.so
b6eec000-b6eee000 rw-p 00005000 08:01 1547521    /lib/libnss_compat-2.5.so
b6eee000-b6ef1000 rw-p b6eee000 00:00 0 
b6ef1000-b6f27000 r-xp 00000000 08:01 1547426    /lib/libsepol.so.1
b6f27000-b6f28000 rw-p 00035000 08:01 1547426    /lib/libsepol.so.1
b6f28000-b6f32000 rw-p b6f28000 00:00 0 
b6f32000-b6f35000 r-xp 00000000 08:04 1393440    /usr/lib/libgpg-error.so.0.3.0
b6f35000-b6f36000 rw-p 00002000 08:04 1393440    /usr/lib/libgpg-error.so.0.3.0
b6f36000-b6f37000 rw-p b6f36000 00:00 0 
b6f37000-b6f86000 r-xp 00000000 08:04 1393438    /usr/lib/libgcrypt.so.11.2.2
b6f86000-b6f88000 rw-p 0004e000 08:04 1393438    /usr/lib/libgcrypt.so.11.2.2
b6f88000-b6f9c000 r-xp 00000000 08:04 1393445    /usr/lib/libtasn1.so.3.0.6
b6f9c000-b6f9d000 rw-p 00013000 08:04 1393445    /usr/lib/libtasn1.so.3.0.6
b6f9d000-b6f9f000 r-xp 00000000 08:01 1547548    /lib/libutil-2.5.so
b6f9f000-b6fa1000 rw-p 00001000 08:01 1547548    /lib/libutil-2.5.so
b6fa1000-b6fb5000 r-xp 00000000 08:01 1547424    /lib/libselinux.so.1
b6fb5000-b6fb7000 rw-p 00013000 08:01 1547424    /lib/libselinux.so.1
b6fb7000-b6fc5000 r-xp 00000000 08:01 1547544    /lib/libresolv-2.5.so
b6fc5000-b6fc7000 rw-p 0000d000 08:01 1547544    /lib/libresolv-2.5.so
b6fc7000-b6fca000 rw-p b6fc7000 00:00 0 
b6fca000-b6fd8000 r-xp 00000000 08:04 1394345    /usr/lib/libavahi-client.so.3.2.2
b6fd8000-b6fd9000 rw-p 0000e000 08:04 1394345    /usr/lib/libavahi-client.so.3.2.2
b6fd9000-b6fe3000 r-xp 00000000 08:04 1394343    /usr/lib/libavahi-common.so.3.4.3
b6fe3000-b6fe4000 rw-p 00009000 08:04 1394343    /usr/lib/libavahi-common.so.3.4.3
b6fe4000-b6fe6000 r-xp 00000000 08:04 1394347    /usr/lib/libavahi-glib.so.1.0.1
b6fe6000-b6fe7000 rw-p 00001000 08:04 1394347    /usr/lib/libavahi-glib.so.1.0.1
b6fe7000-b7051000 r-xp 00000000 08:04 1393377    /usr/lib/libgnutls.so.13.0.9
b7051000-b7057000 rw-p 0006a000 08:04 1393377    /usr/lib/libgnutls.so.13.0.9
b7057000-b7079000 r-xp 00000000 08:04 1393898    /usr/lib/libpng12.so.0.15.0
b7079000-b707a000 rw-p 00021000 08:04 1393898    /usr/lib/libpng12.so.0.15.0
b707a000-b707b000 rw-p b707a000 00:00 0 
b707b000-b7099000 r-xp 00000000 08:04 1394205    /usr/lib/libexpat.so.1.0.0
b7099000-b709b000 rw-p 0001d000 08:04 1394205    /usr/lib/libexpat.so.1.0.0
b709b000-b7107000 r-xp 00000000 08:04 1394004    /usr/lib/libfreetype.so.6.3.16
b7107000-b710b000 rw-p 0006b000 08:04 1394004    /usr/lib/libfreetype.so.6.3.16
b710b000-b711e000 r-xp 00000000 08:04 1393004    /usr/lib/libz.so.1.2.3
b711e000-b711f000 rw-p 00012000 08:04 1393004    /usr/lib/libz.so.1.2.3
b711f000-b7131000 r-xp 00000000 08:01 1547520    /lib/libnsl-2.5.so
b7131000-b7133000 rw-p 00011000 08:01 1547520    /lib/libnsl-2.5.so
b7133000-b7136000 rw-p b7133000 00:00 0 
b7136000-b713a000 r-xp 00000000 08:04 1394298    /usr/lib/libORBitCosNaming-2.so.0.1.0
b713a000-b713b000 rw-p 00003000 08:04 1394298    /usr/lib/libORBitCosNaming-2.so.0.1.0
b713b000-b713f000 r-xp 00000000 08:04 1394195    /usr/lib/libXdmcp.so.6.0.0
b713f000-b7140000 rw-p 00003000 08:04 1394195    /usr/lib/libXdmcp.so.6.0.0
b7140000-b715e000 r-xp 00000000 08:04 1394325    /usr/lib/libjpeg.so.62.0.0
b715e000-b715f000 rw-p 0001d000 08:04 1394325    /usr/lib/libjpeg.so.62.0.0
b715f000-b7160000 rw-p b715f000 00:00 0 
b7160000-b7168000 r-xp 00000000 08:04 1394371    /usr/lib/libstartup-notification-1.so.0.0.0
b7168000-b7169000 rw-p 00007000 08:04 1394371    /usr/lib/libstartup-notification-1.so.0.0.0
b7169000-b716f000 r-xp 00000000 08:01 1547545    /lib/librt-2.5.so
b716f000-b7171000 rw-p 00006000 08:01 1547545    /lib/librt-2.5.so
b7171000-b7175000 r-xp 00000000 08:04 1394285    /usr/lib/libgthread-2.0.so.0.1200.11
b7175000-b7176000 rw-p 00003000 08:04 1394285    /usr/lib/libgthread-2.0.so.0.1200.11
b7176000-b7178000 r-xp 00000000 08:01 1547516    /lib/libdl-2.5.so
b7178000-b717a000 rw-p 00001000 08:01 1547516    /lib/libdl-2.5.so
b717a000-b717c000 r-xp 00000000 08:04 1394284    /usr/lib/libgmodule-2.0.so.0.1200.11
b717c000-b717d000 rw-p 00002000 08:04 1394284    /usr/lib/libgmodule-2.0.so.0.1200.11
b717d000-b71d3000 r-xp 00000000 08:04 1394359    /usr/lib/libgnomevfs-2.so.0.1800.1
b71d3000-b71d6000 rw-p 00055000 08:04 1394359    /usr/lib/libgnomevfs-2.so.0.1800.1
b71d6000-b71d7000 rw-p b71d6000 00:00 0 
b71d7000-b724b000 r-xp 00000000 08:04 1393370    /usr/lib/libcairo.so.2.11.5
b724b000-b724d000 rw-p 00074000 08:04 1393370    /usr/lib/libcairo.so.2.11.5
b724d000-b7251000 r-xp 00000000 08:04 1394203    /usr/lib/libXfixes.so.3.1.0
b7251000-b7252000 rw-p 00003000 08:04 1394203    /usr/lib/libXfixes.so.3.1.0
b7252000-b725a000 r-xp 00000000 08:04 1394274    /usr/lib/libXcursor.so.1.0.2
b725a000-b725b000 rw-p 00007000 08:04 1394274    /usr/lib/libXcursor.so.1.0.2
b725b000-b7262000 r-xp 00000000 08:04 1394239    /usr/lib/libXi.so.6.0.0
b7262000-b7263000 rw-p 00006000 08:04 1394239    /usr/lib/libXi.so.6.0.0
b7263000-b7265000 r-xp 00000000 08:04 1394243    /usr/lib/libXinerama.so.1.0.0
b7265000-b7266000 rw-p 00001000 08:04 1394243    /usr/lib/libXinerama.so.1.0.0
b7266000-b726d000 r-xp 00000000 08:04 1394214    /usr/lib/libXrender.so.1.3.0
b726d000-b726e000 rw-p 00006000 08:04 1394214    /usr/lib/libXrender.so.1.3.0
b726e000-b726f000 rw-p b726e000 00:00 0 
b726f000-b727c000 r-xp 00000000 08:04 1394199    /usr/lib/libXext.so.6.4.0
b727c000-b727d000 rw-p 0000d000 08:04 1394199    /usr/lib/libXext.so.6.4.0
b727d000-b72a0000 r-xp 00000000 08:04 1394212    /usr/lib/libfontconfig.so.1.2.0
b72a0000-b72a8000 rw-p 00023000 08:04 1394212    /usr/lib/libfontconfig.so.1.2.0
b72a8000-b72af000 r-xp 00000000 08:04 1394315    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72af000-b72b0000 rw-p 00007000 08:04 1394315    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72b0000-b72da000 r-xp 00000000 08:04 1394316    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72da000-b72db000 rw-p 0002a000 08:04 1394316    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72db000-b72ef000 r-xp 00000000 08:04 1394292    /usr/lib/libart_lgpl_2.so.2.3.17
b72ef000-b72f0000 rw-p 00013000 08:04 1394292    /usr/lib/libart_lgpl_2.so.2.3.17
b72f0000-b72f7000 r-xp 00000000 08:01 1547594    /lib/libpopt.so.0.0.0
b72f7000-b72f8000 rw-p 00006000 08:01 1547594    /lib/libpopt.so.0.0.0
b72f8000-b72f9000 rw-p b72f8000 00:00 0 
b72f9000-b7322000 r-xp 00000000 08:04 1394363    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7322000-b7323000 rw-p 00029000 08:04 1394363    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7323000-b737e000 r-xp 00000000 08:04 1394365    /usr/lib/libbonoboui-2.so.0.0.0
b737e000-b7381000 rw-p 0005a000 08:04 1394365    /usr/lib/libbonoboui-2.so.0.0.0
b7381000-b7498000 r-xp 00000000 08:04 1394278    /usr/lib/libxml2.so.2.6.27
b7498000-b749e000 rw-p 00116000 08:04 1394278    /usr/lib/libxml2.so.2.6.27
b749e000-b755e000 r-xp 00000000 08:04 1393129    /usr/lib/libasound.so.2.0.0
b755e000-b7563000 rw-p 000bf000 08:04 1393129    /usr/lib/libasound.so.2.0.0
b7563000-b7587000 r-xp 00000000 08:01 1547517    /lib/libm-2.5.so
b7587000-b7589000 rw-p 00023000 08:01 1547517    /lib/libm-2.5.so
b7589000-b75a9000 r-xp 00000000 08:04 1394339    /usr/lib/libaudiofile.so.0.0.2
b75a9000-b75ab000 rw-p 00020000 08:04 1394339    /usr/lib/libaudiofile.so.0.0.2
b75ab000-b75ac000 rw-p b75ab000 00:00 0 
b75ac000-b76d2000 r-xp 00000000 08:01 1547507    /lib/libc-2.5.so
b76d2000-b76d3000 r--p 00125000 08:01 1547507    /lib/libc-2.5.so
b76d3000-b76d5000 rw-p 00126000 08:01 1547507    /lib/libc-2.5.so
b76d5000-b76d8000 rw-p b76d5000 00:00 0 
b76d8000-b76df000 r-xp 00000000 08:01 1548874    /lib/libwrap.so.0.7.6
b76df000-b76e0000 rw-p 00007000 08:01 1548874    /lib/libwrap.so.0.7.6
b76e0000-b7774000 r-xp 00000000 08:04 1394282    /usr/lib/libglib-2.0.so.0.1200.11
b7774000-b7775000 rw-p 00093000 08:04 1394282    /usr/lib/libglib-2.0.so.0.1200.11
b7775000-b7781000 r-xp 00000000 08:04 1394367    /usr/lib/libgnome-keyring.so.0.0.1
b7781000-b7782000 rw-p 0000b000 08:04 1394367    /usr/lib/libgnome-keyring.so.0.0.1
b7782000-b77bb000 r-xp 00000000 08:04 1394283    /usr/lib/libgobject-2.0.so.0.1200.11
b77bb000-b77bc000 rw-p 00039000 08:04 1394283    /usr/lib/libgobject-2.0.so.0.1200.11
b77bc000-b77ee000 r-xp 00000000 08:04 1393826    /usr/lib/libdbus-1.so.3.2.0
b77ee000-b77ef000 rw-p 00031000 08:04 1393826    /usr/lib/libdbus-1.so.3.2.0
b77ef000-b77f0000 rw-p b77ef000 00:00 0 
b77f0000-b780a000 r-xp 00000000 08:04 1394349    /usr/lib/libdbus-glib-1.so.2.1.0
b780a000-b780b000 rw-p 0001a000 08:04 1394349    /usr/lib/libdbus-glib-1.so.2.1.0
b780b000-b781e000 r-xp 00000000 08:01 1547543    /lib/libpthread-2.5.so
b781e000-b7820000 rw-p 00012000 08:01 1547543    /lib/libpthread-2.5.so
b7820000-b7822000 rw-p b7820000 00:00 0 
b7822000-b786b000 r-xp 00000000 08:04 1394296    /usr/lib/libORBit-2.so.0.1.0
b786b000-b7875000 rw-p 00048000 08:04 1394296    /usr/lib/libORBit-2.so.0.1.0
b7875000-b78a4000 r-xp 00000000 08:04 1394308    /usr/lib/libgconf-2.so.4.1.2
b78a4000-b78a7000 rw-p 0002e000 08:04 1394308    /usr/lib/libgconf-2.so.4.1.2
b78a7000-b78ba000 r-xp 00000000 08:04 1394303    /usr/lib/libbonobo-activation.so.4.0.0
b78ba000-b78bc000 rw-p 00013000 08:04 1394303    /usr/lib/libbonobo-activation.so.4.0.0
b78bc000-b790e000 r-xp 00000000 08:04 1394302    /usr/lib/libbonobo-2.so.0.0.0
b790e000-b7918000 rw-p 00051000 08:04 1394302    /usr/lib/libbonobo-2.so.0.0.0
b7918000-b7919000 rw-p b7918000 00:00 0 
b7919000-b7a06000 r-xp 00000000 08:04 1394197    /usr/lib/libX11.so.6.2.0
b7a06000-b7a0a000 rw-p 000ed000 08:04 1394197    /usr/lib/libX11.so.6.2.0
b7a0a000-b7a46000 r-xp 00000000 08:04 1394314    /usr/lib/libpango-1.0.so.0.1600.2
b7a46000-b7a48000 rw-p 0003b000 08:04 1394314    /usr/lib/libpango-1.0.so.0.1600.2
b7a48000-b7a4d000 r-xp 00000000 08:04 1394262    /usr/lib/libXrandr.so.2.1.0
b7a4d000-b7a4e000 rw-p 00005000 08:04 1394262    /usr/lib/libXrandr.so.2.1.0
b7a4e000-b7a64000 r-xp 00000000 08:04 1394329    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a64000-b7a65000 rw-p 00015000 08:04 1394329    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a65000-b7a7e000 r-xp 00000000 08:04 1394290    /usr/lib/libatk-1.0.so.0.1809.1
b7a7e000-b7a80000 rw-p 00018000 08:04 1394290    /usr/lib/libatk-1.0.so.0.1809.1
b7a80000-b7b03000 r-xp 00000000 08:04 1394330    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b03000-b7b06000 rw-p 00083000 08:04 1394330    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b06000-b7b07000 rw-p b7b06000 00:00 0 
b7b07000-b7e58000 r-xp 00000000 08:04 1394331    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e58000-b7e5e000 rw-p 00351000 08:04 1394331    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e5e000-b7e5f000 rw-p b7e5e000 00:00 0 
b7e5f000-b7e73000 r-xp 00000000 08:04 1394361    /usr/lib/libgnome-2.so.0.1800.0
b7e73000-b7e74000 rw-p 00014000 08:04 1394361    /usr/lib/libgnome-2.so.0.1800.0
b7e74000-b7e89000 r-xp 00000000 08:04 1394218    /usr/lib/libICE.so.6.3.0
b7e89000-b7e8b000 rw-p 00014000 08:04 1394218    /usr/lib/libICE.so.6.3.0
b7e8b000-b7e8c000 rw-p b7e8b000 00:00 0 
b7e8c000-b7e94000 r-xp 00000000 08:04 1394220    /usr/lib/libSM.so.6.0.0
b7e94000-b7e95000 rw-p 00007000 08:04 1394220    /usr/lib/libSM.so.6.0.0
b7e95000-b7f1f000 r-xp 00000000 08:04 1394369    /usr/lib/libgnomeui-2.so.0.1788.4
b7f1f000-b7f23000 rw-p 00089000 08:04 1394369    /usr/lib/libgnomeui-2.so.0.1788.4
b7f23000-b7f37000 r-xp 00000000 08:04 1394373    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f37000-b7f38000 rw-p 00014000 08:04 1394373    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f38000-b7f39000 rw-p b7f38000 00:00 0 
b7f39000-b7f42000 r-xp 00000000 08:04 1394341    /usr/lib/libesd.so.0.2.36
b7f42000-b7f43000 rw-p 00009000 08:04 1394341    /usr/lib/libesd.so.0.2.36
b7f43000-b7f45000 r-xp 00000000 08:04 1394193    /usr/lib/libXau.so.6.0.0
b7f45000-b7f46000 rw-p 00001000 08:04 1394193    /usr/lib/libXau.so.6.0.0
b7f46000-b7f47000 r--p 00000000 08:04 1409847    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f47000-b7f48000 r--p 00000000 08:04 1409848    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f48000-b7f49000 r--p 00000000 08:04 1409849    /usr/lib/locale/en_US.utf8/LC_NAME
b7f49000-b7f4a000 r--p 00000000 08:04 1409850    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f4a000-b7f4b000 r--p 00000000 08:04 1409851    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f4b000-b7f4c000 r--p 00000000 08:04 1409852    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f4c000-b7f53000 r--s 00000000 08:04 1392663    /usr/lib/gconv/gconv-modules.cache
b7f53000-b7f54000 r--p 00000000 08:04 1409853    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f54000-b7f56000 rw-p b7f54000 00:00 0 
b7f56000-b7f6f000 r-xp 00000000 08:01 1547375    /lib/ld-2.5.so
b7f6f000-b7f71000 rw-p 00019000 08:01 1547375    /lib/ld-2.5.so
bfdcd000-bfde3000 rw-p bfdcd000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

Connecting to daemon [     ###     ]
(rhythmbox:6179): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:6205): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6207): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6172): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

what does this mean?  how can i fix it?

if i click ok it logs me out and i can only operate while this message box is being displayed.
what gives??:confused::confused::confused:

---

