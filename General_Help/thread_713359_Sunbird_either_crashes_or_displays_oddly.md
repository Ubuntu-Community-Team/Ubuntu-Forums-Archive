---
title: "Sunbird either crashes or displays oddly"
date: 2008-03-02
forum: General Help
---

### Post by Arenlor on 2008-03-02
I'm using the current Ubuntu sunbird, tried to remove --purge and then install it again, no luck. Decided I'd try running it from command line to grab the output, here is the crash:
```
$ sunbird
*** cal_calendar_schema_version not found; initializing storage provider tables
cal_calendar_schema_version
cal_events
cal_todos
cal_attendees
cal_recurrence
cal_properties
Starting calendar alarm service
observer added
observer added
Segmentation fault
```

Here is another crash that I just experienced, this time it came up fine and looking alright, then died when I clicked:
```
$ sunbird
*** cal_calendar_schema_version not found; initializing storage provider tables
cal_calendar_schema_version
cal_events
cal_todos
cal_attendees
cal_recurrence
cal_properties
Starting calendar alarm service
observer added
observer added

(gecko:6354): GLib-GObject-WARNING **: IA__g_object_weak_unref: couldn't find weak ref 0xb77276b0(0x8adb048)
Segmentation fault
```

Another new crash:
```
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7b591de]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb76fd772]
/usr/lib/libgobject-2.0.so.0[0xb770e323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb770f60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb770fa09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c77498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7b536f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb79a906f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb79a973a]
/usr/lib/libgdk-x11-2.0.so.0[0xb79a979b]
/usr/lib/libgdk-x11-2.0.so.0[0xb798f5e8]
/usr/lib/libglib-2.0.so.0[0xb765f551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb766111c]
/usr/lib/libglib-2.0.so.0[0xb766455f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7664909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b539e4]
/usr/lib/sunbird/components/libwidget_gtk2.so[0xb67c873a]
/usr/lib/sunbird/components/libtoolkitcomps.so[0xb66dbab2]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:02 1176283    /usr/lib/sunbird/sunbird-bin
0805b000-0805c000 rw-p 00013000 08:02 1176283    /usr/lib/sunbird/sunbird-bin
0805c000-08d05000 rw-p 0805c000 00:00 0          [heap]
b2eb3000-b2eb4000 ---p b2eb3000 00:00 0 
b2eb4000-b36b4000 rw-p b2eb4000 00:00 0 
b36b4000-b36b5000 ---p b36b4000 00:00 0 
b36b5000-b3eb5000 rw-p b36b5000 00:00 0 
b3eb5000-b3eb6000 ---p b3eb5000 00:00 0 
b3eb6000-b46b6000 rw-p b3eb6000 00:00 0 
b46b6000-b470d000 r-xp 00000000 08:02 1176121    /usr/lib/sunbird/components/libstoragecomps.so
b470d000-b470f000 rw-p 00057000 08:02 1176121    /usr/lib/sunbird/components/libstoragecomps.so
b470f000-b4778000 r-xp 00000000 08:02 1176264    /usr/lib/sunbird/components/libcalbasecomps.so
b4778000-b4784000 rw-p 00069000 08:02 1176264    /usr/lib/sunbird/components/libcalbasecomps.so
b4784000-b47a7000 rw-p b4784000 00:00 0 
b47a7000-b4807000 rw-s 00000000 00:09 1605649    /SYSV00000000 (deleted)
b4807000-b4809000 r-xp 00000000 08:02 555456     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4809000-b480a000 rw-p 00001000 08:02 555456     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b480a000-b4847000 r--p 00000000 08:02 554144     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b4847000-b4882000 r--p 00000000 08:02 554145     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
b4882000-b48c6000 r--p 00000000 08:02 276967     /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b48c6000-b490c000 r--p 00000000 08:02 276965     /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b490c000-b4911000 r-xp 00000000 08:02 1176212    /usr/lib/sunbird/components/libtxmgr.so
b4911000-b4912000 rw-p 00004000 08:02 1176212    /usr/lib/sunbird/components/libtxmgr.so
b4912000-b4942000 r-xp 00000000 08:02 1176211    /usr/lib/sunbird/components/libeditor.so
b4942000-b4944000 rw-p 00030000 08:02 1176211    /usr/lib/sunbird/components/libeditor.so
b4944000-b4981000 r--p 00000000 08:02 554144     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b4981000-b4987000 r--s 00000000 08:02 784142     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4987000-b4989000 r--s 00000000 08:02 784231     /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-x86.cache-2
b4989000-b498f000 r--s 00000000 08:02 784230     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b498f000-b4991000 r--s 00000000 08:02 784229     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4991000-b4993000 r--s 00000000 08:02 784228     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b4993000-b4994000 r--s 00000000 08:02 784227     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4994000-b49ab000 r--s 00000000 08:02 784226     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b49ab000-b49ad000 r--s 00000000 08:02 784225     /var/cache/fontconfig/85130c034ee6c6a57445579585c0b546-x86.cache-2
b49ad000-b49af000 r--s 00000000 08:02 784224     /var/cache/fontconfig/80d0a1cf7989637baed91f874e3e11f6-x86.cache-2
b49af000-b49b1000 r--s 00000000 08:02 784223     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b49b1000-b49b5000 r--s 00000000 08:02 784222     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b49b5000-b49bc000 r--s 00000000 08:02 784173     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b49bc000-b49bd000 r--s 00000000 08:02 784245     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b49bd000-b49bf000 r--s 00000000 08:02 784244     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b49bf000-b49c2000 r--s 00000000 08:02 784243     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b49c2000-b49c6000 r--s 00000000 08:02 784242     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b49c6000-b49c8000 r--s 00000000 08:02 784241     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b49c8000-b49cb000 r--s 00000000 08:02 784240     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b49cb000-b49ce000 r--s 00000000 08:02 784239     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b49ce000-b49d0000 r--s 00000000 08:02 784238     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b49d0000-b49d1000 r--s 00000000 08:02 784237     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b49d1000-b49d3000 r--s 00000000 08:02 784236     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b49d3000-b49d9000 r--s 00000000 08:02 784235     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b49d9000-b49dd000 r--s 00000000 08:02 784220     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b49dd000-b49df000 r--s 00000000 08:02 784234     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b49df000-b49e2000 r--s 00000000 08:02 784221     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b49e2000-b49e6000 r--s 00000000 08:03 1016718    /home/arenlor/.fontconfig/00d1589c2fb27429ea004a02c7184b6f-x86.cache-2
b49e6000-b4a3f000 r-xp 00000000 08:02 1176154    /usr/lib/sunbird/components/libhtmlpars.so
b4a3f000-b4a47000 rw-p 00058000 08:02 1176154    /usr/lib/sunbird/components/libhtmlpars.so
b4a47000-b4b03000 r-xp 00000000 08:02 1176113    /usr/lib/sunbird/components/libuconv.so
b4b03000-b4b09000 rw-p 000bc000 08:02 1176113    /usr/lib/sunbird/components/libuconv.so
b4b09000-b4b13000 rw-p b4b09000 00:00 0 
b4b13000-b4b14000 ---p b4b13000 00:00 0 
b4b14000-b5314000 rw-p b4b14000 00:00 0 
b5314000-b5325000 r-xp 00000000 08:02 1176208    /usr/lib/sunbird/components/libwebbrwsr.so
b5325000-b5327000 rw-p 00010000 08:02 1176208    /usr/lib/sunbird/components/libwebbrwsr.so
b5327000-b5774000 r-xp 00000000 08:02 1176192    /usr/lib/sunbird/components/libgklayout.so
b5774000-b57ba000 rw-p 0044d000 08:02 1176192    /usr/lib/sunbird/components/libgklayout.so
b57ba000-b57c0000 rw-p b57ba000 00:00 0 
b57c0000-b57f6000 r-xp 00000000 08:02 293248     /lib/libsepol.so.1
b57f6000-b57f7000 rw-p 00035000 08:02 293248     /lib/libsepol.so.1
b57f7000-b5801000 rw-p b57f7000 00:00 0 
b5801000-b5850000 r-xp 00000000 08:02 509035     /usr/lib/libgcrypt.so.11.2.3
b5850000-b5852000 rw-p 0004e000 08:02 509035     /usr/lib/libgcrypt.so.11.2.3
b5852000-b5855000 r-xp 00000000 08:02 509037     /usr/lib/libgpg-error.so.0.3.0
b5855000-b5856000 rw-p 00002000 08:02 509037     /usr/lib/libgpg-error.so.0.3.0
b5856000-b5865000 r-xp 00000000 08:02 509281     /usr/lib/libtasn1.so.3.0.9
b5865000-b5866000 rw-p 0000e000 08:02 509281     /usr/lib/libtasn1.so.3.0.9
b5866000-b5927000 r-xp 00000000 08:02 507417     /usr/lib/libasound.so.2.0.0
b5927000-b592c000 rw-p 000c0000 08:02 507417     /usr/lib/libasound.so.2.0.0
b592c000-b5930000 r-xp 00000000 08:02 509633     /usr/lib/libORBitCosNaming-2.so.0.1.0
b5930000-b5931000 rw-p 00003000 08:02 509633     /usr/lib/libORBitCosNaming-2.so.0.1.0
b5931000-b5933000 r-xp 00000000 08:02 293224     /lib/tls/i686/cmov/libutil-2.6.1.so
b5933000-b5935000 rw-p 00001000 08:02 293224     /lib/tls/i686/cmov/libutil-2.6.1.so
b5935000-b5949000 r-xp 00000000 08:02 293247     /lib/libselinux.so.1
b5949000-b594b000 rw-p 00013000 08:02 293247     /lib/libselinux.so.1
b594b000-b595a000 r-xp 00000000 08:02 293220     /lib/tls/i686/cmov/libresolv-2.6.1.so
b595a000-b595c000 rw-p 0000f000 08:02 293220     /lib/tls/i686/cmov/libresolv-2.6.1.so
b595c000-b595e000 rw-p b595c000 00:00 0 
b595e000-b596c000 r-xp 00000000 08:02 511267     /usr/lib/libavahi-client.so.3.2.2
b596c000-b596d000 rw-p 0000e000 08:02 511267     /usr/lib/libavahi-client.so.3.2.2
b596d000-b5977000 r-xp 00000000 08:02 511265     /usr/lib/libavahi-common.so.3.4.4
b5977000-b5978000 rw-p 00009000 08:02 511265     /usr/lib/libavahi-common.so.3.4.4
b5978000-b597a000 r-xp 00000000 08:02 511269     /usr/lib/libavahi-glib.so.1.0.1
b597a000-b597b000 rw-p 00001000 08:02 511269     /usr/lib/libavahi-glib.so.1.0.1
b597b000-b59e5000 r-xp 00000000 08:02 508802     /usr/lib/libgnutls.so.13.3.0
b59e5000-b59eb000 rw-p 0006a000 08:02 508802     /usr/lib/libgnutls.so.13.3.0
b59eb000-b5a1f000 r-xp 00000000 08:02 508629     /usr/lib/libdbus-1.so.3.3.0
b5a1f000-b5a20000 rw-p 00033000 08:02 508629     /usr/lib/libdbus-1.so.3.3.0
b5a20000-b5a3a000 r-xp 00000000 08:02 509686     /usr/lib/libdbus-glib-1.so.2.1.0
b5a3a000-b5a3b000 rw-p 0001a000 08:02 509686     /usr/lib/libdbus-glib-1.so.2.1.0
b5a3b000-b5b53000 r-xp 00000000 08:02 509582     /usr/lib/libxml2.so.2.6.30
b5b53000-b5b58000 rw-p 00118000 08:02 509582     /usr/lib/libxml2.so.2.6.30
b5b58000-b5b59000 rw-p b5b58000 00:00 0 
b5b59000-b5b60000 r-xp 00000000 08:02 293427     /lib/libpopt.so.0.0.0
b5b60000-b5b61000 rw-p 00006000 08:02 293427     /lib/libpopt.so.0.0.0
b5b61000-b5b81000 r-xp 00000000 08:02 511252     /usr/lib/libaudiofile.so.0.0.2
b5b81000-b5b83000 rw-p 00020000 08:02 511252     /usr/lib/libaudiofile.so.0.0.2
b5b83000-b5b8c000 r-xp 00000000 08:02 511254     /usr/lib/libesd.so.0.2.38
b5b8c000-b5b8d000 rw-p 00009000 08:02 511254     /usr/lib/libesd.so.0.2.38
b5b8d000-b5ba0000 r-xp 00000000 08:02 511248     /usr/lib/libbonobo-activation.so.4.0.0
b5ba0000-b5ba2000 rw-p 00013000 08:02 511248     /usr/lib/libbonobo-activation.so.4.0.0
b5ba2000-b5bf4000 r-xp 00000000 08:02 511247     /usr/lib/libbonobo-2.so.0.0.0
b5bf4000-b5bfe000 rw-p 00051000 08:02 511247     /usr/lib/libbonobo-2.so.0.0.0
b5bfe000-b5c54000 r-xp 00000000 08:02 511274     /usr/lib/libgnomevfs-2.so.0.2000.0
b5c54000-b5c57000 rw-p 00055000 08:02 511274     /usr/lib/libgnomevfs-2.so.0.2000.0
b5c57000-b5c6b000 r-xp 00000000 08:02 511278     /usr/lib/libgnome-2.so.0.2000.0
b5c6b000-b5c6c000 rw-p 00014000 08:02 511278     /usr/lib/libgnome-2.so.0.2000.0
b5c6c000-b5c8b000 r-xp 00000000 08:02 509689     /usr/lib/libjpeg.so.62.0.0
b5c8b000-b5c8c000 rw-p 0001e000 08:02 509689     /usr/lib/libjpeg.so.62.0.0
b5c8c000-b5ca4000 r-xp 00000000 08:02 1176159    /usr/lib/sunbird/components/libimglib2.so
b5ca4000-b5ca6000 rw-p 00017000 08:02 1176159    /usr/lib/sunbird/components/libimglib2.so
b5ca6000-b5d06000 rw-s 00000000 00:09 1572880    /SYSV00000000 (deleted)
b5d06000-b5d17000 r-xp 00000000 08:02 509519     /usr/lib/libXft.so.2.1.2
b5d17000-b5d18000 rw-p 00010000 08:02 509519     /usr/lib/libXft.so.2.1.2
b5d1a000-b5d1d000 r-xp 00000000 08:02 1176224    /usr/lib/sunbird/components/libremoteservice.so
b5d1d000-b5d1e000 rw-p 00002000 08:02 1176224    /usr/lib/sunbird/components/libremoteservice.so
b5d1e000-b5d25000 r-xp 00000000 08:02 1176253    /usr/lib/sunbird/components/libpipboot.so
b5d25000-b5d26000 rw-p 00006000 08:02 1176253    /usr/lib/sunbird/components/libpipboot.so
b5d26000-b5d57000 r-xp 00000000 08:02 1176157    /usr/lib/sunbird/components/libgfx_gtk.so
b5d57000-b5d5a000 rw-p 00030000 08:02 1176157    /usr/lib/sunbird/components/libgfx_gtk.so
b5d5a000-b5d70000 r-xp 00000000 08:02 1176216    /usr/lib/sunbird/components/libnsappshell.so
b5d70000-b5d72000 rw-p 00015000 08:02 1176216    /usr/lib/sunbird/components/libnsappshell.so
b5d72000-b5d79000 r-xp 00000000 08:02 293221     /lib/tls/i686/cmov/librt-2.6.1.so
b5d79000-b5d7b000 rw-p 00006000 08:02 293221     /lib/tls/i686/cmov/librt-2.6.1.so
b5d7b000-b5d7f000 r-xp 00000000 08:02 509622     /usr/lib/libgthread-2.0.so.0.1400.1
b5d7f000-b5d80000 rw-p 00003000 08:02 509622     /usr/lib/libgthread-2.0.so.0.1400.1
b5d80000-b5dc9000 r-xp 00000000 08:02 509631     /usr/lib/libORBit-2.so.0.1.0
b5dc9000-b5dd2000 rw-p 00049000 08:02 509631     /usr/lib/libORBit-2.so.0.1.0
b5dd2000-b5dd3000 rw-p b5dd2000 00:00 0 
b5dd3000-b5e02000 r-xp 00000000 08:02 509637     /usr/lib/libgconf-2.so.4.1.2
b5e02000-b5e05000 rw-p 0002e000 08:02 509637     /usr/lib/libgconf-2.so.4.1.2
b5e07000-b5e0d000 r-xp 00000000 08:02 555521     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5e0d000-b5e0e000 rw-p 00005000 08:02 555521     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5e0e000-b5e12000 r-xp 00000000 08:02 1176239    /usr/lib/sunbird/components/libcommandlines.so
b5e12000-b5e13000 rw-p 00003000 08:02 1176239    /usr/lib/sunbird/components/libcommandlines.so
b5e13000-b5e18000 r-xp 00000000 08:02 1176282    /usr/lib/sunbird/components/libsystem-pref.so
b5e18000-b5e19000 rw-p 00004000 08:02 1176282    /usr/lib/sunbird/components/libsystem-pref.so
b5e19000-b5e65000 r-xp 00000000 08:02 1176195    /usr/lib/sunbird/components/libdocshell.so
b5e65000-b5e69000 rw-p 0004b000 08:02 1176195    /usr/lib/sunbird/components/libdocshell.so
b5e69000-b5e90000 r-xp 00000000 08:02 1176151    /usr/lib/sunbird/components/librdf.so
b5e90000-b5e92000 rw-p 00026000 08:02 1176151    /usr/lib/sunbird/components/librdf.so
b5e92000-b5e93000 ---p b5e92000 00:00 0 
b5e93000-b6693000 rw-p b5e93000 00:00 0 
b6693000-b66a6000 r-xp 00000000 08:02 1176149    /usr/lib/sunbird/components/libcaps.so
b66a6000-b66a7000 rw-p 00013000 08:02 1176149    /usr/lib/sunbird/components/libcaps.so
b66a7000-b66d1000 r-xp 00000000 08:02 1176206    /usr/lib/sunbird/components/libembedcomponents.so
b66d1000-b66d3000 rw-p 0002a000 08:02 1176206    /usr/lib/sunbird/components/libembedcomponents.so
b66d3000-b6713000 r-xp 00000000 08:02 1176242    /usr/lib/sunbird/components/libtoolkitcomps.so
b6713000-b6716000 rw-p 00040000 08:02 1176242    /usr/lib/sunbird/components/libtoolkitcomps.so
b6716000-b672b000 r-xp 00000000 08:02 509521     /usr/lib/libICE.so.6.3.0
b672b000-b672d000 rw-p 00014000 08:02 509521     /usr/lib/libICE.so.6.3.0
b672d000-b672e000 rw-p b672d000 00:00 0 
b672e000-b6735000 r-xp 00000000 08:02 509523     /usr/lib/libSM.so.6.0.0
b6735000-b6736000 rw-p 00006000 08:02 509523     /usr/lib/libSM.so.6.0.0
b6736000-b6783000 r-xp 00000000 08:02 509525     /usr/lib/libXt.so.6.0.0
b6783000-b6787000 rw-p 0004c000 08:02 509525     /usr/lib/libXt.so.6.0.0
b6788000-b6794000 r-xp 00000000 08:02 578288     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6794000-b6795000 rw-p 0000c000 08:02 578288     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6795000-b67b2000 r-xp 00000000 08:02 1176083    /usr/lib/sunbird/libgkgfx.so
b67b2000-b67b4000 rw-p 0001c000 08:02 1176083    /usr/lib/sunbird/libgkgfx.so
b67b4000-b67df000 r-xp 00000000 08:02 1176178    /usr/lib/sunbird/components/libwidget_gtk2.so
b67df000-b67e3000 rw-p 0002b000 08:02 1176178    /usr/lib/sunbird/components/libwidget_gtk2.so
b67e3000-b67f4000 r-xp 00000000 08:02 1176141    /usr/lib/sunbird/components/libjar50.so
b67f4000-b67f5000 rw-p 00011000 08:02 1176141    /usr/lib/sunbird/components/libjar50.so
b67f5000-b6840000 r-xp 00000000 08:02 1176108    /usr/lib/sunbird/components/libxpconnect.so
b6840000-b6844000 rw-p 0004b000 08:02 1176108    /usr/lib/sunbird/components/libxpconnect.so
b6844000-b6845000 ---p b6844000 00:00 0 
b6845000-b7045000 rw-p b6845000 00:00 0 
b7045000-b707b000 r-xp 00000000 08:02 1176118    /usr/lib/sunbird/components/libi18n.so
b707b000-b707e000 rw-p 00035000 08:02 1176118    /usr/lib/sunbird/components/libi18n.so
b707e000-b7085000 r-xp 00000000 08:02 1176281    /usr/lib/sunbird/components/libautoconfig.so
b7085000-b7086000 rw-p 00006000 08:02 1176281    /usr/lib/sunbird/components/libautoconfig.so
b7086000-b7135000 r-xp 00000000 08:02 1176139    /usr/lib/sunbird/components/libnecko.so
b7135000-b713d000 rw-p 000af000 08:02 1176139    /usr/lib/sunbird/components/libnecko.so
b713d000-b714b000 r-xp 00000000 08:02 1176147    /usr/lib/sunbird/components/libpref.so
b714b000-b714c000 rw-p 0000e000 08:02 1176147    /usr/lib/sunbird/components/libpref.so
b714c000-b715b000 r-xp 00000000 08:02 1176221    /usr/lib/sunbird/components/libchrome.so
b715b000-b715c000 rw-p 0000f000 08:02 1176221    /usr/lib/sunbird/components/libchrome.so
b715c000-b7165000 r-xp 00000000 08:02 293214     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7165000-b7167000 rw-p 00008000 08:02 293214     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7167000-b716f000 r-xp 00000000 08:02 293216     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b716f000-b7171000 rw-p 00007000 08:02 293216     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7171000-b7185000 r-xp 00000000 08:02 293211     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7185000-b7187000 rw-p 00013000 08:02 293211     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7187000-b7189000 rw-p b7187000 00:00 0 
b7189000-b7190000 r-xp 00000000 08:02 293212     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7190000-b7192000 rw-p 00006000 08:02 293212     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7192000-b7194000 r-xp 00000000 08:02 1176082    /usr/lib/sunbird/libgfxpsshar.so
b7194000-b7195000 rw-p 00001000 08:02 1176082    /usr/lib/sunbird/libgfxpsshar.so
b7195000-b7198000 r-xp 00000000 08:02 1176085    /usr/lib/sunbird/libgtkxtbin.so
b7198000-b7199000 rw-p 00003000 08:02 1176085    /usr/lib/sunbird/libgtkxtbin.so
b7199000-b719b000 r-xp 00000000 08:02 511192     /usr/lib/gconv/UTF-16.so
b719b000-b719d000 rw-p 00001000 08:02 511192     /usr/lib/gconv/UTF-16.so
b719d000-b719e000 r-xp 00000000 08:02 511138     /usr/lib/gconv/ISO8859-1.so
b719e000-b71a0000 rw-p 00000000 08:02 511138     /usr/lib/gconv/ISO8859-1.so
b71a0000-b71df000 r--p 00000000 08:02 539919     /usr/lib/locale/en_US.utf8/LC_CTYPE
b71df000-b71e0000 r--p 00000000 08:02 539920     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b71e0000-b71e1000 r--p 00000000 08:02 539921     /usr/lib/locale/en_US.utf8/LC_TIME
b71e1000-b72c1000 r--p 00000000 08:02 539922     /usr/lib/locale/en_US.utf8/LC_COLLATE
b72c1000-b72c2000 r--p 00000000 08:02 539923     /usr/lib/locale/en_US.utf8/LC_MONETARY
b72c2000-b72c5000 rw-p b72c2000 00:00 0 
b72c5000-b72c9000 r-xp 00000000 08:02 506614     /usr/lib/libXdmcp.so.6.0.0
b72c9000-b72ca000 rw-p 00003000 08:02 506614     /usr/lib/libXdmcp.so.6.0.0
b72ca000-b72ec000 r-xp 00000000 08:02 509682     /usr/lib/libpng12.so.0.15.0
b72ec000-b72ed000 rw-p 00021000 08:02 509682     /usr/lib/libpng12.so.0.15.0
b72ed000-b72ef000 r-xp 00000000 08:02 506612     /usr/lib/libXau.so.6.0.0
b72ef000-b72f0000 rw-p 00001000 08:02 506612     /usr/lib/libXau.so.6.0.0
b72f0000-b730e000 r-xp 00000000 08:02 510334     /usr/lib/libexpat.so.1.0.0
b730e000-b7310000 rw-p 0001e000 08:02 510334     /usr/lib/libexpat.so.1.0.0
b7310000-b7311000 rw-p b7310000 00:00 0 
b7311000-b7325000 r-xp 00000000 08:02 507056     /usr/lib/libz.so.1.2.3.3
b7325000-b7326000 rw-p 00013000 08:02 507056     /usr/lib/libz.so.1.2.3.3
b7326000-b7392000 r-xp 00000000 08:02 506624     /usr/lib/libfreetype.so.6.3.16
b7392000-b7396000 rw-p 0006b000 08:02 506624     /usr/lib/libfreetype.so.6.3.16
b7396000-b73c3000 r-xp 00000000 08:02 510403     /usr/lib/libpangoft2-1.0.so.0.1800.3
b73c3000-b73c4000 rw-p 0002c000 08:02 510403     /usr/lib/libpangoft2-1.0.so.0.1800.3
b73c4000-b7508000 r-xp 00000000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b7508000-b7509000 r--p 00143000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b7509000-b750b000 rw-p 00144000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b750b000-b750f000 rw-p b750b000 00:00 0 
b750f000-b7519000 r-xp 00000000 08:02 293198     /lib/libgcc_s.so.1
b7519000-b751a000 rw-p 0000a000 08:02 293198     /lib/libgcc_s.so.1
b751a000-b7602000 r-xp 00000000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b7602000-b7605000 r--p 000e8000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b7605000-b7607000 rw-p 000eb000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b7607000-b760d000 rw-p b7607000 00:00 0 
b760d000-b7630000 r-xp 00000000 08:02 293209     /lib/tls/i686/cmov/libm-2.6.1.so
b7630000-b7632000 rw-p 00023000 08:02 293209     /lib/tls/i686/cmov/libm-2.6.1.so
b7632000-b76ee000 r-xp 00000000 08:02 509619     /usr/lib/libglib-2.0.so.0.1400.1
b76ee000-b76ef000 rw-p 000bc000 08:02 509619     /usr/lib/libglib-2.0.so.0.1400.1
b76ef000-b76f2000 r-xp 00000000 08:02 509620     /usr/lib/libgmodule-2.0.so.0.1400.1
b76f2000-b76f3000 rw-p 00002000 08:02 509620     /usr/lib/libgmodule-2.0.so.0.1400.1
b76f3000-b772d000 r-xp 00000000 08:02 509621     /usr/lib/libgobject-2.0.so.0.1400.1
b772d000-b772e000 rw-p 0003a000 08:02 509621     /usr/lib/libgobject-2.0.so.0.1400.1
b772e000-b772f000 rw-p b772e000 00:00 0 
b772f000-b7733000 r-xp 00000000 08:02 506622     /usr/lib/libXfixes.so.3.1.0
b7733000-b7734000 rw-p 00003000 08:02 506622     /usr/lib/libXfixes.so.3.1.0
b7734000-b7821000 r-xp 00000000 08:02 506616     /usr/lib/libX11.so.6.2.0
b7821000-b7825000 rw-p 000ed000 08:02 506616     /usr/lib/libX11.so.6.2.0
b7825000-b789a000 r-xp 00000000 08:02 509684     /usr/lib/libcairo.so.2.11.5
b789a000-b789c000 rw-p 00074000 08:02 509684     /usr/lib/libcairo.so.2.11.5
b789c000-b78d7000 r-xp 00000000 08:02 510401     /usr/lib/libpango-1.0.so.0.1800.3
b78d7000-b78d9000 rw-p 0003b000 08:02 510401     /usr/lib/libpango-1.0.so.0.1800.3
b78d9000-b78db000 r-xp 00000000 08:02 510442     /usr/lib/libXdamage.so.1.1.0
b78db000-b78dc000 rw-p 00001000 08:02 510442     /usr/lib/libXdamage.so.1.1.0
b78dc000-b78de000 r-xp 00000000 08:02 510438     /usr/lib/libXcomposite.so.1.0.0
b78de000-b78df000 rw-p 00001000 08:02 510438     /usr/lib/libXcomposite.so.1.0.0
b78df000-b78e0000 rw-p b78df000 00:00 0 
b78e0000-b78e8000 r-xp 00000000 08:02 510440     /usr/lib/libXcursor.so.1.0.2
b78e8000-b78e9000 rw-p 00007000 08:02 510440     /usr/lib/libXcursor.so.1.0.2
b78e9000-b78ee000 r-xp 00000000 08:02 510813     /usr/lib/libXrandr.so.2.1.0
b78ee000-b78ef000 rw-p 00005000 08:02 510813     /usr/lib/libXrandr.so.2.1.0
b78ef000-b78f6000 r-xp 00000000 08:02 510809     /usr/lib/libXi.so.6.0.0
b78f6000-b78f7000 rw-p 00006000 08:02 510809     /usr/lib/libXi.so.6.0.0
b78f7000-b78f9000 r-xp 00000000 08:02 510811     /usr/lib/libXinerama.so.1.0.0
b78f9000-b78fa000 rw-p 00001000 08:02 510811     /usr/lib/libXinerama.so.1.0.0
b78fa000-b7901000 r-xp 00000000 08:02 509517     /usr/lib/libXrender.so.1.3.0
b7901000-b7902000 rw-p 00006000 08:02 509517     /usr/lib/libXrender.so.1.3.0
b7902000-b790f000 r-xp 00000000 08:02 506618     /usr/lib/libXext.so.6.4.0
b790f000-b7910000 rw-p 0000d000 08:02 506618     /usr/lib/libXext.so.6.4.0
b7910000-b7911000 rw-p b7910000 00:00 0 
b7911000-b7934000 r-xp 00000000 08:02 509515     /usr/lib/libfontconfig.so.1.2.0
b7934000-b793c000 rw-p 00023000 08:02 509515     /usr/lib/libfontconfig.so.1.2.0
b793c000-b7944000 r-xp 00000000 08:02 510402     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7944000-b7945000 rw-p 00007000 08:02 510402     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7945000-b795c000 r-xp 00000000 08:02 510816     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b795c000-b795d000 rw-p 00016000 08:02 510816     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b795d000-b7976000 r-xp 00000000 08:02 509679     /usr/lib/libatk-1.0.so.0.2009.1
b7976000-b7978000 rw-p 00018000 08:02 509679     /usr/lib/libatk-1.0.so.0.2009.1
b7978000-b79fc000 r-xp 00000000 08:02 510815     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79fc000-b79ff000 rw-p 00084000 08:02 510815     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79ff000-b7d7c000 r-xp 00000000 08:02 510818     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d7c000-b7d83000 rw-p 0037c000 08:02 510818     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d83000-b7d85000 rw-p b7d83000 00:00 0 
b7d85000-b7d87000 r-xp 00000000 08:02 293208     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d87000-b7d89000 rw-p 00001000 08:02 293208     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d89000-b7d9d000 r-xp 00000000 08:02 293219     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d9d000-b7d9f000 rw-p 00013000 08:02 293219     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d9f000-b7da1000 rw-p b7d9f000 00:00 0 
b7da1000-b7dcf000 r-xp 00000000 08:02 511286     /usr/lib/libnspr4.so.0d
b7dcf000-b7dd0000 rw-p 0002e000 08:02 511286     /usr/lib/libnspr4.so.0d
b7dd0000-b7dd2000 rw-p b7dd0000 00:00 0 
b7dd2000-b7dd6000 r-xp 00000000 08:02 511287     /usr/lib/libplc4.so.0d
b7dd6000-b7dd7000 rw-p 00003000 08:02 511287     /usr/lib/libplc4.so.0d
b7dd7000-b7dd9000 r-xp 00000000 08:02 511288     /usr/lib/libplds4.so.0d
b7dd9000-b7dda000 rw-p 00001000 08:02 511288     /usr/lib/libplds4.so.0d
b7dda000-b7ddb000 r--p 00000000 08:02 539925     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7ddb000-b7ddc000 r--p 00000000 08:02 539926     /usr/lib/locale/en_US.utf8/LC_PAPER
b7ddc000-b7ddd000 r--p 00000000 08:02 539927     /usr/lib/locale/en_US.utf8/LC_NAME
b7ddd000-b7dde000 r--p 00000000 08:02 539928     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7dde000-b7ddf000 r--p 00000000 08:02 539929     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7ddf000-b7de0000 r--p 00000000 08:02 539930     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7de0000-b7de7000 r--s 00000000 08:02 505906     /usr/lib/gconv/gconv-modules.cache
b7de7000-b7de8000 r--p 00000000 08:02 539931     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7de8000-b7e8a000 r-xp 00000000 08:02 1176089    /usr/lib/sunbird/libxpcom_core.so
b7e8a000-b7e92000 rw-p 000a1000 08:02 1176089    /usr/lib/sunbird/libxpcom_core.so
b7e92000-b7e93000 rw-p b7e92000 00:00 0 
b7e93000-b7e95000 r-xp 00000000 08:02 1176087    /usr/lib/sunbird/libxpcom.so
b7e95000-b7e96000 rw-p 00002000 08:02 1176087    /usr/lib/sunbird/libxpcom.so
b7e96000-b7f3d000 r-xp 00000000 08:02 1176086    /usr/lib/sunbird/libmozjs.so
b7f3d000-b7f42000 rw-p 000a7000 08:02 1176086    /usr/lib/sunbird/libmozjs.so
b7f42000-b7f44000 rw-p b7f42000 00:00 0 
b7f44000-b7f5e000 r-xp 00000000 08:02 296346     /lib/ld-2.6.1.so
b7f5e000-b7f60000 rw-p 00019000 08:02 296346     /lib/ld-2.6.1.so
bff18000-bff2d000 rw-p bff18000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted
```

