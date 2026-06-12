---
title: "banshee wont start"
date: 2007-04-13
forum: General Help
---

### Post by dpsleep on 2007-04-13
well i have run into a few problems with banshee before, but I've had no problem fixing them. but this one i have no clue about. when i start banshee i get to the load user interface part of the loading screen then i get an error report that looks like this

```
An unhandled exception was thrown: The given key was not present in the dictionary.

  at System.Collections.Generic.Dictionary`2[System.Int32,Banshee.Base.TrackInfo].get_Item (Int32 ) [0x00000] 
  at Banshee.Base.Library.GetTrack (Int32 id) [0x00000] 
  at Banshee.Plugins.Bookmarks.Bookmark.LoadAll () [0x00000] 
  at Banshee.Plugins.Bookmarks.BookmarksPlugin.HandleLibraryReloaded (System.Object sender, System.EventArgs args) [0x00000] 
  at Banshee.Plugins.Bookmarks.BookmarksPlugin.InterfaceInitialize () [0x00000] 
  at Banshee.Plugins.Plugin.OnUIManagerInitialized (System.Object o, System.EventArgs args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Banshee.Gui.UIManager.OnInitialized () [0x00000] 
  at Banshee.Gui.UIManager.Initialize () [0x00000] 
  at Banshee.PlayerUI..ctor () [0x00000] 
  at Banshee.BansheeEntry+<>c__CompilerGenerated1.<>c__AnonymousMethod17 () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

glade-sharp (2.10.0.0)
Boo.Lang.Compiler (1.0.0.0)
Mono.Security (2.0.0.0)
ShowTrackOnChange (0.0.0.0)
Scope (0.0.0.0)
Cleanup (0.0.0.0)
Banshee.Plugins.Recommendation (0.13.0.23370)
Banshee.Plugins.Radio (0.13.0.23369)
Banshee.Plugins.Podcast (0.13.0.23368)
Banshee.Plugins.NotificationAreaIcon (0.13.0.23367)
Banshee.Plugins.MiniMode (0.13.0.23365)
Banshee.Plugins.MetadataSearch (0.13.0.23365)
Banshee.Plugins.MMKeys (0.13.0.23366)
Banshee.Plugins.Daap (0.13.0.23364)
Banshee.Plugins.Bookmarks (0.13.0.23363)
Banshee.Plugins.Audioscrobbler (0.13.0.23362)
AlbumArt (0.0.0.0)
Alarm (0.2.0.0)
Mono.Zeroconf (0.0.0.0)
Banshee.Plugins.Awn (0.0.0.0)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.13.0.23361)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.13.0.23361)
Banshee.MediaEngine.GStreamer (0.13.0.23360)
System.Xml (2.0.0.0)
System.Transactions (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.13.0.23354)
Last.FM (0.0.0.0)
NDesk.DBus (1.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
gnome-sharp (2.16.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.13.0.23357)
banshee (0.13.0.23359)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.20-14-386 i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
4.0

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"


```

if anyone knows whats going on and can help, it would be much appreciated.

---

### Post by dpsleep on 2007-04-13
ok, nevermind. it was pretty easy to fix, just a corrupt database. if anyone else wants to know how to fix this just goto ~/.gnome2/banshee and delete the .db file.

---

