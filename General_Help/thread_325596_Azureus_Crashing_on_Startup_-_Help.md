---
title: "Azureus Crashing on Startup - Help?"
date: 2006-12-26
forum: General Help
---

### Post by oneiromancer on 2006-12-26
Newish HTPC, presently dual booting XP and Ubuntu, I'm trying/hoping to transition to Ubuntu completely or primarily, but I can't get Azureus to run, and I also can't get Democracy TV to run, and so far they're the only two RSS-BitTorrent clients for Ubuntu I know of...  if someone reading this is more able to help with Democracy (which also crashes on startup) I'll post details on that, but Azureus is what I use on Windows and I know how to set that up for myself for RSS, whereas Democracy just sounded neat to try....  I'm not a *complete* linux noob, but I'm pretty new to Ubuntu, and have no idea why these two programs which say they installed fine won't work...  I've gotten MythTV working with a few headaches and puzzled out the modelines for my living room flat panel, but Azurues is kind of the cornerstone of my HTPC...  it's an Asus M2NPV-VM mobo (in an Antec Fusiion case, as if that mattered, but it does look sweet :-} ), with an Athlong 64 X2, but I'm running standard x86 Ubuntu as I wasn't sure if some problems I had with Myth might not be related...  any other hardware questions I'll address, but here's Azureus's runtime error report, and I'll post the referenced log file I guess:

oneiros@Antec-Fusion-HTPC:/usr/bin$ azureus

An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0x0
Function=[Unknown.]
Library=(N/A)

NOTE: We are unable to locate the function name symbol for the error
      just occurred. Please refer to release documentation for possible
      reason and solutions.


Current Java thread:
        at org.eclipse.swt.internal.gtk.OS._gtk_widget_size_allocate(Native Method)
        at org.eclipse.swt.internal.gtk.OS.gtk_widget_size_allocate(OS.java:8155)
        at org.eclipse.swt.widgets.Shell.forceResize(Shell.java:708)
        at org.eclipse.swt.widgets.Shell.resizeBounds(Shell.java:1103)
        at org.eclipse.swt.widgets.Shell.setBounds(Shell.java:1154)
        at org.eclipse.swt.widgets.Control.setBounds(Control.java:526)
        at org.gudy.azureus2.ui.swt.shells.MessageSlideShell$1.run(MessageSlideShell.java:996)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
        - locked <0xab980060> (a org.eclipse.swt.widgets.RunnableLock)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3143)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2845)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

