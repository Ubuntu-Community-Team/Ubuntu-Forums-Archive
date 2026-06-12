---
title: "Banshee Freeze on start raring ringtail"
date: 2013-05-03
forum: General Help
---

### Post by javaholic on 2013-05-03
Window completely freezes (greyed out) on load and it never recovers.  Click X and i can force quit it.  Annoying cause I have become accustomed to banshee.

Here is the contents of ~/.config/banshee-1/log

```
exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  01:38:22.672] Running Banshee 2.6.1: [Ubuntu 13.04 (linux-gnu, x86_64) @ 2013-04-21 19:43:57 UTC]

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_51_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:6249): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_64_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

```

---

### Post by javaholic on 2013-05-03
Output of 'banshee --debug'

```
banshee --debug
** Running Mono with --debug   **
[1 Debug 11:56:43.535] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Info  11:56:43.550] Running Banshee 2.6.1: [Ubuntu 13.04 (linux-gnu, x86_64) @ 2013-04-21 19:43:57 UTC]
[1 Debug 11:56:43.565] Initializing GTK
[1 Debug 11:56:44.609] Post-Initializing GTK
[1 Debug 11:56:44.625] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 11:56:44.627] Using default gconf-base-key
[1 Debug 11:56:44.711] Core service started (DBusServiceManager, 0.001208)
[1 Debug 11:56:44.714] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 11:56:44.720] Core service started (DBusCommandService, 0.008278)
[1 Debug 11:56:44.749] Opened SQLite (version 3.7.15.2) connection to /home/<<username here>>/.config/banshee-1/banshee.db
[1 Debug 11:56:44.750] Core service started (DbConnection, 0.029574)
[1 Debug 11:56:44.759] Database version 45 is up to date
[1 Debug 11:56:44.774] Running ANALYZE against database to improve performance
[1 Debug 11:56:44.868] Core service started (PreferenceService, 0.012502)
[1 Debug 11:56:44.874] Core service started (Network, 0.005909)
[1 Debug 11:56:44.875] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 11:56:44.875] Core service started (SourceManager, 0.000881)
[1 Debug 11:56:44.880] Core service started (MediaProfileManager, 0.000303)
[1 Debug 11:56:44.883] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 11:56:44.885] Core service started (PlayerEngine, 0.004569)
[1 Debug 11:56:44.899] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 11:56:44.900] Core service started (PlaybackController, 0.002777)
[1 Debug 11:56:44.905] Starting - Startup Job
[1 Debug 11:56:44.906] Core service started (JobScheduler, 0.005418)
[1 Debug 11:56:44.916] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 11:56:44.952] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 11:56:44.955] Core service started (HardwareManager, 0.04883)
[1 Debug 11:56:44.958] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 11:56:44.960] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 11:56:44.962] Core service started (CollectionIndexerService, 0.00679)
[1 Debug 11:56:44.964] Core service started (SaveTrackMetadataService, 0.001436)
[1 Debug 11:56:44.970] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 11:56:44.971] Core service started (GtkElementsService, 0.007366)
[1 Debug 11:56:44.972] Core service started (InterfaceActionService, 0.001194)
[1 Debug 11:56:45.099] Extension actions loaded: Detect Duplicate Songs
[1 Debug 11:56:45.101] Extension actions loaded: MetadataFixActions
[1 Debug 11:56:45.101] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 11:56:45.102] Album artwork path set to /home/<<username here>>/.cache/media-art
[1 Debug 11:56:45.120] Core service started (ArtworkManager, 0.018635)
[1 Debug 11:56:45.120] Core service started (BookmarksService, 0.000206)
[1 Debug 11:56:45.459] Adding context page lastfm-recommendations
[1 Debug 11:56:45.503] Adding context page wikipedia
[1 Debug 11:56:45.506] Adding context page lyrics

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_51_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_64_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_64_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_76_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:21047): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_76_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init
[1 Debug 11:56:45.727] Constructed Nereid interface: 0.575924
[1 Debug 11:56:45.813] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 11:56:45.813] Core service started (NereidPlayerInterface, 0.682679)
[1 Debug 11:56:45.820] Extension service started (DapService, 0.005809)
[1 Debug 11:56:45.830] Audioscrobbler state: connected
[1 Debug 11:56:45.833] Extension service started (AudioscrobblerService, 0.012749)
[1 Debug 11:56:45.866] Extension service started (AudioCdService, 0.032584)
[1 Debug 11:56:45.867] Extension service started (DvdService, 0.001289)
[1 Debug 11:56:45.883] Extension service started (MprisService, 0.016076)
[1 Debug 11:56:45.908] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 11:56:45.908] Extension service started (MultimediaKeysService, 0.024704)
[1 Debug 11:56:45.914] Extension service started (AmazonMp3DownloaderService, 0.005791)
[1 Debug 11:56:45.918] Extension service started (PodcastService, 0.003366)
[1 Debug 11:56:45.920] Extension service started (DaapService, 0.00186)
[1 Debug 11:56:45.948] Extension service started (AppIndicatorService, 0.027658)
[1 Info  11:56:45.951] Updating web proxy from GConf
[1 Debug 11:56:45.956] Direct connection, no proxy in use
[1 Debug 11:56:45.971] Extension service started (GnomeService, 0.022888)
[1 Debug 11:56:45.973] Extension service started (CoverArtService, 0.002452)
[1 Debug 11:56:46.256] Extension service started (LyricsService, 0.282235)
[1 Debug 11:56:46.277] Extension service started (EmusicService, 0.021328)
[1 Debug 11:56:46.317] Extension service started (GStreamerCoreService, 0.039407)
[1 Debug 11:56:46.328] Extension service started (StreamrecorderService, 0.011152)
[1 Debug 11:56:46.334] Extension service started (BpmService, 0.005692)
[1 Info  11:56:46.335] All services are started 1.673503
[1 Debug 11:56:47.758] Extension source loaded: Last.fm
[1 Debug 11:56:47.774] Extension source loaded: Internet Archive
[1 Info  11:56:47.799] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[1 Debug 11:56:47.801] Extension source loaded: Amazon MP3 Store
[1 Debug 11:56:47.805] Extension source loaded: Miro Guide
[1 Debug 11:56:47.933] Extension source loaded: File System Queue
[1 Debug 11:56:47.949] Extension source loaded: Radio
[1 Debug 11:56:47.952] Extension source loaded: Now Playing
[1 Debug 11:56:47.975] Extension source loaded: Audiobooks
[1 Debug 11:56:49.267] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 11:56:49.268] Extension source loaded: Play Queue
[1 Debug 11:56:49.274] Starting GTK main loop
[1 Debug 11:56:49.770] Creating Pango.Layout, configuring Cairo.Context
[1 Info  11:56:49.994] nereid Client Started
[1 Debug 11:56:49.996] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 11:56:50.021] (libbanshee:player) Audiosink has volume: YES
[1 Debug 11:56:50.031] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 11:56:50.052] Player state change: NotReady -> Ready
[1 Debug 11:56:50.072] Loaded equalizer presets: 0.01244
[1 Debug 11:56:50.085] Player state change: Ready -> Idle
[1 Debug 11:56:50.089] (libbanshee:player) Disabled ReplayGain
[1 Info  11:56:50.090] GStreamer version 1.0.6.0, gapless: False, replaygain: False
[1 Debug 11:56:50.096] Delayed Initializating Banshee.Dap.DapService
[1 Debug 11:56:50.103] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 11:56:50.104] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 11:56:50.105] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 11:56:50.109] Delayed Initializating Banshee.Podcasting.PodcastService
[7 Info  11:56:50.134] AppleDeviceSource is ignoring unmounted volume Floppy Disk
[1 Debug 11:56:50.174] Delayed Initializating Banshee.Daap.DaapService
[1 Debug 11:56:50.174] Delayed Initializating Banshee.Streamrecorder.StreamrecorderService

(Banshee:21047): GLib-GObject-WARNING **: cannot register existing type `GstFormat'

(Banshee:21047): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(Banshee:21047): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'

(Banshee:21047): GLib-GObject-WARNING **: cannot register existing type `GstQuery'

(Banshee:21047): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(Banshee:21047): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'

(Banshee:21047): GLib-GObject-WARNING **: cannot register existing type `GstObject'

(Banshee:21047): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(Banshee:21047): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'
[14 Debug 11:56:51.875] DAAP Proxy listening for connections on port 8089
Killed

```

I would be most grateful if someone with more knowhow than me to explain what is going on here.

---

### Post by cbs228 on 2013-05-04
There are one or more extensions which are causing Banshee to freeze, see [https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1099218](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1099218). The Streamrecorder extension, in particular, has caused me problems. There is a workaround given (see #6 and #12) that will help you disable the buggy extensions.

---

### Post by javaholic on 2013-05-06
thanks for the nudge in the right direction after some back and forth I was able to work out that it was banshee-extension-streamrecorder that was causing all the problems.

---

