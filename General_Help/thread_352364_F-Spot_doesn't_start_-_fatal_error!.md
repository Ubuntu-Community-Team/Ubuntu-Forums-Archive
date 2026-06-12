---
title: "F-Spot doesn't start - fatal error!"
date: 2007-02-03
forum: General Help
---

### Post by Carrots171 on 2007-02-03
Whenever I try to start F-Spot, a window pops up saying that "F-Spot Encountered a Fatal Error. This may be due to a programming error. Please help us make F-Spot better by reporting this error. Thank you in advance!". The window also displays some error output. 

I've been using version 0.1.11 of F-Spot (from the repositories) on Dapper for several months before it stopped working today. 

The error output is as follows: 

```
An unhandled exception was thrown: No handler HandleZoomOut found for signal button_press_event

at SignalConnector.ConnectFunc (intptr,intptr,intptr,intptr,intptr,int,intptr) <0x00301>
at (wrapper native-to-managed) SignalConnector.ConnectFunc (intptr,intptr,intptr,intptr,intptr,int,intptr) <0x0004b>
in (unmanaged) 0xb626acbb
at (wrapper managed-to-native) SignalConnector.glade_xml_signal_autoconnect_full (intptr,Glade.XML/SignalConnector/RawXMLConnectFunc,intptr) <0x00004>
at SignalConnector.Autoconnect () <0x00059>
at Glade.XML.Autoconnect (object) <0x00042>
at MainWindow..ctor (Db) <0x0006c>
at FSpot.Core.get_MainWindow () <0x0002a>
at FSpot.Core.Organize () <0x0000f>
at FSpot.Driver.Main (string[]) <0x00547>

.NET Version: 1.1.4322.2032

Assembly Version Information:

gconf-sharp (2.8.0.0)
pango-sharp (2.8.0.0)
SemWeb (0.5.0.2)
glade-sharp (2.8.0.0)
gtkhtml-sharp (2.8.0.0)
System.Data (1.0.5000.0)
Mono.Data.SqliteClient (1.0.5000.0)
Mono.Posix (1.0.5000.0)
gdk-sharp (2.8.0.0)
gnome-vfs-sharp (2.8.0.0)
dbus-sharp (0.60.0.0)
System (1.0.5000.0)
atk-sharp (2.8.0.0)
gtk-sharp (2.8.0.0)
glib-sharp (2.8.0.0)
gnome-sharp (2.8.0.0)
f-spot (0.0.0.0)
mscorlib (1.0.5000.0)

Platform Information: Linux 2.6.15-27-k7 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
```

How do you fix this? Or is this a bug that I should report?

---

### Post by Carrots171 on 2007-02-06
Bump

---

### Post by geektron on 2007-03-15
I actually have the same problem on SLED 10 and I haven't found a solution yet. 

Did you have any luck?

---

