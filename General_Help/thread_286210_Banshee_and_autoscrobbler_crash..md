---
title: "Banshee and autoscrobbler crash."
date: 2006-10-27
forum: General Help
---

### Post by Sewage on 2006-10-27
Banshee keeps crashing when i enable the audio scrobbler plugin. D: It didn't before i did this fresh install to Edgy~ I looked over the error but am not really good at these things, any help would be very bueno.

```
An unhandled exception was thrown: Could not find a part of the path "/home/brad/.gnome2/banshee/plugins".

at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x0022e>
at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0004b>
at System.Xml.XmlTextWriter..ctor (string,System.Text.Encoding) <0x0002a>
at Banshee.Plugins.Audioscrobbler.Queue.Save () <0x00061>
at Banshee.Plugins.Audioscrobbler.Engine.TransmitQueue () <0x00029>
at Banshee.Plugins.Audioscrobbler.Engine.StateTransitionHandler () <0x00175>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x00037>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7f44dd5
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.BansheeEntry.Startup (string[]) <0x00657>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0x00048>
at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000ae>

.NET Version: 2.0.50727.42

Assembly Version Information:

System.Web (2.0.0.0)
TagLib (0.0.0.0)
System.Configuration (2.0.0.0)
Mono.Security (2.0.0.0)
NotificationAreaIcon (0.11.1.41236)
MusicBrainz (0.11.1.41226)
MetadataSearch (0.11.1.41235)
MMKeys (0.11.1.41236)
Banshee.Plugins.Audioscrobbler (0.11.1.41234)
ipod-sharp-ui (0.0.1.0)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.11.1.41233)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.11.1.41233)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.11.1.41232)
GStreamerPlayerEngine (0.11.1.41231)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Last.FM (0.0.0.0)
NDesk.DBus (0.0.0.0)
Mono.Posix (2.0.0.0)
Banshee.Widgets (0.11.1.41228)
glade-sharp (2.10.0.0)
gnome-sharp (2.16.0.0)
gconf-sharp (2.16.0.0)
NDesk.DBus.GLib (0.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.11.1.41231)
banshee (0.11.1.41238)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.17-10-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

```

---

### Post by Sewage on 2006-10-30
I hate to bump but I am really missing my last.fm chats. >:

---

### Post by twstokes on 2006-11-07
I'm having the exact same issue after freshly installing Banshee.

---

### Post by twstokes on 2006-11-08
I got mine working. Just make a directory called "plugins" in ~/.gnome2/banshee:
```

mkdir ~/.gnome2/banshee/plugins
```

I had to restart Banshee for it to take effect.

Evidently the crash is from the plugin not being able to store the AudioscrobblerQueue.xml file.

---

