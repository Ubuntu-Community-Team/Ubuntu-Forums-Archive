---
title: "Ten second session..."
date: 2007-05-02
forum: General Help
---

### Post by charish2k1 on 2007-05-02
Using Ubuntu 7.04 (Feisty) for starters.

I'd changed my startup under System -> Preferences -> Sessions and added gDesklets and Beryl to it. After logging out and logging it to see if it'd work, I got that ten second session message:

**Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.**

The details from the error file:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "charish"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/charish-desktop:/tmp/.ICE-unix/14132
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Initializing gnome-mount extension
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x08204898 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75f16fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb75f260e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77082c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7a9ddb0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7a9f1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7aa2f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7aa31c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7aa327f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7d58440]
/usr/bin/gnome-session[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb77013c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7700df2]
/usr/lib/libglib-2.0.so.0[0xb7703dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7704179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c38044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb759eebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 03:06 5538244    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 03:06 5538244    /usr/bin/gnome-session
08069000-0822d000 rw-p 08069000 00:00 0          [heap]
b5500000-b5521000 rw-p b5500000 00:00 0 
b5521000-b5600000 ---p b5521000 00:00 0 
b5620000-b562b000 r-xp 00000000 03:06 4587584    /lib/libgcc_s.so.1
b562b000-b562c000 rw-p 0000a000 03:06 4587584    /lib/libgcc_s.so.1
b563b000-b563c000 ---p b563b000 00:00 0 
b563c000-b5e3c000 rw-p b563c000 00:00 0 
b5e3c000-b5eb9000 r--p 00000000 03:06 5783702    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5eb9000-b5ebb000 r-xp 00000000 03:06 5670075    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5ebb000-b5ebc000 rw-p 00001000 03:06 5670075    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5ebc000-b5ebf000 r--s 00000000 03:06 7313489    /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b5ebf000-b5ec2000 r--s 00000000 03:06 7313488    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b5ec2000-b5ec8000 r--s 00000000 03:06 7313480    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5ec8000-b5ecb000 r--s 00000000 03:06 7313478    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b5ecb000-b5ecc000 r--s 00000000 03:06 7313476    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b5ecc000-b5ecf000 r--s 00000000 03:06 7313475    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5ecf000-b5ed0000 r--s 00000000 03:06 7313474    /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b5ed0000-b5ed1000 r--s 00000000 03:06 7313473    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5ed1000-b5ed2000 r--s 00000000 03:06 7313472    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5ed2000-b5ed6000 r--s 00000000 03:06 7313471    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5ed6000-b5ef1000 r--s 00000000 03:06 7313407    /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b5ef1000-b5f0d000 r--s 00000000 03:06 7313406    /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b5f0d000-b5f2b000 r--s 00000000 03:06 7313405    /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b5f2b000-b5f2c000 r--s 00000000 03:06 7313403    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5f2c000-b5f2e000 r--s 00000000 03:06 7313370    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b5f2e000-b5f30000 r--s 00000000 03:06 7313369    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b5f30000-b5f31000 r--s 00000000 03:06 7313368    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5f31000-b5f32000 r--s 00000000 03:06 7313367    /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b5f32000-b5f34000 r--s 00000000 03:06 7313366    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b5f34000-b5f3a000 r--s 00000000 03:06 7313361    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5f3a000-b5f3c000 r--s 00000000 03:06 7313271    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5f3c000-b5f3e000 r--s 00000000 03:06 7313270    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b5f3e000-b5f46000 r--s 00000000 03:06 7313269    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5f46000-b5f4c000 r--s 00000000 03:06 7313268    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5f4c000-b5f4d000 r--s 00000000 03:06 7313267    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5f4d000-b5f64000 r--s 00000000 03:06 7313266    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5f64000-b5f66000 r--s 00000000 03:06 7313264    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5f66000-b5f6c000 r--s 00000000 03:06 7313262    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5f6c000-b5f70000 r--s 00000000 03:06 7313234    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b5f70000-b5f73000 r--s 00000000 03:06 7313175    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b5f73000-b5f77000 r--s 00000000 03:06 7313174    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5f77000-b5f7e000 r--s 00000000 03:06 7313118    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5f7e000-b5f7f000 r--s 00000000 03:06 7313265    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b5f7f000-b5f80000 r--s 00000000 03:06 7313470    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5f80000-b5f81000 r--s 00000000 03:06 7313487    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5f81000-b5f82000 r--s 00000000 03:06 7313486    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b5f82000-b5f83000 r--s 00000000 03:06 7313485    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b5f83000-b5f86000 r--s 00000000 03:06 7307350    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b5f86000-b5f8a000 r--s 00000000 03:06 7313362    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5f8a000-b5f93000 r--s 00000000 03:06 7313484    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b5f93000-b5f95000 r--s 00000000 03:06 7313363    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b5f95000-b5f96000 r--s 00000000 03:06 7313467    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b5f96000-b5f98000 r--s 00000000 03:06 7313483    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5f98000-b5f99000 r--s 00000000 03:06 7313263    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5f99000-b5f9e000 r--s 00000000 03:06 7313482    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5f9e000-b5fa2000 r--s 00000000 03:06 7313466    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b5fa2000-b5fa7000 r--s 00000000 03:06 7313531    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b5fa7000-b5faa000 r--s 00000000 03:06 7313404    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5faa000-b5fab000 r--s 00000000 03:06 7313463    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5fab000-b5fad000 r--s 00000000 03:06 7313360    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b5fad000-b5fb0000 r--s 00000000 03:06 7313464    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5fb0000-b5fb6000 r--s 00000000 03:06 7307354    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5fb6000-b5fbc000 r--s 00000000 03:06 7307358    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b5fbc000-b5fbd000 r--s 00000000 03:06 7313481    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b5fbd000-b5fc6000 r--s 00000000 03:06 7307364    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b5fc6000-b5fcc000 r--s 00000000 03:06 7307372    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b5fcc000-b5fd0000 r--s 00000000 03:06 7309303    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b5fd0000-b5fd5000 r--s 00000000 03:06 7309002    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b5fd5000-b5fdc000 r--s 00000000 03:06 7313493    /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b5fdc000-b62da000 r--s 00000000 03:06 7116628    /home/charish/.fontconfig/6e8a1e72bef47a026b2d78a67cd97fb9-x86.cache-2
b62da000-b6596000 r--p 00000000 03:06 5886159    /usr/share/icons/hicolor/icon-theme.cache
b6596000-b6c3f000 r--p 00000000 03:06 5886152    /usr/share/icons/gnome/icon-theme.cache
b6c3f000-b6c46000 r-xp 00000000 03:06 5603352    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6c46000-b6c47000 rw-p 00007000 03:06 5603352    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
b6c47000-b6c63000 r-xp 00000000 03:06 5603343    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6c63000-b6c64000 rw-p 0001b000 03:06 5603343    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6c64000-b6cc4000 rw-s 00000000 00:08 6750208    /SYSV00000000 (deleted)
b6cc4000-b6d31000 rw-p b6cc4000 00:00 0 
b6d31000-b6d35000 r-xp 00000000 03:06 5603378    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d35000-b6d36000 rw-p 00003000 03:06 5603378    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6d36000-b6d3d000 r-xp 00000000 03:06 5539517    /usr/lib/libfam.so.0.0.0
b6d3d000-b6d3e000 rw-p 00006000 03:06 5539517    /usr/lib/libfam.so.0.0.0
b6d3e000-b6d44000 r-xp 00000000 03:06 4587547    /lib/libacl.so.1.1.0
b6d44000-b6d45000 rw-p 00005000 03:06 4587547    /lib/libacl.so.1.1.0
b6d45000-b6d48000 r-xp 00000000 03:06 4587551    /lib/libattr.so.1.1.0
b6d48000-b6d49000 rw-p 00002000 03:06 4587551    /lib/libattr.so.1.1.0
b6d49000-b6d4a000 r--s 00000000 03:06 7313173    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b6d4a000-b6d4f000 r--p 00000000 03:06 5965915    /usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo
b6d4f000-b6d56000 r--p 00000000 03:06 5965944    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-vfs-2.0.mo
b6d56000-b6d58000 r--p 00000000 03:06 5965921    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-desktop-2.0.mo
b6d58000-b6d64000 r-xp 00000000 03:06 5541855    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d64000-b6d65000 rw-p 0000b000 03:06 5541855    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6d65000-b6d6c000 r--p 00000000 03:06 5965966    /usr/share/locale-langpack/en_CA/LC_MESSAGES/libgnome-2.0.mo
b6d6c000-b6d6f000 r--p 00000000 03:06 5965937    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-session-2.0.mo
b6d6f000-b6d70000 r-xp 00000000 03:06 5541444    /usr/lib/gconv/ISO8859-1.so
b6d70000-b6d72000 rw-p 00000000 03:06 5541444    /usr/lib/gconv/ISO8859-1.so
b6d72000-b6d92000 r--p 00000000 03:06 5965953    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
b6d92000-b6da1000 r--p 00000000 03:06 5965954    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo
b6da1000-b6ddc000 r--p 00000000 03:06 5604232    /usr/lib/locale/en_CA.utf8/LC_CTYPE
b6ddc000-b6ddd000 r--p 00000000 03:06 5604237    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b6ddd000-b6dde000 r--p 00000000 03:06 5604240    /usr/lib/locale/en_CA.utf8/LC_TIME
b6dde000-b6eb5000 r--p 00000000 03:06 5604231    /usr/lib/locale/en_CA.utf8/LC_COLLATE
b6eb5000-b6ebe000 r-xp 00000000 03:06 4590837    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ebe000-b6ec0000 rw-p 00008000 03:06 4590837    /lib/tls/i686/cmov/libnss_files-2.5.so
b6ec0000-b6ec8000 r-xp 00000000 03:06 4590841    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6ec8000-b6eca000 rw-p 00007000 03:06 4590841    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eca000-b6ed1000 r-xp 00000000 03:06 4590833    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ed1000-b6ed3000 rw-p 00006000 03:06 4590833    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ed3000-b6ed6000 rw-p b6ed3000 00:00 0 
b6ed6000-b6f0c000 r-xp 00000000 03:06 4587638    /lib/libsepol.so.1
b6f0c000-b6f0d000 rw-p 00035000 03:06 4587638    /lib/libsepol.so.1
b6f0d000-b6f17000 rw-p b6f0d000 00:00 0 
b6f17000-b6f1a000 r-xp 00000000 03:06 5539670    /usr/lib/libgpg-error.so.0.3.0
b6f1a000-b6f1b000 rw-p 00002000 03:06 5539670    /usr/lib/libgpg-error.so.0.3.0
b6f1b000-b6f6a000 r-xp 00000000 03:06 5539558    /usr/lib/libgcrypt.so.11.2.2
b6f6a000-b6f6c000 rw-p 0004e000 03:06 5539558    /usr/lib/libgcrypt.so.11.2.2
b6f6c000-b6f6d000 rw-p b6f6c000 00:00 0 
b6f6d000-b6f81000 r-xp 00000000 03:06 5540014    /usr/lib/libtasn1.so.3.0.6
b6f81000-b6f82000 rw-p 00013000 03:06 5540014    /usr/lib/libtasn1.so.3.0.6
b6f82000-b6f84000 r-xp 00000000 03:06 4590854    /lib/tls/i686/cmov/libutil-2.5.so
b6f84000-b6f86000 rw-p 00001000 03:06 4590854    /lib/tls/i686/cmov/libutil-2.5.so
b6f86000-b6f9a000 r-xp 00000000 03:06 4587637    /lib/libselinux.so.1
b6f9a000-b6f9c000 rw-p 00013000 03:06 4587637    /lib/libselinux.so.1
b6f9c000-b6fab000 r-xp 00000000 03:06 4590848    /lib/tls/i686/cmov/libresolv-2.5.so
b6fab000-b6fad000 rw-p 0000f000 03:06 4590848    /lib/tls/i686/cmov/libresolv-2.5.so
b6fad000-b6faf000 rw-p b6fad000 00:00 0 
b6faf000-b6fbd000 r-xp 00000000 03:06 5539396    /usr/lib/libavahi-client.so.3.2.2
b6fbd000-b6fbe000 rw-p 0000e000 03:06 5539396    /usr/lib/libavahi-client.so.3.2.2
b6fbe000-b6fbf000 rw-p b6fbe000 00:00 0 
b6fbf000-b6fc9000 r-xp 00000000 03:06 5539398    /usr/lib/libavahi-common.so.3.4.3
b6fc9000-b6fca000 rw-p 00009000 03:06 5539398    /usr/lib/libavahi-common.so.3.4.3
b6fca000-b6fcc000 r-xp 00000000 03:06 5539402    /usr/lib/libavahi-glib.so.1.0.1
b6fcc000-b6fcd000 rw-p 00001000 03:06 5539402    /usr/lib/libavahi-glib.so.1.0.1
b6fcd000-b7037000 r-xp 00000000 03:06 5539666    /usr/lib/libgnutls.so.13.0.9
b7037000-b703d000 rw-p 0006a000 03:06 5539666    /usr/lib/libgnutls.so.13.0.9
b703d000-b705f000 r-xp 00000000 03:06 5539926    /usr/lib/libpng12.so.0.15.0
b705f000-b7060000 rw-p 00021000 03:06 5539926    /usr/lib/libpng12.so.0.15.0
b7060000-b707e000 r-xp 00000000 03:06 5539513    /usr/lib/libexpat.so.1.0.0
b707e000-b7080000 rw-p 0001d000 03:06 5539513    /usr/lib/libexpat.so.1.0.0
b7080000-b7081000 rw-p b7080000 00:00 0 
b7081000-b70e9000 r-xp 00000000 03:06 5539529    /usr/lib/libfreetype.so.6.3.10
b70e9000-b70ec000 rw-p 00068000 03:06 5539529    /usr/lib/libfreetype.so.6.3.10
b70ec000-b70ff000 r-xp 00000000 03:06 5540072    /usr/lib/libz.so.1.2.3
b70ff000-b7100000 rw-p 00012000 03:06 5540072    /usr/lib/libz.so.1.2.3
b7100000-b7113000 r-xp 00000000 03:06 4590831    /lib/tls/i686/cmov/libnsl-2.5.so
b7113000-b7115000 rw-p 00012000 03:06 4590831    /lib/tls/i686/cmov/libnsl-2.5.so
b7115000-b7117000 rw-p b7115000 00:00 0 
b7117000-b711b000 r-xp 00000000 03:06 5539303    /usr/lib/libORBitCosNaming-2.so.0.1.0
b711b000-b711c000 rw-p 00003000 03:06 5539303    /usr/lib/libORBitCosNaming-2.so.0.1.0
b711c000-b711d000 rw-p b711c000 00:00 0 
b711d000-b7121000 r-xp 00000000 03:06 5539328    /usr/lib/libXdmcp.so.6.0.0
b7121000-b7122000 rw-p 00003000 03:06 5539328    /usr/lib/libXdmcp.so.6.0.0
b7122000-b7140000 r-xp 00000000 03:06 5539795    /usr/lib/libjpeg.so.62.0.0
b7140000-b7141000 rw-p 0001d000 03:06 5539795    /usr/lib/libjpeg.so.62.0.0
b7141000-b7149000 r-xp 00000000 03:06 5540004    /usr/lib/libstartup-notification-1.so.0.0.0
b7149000-b714a000 rw-p 00007000 03:06 5540004    /usr/lib/libstartup-notification-1.so.0.0.0
b714a000-b714b000 rw-p b714a000 00:00 0 
b714b000-b7152000 r-xp 00000000 03:06 4590850    /lib/tls/i686/cmov/librt-2.5.so
b7152000-b7154000 rw-p 00006000 03:06 4590850    /lib/tls/i686/cmov/librt-2.5.so
b7154000-b7158000 r-xp 00000000 03:06 5539722    /usr/lib/libgthread-2.0.so.0.1200.11
b7158000-b7159000 rw-p 00003000 03:06 5539722    /usr/lib/libgthread-2.0.so.0.1200.11
b7159000-b715b000 r-xp 00000000 03:06 4590826    /lib/tls/i686/cmov/libdl-2.5.so
b715b000-b715d000 rw-p 00001000 03:06 4590826    /lib/tls/i686/cmov/libdl-2.5.so
b715d000-b715f000 r-xp 00000000 03:06 5539624    /usr/lib/libgmodule-2.0.so.0.1200.11
b715f000-b7160000 rw-p 00002000 03:06 5539624    /usr/lib/libgmodule-2.0.so.0.1200.11
b7160000-b71b6000 r-xp 00000000 03:06 5539658    /usr/lib/libgnomevfs-2.so.0.1800.1
b71b6000-b71b9000 rw-p 00055000 03:06 5539658    /usr/lib/libgnomevfs-2.so.0.1800.1
b71b9000-b7227000 r-xp 00000000 03:06 5539421    /usr/lib/libcairo.so.2.11.1
b7227000-b7229000 rw-p 0006d000 03:06 5539421    /usr/lib/libcairo.so.2.11.1
b7229000-b722a000 rw-p b7229000 00:00 0 
b722a000-b722e000 r-xp 00000000 03:06 5539334    /usr/lib/libXfixes.so.3.1.0
b722e000-b722f000 rw-p 00003000 03:06 5539334    /usr/lib/libXfixes.so.3.1.0
b722f000-b7237000 r-xp 00000000 03:06 5539324    /usr/lib/libXcursor.so.1.0.2
b7237000-b7238000 rw-p 00007000 03:06 5539324    /usr/lib/libXcursor.so.1.0.2
b7238000-b723f000 r-xp 00000000 03:06 5539340    /usr/lib/libXi.so.6.0.0
b723f000-b7240000 rw-p 00006000 03:06 5539340    /usr/lib/libXi.so.6.0.0
b7240000-b7242000 r-xp 00000000 03:06 5539342    /usr/lib/libXinerama.so.1.0.0
b7242000-b7243000 rw-p 00001000 03:06 5539342    /usr/lib/libXinerama.so.1.0.0
b7243000-b724a000 r-xp 00000000 03:06 5539354    /usr/lib/libXrender.so.1.3.0
b724a000-b724b000 rw-p 00006000 03:06 5539354    /usr/lib/libXrender.so.1.3.0
b724b000-b7258000 r-xp 00000000 03:06 5539332    /usr/lib/libXext.so.6.4.0
b7258000-b7259000 rw-p 0000d000 03:06 5539332    /usr/lib/libXext.so.6.4.0
b7259000-b725a000 rw-p b7259000 00:00 0 
b725a000-b727d000 r-xp 00000000 03:06 5539519    /usr/lib/libfontconfig.so.1.2.0
b727d000-b7285000 rw-p 00023000 03:06 5539519    /usr/lib/libfontconfig.so.1.2.0
b7285000-b728c000 r-xp 00000000 03:06 5539903    /usr/lib/libpangocairo-1.0.so.0.1600.2
b728c000-b728d000 rw-p 00007000 03:06 5539903    /usr/lib/libpangocairo-1.0.so.0.1600.2
b728d000-b72b7000 r-xp 00000000 03:06 5539905    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72b7000-b72b8000 rw-p 0002a000 03:06 5539905    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72b8000-b72cc000 r-xp 00000000 03:06 5539380    /usr/lib/libart_lgpl_2.so.2.3.17
b72cc000-b72cd000 rw-p 00013000 03:06 5539380    /usr/lib/libart_lgpl_2.so.2.3.17
b72cd000-b72d4000 r-xp 00000000 03:06 4587627    /lib/libpopt.so.0.0.0
b72d4000-b72d5000 rw-p 00006000 03:06 4587627    /lib/libpopt.so.0.0.0
b72d5000-b72fe000 r-xp 00000000 03:06 5539640    /usr/lib/libgnomecanvas-2.so.0.1400.0
b72fe000-b72ff000 rw-p 00029000 03:06 5539640    /usr/lib/libgnomecanvas-2.so.0.1400.0
b72ff000-b7300000 rw-p b72ff000 00:00 0 
b7300000-b735b000 r-xp 00000000 03:06 5539417    /usr/lib/libbonoboui-2.so.0.0.0
b735b000-b735e000 rw-p 0005a000 03:06 5539417    /usr/lib/libbonoboui-2.so.0.0.0
b735e000-b7475000 r-xp 00000000 03:06 5540066    /usr/lib/libxml2.so.2.6.27
b7475000-b747b000 rw-p 00116000 03:06 5540066    /usr/lib/libxml2.so.2.6.27
b747b000-b753b000 r-xp 00000000 03:06 5539382    /usr/lib/libasound.so.2.0.0
b753b000-b7540000 rw-p 000bf000 03:06 5539382    /usr/lib/libasound.so.2.0.0
b7540000-b7565000 r-xp 00000000 03:06 4590828    /lib/tls/i686/cmov/libm-2.5.so
b7565000-b7567000 rw-p 00024000 03:06 4590828    /lib/tls/i686/cmov/libm-2.5.so
b7567000-b7587000 r-xp 00000000 03:06 5539394    /usr/lib/libaudiofile.so.0.0.2
b7587000-b7589000 rw-p 00020000 03:06 5539394    /usr/lib/libaudiofile.so.0.0.2
b7589000-b76c4000 r-xp 00000000 03:06 4590820    /lib/tls/i686/cmov/libc-2.5.so
b76c4000-b76c5000 r--p 0013b000 03:06 4590820    /lib/tls/i686/cmov/libc-2.5.so
b76c5000-b76c7000 rw-p 0013c000 03:06 4590820    /lib/tls/i686/cmov/libc-2.5.so
b76c7000-b76cb000 rw-p b76c7000 00:00 0 
b76cb000-b76d2000 r-xp 00000000 03:06 4587658    /lib/libwrap.so.0.7.6
b76d2000-b76d3000 rw-p 00007000 03:06 4587658    /lib/libwrap.so.0.7.6
b76d3000-b7767000 r-xp 00000000 03:06 5539614    /usr/lib/libglib-2.0.so.0.1200.11
b7767000-b7768000 rw-p 00093000 03:06 5539614    /usr/lib/libglib-2.0.so.0.1200.11
b7768000-b7774000 r-xp 00000000 03:06 5539630    /usr/lib/libgnome-keyring.so.0.0.1
b7774000-b7775000 rw-p 0000b000 03:06 5539630    /usr/lib/libgnome-keyring.so.0.0.1
b7775000-b77ae000 r-xp 00000000 03:06 5539668    /usr/lib/libgobject-2.0.so.0.1200.11
b77ae000-b77af000 rw-p 00039000 03:06 5539668    /usr/lib/libgobject-2.0.so.0.1200.11
b77af000-b77e0000 r-xp 00000000 03:06 5539455    /usr/lib/libdbus-1.so.3.2.0
b77e0000-b77e1000 rw-p 00031000 03:06 5539455    /usr/lib/libdbus-1.so.3.2.0
b77e1000-b77fb000 r-xp 00000000 03:06 5539457    /usr/lib/libdbus-glib-1.so.2.1.0
b77fb000-b77fc000 rw-p 0001a000 03:06 5539457    /usr/lib/libdbus-glib-1.so.2.1.0
b77fc000-b77fd000 rw-p b77fc000 00:00 0 
b77fd000-b7810000 r-xp 00000000 03:06 4590846    /lib/tls/i686/cmov/libpthread-2.5.so
b7810000-b7812000 rw-p 00013000 03:06 4590846    /lib/tls/i686/cmov/libpthread-2.5.so
b7812000-b7814000 rw-p b7812000 00:00 0 
b7814000-b785d000 r-xp 00000000 03:06 5539299    /usr/lib/libORBit-2.so.0.1.0
b785d000-b7867000 rw-p 00048000 03:06 5539299    /usr/lib/libORBit-2.so.0.1.0
b7867000-b7896000 r-xp 00000000 03:06 5539556    /usr/lib/libgconf-2.so.4.1.2
b7896000-b7899000 rw-p 0002e000 03:06 5539556    /usr/lib/libgconf-2.so.4.1.2
b7899000-b78ac000 r-xp 00000000 03:06 5539415    /usr/lib/libbonobo-activation.so.4.0.0
b78ac000-b78ae000 rw-p 00013000 03:06 5539415    /usr/lib/libbonobo-activation.so.4.0.0
b78ae000-b7900000 r-xp 00000000 03:06 5539413    /usr/lib/libbonobo-2.so.0.0.0
b7900000-b790a000 rw-p 00051000 03:06 5539413    /usr/lib/libbonobo-2.so.0.0.0
b790a000-b790b000 rw-p b790a000 00:00 0 
b790b000-b79f8000 r-xp 00000000 03:06 5539311    /usr/lib/libX11.so.6.2.0
b79f8000-b79fc000 rw-p 000ed000 03:06 5539311    /usr/lib/libX11.so.6.2.0
b79fc000-b7a38000 r-xp 00000000 03:06 5539901    /usr/lib/libpango-1.0.so.0.1600.2
b7a38000-b7a3a000 rw-p 0003b000 03:06 5539901    /usr/lib/libpango-1.0.so.0.1600.2
b7a3a000-b7a3f000 r-xp 00000000 03:06 5539352    /usr/lib/libXrandr.so.2.1.0
b7a3f000-b7a40000 rw-p 00005000 03:06 5539352    /usr/lib/libXrandr.so.2.1.0
b7a40000-b7a56000 r-xp 00000000 03:06 5539578    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a56000-b7a57000 rw-p 00015000 03:06 5539578    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a57000-b7a70000 r-xp 00000000 03:06 5539388    /usr/lib/libatk-1.0.so.0.1809.1
b7a70000-b7a72000 rw-p 00018000 03:06 5539388    /usr/lib/libatk-1.0.so.0.1809.1
b7a72000-b7af5000 r-xp 00000000 03:06 5539576    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7af5000-b7af8000 rw-p 00083000 03:06 5539576    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7af8000-b7af9000 rw-p b7af8000 00:00 0 
b7af9000-b7e4a000 r-xp 00000000 03:06 5539725    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e4a000-b7e50000 rw-p 00351000 03:06 5539725    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e50000-b7e51000 rw-p b7e50000 00:00 0 
b7e51000-b7e65000 r-xp 00000000 03:06 5539626    /usr/lib/libgnome-2.so.0.1800.0
b7e65000-b7e66000 rw-p 00014000 03:06 5539626    /usr/lib/libgnome-2.so.0.1800.0
b7e66000-b7e7b000 r-xp 00000000 03:06 5539289    /usr/lib/libICE.so.6.3.0
b7e7b000-b7e7d000 rw-p 00014000 03:06 5539289    /usr/lib/libICE.so.6.3.0
b7e7d000-b7e7e000 rw-p b7e7d000 00:00 0 
b7e7e000-b7e86000 r-xp 00000000 03:06 5539307    /usr/lib/libSM.so.6.0.0
b7e86000-b7e87000 rw-p 00007000 03:06 5539307    /usr/lib/libSM.so.6.0.0
b7e87000-b7f11000 r-xp 00000000 03:06 5539656    /usr/lib/libgnomeui-2.so.0.1788.4
b7f11000-b7f15000 rw-p 00089000 03:06 5539656    /usr/lib/libgnomeui-2.so.0.1788.4
b7f15000-b7f29000 r-xp 00000000 03:06 5539628    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f29000-b7f2a000 rw-p 00014000 03:06 5539628    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f2a000-b7f2b000 rw-p b7f2a000 00:00 0 
b7f2b000-b7f34000 r-xp 00000000 03:06 5539504    /usr/lib/libesd.so.0.2.36
b7f34000-b7f35000 rw-p 00009000 03:06 5539504    /usr/lib/libesd.so.0.2.36
b7f35000-b7f37000 r-xp 00000000 03:06 5539317    /usr/lib/libXau.so.6.0.0
b7f37000-b7f38000 rw-p 00001000 03:06 5539317    /usr/lib/libXau.so.6.0.0
b7f38000-b7f39000 r--p 00000000 03:06 5604235    /usr/lib/locale/en_CA.utf8/LC_MONETARY
b7f39000-b7f3a000 r--p 00000000 03:06 5604241    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f3a000-b7f3b000 r--p 00000000 03:06 5604238    /usr/lib/locale/en_CA.utf8/LC_PAPER
b7f3b000-b7f3c000 r--p 00000000 03:06 5604236    /usr/lib/locale/en_CA.utf8/LC_NAME
b7f3c000-b7f3d000 r--p 00000000 03:06 5604230    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
b7f3d000-b7f3e000 r--p 00000000 03:06 5604239    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
b7f3e000-b7f3f000 r--p 00000000 03:06 5604234    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
b7f3f000-b7f46000 r--s 00000000 03:06 5541497    /usr/lib/gconv/gconv-modules.cache
b7f46000-b7f47000 r--p 00000000 03:06 5604233    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
b7f47000-b7f49000 rw-p b7f47000 00:00 0 
b7f49000-b7f62000 r-xp 00000000 03:06 4587541    /lib/ld-2.5.so
b7f62000-b7f64000 rw-p 00019000 03:06 4587541    /lib/ld-2.5.so
bffbe000-bffd3000 rw-p bffbe000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/charish/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

(update-notifier:14212): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

Any remedy to this? I can't open the Sessions from Preferences to take them both off so I'm pretty much stuck. Thanks for the help in advance! ^_^

EDIT: I also downloaded and used Art Manager in order to change the splash screen that comes up after the login and the icons as well.

---

### Post by phidia on 2007-05-02
If this is the "session only lasted less than 10 seconds" error you can try
cd /home
sudo chmod 700 <yourusername>
sudo chown <yourusername> <yourusername>
sudo chgrp <yourusername> <yourusername>
cd <yourusername>
sudo chmod -R 777

You may not need the last command so try without it-good luck

---

### Post by charish2k1 on 2007-05-03
Nope, that little batch of commands didn't work x.x; Any other suggestions?

---

### Post by phidia on 2007-05-03
Create a new user, log into that account if you can. If you can do that maybe you can compare the dot files in the working account to the ones in your account you can't log into.

---

### Post by asymmetric on 2007-06-09
i've had the same problem, and in my case it was caused by a new splash-screen installed via gnome-art..

i solved the problem by going to $HOME/.gnome2/gnome-art/downloads and deleting everything inside, beyond uninstalling the splash-screen via gnome-art (or gnome-splashscreen-manager) and then gnome-art itself


byez
asy

---