Dynamic libraries:
08048000-08057000 r-xp 00000000 08:13 1677731    /usr/lib/j2se/1.4/jre/bin/java
08057000-08059000 rwxp 0000e000 08:13 1677731    /usr/lib/j2se/1.4/jre/bin/java
08059000-086a0000 rwxp 08059000 00:00 0          [heap]
a66c2000-a672e000 r-xp 00000000 08:13 1533663    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
a672e000-a678e000 rwxs 00000000 00:08 6881304    /SYSV00000000 (deleted)
a75aa000-a761b000 r-xp 00000000 08:13 1533667    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a78a0000-a7900000 rwxs 00000000 00:08 6815760    /SYSV00000000 (deleted)
a7a2a000-a7a39000 r-xp 00000000 08:13 1254745    /lib/tls/i686/cmov/libresolv-2.4.so
a7a39000-a7a3b000 rwxp 0000f000 08:13 1254745    /lib/tls/i686/cmov/libresolv-2.4.so
a7a96000-a7c4d000 r-xp 00000000 08:13 1617205    /usr/share/icons/hicolor/icon-theme.cache
a7c4d000-a8d35000 r-xp 00000000 08:13 1682672    /usr/share/icons/crystalsvg/icon-theme.cache
a8d35000-a9394000 r-xp 00000000 08:13 1612607    /usr/share/icons/gnome/icon-theme.cache
a9394000-a95ec000 r-xp 00000000 08:13 1617202    /usr/share/icons/Tango/icon-theme.cache
a95ec000-a974d000 r-xp 00000000 08:13 1616115    /usr/share/icons/Human/icon-theme.cache
a974d000-a97fd000 r-xp 00000000 08:13 1677847    /usr/lib/jni/libgtkjni-2.10.so
a97fd000-a9800000 rwxp 000af000 08:13 1677847    /usr/lib/jni/libgtkjni-2.10.so
a9905000-a9908000 rwxs 00000000 00:08 6848535    /SYSV00000000 (deleted)
a9908000-a990c000 r-xp 00000000 08:13 1254732    /lib/tls/i686/cmov/libnss_dns-2.4.so
a990c000-a990e000 rwxp 00003000 08:13 1254732    /lib/tls/i686/cmov/libnss_dns-2.4.so
a990e000-a9910000 r-xp 00000000 08:13 1466432    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
a9910000-a9911000 rwxp 00001000 08:13 1466432    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
a9911000-a9924000 r-xs 00000000 08:13 1547630    /usr/share/azureus/plugins/bdcc/bdcc_2.2.2.jar
a9924000-a9950000 r-xs 00000000 08:13 1547628    /usr/share/azureus/plugins/azplugins/azplugins_2.1.1.jar
a9950000-a99a1000 r-xp 00000000 08:13 1617200    /usr/share/icons/Tangerine/icon-theme.cache
a99a1000-a99ae000 r-xp 00000000 08:13 1677869    /usr/lib/jni/libglibjni-0.4.so
a99ae000-a99af000 rwxp 0000c000 08:13 1677869    /usr/lib/jni/libglibjni-0.4.so
a9a30000-a9a41000 r-xp 00000000 08:13 1384845    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a9a41000-a9a42000 rwxp 00011000 08:13 1384845    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a9a42000-a9a77000 r-xp 00000000 08:13 1677820    /usr/lib/jni/libswt-gtk-3235.so
a9a77000-a9a79000 rwxp 00034000 08:13 1677820    /usr/lib/jni/libswt-gtk-3235.so
a9a7a000-a9b51000 r-xp 00000000 08:13 1386060    /usr/lib/locale/en_US.utf8/LC_COLLATE
a9b51000-a9b6d000 r-xp 00000000 08:13 1337064    /usr/lib/libexpat.so.1.0.0
a9b6d000-a9b6f000 rwxp 0001c000 08:13 1337064    /usr/lib/libexpat.so.1.0.0
a9b6f000-a9b92000 r-xp 00000000 08:13 1336954    /usr/lib/libpng12.so.0.1.2.8
a9b92000-a9b93000 rwxp 00023000 08:13 1336954    /usr/lib/libpng12.so.0.1.2.8
a9b93000-a9b97000 r-xp 00000000 08:13 1336879    /usr/lib/libXdmcp.so.6.0.0
a9b97000-a9b98000 rwxp 00003000 08:13 1336879    /usr/lib/libXdmcp.so.6.0.0
a9b98000-a9b9a000 r-xp 00000000 08:13 1336870    /usr/lib/libXau.so.6.0.0
a9b9a000-a9b9b000 rwxp 00001000 08:13 1336870    /usr/lib/libXau.so.6.0.0
a9b9b000-a9bae000 r-xp 00000000 08:13 1337610    /usr/lib/libz.so.1.2.3
a9bae000-a9baf000 rwxp 00012000 08:13 1337610    /usr/lib/libz.so.1.2.3
a9baf000-a9c16000 r-xp 00000000 08:13 1337080    /usr/lib/libfreetype.so.6.3.10
a9c16000-a9c19000 rwxp 00067000 08:13 1337080    /usr/lib/libfreetype.so.6.3.10
a9c19000-a9c43000 r-xp 00000000 08:13 1337455    /usr/lib/libpangoft2-1.0.so.0.1400.5
a9c43000-a9c44000 rwxp 00029000 08:13 1337455    /usr/lib/libpangoft2-1.0.so.0.1400.5
a9c44000-a9c48000 r-xp 00000000 08:13 1336885    /usr/lib/libXfixes.so.3.1.0
a9c48000-a9c49000 rwxp 00003000 08:13 1336885    /usr/lib/libXfixes.so.3.1.0
a9c49000-a9c51000 r-xp 00000000 08:13 1336875    /usr/lib/libXcursor.so.1.0.2
a9c51000-a9c52000 rwxp 00007000 08:13 1336875    /usr/lib/libXcursor.so.1.0.2
a9c52000-a9c54000 r-xp 00000000 08:13 1336903    /usr/lib/libXrandr.so.2.0.0
a9c54000-a9c55000 rwxp 00002000 08:13 1336903    /usr/lib/libXrandr.so.2.0.0
a9c55000-a9c5c000 r-xp 00000000 08:13 1336891    /usr/lib/libXi.so.6.0.0
a9c5c000-a9c5d000 rwxp 00006000 08:13 1336891    /usr/lib/libXi.so.6.0.0
a9c5d000-a9c64000 r-xp 00000000 08:13 1336905    /usr/lib/libXrender.so.1.3.0
a9c64000-a9c65000 rwxp 00006000 08:13 1336905    /usr/lib/libXrender.so.1.3.0
a9c65000-a9c8e000 r-xp 00000000 08:13 1337070    /usr/lib/libfontconfig.so.1.0.4
a9c8e000-a9c93000 rwxp 00028000 08:13 1337070    /usr/lib/libfontconfig.so.1.0.4
a9c94000-a9ca0000 r-xp 00000000 08:13 1336883    /usr/lib/libXext.so.6.4.0
a9ca0000-a9ca1000 rwxp 0000c000 08:13 1336883    /usr/lib/libXext.so.6.4.0
a9ca1000-a9ca8000 r-xp 00000000 08:13 1254747    /lib/tls/i686/cmov/librt-2.4.so
a9ca8000-a9caa000 rwxp 00006000 08:13 1254747    /lib/tls/i686/cmov/librt-2.4.so
a9caa000-a9d0a000 r-xp 00000000 08:13 1336975    /usr/lib/libcairo.so.2.9.2
a9d0a000-a9d0c000 rwxp 0005f000 08:13 1336975    /usr/lib/libcairo.so.2.9.2
a9d0c000-a9d9d000 r-xp 00000000 08:13 1337171    /usr/lib/libglib-2.0.so.0.1200.4
a9d9d000-a9d9e000 rwxp 00091000 08:13 1337171    /usr/lib/libglib-2.0.so.0.1200.4
a9d9e000-a9da1000 r-xp 00000000 08:13 1337183    /usr/lib/libgmodule-2.0.so.0.1200.4
a9da1000-a9da2000 rwxp 00002000 08:13 1337183    /usr/lib/libgmodule-2.0.so.0.1200.4
a9da2000-a9ddb000 r-xp 00000000 08:13 1337223    /usr/lib/libgobject-2.0.so.0.1200.4
a9ddb000-a9ddc000 rwxp 00038000 08:13 1337223    /usr/lib/libgobject-2.0.so.0.1200.4
a9ddc000-a9df4000 r-xp 00000000 08:13 1336942    /usr/lib/libatk-1.0.so.0.1213.0
a9df4000-a9df6000 rwxp 00017000 08:13 1336942    /usr/lib/libatk-1.0.so.0.1213.0
a9df6000-a9ebc000 r-xp 00000000 08:13 1336864    /usr/lib/libX11.so.6.2.0
a9ebc000-a9ebf000 rwxp 000c5000 08:13 1336864    /usr/lib/libX11.so.6.2.0
a9ebf000-a9ef7000 r-xp 00000000 08:13 1337451    /usr/lib/libpango-1.0.so.0.1400.5
a9ef7000-a9ef9000 rwxp 00037000 08:13 1337451    /usr/lib/libpango-1.0.so.0.1400.5
a9ef9000-a9f00000 r-xp 00000000 08:13 1337453    /usr/lib/libpangocairo-1.0.so.0.1400.5
a9f00000-a9f01000 rwxp 00006000 08:13 1337453    /usr/lib/libpangocairo-1.0.so.0.1400.5
a9f01000-a9f82000 r-xp 00000000 08:13 1336124    /usr/lib/libgdk-x11-2.0.so.0.1000.6
a9f82000-a9f85000 rwxp 00081000 08:13 1336124    /usr/lib/libgdk-x11-2.0.so.0.1000.6
a9f85000-a9f9a000 r-xp 00000000 08:13 1335964    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
a9f9a000-a9f9b000 rwxp 00015000 08:13 1335964    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
a9f9b000-a9f9f000 r-xp 00000000 08:13 1336911    /usr/lib/libXtst.so.6.1.0
a9f9f000-a9fa0000 rwxp 00003000 08:13 1336911    /usr/lib/libXtst.so.6.1.0
a9fa0000-aa2e9000 r-xp 00000000 08:13 1336125    /usr/lib/libgtk-x11-2.0.so.0.1000.6
aa2e9000-aa2ef000 rwxp 00349000 08:13 1336125    /usr/lib/libgtk-x11-2.0.so.0.1000.6
aa2f2000-aa2f3000 r-xp 00000000 08:13 1369244    /usr/lib/gconv/ISO8859-1.so
aa2f3000-aa2f5000 rwxp 00001000 08:13 1369244    /usr/lib/gconv/ISO8859-1.so
aa2f5000-aa2f6000 r-xp 00000000 08:13 1368334    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
aa2f6000-aa2f7000 rwxp 00000000 08:13 1368334    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
aa2f7000-aa2f8000 r-xp 00000000 08:13 1386066    /usr/lib/locale/en_US.utf8/LC_NUMERIC
aa2f8000-aa2f9000 r-xp 00000000 08:13 1386069    /usr/lib/locale/en_US.utf8/LC_TIME
aa2f9000-aa2fa000 r-xp 00000000 08:13 1386064    /usr/lib/locale/en_US.utf8/LC_MONETARY
aa2fa000-aa2fb000 r-xp 00000000 08:13 1400852    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
aa2fb000-aa2fc000 r-xp 00000000 08:13 1386067    /usr/lib/locale/en_US.utf8/LC_PAPER
aa2fc000-aa2fd000 r-xp 00000000 08:13 1386065    /usr/lib/locale/en_US.utf8/LC_NAME
aa2fd000-aa2fe000 r-xp 00000000 08:13 1386059    /usr/lib/locale/en_US.utf8/LC_ADDRESS
aa2fe000-aa2ff000 r-xp 00000000 08:13 1386068    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
aa2ff000-aa355000 r-xp 00000000 08:13 1677821    /usr/lib/jni/libswt-pi-gtk-3235.so
aa355000-aa357000 rwxp 00055000 08:13 1677821    /usr/lib/jni/libswt-pi-gtk-3235.so
aa6de000-aa6e4000 r-xp 00000000 08:13 1402024    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa6e4000-aa6e5000 rwxp 00006000 08:13 1402024    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa7e7000-aa887000 r-xs 00000000 08:13 1488253    /usr/share/java/gtk2.10.jar
aa887000-aa88f000 r-xs 00000000 08:13 1488252    /usr/share/java/cairo1.0.jar
aa88f000-aa895000 r-xs 00000000 08:13 1488251    /usr/share/java/glib0.4.jar
aa895000-aaa42000 r-xs 00000000 08:13 1677831    /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.1.v3235.jar
aaa42000-aaa76000 r-xs 00000000 08:13 1488248    /usr/share/java/log4j-1.2.13.jar
aaa76000-aab6b000 r-xs 00000000 08:13 1488242    /usr/share/java/bcprov.jar
aac6d000-aac7c000 r-xp 00000000 08:13 1402043    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aac7c000-aac7d000 rwxp 0000e000 08:13 1402043    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aaca3000-ab3d0000 r-xs 00000000 08:13 1487937    /usr/share/java/Azureus2.jar
ab3d0000-ab3de000 r-xs 00000000 08:13 1402003    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
ab3de000-ab49a000 r-xs 00000000 08:13 1402004    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
ab49a000-ab4b6000 r-xs 00000000 08:13 1402002    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
ab6ba000-ab6ed000 r-xp 00000000 08:13 1386061    /usr/lib/locale/en_US.utf8/LC_CTYPE
b38f0000-b38f2000 r-xp 00000000 08:13 1336893    /usr/lib/libXinerama.so.1.0.0
b38f2000-b38f3000 rwxp 00001000 08:13 1336893    /usr/lib/libXinerama.so.1.0.0
b38f3000-b38fb000 r-xs 00000000 08:13 1488246    /usr/share/java/commons-cli-1.0.jar
b59a3000-b5f43000 r-xs 00000000 08:13 1402020    /usr/lib/j2se/1.4/jre/lib/charsets.jar
b5f43000-b5f54000 r-xs 00000000 08:13 1401999    /usr/lib/j2se/1.4/jre/lib/jce.jar
b5f54000-b6031000 r-xs 00000000 08:13 1401994    /usr/lib/j2se/1.4/jre/lib/jsse.jar
b6031000-b6047000 r-xs 00000000 08:13 1402022    /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
b6091000-b7a3d000 r-xs 00000000 08:13 1402054    /usr/lib/j2se/1.4/jre/lib/rt.jar
b7a3d000-b7a4e000 r-xp 00000000 08:13 1402040    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a4e000-b7a50000 rwxp 00011000 08:13 1402040    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a50000-b7a6f000 r-xp 00000000 08:13 1402027    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a6f000-b7a70000 rwxp 0001f000 08:13 1402027    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a70000-b7a81000 r-xp 00000000 08:13 1402032    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a81000-b7a82000 rwxp 00011000 08:13 1402032    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a82000-b7a8b000 r-xp 00000000 08:13 1254734    /lib/tls/i686/cmov/libnss_files-2.4.so
b7a8b000-b7a8d000 rwxp 00008000 08:13 1254734    /lib/tls/i686/cmov/libnss_files-2.4.so
b7a8d000-b7a95000 r-xp 00000000 08:13 1254738    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7a95000-b7a97000 rwxp 00007000 08:13 1254738    /lib/tls/i686/cmov/libnss_nis-2.4.so
b7a97000-b7a9e000 r-xp 00000000 08:13 1254730    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7a9e000-b7aa0000 rwxp 00006000 08:13 1254730    /lib/tls/i686/cmov/libnss_compat-2.4.so
b7aa0000-b7aa4000 r-xp 00000000 08:13 1337275    /usr/lib/libgthread-2.0.so.0.1200.4
b7aa4000-b7aa5000 rwxp 00003000 08:13 1337275    /usr/lib/libgthread-2.0.so.0.1200.4
b7aa5000-b7aa8000 r-xs 00000000 08:13 1402001    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
b7aa8000-b7aaf000 r-xs 00000000 08:13 1369296    /usr/lib/gconv/gconv-modules.cache
b7aaf000-b7ad3000 r-xp 00000000 08:13 1254725    /lib/tls/i686/cmov/libm-2.4.so
b7ad3000-b7ad5000 rwxp 00023000 08:13 1254725    /lib/tls/i686/cmov/libm-2.4.so
b7ad5000-b7ae7000 r-xp 00000000 08:13 1254728    /lib/tls/i686/cmov/libnsl-2.4.so
b7ae7000-b7ae9000 rwxp 00011000 08:13 1254728    /lib/tls/i686/cmov/libnsl-2.4.so
b7aeb000-b7dac000 r-xp 00000000 08:13 1666182    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7dac000-b7dc7000 rwxp 002c0000 08:13 1666182    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7ddf000-b7f0c000 r-xp 00000000 08:13 1254717    /lib/tls/i686/cmov/libc-2.4.so
b7f0c000-b7f0e000 r-xp 0012c000 08:13 1254717    /lib/tls/i686/cmov/libc-2.4.so
b7f0e000-b7f10000 rwxp 0012e000 08:13 1254717    /lib/tls/i686/cmov/libc-2.4.so
b7f14000-b7f16000 r-xp 00000000 08:13 1254723    /lib/tls/i686/cmov/libdl-2.4.so
b7f16000-b7f18000 rwxp 00001000 08:13 1254723    /lib/tls/i686/cmov/libdl-2.4.so
b7f18000-b7f27000 r-xp 00000000 08:13 1254743    /lib/tls/i686/cmov/libpthread-2.4.so
b7f27000-b7f29000 rwxp 0000f000 08:13 1254743    /lib/tls/i686/cmov/libpthread-2.4.so
b7f2b000-b7f2c000 r-xp 00000000 08:13 1386063    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f2c000-b7f2d000 r-xp 00000000 08:13 1386062    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f2d000-b7f31000 rwxs 00000000 08:13 667973     /tmp/hsperfdata_oneiros/5897
b7f31000-b7f39000 r-xp 00000000 08:13 1677671    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f39000-b7f3a000 rwxp 00007000 08:13 1677671    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7f3c000-b7f55000 r-xp 00000000 08:13 1221622    /lib/ld-2.4.so
b7f55000-b7f57000 rwxp 00018000 08:13 1221622    /lib/ld-2.4.so
bf8c5000-bf8db000 rwxp bf8c5000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

