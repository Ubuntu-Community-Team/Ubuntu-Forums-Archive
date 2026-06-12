---
title: "Login problems"
date: 2007-09-15
forum: General Help
---

### Post by razumny on 2007-09-15
I have got a problem;

I am running Ubuntu Feisty.

When I log in to m computer, it immediately logs off, and I go back to the login screen. When I log in again, I get an errormessage saying "Your sesion only lasted less than 10 seconds" When I press the "OK" button, I am immediately thrown out of the logged in session.

I viewed the details from the ~/.xsession-errors file, and here's what it said:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "wiseguy"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/wisebuntu:/tmp/.ICE-unix/5871
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x081f1608 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb768e6fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb768f60e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77a52c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b3bdb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7b3d1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7b40f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7b411c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7b4127f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7df6440]
/usr/bin/gnome-session[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb779e3c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb779ddf2]
/usr/lib/libglib-2.0.so.0[0xb77a0dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb77a1335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb77c740d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb779ddf2]
/usr/lib/libglib-2.0.so.0[0xb77a0dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb77a1179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cd6044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb763bebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:01 6406596    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:01 6406596    /usr/bin/gnome-session
08069000-08221000 rw-p 08069000 00:00 0          [heap]
b5a00000-b5a21000 rw-p b5a00000 00:00 0 
b5a21000-b5b00000 ---p b5a21000 00:00 0 
b5b28000-b5b33000 r-xp 00000000 08:01 4931648    /lib/libgcc_s.so.1
b5b33000-b5b34000 rw-p 0000a000 08:01 4931648    /lib/libgcc_s.so.1
b5b43000-b5ba3000 rw-s 00000000 00:08 1212420    /SYSV00000000 (deleted)
b5ba3000-b5ba4000 ---p b5ba3000 00:00 0 
b5ba4000-b63a4000 rw-p b5ba4000 00:00 0 
b63a4000-b6421000 r--p 00000000 08:01 6604857    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6421000-b6423000 r-xp 00000000 08:01 6472302    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6423000-b6424000 rw-p 00001000 08:01 6472302    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6424000-b642a000 r--s 00000000 08:01 3735644    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b642a000-b642b000 r--s 00000000 08:01 3736097    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b642b000-b642e000 r--s 00000000 08:01 3736096    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b642e000-b642f000 r--s 00000000 08:01 3736095    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b642f000-b6430000 r--s 00000000 08:01 3736094    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6430000-b6434000 r--s 00000000 08:01 3735641    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6434000-b6435000 r--s 00000000 08:01 3736092    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6435000-b6437000 r--s 00000000 08:01 3736091    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6437000-b6439000 r--s 00000000 08:01 3736090    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6439000-b643a000 r--s 00000000 08:01 3736089    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b643a000-b643c000 r--s 00000000 08:01 3736088    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b643c000-b6442000 r--s 00000000 08:01 3736087    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6442000-b6444000 r--s 00000000 08:01 3736086    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6444000-b6446000 r--s 00000000 08:01 3736085    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6446000-b644e000 r--s 00000000 08:01 3736084    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b644e000-b6454000 r--s 00000000 08:01 3736083    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6454000-b6455000 r--s 00000000 08:01 3736082    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6455000-b646c000 r--s 00000000 08:01 3735660    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b646c000-b646e000 r--s 00000000 08:01 3736081    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b646e000-b6474000 r--s 00000000 08:01 3736080    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6474000-b6477000 r--s 00000000 08:01 3736079    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b6477000-b647b000 r--s 00000000 08:01 3735626    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b647b000-b647d000 r--s 00000000 08:01 3736076    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b647d000-b647e000 r--s 00000000 08:01 3736126    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b647e000-b647f000 r--s 00000000 08:01 3736125    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b647f000-b6480000 r--s 00000000 08:01 3736124    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b6480000-b6481000 r--s 00000000 08:01 3736123    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b6481000-b6482000 r--s 00000000 08:01 3736069    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6482000-b6485000 r--s 00000000 08:01 3736121    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6485000-b648a000 r--s 00000000 08:01 3736068    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b648a000-b648c000 r--s 00000000 08:01 3736119    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b648c000-b648d000 r--s 00000000 08:01 3736118    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b648d000-b648f000 r--s 00000000 08:01 3736117    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b648f000-b6490000 r--s 00000000 08:01 3736116    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6490000-b6495000 r--s 00000000 08:01 3736115    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6495000-b6499000 r--s 00000000 08:01 3736114    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6499000-b649b000 r--s 00000000 08:01 3736113    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b649b000-b649e000 r--s 00000000 08:01 3736112    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b649e000-b649f000 r--s 00000000 08:01 3736111    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b649f000-b64a1000 r--s 00000000 08:01 3736110    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b64a1000-b64a5000 r--s 00000000 08:01 3736066    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b64a5000-b64ab000 r--s 00000000 08:01 3736108    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b64ab000-b64ac000 r--s 00000000 08:01 3736107    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b64ac000-b64b4000 r--s 00000000 08:01 3736106    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b64b4000-b669b000 r--p 00000000 08:01 6701968    /usr/share/icons/hicolor/icon-theme.cache
b669b000-b6d42000 r--p 00000000 08:01 6705412    /usr/share/icons/gnome/icon-theme.cache
b6d42000-b6d5e000 r-xp 00000000 08:01 6455650    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d5e000-b6d5f000 rw-p 0001b000 08:01 6455650    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6d5f000-b6dbf000 rw-s 00000000 00:08 1179651    /SYSV00000000 (deleted)
b6dbf000-b6e0c000 rw-p b6dbf000 00:00 0 
b6e0c000-b6e13000 r-xp 00000000 08:01 6407618    /usr/lib/libfam.so.0.0.0
b6e13000-b6e14000 rw-p 00006000 08:01 6407618    /usr/lib/libfam.so.0.0.0
b6e14000-b6e1a000 r-xp 00000000 08:01 4931611    /lib/libacl.so.1.1.0
b6e1a000-b6e1b000 rw-p 00005000 08:01 4931611    /lib/libacl.so.1.1.0
b6e1b000-b6e1e000 r-xp 00000000 08:01 4931615    /lib/libattr.so.1.1.0
b6e1e000-b6e1f000 rw-p 00002000 08:01 4931615    /lib/libattr.so.1.1.0
b6e1f000-b6e21000 r--s 00000000 08:01 3736065    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6e21000-b6e24000 r--s 00000000 08:01 3736104    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6e24000-b6e26000 r--s 00000000 08:01 3736063    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6e26000-b6e28000 r--s 00000000 08:01 3736101    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6e28000-b6e2c000 r-xp 00000000 08:01 6455685    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e2c000-b6e2d000 rw-p 00003000 08:01 6455685    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6e2e000-b6e3a000 r-xp 00000000 08:01 6455608    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e3a000-b6e3b000 rw-p 0000b000 08:01 6455608    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6e3b000-b6e3c000 r-xp 00000000 08:01 1376438    /usr/lib/gconv/ISO8859-1.so
b6e3c000-b6e3e000 rw-p 00000000 08:01 1376438    /usr/lib/gconv/ISO8859-1.so
b6e3e000-b6e79000 r--p 00000000 08:01 6456611    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e79000-b6e7a000 r--p 00000000 08:01 6456616    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6e7a000-b6e7b000 r--p 00000000 08:01 6456619    /usr/lib/locale/en_US.utf8/LC_TIME
b6e7b000-b6f52000 r--p 00000000 08:01 6456610    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6f52000-b6f5b000 r-xp 00000000 08:01 4965651    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f5b000-b6f5d000 rw-p 00008000 08:01 4965651    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f5d000-b6f65000 r-xp 00000000 08:01 4965655    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f65000-b6f67000 rw-p 00007000 08:01 4965655    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f67000-b6f6e000 r-xp 00000000 08:01 4965647    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f6e000-b6f70000 rw-p 00006000 08:01 4965647    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f70000-b6f73000 rw-p b6f70000 00:00 0 
b6f73000-b6fa9000 r-xp 00000000 08:01 4931702    /lib/libsepol.so.1
b6fa9000-b6faa000 rw-p 00035000 08:01 4931702    /lib/libsepol.so.1
b6faa000-b6fb4000 rw-p b6faa000 00:00 0 
b6fb4000-b6fb7000 r-xp 00000000 08:01 6407771    /usr/lib/libgpg-error.so.0.3.0
b6fb7000-b6fb8000 rw-p 00002000 08:01 6407771    /usr/lib/libgpg-error.so.0.3.0
b6fb8000-b7007000 r-xp 00000000 08:01 6407659    /usr/lib/libgcrypt.so.11.2.2
b7007000-b7009000 rw-p 0004e000 08:01 6407659    /usr/lib/libgcrypt.so.11.2.2
b7009000-b700a000 rw-p b7009000 00:00 0 
b700a000-b701e000 r-xp 00000000 08:01 6408115    /usr/lib/libtasn1.so.3.0.6
b701e000-b701f000 rw-p 00013000 08:01 6408115    /usr/lib/libtasn1.so.3.0.6
b701f000-b7021000 r-xp 00000000 08:01 4965668    /lib/tls/i686/cmov/libutil-2.5.so
b7021000-b7023000 rw-p 00001000 08:01 4965668    /lib/tls/i686/cmov/libutil-2.5.so
b7023000-b7037000 r-xp 00000000 08:01 4931701    /lib/libselinux.so.1
b7037000-b7039000 rw-p 00013000 08:01 4931701    /lib/libselinux.so.1
b7039000-b7048000 r-xp 00000000 08:01 4965662    /lib/tls/i686/cmov/libresolv-2.5.so
b7048000-b704a000 rw-p 0000f000 08:01 4965662    /lib/tls/i686/cmov/libresolv-2.5.so
b704a000-b704c000 rw-p b704a000 00:00 0 
b704c000-b705a000 r-xp 00000000 08:01 6407497    /usr/lib/libavahi-client.so.3.2.2
b705a000-b705b000 rw-p 0000e000 08:01 6407497    /usr/lib/libavahi-client.so.3.2.2
b705b000-b705c000 rw-p b705b000 00:00 0 
b705c000-b7066000 r-xp 00000000 08:01 6407499    /usr/lib/libavahi-common.so.3.4.3
b7066000-b7067000 rw-p 00009000 08:01 6407499    /usr/lib/libavahi-common.so.3.4.3
b7067000-b7069000 r-xp 00000000 08:01 6407503    /usr/lib/libavahi-glib.so.1.0.1
b7069000-b706a000 rw-p 00001000 08:01 6407503    /usr/lib/libavahi-glib.so.1.0.1
b706a000-b70d4000 r-xp 00000000 08:01 6407767    /usr/lib/libgnutls.so.13.0.9
b70d4000-b70da000 rw-p 0006a000 08:01 6407767    /usr/lib/libgnutls.so.13.0.9
b70da000-b70fc000 r-xp 00000000 08:01 6407691    /usr/lib/libpng12.so.0.15.0
b70fc000-b70fd000 rw-p 00021000 08:01 6407691    /usr/lib/libpng12.so.0.15.0
b70fd000-b711b000 r-xp 00000000 08:01 6407614    /usr/lib/libexpat.so.1.0.0
b711b000-b711d000 rw-p 0001d000 08:01 6407614    /usr/lib/libexpat.so.1.0.0
b711d000-b711e000 rw-p b711d000 00:00 0 
b711e000-b7186000 r-xp 00000000 08:01 6407491    /usr/lib/libfreetype.so.6.3.10
b7186000-b7189000 rw-p 00068000 08:01 6407491    /usr/lib/libfreetype.so.6.3.10
b7189000-b719c000 r-xp 00000000 08:01 6408173    /usr/lib/libz.so.1.2.3
b719c000-b719d000 rw-p 00012000 08:01 6408173    /usr/lib/libz.so.1.2.3
b719d000-b71b0000 r-xp 00000000 08:01 4965645    /lib/tls/i686/cmov/libnsl-2.5.so
b71b0000-b71b2000 rw-p 00012000 08:01 4965645    /lib/tls/i686/cmov/libnsl-2.5.so
b71b2000-b71b4000 rw-p b71b2000 00:00 0 
b71b4000-b71b8000 r-xp 00000000 08:01 6407404    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71b8000-b71b9000 rw-p 00003000 08:01 6407404    /usr/lib/libORBitCosNaming-2.so.0.1.0
b71b9000-b71ba000 rw-p b71b9000 00:00 0 
b71ba000-b71be000 r-xp 00000000 08:01 6407429    /usr/lib/libXdmcp.so.6.0.0
b71be000-b71bf000 rw-p 00003000 08:01 6407429    /usr/lib/libXdmcp.so.6.0.0
b71bf000-b71dd000 r-xp 00000000 08:01 6407896    /usr/lib/libjpeg.so.62.0.0
b71dd000-b71de000 rw-p 0001d000 08:01 6407896    /usr/lib/libjpeg.so.62.0.0
b71de000-b71e6000 r-xp 00000000 08:01 6408105    /usr/lib/libstartup-notification-1.so.0.0.0
b71e6000-b71e7000 rw-p 00007000 08:01 6408105    /usr/lib/libstartup-notification-1.so.0.0.0
b71e7000-b71e8000 rw-p b71e7000 00:00 0 
b71e8000-b71ef000 r-xp 00000000 08:01 4965664    /lib/tls/i686/cmov/librt-2.5.so
b71ef000-b71f1000 rw-p 00006000 08:01 4965664    /lib/tls/i686/cmov/librt-2.5.so
b71f1000-b71f5000 r-xp 00000000 08:01 6407823    /usr/lib/libgthread-2.0.so.0.1200.11
b71f5000-b71f6000 rw-p 00003000 08:01 6407823    /usr/lib/libgthread-2.0.so.0.1200.11
b71f6000-b71f8000 r-xp 00000000 08:01 4965640    /lib/tls/i686/cmov/libdl-2.5.so
b71f8000-b71fa000 rw-p 00001000 08:01 4965640    /lib/tls/i686/cmov/libdl-2.5.so
b71fa000-b71fc000 r-xp 00000000 08:01 6407725    /usr/lib/libgmodule-2.0.so.0.1200.11
b71fc000-b71fd000 rw-p 00002000 08:01 6407725    /usr/lib/libgmodule-2.0.so.0.1200.11
b71fd000-b7253000 r-xp 00000000 08:01 6407759    /usr/lib/libgnomevfs-2.so.0.1800.1
b7253000-b7256000 rw-p 00055000 08:01 6407759    /usr/lib/libgnomevfs-2.so.0.1800.1
b7256000-b72c4000 r-xp 00000000 08:01 6407522    /usr/lib/libcairo.so.2.11.1
b72c4000-b72c6000 rw-p 0006d000 08:01 6407522    /usr/lib/libcairo.so.2.11.1
b72c6000-b72c7000 rw-p b72c6000 00:00 0 
b72c7000-b72cb000 r-xp 00000000 08:01 6407435    /usr/lib/libXfixes.so.3.1.0
b72cb000-b72cc000 rw-p 00003000 08:01 6407435    /usr/lib/libXfixes.so.3.1.0
b72cc000-b72d4000 r-xp 00000000 08:01 6407425    /usr/lib/libXcursor.so.1.0.2
b72d4000-b72d5000 rw-p 00007000 08:01 6407425    /usr/lib/libXcursor.so.1.0.2
b72d5000-b72dc000 r-xp 00000000 08:01 6407441    /usr/lib/libXi.so.6.0.0
b72dc000-b72dd000 rw-p 00006000 08:01 6407441    /usr/lib/libXi.so.6.0.0
b72dd000-b72df000 r-xp 00000000 08:01 6407443    /usr/lib/libXinerama.so.1.0.0
b72df000-b72e0000 rw-p 00001000 08:01 6407443    /usr/lib/libXinerama.so.1.0.0
b72e0000-b72e7000 r-xp 00000000 08:01 6407455    /usr/lib/libXrender.so.1.3.0
b72e7000-b72e8000 rw-p 00006000 08:01 6407455    /usr/lib/libXrender.so.1.3.0
b72e8000-b72f5000 r-xp 00000000 08:01 6407433    /usr/lib/libXext.so.6.4.0
b72f5000-b72f6000 rw-p 0000d000 08:01 6407433    /usr/lib/libXext.so.6.4.0
b72f6000-b72f7000 rw-p b72f6000 00:00 0 
b72f7000-b731a000 r-xp 00000000 08:01 6407620    /usr/lib/libfontconfig.so.1.2.0
b731a000-b7322000 rw-p 00023000 08:01 6407620    /usr/lib/libfontconfig.so.1.2.0
b7322000-b7329000 r-xp 00000000 08:01 6408004    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7329000-b732a000 rw-p 00007000 08:01 6408004    /usr/lib/libpangocairo-1.0.so.0.1600.2
b732a000-b7354000 r-xp 00000000 08:01 6408006    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7354000-b7355000 rw-p 0002a000 08:01 6408006    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7355000-b7369000 r-xp 00000000 08:01 6407481    /usr/lib/libart_lgpl_2.so.2.3.17
b7369000-b736a000 rw-p 00013000 08:01 6407481    /usr/lib/libart_lgpl_2.so.2.3.17
b736a000-b7371000 r-xp 00000000 08:01 4931691    /lib/libpopt.so.0.0.0
b7371000-b7372000 rw-p 00006000 08:01 4931691    /lib/libpopt.so.0.0.0
b7372000-b739b000 r-xp 00000000 08:01 6407741    /usr/lib/libgnomecanvas-2.so.0.1400.0
b739b000-b739c000 rw-p 00029000 08:01 6407741    /usr/lib/libgnomecanvas-2.so.0.1400.0
b739c000-b739d000 rw-p b739c000 00:00 0 
b739d000-b73f8000 r-xp 00000000 08:01 6407518    /usr/lib/libbonoboui-2.so.0.0.0
b73f8000-b73fb000 rw-p 0005a000 08:01 6407518    /usr/lib/libbonoboui-2.so.0.0.0
b73fb000-b7512000 r-xp 00000000 08:01 6408167    /usr/lib/libxml2.so.2.6.27
b7512000-b7518000 rw-p 00116000 08:01 6408167    /usr/lib/libxml2.so.2.6.27
b7518000-b75d8000 r-xp 00000000 08:01 6407483    /usr/lib/libasound.so.2.0.0
b75d8000-b75dd000 rw-p 000bf000 08:01 6407483    /usr/lib/libasound.so.2.0.0
b75dd000-b7602000 r-xp 00000000 08:01 4965642    /lib/tls/i686/cmov/libm-2.5.so
b7602000-b7604000 rw-p 00024000 08:01 4965642    /lib/tls/i686/cmov/libm-2.5.so
b7604000-b7624000 r-xp 00000000 08:01 6407495    /usr/lib/libaudiofile.so.0.0.2
b7624000-b7626000 rw-p 00020000 08:01 6407495    /usr/lib/libaudiofile.so.0.0.2
b7626000-b7761000 r-xp 00000000 08:01 4965634    /lib/tls/i686/cmov/libc-2.5.so
b7761000-b7762000 r--p 0013b000 08:01 4965634    /lib/tls/i686/cmov/libc-2.5.so
b7762000-b7764000 rw-p 0013c000 08:01 4965634    /lib/tls/i686/cmov/libc-2.5.so
b7764000-b7768000 rw-p b7764000 00:00 0 
b7768000-b776f000 r-xp 00000000 08:01 4931897    /lib/libwrap.so.0.7.6
b776f000-b7770000 rw-p 00007000 08:01 4931897    /lib/libwrap.so.0.7.6
b7770000-b7804000 r-xp 00000000 08:01 6407715    /usr/lib/libglib-2.0.so.0.1200.11
b7804000-b7805000 rw-p 00093000 08:01 6407715    /usr/lib/libglib-2.0.so.0.1200.11
b7805000-b7811000 r-xp 00000000 08:01 6407731    /usr/lib/libgnome-keyring.so.0.0.1
b7811000-b7812000 rw-p 0000b000 08:01 6407731    /usr/lib/libgnome-keyring.so.0.0.1
b7812000-b784b000 r-xp 00000000 08:01 6407769    /usr/lib/libgobject-2.0.so.0.1200.11
b784b000-b784c000 rw-p 00039000 08:01 6407769    /usr/lib/libgobject-2.0.so.0.1200.11
b784c000-b787e000 r-xp 00000000 08:01 6406889    /usr/lib/libdbus-1.so.3.2.0
b787e000-b787f000 rw-p 00031000 08:01 6406889    /usr/lib/libdbus-1.so.3.2.0
b787f000-b7899000 r-xp 00000000 08:01 6407558    /usr/lib/libdbus-glib-1.so.2.1.0
b7899000-b789a000 rw-p 0001a000 08:01 6407558    /usr/lib/libdbus-glib-1.so.2.1.0
b789a000-b789b000 rw-p b789a000 00:00 0 
b789b000-b78ae000 r-xp 00000000 08:01 4965660    /lib/tls/i686/cmov/libpthread-2.5.so
b78ae000-b78b0000 rw-p 00013000 08:01 4965660    /lib/tls/i686/cmov/libpthread-2.5.so
b78b0000-b78b2000 rw-p b78b0000 00:00 0 
b78b2000-b78fb000 r-xp 00000000 08:01 6407400    /usr/lib/libORBit-2.so.0.1.0
b78fb000-b7905000 rw-p 00048000 08:01 6407400    /usr/lib/libORBit-2.so.0.1.0
b7905000-b7934000 r-xp 00000000 08:01 6407657    /usr/lib/libgconf-2.so.4.1.2
b7934000-b7937000 rw-p 0002e000 08:01 6407657    /usr/lib/libgconf-2.so.4.1.2
b7937000-b794a000 r-xp 00000000 08:01 6407516    /usr/lib/libbonobo-activation.so.4.0.0
b794a000-b794c000 rw-p 00013000 08:01 6407516    /usr/lib/libbonobo-activation.so.4.0.0
b794c000-b799e000 r-xp 00000000 08:01 6407514    /usr/lib/libbonobo-2.so.0.0.0
b799e000-b79a8000 rw-p 00051000 08:01 6407514    /usr/lib/libbonobo-2.so.0.0.0
b79a8000-b79a9000 rw-p b79a8000 00:00 0 
b79a9000-b7a96000 r-xp 00000000 08:01 6407412    /usr/lib/libX11.so.6.2.0
b7a96000-b7a9a000 rw-p 000ed000 08:01 6407412    /usr/lib/libX11.so.6.2.0
b7a9a000-b7ad6000 r-xp 00000000 08:01 6408002    /usr/lib/libpango-1.0.so.0.1600.2
b7ad6000-b7ad8000 rw-p 0003b000 08:01 6408002    /usr/lib/libpango-1.0.so.0.1600.2
b7ad8000-b7add000 r-xp 00000000 08:01 6407453    /usr/lib/libXrandr.so.2.1.0
b7add000-b7ade000 rw-p 00005000 08:01 6407453    /usr/lib/libXrandr.so.2.1.0
b7ade000-b7af4000 r-xp 00000000 08:01 6407679    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7af4000-b7af5000 rw-p 00015000 08:01 6407679    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7af5000-b7b0e000 r-xp 00000000 08:01 6407489    /usr/lib/libatk-1.0.so.0.1809.1
b7b0e000-b7b10000 rw-p 00018000 08:01 6407489    /usr/lib/libatk-1.0.so.0.1809.1
b7b10000-b7b93000 r-xp 00000000 08:01 6407677    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b93000-b7b96000 rw-p 00083000 08:01 6407677    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b96000-b7b97000 rw-p b7b96000 00:00 0 
b7b97000-b7ee8000 r-xp 00000000 08:01 6407826    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ee8000-b7eee000 rw-p 00351000 08:01 6407826    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7eee000-b7eef000 rw-p b7eee000 00:00 0 
b7eef000-b7f03000 r-xp 00000000 08:01 6407727    /usr/lib/libgnome-2.so.0.1800.0
b7f03000-b7f04000 rw-p 00014000 08:01 6407727    /usr/lib/libgnome-2.so.0.1800.0
b7f04000-b7f19000 r-xp 00000000 08:01 6407390    /usr/lib/libICE.so.6.3.0
b7f19000-b7f1b000 rw-p 00014000 08:01 6407390    /usr/lib/libICE.so.6.3.0
b7f1b000-b7f1c000 rw-p b7f1b000 00:00 0 
b7f1c000-b7f24000 r-xp 00000000 08:01 6407408    /usr/lib/libSM.so.6.0.0
b7f24000-b7f25000 rw-p 00007000 08:01 6407408    /usr/lib/libSM.so.6.0.0
b7f25000-b7faf000 r-xp 00000000 08:01 6407757    /usr/lib/libgnomeui-2.so.0.1788.4
b7faf000-b7fb3000 rw-p 00089000 08:01 6407757    /usr/lib/libgnomeui-2.so.0.1788.4
b7fb3000-b7fc7000 r-xp 00000000 08:01 6407729    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fc7000-b7fc8000 rw-p 00014000 08:01 6407729    /usr/lib/libgnome-desktop-2.so.2.3.5
b7fc8000-b7fc9000 rw-p b7fc8000 00:00 0 
b7fc9000-b7fd2000 r-xp 00000000 08:01 6407605    /usr/lib/libesd.so.0.2.36
b7fd2000-b7fd3000 rw-p 00009000 08:01 6407605    /usr/lib/libesd.so.0.2.36
b7fd3000-b7fd5000 r-xp 00000000 08:01 6407418    /usr/lib/libXau.so.6.0.0
b7fd5000-b7fd6000 rw-p 00001000 08:01 6407418    /usr/lib/libXau.so.6.0.0
b7fd6000-b7fd7000 r--p 00000000 08:01 6456614    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fd7000-b7fd8000 r--p 00000000 08:01 6471726    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fd8000-b7fd9000 r--p 00000000 08:01 6456617    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fd9000-b7fda000 r--p 00000000 08:01 6456615    /usr/lib/locale/en_US.utf8/LC_NAME
b7fda000-b7fdb000 r--p 00000000 08:01 6456609    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fdb000-b7fdc000 r--p 00000000 08:01 6456618    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fdc000-b7fdd000 r--p 00000000 08:01 6456613    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fdd000-b7fe4000 r--s 00000000 08:01 1376491    /usr/lib/gconv/gconv-modules.cache
b7fe4000-b7fe5000 r--p 00000000 08:01 6456612    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fe5000-b7fe7000 rw-p b7fe5000 00:00 0 
b7fe7000-b8000000 r-xp 00000000 08:01 4931605    /lib/ld-2.5.so
b8000000-b8002000 rw-p 00019000 08:01 4931605    /lib/ld-2.5.so
bfa05000-bfa1a000 rw-p bfa05000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(update-notifier:5958): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:5957): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