And the time when it starts up but freezes:
```
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb76dc772]
/usr/lib/libgobject-2.0.so.0[0xb76ed323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb76ee60f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb76eea09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c56498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x475)[0xb7b326f5]
/usr/lib/libgdk-x11-2.0.so.0[0xb798806f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb798873a]
/usr/lib/libgdk-x11-2.0.so.0[0xb798879b]
/usr/lib/libgdk-x11-2.0.so.0[0xb796e5e8]
/usr/lib/libglib-2.0.so.0[0xb763e551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb764011c]
/usr/lib/libglib-2.0.so.0[0xb764355f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7643909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7b329e4]
/usr/lib/sunbird/components/libwidget_gtk2.so[0xb67a773a]
======= Memory map: ========
08048000-0805b000 r-xp 00000000 08:02 1176283    /usr/lib/sunbird/sunbird-bin
0805b000-0805c000 rw-p 00013000 08:02 1176283    /usr/lib/sunbird/sunbird-bin
0805c000-08d04000 rw-p 0805c000 00:00 0          [heap]
b2d00000-b2d21000 rw-p b2d00000 00:00 0 
b2d21000-b2e00000 ---p b2d21000 00:00 0 
b2e92000-b2e93000 ---p b2e92000 00:00 0 
b2e93000-b3693000 rw-p b2e93000 00:00 0 
b3693000-b3694000 ---p b3693000 00:00 0 
b3694000-b3e94000 rw-p b3694000 00:00 0 
b3e94000-b3e95000 ---p b3e94000 00:00 0 
b3e95000-b4695000 rw-p b3e95000 00:00 0 
b4695000-b46ec000 r-xp 00000000 08:02 1176121    /usr/lib/sunbird/components/libstoragecomps.so
b46ec000-b46ee000 rw-p 00057000 08:02 1176121    /usr/lib/sunbird/components/libstoragecomps.so
b46ee000-b4757000 r-xp 00000000 08:02 1176264    /usr/lib/sunbird/components/libcalbasecomps.so
b4757000-b4763000 rw-p 00069000 08:02 1176264    /usr/lib/sunbird/components/libcalbasecomps.so
b4763000-b4786000 rw-p b4763000 00:00 0 
b4786000-b47e6000 rw-s 00000000 00:09 1802257    /SYSV00000000 (deleted)
b47e6000-b47e8000 r-xp 00000000 08:02 555456     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b47e8000-b47e9000 rw-p 00001000 08:02 555456     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b47e9000-b4826000 r--p 00000000 08:02 554144     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b4826000-b4861000 r--p 00000000 08:02 554145     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
b4861000-b48a5000 r--p 00000000 08:02 276967     /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
b48a5000-b48eb000 r--p 00000000 08:02 276965     /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
b48eb000-b48f0000 r-xp 00000000 08:02 1176212    /usr/lib/sunbird/components/libtxmgr.so
b48f0000-b48f1000 rw-p 00004000 08:02 1176212    /usr/lib/sunbird/components/libtxmgr.so
b48f1000-b4921000 r-xp 00000000 08:02 1176211    /usr/lib/sunbird/components/libeditor.so
b4921000-b4923000 rw-p 00030000 08:02 1176211    /usr/lib/sunbird/components/libeditor.so
b4923000-b4960000 r--p 00000000 08:02 554144     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b4960000-b4966000 r--s 00000000 08:02 784142     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4966000-b4968000 r--s 00000000 08:02 784231     /var/cache/fontconfig/f24b2111ab8703b4e963115a8cf14259-x86.cache-2
b4968000-b496e000 r--s 00000000 08:02 784230     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b496e000-b4970000 r--s 00000000 08:02 784229     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4970000-b4972000 r--s 00000000 08:02 784228     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b4972000-b4973000 r--s 00000000 08:02 784227     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4973000-b498a000 r--s 00000000 08:02 784226     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b498a000-b498c000 r--s 00000000 08:02 784225     /var/cache/fontconfig/85130c034ee6c6a57445579585c0b546-x86.cache-2
b498c000-b498e000 r--s 00000000 08:02 784224     /var/cache/fontconfig/80d0a1cf7989637baed91f874e3e11f6-x86.cache-2
b498e000-b4990000 r--s 00000000 08:02 784223     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4990000-b4994000 r--s 00000000 08:02 784222     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4994000-b499b000 r--s 00000000 08:02 784173     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b499b000-b499c000 r--s 00000000 08:02 784245     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b499c000-b499e000 r--s 00000000 08:02 784244     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b499e000-b49a1000 r--s 00000000 08:02 784243     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b49a1000-b49a5000 r--s 00000000 08:02 784242     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b49a5000-b49a7000 r--s 00000000 08:02 784241     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b49a7000-b49aa000 r--s 00000000 08:02 784240     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b49aa000-b49ad000 r--s 00000000 08:02 784239     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b49ad000-b49af000 r--s 00000000 08:02 784238     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b49af000-b49b0000 r--s 00000000 08:02 784237     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b49b0000-b49b2000 r--s 00000000 08:02 784236     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b49b2000-b49b8000 r--s 00000000 08:02 784235     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b49b8000-b49bc000 r--s 00000000 08:02 784220     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b49bc000-b49be000 r--s 00000000 08:02 784234     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b49be000-b49c1000 r--s 00000000 08:02 784221     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b49c1000-b49c5000 r--s 00000000 08:03 1016718    /home/arenlor/.fontconfig/00d1589c2fb27429ea004a02c7184b6f-x86.cache-2
b49c5000-b4a1e000 r-xp 00000000 08:02 1176154    /usr/lib/sunbird/components/libhtmlpars.so
b4a1e000-b4a26000 rw-p 00058000 08:02 1176154    /usr/lib/sunbird/components/libhtmlpars.so
b4a26000-b4ae2000 r-xp 00000000 08:02 1176113    /usr/lib/sunbird/components/libuconv.so
b4ae2000-b4ae8000 rw-p 000bc000 08:02 1176113    /usr/lib/sunbird/components/libuconv.so
b4ae8000-b4af2000 rw-p b4ae8000 00:00 0 
b4af2000-b4af3000 ---p b4af2000 00:00 0 
b4af3000-b52f3000 rw-p b4af3000 00:00 0 
b52f3000-b5304000 r-xp 00000000 08:02 1176208    /usr/lib/sunbird/components/libwebbrwsr.so
b5304000-b5306000 rw-p 00010000 08:02 1176208    /usr/lib/sunbird/components/libwebbrwsr.so
b5306000-b5753000 r-xp 00000000 08:02 1176192    /usr/lib/sunbird/components/libgklayout.so
b5753000-b5799000 rw-p 0044d000 08:02 1176192    /usr/lib/sunbird/components/libgklayout.so
b5799000-b579f000 rw-p b5799000 00:00 0 
b579f000-b57d5000 r-xp 00000000 08:02 293248     /lib/libsepol.so.1
b57d5000-b57d6000 rw-p 00035000 08:02 293248     /lib/libsepol.so.1
b57d6000-b57e0000 rw-p b57d6000 00:00 0 
b57e0000-b582f000 r-xp 00000000 08:02 509035     /usr/lib/libgcrypt.so.11.2.3
b582f000-b5831000 rw-p 0004e000 08:02 509035     /usr/lib/libgcrypt.so.11.2.3
b5831000-b5834000 r-xp 00000000 08:02 509037     /usr/lib/libgpg-error.so.0.3.0
b5834000-b5835000 rw-p 00002000 08:02 509037     /usr/lib/libgpg-error.so.0.3.0
b5835000-b5844000 r-xp 00000000 08:02 509281     /usr/lib/libtasn1.so.3.0.9
b5844000-b5845000 rw-p 0000e000 08:02 509281     /usr/lib/libtasn1.so.3.0.9
b5845000-b5906000 r-xp 00000000 08:02 507417     /usr/lib/libasound.so.2.0.0
b5906000-b590b000 rw-p 000c0000 08:02 507417     /usr/lib/libasound.so.2.0.0
b590b000-b590f000 r-xp 00000000 08:02 509633     /usr/lib/libORBitCosNaming-2.so.0.1.0
b590f000-b5910000 rw-p 00003000 08:02 509633     /usr/lib/libORBitCosNaming-2.so.0.1.0
b5910000-b5912000 r-xp 00000000 08:02 293224     /lib/tls/i686/cmov/libutil-2.6.1.so
b5912000-b5914000 rw-p 00001000 08:02 293224     /lib/tls/i686/cmov/libutil-2.6.1.so
b5914000-b5928000 r-xp 00000000 08:02 293247     /lib/libselinux.so.1
b5928000-b592a000 rw-p 00013000 08:02 293247     /lib/libselinux.so.1
b592a000-b5939000 r-xp 00000000 08:02 293220     /lib/tls/i686/cmov/libresolv-2.6.1.so
b5939000-b593b000 rw-p 0000f000 08:02 293220     /lib/tls/i686/cmov/libresolv-2.6.1.so
b593b000-b593d000 rw-p b593b000 00:00 0 
b593d000-b594b000 r-xp 00000000 08:02 511267     /usr/lib/libavahi-client.so.3.2.2
b594b000-b594c000 rw-p 0000e000 08:02 511267     /usr/lib/libavahi-client.so.3.2.2
b594c000-b5956000 r-xp 00000000 08:02 511265     /usr/lib/libavahi-common.so.3.4.4
b5956000-b5957000 rw-p 00009000 08:02 511265     /usr/lib/libavahi-common.so.3.4.4
b5957000-b5959000 r-xp 00000000 08:02 511269     /usr/lib/libavahi-glib.so.1.0.1
b5959000-b595a000 rw-p 00001000 08:02 511269     /usr/lib/libavahi-glib.so.1.0.1
b595a000-b59c4000 r-xp 00000000 08:02 508802     /usr/lib/libgnutls.so.13.3.0
b59c4000-b59ca000 rw-p 0006a000 08:02 508802     /usr/lib/libgnutls.so.13.3.0
b59ca000-b59fe000 r-xp 00000000 08:02 508629     /usr/lib/libdbus-1.so.3.3.0
b59fe000-b59ff000 rw-p 00033000 08:02 508629     /usr/lib/libdbus-1.so.3.3.0
b59ff000-b5a19000 r-xp 00000000 08:02 509686     /usr/lib/libdbus-glib-1.so.2.1.0
b5a19000-b5a1a000 rw-p 0001a000 08:02 509686     /usr/lib/libdbus-glib-1.so.2.1.0
b5a1a000-b5b32000 r-xp 00000000 08:02 509582     /usr/lib/libxml2.so.2.6.30
b5b32000-b5b37000 rw-p 00118000 08:02 509582     /usr/lib/libxml2.so.2.6.30
b5b37000-b5b38000 rw-p b5b37000 00:00 0 
b5b38000-b5b3f000 r-xp 00000000 08:02 293427     /lib/libpopt.so.0.0.0
b5b3f000-b5b40000 rw-p 00006000 08:02 293427     /lib/libpopt.so.0.0.0
b5b40000-b5b60000 r-xp 00000000 08:02 511252     /usr/lib/libaudiofile.so.0.0.2
b5b60000-b5b62000 rw-p 00020000 08:02 511252     /usr/lib/libaudiofile.so.0.0.2
b5b62000-b5b6b000 r-xp 00000000 08:02 511254     /usr/lib/libesd.so.0.2.38
b5b6b000-b5b6c000 rw-p 00009000 08:02 511254     /usr/lib/libesd.so.0.2.38
b5b6c000-b5b7f000 r-xp 00000000 08:02 511248     /usr/lib/libbonobo-activation.so.4.0.0
b5b7f000-b5b81000 rw-p 00013000 08:02 511248     /usr/lib/libbonobo-activation.so.4.0.0
b5b81000-b5bd3000 r-xp 00000000 08:02 511247     /usr/lib/libbonobo-2.so.0.0.0
b5bd3000-b5bdd000 rw-p 00051000 08:02 511247     /usr/lib/libbonobo-2.so.0.0.0
b5bdd000-b5c33000 r-xp 00000000 08:02 511274     /usr/lib/libgnomevfs-2.so.0.2000.0
b5c33000-b5c36000 rw-p 00055000 08:02 511274     /usr/lib/libgnomevfs-2.so.0.2000.0
b5c36000-b5c4a000 r-xp 00000000 08:02 511278     /usr/lib/libgnome-2.so.0.2000.0
b5c4a000-b5c4b000 rw-p 00014000 08:02 511278     /usr/lib/libgnome-2.so.0.2000.0
b5c4b000-b5c6a000 r-xp 00000000 08:02 509689     /usr/lib/libjpeg.so.62.0.0
b5c6a000-b5c6b000 rw-p 0001e000 08:02 509689     /usr/lib/libjpeg.so.62.0.0
b5c6b000-b5c83000 r-xp 00000000 08:02 1176159    /usr/lib/sunbird/components/libimglib2.so
b5c83000-b5c85000 rw-p 00017000 08:02 1176159    /usr/lib/sunbird/components/libimglib2.so
b5c85000-b5ce5000 rw-s 00000000 00:09 1769488    /SYSV00000000 (deleted)
b5ce5000-b5cf6000 r-xp 00000000 08:02 509519     /usr/lib/libXft.so.2.1.2
b5cf6000-b5cf7000 rw-p 00010000 08:02 509519     /usr/lib/libXft.so.2.1.2
b5cf9000-b5cfc000 r-xp 00000000 08:02 1176224    /usr/lib/sunbird/components/libremoteservice.so
b5cfc000-b5cfd000 rw-p 00002000 08:02 1176224    /usr/lib/sunbird/components/libremoteservice.so
b5cfd000-b5d04000 r-xp 00000000 08:02 1176253    /usr/lib/sunbird/components/libpipboot.so
b5d04000-b5d05000 rw-p 00006000 08:02 1176253    /usr/lib/sunbird/components/libpipboot.so
b5d05000-b5d36000 r-xp 00000000 08:02 1176157    /usr/lib/sunbird/components/libgfx_gtk.so
b5d36000-b5d39000 rw-p 00030000 08:02 1176157    /usr/lib/sunbird/components/libgfx_gtk.so
b5d39000-b5d4f000 r-xp 00000000 08:02 1176216    /usr/lib/sunbird/components/libnsappshell.so
b5d4f000-b5d51000 rw-p 00015000 08:02 1176216    /usr/lib/sunbird/components/libnsappshell.so
b5d51000-b5d58000 r-xp 00000000 08:02 293221     /lib/tls/i686/cmov/librt-2.6.1.so
b5d58000-b5d5a000 rw-p 00006000 08:02 293221     /lib/tls/i686/cmov/librt-2.6.1.so
b5d5a000-b5d5e000 r-xp 00000000 08:02 509622     /usr/lib/libgthread-2.0.so.0.1400.1
b5d5e000-b5d5f000 rw-p 00003000 08:02 509622     /usr/lib/libgthread-2.0.so.0.1400.1
b5d5f000-b5da8000 r-xp 00000000 08:02 509631     /usr/lib/libORBit-2.so.0.1.0
b5da8000-b5db1000 rw-p 00049000 08:02 509631     /usr/lib/libORBit-2.so.0.1.0
b5db1000-b5db2000 rw-p b5db1000 00:00 0 
b5db2000-b5de1000 r-xp 00000000 08:02 509637     /usr/lib/libgconf-2.so.4.1.2
b5de1000-b5de4000 rw-p 0002e000 08:02 509637     /usr/lib/libgconf-2.so.4.1.2
b5de6000-b5dec000 r-xp 00000000 08:02 555521     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5dec000-b5ded000 rw-p 00005000 08:02 555521     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5ded000-b5df1000 r-xp 00000000 08:02 1176239    /usr/lib/sunbird/components/libcommandlines.so
b5df1000-b5df2000 rw-p 00003000 08:02 1176239    /usr/lib/sunbird/components/libcommandlines.so
b5df2000-b5df7000 r-xp 00000000 08:02 1176282    /usr/lib/sunbird/components/libsystem-pref.so
b5df7000-b5df8000 rw-p 00004000 08:02 1176282    /usr/lib/sunbird/components/libsystem-pref.so
b5df8000-b5e44000 r-xp 00000000 08:02 1176195    /usr/lib/sunbird/components/libdocshell.so
b5e44000-b5e48000 rw-p 0004b000 08:02 1176195    /usr/lib/sunbird/components/libdocshell.so
b5e48000-b5e6f000 r-xp 00000000 08:02 1176151    /usr/lib/sunbird/components/librdf.so
b5e6f000-b5e71000 rw-p 00026000 08:02 1176151    /usr/lib/sunbird/components/librdf.so
b5e71000-b5e72000 ---p b5e71000 00:00 0 
b5e72000-b6672000 rw-p b5e72000 00:00 0 
b6672000-b6685000 r-xp 00000000 08:02 1176149    /usr/lib/sunbird/components/libcaps.so
b6685000-b6686000 rw-p 00013000 08:02 1176149    /usr/lib/sunbird/components/libcaps.so
b6686000-b66b0000 r-xp 00000000 08:02 1176206    /usr/lib/sunbird/components/libembedcomponents.so
b66b0000-b66b2000 rw-p 0002a000 08:02 1176206    /usr/lib/sunbird/components/libembedcomponents.so
b66b2000-b66f2000 r-xp 00000000 08:02 1176242    /usr/lib/sunbird/components/libtoolkitcomps.so
b66f2000-b66f5000 rw-p 00040000 08:02 1176242    /usr/lib/sunbird/components/libtoolkitcomps.so
b66f5000-b670a000 r-xp 00000000 08:02 509521     /usr/lib/libICE.so.6.3.0
b670a000-b670c000 rw-p 00014000 08:02 509521     /usr/lib/libICE.so.6.3.0
b670c000-b670d000 rw-p b670c000 00:00 0 
b670d000-b6714000 r-xp 00000000 08:02 509523     /usr/lib/libSM.so.6.0.0
b6714000-b6715000 rw-p 00006000 08:02 509523     /usr/lib/libSM.so.6.0.0
b6715000-b6762000 r-xp 00000000 08:02 509525     /usr/lib/libXt.so.6.0.0
b6762000-b6766000 rw-p 0004c000 08:02 509525     /usr/lib/libXt.so.6.0.0
b6767000-b6773000 r-xp 00000000 08:02 578288     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6773000-b6774000 rw-p 0000c000 08:02 578288     /usr/lib/gtk-2.0/2.10.0/engines/libcrux-engine.so
b6774000-b6791000 r-xp 00000000 08:02 1176083    /usr/lib/sunbird/libgkgfx.so
b6791000-b6793000 rw-p 0001c000 08:02 1176083    /usr/lib/sunbird/libgkgfx.so
b6793000-b67be000 r-xp 00000000 08:02 1176178    /usr/lib/sunbird/components/libwidget_gtk2.so
b67be000-b67c2000 rw-p 0002b000 08:02 1176178    /usr/lib/sunbird/components/libwidget_gtk2.so
b67c2000-b67d3000 r-xp 00000000 08:02 1176141    /usr/lib/sunbird/components/libjar50.so
b67d3000-b67d4000 rw-p 00011000 08:02 1176141    /usr/lib/sunbird/components/libjar50.so
b67d4000-b681f000 r-xp 00000000 08:02 1176108    /usr/lib/sunbird/components/libxpconnect.so
b681f000-b6823000 rw-p 0004b000 08:02 1176108    /usr/lib/sunbird/components/libxpconnect.so
b6823000-b6824000 ---p b6823000 00:00 0 
b6824000-b7024000 rw-p b6824000 00:00 0 
b7024000-b705a000 r-xp 00000000 08:02 1176118    /usr/lib/sunbird/components/libi18n.so
b705a000-b705d000 rw-p 00035000 08:02 1176118    /usr/lib/sunbird/components/libi18n.so
b705d000-b7064000 r-xp 00000000 08:02 1176281    /usr/lib/sunbird/components/libautoconfig.so
b7064000-b7065000 rw-p 00006000 08:02 1176281    /usr/lib/sunbird/components/libautoconfig.so
b7065000-b7114000 r-xp 00000000 08:02 1176139    /usr/lib/sunbird/components/libnecko.so
b7114000-b711c000 rw-p 000af000 08:02 1176139    /usr/lib/sunbird/components/libnecko.so
b711c000-b712a000 r-xp 00000000 08:02 1176147    /usr/lib/sunbird/components/libpref.so
b712a000-b712b000 rw-p 0000e000 08:02 1176147    /usr/lib/sunbird/components/libpref.so
b712b000-b713a000 r-xp 00000000 08:02 1176221    /usr/lib/sunbird/components/libchrome.so
b713a000-b713b000 rw-p 0000f000 08:02 1176221    /usr/lib/sunbird/components/libchrome.so
b713b000-b7144000 r-xp 00000000 08:02 293214     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7144000-b7146000 rw-p 00008000 08:02 293214     /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7146000-b714e000 r-xp 00000000 08:02 293216     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b714e000-b7150000 rw-p 00007000 08:02 293216     /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b7150000-b7164000 r-xp 00000000 08:02 293211     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7164000-b7166000 rw-p 00013000 08:02 293211     /lib/tls/i686/cmov/libnsl-2.6.1.so
b7166000-b7168000 rw-p b7166000 00:00 0 
b7168000-b716f000 r-xp 00000000 08:02 293212     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b716f000-b7171000 rw-p 00006000 08:02 293212     /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7171000-b7173000 r-xp 00000000 08:02 1176082    /usr/lib/sunbird/libgfxpsshar.so
b7173000-b7174000 rw-p 00001000 08:02 1176082    /usr/lib/sunbird/libgfxpsshar.so
b7174000-b7177000 r-xp 00000000 08:02 1176085    /usr/lib/sunbird/libgtkxtbin.so
b7177000-b7178000 rw-p 00003000 08:02 1176085    /usr/lib/sunbird/libgtkxtbin.so
b7178000-b717a000 r-xp 00000000 08:02 511192     /usr/lib/gconv/UTF-16.so
b717a000-b717c000 rw-p 00001000 08:02 511192     /usr/lib/gconv/UTF-16.so
b717c000-b717d000 r-xp 00000000 08:02 511138     /usr/lib/gconv/ISO8859-1.so
b717d000-b717f000 rw-p 00000000 08:02 511138     /usr/lib/gconv/ISO8859-1.so
b717f000-b71be000 r--p 00000000 08:02 539919     /usr/lib/locale/en_US.utf8/LC_CTYPE
b71be000-b71bf000 r--p 00000000 08:02 539920     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b71bf000-b71c0000 r--p 00000000 08:02 539921     /usr/lib/locale/en_US.utf8/LC_TIME
b71c0000-b72a0000 r--p 00000000 08:02 539922     /usr/lib/locale/en_US.utf8/LC_COLLATE
b72a0000-b72a1000 r--p 00000000 08:02 539923     /usr/lib/locale/en_US.utf8/LC_MONETARY
b72a1000-b72a4000 rw-p b72a1000 00:00 0 
b72a4000-b72a8000 r-xp 00000000 08:02 506614     /usr/lib/libXdmcp.so.6.0.0
b72a8000-b72a9000 rw-p 00003000 08:02 506614     /usr/lib/libXdmcp.so.6.0.0
b72a9000-b72cb000 r-xp 00000000 08:02 509682     /usr/lib/libpng12.so.0.15.0
b72cb000-b72cc000 rw-p 00021000 08:02 509682     /usr/lib/libpng12.so.0.15.0
b72cc000-b72ce000 r-xp 00000000 08:02 506612     /usr/lib/libXau.so.6.0.0
b72ce000-b72cf000 rw-p 00001000 08:02 506612     /usr/lib/libXau.so.6.0.0
b72cf000-b72ed000 r-xp 00000000 08:02 510334     /usr/lib/libexpat.so.1.0.0
b72ed000-b72ef000 rw-p 0001e000 08:02 510334     /usr/lib/libexpat.so.1.0.0
b72ef000-b72f0000 rw-p b72ef000 00:00 0 
b72f0000-b7304000 r-xp 00000000 08:02 507056     /usr/lib/libz.so.1.2.3.3
b7304000-b7305000 rw-p 00013000 08:02 507056     /usr/lib/libz.so.1.2.3.3
b7305000-b7371000 r-xp 00000000 08:02 506624     /usr/lib/libfreetype.so.6.3.16
b7371000-b7375000 rw-p 0006b000 08:02 506624     /usr/lib/libfreetype.so.6.3.16
b7375000-b73a2000 r-xp 00000000 08:02 510403     /usr/lib/libpangoft2-1.0.so.0.1800.3
b73a2000-b73a3000 rw-p 0002c000 08:02 510403     /usr/lib/libpangoft2-1.0.so.0.1800.3
b73a3000-b74e7000 r-xp 00000000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b74e7000-b74e8000 r--p 00143000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b74e8000-b74ea000 rw-p 00144000 08:02 293205     /lib/tls/i686/cmov/libc-2.6.1.so
b74ea000-b74ee000 rw-p b74ea000 00:00 0 
b74ee000-b74f8000 r-xp 00000000 08:02 293198     /lib/libgcc_s.so.1
b74f8000-b74f9000 rw-p 0000a000 08:02 293198     /lib/libgcc_s.so.1
b74f9000-b75e1000 r-xp 00000000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b75e1000-b75e4000 r--p 000e8000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b75e4000-b75e6000 rw-p 000eb000 08:02 508704     /usr/lib/libstdc++.so.6.0.9
b75e6000-b75ec000 rw-p b75e6000 00:00 0 
b75ec000-b760f000 r-xp 00000000 08:02 293209     /lib/tls/i686/cmov/libm-2.6.1.so
b760f000-b7611000 rw-p 00023000 08:02 293209     /lib/tls/i686/cmov/libm-2.6.1.so
b7611000-b76cd000 r-xp 00000000 08:02 509619     /usr/lib/libglib-2.0.so.0.1400.1
b76cd000-b76ce000 rw-p 000bc000 08:02 509619     /usr/lib/libglib-2.0.so.0.1400.1
b76ce000-b76d1000 r-xp 00000000 08:02 509620     /usr/lib/libgmodule-2.0.so.0.1400.1
b76d1000-b76d2000 rw-p 00002000 08:02 509620     /usr/lib/libgmodule-2.0.so.0.1400.1
b76d2000-b770c000 r-xp 00000000 08:02 509621     /usr/lib/libgobject-2.0.so.0.1400.1
b770c000-b770d000 rw-p 0003a000 08:02 509621     /usr/lib/libgobject-2.0.so.0.1400.1
b770d000-b770e000 rw-p b770d000 00:00 0 
b770e000-b7712000 r-xp 00000000 08:02 506622     /usr/lib/libXfixes.so.3.1.0
b7712000-b7713000 rw-p 00003000 08:02 506622     /usr/lib/libXfixes.so.3.1.0
b7713000-b7800000 r-xp 00000000 08:02 506616     /usr/lib/libX11.so.6.2.0
b7800000-b7804000 rw-p 000ed000 08:02 506616     /usr/lib/libX11.so.6.2.0
b7804000-b7879000 r-xp 00000000 08:02 509684     /usr/lib/libcairo.so.2.11.5
b7879000-b787b000 rw-p 00074000 08:02 509684     /usr/lib/libcairo.so.2.11.5
b787b000-b78b6000 r-xp 00000000 08:02 510401     /usr/lib/libpango-1.0.so.0.1800.3
b78b6000-b78b8000 rw-p 0003b000 08:02 510401     /usr/lib/libpango-1.0.so.0.1800.3
b78b8000-b78ba000 r-xp 00000000 08:02 510442     /usr/lib/libXdamage.so.1.1.0
b78ba000-b78bb000 rw-p 00001000 08:02 510442     /usr/lib/libXdamage.so.1.1.0
b78bb000-b78bd000 r-xp 00000000 08:02 510438     /usr/lib/libXcomposite.so.1.0.0
b78bd000-b78be000 rw-p 00001000 08:02 510438     /usr/lib/libXcomposite.so.1.0.0
b78be000-b78bf000 rw-p b78be000 00:00 0 
b78bf000-b78c7000 r-xp 00000000 08:02 510440     /usr/lib/libXcursor.so.1.0.2
b78c7000-b78c8000 rw-p 00007000 08:02 510440     /usr/lib/libXcursor.so.1.0.2
b78c8000-b78cd000 r-xp 00000000 08:02 510813     /usr/lib/libXrandr.so.2.1.0
b78cd000-b78ce000 rw-p 00005000 08:02 510813     /usr/lib/libXrandr.so.2.1.0
b78ce000-b78d5000 r-xp 00000000 08:02 510809     /usr/lib/libXi.so.6.0.0
b78d5000-b78d6000 rw-p 00006000 08:02 510809     /usr/lib/libXi.so.6.0.0
b78d6000-b78d8000 r-xp 00000000 08:02 510811     /usr/lib/libXinerama.so.1.0.0
b78d8000-b78d9000 rw-p 00001000 08:02 510811     /usr/lib/libXinerama.so.1.0.0
b78d9000-b78e0000 r-xp 00000000 08:02 509517     /usr/lib/libXrender.so.1.3.0
b78e0000-b78e1000 rw-p 00006000 08:02 509517     /usr/lib/libXrender.so.1.3.0
b78e1000-b78ee000 r-xp 00000000 08:02 506618     /usr/lib/libXext.so.6.4.0
b78ee000-b78ef000 rw-p 0000d000 08:02 506618     /usr/lib/libXext.so.6.4.0
b78ef000-b78f0000 rw-p b78ef000 00:00 0 
b78f0000-b7913000 r-xp 00000000 08:02 509515     /usr/lib/libfontconfig.so.1.2.0
b7913000-b791b000 rw-p 00023000 08:02 509515     /usr/lib/libfontconfig.so.1.2.0
b791b000-b7923000 r-xp 00000000 08:02 510402     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7923000-b7924000 rw-p 00007000 08:02 510402     /usr/lib/libpangocairo-1.0.so.0.1800.3
b7924000-b793b000 r-xp 00000000 08:02 510816     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b793b000-b793c000 rw-p 00016000 08:02 510816     /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b793c000-b7955000 r-xp 00000000 08:02 509679     /usr/lib/libatk-1.0.so.0.2009.1
b7955000-b7957000 rw-p 00018000 08:02 509679     /usr/lib/libatk-1.0.so.0.2009.1
b7957000-b79db000 r-xp 00000000 08:02 510815     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79db000-b79de000 rw-p 00084000 08:02 510815     /usr/lib/libgdk-x11-2.0.so.0.1200.0
b79de000-b7d5b000 r-xp 00000000 08:02 510818     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d5b000-b7d62000 rw-p 0037c000 08:02 510818     /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7d62000-b7d64000 rw-p b7d62000 00:00 0 
b7d64000-b7d66000 r-xp 00000000 08:02 293208     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d66000-b7d68000 rw-p 00001000 08:02 293208     /lib/tls/i686/cmov/libdl-2.6.1.so
b7d68000-b7d7c000 r-xp 00000000 08:02 293219     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d7c000-b7d7e000 rw-p 00013000 08:02 293219     /lib/tls/i686/cmov/libpthread-2.6.1.so
b7d7e000-b7d80000 rw-p b7d7e000 00:00 0 
b7d80000-b7dae000 r-xp 00000000 08:02 511286     /usr/lib/libnspr4.so.0d
b7dae000-b7daf000 rw-p 0002e000 08:02 511286     /usr/lib/libnspr4.so.0d
b7daf000-b7db1000 rw-p b7daf000 00:00 0 
b7db1000-b7db5000 r-xp 00000000 08:02 511287     /usr/lib/libplc4.so.0d
b7db5000-b7db6000 rw-p 00003000 08:02 511287     /usr/lib/libplc4.so.0d
b7db6000-b7db8000 r-xp 00000000 08:02 511288     /usr/lib/libplds4.so.0d
b7db8000-b7db9000 rw-p 00001000 08:02 511288     /usr/lib/libplds4.so.0d
b7db9000-b7dba000 r--p 00000000 08:02 539925     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7dba000-b7dbb000 r--p 00000000 08:02 539926     /usr/lib/locale/en_US.utf8/LC_PAPER
b7dbb000-b7dbc000 r--p 00000000 08:02 539927     /usr/lib/locale/en_US.utf8/LC_NAME
b7dbc000-b7dbd000 r--p 00000000 08:02 539928     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7dbd000-b7dbe000 r--p 00000000 08:02 539929     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7dbe000-b7dbf000 r--p 00000000 08:02 539930     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7dbf000-b7dc6000 r--s 00000000 08:02 505906     /usr/lib/gconv/gconv-modules.cache
b7dc6000-b7dc7000 r--p 00000000 08:02 539931     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7dc7000-b7e69000 r-xp 00000000 08:02 1176089    /usr/lib/sunbird/libxpcom_core.so
b7e69000-b7e71000 rw-p 000a1000 08:02 1176089    /usr/lib/sunbird/libxpcom_core.so
b7e71000-b7e72000 rw-p b7e71000 00:00 0 
b7e72000-b7e74000 r-xp 00000000 08:02 1176087    /usr/lib/sunbird/libxpcom.so
b7e74000-b7e75000 rw-p 00002000 08:02 1176087    /usr/lib/sunbird/libxpcom.so
b7e75000-b7f1c000 r-xp 00000000 08:02 1176086    /usr/lib/sunbird/libmozjs.so
b7f1c000-b7f21000 rw-p 000a7000 08:02 1176086    /usr/lib/sunbird/libmozjs.so
b7f21000-b7f23000 rw-p b7f21000 00:00 0 
b7f23000-b7f3d000 r-xp 00000000 08:02 296346     /lib/ld-2.6.1.so
b7f3d000-b7f3f000 rw-p 00019000 08:02 296346     /lib/ld-2.6.1.so
bfd90000-bfda6000 rw-p bfd90000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Killed
```