Heap at VM Abort:
Heap
 def new generation   total 576K, used 468K [0xab8f0000, 0xab990000, 0xabdd0000)
  eden space 512K,  81% used [0xab8f0000, 0xab958180, 0xab970000)
  from space 64K,  82% used [0xab980000, 0xab98d270, 0xab990000)
  to   space 64K,   0% used [0xab970000, 0xab970000, 0xab980000)
 tenured generation   total 3772K, used 2639K [0xabdd0000, 0xac17f000, 0xaf8f0000)
   the space 3772K,  69% used [0xabdd0000, 0xac063ff0, 0xac064000, 0xac17f000)
 compacting perm gen  total 11008K, used 10887K [0xaf8f0000, 0xb03b0000, 0xb38f0000)
   the space 11008K,  98% used [0xaf8f0000, 0xb0391ef8, 0xb0392000, 0xb03b0000)

Local Time = Tue Dec 26 02:04:36 2006
Elapsed Time = 3
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid5897.log.
# Please refer to the file for further information.
#
Aborted (core dumped)
oneiros@Antec-Fusion-HTPC:/usr/bin$

---

### Post by zanglang on 2006-12-26
Not quite sure what's wrong there, but I noticed that you seem to be using Java 1.4.x... I remember Azureus has some problems with that version. Maybe try upgrading to 1.5 or even 1.6 first?