I recently made  change to the sessions module; I added an automatic startup for GAIM. GAIM does start up fine.

At times I have also received errormessages concerning Nautilus, but I can't reproduce that now.

I can't gain access to the sessions module, so I am unable to edit it.

I have tried to change the session in the login window, but no such luck I'm afraid.

Does anyone have any tips?

---

### Post by razumny on 2007-09-15
More info:

The Nautilus error message is as follows:

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.


The session error message goes as follows:

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

---

### Post by por100pre1 on 2007-09-15
Try this:

Crtl+Alt+F1. Everything will go dark

login with your username and password

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

```
sudo nano /etc/X11/xorg.conf
```

At the end of the **Section "InputDevice"** add this line above the **EndSection** line:

```
Option "SHMConfig" "true"
```

**(Be sure to use the Tab key instead of space to align that! Don't use space!)**

Press Ctrl+LetterO to save and Ctrl+X to exit.

```
sudo startx
``` or ```
sudo reboot
```

If that doesn't work, put everything back together:

Crtl+Alt+F1. Everything will go dark

login with your username and password

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

```
sudo reboot
```

Hope this helps. :)

---

### Post by razumny on 2007-09-15
Tried that just now; didn't work, unfortunately

Still, thanks for a lucid and simple guide

---

### Post by razumny on 2007-09-15
Also, what was i supposed to achieve; i.e., what was I trying to do with this?

---

### Post by por100pre1 on 2007-09-15
In the error log you showed us:

> Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
GSynaptics couldn't initialize.
**You have to set 'SHMConfig' 'true' in Xorg.conf **or XFree86.conf to use GSynaptics

So I basically showed you how to do so. Sorry it didn't worked. :(

---

### Post by razumny on 2007-09-16
So, at this point, I am more or less at a loss for what to do; and am seriously considering reinstalling Ubuntu.

Luckily, I am able to extract all my files from the computer before I do this, so I should be fine. Still though, kinda annoying to have to do so.

Anyone have any good tips for things to try?

---

### Post by razumny on 2007-09-16
OK, I can't be arsed trying to solve this any more; I'm reinstalling the computer

---

### Post by razumny on 2007-09-17
Reinstalled - works fine

Case closed

---

