---
title: "Programs open then close immediately"
date: 2007-01-14
forum: General Help
---

### Post by strumluff on 2007-01-14
Hi there,

I am fairly new to linux but not computer illiterate, searched and tried what I can to find a solution but to no avail. Here's the problem:

I installed a few new packages recently, XMMS and Azureus among others. The programs were working fine and they were all set up properly. Now for some reason I tried to start Azureus and it would open and then close immediately. Strange as it was I thought I could resolve the problem by reinstalling the package, however even after reinstalling it would still close after opening (I can see the main window for a split second). I'm not sure if the program had re-installed properly as I could still see an open torrent in the program during that second I had to see the window.

Anyway, XMMS was working fine, until it crashed, after being forced to reboot I tried to open the program and the same thing happened, the program loaded, I could see it was open for a split second and it closed again.

Any help on how to get these programs working again will be great, 

Thanks.

Edit: I'm running Ubuntu Edgy 6.10

---

### Post by taurus on 2007-01-14
Try to run them from a terminal so you can see what the error messages are!

Applications -> Accessories -> Terminal
```
azureus
xmms
```

---

### Post by strumluff on 2007-01-14
Oh thanks Taurus, well I the error messages haven't helped me, maybe someone can understand better than me.

For XMMS the error message is:

Message: device: default
Gdk-ERROR **: BadAccess (attempt to access private resource denied)
  serial 9 error_code 10 request_code 33 minor_code 0

For Azureus the error message is (rather long):

DEBUG::Sun Jan 14 21:53:14 GMT 2007::com.aelitis.azureus.plugins.upnp.UPnPPlugin$9::log::504:
  org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://192.168.0.1:49152/ipcfg.xml':java.net.ConnectException: Connection refused
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(Unknown Source)
        at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
        at java.net.PlainSocketImpl.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at sun.net.NetworkClient.doConnect(Unknown Source)
        at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
        at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
        at sun.net.www.http.HttpClient.<init>(Unknown Source)
        at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
        at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown](www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(Unknown](www.protocol.http.HttpURLConnection.plainConnect(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.connect(Unknown](www.protocol.http.HttpURLConnection.connect(Unknown) Source)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:447)
        ... 2 more

DEBUG::Sun Jan 14 21:53:14 GMT 2007::com.aelitis.azureus.plugins.upnp.UPnPPlugin::rootDeviceFound::728:
  com.aelitis.net.upnp.UPnPException: Root device location 'http://192.168.0.1:49152/ipcfg.xml' - data read failed
        at com.aelitis.net.upnp.impl.UPnPImpl.downloadXML(UPnPImpl.java:481)
        at com.aelitis.net.upnp.impl.services.UPnPServiceImpl.loadDescription(UPnPServiceImpl.java:213)
        at com.aelitis.net.upnp.impl.services.UPnPServiceImpl.getActions(UPnPServiceImpl.java:91)
        at com.aelitis.net.upnp.impl.services.UPnPServiceImpl.getAction(UPnPServiceImpl.java:107)
        at com.aelitis.net.upnp.impl.services.UPnPSSWANConnectionImpl.getPortMappings(UPnPSSWANConnectionImpl.java:483)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.addService(UPnPPlugin.java:993)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processServices(UPnPPlugin.java:939)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:899)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.processDevice(UPnPPlugin.java:905)
        at com.aelitis.azureus.plugins.upnp.UPnPPlugin.rootDeviceFound(UPnPPlugin.java:691)
        at com.aelitis.net.upnp.impl.UPnPImpl$1.runSupport(UPnPImpl.java:237)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.gudy.azureus2.core3.util.ThreadPool$3.runSupport(ThreadPool.java:523)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:69)
Caused by: org.gudy.azureus2.plugins.utils.resourcedownloader.ResourceDownloaderException: I/O Exception while downloading 'http://192.168.0.1:49152/ipcfg.xml':java.net.ConnectException: Connection refused
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:572)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl$2.runSupport(ResourceDownloaderURLImpl.java:319)
        ... 1 more