Screenshot of the last is attached.

---

### Post by Arenlor on 2008-03-04
Anyone at least know how I can send the output to a file so I can post the whole thing here?

---

### Post by Arenlor on 2008-03-07
No ideas at all? I tried using older versions from the mozilla site but they didn't work neither.

---

### Post by rev087 on 2008-03-31
I have the exact same issue, and also didnt got a fix yet :(

---

### Post by centyx on 2008-04-01
This issue appears to be resolved in 0.8 ( I tried the the latest nightly snapshot from [http://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/nightly/latest-mozilla1.8/](http://ftp.mozilla.org/pub/mozilla.org/calendar/sunbird/nightly/latest-mozilla1.8/) ).

Until then, switch to a lightweight GTK theme like Clearlooks Compact. Sunbird works with this theme for me. I found this theme at the trusty [http://art.gnome.org](http://art.gnome.org).

Cheers,

Michael

---

### Post by centyx on 2008-04-01
> **Arenlor said:**
> Anyone at least know how I can send the output to a file so I can post the whole thing here?

I opened up a terminal and ran screen ( sudo apt-get install screen if you don't have it ), turned on logging ( ctrl-a-H ), ran sunbird, and then turned logging off ( ctrl-a-H again ).  

Screen will tell you the name of the file it saved the output to, usually something like screenlog.0.

---

### Post by centyx on 2008-04-09
Sunbird 0.8 is out, hurray. 

[http://www.mozilla.org/projects/calendar/](http://www.mozilla.org/projects/calendar/)

---

### Post by monolux on 2008-04-12
May I recommend using Lightning! It helped me out, Sunbird gave me the same problem as you guys, and personally I think Lightning(also from Mozilla) is a lot better.

---

