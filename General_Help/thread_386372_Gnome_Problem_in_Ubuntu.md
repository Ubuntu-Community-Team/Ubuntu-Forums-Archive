---
title: "Gnome Problem in Ubuntu"
date: 2007-03-16
forum: General Help
---

### Post by taser on 2007-03-16
My user login is aborting as soon as I login. The message I keep getting is:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging on with one of the failsafe sessions to see if you can fix this problem.

It seems to be limited to my user; I'm currently using my wife's login on the same computer with no errors. The text of the error is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "taser"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/server1.example.com:/tmp/.ICE-unix/7700
seahorse nautilus module initialized
Initializing gnome-mount extension
Initializing nautilus-open-terminal extension
gsynaptics-init: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

(process:7834): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0825ab20 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76526dc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb76535ee]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb77692c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7af8db0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7afa1e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7afdf2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7afe1c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7afe27f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7db3440]
x-session-manager[0x805ce15]
/usr/lib/libglib-2.0.so.0[0xb77623c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7761df2]
/usr/lib/libglib-2.0.so.0[0xb7764dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb7765335]
x-session-manager[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb778b40d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7761df2]
/usr/lib/libglib-2.0.so.0[0xb7764dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7765179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c93044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75ffebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:02 3707253    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:02 3707253    /usr/bin/gnome-session
08069000-08282000 rw-p 08069000 00:00 0          [heap]
b4b00000-b4b21000 rw-p b4b00000 00:00 0 
b4b21000-b4c00000 ---p b4b21000 00:00 0 
b4c60000-b4c6b000 r-xp 00000000 08:02 3966864    /lib/libgcc_s.so.1
b4c6b000-b4c6c000 rw-p 0000a000 08:02 3966864    /lib/libgcc_s.so.1
b4c91000-b4c97000 r-xp 00000000 08:02 2162709    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4c97000-b4c98000 rw-p 00005000 08:02 2162709    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4c98000-b4cf8000 rw-s 00000000 00:08 2752536    /SYSV00000000 (deleted)
b4cf8000-b4cf9000 ---p b4cf8000 00:00 0 
b4cf9000-b54f9000 rw-p b4cf9000 00:00 0 
b54f9000-b5576000 r--p 00000000 08:02 1196410    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5576000-b5578000 r-xp 00000000 08:02 3801546    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5578000-b5579000 rw-p 00001000 08:02 3801546    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5579000-b557c000 r--s 00000000 08:02 2886333    /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b557c000-b557f000 r--s 00000000 08:02 2886327    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b557f000-b5585000 r--s 00000000 08:02 2886326    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5585000-b5588000 r--s 00000000 08:02 2886323    /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b5588000-b5589000 r--s 00000000 08:02 2886321    /var/cache/fontconfig/cc350556a40230a43bbdf28d7b7e2141-x86.cache-2
b5589000-b558a000 r--s 00000000 08:02 2886320    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b558a000-b558d000 r--s 00000000 08:02 2886318    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b558d000-b558e000 r--s 00000000 08:02 2886317    /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b558e000-b558f000 r--s 00000000 08:02 2886315    /var/cache/fontconfig/fc14e3aff40829fbb7132d5e06a8168b-x86.cache-2
b558f000-b5590000 r--s 00000000 08:02 2886312    /var/cache/fontconfig/dc69028cb7d26f67d8024a5e4f94b512-x86.cache-2
b5590000-b5591000 r--s 00000000 08:02 2886311    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5591000-b5592000 r--s 00000000 08:02 2886310    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5592000-b5593000 r--s 00000000 08:02 2886309    /var/cache/fontconfig/0097a0479515711d822f246202383c92-x86.cache-2
b5593000-b5597000 r--s 00000000 08:02 2886308    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5597000-b559a000 r--s 00000000 08:02 2886306    /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b559a000-b55b5000 r--s 00000000 08:02 2886305    /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b55b5000-b55d1000 r--s 00000000 08:02 2886303    /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b55d1000-b55ef000 r--s 00000000 08:02 2886301    /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b55ef000-b55f0000 r--s 00000000 08:02 2886300    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b55f0000-b55f2000 r--s 00000000 08:02 2886297    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b55f2000-b55f4000 r--s 00000000 08:02 2886296    /var/cache/fontconfig/dfe01fa16583a856689483e0569db943-x86.cache-2
b55f4000-b55f6000 r--s 00000000 08:02 2886295    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b55f6000-b55f7000 r--s 00000000 08:02 2890965    /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b55f7000-b55f8000 r--s 00000000 08:02 2886293    /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b55f8000-b55fa000 r--s 00000000 08:02 2886292    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b55fa000-b5600000 r--s 00000000 08:02 2886291    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5600000-b5602000 r--s 00000000 08:02 2886287    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5602000-b5604000 r--s 00000000 08:02 2886286    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b5604000-b560c000 r--s 00000000 08:02 2886285    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b560c000-b5611000 r--s 00000000 08:02 2890964    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5611000-b5612000 r--s 00000000 08:02 2886283    /var/cache/fontconfig/9451a55048e8dbe8633e64d34165fdf2-x86.cache-2
b5612000-b5614000 r--s 00000000 08:02 2886282    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b5614000-b5615000 r--s 00000000 08:02 2886281    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5615000-b562c000 r--s 00000000 08:02 2886280    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b562c000-b562e000 r--s 00000000 08:02 2886279    /var/cache/fontconfig/80d0a1cf7989637baed91f874e3e11f6-x86.cache-2
b562e000-b5630000 r--s 00000000 08:02 2890963    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5630000-b5636000 r--s 00000000 08:02 2886277    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5636000-b563a000 r--s 00000000 08:02 2886276    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b563a000-b563d000 r--s 00000000 08:02 2890962    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b563d000-b5644000 r--s 00000000 08:02 2886274    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5644000-b5661000 r--s 00000000 08:02 2887023    /var/cache/fontconfig/cabbd14511b9e8a55e92af97fb3a0461-x86.cache-2
b5661000-b5668000 r--s 00000000 08:02 2885775    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5668000-b56a8000 r--s 00000000 08:02 2885774    /var/cache/fontconfig/eeebfc908bd29a90773fd860017aada4-x86.cache-2
b56a8000-b56e8000 r--s 00000000 08:02 2885773    /var/cache/fontconfig/21a99156bb11811cef641abeda519a45-x86.cache-2
b56e8000-b56e9000 r--s 00000000 08:02 2886990    /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b56e9000-b56ea000 r--s 00000000 08:02 2886986    /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b56ea000-b56eb000 r--s 00000000 08:02 2886985    /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b56eb000-b56ec000 r--s 00000000 08:02 2886983    /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b56ec000-b56ee000 r--s 00000000 08:02 2886880    /var/cache/fontconfig/0f004ce578a5ca7ae310546afb5e47d3-x86.cache-2
b56ee000-b56ef000 r--s 00000000 08:02 2886879    /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b56ef000-b56f2000 r--s 00000000 08:02 2886878    /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b56f2000-b56f6000 r--s 00000000 08:02 2886877    /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b56f6000-b56fd000 r--s 00000000 08:02 2886876    /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b56fd000-b5702000 r--s 00000000 08:02 2886875    /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b5702000-b5703000 r--s 00000000 08:02 2886874    /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b5703000-b5705000 r--s 00000000 08:02 2886873    /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b5705000-b5706000 r--s 00000000 08:02 2886872    /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5706000-b570b000 r--s 00000000 08:02 2886871    /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b570b000-b5710000 r--s 00000000 08:02 2886870    /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b5710000-b5717000 r--s 00000000 08:02 2886869    /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b5717000-b571a000 r--s 00000000 08:02 2890811    /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b571a000-b571c000 r--s 00000000 08:02 2886669    /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b571c000-b571e000 r--s 00000000 08:02 2886611    /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b571e000-b5721000 r--s 00000000 08:02 2886446    /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5721000-b5728000 r--s 00000000 08:02 2886445    /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b5728000-b572e000 r--s 00000000 08:02 2886444    /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b572e000-b621c000 r--p 00000000 08:02 3802732    /usr/share/icons/hicolor/icon-theme.cache
b621c000-b68d8000 r--p 00000000 08:02 3802083    /usr/share/icons/gnome/icon-theme.cache
b68d8000-b6cd5000 r--p 00000000 08:02 1019802    /usr/share/icons/gnomedev/icon-theme.cache
b6cd5000-b6d06000 r-xp 00000000 08:02 442679     /usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so
b6d06000-b6d07000 rw-p 00030000 08:02 442679     /usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so
b6d07000-b6d67000 rw-s 00000000 00:08 2719767    /SYSV00000000 (deleted)
b6d67000-b6db4000 rw-p b6d67000 00:00 0 
b6db4000-b6dbb000 r-xp 00000000 08:02 2375784    /usr/lib/libfam.so.0.0.0
b6dbb000-b6dbc000 rw-p 00006000 08:02 2375784    /usr/lib/libfam.so.0.0.0
b6dbc000-b6dc2000 r-xp 00000000 08:02 4079825    /lib/libacl.so.1.1.0
b6dc2000-b6dc3000 rw-p 00005000 08:02 4079825    /lib/libacl.so.1.1.0
b6dc3000-b6dc6000 r-xp 00000000 08:02 4079838    /lib/libattr.so.1.1.0
b6dc6000-b6dc7000 rw-p 00002000 08:02 4079838    /lib/libattr.so.1.1.0
b6dc7000-b6dd1000 r--s 00000000 08:02 2886442    /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6dd1000-b6dd8000 r--s 00000000 08:02 2886441    /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6dd8000-b6ddd000 r--s 00000000 08:02 2886440    /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6ddd000-b6de2000 r--s 00000000 08:02 2886439    /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6de2000-b6de7000 r--p 00000000 08:02 985981     /usr/share/icons/Nuvola/icon-theme.cache
b6de7000-b6deb000 r-xp 00000000 08:02 2162701    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6deb000-b6dec000 rw-p 00003000 08:02 2162701    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6dec000-b6e27000 r--p 00000000 08:02 4066575    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e27000-b6efe000 r--p 00000000 08:02 4065426    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6efe000-b6f07000 r-xp 00000000 08:02 4079740    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f07000-b6f09000 rw-p 00008000 08:02 4079740    /lib/tls/i686/cmov/libnss_files-2.5.so
b6f09000-b6f11000 r-xp 00000000 08:02 4079743    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f11000-b6f13000 rw-p 00007000 08:02 4079743    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6f13000-b6f1a000 r-xp 00000000 08:02 4079702    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f1a000-b6f1c000 rw-p 00006000 08:02 4079702    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6f1c000-b6f20000 rw-p b6f1c000 00:00 0 
b6f20000-b6f56000 r-xp 00000000 08:02 3966878    /lib/libsepol.so.1
b6f56000-b6f57000 rw-p 00035000 08:02 3966878    /lib/libsepol.so.1
b6f57000-b6f61000 rw-p b6f57000 00:00 0 
b6f61000-b6f64000 r-xp 00000000 08:02 2376418    /usr/lib/libgpg-error.so.0.3.0
b6f64000-b6f65000 rw-p 00002000 08:02 2376418    /usr/lib/libgpg-error.so.0.3.0
b6f65000-b6fb4000 r-xp 00000000 08:02 3703120    /usr/lib/libgcrypt.so.11.2.2
b6fb4000-b6fb6000 rw-p 0004e000 08:02 3703120    /usr/lib/libgcrypt.so.11.2.2
b6fb6000-b6fca000 r-xp 00000000 08:02 3706997    /usr/lib/libtasn1.so.3.0.6
b6fca000-b6fcb000 rw-p 00013000 08:02 3706997    /usr/lib/libtasn1.so.3.0.6
b6fcb000-b6fcf000 r-xp 00000000 08:02 3702957    /usr/lib/libXdmcp.so.6.0.0
b6fcf000-b6fd0000 rw-p 00003000 08:02 3702957    /usr/lib/libXdmcp.so.6.0.0
b6fd0000-b6fd1000 rw-p b6fd0000 00:00 0 
b6fd1000-b6fd3000 r-xp 00000000 08:02 2953115    /lib/tls/i686/cmov/libutil-2.5.so
b6fd3000-b6fd5000 rw-p 00001000 08:02 2953115    /lib/tls/i686/cmov/libutil-2.5.so
b6fd5000-b6fe9000 r-xp 00000000 08:02 4065789    /lib/libselinux.so.1
b6fe9000-b6feb000 rw-p 00013000 08:02 4065789    /lib/libselinux.so.1
b6feb000-b6ffa000 r-xp 00000000 08:02 2953108    /lib/tls/i686/cmov/libresolv-2.5.so
b6ffa000-b6ffc000 rw-p 0000f000 08:02 2953108    /lib/tls/i686/cmov/libresolv-2.5.so
b6ffc000-b6ffe000 rw-p b6ffc000 00:00 0 
b6ffe000-b700c000 r-xp 00000000 08:02 2376411    /usr/lib/libavahi-client.so.3.2.2
b700c000-b700d000 rw-p 0000e000 08:02 2376411    /usr/lib/libavahi-client.so.3.2.2
b700d000-b7017000 r-xp 00000000 08:02 3705874    /usr/lib/libavahi-common.so.3.4.3
b7017000-b7018000 rw-p 00009000 08:02 3705874    /usr/lib/libavahi-common.so.3.4.3
b7018000-b7019000 rw-p b7018000 00:00 0 
b7019000-b701b000 r-xp 00000000 08:02 2376413    /usr/lib/libavahi-glib.so.1.0.1
b701b000-b701c000 rw-p 00001000 08:02 2376413    /usr/lib/libavahi-glib.so.1.0.1
b701c000-b7086000 r-xp 00000000 08:02 3708924    /usr/lib/libgnutls.so.13.0.9
b7086000-b708c000 rw-p 0006a000 08:02 3708924    /usr/lib/libgnutls.so.13.0.9
b708c000-b70ae000 r-xp 00000000 08:02 3704594    /usr/lib/libpng12.so.0.15.0
b70ae000-b70af000 rw-p 00021000 08:02 3704594    /usr/lib/libpng12.so.0.15.0
b70af000-b70cd000 r-xp 00000000 08:02 3709395    /usr/lib/libexpat.so.1.0.0
b70cd000-b70cf000 rw-p 0001d000 08:02 3709395    /usr/lib/libexpat.so.1.0.0
b70cf000-b7136000 r-xp 00000000 08:02 3705539    /usr/lib/libfreetype.so.6.3.10
b7136000-b7139000 rw-p 00067000 08:02 3705539    /usr/lib/libfreetype.so.6.3.10
b7139000-b713a000 rw-p b7139000 00:00 0 
b713a000-b714d000 r-xp 00000000 08:02 3704346    /usr/lib/libz.so.1.2.3
b714d000-b714e000 rw-p 00012000 08:02 3704346    /usr/lib/libz.so.1.2.3
b714e000-b7161000 r-xp 00000000 08:02 4079701    /lib/tls/i686/cmov/libnsl-2.5.so
b7161000-b7163000 rw-p 00012000 08:02 4079701    /lib/tls/i686/cmov/libnsl-2.5.so
b7163000-b7165000 rw-p b7163000 00:00 0 
b7165000-b7169000 r-xp 00000000 08:02 2376361    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7169000-b716a000 rw-p 00003000 08:02 2376361    /usr/lib/libORBitCosNaming-2.so.0.1.0
b716a000-b7181000 r-xp 00000000 08:02 3706201    /usr/lib/libxcb.so.1.0.0
b7181000-b7182000 rw-p 00016000 08:02 3706201    /usr/lib/libxcb.so.1.0.0
b7182000-b7183000 rw-p b7182000 00:00 0 
b7183000-b7184000 r-xp 00000000 08:02 3706203    /usr/lib/libxcb-xlib.so.0.0.0
b7184000-b7185000 rw-p 00000000 08:02 3706203    /usr/lib/libxcb-xlib.so.0.0.0
b7185000-b71a3000 r-xp 00000000 08:02 3704477    /usr/lib/libjpeg.so.62.0.0
b71a3000-b71a4000 rw-p 0001d000 08:02 3704477    /usr/lib/libjpeg.so.62.0.0
b71a4000-b71ac000 r-xp 00000000 08:02 3707262    /usr/lib/libstartup-notification-1.so.0.0.0
b71ac000-b71ad000 rw-p 00007000 08:02 3707262    /usr/lib/libstartup-notification-1.so.0.0.0
b71ad000-b71ae000 rw-p b71ad000 00:00 0 
b71ae000-b71b5000 r-xp 00000000 08:02 2953110    /lib/tls/i686/cmov/librt-2.5.so
b71b5000-b71b7000 rw-p 00006000 08:02 2953110    /lib/tls/i686/cmov/librt-2.5.so
b71b7000-b71bb000 r-xp 00000000 08:02 3706251    /usr/lib/libgthread-2.0.so.0.1200.11
b71bb000-b71bc000 rw-p 00003000 08:02 3706251    /usr/lib/libgthread-2.0.so.0.1200.11
b71bc000-b71be000 r-xp 00000000 08:02 4079695    /lib/tls/i686/cmov/libdl-2.5.so
b71be000-b71c0000 rw-p 00001000 08:02 4079695    /lib/tls/i686/cmov/libdl-2.5.so
b71c0000-b71c2000 r-xp 00000000 08:02 3705726    /usr/lib/libgmodule-2.0.so.0.1200.11
b71c2000-b71c3000 rw-p 00002000 08:02 3705726    /usr/lib/libgmodule-2.0.so.0.1200.11
b71c3000-b7218000 r-xp 00000000 08:02 2377252    /usr/lib/libgnomevfs-2.so.0.1799.1
b7218000-b721b000 rw-p 00055000 08:02 2377252    /usr/lib/libgnomevfs-2.so.0.1799.1
b721b000-b7288000 r-xp 00000000 08:02 2377233    /usr/lib/libcairo.so.2.11.0
b7288000-b728a000 rw-p 0006c000 08:02 2377233    /usr/lib/libcairo.so.2.11.0
b728a000-b728b000 rw-p b728a000 00:00 0 
b728b000-b728f000 r-xp 00000000 08:02 3706086    /usr/lib/libXfixes.so.3.1.0
b728f000-b7290000 rw-p 00003000 08:02 3706086    /usr/lib/libXfixes.so.3.1.0
b7290000-b7298000 r-xp 00000000 08:02 3705716    /usr/lib/libXcursor.so.1.0.2
b7298000-b7299000 rw-p 00007000 08:02 3705716    /usr/lib/libXcursor.so.1.0.2
b7299000-b72a0000 r-xp 00000000 08:02 3704869    /usr/lib/libXi.so.6.0.0
b72a0000-b72a1000 rw-p 00006000 08:02 3704869    /usr/lib/libXi.so.6.0.0
b72a1000-b72a3000 r-xp 00000000 08:02 3707595    /usr/lib/libXinerama.so.1.0.0
b72a3000-b72a4000 rw-p 00001000 08:02 3707595    /usr/lib/libXinerama.so.1.0.0
b72a4000-b72ab000 r-xp 00000000 08:02 3704584    /usr/lib/libXrender.so.1.3.0
b72ab000-b72ac000 rw-p 00006000 08:02 3704584    /usr/lib/libXrender.so.1.3.0
b72ac000-b72b9000 r-xp 00000000 08:02 3702970    /usr/lib/libXext.so.6.4.0
b72b9000-b72ba000 rw-p 0000d000 08:02 3702970    /usr/lib/libXext.so.6.4.0
b72ba000-b72bb000 rw-p b72ba000 00:00 0 
b72bb000-b72de000 r-xp 00000000 08:02 3712580    /usr/lib/libfontconfig.so.1.2.0
b72de000-b72e6000 rw-p 00023000 08:02 3712580    /usr/lib/libfontconfig.so.1.2.0
b72e6000-b72ed000 r-xp 00000000 08:02 3705954    /usr/lib/libpangocairo-1.0.so.0.1600.1
b72ed000-b72ee000 rw-p 00007000 08:02 3705954    /usr/lib/libpangocairo-1.0.so.0.1600.1
b72ee000-b7318000 r-xp 00000000 08:02 3706124    /usr/lib/libpangoft2-1.0.so.0.1600.1
b7318000-b7319000 rw-p 0002a000 08:02 3706124    /usr/lib/libpangoft2-1.0.so.0.1600.1
b7319000-b732d000 r-xp 00000000 08:02 3709233    /usr/lib/libart_lgpl_2.so.2.3.17
b732d000-b732e000 rw-p 00013000 08:02 3709233    /usr/lib/libart_lgpl_2.so.2.3.17
b732e000-b7335000 r-xp 00000000 08:02 4079934    /lib/libpopt.so.0.0.0
b7335000-b7336000 rw-p 00006000 08:02 4079934    /lib/libpopt.so.0.0.0
b7336000-b735f000 r-xp 00000000 08:02 3704942    /usr/lib/libgnomecanvas-2.so.0.1400.0
b735f000-b7360000 rw-p 00029000 08:02 3704942    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7360000-b7361000 rw-p b7360000 00:00 0 
b7361000-b73bc000 r-xp 00000000 08:02 3705309    /usr/lib/libbonoboui-2.so.0.0.0
b73bc000-b73bf000 rw-p 0005a000 08:02 3705309    /usr/lib/libbonoboui-2.so.0.0.0
b73bf000-b74d6000 r-xp 00000000 08:02 3706231    /usr/lib/libxml2.so.2.6.27
b74d6000-b74dc000 rw-p 00116000 08:02 3706231    /usr/lib/libxml2.so.2.6.27
b74dc000-b759c000 r-xp 00000000 08:02 3703708    /usr/lib/libasound.so.2.0.0
b759c000-b75a1000 rw-p 000bf000 08:02 3703708    /usr/lib/libasound.so.2.0.0
b75a1000-b75c6000 r-xp 00000000 08:02 4079697    /lib/tls/i686/cmov/libm-2.5.so
b75c6000-b75c8000 rw-p 00024000 08:02 4079697    /lib/tls/i686/cmov/libm-2.5.so
b75c8000-b75e8000 r-xp 00000000 08:02 3711208    /usr/lib/libaudiofile.so.0.0.2
b75e8000-b75ea000 rw-p 00020000 08:02 3711208    /usr/lib/libaudiofile.so.0.0.2
b75ea000-b7725000 r-xp 00000000 08:02 4079692    /lib/tls/i686/cmov/libc-2.5.so
b7725000-b7726000 r--p 0013b000 08:02 4079692    /lib/tls/i686/cmov/libc-2.5.so
b7726000-b7728000 rw-p 0013c000 08:02 4079692    /lib/tls/i686/cmov/libc-2.5.so
b7728000-b772c000 rw-p b7728000 00:00 0 
b772c000-b7733000 r-xp 00000000 08:02 4079651    /lib/libwrap.so.0.7.6
b7733000-b7734000 rw-p 00007000 08:02 4079651    /lib/libwrap.so.0.7.6
b7734000-b77c8000 r-xp 00000000 08:02 3704478    /usr/lib/libglib-2.0.so.0.1200.11
b77c8000-b77c9000 rw-p 00093000 08:02 3704478    /usr/lib/libglib-2.0.so.0.1200.11
b77c9000-b77d5000 r-xp 00000000 08:02 3707256    /usr/lib/libgnome-keyring.so.0.0.1
b77d5000-b77d6000 rw-p 0000b000 08:02 3707256    /usr/lib/libgnome-keyring.so.0.0.1
b77d6000-b780f000 r-xp 00000000 08:02 3704480    /usr/lib/libgobject-2.0.so.0.1200.11
b780f000-b7810000 rw-p 00039000 08:02 3704480    /usr/lib/libgobject-2.0.so.0.1200.11
b7810000-b7841000 r-xp 00000000 08:02 2376405    /usr/lib/libdbus-1.so.3.2.0
b7841000-b7842000 rw-p 00031000 08:02 2376405    /usr/lib/libdbus-1.so.3.2.0
b7842000-b785c000 r-xp 00000000 08:02 3704431    /usr/lib/libdbus-glib-1.so.2.1.0
b785c000-b785d000 rw-p 0001a000 08:02 3704431    /usr/lib/libdbus-glib-1.so.2.1.0
b785d000-b785e000 rw-p b785d000 00:00 0 
b785e000-b7871000 r-xp 00000000 08:02 2953106    /lib/tls/i686/cmov/libpthread-2.5.so
b7871000-b7873000 rw-p 00013000 08:02 2953106    /lib/tls/i686/cmov/libpthread-2.5.so
b7873000-b7875000 rw-p b7873000 00:00 0 
b7875000-b78be000 r-xp 00000000 08:02 3706136    /usr/lib/libORBit-2.so.0.1.0
b78be000-b78c8000 rw-p 00048000 08:02 3706136    /usr/lib/libORBit-2.so.0.1.0
b78c8000-b78f7000 r-xp 00000000 08:02 3706925    /usr/lib/libgconf-2.so.4.1.2
b78f7000-b78fa000 rw-p 0002e000 08:02 3706925    /usr/lib/libgconf-2.so.4.1.2
b78fa000-b790d000 r-xp 00000000 08:02 2376382    /usr/lib/libbonobo-activation.so.4.0.0
b790d000-b790f000 rw-p 00013000 08:02 2376382    /usr/lib/libbonobo-activation.so.4.0.0
b790f000-b7961000 r-xp 00000000 08:02 2376364    /usr/lib/libbonobo-2.so.0.0.0
b7961000-b796b000 rw-p 00051000 08:02 2376364    /usr/lib/libbonobo-2.so.0.0.0
b796b000-b796c000 rw-p b796b000 00:00 0 
b796c000-b7a53000 r-xp 00000000 08:02 3702972    /usr/lib/libX11.so.6.2.0
b7a53000-b7a57000 rw-p 000e7000 08:02 3702972    /usr/lib/libX11.so.6.2.0
b7a57000-b7a93000 r-xp 00000000 08:02 3704639    /usr/lib/libpango-1.0.so.0.1600.1
b7a93000-b7a95000 rw-p 0003b000 08:02 3704639    /usr/lib/libpango-1.0.so.0.1600.1
b7a95000-b7a9a000 r-xp 00000000 08:02 3702991    /usr/lib/libXrandr.so.2.1.0
b7a9a000-b7a9b000 rw-p 00005000 08:02 3702991    /usr/lib/libXrandr.so.2.1.0
b7a9b000-b7ab1000 r-xp 00000000 08:02 3708713    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ab1000-b7ab2000 rw-p 00015000 08:02 3708713    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7ab2000-b7acb000 r-xp 00000000 08:02 2376357    /usr/lib/libatk-1.0.so.0.1809.1
b7acb000-b7acd000 rw-p 00018000 08:02 2376357    /usr/lib/libatk-1.0.so.0.1809.1
b7acd000-b7b50000 r-xp 00000000 08:02 3708714    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b50000-b7b53000 rw-p 00083000 08:02 3708714    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b53000-b7b54000 rw-p b7b53000 00:00 0 
b7b54000-b7ea5000 r-xp 00000000 08:02 3708715    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7ea5000-b7eab000 rw-p 00351000 08:02 3708715    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7eab000-b7eac000 rw-p b7eab000 00:00 0 
b7eac000-b7ec0000 r-xp 00000000 08:02 3703709    /usr/lib/libgnome-2.so.0.1800.0
b7ec0000-b7ec1000 rw-p 00014000 08:02 3703709    /usr/lib/libgnome-2.so.0.1800.0
b7ec1000-b7ed6000 r-xp 00000000 08:02 3704358    /usr/lib/libICE.so.6.3.0
b7ed6000-b7ed8000 rw-p 00014000 08:02 3704358    /usr/lib/libICE.so.6.3.0
b7ed8000-b7ed9000 rw-p b7ed8000 00:00 0 
b7ed9000-b7ee1000 r-xp 00000000 08:02 3704364    /usr/lib/libSM.so.6.0.0
b7ee1000-b7ee2000 rw-p 00007000 08:02 3704364    /usr/lib/libSM.so.6.0.0
b7ee2000-b7f6c000 r-xp 00000000 08:02 3707263    /usr/lib/libgnomeui-2.so.0.1788.4
b7f6c000-b7f70000 rw-p 00089000 08:02 3707263    /usr/lib/libgnomeui-2.so.0.1788.4
b7f70000-b7f84000 r-xp 00000000 08:02 3704630    /usr/lib/libgnome-desktop-2.so.2.3.4
b7f84000-b7f85000 rw-p 00014000 08:02 3704630    /usr/lib/libgnome-desktop-2.so.2.3.4
b7f85000-b7f86000 rw-p b7f85000 00:00 0 
b7f86000-b7f8f000 r-xp 00000000 08:02 3709013    /usr/lib/libesd.so.0.2.36
b7f8f000-b7f90000 rw-p 00009000 08:02 3709013    /usr/lib/libesd.so.0.2.36
b7f90000-b7f92000 r-xp 00000000 08:02 3702953    /usr/lib/libXau.so.6.0.0
b7f92000-b7f93000 rw-p 00001000 08:02 3702953    /usr/lib/libXau.so.6.0.0
b7f95000-b7f96000 r--s 00000000 08:02 2886443    /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f96000-b7f97000 r--s 00000000 08:02 2886273    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b7f97000-b7fa3000 r-xp 00000000 08:02 3817641    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7fa3000-b7fa4000 rw-p 0000b000 08:02 3817641    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b7fa4000-b7fa5000 r-xp 00000000 08:02 3718740    /usr/lib/gconv/ISO8859-1.so
b7fa5000-b7fa7000 rw-p 00000000 08:02 3718740    /usr/lib/gconv/ISO8859-1.so
b7fa7000-b7fa8000 r--p 00000000 08:02 4065424    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fa8000-b7fa9000 r--p 00000000 08:02 4066806    /usr/lib/locale/en_US.utf8/LC_TIME
b7fa9000-b7faa000 r--p 00000000 08:02 4066807    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7faa000-b7fab000 r--p 00000000 08:02 4065429    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fab000-b7fac000 r--p 00000000 08:02 4067088    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fac000-b7fad000 r--p 00000000 08:02 4066808    /usr/lib/locale/en_US.utf8/LC_NAME
b7fad000-b7fae000 r--p 00000000 08:02 4066809    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fae000-b7faf000 r--p 00000000 08:02 4066810    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7faf000-b7fb0000 r--p 00000000 08:02 4066811    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fb0000-b7fb7000 r--s 00000000 08:02 3820844    /usr/lib/gconv/gconv-modules.cache
b7fb7000-b7fb8000 r--p 00000000 08:02 4066813    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fb8000-b7fba000 rw-p b7fb8000 00:00 0 
b7fba000-b7fd3000 r-xp 00000000 08:02 3999812    /lib/ld-2.5.so
b7fd3000-b7fd5000 rw-p 00019000 08:02 3999812    /lib/ld-2.5.so
bfb19000-bfb2f000 rw-p bfb19000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(update-notifier:7823): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by dbbolton on 2007-03-17
which login session causes this ? have you tried failsafe gnome ?

---

### Post by taser on 2007-03-17
It's a normal Gnome session. I've tried both failsafe and normal Gnome, with similar results; using a terminal session works OK. The first time I login using either type of Gnome session, it returns me to the login screen without any error screen or condition. After that first login, I get the message about my last login lasting less than 10 seconds.

---

### Post by zerohalo on 2007-04-21
Seems like others have the same problem. You might want to add your session log here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/93613)

---

