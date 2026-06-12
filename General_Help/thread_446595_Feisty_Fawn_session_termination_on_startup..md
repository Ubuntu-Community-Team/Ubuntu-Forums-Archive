---
title: "Feisty Fawn session termination on startup."
date: 2007-05-17
forum: General Help
---

### Post by Gramlengo on 2007-05-17
Everything worked well untill I started my PC today.
After logging in I get the following message:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "gramlengo"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Gramlengo:/tmp/.ICE-unix/6636
Initializing gnome-mount extension

(gnome-power-manager:6730): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:6728): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

When I click OK, the session is terminated.
I am boggled.

Edit: I restarted X, and I am now getting a different error code:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "gramlengo"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Gramlengo:/tmp/.ICE-unix/7042
*** glibc detected *** x-session-manager: free(): invalid pointer: 0x08206898 ***
Initializing gnome-mount extension
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75d77cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75dae30]
/usr/lib/libICE.so.6(_IceFreeConnection+0xde)[0xb7e6008e]
/usr/lib/libICE.so.6(IceCloseConnection+0xb9)[0xb7e601a9]
/usr/lib/libgnomeui-2.so.0[0xb7eb1698]
/usr/lib/libglib-2.0.so.0[0xb771040d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76e6df2]
/usr/lib/libglib-2.0.so.0[0xb76e9dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb76ea335]
x-session-manager[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb771040d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb76e6df2]
/usr/lib/libglib-2.0.so.0[0xb76e9dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb76ea179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c1e044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7585ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 03:03 1946649    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 03:03 1946649    /usr/bin/gnome-session
08069000-0823b000 rw-p 08069000 00:00 0          [heap]
b5800000-b5821000 rw-p b5800000 00:00 0 
b5821000-b5900000 ---p b5821000 00:00 0 
b59d5000-b59e0000 r-xp 00000000 03:03 49086      /lib/libgcc_s.so.1
b59e0000-b59e1000 rw-p 0000a000 03:03 49086      /lib/libgcc_s.so.1
b59ef000-b5a4f000 rw-s 00000000 00:08 3473414    /SYSV00000000 (deleted)
b5a4f000-b5a50000 ---p b5a4f000 00:00 0 
b5a50000-b6250000 rw-p b5a50000 00:00 0 
b6250000-b62cd000 r--p 00000000 03:03 2158710    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b62cd000-b62cf000 r-xp 00000000 03:03 1995798    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b62cf000-b62d0000 rw-p 00001000 03:03 1995798    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b62d0000-b62d6000 r--s 00000000 03:03 2420454    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b62d6000-b62d7000 r--s 00000000 03:03 2420379    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b62d7000-b62da000 r--s 00000000 03:03 2420393    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b62da000-b62db000 r--s 00000000 03:03 2420375    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b62db000-b62dc000 r--s 00000000 03:03 2420387    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b62dc000-b62e0000 r--s 00000000 03:03 2420371    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b62e0000-b62e1000 r--s 00000000 03:03 2420367    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b62e1000-b62e3000 r--s 00000000 03:03 2420383    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b62e3000-b62e5000 r--s 00000000 03:03 2420377    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b62e5000-b62e6000 r--s 00000000 03:03 2420309    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b62e6000-b62e8000 r--s 00000000 03:03 2420307    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b62e8000-b62ee000 r--s 00000000 03:03 2420373    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b62ee000-b62f0000 r--s 00000000 03:03 2420303    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b62f0000-b62f2000 r--s 00000000 03:03 2420301    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b62f2000-b62fa000 r--s 00000000 03:03 2420311    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b62fa000-b6300000 r--s 00000000 03:03 2420305    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6300000-b6301000 r--s 00000000 03:03 2420299    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6301000-b6318000 r--s 00000000 03:03 2420277    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6318000-b631a000 r--s 00000000 03:03 2420295    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b631a000-b6320000 r--s 00000000 03:03 2420297    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6320000-b6323000 r--s 00000000 03:03 2420718    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6323000-b6327000 r--s 00000000 03:03 2420735    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6327000-b632d000 r--s 00000000 03:03 2420267    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b632d000-b632e000 r--s 00000000 03:03 2420714    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b632e000-b632f000 r--s 00000000 03:03 2420721    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b632f000-b6330000 r--s 00000000 03:03 2420720    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6330000-b6331000 r--s 00000000 03:03 2420719    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6331000-b6332000 r--s 00000000 03:03 2420274    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6332000-b6335000 r--s 00000000 03:03 2420715    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6335000-b633a000 r--s 00000000 03:03 2420273    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b633a000-b633c000 r--s 00000000 03:03 2420716    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b633c000-b633d000 r--s 00000000 03:03 2420712    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b633d000-b633f000 r--s 00000000 03:03 2420694    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b633f000-b6340000 r--s 00000000 03:03 2420713    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6340000-b6345000 r--s 00000000 03:03 2420736    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6345000-b6349000 r--s 00000000 03:03 2420709    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6349000-b634b000 r--s 00000000 03:03 2420730    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b634b000-b634e000 r--s 00000000 03:03 2420711    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b634e000-b634f000 r--s 00000000 03:03 2420710    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b634f000-b6351000 r--s 00000000 03:03 2420724    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6351000-b6355000 r--s 00000000 03:03 2420271    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6355000-b635b000 r--s 00000000 03:03 2420707    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b635b000-b635c000 r--s 00000000 03:03 2420706    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b635c000-b6364000 r--s 00000000 03:03 2420705    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6364000-b6366000 r--s 00000000 03:03 2420270    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6366000-b6369000 r--s 00000000 03:03 2420703    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6369000-b65c2000 r--p 00000000 03:03 2243141    /usr/share/icons/hicolor/icon-theme.cache
b65c2000-b6c69000 r--p 00000000 03:03 2243140    /usr/share/icons/gnome/icon-theme.cache
b6c69000-b6c8b000 r--p 00000000 03:03 2240650    /usr/share/icons/Crux/icon-theme.cache
b6c8b000-b6c97000 r-xp 00000000 03:03 1995262    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6c97000-b6c98000 rw-p 0000b000 03:03 1995262    /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6c98000-b6cf8000 rw-s 00000000 00:08 3440645    /SYSV00000000 (deleted)
b6cf8000-b6d55000 rw-p b6cf8000 00:00 0 
b6d55000-b6d5c000 r-xp 00000000 03:03 1948527    /usr/lib/libfam.so.0.0.0
b6d5c000-b6d5d000 rw-p 00006000 03:03 1948527    /usr/lib/libfam.so.0.0.0
b6d5d000-b6d63000 r-xp 00000000 03:03 2567297    /lib/libacl.so.1.1.0
b6d63000-b6d64000 rw-p 00005000 03:03 2567297    /lib/libacl.so.1.1.0
b6d64000-b6d67000 r-xp 00000000 03:03 2567339    /lib/libattr.so.1.1.0
b6d67000-b6d68000 rw-p 00002000 03:03 2567339    /lib/libattr.so.1.1.0
b6d68000-b6d6a000 r--s 00000000 03:03 2420269    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d6a000-b6d70000 r--s 00000000 03:03 2420266    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6d70000-b6d74000 r-xp 00000000 03:03 1996384    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d74000-b6d75000 rw-p 00003000 03:03 1996384    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d76000-b6d82000 r-xp 00000000 03:03 1995273    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d82000-b6d83000 rw-p 0000b000 03:03 1995273    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d83000-b6d84000 r-xp 00000000 03:03 1962731    /usr/lib/gconv/ISO8859-1.so
b6d84000-b6d86000 rw-p 00000000 03:03 1962731    /usr/lib/gconv/ISO8859-1.so
b6d86000-b6dc1000 r--p 00000000 03:03 1995231    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6dc1000-b6dc2000 r--p 00000000 03:03 1996412    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6dc2000-b6dc3000 r--p 00000000 03:03 1996423    /usr/lib/locale/en_US.utf8/LC_TIME
b6dc3000-b6e9a000 r--p 00000000 03:03 1996406    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6e9a000-b6e9b000 r--p 00000000 03:03 1996424    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6e9b000-b6ea4000 r-xp 00000000 03:03 2326730    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ea4000-b6ea6000 rw-p 00008000 03:03 2326730    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ea6000-b6eae000 r-xp 00000000 03:03 2326732    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eae000-b6eb0000 rw-p 00007000 03:03 2326732    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eb0000-b6eb7000 r-xp 00000000 03:03 2326728    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6eb7000-b6eb9000 rw-p 00006000 03:03 2326728    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6eb9000-b6ebd000 rw-p b6eb9000 00:00 0 
b6ebd000-b6ef3000 r-xp 00000000 03:03 2567279    /lib/libsepol.so.1
b6ef3000-b6ef4000 rw-p 00035000 03:03 2567279    /lib/libsepol.so.1
b6ef4000-b6efe000 rw-p b6ef4000 00:00 0 
b6efe000-b6f01000 r-xp 00000000 03:03 1947160    /usr/lib/libgpg-error.so.0.3.0
b6f01000-b6f02000 rw-p 00002000 03:03 1947160    /usr/lib/libgpg-error.so.0.3.0
b6f02000-b6f51000 r-xp 00000000 03:03 1947174    /usr/lib/libgcrypt.so.11.2.2
b6f51000-b6f53000 rw-p 0004e000 03:03 1947174    /usr/lib/libgcrypt.so.11.2.2
b6f53000-b6f67000 r-xp 00000000 03:03 1947351    /usr/lib/libtasn1.so.3.0.6
b6f67000-b6f68000 rw-p 00013000 03:03 1947351    /usr/lib/libtasn1.so.3.0.6
b6f68000-b6f69000 rw-p b6f68000 00:00 0 
b6f69000-b6f6b000 r-xp 00000000 03:03 2326740    /lib/tls/i686/cmov/libutil-2.5.so
b6f6b000-b6f6d000 rw-p 00001000 03:03 2326740    /lib/tls/i686/cmov/libutil-2.5.so
b6f6d000-b6f81000 r-xp 00000000 03:03 2567286    /lib/libselinux.so.1
b6f81000-b6f83000 rw-p 00013000 03:03 2567286    /lib/libselinux.so.1
b6f83000-b6f92000 r-xp 00000000 03:03 2326736    /lib/tls/i686/cmov/libresolv-2.5.so
b6f92000-b6f94000 rw-p 0000f000 03:03 2326736    /lib/tls/i686/cmov/libresolv-2.5.so
b6f94000-b6f96000 rw-p b6f94000 00:00 0 
b6f96000-b6fa4000 r-xp 00000000 03:03 1947398    /usr/lib/libavahi-client.so.3.2.2
b6fa4000-b6fa5000 rw-p 0000e000 03:03 1947398    /usr/lib/libavahi-client.so.3.2.2
b6fa5000-b6faf000 r-xp 00000000 03:03 1947438    /usr/lib/libavahi-common.so.3.4.3
b6faf000-b6fb0000 rw-p 00009000 03:03 1947438    /usr/lib/libavahi-common.so.3.4.3
b6fb0000-b6fb2000 r-xp 00000000 03:03 1947901    /usr/lib/libavahi-glib.so.1.0.1
b6fb2000-b6fb3000 rw-p 00001000 03:03 1947901    /usr/lib/libavahi-glib.so.1.0.1
b6fb3000-b6fb4000 rw-p b6fb3000 00:00 0 
b6fb4000-b701e000 r-xp 00000000 03:03 1947713    /usr/lib/libgnutls.so.13.0.9
b701e000-b7024000 rw-p 0006a000 03:03 1947713    /usr/lib/libgnutls.so.13.0.9
b7024000-b7046000 r-xp 00000000 03:03 1946116    /usr/lib/libpng12.so.0.15.0
b7046000-b7047000 rw-p 00021000 03:03 1946116    /usr/lib/libpng12.so.0.15.0
b7047000-b7065000 r-xp 00000000 03:03 1947213    /usr/lib/libexpat.so.1.0.0
b7065000-b7067000 rw-p 0001d000 03:03 1947213    /usr/lib/libexpat.so.1.0.0
b7067000-b70cf000 r-xp 00000000 03:03 1947881    /usr/lib/libfreetype.so.6.3.10
b70cf000-b70d2000 rw-p 00068000 03:03 1947881    /usr/lib/libfreetype.so.6.3.10
b70d2000-b70d3000 rw-p b70d2000 00:00 0 
b70d3000-b70e6000 r-xp 00000000 03:03 1948367    /usr/lib/libz.so.1.2.3
b70e6000-b70e7000 rw-p 00012000 03:03 1948367    /usr/lib/libz.so.1.2.3
b70e7000-b70fa000 r-xp 00000000 03:03 2326727    /lib/tls/i686/cmov/libnsl-2.5.so
b70fa000-b70fc000 rw-p 00012000 03:03 2326727    /lib/tls/i686/cmov/libnsl-2.5.so
b70fc000-b70fe000 rw-p b70fc000 00:00 0 
b70fe000-b7102000 r-xp 00000000 03:03 1946534    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7102000-b7103000 rw-p 00003000 03:03 1946534    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7103000-b7107000 r-xp 00000000 03:03 1946702    /usr/lib/libXdmcp.so.6.0.0
b7107000-b7108000 rw-p 00003000 03:03 1946702    /usr/lib/libXdmcp.so.6.0.0
b7108000-b7109000 rw-p b7108000 00:00 0 
b7109000-b7127000 r-xp 00000000 03:03 1947618    /usr/lib/libjpeg.so.62.0.0
b7127000-b7128000 rw-p 0001d000 03:03 1947618    /usr/lib/libjpeg.so.62.0.0
b7128000-b7130000 r-xp 00000000 03:03 1948498    /usr/lib/libstartup-notification-1.so.0.0.0
b7130000-b7131000 rw-p 00007000 03:03 1948498    /usr/lib/libstartup-notification-1.so.0.0.0
b7131000-b7138000 r-xp 00000000 03:03 2326737    /lib/tls/i686/cmov/librt-2.5.so
b7138000-b713a000 rw-p 00006000 03:03 2326737    /lib/tls/i686/cmov/librt-2.5.so
b713a000-b713e000 r-xp 00000000 03:03 1948360    /usr/lib/libgthread-2.0.so.0.1200.11
b713e000-b713f000 rw-p 00003000 03:03 1948360    /usr/lib/libgthread-2.0.so.0.1200.11
b713f000-b7140000 rw-p b713f000 00:00 0 
b7140000-b7142000 r-xp 00000000 03:03 2322759    /lib/tls/i686/cmov/libdl-2.5.so
b7142000-b7144000 rw-p 00001000 03:03 2322759    /lib/tls/i686/cmov/libdl-2.5.so
b7144000-b7146000 r-xp 00000000 03:03 1948358    /usr/lib/libgmodule-2.0.so.0.1200.11
b7146000-b7147000 rw-p 00002000 03:03 1948358    /usr/lib/libgmodule-2.0.so.0.1200.11
b7147000-b719d000 r-xp 00000000 03:03 1947460    /usr/lib/libgnomevfs-2.so.0.1800.1
b719d000-b71a0000 rw-p 00055000 03:03 1947460    /usr/lib/libgnomevfs-2.so.0.1800.1
b71a0000-b720e000 r-xp 00000000 03:03 1946802    /usr/lib/libcairo.so.2.11.1
b720e000-b7210000 rw-p 0006d000 03:03 1946802    /usr/lib/libcairo.so.2.11.1
b7210000-b7214000 r-xp 00000000 03:03 1946904    /usr/lib/libXfixes.so.3.1.0
b7214000-b7215000 rw-p 00003000 03:03 1946904    /usr/lib/libXfixes.so.3.1.0
b7215000-b721d000 r-xp 00000000 03:03 1946909    /usr/lib/libXcursor.so.1.0.2
b721d000-b721e000 rw-p 00007000 03:03 1946909    /usr/lib/libXcursor.so.1.0.2
b721e000-b721f000 rw-p b721e000 00:00 0 
b721f000-b7226000 r-xp 00000000 03:03 1946937    /usr/lib/libXi.so.6.0.0
b7226000-b7227000 rw-p 00006000 03:03 1946937    /usr/lib/libXi.so.6.0.0
b7227000-b7229000 r-xp 00000000 03:03 1947165    /usr/lib/libXinerama.so.1.0.0
b7229000-b722a000 rw-p 00001000 03:03 1947165    /usr/lib/libXinerama.so.1.0.0
b722a000-b7231000 r-xp 00000000 03:03 1946800    /usr/lib/libXrender.so.1.3.0
b7231000-b7232000 rw-p 00006000 03:03 1946800    /usr/lib/libXrender.so.1.3.0
b7232000-b723f000 r-xp 00000000 03:03 1946920    /usr/lib/libXext.so.6.4.0
b723f000-b7240000 rw-p 0000d000 03:03 1946920    /usr/lib/libXext.so.6.4.0
b7240000-b7263000 r-xp 00000000 03:03 1946049    /usr/lib/libfontconfig.so.1.2.0
b7263000-b726b000 rw-p 00023000 03:03 1946049    /usr/lib/libfontconfig.so.1.2.0
b726b000-b7272000 r-xp 00000000 03:03 1946872    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7272000-b7273000 rw-p 00007000 03:03 1946872    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7273000-b7274000 rw-p b7273000 00:00 0 
b7274000-b729e000 r-xp 00000000 03:03 1946873    /usr/lib/libpangoft2-1.0.so.0.1600.2
b729e000-b729f000 rw-p 0002a000 03:03 1946873    /usr/lib/libpangoft2-1.0.so.0.1600.2
b729f000-b72b3000 r-xp 00000000 03:03 1947203    /usr/lib/libart_lgpl_2.so.2.3.17
b72b3000-b72b4000 rw-p 00013000 03:03 1947203    /usr/lib/libart_lgpl_2.so.2.3.17
b72b4000-b72bb000 r-xp 00000000 03:03 2567314    /lib/libpopt.so.0.0.0
b72bb000-b72bc000 rw-p 00006000 03:03 2567314    /lib/libpopt.so.0.0.0
b72bc000-b72e5000 r-xp 00000000 03:03 1945977    /usr/lib/libgnomecanvas-2.so.0.1400.0
b72e5000-b72e6000 rw-p 00029000 03:03 1945977    /usr/lib/libgnomecanvas-2.so.0.1400.0
b72e6000-b7341000 r-xp 00000000 03:03 1947131    /usr/lib/libbonoboui-2.so.0.0.0
b7341000-b7344000 rw-p 0005a000 03:03 1947131    /usr/lib/libbonoboui-2.so.0.0.0
b7344000-b745b000 r-xp 00000000 03:03 1946692    /usr/lib/libxml2.so.2.6.27
b745b000-b7461000 rw-p 00116000 03:03 1946692    /usr/lib/libxml2.so.2.6.27
b7461000-b7462000 rw-p b7461000 00:00 0 
b7462000-b7522000 r-xp 00000000 03:03 1947706    /usr/lib/libasound.so.2.0.0
b7522000-b7527000 rw-p 000bf000 03:03 1947706    /usr/lib/libasound.so.2.0.0
b7527000-b754c000 r-xp 00000000 03:03 2326725    /lib/tls/i686/cmov/libm-2.5.so
b754c000-b754e000 rw-p 00024000 03:03 2326725    /lib/tls/i686/cmov/libm-2.5.so
b754e000-b756e000 r-xp 00000000 03:03 1946717    /usr/lib/libaudiofile.so.0.0.2
b756e000-b7570000 rw-p 00020000 03:03 1946717    /usr/lib/libaudiofile.so.0.0.2
b7570000-b76ab000 r-xp 00000000 03:03 2322656    /lib/tls/i686/cmov/libc-2.5.so
b76ab000-b76ac000 r--p 0013b000 03:03 2322656    /lib/tls/i686/cmov/libc-2.5.so
b76ac000-b76ae000 rw-p 0013c000 03:03 2322656    /lib/tls/i686/cmov/libc-2.5.so
b76ae000-b76b1000 rw-p b76ae000 00:00 0 
b76b1000-b76b8000 r-xp 00000000 03:03 2567337    /lib/libwrap.so.0.7.6
b76b8000-b76b9000 rw-p 00007000 03:03 2567337    /lib/libwrap.so.0.7.6
b76b9000-b774d000 r-xp 00000000 03:03 1948354    /usr/lib/libglib-2.0.so.0.1200.11
b774d000-b774e000 rw-p 00093000 03:03 1948354    /usr/lib/libglib-2.0.so.0.1200.11
b774e000-b774f000 rw-p b774e000 00:00 0 
b774f000-b775b000 r-xp 00000000 03:03 1947527    /usr/lib/libgnome-keyring.so.0.0.1
b775b000-b775c000 rw-p 0000b000 03:03 1947527    /usr/lib/libgnome-keyring.so.0.0.1
b775c000-b7795000 r-xp 00000000 03:03 1948356    /usr/lib/libgobject-2.0.so.0.1200.11
b7795000-b7796000 rw-p 00039000 03:03 1948356    /usr/lib/libgobject-2.0.so.0.1200.11
b7796000-b77c7000 r-xp 00000000 03:03 1946635    /usr/lib/libdbus-1.so.3.2.0
b77c7000-b77c8000 rw-p 00031000 03:03 1946635    /usr/lib/libdbus-1.so.3.2.0
b77c8000-b77e2000 r-xp 00000000 03:03 1947523    /usr/lib/libdbus-glib-1.so.2.1.0
b77e2000-b77e3000 rw-p 0001a000 03:03 1947523    /usr/lib/libdbus-glib-1.so.2.1.0
b77e3000-b77f6000 r-xp 00000000 03:03 2326735    /lib/tls/i686/cmov/libpthread-2.5.so
b77f6000-b77f8000 rw-p 00013000 03:03 2326735    /lib/tls/i686/cmov/libpthread-2.5.so
b77f8000-b77fb000 rw-p b77f8000 00:00 0 
b77fb000-b7844000 r-xp 00000000 03:03 1946435    /usr/lib/libORBit-2.so.0.1.0
b7844000-b784e000 rw-p 00048000 03:03 1946435    /usr/lib/libORBit-2.so.0.1.0
b784e000-b787d000 r-xp 00000000 03:03 1946223    /usr/lib/libgconf-2.so.4.1.2
b787d000-b7880000 rw-p 0002e000 03:03 1946223    /usr/lib/libgconf-2.so.4.1.2
b7880000-b7893000 r-xp 00000000 03:03 1947806    /usr/lib/libbonobo-activation.so.4.0.0
b7893000-b7895000 rw-p 00013000 03:03 1947806    /usr/lib/libbonobo-activation.so.4.0.0
b7895000-b78e7000 r-xp 00000000 03:03 1947219    /usr/lib/libbonobo-2.so.0.0.0
b78e7000-b78f1000 rw-p 00051000 03:03 1947219    /usr/lib/libbonobo-2.so.0.0.0
b78f1000-b79de000 r-xp 00000000 03:03 1946768    /usr/lib/libX11.so.6.2.0
b79de000-b79e2000 rw-p 000ed000 03:03 1946768    /usr/lib/libX11.so.6.2.0
b79e2000-b7a1e000 r-xp 00000000 03:03 1946871    /usr/lib/libpango-1.0.so.0.1600.2
b7a1e000-b7a20000 rw-p 0003b000 03:03 1946871    /usr/lib/libpango-1.0.so.0.1600.2
b7a20000-b7a21000 rw-p b7a20000 00:00 0 
b7a21000-b7a26000 r-xp 00000000 03:03 1947065    /usr/lib/libXrandr.so.2.1.0
b7a26000-b7a27000 rw-p 00005000 03:03 1947065    /usr/lib/libXrandr.so.2.1.0
b7a27000-b7a3d000 r-xp 00000000 03:03 1947491    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a3d000-b7a3e000 rw-p 00015000 03:03 1947491    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a3e000-b7a57000 r-xp 00000000 03:03 1947546    /usr/lib/libatk-1.0.so.0.1809.1
b7a57000-b7a59000 rw-p 00018000 03:03 1947546    /usr/lib/libatk-1.0.so.0.1809.1
b7a59000-b7adc000 r-xp 00000000 03:03 1947492    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7adc000-b7adf000 rw-p 00083000 03:03 1947492    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7adf000-b7e30000 r-xp 00000000 03:03 1947724    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e30000-b7e36000 rw-p 00351000 03:03 1947724    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e36000-b7e37000 rw-p b7e36000 00:00 0 
b7e37000-b7e4b000 r-xp 00000000 03:03 1946166    /usr/lib/libgnome-2.so.0.1800.0
b7e4b000-b7e4c000 rw-p 00014000 03:03 1946166    /usr/lib/libgnome-2.so.0.1800.0
b7e4c000-b7e4d000 rw-p b7e4c000 00:00 0 
b7e4d000-b7e62000 r-xp 00000000 03:03 1946015    /usr/lib/libICE.so.6.3.0
b7e62000-b7e64000 rw-p 00014000 03:03 1946015    /usr/lib/libICE.so.6.3.0
b7e64000-b7e65000 rw-p b7e64000 00:00 0 
b7e65000-b7e6d000 r-xp 00000000 03:03 1946092    /usr/lib/libSM.so.6.0.0
b7e6d000-b7e6e000 rw-p 00007000 03:03 1946092    /usr/lib/libSM.so.6.0.0
b7e6e000-b7ef8000 r-xp 00000000 03:03 1947534    /usr/lib/libgnomeui-2.so.0.1788.4
b7ef8000-b7efc000 rw-p 00089000 03:03 1947534    /usr/lib/libgnomeui-2.so.0.1788.4
b7efc000-b7f10000 r-xp 00000000 03:03 1946549    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f10000-b7f11000 rw-p 00014000 03:03 1946549    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f11000-b7f1a000 r-xp 00000000 03:03 1946308    /usr/lib/libesd.so.0.2.36
b7f1a000-b7f1b000 rw-p 00009000 03:03 1946308    /usr/lib/libesd.so.0.2.36
b7f1b000-b7f1d000 r-xp 00000000 03:03 1946478    /usr/lib/libXau.so.6.0.0
b7f1d000-b7f1e000 rw-p 00001000 03:03 1946478    /usr/lib/libXau.so.6.0.0
b7f1e000-b7f1f000 rw-p b7f1e000 00:00 0 
b7f1f000-b7f20000 r--p 00000000 03:03 2011370    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f20000-b7f21000 r--p 00000000 03:03 1996523    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f21000-b7f22000 r--p 00000000 03:03 1996425    /usr/lib/locale/en_US.utf8/LC_NAME
b7f22000-b7f23000 r--p 00000000 03:03 1996426    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f23000-b7f24000 r--p 00000000 03:03 1996427    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f24000-b7f25000 r--p 00000000 03:03 1996428    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f25000-b7f2c000 r--s 00000000 03:03 1962790    /usr/lib/gconv/gconv-modules.cache
b7f2c000-b7f2d000 r--p 00000000 03:03 1996429    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f2d000-b7f2e000 rw-p b7f2d000 00:00 0 
b7f2e000-b7f47000 r-xp 00000000 03:03 49062      /lib/ld-2.5.so
b7f47000-b7f49000 rw-p 00019000 03:03 49062      /lib/ld-2.5.so
bf86a000-bf880000 rw-p bf86a000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(evolution-alarm-notify:7137): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:7144): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 50494 1179446400 1179395906
evolution-alarm-notify-Message:  Fri May 18 03:00:00 2007

evolution-alarm-notify-Message:  Thu May 17 12:58:26 2007


(update-notifier:7129): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

---

### Post by Gramlengo on 2007-05-17
Update: I removed Update-Notifier package using Syneptic and problem solved, still ahve no idea what the hell that was.
Whenever I re-install update-notifier crashes resume.

---

### Post by Nikos.Alexandris on 2007-06-05
I have a similar issue the last 4 days!

[http://ubuntuforums.org/showthread.php?p=2785250#post2785250](http://ubuntuforums.org/showthread.php?p=2785250#post2785250)

And in another thread somebody is reporting "Strange 10 Seconds Login Error"

[http://ubuntuforums.org/showthread.php?t=453715&highlight=Fontconfig+error](http://ubuntuforums.org/showthread.php?t=453715&highlight=Fontconfig+error)

Anybody knows what this is?

Does it have to do with ati's new driver's or with 3D acceleration at all?

---