---

### Post by oneiromancer on 2006-12-26
Well, I downlaoded and installed Java 1.5 from Sun's site (didn't see 1.6, and never even heard it was out, is it beta or something?), and then decided to try starting azurues, and it seems not to die now....  HOWEVER, it appears this is because I randomly decided to try starting it as root...  because when I type java -version it still says 1.4.2, so
 a) any idea why azurues would work as root and not as admin user?  and 
b) If installing Sun's 1.5 (5.0) upgrade didnt replace the 1.4.2 version or whatever, how do I upgrade properly?  Never done much with java on linux....  also does anyone know if azurues plugins from windows will work in linux?  I assume so, but not 100% sure, dont recall any different options at download for OS or anything....    thanks all...

---

### Post by Get_Ya_Wicked_On on 2006-12-26
Search, please. Goodness.

---

### Post by zanglang on 2006-12-27
Oops, I meant java 6.0. :P I'm not sure how to cleanly uninstall java, but you'll need to use 'update-alternatives' to properly select your default Java version. Check the FAQ and Howto forums.

Otherwise, you might want to try simply using Automatix to install Java and Azureus from scratch:
[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

---

### Post by gapplewagen on 2007-01-16
I had the same problem and doing a:

```

mv .azureus .oldazureus

```

from your user's home directory, and then re-running it fixed the problem.  Guess I had some bad torrent files stuck in there or something?  It makes you go through the initial setup again but it works at least.

---

### Post by WerX on 2007-02-20
I had this same problem, though for some reason it originally ran fine then decided to crash on start. Either way, just installing automatix, then selecting azureus installed Java and Azureus again and it works a treat now. Thanks for the suggestion.

---

