---
title: "weird p2p client problems"
date: 2007-10-02
forum: General Help
---

### Post by billybag on 2007-10-02
i apologize if this is a touchy subject.

Azureus starts up then just exits. leaves. byes
Deluge claims it is starting up in my bottom panel... but nothing starts up
Frostwire. click on the icon a million times. nothing happens.

???

azureus error log:

```


An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0xA969B172
Function=(null)
Library=/usr/lib/jni/libglibjni-0.4.so

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
	at org.eclipse.swt.internal.gtk.OS._gtk_widget_size_allocate(Native Method)
	at org.eclipse.swt.internal.gtk.OS.gtk_widget_size_allocate(OS.java:8173)
	at org.eclipse.swt.widgets.Shell.forceResize(Shell.java:708)
	at org.eclipse.swt.widgets.Shell.resizeBounds(Shell.java:1103)
	at org.eclipse.swt.widgets.Shell.setBounds(Shell.java:1154)
	at org.eclipse.swt.widgets.Control.setBounds(Control.java:526)
	at org.gudy.azureus2.ui.swt.shells.MessageSlideShell$1.run(MessageSlideShell.java:996)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
	- locked <0xac019de0> (a org.eclipse.swt.widgets.RunnableLock)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3157)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2859)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

Dynamic libraries:
08048000-08057000 r-xp 00000000 03:01 33282      /usr/lib/j2se/1.4/jre/bin/java
08057000-08059000 rwxp 0000e000 03:01 33282      /usr/lib/j2se/1.4/jre/bin/java
08059000-086e8000 rwxp 08059000 00:00 0          [heap]
a7a77000-a7aed000 r-xp 00000000 03:01 1195076    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
a82fd000-a830c000 r-xp 00000000 03:01 704319     /lib/tls/i686/cmov/libresolv-2.5.so
a830c000-a830e000 rwxp 0000f000 03:01 704319     /lib/tls/i686/cmov/libresolv-2.5.so
a8310000-a8314000 r-xp 00000000 03:01 704306     /lib/tls/i686/cmov/libnss_dns-2.5.so
a8314000-a8316000 rwxp 00003000 03:01 704306     /lib/tls/i686/cmov/libnss_dns-2.5.so
a8316000-a8318000 r-xp 00000000 03:01 670521     /lib/libnss_mdns4_minimal.so.2
a8318000-a8319000 rwxp 00001000 03:01 670521     /lib/libnss_mdns4_minimal.so.2
a882f000-a885b000 r-xs 00000000 03:01 51560      /usr/share/azureus/plugins/azplugins/azplugins_2.1.1.jar
a885b000-a885d000 r-xp 00000000 03:01 1047697    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
a885d000-a885e000 rwxp 00001000 03:01 1047697    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
a885e000-a88db000 r-xp 00000000 03:01 1195080    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a88db000-a88e1000 r-xs 00000000 03:01 688444     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
a88e1000-a88e2000 r-xs 00000000 03:01 688745     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
a88e2000-a88e5000 r-xs 00000000 03:01 688744     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
a88e5000-a88e6000 r-xs 00000000 03:01 688743     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
a88e6000-a88e7000 r-xs 00000000 03:01 688742     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
a88e7000-a88eb000 r-xs 00000000 03:01 688441     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
a88eb000-a88ee000 r-xs 00000000 03:01 688853     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
a88ee000-a88ef000 r-xs 00000000 03:01 688740     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
a88ef000-a88f1000 r-xs 00000000 03:01 688739     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
a88f1000-a88f3000 r-xs 00000000 03:01 688738     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
a88f3000-a88f4000 r-xs 00000000 03:01 688737     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
a88f4000-a88f6000 r-xs 00000000 03:01 688736     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
a88f6000-a88fc000 r-xs 00000000 03:01 688735     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
a88fc000-a88fe000 r-xs 00000000 03:01 688734     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
a88fe000-a8900000 r-xs 00000000 03:01 688733     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
a8900000-a8908000 r-xs 00000000 03:01 688732     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
a8908000-a890e000 r-xs 00000000 03:01 688731     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
a890e000-a890f000 r-xs 00000000 03:01 688730     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
a890f000-a8926000 r-xs 00000000 03:01 688927     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
a8926000-a8928000 r-xs 00000000 03:01 688729     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
a8928000-a892e000 r-xs 00000000 03:01 688728     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
a892e000-a8931000 r-xs 00000000 03:01 688727     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
a8931000-a8935000 r-xs 00000000 03:01 688426     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
a8935000-a893c000 r-xs 00000000 03:01 688852     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
a893c000-a893d000 r-xs 00000000 03:01 688771     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
a893d000-a893e000 r-xs 00000000 03:01 688770     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
a893e000-a893f000 r-xs 00000000 03:01 688769     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
a893f000-a8940000 r-xs 00000000 03:01 688768     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
a8940000-a8941000 r-xs 00000000 03:01 688870     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
a8941000-a8944000 r-xs 00000000 03:01 688766     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
a8944000-a8949000 r-xs 00000000 03:01 688869     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
a8949000-a894b000 r-xs 00000000 03:01 688764     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
a894b000-a894c000 r-xs 00000000 03:01 688763     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
a894c000-a894e000 r-xs 00000000 03:01 688762     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
a894e000-a894f000 r-xs 00000000 03:01 688761     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
a894f000-a8954000 r-xs 00000000 03:01 688760     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
a8954000-a8958000 r-xs 00000000 03:01 688759     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
a8958000-a895d000 r-xs 00000000 03:01 688825     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
a895d000-a8960000 r-xs 00000000 03:01 688757     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
a8960000-a8961000 r-xs 00000000 03:01 688756     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
a8961000-a8963000 r-xs 00000000 03:01 688755     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
a8963000-a8967000 r-xs 00000000 03:01 688867     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
a8967000-a896d000 r-xs 00000000 03:01 688753     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
a896d000-a896e000 r-xs 00000000 03:01 688752     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
a896e000-a8976000 r-xs 00000000 03:01 688751     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
a8976000-a8978000 r-xs 00000000 03:01 688866     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
a8978000-a897b000 r-xs 00000000 03:01 688749     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
a897b000-a897d000 r-xs 00000000 03:01 688807     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
a897d000-a8984000 r-xs 00000000 03:01 688851     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
a8984000-a8997000 r-xs 00000000 03:01 51976      /usr/share/azureus/plugins/bdcc/bdcc_2.2.2.jar
a8997000-a8b8d000 r-xp 00000000 03:01 1281039    /usr/share/icons/hicolor/icon-theme.cache
a8b8d000-a9234000 r-xp 00000000 03:01 1280887    /usr/share/icons/gnome/icon-theme.cache
a9234000-a948b000 r-xp 00000000 03:01 1280002    /usr/share/icons/Tango/icon-theme.cache
a948b000-a952c000 r-xp 00000000 03:01 1278805    /usr/share/icons/Tangerine/icon-theme.cache
a952c000-a9692000 r-xp 00000000 03:01 1277259    /usr/share/icons/Human/icon-theme.cache
a9692000-a969f000 r-xp 00000000 03:01 1395555    /usr/lib/jni/libglibjni-0.4.so
a969f000-a96a0000 rwxp 0000c000 03:01 1395555    /usr/lib/jni/libglibjni-0.4.so
a96a0000-a9753000 r-xp 00000000 03:01 1395553    /usr/lib/jni/libgtkjni-2.10.so
a9753000-a9756000 rwxp 000b3000 03:01 1395553    /usr/lib/jni/libgtkjni-2.10.so
a9756000-a97b6000 rwxs 00000000 00:08 1507348    /SYSV00000000 (deleted)
a97b6000-a97b9000 rwxs 00000000 00:08 1474579    /SYSV00000000 (deleted)
a97b9000-a9819000 rwxs 00000000 00:08 1441810    /SYSV00000000 (deleted)
a989a000-a98ac000 r-xp 00000000 03:01 1062965    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a98ac000-a98ad000 rwxp 00011000 03:01 1062965    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a98ad000-a98e5000 r-xp 00000000 03:01 1395548    /usr/lib/jni/libswt-gtk-3236.so
a98e5000-a98e7000 rwxp 00037000 03:01 1395548    /usr/lib/jni/libswt-gtk-3236.so
a98e8000-a99bf000 r-xp 00000000 03:01 1063932    /usr/lib/locale/en_US.utf8/LC_COLLATE
a99bf000-a99dd000 r-xp 00000000 03:01 1015294    /usr/lib/libexpat.so.1.0.0
a99dd000-a99df000 rwxp 0001d000 03:01 1015294    /usr/lib/libexpat.so.1.0.0
a99df000-a9a01000 r-xp 00000000 03:01 1015371    /usr/lib/libpng12.so.0.15.0
a9a01000-a9a02000 rwxp 00021000 03:01 1015371    /usr/lib/libpng12.so.0.15.0
a9a02000-a9a06000 r-xp 00000000 03:01 1015109    /usr/lib/libXdmcp.so.6.0.0
a9a06000-a9a07000 rwxp 00003000 03:01 1015109    /usr/lib/libXdmcp.so.6.0.0
a9a07000-a9a09000 r-xp 00000000 03:01 1015098    /usr/lib/libXau.so.6.0.0
a9a09000-a9a0a000 rwxp 00001000 03:01 1015098    /usr/lib/libXau.so.6.0.0
a9a0a000-a9a1d000 r-xp 00000000 03:01 1015853    /usr/lib/libz.so.1.2.3
a9a1d000-a9a1e000 rwxp 00012000 03:01 1015853    /usr/lib/libz.so.1.2.3
a9a1e000-a9a86000 r-xp 00000000 03:01 1015204    /usr/lib/libfreetype.so.6.3.10
a9a86000-a9a89000 rwxp 00068000 03:01 1015204    /usr/lib/libfreetype.so.6.3.10
a9a89000-a9ab3000 r-xp 00000000 03:01 1015686    /usr/lib/libpangoft2-1.0.so.0.1600.2
a9ab3000-a9ab4000 rwxp 0002a000 03:01 1015686    /usr/lib/libpangoft2-1.0.so.0.1600.2
a9ab4000-a9abc000 r-xp 00000000 03:01 1015105    /usr/lib/libXcursor.so.1.0.2
a9abc000-a9abd000 rwxp 00007000 03:01 1015105    /usr/lib/libXcursor.so.1.0.2
a9abd000-a9ac2000 r-xp 00000000 03:01 1015133    /usr/lib/libXrandr.so.2.1.0
a9ac2000-a9ac3000 rwxp 00005000 03:01 1015133    /usr/lib/libXrandr.so.2.1.0
a9ac3000-a9aca000 r-xp 00000000 03:01 1015121    /usr/lib/libXi.so.6.0.0
a9aca000-a9acb000 rwxp 00006000 03:01 1015121    /usr/lib/libXi.so.6.0.0
a9acb000-a9acd000 r-xp 00000000 03:01 1015123    /usr/lib/libXinerama.so.1.0.0
a9acd000-a9ace000 rwxp 00001000 03:01 1015123    /usr/lib/libXinerama.so.1.0.0
a9ace000-a9ad5000 r-xp 00000000 03:01 1015135    /usr/lib/libXrender.so.1.3.0
a9ad5000-a9ad6000 rwxp 00006000 03:01 1015135    /usr/lib/libXrender.so.1.3.0
a9ad6000-a9af9000 r-xp 00000000 03:01 1015300    /usr/lib/libfontconfig.so.1.2.0
a9af9000-a9b01000 rwxp 00023000 03:01 1015300    /usr/lib/libfontconfig.so.1.2.0
a9b01000-a9b0e000 r-xp 00000000 03:01 1015113    /usr/lib/libXext.so.6.4.0
a9b0e000-a9b0f000 rwxp 0000d000 03:01 1015113    /usr/lib/libXext.so.6.4.0
a9b0f000-a9b16000 r-xp 00000000 03:01 704321     /lib/tls/i686/cmov/librt-2.5.so
a9b16000-a9b18000 rwxp 00006000 03:01 704321     /lib/tls/i686/cmov/librt-2.5.so
a9b18000-a9b86000 r-xp 00000000 03:01 1015202    /usr/lib/libcairo.so.2.11.1
a9b86000-a9b88000 rwxp 0006d000 03:01 1015202    /usr/lib/libcairo.so.2.11.1
a9b88000-a9c1c000 r-xp 00000000 03:01 1015395    /usr/lib/libglib-2.0.so.0.1200.11
a9c1c000-a9c1d000 rwxp 00093000 03:01 1015395    /usr/lib/libglib-2.0.so.0.1200.11
a9c1d000-a9c1f000 r-xp 00000000 03:01 1015405    /usr/lib/libgmodule-2.0.so.0.1200.11
a9c1f000-a9c20000 rwxp 00002000 03:01 1015405    /usr/lib/libgmodule-2.0.so.0.1200.11
a9c20000-a9c59000 r-xp 00000000 03:01 1015449    /usr/lib/libgobject-2.0.so.0.1200.11
a9c59000-a9c5a000 rwxp 00039000 03:01 1015449    /usr/lib/libgobject-2.0.so.0.1200.11
a9c5a000-a9c73000 r-xp 00000000 03:01 1015169    /usr/lib/libatk-1.0.so.0.1809.1
a9c73000-a9c75000 rwxp 00018000 03:01 1015169    /usr/lib/libatk-1.0.so.0.1809.1
a9c75000-a9c79000 r-xp 00000000 03:01 1015115    /usr/lib/libXfixes.so.3.1.0
a9c79000-a9c7a000 rwxp 00003000 03:01 1015115    /usr/lib/libXfixes.so.3.1.0
a9c7a000-a9d67000 r-xp 00000000 03:01 1015092    /usr/lib/libX11.so.6.2.0
a9d67000-a9d6b000 rwxp 000ed000 03:01 1015092    /usr/lib/libX11.so.6.2.0
a9d6b000-a9da7000 r-xp 00000000 03:01 1015682    /usr/lib/libpango-1.0.so.0.1600.2
a9da7000-a9da9000 rwxp 0003b000 03:01 1015682    /usr/lib/libpango-1.0.so.0.1600.2
a9da9000-a9db0000 r-xp 00000000 03:01 1015684    /usr/lib/libpangocairo-1.0.so.0.1600.2
a9db0000-a9db1000 rwxp 00007000 03:01 1015684    /usr/lib/libpangocairo-1.0.so.0.1600.2
a9db1000-a9e34000 r-xp 00000000 03:01 1015357    /usr/lib/libgdk-x11-2.0.so.0.1000.11
a9e34000-a9e37000 rwxp 00083000 03:01 1015357    /usr/lib/libgdk-x11-2.0.so.0.1000.11
a9e37000-a9e4d000 r-xp 00000000 03:01 1015359    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
a9e4d000-a9e4e000 rwxp 00015000 03:01 1015359    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
a9e4e000-aa19f000 r-xp 00000000 03:01 1015506    /usr/lib/libgtk-x11-2.0.so.0.1000.11
aa19f000-aa1a5000 rwxp 00351000 03:01 1015506    /usr/lib/libgtk-x11-2.0.so.0.1000.11
aa1a6000-aa1fe000 r-xp 00000000 03:01 1395549    /usr/lib/jni/libswt-pi-gtk-3236.so
aa1fe000-aa200000 rwxp 00058000 03:01 1395549    /usr/lib/jni/libswt-pi-gtk-3236.so
aa302000-aa306000 r-xp 00000000 03:01 1015141    /usr/lib/libXtst.so.6.1.0
aa306000-aa307000 rwxp 00003000 03:01 1015141    /usr/lib/libXtst.so.6.1.0
aa307000-aa30b000 r-xp 00000000 03:01 1015503    /usr/lib/libgthread-2.0.so.0.1200.11
aa30b000-aa30c000 rwxp 00003000 03:01 1015503    /usr/lib/libgthread-2.0.so.0.1200.11
aa30c000-aa30d000 r-xs 00000000 03:01 1313717    /usr/lib/j2se/1.4/jre/lib/security/local_policy.jar
aa30d000-aa30e000 r-xs 00000000 03:01 1313718    /usr/lib/j2se/1.4/jre/lib/security/US_export_policy.jar
aa30e000-aa30f000 r-xp 00000000 03:01 1031112    /usr/lib/gconv/ISO8859-1.so
aa30f000-aa311000 rwxp 00000000 03:01 1031112    /usr/lib/gconv/ISO8859-1.so
aa311000-aa312000 r-xp 00000000 03:01 1063938    /usr/lib/locale/en_US.utf8/LC_NUMERIC
aa312000-aa313000 r-xp 00000000 03:01 1063941    /usr/lib/locale/en_US.utf8/LC_TIME
aa313000-aa314000 r-xp 00000000 03:01 1063936    /usr/lib/locale/en_US.utf8/LC_MONETARY
aa314000-aa315000 r-xp 00000000 03:01 1079257    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
aa315000-aa316000 r-xp 00000000 03:01 1063939    /usr/lib/locale/en_US.utf8/LC_PAPER
aa316000-aa317000 r-xp 00000000 03:01 1063937    /usr/lib/locale/en_US.utf8/LC_NAME
aa317000-aa318000 r-xp 00000000 03:01 1063931    /usr/lib/locale/en_US.utf8/LC_ADDRESS
aa720000-aa726000 r-xp 00000000 03:01 1346414    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa726000-aa727000 rwxp 00006000 03:01 1346414    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa829000-aa8c9000 r-xs 00000000 03:01 1146217    /usr/share/java/gtk2.10.jar
aa8c9000-aa8d1000 r-xs 00000000 03:01 1146216    /usr/share/java/cairo1.0.jar
aa8d1000-aa8d7000 r-xs 00000000 03:01 1146215    /usr/share/java/glib0.4.jar
aa8d7000-aaa6a000 r-xs 00000000 03:01 51497      /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar
aaa6a000-aaa9e000 r-xs 00000000 03:01 1146212    /usr/share/java/log4j-1.2.13.jar
aaa9e000-aab93000 r-xs 00000000 03:01 1146206    /usr/share/java/bcprov.jar
aac95000-aaca4000 r-xp 00000000 03:01 1346436    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aaca4000-aaca5000 rwxp 0000e000 03:01 1346436    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aaccb000-ab3f8000 r-xs 00000000 03:01 1146218    /usr/share/java/Azureus2.jar
ab3f8000-ab414000 r-xs 00000000 03:01 1313721    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
ab414000-ab422000 r-xs 00000000 03:01 1313722    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
ab422000-ab4de000 r-xs 00000000 03:01 1313723    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
ab6e2000-ab71d000 r-xp 00000000 03:01 1063933    /usr/lib/locale/en_US.utf8/LC_CTYPE
b3920000-b3921000 r-xp 00000000 03:01 1063940    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b3921000-b3922000 r-xp 00000000 03:01 1063935    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b3922000-b392a000 r-xs 00000000 03:01 1146210    /usr/share/java/commons-cli-1.0.jar
b59d2000-b5f72000 r-xs 00000000 03:01 1261921    /usr/lib/j2se/1.4/jre/lib/charsets.jar
b5f72000-b5f83000 r-xs 00000000 03:01 1261919    /usr/lib/j2se/1.4/jre/lib/jce.jar
b5f83000-b6060000 r-xs 00000000 03:01 1261917    /usr/lib/j2se/1.4/jre/lib/jsse.jar
b6060000-b6076000 r-xs 00000000 03:01 1261923    /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
b60c0000-b7a6c000 r-xs 00000000 03:01 1261924    /usr/lib/j2se/1.4/jre/lib/rt.jar
b7a6c000-b7a7d000 r-xp 00000000 03:01 1346433    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a7d000-b7a7f000 rwxp 00011000 03:01 1346433    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a7f000-b7a9e000 r-xp 00000000 03:01 1346417    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a9e000-b7a9f000 rwxp 0001f000 03:01 1346417    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a9f000-b7ab0000 r-xp 00000000 03:01 1346422    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7ab0000-b7ab1000 rwxp 00011000 03:01 1346422    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7ab1000-b7aba000 r-xp 00000000 03:01 704308     /lib/tls/i686/cmov/libnss_files-2.5.so
b7aba000-b7abc000 rwxp 00008000 03:01 704308     /lib/tls/i686/cmov/libnss_files-2.5.so
b7abc000-b7ac4000 r-xp 00000000 03:01 704312     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7ac4000-b7ac6000 rwxp 00007000 03:01 704312     /lib/tls/i686/cmov/libnss_nis-2.5.so
b7ac6000-b7acd000 r-xp 00000000 03:01 704304     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7acd000-b7acf000 rwxp 00006000 03:01 704304     /lib/tls/i686/cmov/libnss_compat-2.5.so
b7acf000-b7ad0000 r-xp 00000000 03:01 1063934    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7ad0000-b7ad7000 r-xs 00000000 03:01 1031165    /usr/lib/gconv/gconv-modules.cache
b7ad7000-b7adb000 rwxs 00000000 03:01 784945     /tmp/hsperfdata_billy/13369
b7adb000-b7b00000 r-xp 00000000 03:01 704299     /lib/tls/i686/cmov/libm-2.5.so
b7b00000-b7b02000 rwxp 00024000 03:01 704299     /lib/tls/i686/cmov/libm-2.5.so
b7b02000-b7b15000 r-xp 00000000 03:01 704302     /lib/tls/i686/cmov/libnsl-2.5.so
b7b15000-b7b17000 rwxp 00012000 03:01 704302     /lib/tls/i686/cmov/libnsl-2.5.so
b7b19000-b7dda000 r-xp 00000000 03:01 1346426    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7dda000-b7df5000 rwxp 002c0000 03:01 1346426    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7e0d000-b7f48000 r-xp 00000000 03:01 704291     /lib/tls/i686/cmov/libc-2.5.so
b7f48000-b7f49000 r-xp 0013b000 03:01 704291     /lib/tls/i686/cmov/libc-2.5.so
b7f49000-b7f4b000 rwxp 0013c000 03:01 704291     /lib/tls/i686/cmov/libc-2.5.so
b7f4e000-b7f50000 r-xp 00000000 03:01 704297     /lib/tls/i686/cmov/libdl-2.5.so
b7f50000-b7f52000 rwxp 00001000 03:01 704297     /lib/tls/i686/cmov/libdl-2.5.so
b7f52000-b7f65000 r-xp 00000000 03:01 704317     /lib/tls/i686/cmov/libpthread-2.5.so
b7f65000-b7f67000 rwxp 00013000 03:01 704317     /lib/tls/i686/cmov/libpthread-2.5.so
b7f6a000-b7f6d000 r-xs 00000000 03:01 1313720    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
b7f6d000-b7f75000 r-xp 00000000 03:01 33231      /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f75000-b7f76000 rwxp 00007000 03:01 33231      /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f77000-b7f90000 r-xp 00000000 03:01 670570     /lib/ld-2.5.so
b7f90000-b7f92000 rwxp 00019000 03:01 670570     /lib/ld-2.5.so
bff52000-bff67000 rwxp bff52000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

Heap at VM Abort:
Heap
 def new generation   total 576K, used 575K [0xab920000, 0xab9c0000, 0xabe00000)
  eden space 512K,  99% used [0xab920000, 0xab99fff8, 0xab9a0000)
  from space 64K, 100% used [0xab9b0000, 0xab9c0000, 0xab9c0000)
  to   space 64K,   0% used [0xab9a0000, 0xab9a0000, 0xab9b0000)
 tenured generation   total 3648K, used 3100K [0xabe00000, 0xac190000, 0xaf920000)
   the space 3648K,  84% used [0xabe00000, 0xac107080, 0xac107200, 0xac190000)
 compacting perm gen  total 13056K, used 13025K [0xaf920000, 0xb05e0000, 0xb3920000)
   the space 13056K,  99% used [0xaf920000, 0xb05d8528, 0xb05d8600, 0xb05e0000)

Local Time = Mon Oct  1 23:42:54 2007
Elapsed Time = 86
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#

```


i want to assume it is a java problem but deluge is written in python i believe... i may be wrong.

---

### Post by peabody on 2007-10-02
What java are you using?  GNU classpath or Sun Java?  Ubuntu comes with GNU classpath by default I believe and while the developers of that software have made an incredibly noble effort at getting decent compatibility, it still has rough edges.  You might want to look into getting Sun Java.

---

### Post by billybag on 2007-10-02
i have sun java installed but i am going to see if reinstalling it will help

---

### Post by billybag on 2007-10-02
okay i have sun java 6 but java 1.4 and i cannot seem to figure out how to update to java 1.5

---

### Post by billybag on 2007-10-02
does anyone know how to update from 1.4 to 1.5?  i cannot seem to get it

---

### Post by peabody on 2007-10-02
Are you running feisty?  Installed the sun java packages for feisty and my java is 1.6.

---

