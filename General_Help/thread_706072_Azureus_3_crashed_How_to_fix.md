---
title: "Azureus 3 crashed How to fix"
date: 2008-02-24
forum: General Help
---

### Post by cnshzj007 on 2008-02-24
```
bond007@bond007-laptop:/opt/azureus$ ./azureus 
Starting Azureus...
Suitable java version found [java = 1.6.0_04]
Configuring environment...
Java exec found in PATH. Verifying...
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
Locale Initializing took 580ms
   Core: 26ms for å&#138;*è½½æ&#146;ä»¶ï¼&#154;azupdater
   Core: 25ms for å&#138;*è½½æ&#146;ä»¶ï¼&#154;azupnpav
   Core: 50ms for å&#138;*è½½æ&#146;ä»¶ï¼&#154;azplugins
   Core: 50ms for å&#138;*è½½æ&#146;ä»¶ï¼&#154;azrating
   Core: 157ms for å&#138;*è½½æ&#146;ä»¶ï¼&#154;å&#134;&#133;å»º
   Core: 177ms for è£&#133;è½½ Torrent 1 ç&#154;&#132; 1 : /home/bond007/.azureus/torrents/Gopher+%5BCVKEGP27YCADFIBV6AJAUV74JEXIK6DP%5D.torrent
   Core: 174ms for å&#136;å§&#139;å&#140;&#150;å&#133;¨å±&#128; Torrent ç®¡ç&#134;å&#153;¨
   Core: 75ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;UPnP Media Server
   Core: 137ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;Tracker Static Pages
   Core: 26ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;Client ID
   Core: 25ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;UPnP
   Core: 27ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;DHT
   Core: 26ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;DHT Tracker
   Core: 25ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;azextseed
Core Initializing took 1102ms
GUI Initializing took 25ms
DEBUG::Sun Feb 24 15:43:54 CST 2008  ExternalStimulus debug
   Core: 180ms for å&#136;å§&#139;å&#140;&#150;æ&#146;ä»¶ï¼&#154;azlocaltracker
skin init took 1362ms
createWindow init took 152ms
skin layout took 268ms
skin widgets init took 300ms
shell.open took 292ms
processStartupDMS took 0ms
psDMS 6ms
1203839037940:Downloading-Mini] doPaint MediaThumb took 236ms. ListRow {0,Downloading-Mini,visible}
1203839038001:Downloading-Mini] doPaint took 297ms. ListRow {0,Downloading-Mini,visible}
1203839038002:Downloading-Mini] 298ms to paint0 - 0

(SWT:16460): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xa7266767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xa72668b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xa752e29d]
#3 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xa3c408ce]
#4 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xa3c1d067]
#5 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so [0xa3c1d318]
#6 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xa3c1d61f]
#7 [0xb4d1d3aa]
#8 [0xb4d15f0d]
#9 [0xb4d15f0d]
#10 [0xb4d13249]
#11 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/server/libjvm.so [0x637338d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/server/libjvm.so [0x64fd168]
#13 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/server/libjvm.so [0x6373220]
#14 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x363) [0x63c90d3]
#15 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7d2e96d]
#16 [0xb4d1d3aa]
#17 [0xb4d15da7]
#18 [0xb4d13249]
#19 /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/server/libjvm.so [0x637338d]
java: xcb_xlib.c:82: xcb_xlib_unlock: &#26029;&#35328; `c->xlib.lock' &#22833;&#36133;.
./azureus: line 188: 16460 &#24573;&#30053;                  (core dumped) ${JAVA_PROGRAM_DIR}java "${JAVA_ARGS}" -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" -Dazureus.script="$0" $JAVA_PROPS $START_CLASS "$@"
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

```

---

### Post by danwood76 on 2008-02-24
How did you install azureus and java?

---