Caused by: java.net.ConnectException: Connection refused
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(Unknown Source)
        at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
        at java.net.PlainSocketImpl.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at sun.net.NetworkClient.doConnect(Unknown Source)
        at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
        at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
        at sun.net.www.http.HttpClient.<init>(Unknown Source)
        at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
        at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown](www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(Unknown](www.protocol.http.HttpURLConnection.plainConnect(Unknown) Source)
        at sun.net.[www.protocol.http.HttpURLConnection.connect(Unknown](www.protocol.http.HttpURLConnection.connect(Unknown) Source)
        at org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl.download(ResourceDownloaderURLImpl.java:447)
        ... 2 more

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=6591, tid=3085039280
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_10-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid6591.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by danbh on 2007-01-28
I also have this error on my machine.  Here is how I created the error on Ubuntu Edgy:

Install azureus via apt-get
Attempt to add a torrent by double clicking a torrent.  
The program will open and then immediately close.
From now on, all other methods of opening azureus will just open, and then immediately close.

I deleted the azureus user folder of ~/.azzureus , and then I would be able to open azureus again.  I could drag-and-drop torrents, and azureus would work fine.  But, if I tried to click a torrent, azureus would return to its nonfunctional behavior.

```
An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0xA9784D02
Function=(null)
Library=/usr/lib/jni/libglibjni-0.4.so

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
        - locked <0xab911ee8> (a org.eclipse.swt.widgets.RunnableLock)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3143)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2845)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

Dynamic libraries:
08048000-08057000 r-xp 00000000 03:04 951209     /usr/lib/j2se/1.4/jre/bin/java
08057000-08059000 rwxp 0000e000 03:04 951209     /usr/lib/j2se/1.4/jre/bin/java
08059000-0866b000 rwxp 08059000 00:00 0          [heap]
a6f73000-a6fdf000 r-xp 00000000 03:04 1082456    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
a6fdf000-a6fe6000 r-xp 00000000 03:04 902441     /usr/lib/libfam.so.0.0.0
a6fe6000-a6fe7000 rwxp 00006000 03:04 902441     /usr/lib/libfam.so.0.0.0
a6fe7000-a6fec000 r-xp 00000000 03:04 426017     /lib/libacl.so.1.1.0
a6fec000-a6fed000 rwxp 00005000 03:04 426017     /lib/libacl.so.1.1.0
a6fed000-a6ff0000 r-xp 00000000 03:04 426062     /lib/libattr.so.1.1.0
a6ff0000-a6ff1000 rwxp 00002000 03:04 426062     /lib/libattr.so.1.1.0
a6fff000-a70b2000 r-xp 00000000 03:04 901471     /usr/lib/libasound.so.2.0.0
a70b2000-a70b7000 rwxp 000b2000 03:04 901471     /usr/lib/libasound.so.2.0.0
a70b7000-a70ba000 r-xp 00000000 03:04 902108     /usr/lib/libORBitCosNaming-2.so.0.1.0
a70ba000-a70bb000 rwxp 00003000 03:04 902108     /usr/lib/libORBitCosNaming-2.so.0.1.0
a70bb000-a70ed000 r-xp 00000000 03:04 426005     /lib/libsepol.so.1
a70ed000-a70ee000 rwxp 00031000 03:04 426005     /lib/libsepol.so.1
a70f8000-a7144000 r-xp 00000000 03:04 902570     /usr/lib/libgcrypt.so.11.2.1
a7144000-a7146000 rwxp 0004b000 03:04 902570     /usr/lib/libgcrypt.so.11.2.1
a7146000-a7158000 r-xp 00000000 03:04 902074     /usr/lib/libtasn1.so.3.0.5
a7158000-a7159000 rwxp 00011000 03:04 902074     /usr/lib/libtasn1.so.3.0.5
a7159000-a7177000 r-xp 00000000 03:04 901517     /usr/lib/libjpeg.so.62.0.0
a7177000-a7178000 rwxp 0001d000 03:04 901517     /usr/lib/libjpeg.so.62.0.0
a7178000-a7183000 r-xp 00000000 03:04 819272     /usr/lib/libgnome-keyring.so.0.0.1
a7183000-a7184000 rwxp 0000a000 03:04 819272     /usr/lib/libgnome-keyring.so.0.0.1
a7184000-a7198000 r-xp 00000000 03:04 902421     /usr/lib/libart_lgpl_2.so.2.3.17
a7198000-a7199000 rwxp 00013000 03:04 902421     /usr/lib/libart_lgpl_2.so.2.3.17
a7199000-a71c1000 r-xp 00000000 03:04 902644     /usr/lib/libgnomecanvas-2.so.0.1400.0
a71c1000-a71c2000 rwxp 00027000 03:04 902644     /usr/lib/libgnomecanvas-2.so.0.1400.0
a71c2000-a721c000 r-xp 00000000 03:04 819270     /usr/lib/libbonoboui-2.so.0.0.0
a721c000-a721f000 rwxp 0005a000 03:04 819270     /usr/lib/libbonoboui-2.so.0.0.0
a721f000-a7225000 r-xp 00000000 03:04 426045     /lib/libpopt.so.0.0.0
a7225000-a7226000 rwxp 00006000 03:04 426045     /lib/libpopt.so.0.0.0
a7226000-a7244000 r-xp 00000000 03:04 902438     /usr/lib/libaudiofile.so.0.0.2
a7244000-a7246000 rwxp 0001e000 03:04 902438     /usr/lib/libaudiofile.so.0.0.2
a7246000-a724f000 r-xp 00000000 03:04 902531     /usr/lib/libesd.so.0.2.36
a724f000-a7250000 rwxp 00008000 03:04 902531     /usr/lib/libesd.so.0.2.36
a7250000-a7262000 r-xp 00000000 03:04 901194     /usr/lib/libbonobo-activation.so.4.0.0
a7262000-a7264000 rwxp 00012000 03:04 901194     /usr/lib/libbonobo-activation.so.4.0.0
a7264000-a72b4000 r-xp 00000000 03:04 901147     /usr/lib/libbonobo-2.so.0.0.0
a72b4000-a72be000 rwxp 0004f000 03:04 901147     /usr/lib/libbonobo-2.so.0.0.0
a72be000-a72d0000 r-xp 00000000 03:04 426008     /lib/libselinux.so.1
a72d0000-a72d2000 rwxp 00011000 03:04 426008     /lib/libselinux.so.1
a72d2000-a72e0000 r-xp 00000000 03:04 902098     /usr/lib/libavahi-client.so.3.2.0
a72e0000-a72e1000 rwxp 0000e000 03:04 902098     /usr/lib/libavahi-client.so.3.2.0
a72e1000-a72eb000 r-xp 00000000 03:04 901292     /usr/lib/libavahi-common.so.3.4.2
a72eb000-a72ec000 rwxp 00009000 03:04 901292     /usr/lib/libavahi-common.so.3.4.2
a72ec000-a7355000 r-xp 00000000 03:04 902083     /usr/lib/libgnutls.so.13.0.5
a7355000-a735b000 rwxp 00068000 03:04 902083     /usr/lib/libgnutls.so.13.0.5
a735b000-a738a000 r-xp 00000000 03:04 902288     /usr/lib/libdbus-1.so.3.0.0
a738a000-a738b000 rwxp 0002f000 03:04 902288     /usr/lib/libdbus-1.so.3.0.0
a738b000-a73a5000 r-xp 00000000 03:04 902321     /usr/lib/libdbus-glib-1.so.2.0.0
a73a5000-a73a6000 rwxp 00019000 03:04 902321     /usr/lib/libdbus-glib-1.so.2.0.0
a73a6000-a74b9000 r-xp 00000000 03:04 902110     /usr/lib/libxml2.so.2.6.26
a74b9000-a74be000 rwxp 00113000 03:04 902110     /usr/lib/libxml2.so.2.6.26
a74bf000-a7506000 r-xp 00000000 03:04 902101     /usr/lib/libORBit-2.so.0.1.0
a7506000-a7510000 rwxp 00046000 03:04 902101     /usr/lib/libORBit-2.so.0.1.0
a7510000-a753e000 r-xp 00000000 03:04 901705     /usr/lib/libgconf-2.so.4.1.0
a753e000-a7541000 rwxp 0002e000 03:04 901705     /usr/lib/libgconf-2.so.4.1.0
a7541000-a75c6000 r-xp 00000000 03:04 819274     /usr/lib/libgnomeui-2.so.0.1600.1
a75c6000-a75ca000 rwxp 00084000 03:04 819274     /usr/lib/libgnomeui-2.so.0.1600.1
a75ca000-a75de000 r-xp 00000000 03:04 901892     /usr/lib/libgnome-2.so.0.1600.0
a75de000-a75df000 rwxp 00013000 03:04 901892     /usr/lib/libgnome-2.so.0.1600.0
a75df000-a7634000 r-xp 00000000 03:04 902693     /usr/lib/libgnomevfs-2.so.0.1600.1
a7634000-a7637000 rwxp 00054000 03:04 902693     /usr/lib/libgnomevfs-2.so.0.1600.1
a7638000-a7644000 r-xp 00000000 03:04 934473     /usr/lib/gnome-vfs-2.0/modules/libfile.so
a7644000-a7645000 rwxp 0000b000 03:04 934473     /usr/lib/gnome-vfs-2.0/modules/libfile.so
a76c6000-a76e2000 r-xp 00000000 03:04 1230279    /usr/lib/X11/locale/common/ximcp.so.2.0.0
a76e2000-a76e4000 rwxp 0001b000 03:04 1230279    /usr/lib/X11/locale/common/ximcp.so.2.0.0
a76e4000-a7781000 r-xp 00000000 03:04 1002873    /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
a7781000-a7793000 rwxp 0009d000 03:04 1002873    /usr/lib/j2se/1.4/jre/lib/i386/libfontmanager.so
a7797000-a77e1000 r-xp 00000000 03:04 902349     /usr/lib/libXt.so.6.0.0
a77e1000-a77e5000 rwxp 00049000 03:04 902349     /usr/lib/libXt.so.6.0.0
a77e5000-a79d7000 r-xp 00000000 03:04 1002857    /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
a79d7000-a79f1000 rwxp 001f1000 03:04 1002857    /usr/lib/j2se/1.4/jre/lib/i386/libXm.so.3
a79f2000-a7ad3000 r-xp 00000000 03:04 1002865    /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
a7ad3000-a7adc000 rwxp 000e0000 03:04 1002865    /usr/lib/j2se/1.4/jre/lib/i386/libawt.so
a7c00000-a7c15000 r-xp 00000000 03:04 902378     /usr/lib/libICE.so.6.3.0
a7c15000-a7c16000 rwxp 00014000 03:04 902378     /usr/lib/libICE.so.6.3.0
a7c18000-a7c7e000 r-xp 00000000 03:04 1002851    /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
a7c7e000-a7c7f000 rwxp 00066000 03:04 1002851    /usr/lib/j2se/1.4/jre/lib/i386/libmlib_image.so
a7e00000-a7e03000 r-xp 00000000 03:04 901451     /usr/lib/libgpg-error.so.0.2.0
a7e03000-a7e04000 rwxp 00002000 03:04 901451     /usr/lib/libgpg-error.so.0.2.0
a7e04000-a7e0c000 r-xp 00000000 03:04 902333     /usr/lib/libSM.so.6.0.0
a7e0c000-a7e0d000 rwxp 00007000 03:04 902333     /usr/lib/libSM.so.6.0.0
a7e0d000-a7e6d000 rwxs 00000000 00:08 4259856    /SYSV00000000 (deleted)
a8900000-a8907000 r-xp 00000000 03:04 901578     /usr/lib/libXp.so.6.2.0
a8907000-a8908000 rwxp 00006000 03:04 901578     /usr/lib/libXp.so.6.2.0
a890b000-a890d000 r-xp 00000000 03:04 458872     /lib/tls/i686/cmov/libutil-2.4.so
a890d000-a890f000 rwxp 00001000 03:04 458872     /lib/tls/i686/cmov/libutil-2.4.so
a890f000-a8911000 r-xp 00000000 03:04 903166     /usr/lib/libavahi-glib.so.1.0.1
a8911000-a8912000 rwxp 00002000 03:04 903166     /usr/lib/libavahi-glib.so.1.0.1
a8912000-a8915000 r-xp 00000000 03:04 65556      /usr/lib/jni/libswt-gnome-gtk-3235.so
a8915000-a8916000 rwxp 00002000 03:04 65556      /usr/lib/jni/libswt-gnome-gtk-3235.so
a8916000-a8919000 rwxs 00000000 00:08 4227087    /SYSV00000000 (deleted)
a8ca0000-a8cb3000 r-xs 00000000 03:04 101302     /usr/share/azureus/plugins/bdcc/bdcc_2.2.2.jar
a8cb3000-a8cdf000 r-xs 00000000 03:04 101299     /usr/share/azureus/plugins/azplugins/azplugins_2.1.1.jar
a8cdf000-a8e6d000 r-xp 00000000 03:04 1147308    /usr/share/icons/hicolor/icon-theme.cache
a8e6d000-a94cc000 r-xp 00000000 03:04 1146939    /usr/share/icons/gnome/icon-theme.cache
a94cc000-a9724000 r-xp 00000000 03:04 1069381    /usr/share/icons/Tango/icon-theme.cache
a9724000-a9775000 r-xp 00000000 03:04 950401     /usr/share/icons/Tangerine/icon-theme.cache
a9775000-a977c000 r-xp 00000000 03:04 71641      /usr/share/icons/Human/icon-theme.cache
a977c000-a9789000 r-xp 00000000 03:04 65543      /usr/lib/jni/libglibjni-0.4.so
a9789000-a978a000 rwxp 0000c000 03:04 65543      /usr/lib/jni/libglibjni-0.4.so
a978a000-a983a000 r-xp 00000000 03:04 68857      /usr/lib/jni/libgtkjni-2.10.so
a983a000-a983d000 rwxp 000af000 03:04 68857      /usr/lib/jni/libgtkjni-2.10.so
a983d000-a983f000 r-xp 00000000 03:04 934056     /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
a983f000-a9840000 rwxp 00001000 03:04 934056     /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
a9840000-a98b1000 r-xp 00000000 03:04 1082461    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
a98b1000-a9911000 rwxs 00000000 00:08 4194316    /SYSV00000000 (deleted)
a99dc000-a99ed000 r-xp 00000000 03:04 1234702    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a99ed000-a99ee000 rwxp 00011000 03:04 1234702    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
a99ee000-a9a23000 r-xp 00000000 03:04 71662      /usr/lib/jni/libswt-gtk-3235.so
a9a23000-a9a25000 rwxp 00034000 03:04 71662      /usr/lib/jni/libswt-gtk-3235.so
a9a26000-a9afd000 r-xp 00000000 03:04 16862      /usr/lib/locale/en_US.utf8/LC_COLLATE
a9afd000-a9b19000 r-xp 00000000 03:04 902336     /usr/lib/libexpat.so.1.0.0
a9b19000-a9b1b000 rwxp 0001c000 03:04 902336     /usr/lib/libexpat.so.1.0.0
a9b1b000-a9b3e000 r-xp 00000000 03:04 904212     /usr/lib/libpng12.so.0.1.2.8
a9b3e000-a9b3f000 rwxp 00023000 03:04 904212     /usr/lib/libpng12.so.0.1.2.8
a9b3f000-a9b43000 r-xp 00000000 03:04 901679     /usr/lib/libXdmcp.so.6.0.0
a9b43000-a9b44000 rwxp 00003000 03:04 901679     /usr/lib/libXdmcp.so.6.0.0
a9b44000-a9b46000 r-xp 00000000 03:04 901483     /usr/lib/libXau.so.6.0.0
a9b46000-a9b47000 rwxp 00001000 03:04 901483     /usr/lib/libXau.so.6.0.0
a9b47000-a9b5a000 r-xp 00000000 03:04 901757     /usr/lib/libz.so.1.2.3
a9b5a000-a9b5b000 rwxp 00012000 03:04 901757     /usr/lib/libz.so.1.2.3
a9b5b000-a9bc2000 r-xp 00000000 03:04 901770     /usr/lib/libfreetype.so.6.3.10
a9bc2000-a9bc5000 rwxp 00067000 03:04 901770     /usr/lib/libfreetype.so.6.3.10
a9bc5000-a9bef000 r-xp 00000000 03:04 901918     /usr/lib/libpangoft2-1.0.so.0.1400.5
a9bef000-a9bf0000 rwxp 00029000 03:04 901918     /usr/lib/libpangoft2-1.0.so.0.1400.5
a9bf0000-a9bf4000 r-xp 00000000 03:04 901198     /usr/lib/libXfixes.so.3.1.0
a9bf4000-a9bf5000 rwxp 00003000 03:04 901198     /usr/lib/libXfixes.so.3.1.0
a9bf5000-a9bfd000 r-xp 00000000 03:04 902372     /usr/lib/libXcursor.so.1.0.2
a9bfd000-a9bfe000 rwxp 00007000 03:04 902372     /usr/lib/libXcursor.so.1.0.2
a9bfe000-a9c00000 r-xp 00000000 03:04 902364     /usr/lib/libXrandr.so.2.0.0
a9c00000-a9c01000 rwxp 00002000 03:04 902364     /usr/lib/libXrandr.so.2.0.0
a9c01000-a9c08000 r-xp 00000000 03:04 901379     /usr/lib/libXi.so.6.0.0
a9c08000-a9c09000 rwxp 00006000 03:04 901379     /usr/lib/libXi.so.6.0.0
a9c09000-a9c0b000 r-xp 00000000 03:04 902376     /usr/lib/libXinerama.so.1.0.0
a9c0b000-a9c0c000 rwxp 00001000 03:04 902376     /usr/lib/libXinerama.so.1.0.0
a9c0c000-a9c13000 r-xp 00000000 03:04 901309     /usr/lib/libXrender.so.1.3.0
a9c13000-a9c14000 rwxp 00006000 03:04 901309     /usr/lib/libXrender.so.1.3.0
a9c14000-a9c3d000 r-xp 00000000 03:04 901771     /usr/lib/libfontconfig.so.1.0.4
a9c3d000-a9c42000 rwxp 00028000 03:04 901771     /usr/lib/libfontconfig.so.1.0.4
a9c43000-a9c4f000 r-xp 00000000 03:04 901135     /usr/lib/libXext.so.6.4.0
a9c4f000-a9c50000 rwxp 0000c000 03:04 901135     /usr/lib/libXext.so.6.4.0
a9c50000-a9c57000 r-xp 00000000 03:04 458869     /lib/tls/i686/cmov/librt-2.4.so
a9c57000-a9c59000 rwxp 00006000 03:04 458869     /lib/tls/i686/cmov/librt-2.4.so
a9c59000-a9cb9000 r-xp 00000000 03:04 901813     /usr/lib/libcairo.so.2.9.2
a9cb9000-a9cbb000 rwxp 0005f000 03:04 901813     /usr/lib/libcairo.so.2.9.2
a9cbb000-a9d4c000 r-xp 00000000 03:04 901682     /usr/lib/libglib-2.0.so.0.1200.4
a9d4c000-a9d4d000 rwxp 00091000 03:04 901682     /usr/lib/libglib-2.0.so.0.1200.4
a9d4d000-a9d86000 r-xp 00000000 03:04 901695     /usr/lib/libgobject-2.0.so.0.1200.4
a9d86000-a9d87000 rwxp 00038000 03:04 901695     /usr/lib/libgobject-2.0.so.0.1200.4
a9d87000-a9d9f000 r-xp 00000000 03:04 901726     /usr/lib/libatk-1.0.so.0.1213.0
a9d9f000-a9da1000 rwxp 00017000 03:04 901726     /usr/lib/libatk-1.0.so.0.1213.0
a9da1000-a9e67000 r-xp 00000000 03:04 902338     /usr/lib/libX11.so.6.2.0
a9e67000-a9e6a000 rwxp 000c5000 03:04 902338     /usr/lib/libX11.so.6.2.0
a9e6a000-a9ea2000 r-xp 00000000 03:04 901846     /usr/lib/libpango-1.0.so.0.1400.5
a9ea2000-a9ea4000 rwxp 00037000 03:04 901846     /usr/lib/libpango-1.0.so.0.1400.5
a9ea4000-a9eab000 r-xp 00000000 03:04 901936     /usr/lib/libpangocairo-1.0.so.0.1400.5
a9eab000-a9eac000 rwxp 00006000 03:04 901936     /usr/lib/libpangocairo-1.0.so.0.1400.5
a9eac000-a9f2d000 r-xp 00000000 03:04 901455     /usr/lib/libgdk-x11-2.0.so.0.1000.6
a9f2d000-a9f30000 rwxp 00081000 03:04 901455     /usr/lib/libgdk-x11-2.0.so.0.1000.6
a9f30000-a9f45000 r-xp 00000000 03:04 901454     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
a9f45000-a9f46000 rwxp 00015000 03:04 901454     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
a9f46000-a9f4a000 r-xp 00000000 03:04 902396     /usr/lib/libXtst.so.6.1.0
a9f4a000-a9f4b000 rwxp 00003000 03:04 902396     /usr/lib/libXtst.so.6.1.0
a9f4b000-a9f4f000 r-xp 00000000 03:04 901721     /usr/lib/libgthread-2.0.so.0.1200.4
a9f4f000-a9f50000 rwxp 00003000 03:04 901721     /usr/lib/libgthread-2.0.so.0.1200.4
a9f50000-aa299000 r-xp 00000000 03:04 901458     /usr/lib/libgtk-x11-2.0.so.0.1000.6
aa299000-aa29f000 rwxp 00349000 03:04 901458     /usr/lib/libgtk-x11-2.0.so.0.1000.6
aa2a0000-aa2f6000 r-xp 00000000 03:04 71663      /usr/lib/jni/libswt-pi-gtk-3235.so
aa2f6000-aa2f8000 rwxp 00055000 03:04 71663      /usr/lib/jni/libswt-pi-gtk-3235.so
aa47b000-aa48a000 r-xp 00000000 03:04 458868     /lib/tls/i686/cmov/libresolv-2.4.so
aa48a000-aa48c000 rwxp 0000f000 03:04 458868     /lib/tls/i686/cmov/libresolv-2.4.so
aa48e000-aa492000 r-xp 00000000 03:04 458861     /lib/tls/i686/cmov/libnss_dns-2.4.so
aa492000-aa494000 rwxp 00003000 03:04 458861     /lib/tls/i686/cmov/libnss_dns-2.4.so
aa494000-aa495000 r-xp 00000000 03:04 919178     /usr/lib/gconv/ISO8859-1.so
aa495000-aa497000 rwxp 00001000 03:04 919178     /usr/lib/gconv/ISO8859-1.so
aa497000-aa498000 r-xp 00000000 03:04 1230281    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
aa498000-aa499000 rwxp 00000000 03:04 1230281    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
aa499000-aa49a000 r-xp 00000000 03:04 16860      /usr/lib/locale/en_US.utf8/LC_NUMERIC
aa49a000-aa49b000 r-xp 00000000 03:04 18240      /usr/lib/locale/en_US.utf8/LC_TIME
aa49b000-aa49c000 r-xp 00000000 03:04 18241      /usr/lib/locale/en_US.utf8/LC_MONETARY
aa49c000-aa49d000 r-xp 00000000 03:04 16912      /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
aa49d000-aa49e000 r-xp 00000000 03:04 16933      /usr/lib/locale/en_US.utf8/LC_PAPER
aa49e000-aa49f000 r-xp 00000000 03:04 18243      /usr/lib/locale/en_US.utf8/LC_NAME
aa49f000-aa4a0000 r-xp 00000000 03:04 18244      /usr/lib/locale/en_US.utf8/LC_ADDRESS
aa4a0000-aa4a1000 r-xp 00000000 03:04 18245      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
aa4a1000-aa4a2000 r-xp 00000000 03:04 18246      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
aa6a6000-aa6ac000 r-xp 00000000 03:04 1002842    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa6ac000-aa6ad000 rwxp 00006000 03:04 1002842    /usr/lib/j2se/1.4/jre/lib/i386/libnio.so
aa7af000-aa84f000 r-xs 00000000 03:04 1032875    /usr/share/java/gtk2.10.jar
aa84f000-aa857000 r-xs 00000000 03:04 1032873    /usr/share/java/cairo1.0.jar
aa857000-aa85d000 r-xs 00000000 03:04 1032872    /usr/share/java/glib0.4.jar
aa85d000-aaa0a000 r-xs 00000000 03:04 101185     /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.1.v3235.jar
aaa0a000-aaa12000 r-xs 00000000 03:04 1032597    /usr/share/java/commons-cli-1.0.jar
aaa12000-aaa46000 r-xs 00000000 03:04 1032599    /usr/share/java/log4j-1.2.13.jar
aaa46000-aab3b000 r-xs 00000000 03:04 1032348    /usr/share/java/bcprov.jar
aac3d000-aac4c000 r-xp 00000000 03:04 1002864    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aac4c000-aac4d000 rwxp 0000e000 03:04 1002864    /usr/lib/j2se/1.4/jre/lib/i386/libnet.so
aac73000-ab3a0000 r-xs 00000000 03:04 1032879    /usr/share/java/Azureus2.jar
ab3a0000-ab3ae000 r-xs 00000000 03:04 1002825    /usr/lib/j2se/1.4/jre/lib/ext/ldapsec.jar
ab3ae000-ab46a000 r-xs 00000000 03:04 1002826    /usr/lib/j2se/1.4/jre/lib/ext/localedata.jar
ab46a000-ab486000 r-xs 00000000 03:04 1002824    /usr/lib/j2se/1.4/jre/lib/ext/sunjce_provider.jar
ab68a000-ab6bd000 r-xp 00000000 03:04 16778      /usr/lib/locale/en_US.utf8/LC_CTYPE
b5968000-b5f08000 r-xs 00000000 03:04 984796     /usr/lib/j2se/1.4/jre/lib/charsets.jar
b5f08000-b5f19000 r-xs 00000000 03:04 984794     /usr/lib/j2se/1.4/jre/lib/jce.jar
b5f19000-b5ff6000 r-xs 00000000 03:04 984792     /usr/lib/j2se/1.4/jre/lib/jsse.jar
b5ff6000-b600c000 r-xs 00000000 03:04 984798     /usr/lib/j2se/1.4/jre/lib/sunrsasign.jar
b6056000-b7a02000 r-xs 00000000 03:04 984799     /usr/lib/j2se/1.4/jre/lib/rt.jar
b7a02000-b7a13000 r-xp 00000000 03:04 1002861    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a13000-b7a15000 rwxp 00011000 03:04 1002861    /usr/lib/j2se/1.4/jre/lib/i386/libzip.so
b7a15000-b7a34000 r-xp 00000000 03:04 1002845    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a34000-b7a35000 rwxp 0001f000 03:04 1002845    /usr/lib/j2se/1.4/jre/lib/i386/libjava.so
b7a35000-b7a46000 r-xp 00000000 03:04 1002850    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a46000-b7a47000 rwxp 00011000 03:04 1002850    /usr/lib/j2se/1.4/jre/lib/i386/libverify.so
b7a47000-b7a50000 r-xp 00000000 03:04 458862     /lib/tls/i686/cmov/libnss_files-2.4.so
b7a50000-b7a52000 rwxp 00008000 03:04 458862     /lib/tls/i686/cmov/libnss_files-2.4.so
b7a52000-b7a5a000 r-xp 00000000 03:04 458864     /lib/tls/i686/cmov/libnss_nis-2.4.so
b7a5a000-b7a5c000 rwxp 00007000 03:04 458864     /lib/tls/i686/cmov/libnss_nis-2.4.so
b7a5c000-b7a63000 r-xp 00000000 03:04 458860     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7a63000-b7a65000 rwxp 00006000 03:04 458860     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7a65000-b7a68000 r-xp 00000000 03:04 901718     /usr/lib/libgmodule-2.0.so.0.1200.4
b7a68000-b7a69000 rwxp 00002000 03:04 901718     /usr/lib/libgmodule-2.0.so.0.1200.4
b7a69000-b7a6c000 r-xs 00000000 03:04 1002823    /usr/lib/j2se/1.4/jre/lib/ext/dnsns.jar
b7a6c000-b7a73000 r-xs 00000000 03:04 917506     /usr/lib/gconv/gconv-modules.cache
b7a73000-b7a97000 r-xp 00000000 03:04 458857     /lib/tls/i686/cmov/libm-2.4.so
b7a97000-b7a99000 rwxp 00023000 03:04 458857     /lib/tls/i686/cmov/libm-2.4.so
b7a99000-b7aab000 r-xp 00000000 03:04 458859     /lib/tls/i686/cmov/libnsl-2.4.so
b7aab000-b7aad000 rwxp 00011000 03:04 458859     /lib/tls/i686/cmov/libnsl-2.4.so
b7aaf000-b7d70000 r-xp 00000000 03:04 1002854    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7d70000-b7d8b000 rwxp 002c0000 03:04 1002854    /usr/lib/j2se/1.4/jre/lib/i386/client/libjvm.so
b7da3000-b7ed0000 r-xp 00000000 03:04 458853     /lib/tls/i686/cmov/libc-2.4.so
b7ed0000-b7ed2000 r-xp 0012c000 03:04 458853     /lib/tls/i686/cmov/libc-2.4.so
b7ed2000-b7ed4000 rwxp 0012e000 03:04 458853     /lib/tls/i686/cmov/libc-2.4.so
b7ed8000-b7eda000 r-xp 00000000 03:04 458856     /lib/tls/i686/cmov/libdl-2.4.so
b7eda000-b7edc000 rwxp 00001000 03:04 458856     /lib/tls/i686/cmov/libdl-2.4.so
b7edc000-b7eeb000 r-xp 00000000 03:04 458867     /lib/tls/i686/cmov/libpthread-2.4.so
b7eeb000-b7eed000 rwxp 0000f000 03:04 458867     /lib/tls/i686/cmov/libpthread-2.4.so
b7eef000-b7ef0000 r-xp 00000000 03:04 18247      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7ef0000-b7ef4000 rwxs 00000000 03:04 377015     /tmp/hsperfdata_dale/14386
b7ef4000-b7efc000 r-xp 00000000 03:04 1019308    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7efc000-b7efd000 rwxp 00007000 03:04 1019308    /usr/lib/j2se/1.4/jre/lib/i386/native_threads/libhpi.so
b7eff000-b7f18000 r-xp 00000000 03:04 426000     /lib/ld-2.4.so
b7f18000-b7f1a000 rwxp 00018000 03:04 426000     /lib/ld-2.4.so
bf91f000-bf935000 rwxp bf91f000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

Heap at VM Abort:
Heap
 def new generation   total 576K, used 391K [0xab8c0000, 0xab960000, 0xabda0000)
  eden space 512K,  64% used [0xab8c0000, 0xab912070, 0xab940000)
  from space 64K,  98% used [0xab940000, 0xab94fc90, 0xab950000)
  to   space 64K,   0% used [0xab950000, 0xab950000, 0xab960000)
 tenured generation   total 4700K, used 3348K [0xabda0000, 0xac237000, 0xaf8c0000)
   the space 4700K,  71% used [0xabda0000, 0xac0e5100, 0xac0e5200, 0xac237000)
 compacting perm gen  total 13568K, used 13389K [0xaf8c0000, 0xb0600000, 0xb38c0000)
   the space 13568K,  98% used [0xaf8c0000, 0xb05d3508, 0xb05d3600, 0xb0600000)

Local Time = Sun Jan 28 14:50:55 2007
Elapsed Time = 7
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid14386.log.
# Please refer to the file for further information.
#
Aborted (core dumped)

```

This error report was generated by running azureus via the CLI.

---

### Post by taurus on 2007-01-28
Looks like you don't have either Sun's java or Blackdown's java installed!  What's the output of this command from a terminal?

```
java -version
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by AceRimmer on 2007-01-30
I'm having the exact same problem, here is the error message I'm getting. 

```
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Tue Jan 30 16:50:22 CST 2007::org.gudy.azureus2.core3.config.impl.ConfigurationManager::getIntParameterRaw::268:
  java.lang.ClassCastException: [B
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getIntParameterRaw(ConfigurationManager.java:266)
        at org.gudy.azureus2.core3.config.impl.ConfigurationManager.getIntParameter(ConfigurationManager.java:274)
        at org.gudy.azureus2.core3.config.COConfigurationManager.getIntParameter(COConfigurationManager.java:171)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.checkForWhatsNewWindow(MainWindow.java:1543)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.showMainWindow(MainWindow.java:675)
        at org.gudy.azureus2.ui.swt.mainwindow.MainWindow.runSupport(MainWindow.java:571)
        at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:123)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3143)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2845)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:125)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb058dd02, pid=8062, tid=3085108912
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid8062.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

And I get this. 
```
aaron@Cthulhu:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
aaron@Cthulhu:~$ 
```

I uninstalled and reinstalled the azureus package with no luck.

---

### Post by AceRimmer on 2007-01-31
Anybody?

---

### Post by mcglnx on 2007-01-31
Did you try with Java 1.4?

---

### Post by hmsf on 2007-01-31
Have you tried this solution?

[http://ubuntuforums.org/showpost.php?p=2077489&postcount=6]("http://ubuntuforums.org/showpost.php?p=2077489&postcount=6")

It's been working for me at least until now, since this morning..

---

### Post by lenooh on 2007-02-07
take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=351689]("http://ubuntuforums.org/showthread.php?t=351689")

---

